---
title: "PHP script cannot run .sh script..."
date: 2009-05-22
forum: Desktop Environments
---

### Post by Browner87 on 2009-05-22
I have a small personal web server running Ubuntu Hardy 8.04 and my problem is that when I try to access a PHP page I want it to do two things: 

1) Take a screenshot of the desktop on the SERVER
2) Redirect to that picture

This should be simple PHP code since the picture will always be the same file. What I have so far (for those who know PHP) is:

[PHP]<?php
	shell_exec('/media/disk/apache2dir/mine/screenshot.sh');
	sleep(3);
	header('Location: http://browner87.servebeer.com/mine/screenshot.png');

?>[/PHP]

The script screenshot.sh is also 2 lines (3 with the middle one added for debugging)

```
import -window root /media/disk/apache2dir/mine/screenshot.png
echo This should have ****ing worked!!
exit
```

The code in the script appears to run since I can capture the output. If, in the PHP, I echo the output of the shell_exec, it writes 'This should have ****ing worked!!' on the screen. However, nothing happens. No screenshot is taken and screenshot.png is not modified. If I run the first line of the script in a terminal (or run the script file for that matter), it works fine. The computer beeps, takes a sceenshot, beeps, then is done. The screenshot.png file is not updated. 

I have tried almost every combination of chmod and chown from 111 to 777 and root to browner87 to www-data and NOTHING makes the script run right.

Does anyone have a suggestion? Please?

---

### Post by mk__ on 2009-05-22
Either do this from a terminal:
```
sudo chmod +x /media/disk/apache2dir/mine/screenshot.sh
```
or change the code to this:
[PHP]<?php
    shell_exec('sh /media/disk/apache2dir/mine/screenshot.sh');
    sleep(3);
    header('Location: http://browner87.servebeer.com/mine/screenshot.png');

?> [/PHP]

---

### Post by Browner87 on 2009-05-24
I did both and no change. Good suggestions tho - I never tried putting 'sh' before my command.

Any other ideas?

---

### Post by Browner87 on 2009-05-25
I think an important detail is that this script has the same behavior as a Cron job. There is output, but no screenshot is taken.

---

### Post by s.fox on 2009-05-25
Hi,

Which version of php are you using?  The reason i ask is that shell_exec() is disabled when php safe mode is enabled.  Of course php safe mode was removed in PHP 6.0.0,  so it may not be what is making your script fail. 

Just a thought.  

-Ash R

---

### Post by Browner87 on 2009-05-25
I believe PHP5, but note the same behavior when set as a Cron job to be run. 

The problem I seem to be having more specifically is that my .sh script can ONLY be run through a terminal. Can anyone explain this?

I've heard of two possibilities really (since I do know the script is running - if I add a line in the script saying echo hello >> /tmp.txt, it adds hello to that file):

1) User permissions: the user Cron is running as doesn't have rights to run the Import command (or scrot - I've tried it too)
2) No Output: I read something about Cron not being able to handle many outputs of some programs or something. Also, perhaps these programs need more environment variables defined?

---

### Post by zomtec on 2009-05-26
As far as i know, neither cron or apache has access to the X server by default. you cannot do <?php exec('firefox &');?> for example.
Of course there are workarounds ... maybe take a look at the apache docs.

---

### Post by Browner87 on 2009-05-26
Does anyone know by chance how to work around this? I'm still stumped and can't find ANYTHING with a conclusive answer on how to do this.

---

### Post by Browner87 on 2009-05-27
Yay! Breakthorugh (kind of)

[http://studio.imagemagick.org/pipermail/magick-users/2005-November/016725.html]("http://studio.imagemagick.org/pipermail/magick-users/2005-November/016725.html")

[]("http://studio.imagemagick.org/pipermail/magick-users/2005-December/016886.html")

This sounds like the exact answer to what I need, but I can't quite make sense of what I have to do. I'm sure I can figure out how to get the DISPLAY environment variable set to (though I don't know what I'd set it to), but the rest just made a nice whooshing sound as it went over my head. Any help with it?

EDIT: Just added the second link and nothing seems to have worked yet. Here is my code:

[PHP]	shell_exec('DISPLAY=:0');
	shell_exec('export DISPLAY');
	shell_exec('HOME=/home/browner87');     //# or whatever it is
     shell_exec('export HOME');

	exec('import -display :0.0 -window root /media/disk/path/screenshot.png');[/PHP]

Any more ideas on this?

EDIT2:

In Cron I now have added DISPLAY=:0 and HOME=/home/browner87 and now it works. The problem now is that it won't work in PHP. I also tried one-lining it with semi-colons, but still no luck. I have the following in a .sh script:

> #!/bin/bash
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DISPLAY=:0
HOME=/home/browner87
/usr/bin/import -silent -display :0.0 -window root /media/disk/apache2dir/mine/screenshot.png

it works if in (sudo crontab -e) I put the path to the script, but if in PHP I say shell_exec('path to the script');, it does nothing.

---

### Post by orange-wedge on 2009-05-27
First of all it always helps to debug the output of cron scripts or daemon scripts by redirecting the output to a file.  You also could try using the exec function in php.:

[php]
 <?php 
    exec('sh /media/disk/apache2dir/mine/screenshot.sh > /tmp/screenshot.log'); 
    sleep(3); 
    header('Location: http://browner87.servebeer.com/mine/screenshot.png'); 

?>  [/php]Most likely your display is going to need be set with the following shell command:
```
export DISPLAY=localhost:0.0
```But you you will need to translate that to php with the function putenv:

[http://www.php.net/manual/en/function.putenv.php](http://www.php.net/manual/en/function.putenv.php)

---

### Post by Browner87 on 2009-05-28
[PHP]<?php

	putenv('DISPLAY=localhost:0.0"');
	shell_exec('/media/disk/apache2dir/mine/screenshot.sh > /media/disk/apache2dir/mine/screenshot.log');
	sleep(3);
	header('Location: http://browner87.servebeer.com/mine/screenshot.png');
	exit;
?>[/PHP]

no screenshot is taken and screenshot.log is empty. :(

Good advice though. Any more bits of good information?

---

### Post by orange-wedge on 2009-05-28
I'm noticing an extra double quote at the end of your putenv function.  

Try this:
[php]putenv('DISPLAY=localhost:0.0')[/php]

---

### Post by Browner87 on 2009-05-28
Whoops, my bad. Thanks. I'll try that.

Unfortunately I won't know if it worked until I get home because I got the screenshots working with Cron on 1 minute intervals, but I forgot ubuntu blacks the screen after a while, so I can't tell if it worked or not yet :P


EDIT: Nope, no working yet, but I'm not going to stress over it - I can now make Cron run it every minute, so that's good enough for now. Unless anyone can suggest an answer to this of course ^_^

---

