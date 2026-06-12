---
title: "Trying to understand /etc/rc*"
date: 2009-02-25
forum: General Help
---

### Post by poliocough on 2009-02-25
Hey guys, thanks in advance for your time! I have a question about how the /etc/rc*.d machinery works.

My box setup: MacBook 5.1 running Ubuntu 8.10. No significant package changes.

My problem: keyboard backlight is ON by default. It goes on whenever the system comes online, whenever it returns from suspend and whenever i unplug power. I want it to be off by default. I want to learn more about Ubuntu as a side-effect.

My planned approach: add a script into the /etc/rc5.d directory that echoes 0 to the right /sys.. file. I can do this by hand - just want it to happen automatically. My first attempt at this didnt work - so I decided to create a little debugging widget. 

I've created the following general-purpose script in my home directory called "runmark_home". All it does is get the current timestamp and creates an empty "marker file" with the timestamp as the name. 

```
#!/bin/sh
if [ $# -ne 0 ]; then
        NAME=$1
else
        NAME=UNK_RUN
fi
FILENAME=`date +%Y%m%d_%H_%M_%S`
FILENAME="/home/MYUSERNAME/"${FILENAME}_${NAME}
/usr/bin/touch $FILENAME
```

So from my home directory I can do:
```
$ scripts/runmark_home testrun
$ ls 20090225_00_42_04_testrun
20090225_00_42_04_testrun
```
...voila the file is created!

Let's try to get this to be run once every time the system starts up. That should be easy enough... Some random searching, investigation,etc, makes /etc/rc5.d look promising. So here's what I did:

```
$ cat /etc/init.d/samplescript 
#! /bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
/home/MYUSERNAME/scripts/runmark_home samplescript
exit 0
$ ls -l /etc/rc5.d/S99sample 
lrwxrwxrwx 1 root root 24 2009-02-25 00:13 /etc/rc5.d/S99sample -> /etc/init.d/samplescript
```

Problem: no "mark file" appears when I boot the system up. Tried a few times. 

Now my limited knowledge of Linux is probably immediately apparent. I appreciate any advice you may offer:
Why doesn't the file appear?
How can we debug/trace this? Does the script get invoked? What part of the script fails?
How / how else do I go about figuring out keyboard backlight problem (might be a question for mactel)?

Thank you very much!!!

---

### Post by Agent ME on 2009-02-25
This link might be useful: [http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/](http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/)

Sorry that I'm not able to look more into this.

---

### Post by mb_webguy on 2009-02-25
Agent ME's link is nice as a general overview of Ubuntu's init process, but I'm not sure it actually addresses your problem.

Before Upstart, if you wanted to run some script at startup, you'd add it to a file called /etc/rc.local, and while you can technically still do that, the preferred method in Upstart is a bit different.

1) Create a file called /etc/init.d/local, using the command "sudo gedit /etc/init.d/local". This is a shell script, so it should begin with:```
#! /bin/sh
```Add any commands or applications you want to run at startup in the script, then save and exit.

2) Make the script executable using the command "sudo chmod a+x /etc/init.d/local".

3) Add the script to Init using the command "sudo update-rc.d local defaults 80".

You only have to do steps 2 and 3 once.  After that, you just need to edit /etc/init.d/local to change what you're running at startup.

---

### Post by KeyserSoze93 on 2009-02-25
A couple of possible mistakes:
```
#!/bin/bash

bash /home/MYUSERNAME/scripts/runmark_home/samplescript

exit 0

```

This should take care of several issues.

First, though I've read that some versions of Linux accept a hashbang with a space, I have not seen this behaviour in Ubuntu.

Second, adding the directory to the path is perfectly valid, but you would want to put the call to the script on the next line after the space, or put a semicolon.

Since the script needs to had 755 permissions for it to work simply by being called from the PATH, it's simpler just to call bash on it, which eliminates the need for having the PATH setting in there at all.

The last point, I changed sh to bash since many distros now ship with sh and a link to dash so if you want bash, you should call it by name.

---

### Post by poliocough on 2009-03-02
Thanks a lot for the reply guys. Here's an update (didn't get around to this earlier.

Some of the erratums were definitely helpful. The one by Keyser is slightly incorrect:
```
bash /home/MYUSERNAME/scripts/runmark_home samplescript
```
 --"samplescript" is an argument. Minor detail.

I think another thing I didn't understand was the runlevel number. I was under the impression that the system boots up in as follows:
runlevel 0 -> runlevel 1 -> ... -> runlevel 5 

I thought runlevel 5 was the point at which I log in and start using things. Not so. According to my box:
```
[gepard:etc]$ runlevel
N 2

```

So of course my script didn't get invoked because I put it in rc5.d! We learn slowly but surely. After adding my script to rc2.d I got the desired result. 

I am not sure what the other runlevels are used for in Ubuntu and when the system enters them. 

Furthermore, I realize the system does NOT APPEAR to change runlevels on:
- suspend
- resume
- power cord unplug/replug

I need an "entry point" / script that's triggered by these events. Suggestions?
Thank you!

---

### Post by poliocough on 2009-03-07
Still not sure how to get gnome-power-manager to do this...b-bum-bum-bump!

---

