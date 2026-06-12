---
title: "Cannot start X"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Sutekh on 2005-11-09
My issue came about after using KDE (installed alongside with GNOME) for the second time.  The only things of consequence that I did were to change the menu bar/window themes a bit.  After logging out of KDE and trying to log into GNOME, all I get is the brown screen, with occasional flashing of the panels, and then nothing.  I could Alt+Ctl+Backspace and log into KDE or the Failsafe Terminal, where 'startx' gives the following error:

```

xauth: creating new authority file /home/user/.serverauth.9801
x: warning; process set priority -1 instead of requested priority 0
Fatal server error:
        Server is already active for display 0,
        If this server is no longer running, remove /tmp/.X0-lock and start again

```

I checked out [http://wiki.x.org/wiki/FAQErrorMessages]("http://wiki.x.org/wiki/FAQErrorMessages")
and removed the .X0-lock file.

After that I could log into GNOME using sudo startx from the terminal, but not from the log in greeter.  If I try to log in from the greeter I now get a warning box saying my session was only 10 seconds long or something and in ~/.xsession-errors this is displayed
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "user"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir	:ERROR: euid ~=0, directory /dev/X will not be created
_IceTransmkdir	:ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir (/dev/X) failed, errno=13
_IceTransOpen: transport open failed for 'pts/ubuntu'
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC Connection
_IceTransOpen: transport open failed for 'isc/ubuntu'
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for 'sco/ubuntu'
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

```

and then back to the log in screen we go.

I also checked out /var/log/Xorg.O.log for errors but only found some warnings (I clipped the rest out)
```

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist. Entry deleted for font path
(WW) The directory "/usr/share/X11/fonts/CID" does not exist. Entry deleted for font path
(WW) 'fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID" Entry deleted
	(Run "mkfontdir" on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
(WW) Open APM failed (/dev/apm_bios) (no such file or directory)
(WW) Ignoring request to load module GLcore
(WW) (1600x1200, 17 TFT-LCD) mode clock 162 MHz exceeds DDC maximum 140 MHz
(WW) (1400x1050, 17 TFT-LCD) mode clock 151 MHz exceeds DDC maximum 140 MHz
(WW) (1680x1050, 17 TFT-LCD) mode clock 147.14 MHz exceeds DDC maximum 140 MHz
(WW) (1920x1200, 17 TFT-LCD) mode clock 193.16 MHz exceeds DDC maximum 140 MHz
(WW) NVIDIA(0) Not using mode "960x600" (height 1200 is larger than EDID specified maximum 1024	
(WW) NVIDIA(0) Not using mode "800x600" (height 1200 is larger than EDID specified maximum 1024	
(WW) NVIDIA(0) Not using mode "840x525" (height 1200 is larger than EDID specified maximum 1050	
(WW) NVIDIA(0) Not using mode "700x525" (height 1200 is larger than EDID specified maximum 1050	
(WW) NVIDIA(0) Not using mode "700x525" (height 1200 is larger than EDID specified maximum 1050	
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
(WW) Open APM failed (/dev/apm_bios) (no such file or directory)

```

I also did 
```

sudo dpkg-reconfigure xserver-xorg

```

but that had no change.  I have no clue what to do with all this.  I can still start a root session of GNOME from the failsafe terminal and KDE, but not GNOME.  :-k
Can anyone suggest something else to do??  
Muchly appreciated!!

---

### Post by Remmelas on 2005-11-09
you say you can start gnome using sudo from the cammand line, but can you do it without using sudo?  also, just to be sure, use from the command line sudo /etc/init.d/gdm stop to make sure there are no other sessions running when you try to start X from the command line.

---

### Post by Sutekh on 2005-11-09
I did try startx from the command line without sudo, and I got something to the effect of 'you don't have permission to start x' (off the top of my head).

I did try sudo /etc/init.d/gdm start, but I guess I should have tried sudo  /etc/init.d/gdm stop first.  Thanks! I'll give that a try.

---

### Post by Juzz on 2005-11-09
I also had the problem with Gnome and the less than 10 secs session shortly after upgrading to Breezy.
I found out that it was one of my . files in my home dir that had owner set to root:root instead of "my user":"my user".
After a quick sudo chown veggerby:veggerby . I could start up again - you could try this:
sudo chown -R "your user":"your user" /home/"your user"

---

### Post by Sutekh on 2005-11-09
[QUOTE=Juzz]I also had the problem with Gnome and the less than 10 secs session shortly after upgrading to Breezy.
I found out that it was one of my . files in my home dir that had owner set to root:root instead of "my user":"my user".
After a quick sudo chown veggerby:veggerby . I could start up again - you could try this:
sudo chown -R "your user":"your user" /home/"your user"[/QUOTE]

Yes I did remeber seeing something about permission denied on something like /home/user/.ICEauthority, perhaps that's the cause..

What does the "user:user" part of the chown call do? I've never seen that before.  And thanks for the input!!

---

### Post by Remmelas on 2005-11-09
[QUOTE=Sutekh]
What does the "user:user" part of the chown call do? I've never seen that before.  And thanks for the input!![/QUOTE]
before the colon is the user, after is the group.

chown -R mike:users /home/mike
for example would change all the files in the /home/mike directory to be owned by the user 'mike', and the group 'users'

ubuntu uses one group per user, so in ubuntu i would do chown -R mike:mike /home/mike

---

### Post by Sutekh on 2005-11-09
Ahh no need for chgrp which is what I would have used before.
  
Still a couple of hours till I can give these ideas a try, but its nice to work up a list to check-off as I go.

---

### Post by Sutekh on 2005-11-10
Ok using sudo /etc/init.d/gdm stop from the failsafe terminal goes to a black screen where I log on.  Then sudo /etc/init.d/gdm start flashes between the command line and what I guess is the start up screen.

Changing permissions in my home folder got rid of the 10 second session window, when trying to log in from the graphical greeter, but after that I'm back to the brown screen with the flashing panels.

So I don't know whats going on at all.

I tried the following command (from the xorg wiki)
```

ps aux | grep 'cat /tmp/.X0-lock'

```

it returns the following
```

user     10224  0.0  0.0   3064   764 pts/1    R+   20:36   0:00 grep cat /tmp/.X0-lock

```
so I guess that means that another session of X is running, right?

If I press Alt+Ctl+F8 the screen switches to another screen that has what looks like a loading screen.  Could this be the culprit?

---

### Post by Sutekh on 2005-11-10
Ok I read somewhere that if the output of

```

ps ax | grep X
```
and 
```

cat /tmp/.X0-lock
```

give the same PID then the lock file is valid, and there is definately another session started.  Which is the case for me.

But no matter how I stop this session, it is always there even after a reboot.  What could be the cause?  Incidentally if I create another user, there is no issue logging in.

---

### Post by Juzz on 2005-11-10
[QUOTE=Sutekh]But no matter how I stop this session, it is always there even after a reboot.  What could be the cause?  Incidentally if I create another user, there is no issue logging in.[/QUOTE]
OK, that definitely points to something fishy in your homedir.

Did you try the chown command on your homedir yet?

---

### Post by Sutekh on 2005-11-10
Yes and no.. I didn't want to change the permissions of anything that really should be owned by root, so I only changed the permissions for /home/user/.ICEauthority because it was mentioned in .xsession-errors.  That got rid of the 10 second session window, but not the issue with the brown screen and flashing panels. 

Now I'll just change everything in my home folder and cross my fingers..

---

### Post by Juzz on 2005-11-10
Anything in your home folder should really be owned by you - I just think that it is a minor slip from the system when updating some of your packages.

Anyways it should be quite safe for you to do the chown on your own home dir ;)

---

### Post by Deekin on 2005-11-10
[quote=Juzz]Anything in your home folder should really be owned by you - I just think that it is a minor slip from the system when updating some of your packages.

Anyways it should be quite safe for you to do the chown on your own home dir ;)[/quote]

Agreed - I had the same kind of hiccup happen to me a bit ago - chowning your home dir will be fine and should resolve the issue :)

---

### Post by Sutekh on 2005-11-10
[QUOTE=Deekin][QUOTE=Juzz]
Anything in your home folder should really be owned by you - I just think that it is a minor slip from the system when updating some of your packages.

Anyways it should be quite safe for you to do the chown on your own home dir [/QUOTE]

Agreed - I had the same kind of hiccup happen to me a bit ago - chowning your home dir will be fine and should resolve the issue :)[/QUOTE]

OK thanks guys, time to reclaim my home.

---

### Post by Sutekh on 2005-11-12
Well I chowned my home folder but I still can't log into GNOME with my user.  

On Alt Ctl F8 there is still a loading screen, so I'm thinking there must be some startup script or something that tries to load GNOME, which creates a lock.  Which is why I can log onto KDE under my original user, or GNOME with a new user or root.  After every reboot, ownership change and deletion of lock file, the loading screen is always there.  If something was trying to start GNOME, where would I find it?

---

### Post by Sutekh on 2005-11-12
Ok as far as I can tell when my PC starts up, it tries to start the GDM on console 8 (or vt8 or tty8 or whatever it is called).  It seems to also want to log in using my original user, which creates that stupid .X0-lock file.  So I can't log into GNOME on console 7 (vt7, etc) unless I use a different user.  Alternatively I can log into KDE or the Failsafe terminal.  I'm pretty sure that's whats happening.  

The GDM that is trying to start on console 8 is frozen, so how do I kill it? Alt Ctl Backspace has no effect.  And how do I stop it trying to start up each time my PC turns on?

---

