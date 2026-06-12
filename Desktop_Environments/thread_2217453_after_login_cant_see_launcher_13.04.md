---
title: "after login cant see launcher 13.04"
date: 2014-04-17
forum: Desktop Environments
---

### Post by wadafjeubu on 2014-04-17
Hi all, After I start up my PC and booted ubuntu 13.04, my user logs in automatically and I see the desk top Unity, but not the launcher. I can, for example, not run a terminal to invoke any programs. Can anyone help? What do I need to do?
Right click on the desktop only give my the ability to make change to the screen.

My PC is dual boot, with ubuntu as standard (on a dedicated harddrive) and windows 7 on an other HDD.
Thanks in advance for the help!

regards!

---

### Post by Redalien0304 on 2014-04-17
Ubuntu 13.04 is EOL (End Of Life) & no longer supported. You should upgrade to Ubuntu 13.10 or Ubuntu 14.04 Trusty, which is to be Released Today at some Point. Try this from a terminal Line: sudo apt-get install update-manager-core, then 
sudo do-release-upgrade

---

### Post by wadafjeubu on 2014-04-17
Well, I would like to UPGRADE .. but need to be able to invoke the upgrade program of course. So HOW do I do that!!!!

---

### Post by Redalien0304 on 2014-04-17
Have you tried the Recovery Option? in advanced options in grub boot menu.

---

### Post by wadafjeubu on 2014-04-17
no I did not, but thanks I will check that! Thanks.

---

### Post by grahammechanical on 2014-04-17
There is something to note. If you right click the desktop and select Change Desktop Background, that will open System Settings. A useful thing to know when the problem is with the video driver.

Please confirm that you cannot open the Dash by tapping the windows (super) key. Or that Crtl+Alt+T does not open a terminal. Or, the Ctrl+Alt+F2 does not open a tty.

Another thing to note, when running the Recovery mode if we want to change any system settings will will need to put the file system into read/write mode. And to update/upgrade we will need a both the file system to be in read/write mode and a network connection. So, first select Network and then select Root.

I have never used recovery mode to upgrade to a new version of Ubuntu. It would be an interesting experiment. I might try it out. You will need to reboot

```
shutdown -r now
```

will do it. This command will reset Compiz

```
dconf reset -f /org/compiz/
```

This command will rest Unity

```
setsid unity
```

Try them before trying to upgrade to 13.10. To get out of Root and back to the recovery menu type exit.

Regards.

---

### Post by wadafjeubu on 2014-04-23
Thx all for the help. Unfortunately, the recovery mode did not work. What I did last week when 14.04 came out, I installed that! In doing do (re) created a (new) SU and  a regular user. 

However, my dual boot with Windows 7 is broken: in my boot screen my link to windows 7 is not working; message saying that I need to use the windows 7 dvd to (re)install. But I believe that the issue is the boot .....

Can anyone help to repair that? Thanks a lot again!

regards,

---

