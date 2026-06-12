---
title: "Mysterious file?"
date: 2011-03-29
forum: Desktop Environments
---

### Post by gusteman on 2011-03-29
Hi there,
spending time scrolling through the filesystem I came up with this file:
[COLOR="Red"]file system/var/log/lastlog    285,4KB    type:unknown[/COLOR]
First of all I checked it out with ClamAv which indicated no virus found.
Then I tried to open it with Gedit, in vain
Anyone has any idea about the origin of this file? :confused:
Tks

---

### Post by gabefair on 2011-03-30
Could you open the file and provide us with some of the insides?
We might be able to help if there was some more infomation.

-Gabe

---

### Post by Enigmapond on 2011-03-30
No need to worry...1. you will never see a virus in Ubuntu...so , there really is no need for Clamav and 2. This is just a log of the last login.

[http://manpages.ubuntu.com/manpages/hardy/man8/lastlog.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/lastlog.8.html)

---

### Post by matt-fender on 2011-03-30
My filesystem has the same file, i opened it with Gedit and it asks me:

" Are you sure you are not trying to open a binary file? "

This is probably just a system log, unless it's causing you harm I'd leave it well alone :)

[http://ubuntuforums.org/showthread.php?t=956704](http://ubuntuforums.org/showthread.php?t=956704)

---

### Post by gusteman on 2011-03-31
matt-fender wrote: > This is probably just a system log, unless it's causing you harm I'd leave it well alone
I wouldn't know if it's causing harm. I only noticed that since March 24 I have no more log-in screen when I start up Ubuntu. I had the same problem with Hardy on my other HD (/dev/sdb1), although I did not look for that lastlog file, so I'm unable to tell you if it was there or not. Yesterday I reformatted that disk and installed Lucid 10.04.2 on it. There I have also this "lastlog" file, dated on March 30, which seems ok. I also have my login screen working as it should.
But the "lastlog" on my first HD (/dev/sda1) is dated March 27, even after I closed and re-opend Lucid numerous times between March 27 and now. So it seems to me that this can hardly be a log of my last login seeing this lastlog file is dated March 24.
Enigmapond wrote: > you will never see a virus in Ubuntu...so , there really is no need for ClamavI am aware of that, but, first of all, I used ClamAv because, when trying to open the file, this was the first suggestion the system gave me. Secondly, the fact that the file does not react on any attempt to open it, plus that is does not seem to be a log from the last login, I was thinking more in the direction of phishing or hijacking.
I tried to open the file in the terminal and came up with the following:
> gusteman@gusteman-desktop-2:/var/log$ ls -a
.              daemon.log.2.gz  faillog         mail.info              pm-powersave.log.3.gz  user.log.1
..             daemon.log.3.gz  fontconfig.log  mail.info.1            pm-powersave.log.4.gz  user.log.2.gz
acpid          daemon.log.4.gz  fsck            mail.info.2.gz         pycentral.log          user.log.3.gz
apparmor       debug            gdm             mail.info.3.gz         samba                  user.log.4.gz
apt            debug.1          installer       mail.info.4.gz         scrollkeeper.log       wtmp
auth.log       debug.2.gz       jockey.log      mail.log               scrollkeeper.log.1     wtmp.1.gz
auth.log.1     debug.3.gz       jockey.log.1    mail.log.1             scrollkeeper.log.2     wvdialconf.log
auth.log.2.gz  debug.4.gz       kern.log        mail.log.2.gz          speech-dispatcher      Xorg.0.log
auth.log.3.gz  dist-upgrade     kern.log.1      mail.log.3.gz          syslog                 Xorg.0.log.old
auth.log.4.gz  dmesg            kern.log.2.gz   mail.log.4.gz          syslog.1               Xorg.1.log
boot           dmesg.0          kern.log.3.gz   mail.warn              syslog.2.gz            Xorg.1.log.old
boot.log       dmesg.1.gz       kern.log.4.gz   messages               syslog.3.gz            Xorg.2.log
bootstrap.log  dmesg.2.gz       landscape       messages.1             syslog.4.gz            Xorg.3.log
btmp           dmesg.3.gz       lastlog         messages.2.gz          syslog.5.gz            Xorg.4.log
btmp.1.gz      dmesg.4.gz       lpr.log         messages.3.gz          syslog.6.gz            Xorg.5.log
clamav         dpkg.log         lpr.log.1       messages.4.gz          syslog.7.gz            Xorg.failsafe.log
ConsoleKit     dpkg.log.1       lpr.log.2.gz    news                   udev
cups           dpkg.log.2.gz    lpr.log.3.gz    pm-powersave.log       ufw.log
daemon.log     dpkg.log.3.gz    lpr.log.4.gz    pm-powersave.log.1     unattended-upgrades
daemon.log.1   dpkg.log.4.gz    mail.err        pm-powersave.log.2.gz  user.log
gusteman@gusteman-desktop-2:/var/log$ edit lastlog
Warning: unknown mime-type for "lastlog" -- using "application/octet-stream"
Error: no write permission for file "lastlog"
gusteman@gusteman-desktop-2:/var/log$ 
 So, if this lastlog file is part of the system, it seems quuite strange that the system cannot open it :confused:
Anyone has any suggestions to open this file?
Tks for coop

---

### Post by Karlchen on 2011-03-31
Hello, gusteman.

The file **/var/log/lastlog** is not a plain text file. Therefore trying to read it using a text editor is of little use.
The file **/var/log/lastlog** can be inspected with the help of the programme **lastlog**.
For more details on **lastlog**, please, launch **man lastlog**.

Kind regards,
Karl

---

### Post by gusteman on 2011-03-31
Hi there Karlchen,
thanks for the hints.
As a matter of fact I succeeded in opening the **lastlog** file.
But strangely it came up with a weird output: according to the **lastlog** file **I never logged in** ! Nor did any of my programs !
It looks like my PC never has been used before, and not even now too !
Very strange indeed.
If it is a file that is supposed to show every log-in they should at least be traceable, no?
I will keep this post open for the next few days, and if I don't get any solutions on this problem I will mark it as "solved".
See you all later, guys !

---

### Post by matt-fender on 2011-03-31
> **gusteman said:**
> matt-fender wrote: 
I wouldn't know if it's causing harm. I only noticed that since March 24 I have no more log-in screen when I start up Ubuntu. I had the same problem with Hardy on my other HD (/dev/sdb1), although I did not look for that lastlog file, so I'm unable to tell you if it was there or not. Yesterday I reformatted that disk and installed Lucid 10.04.2 on it. There I have also this "lastlog" file, dated on March 30, which seems ok. I also have my login screen working as it should.
But the "lastlog" on my first HD (/dev/sda1) is dated March 27, even after I closed and re-opend Lucid numerous times between March 27 and now. So it seems to me that this can hardly be a log of my last login seeing this lastlog file is dated March 24.
Enigmapond wrote: I am aware of that, but, first of all, I used ClamAv because, when trying to open the file, this was the first suggestion the system gave me. Secondly, the fact that the file does not react on any attempt to open it, plus that is does not seem to be a log from the last login, I was thinking more in the direction of phishing or hijacking.
I tried to open the file in the terminal and came up with the following:
 So, if this lastlog file is part of the system, it seems quuite strange that the system cannot open it :confused:
Anyone has any suggestions to open this file?
Tks for coop




[http://askubuntu.com/questions/22528/why-does-lastlog-show-every-user-as-never-having-logged-in](http://askubuntu.com/questions/22528/why-does-lastlog-show-every-user-as-never-having-logged-in)



     
 
                                Login via gdm is not logged in lastlog. In this respect ck-history --last might give you more information.
  To test this, go to a console (Ctrl+Alt+F1), log in, then come back to Gnome (Alt+F7) and check the output of lastlog.

---

### Post by gusteman on 2011-04-01
Hi there, Matt-Finder, thanks for the assistance.
As you suggested I performed (Ctrl+Alt+F1), logged in, and there it went wrong: (Alt+F7) didn't react, nor did any other combination so I performed (Ctrl+Alt+Del) and re-booted.
However, after loggin in I got this message:
System information disabled due to load higher than 1.
Does this mean anything to you?
After re-boot I checked lastlog and there it was: my login as you predicted.
Thanks already for that.
Now the problem of (Alt+F7) not reacting.
Any suggestions on that?
Greetings, gusteman
I noticed that, after having logged in through (Ctrl+Alt+F1) my CPU-usage dropped from 100% to 10%. ???

---

### Post by matt-fender on 2011-04-01
> **gusteman said:**
> Hi there, Matt-Finder, thanks for the assistance.
As you suggested I performed (Ctrl+Alt+F1), logged in, and there it went wrong: (Alt+F7) didn't react, nor did any other combination so I performed (Ctrl+Alt+Del) and re-booted.
However, after loggin in I got this message:
System information disabled due to load higher than 1.
Does this mean anything to you?
After re-boot I checked lastlog and there it was: my login as you predicted.
Thanks already for that.
Now the problem of (Alt+F7) not reacting.
Any suggestions on that?
Greetings, gusteman
I noticed that, after having logged in through (Ctrl+Alt+F1) my CPU-usage dropped from 100% to 10%. ???


I just tried to reproduce the problem, but ALT-F7 is working flawless for me, to get back to my session. Perhaps it might be a good idea to start a new thread for that? I actually think a friend of mine has the same problem, so a thread might be a good start.
Regards, Matt

PS: Just a quick thought however, are you on a laptop/netbook? if so try Ctrl-Fn-Alt-F7 or Fn-Alt-F7 to return to GUI.

---

### Post by gusteman on 2011-04-02
matt-fender wrote> PS: Just a quick thought however, are you on a laptop/netbook? if so try Ctrl-Fn-Alt-F7 or Fn-Alt-F7 to return to GUI. Nope, I'm on a regular desktop machine, so the notebook approach is not an issue.
Anyway, apart from the Alt-F7 problem, I got what I wanted: the lastlog file has no more mysteries for me.
Thanks to everyone for the helpfull interveniences.
Once again the Ubuntu Community proved being a wonderfull way of life.
See you later guys :D

---

