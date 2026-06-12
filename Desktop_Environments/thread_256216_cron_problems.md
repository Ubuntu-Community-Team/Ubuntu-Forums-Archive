---
title: "cron problems"
date: 2006-09-12
forum: Desktop Environments
---

### Post by puchat3k on 2006-09-12
[FONT="Arial"][SIZE="4"]Hello
I would like to periodically take a screen shot of my desktop and upload it to a server, besides that it could be fun to automatically change the desktop background to a random wallpaper every once in a while. I figured that cron would be ideal for the job. I found some scripts I could use:[/SIZE][/FONT]

shot.bash for the screen shot
```

#!/bin/bash
/usr/bin/import -window root -resize 640x480 /home/jakub/mydesktop.jpg

```

random-wall.bash for the random wallpaper
```
#!/bin/bash
# by lcj (c) 2002.10.22
# thanks goes to: Cegla, star @ #gnome-art
# Purpose: Change randomly wallpaper in Gnome, when nautilus is set to draw desktop
# Usage: change the value: WALLPAPERS_LOCATION to directory with wallpapers,
# remember the / at the end. There should be no other files than the
# pictures intended for wallpaper in that directory
# version: 0.2
# history:
# 22-Oct-2002, version 0.2 Initial release
# 22-Oct-2002, changed to work with pictures from given directory
# 14-May-2003, finaly got a real RANDOM NUMBER!
#
# CONFIGURATION
# CHANGE THE DIR BELOW TO YOUR WALLPAPER DIRECTORY:
####################################################
WALLPAPERS_LOCATION="/home/jakub/dokumenty/pix/stare/"
####################################################
# END OF CONFIGURATION
# main code, lets enter the directory
cd $WALLPAPERS_LOCATION
# counting number of files
ile=`ls | wc -l | tr -d "[ ]"`
#reset counter to 1
counter=1
# now get every file name and put it ino pic[licznik] table
for i in `ls`
do
 pic[counter]=${WALLPAPERS_LOCATION}$i
 ((counter=counter+1))
done  
# now lets get the RANDOM number
which_pic=$(($RANDOM % $ile))
# set $ update the wallpaper
echo $which_pic
/usr/bin/fbsetbg -f ${pic[$which_pic]}
```

ps -A | grep cron output:
```
4660 ?        00:00:00 cron
```

crontab -l output:
```
*/30 * * * * /home/jakub/random-wall.bash   >/dev/null 2>&1
*/5 * * * * /home/jakub/shot.bash    >/dev/null 2>&1
*/1 * * * * * echo Hello > /home/jakub/hello.log
```

[FONT="Arial"][SIZE="4"]As you can see I've added a third cron job to the crontab to test if something at all works, sadly it doesn't. All of my scripts work fine from the command line but fail when they are theoretically supposed to be run by cron.
I've also created the /etc/cron.allow and /etc/cron.deny files and edited them accordingly (to allow user 'jakub'). This step is kind of pointless because without those files present cron should allow all users to use it.
And finally 'cat /var/log/syslog | grep cron' shows that the crontab has been edited, installed and so on but not if the commands have been executed, there are no errors or otherwise something that could lead me int he right direction. 
I'm seriously bummed. This is my first time using cron, a utility that is very well documented. I think that I did everything right and according to the manuals. In theory crond should read the users crontabs and attempt to execute the commands but somehow in my case there is a problem. But maybe I've made a mistake somewhere or I've forgot about something. Any input would be greatly appreciated. Thanks in advance.[/SIZE][/FONT]

---

### Post by vachun on 2006-09-13
Try to add this line in your crontab file 

* * * * * /home/jakub/test 
( there are only 5 '*' , not 6 as in your example )

and create bash script   /home/jakub/test
#/bin/bash
echo Hello > /home/jakub/hello.log

let me know, if it works ...

Jan

---

### Post by puchat3k on 2006-09-15
I've done as you had said. In my crontab I put the command:
```
* * * * * /home/jakub/test.bash
```

The contents of the file are as follows:
```
#/bin/bash
echo Hello > /home/jakub/test.log
```

The above setup does _not_ work. I have yet to se a test.log file created in my home folder containing "hello"

After you pointed out my mistake with the extra star I have corrected it and now I also have such a command in my crontab:
```
* * * * * echo Hello > /home/jakub/hello.log
```

This above command works so my first impression that cron doesn't work is of course false. But what to do with your suggesstion how to get the test.log command running and my other scripts?

---

