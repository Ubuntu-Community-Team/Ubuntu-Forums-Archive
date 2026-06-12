---
title: "Login Failure After Logout"
date: 2006-06-24
forum: Desktop Environments
---

### Post by el33tcapitan on 2006-06-24
After I log out of my current Gnome session, if I try to log right back in (or wait and try to log back in) without a restart, Gnome will hang and will never load the windows manager or nautilus or anything.

Any ideas?

---

### Post by bscbrit on 2006-06-24
No - not yet!
Are there any error indications?  Have you looked in the logs (/var/logs/) for any clues?  Can you get to the command line?  Can you boot up in recovery mode?
What _exactly_ do you see during a boot sequence that eventually fails? At what point does it fail?

---

### Post by el33tcapitan on 2006-06-24
I don't see anything. It just goes to the orange screen and nothing happens (orange screen being that which shows up before everything loads up). This is after I type in my login and password.

I also can't reach the command line. I will try to boot in recovery mode to see if that will work.

---

### Post by el33tcapitan on 2006-06-24
Failsafe Gnome does not work either. Exactly what happens (or doesn't happen, rather) is that the splash screen for Ubuntu that shows the lilttle icons for the Windows Manager and Nautilus, etc. never shows. As a result I never have a fully loaded desktop environment and I cannot run any commands or open any programs. Again, this happens only once I've logged out once without restarting my computer.

---

### Post by bscbrit on 2006-06-24
OK, I'm a little confused by your reply.  The recovery mode will **not** get you back to a graphics display.  It **will** get you back into your computer at the command line and you can then check your logs (/var/log/) for any clues as to what the problem is.  Once we know what is causing the problem we can set about fixing it.  Otherwise, you either accept that you have to reboot each time, or you re-install because something is not quite right.  However, 99% of problems can be fixed from the command line using the expertise that various people on this forum have.  

If you are not comfortable using the command line then simply ask for more help, or re-install and try again. :-D

---

### Post by el33tcapitan on 2006-06-24
Which log am I looking for? There are many in the /var/log/ area.

Do I have to be in recovery mode to find the log that we are looking for, because I can access plenty of them from Gnome?

---

### Post by ifokkema on 2006-06-24
[QUOTE=el33tcapitan]Which log am I looking for? There are many in the /var/log/ area.

Do I have to be in recovery mode to find the log that we are looking for, because I can access plenty of them from Gnome?[/QUOTE]
In /var/log there are lots of system logs. But if Gnome logs you in, but hangs, something may be in your ~/.xsession-errors. You don't have to boot in recovery mode to look at that file. When it hangs, press Ctrl-Alt-F1 to go to your console. There, log in, and take a look at that file
```
less .xsession-errors
```
because it'll be overwritten next time you log in, copy the file so you can paste the contents after a succesfull login.
Copying the file:
```
cp .xsession-errors xsession-errors.txt
```
Getting back to your graphical interface: Ctrl-Alt-F7.
Maybe also useful: restarting the X server (HARD restart) Ctrl-Alt-Backspace.

---

### Post by bscbrit on 2006-06-25
You are correct that there are lots of different logs and knowing which one to look at is a problem.

When investigating problems, you will find plenty of useful information in dmesg, syslog, Xorg.log and others.  There are also logs for specific applications.  But knowing which one to look at depends on the nature of the fault that you are trying to pin down.

ifokkema gave you some good advice when looking for gnome specific problems.  From your description of the fault I could not tell what kind of problem exactly you were experiencing. "Gnome will hang and will never load the windows manager or nautilus or anything" still left me unsure as to what you were seeing on the screen.  For example, were you being prompted for your login ID and password?  Was gnome itself being corrupted by your previous log-out?  I was trying to pin down exactly where the problem was.

As you have not returned for 18 hours or so, I assume that you have solved the problem.  If so, well done!  If not, let me or someone else know how you are faring and I am sure someone will try to assist.

Good luck.

---

### Post by andril on 2006-06-25
Same issue - all I did was go inti KDE then log out and go into XFCE - I restarted the PC due to bad weather and the GNOME desktop will not load. I see the spash screen loads 3 icons, and then just the a blank screen. ](*,)  This really sucks! Can someone resolve this I can get in still with KDE & XFCE - Please help us. Thanks In Advance!


