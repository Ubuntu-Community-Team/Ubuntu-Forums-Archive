---
title: "Will this stump Synaptic?"
date: 2006-05-20
forum: Desktop Environments
---

### Post by lonelypauly on 2006-05-20
is there an app available to track my pc in the event it was ever stolen?

there are a few programs in the windows world that secretly report their ip address and other pieces of info periodically which can help authorities track down your gear.  

im assuming this is really easy to do...i have a web server so i could just have it send a logfile or something?  i just wouldn't know the first thing about it.

---

### Post by kaamos on 2006-05-20
If you just need the ip, you could use this script: [http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip)
Then just use "host yourdnsaddress" to get ip. You could alter the script as well to for example pass on log files with ftp or scp.

---

### Post by tomchuk on 2006-05-20
you could just add a cron job to hit a non-existant page on your server with `wget --quiet --spider` - your apache error logs would show a 404 with the client's IP.

for instance, in your crontab (crontab -e):
```

0 12 * * * wget --quiet --spider http://whatever.com/trackme

```

Just grep for trackme in your apache error logs and you'll get a list of IPs your computer was at noon every day.

Or you could hit a php script on your server that does the logging for you:

[php]
<?php
    $ip = $_SERVER['REMOTE_ADDR'];
    $file = "ip.txt";
    $date = date('l dS \of F Y h:i:s A');

    $handle = fopen($file, "a");
    if(!$handle)
        die("Unable to get handle on file: $file");

    if(fwrite($handle, $date . " : " . $ip . "\n") === FALSE){
        fclose($handle);
        die("Unsuccessful write to file: $file");
    }
    echo ($ip);
    fclose($handle);
?>
[/php]

just make sure you have a file ip.txt in the same directory that the server has write permission to.

---

