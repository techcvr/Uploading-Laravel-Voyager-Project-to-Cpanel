### Uploading-Laravel-Voyager-Project-to-Cpanel

1. upload the all files except the public folder in root of cpanel
2. upload the public folder in your project folder in public_html
3. update the PHP version to latest version which supported the laravel version.
4. open index.php in public_html folder and change the address of your root laravel files 
```
From
require __DIR__.'/../vendor/autoload.php';

To 
require __DIR__.'/vendor/autoload.php';

AND Change Bootstrap Path

From
$app = require_once __DIR__.'/../bootstrap/app.php';

To
$app = require_once __DIR__.'/bootstrap/app.php';
```

5. Login to voyager admin and run this command ->  php artisan storage:link 
6. go to config/filesystem and change 'public' object from:
``` 
'public' => [
    'driver' => 'local',
    'root' => storage_path('app/public'),
    'url' => env('APP_URL').'/storage',
    'visibility' => 'storage',
],
        
========== To =========== 

'public' => [
    'driver' => 'local',
    'root' => storage_path('app/public'),
    'url' => env('APP_URL').'/storage/app/public',
    'visibility' => 'public',
],

```
That's it. Your Voyager admin panel is ready.
