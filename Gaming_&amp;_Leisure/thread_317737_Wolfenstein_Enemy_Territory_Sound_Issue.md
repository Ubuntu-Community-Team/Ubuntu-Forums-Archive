---
title: "Wolfenstein Enemy Territory Sound Issue"
date: 2006-12-12
forum: Gaming &amp; Leisure
---

### Post by ZERO_SHIFT on 2006-12-12
This is what works for me (from terminal) to let Wolfenstein Enemy Territory sound work:

sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

Is there a command in which I can play the game without having to put in these commands over and over again.

Thanks in advance.

---

### Post by Shatrat on 2006-12-12
Put those into a script and then run the script instead of the ET executable?

---

### Post by Biggus on 2006-12-13
Hi there. I don't mean to disrupt the thread, but I've just found this thread, while searching for a solution as to how to get sound on ET.

When you say a script, I presume you must mean some sort of simple program, much like the ancient old .bat files I used to use in MS-DOS?

Is it simply the case that I would open up a text editor, put in the commands (the text used by ZERO_SHIFT), and add a command to launch the game? If so, do I have to give it any special sort of extension?

---

### Post by ZERO_SHIFT on 2006-12-15
How do you do a script?

---

### Post by Biggus on 2006-12-15
Hi dude. I'm still here trying to work this one out too.

I've copied and pasted the text we both use into a little file in my Desktop folder.

I've been using this page here : [URL="http://www.freeos.com/guides/lsst/ch02sec01.html"]http://www.freeos.com/guides/lsst/ch02sec01.html
[/URL]
as a guide.

The problem I've encountered is that when the script runs the 'sudo -i' command, the script appears to go to a 'rooted' terminal line (Hope that made sense) and cease processing, cuasing you to have to exit from the 'rooted' login back to my own one.

This is my output (the script is called first, mainly because its my first script)

> maddave@maddave-mwuhahaha:~/Desktop$ ./first
bash: ./first: Permission denied
maddave@maddave-mwuhahaha:~/Desktop$ chmod 755 first
maddave@maddave-mwuhahaha:~/Desktop$ ./first
Password:
root@maddave-mwuhahaha:~# exit


I'm gonna keep working on it dude, I'll report back with any success I have.

---

### Post by thelostsoul on 2006-12-16
Try "sudo su -c [command]"

EDIT:

What I mean is:
sudo killall esd
sudo su -c "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss"
exit
et

---

### Post by russell.h on 2006-12-19
start a bash script with:
```
#!/bin/bash
```
That tells the computer its a bash script.

---

### Post by russell.h on 2006-12-19
Oops, sorry I misread that. Nevermind that then... :-#

---

### Post by ZERO_SHIFT on 2006-12-24
So is it something like this:

#!/bin/bash
sudo killall esd
sudo su -c "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss"
exit
et

---

### Post by Milky Way on 2006-12-29
I'm having the same problem when running ET.

the with the script from ZERO_SHIFT this:

> Unknown id: 0

gets printed in the terminal, it looks like it's coming from the:

> sudo su -c "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" 

line.

typing the commands in the terminal gets the sound working.

EDIT:

using the solution provided in this topic:
[http://ubuntuforums.org/showthread.php?t=77217](http://ubuntuforums.org/showthread.php?t=77217)

> **sinbad782 said:**
> Note to others: have managed to fix this. I took two steps:
2.) Fix sound by adding settings to startup scripts:

To fix the sound problems, add the following three lines to your /etc/init.d/bootmisc.sh file:

#-----------------------
# fix sound for Quake 3 and Enemy Territory
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
#------------------------



Finally, reboot and you're done. Don't forget to adjust the shortcuts in your menus to point to the new Quake 3 binary (usually at /usr/local/games/quake3/linuxquake3 )

I got the sound working, without the use of a script to start et.

---

### Post by dbbolton on 2007-01-19
you have to 'chmod +x' before running a shell script

---