Correction to myself - XFCE has it's issues also

---

### Post by el33tcapitan on 2006-06-25
I don't even get the splash screen.

Here's the readout from the file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "eladmiral"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ElAdmiral:/tmp/.ICE-unix/6038

---

### Post by ifokkema on 2006-06-25
[QUOTE=el33tcapitan]I don't even get the splash screen.

Here's the readout from the file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "eladmiral"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ElAdmiral:/tmp/.ICE-unix/6038[/QUOTE]

My .xsession-errors continues after these lines with this:
```
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
```
(etc, etc)

Anyone knows where this manager.c is from?

---

### Post by andril on 2006-06-25
[QUOTE=ifokkema]My .xsession-errors continues after these lines with this:
```
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
```
(etc, etc)

Anyone knows where this manager.c is from?[/QUOTE]


Wow this must be a bug - since the problems are similar - what can we do? ](*,) Are we looking for a reinstall?

---

### Post by ifokkema on 2006-06-26
[QUOTE=andril]Wow this must be a bug - since the problems are similar - what can we do? ](*,) Are we looking for a reinstall?[/QUOTE]

Hmm... I now have the same problem :)

Just started up my PC and logged in. You saw Ubuntu notifying me of the services which are being started, but after that only my desktop wallpaper showed up and my mouse pointer - nothing else. No keyboard shortcuts where working either. Killed X using Ctr-Alt-Backspace, tried logging in and guess what - just got the screen color (brownish), no wallpaper, no notification of services starting up... Rebooted, now it's fine.

This is a clean Dapper install.

---

### Post by el33tcapitan on 2006-06-26
That's what I get every time I log out and try to log back in: just the screen color with no wallpaper or notification services starting up.

---

### Post by Aryxa on 2006-07-03
I just installed 6.06 and it automatically updated. When I had to reboot, I logged in and I got a black screen with only a mouse pointer. 

I have tried 10 reboots and it happens again. I can only log i with fail safe gnome.

Any Ideas? Seems to be the updates?

---

### Post by ifokkema on 2006-07-03
[QUOTE=Aryxa]I just installed 6.06 and it automatically updated. When I had to reboot, I logged in and I got a black screen with only a mouse pointer. 

I have tried 10 reboots and it happens again. I can only log i with fail safe gnome.

Any Ideas? Seems to be the updates?[/QUOTE]
If you try the normal Gnome session, check out the .xsession-errors in your home directory. How to do that is described here:
[http://www.ubuntuforums.org/showpost.php?p=1178030&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1178030&postcount=7)

---

### Post by Aryxa on 2006-07-03
[QUOTE=ifokkema]If you try the normal Gnome session, check out the .xsession-errors in your home directory. How to do that is described here:
[http://www.ubuntuforums.org/showpost.php?p=1178030&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1178030&postcount=7)[/QUOTE]

I fixed it. I went into failsafe and into synatic and it said some file was corrupted, and it told me to ```
dpkg --configure -a
``` I did just that and it is fixed :)

I was so close to putting breezy back on!

---

### Post by ifokkema on 2006-07-03
[QUOTE=Aryxa]I fixed it. I went into failsafe and into synatic and it said some file was corrupted, and it told me to ```
dpkg --configure -a
``` I did just that and it is fixed :)[/QUOTE]
This means that an install or upgrade did not complete and was interrupted by something.

[QUOTE=Aryxa]I was so close to putting breezy back on![/QUOTE]
This is an example of a problem that can occur on Breezy just as easy. My dad also gives up on a distribution very easily, even when running in to trivial problems. Sometimes a problem seems huge, even if it can take just a minute or so to get it fixed again.

---

