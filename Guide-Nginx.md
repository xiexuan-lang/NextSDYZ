# Guide: How to start enjoy NextSDYZ on your iFlytek tablet within 10 minutes
*For network technology learning and communication purposes ONLY*

## 1.Download Nginx to the computer
Nginx doesn't need to install, you only need to extract the .zip file to a safe place and remember the path.

## 2.Edit nginx.conf files
Open "nginx.conf" in Notepad or other plain editer, replace all the text with the following:

``` 
worker_processes  1;

events {
    worker_connections  1024;
}


http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;

    keepalive_timeout  65;

    gzip  on;

    server {

    listen 9000;
    server_name sdyz.huangyinhao.top:9000;

    client_max_body_size 512M;
    client_body_timeout 300s;
    fastcgi_buffers 64 4K;

    gzip on;
    gzip_vary on;
    gzip_comp_level 4;
    gzip_min_length 256;
    gzip_proxied expired no-cache no-store private no_last_modified no_etag auth;
    gzip_types application/atom+xml application/javascript application/json application/ld+json application/manifest+json application/rss+xml application/vnd.geo+json application/vnd.ms-fontobject application/wasm application/x-font-ttf application/x-web-app-manifest+json application/xhtml+xml application/xml font/opentype image/bmp image/svg+xml image/x-icon text/cache-manifest text/css text/plain text/vcard text/vnd.rim.location.xloc text/vtt text/x-component text/x-cross-domain-policy;


    add_header Referrer-Policy                      "no-referrer"   always;
    add_header X-Content-Type-Options               "nosniff"       always;
    add_header X-Download-Options                   "noopen"        always;
    add_header X-Frame-Options                      "SAMEORIGIN"    always;
    add_header X-Permitted-Cross-Domain-Policies    "none"          always;
    add_header X-Robots-Tag                         "none"          always;
    add_header X-XSS-Protection                     "1; mode=block" always;
    fastcgi_hide_header X-Powered-By;

    }
}
```
Then save this file.

## 3.Change Metric Settings
Change WLAN's Metric to "5", and LAN's Metric to "10".

## 4.Setup cron job for Nginx
Let it run **15 minutes after** user login, because iFlytek Class Service will always kill Nginx if Nginx starts before it.

Don't forget to set the 

![image](https://user-images.githubusercontent.com/64564727/154861023-a293548e-f156-4163-84cd-ea945bfdb015.png)


*If you see a cron job called "justRestartPC", delete it.*

## 5.Setup cron job for WiFi connection
For some unknow reasons, iFlytek Microcube will not automatically connect to sdyz-linshi after system reboot, so you need to run `netsh` in cmd to connect sdyz-linshi.

The command is the following.
```
netsh wlan connect name=sdyz-linshi
```
You have to connect to sdyz-linshi manually once, or the command will not work.

Let it run **15 seconds after** user login.

## 6.Reboot the computer
You must be tired but extied, why not drink a cup of coffee and take a few laps around the beautiful campus? 

Enjoy!
