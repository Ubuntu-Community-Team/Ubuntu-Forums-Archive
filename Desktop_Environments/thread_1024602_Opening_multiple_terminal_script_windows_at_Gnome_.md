---
title: "Opening multiple terminal script windows at Gnome bootup as root with gksudo &amp; script"
date: 2008-12-29
forum: Desktop Environments
---

### Post by feizex on 2008-12-29
Hi Guys,

I am still new to linux. I found a way to Open multiple terminal script windows at bootup while only having to type in password once.

You may wonder why I want to do this. Well I have a few scripts to monitor my asterisk server and they all need to run as root so they contain sudo. The thing is that A) I had trouble getting them to run in the first place and B) I only wanted to type in password once.

Here is my solution. This will help other novices like me. Maybe you have more sophisticated means.

Create new file startup.sh on desktop. Right click properties > Permissions and make it executable. Paste in the following lines.
gnome-terminal -x Desktop/script\ name\ 1.sh&
gnome-terminal -x Desktop/script\ name\ 2.sh&
gnome-terminal -x Desktop/script\ name\ 3.sh&

This script is going to run your 3 scripts on your desktop called "script name 1.sh" and 2 & 3. The & at the end is so that they spawn as background processes, otherwise you would have to close the first window before the 2nd would open etc.

They may contain sudo commands in them. That's OK because we're going to start them with gksudo so they won't ask for a password. In fact I tested taking sudo out of the scripts and that works OK too seeing as they are run with root access when they are called. I kept sudo in my scripts seeing as I also want to run them manually at other times.

Go to System > Preferences > Sessions
Startup Programs Tab > Add button

Here is the command you're going to run:
gksudo Desktop/startup.sh

Now when you reboot and log in, gksudo will popup a window asking for password. After that it will spawn 3 windows each running one of your scripts in it!

Regards,
Feizex. :popcorn:

---

### Post by masam on 2010-01-31
if you would like for this script to run at boot up WITHOUT having to type a password, her are the steps to take:

1)open Terminal.
2)"cd /etc" (without the quotes)
3)"gedit && sudo visudo"
(quit gedit, this will bring you back to the terminal, copy below)

```
#Bug: https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/30291
# https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/47662
#Defaults !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"
```

paste this over top of what may already be there.

at the end of the file, insert this line:

```
username ALL= NOPASSWD: /home/%user/Desktop/startup.sh
```

the %user will be your username/home.

hit Control + o to write the file, but make sure you save it as "sudoers" and not "sudoers.tmp".
hit Control + x to exit.

4)continued from previous Howto:

> Go to System > Preferences > Startup Applications > Add button

Here is the command you're going to run:
sudo /home/%user/Desktop/startup.sh

the only change to feizex's quote is the "sudo" instead of "gksudo" and the full path to the working script.

5)reboot.
6)enjoy!(hope this helps)

---

