---
title: "[SOLVED] ICEauthority error"
date: 2008-10-16
forum: Desktop Environments
---

### Post by JakeWatkins on 2008-10-16
Could not update ICEauthority file /home/jake/.ICEauthority

Is the error I get every time I boot up.. and it doesn't let me log on until I hit "OK"

---

### Post by aysiu on 2008-10-16
Boot into recovery mode and choose to drop to a root shell. If you don't know how to do that, check out the first half of [this tutorial](http://psychocats.net/ubuntu/resetpassword).

Then type ```
chown jake:jake /home/jake/.ICEauthority
chmod 644 /home/jake/.ICEauthority
exit
``` and resume the normal boot. That should fix it.

---

### Post by aysiu on 2008-10-16
I don't know for certain, but it's possible that running a graphical application with *sudo* (instead of *gksudo*) might have messed up your .ICEauthority file. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Sohlman on 2008-12-02
Hi, I have some sort of the same problem.
First i got this message.> "User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."
 then i did```
sudo chown user:user /home/user/.dmrc
chmod 644 /home/calle/.dmrc
sudo chown -R calle /home/calle
```Then when i restarted the computer i got> Could not update ICEauthority file /home/calle/.ICEauthority. and >  **"Norwegian"** Det er problemer med konfigurasjonstjeneren. (/usr/lib/libgconf2-4/gconf-sanity-check-2 avsluttet med status 256)  
**"English"** There is a problem with the configurationservice. (usr/lib/libgconf2-4/gconf-sanity-check-2 ended with state 256)
There is only one option "exit", after that i only see a blue screen and my mouse. i could press CTRL-ALT-F3 to open console login, i enter uername and password and im in the desctop console/terminal, but don't know what write after that...

So pleas any help i cant use the computer, now im using a second pc to find the solution. and also pleas say what information you need to help me fix the problem.

---

### Post by kinemagician on 2009-01-05
I have exactly the same problem described by Sohlman....

---

### Post by SvenRieke on 2009-11-08
> **Sohlman said:**
> There is only one option "exit", after that i only see a blue screen and my mouse. i could press CTRL-ALT-F3 to open console login, i enter uername and password and im in the desctop console/terminal, but don't know what write after that...


I have the same problem suddenly with my new Karmic, first the .ICEauthority message, then the usr/lib/libgconf2-4/gconf-sanity-check-2 one.
My Gnome session isn't able to boot up correctly.

Tried to remove the .ICEauthority file, like mentioned in another thread, but that doesn't help.

I fix the problem at least for one session with:
[LIST]
[*]**Ctrl-Alt-F1** to enter a shell (login, password)
[*]**sudo service gdm restart** to relaunch the desktop, now everything works fine.
[/LIST]

But during the next boot-up, I get the same errors again.

---

### Post by Delvien on 2009-11-09
same error here. unable to find a work around so far.

---

### Post by zamarax on 2009-11-12
I'm also experiencing the same error in Karmic, it looks as though an update may have broken it, has anyone found a fix?

---

### Post by Revan13 on 2009-11-13
Me too, exactly the same, but the chown did not help me :(

---

### Post by AlexDudko on 2009-11-13
Same problem here. chown chmod helped in one case (home partition wasn't encrypted) but didn't do the trick with the box with encrypted one. Both computers aren't mine (my friends') but they say they installed and updated some packages. They both installed some themes but don't remember which. One of them also installed some dictionaries and changed login language.

---

### Post by Sorrin on 2009-11-14
I had the same error, and was able to fix it using the instructions shown above (changing the folder permissions to 644).
 
Another option is to log in as root, remove the user that generates this error, and create a new user...

---

### Post by orawax on 2009-11-30
It seems that automatic login is currently broken in Karmic.

I had a recurring problem with .ICEauthority but couldn't figure out when it started. Then I enabled automatic login also in my laptop, and got the same problem there. So I disabled autologin and since then the error's gone.

---

### Post by semasont on 2009-12-01
> **aysiu said:**
> I don't know for certain, but it's possible that running a graphical application with *sudo* (instead of *gksudo*) might have messed up your .ICEauthority file. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

had the same problem. think you're right, because yesterday I started KlamAv (KDE -.-) in Console with:

```
sudo klamav
```

After reboot (for other reason) I got the .ICEauthority error.

Unfortunately I didn't recognize the logs in console while starting KlamAV....

Thanks to aysiu, this solution worked fine for me :)

---

### Post by technicallygeek on 2009-12-02
:D
```
chown jake:jake /home/jake/.ICEauthority
chmod 644 /home/jake/.ICEauthority
exit
``` 

This seemed to fix the error I was receiving about profile updates. I just logged in as root (yes I know [-X ) issued the command logged out and logged back in under my user account and no error message ;)

---

### Post by coyotepod on 2009-12-06
tried the chown and chmod methods as root did not work for me either, nor did deleting the .ICEauthority file. still searching...

I did some sudo stuff in the last couple days (never rebooted) then recently updated packages (12/5/09), rebooted and got the double ICE / gmd error messages :-(

---

### Post by Kobalt on 2009-12-08
Same problem here unfortunately. First error message :
> Could not update ICEauthority file /home/kobalt/.ICEauthority
And then:
> (usr/lib/libgconf2-4/gconf-sanity-check-2 has quit with state 256)
After this I get an error that Nautilus cannot create the following folders : /home/kobalt/Desktop and /home/kobalt/.nautilus
At this point nothing else happens, the systems stops displaying an empty wallpaper and doesn't load anything else.

---

### Post by Kobalt on 2009-12-08
OK, my problem is solved : I had changed my account password and didn't modify my encrypted /home passphrase. It's now done, and all is working great again. FYI

---

### Post by leapfrog7 on 2009-12-12
Just to give some input, the only problem I had was the:

Could not update ICEauthority file

I did not boot in recovery mode, but I did the chown and chmod codes and it fixed it for me. I did enter them as root user also. Hope you all can fix yours

---

