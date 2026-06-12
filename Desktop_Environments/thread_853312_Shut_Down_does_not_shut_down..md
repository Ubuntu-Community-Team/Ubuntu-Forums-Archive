---
title: "Shut Down does not shut down."
date: 2008-07-08
forum: Desktop Environments
---

### Post by Mahinva on 2008-07-08
Since about 2 days ago (equaling maybe 6 computer sessions), Ubuntu will no longer shut down after going through the Quit menu. All icons will be removed from the desktop and all running applications close. The panel I've got set up on the bottom of my screen also closes. Despite this, my computer "hangs up" - it will not finish shutting down. If I hit CRTL+ALT+Backspace, shut down resumes - the default Ubuntu screen kicks in, the progress bar does its thing, and the computer pleasantly shuts down. I have waited, to see if my computer is simply taking a while to respond, however no shut down occurs after a few minutes.

I get no error dialogs, no text whatsoever.

I used to get a wall of text before the shut down would complete, however I didn't have a method of capturing the dialog - no photo taken with camera. This wall of text no longer appears.

What could be the problem?

SOLUTION:

Edit /etc/X11/Xsession.d/55keytouchd_launch and replaced the line

KEYTOUCHLAUNCH=/usr/bin/keytouchd-launch

with

KEYTOUCHLAUNCH="/usr/bin/keytouchd-launch --exit-with-session"

I had to edit the file under the terminal command Sudo Nautilus, or else I could not save the file.

After changing the line, the first time I shut down, I still had to CTRL+ALT+Backspace. Subsequent shut downs or restarts work as intended.

---

### Post by walkerk on 2008-07-08
does shutdown work from the cli?

```
sudo shutdown -h now
```

I believe Gnome uses GDM to send a shutdown message to the system w/ gdm-control ... Curious to see if /sbin/shutdown does the trick.

---

### Post by Mahinva on 2008-07-08
walkerk - Thanks for the quick reply. After typing that code into the terminal, I am prompted to provide my password. After entering my password, the computer does shut down without acting as I had described in my first post.

---

### Post by Mahinva on 2008-07-08
Did some more testing, and shutting down via Quit menu still keeps my computer from shutting down properly. I still have to CTRL+ALT+Backspace.

---

### Post by Mahinva on 2008-07-24
I'm sad to say that this is still occuring.

Interestingly enough, after finally getting rid of my XP partition and reinstalling Ubuntu, shutting down did not hang on a blank desktop - for a day or so.

Once again, I have to ctrl+alt+backspace after clicking "shut down" in order for the computer to shut down. I have added the "Quit" module to my panel, but the results are the same.

---

### Post by Potatoj316 on 2008-07-24
It would be a pain but you could put a link in your panel to a script that runs that shutdown command.  There should be a way to do this though to make it work the way it should.

---

### Post by warp99 on 2008-07-24
You have a program that is hanging the desktop prior to shutdown. A good example is Keytouch since the current version in the repositories does not unload on some machines during logout, but there is a workaround. So I would try this first:

Open a terminal and check this file to see if there are any problems unloading an app prior to shutdown:

```
gedit ~/.xsession-errors
```

Go through the log file and you should see some errors where the 'hangup' occurs when you logout. If there is too much information to 'grep' through you can delete the file and restart you session since a new .xsessions-errors file will be generated.

---

### Post by Mahinva on 2008-07-25
Thank you, warp99. When I look at the .xsession-errors file, my untrained eyes do not find a blatant cause. However, I do use Keytouch and the time when this problem started does (by my memory) coincide with the time when I installed Keytouch after a fresh installation of Ubuntu. The same could be said for when I was dual-booting XP and Ubuntu - the problem started after installing Keytouch.

It would make sense that Keytouch is the culprit, however I will include the .xsession-errors file as I may be overlooking something important there.

```
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 29: [[: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/maria-desktop:/tmp/.ICE-unix/5660
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0326 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...none found
Throttle level is 0
11
evolution-alarm-notify-Message: Setting timeout for 41171 1217030400 1216989229
evolution-alarm-notify-Message:  Fri Jul 25 20:00:00 2008

evolution-alarm-notify-Message:  Fri Jul 25 08:33:49 2008

seahorse nautilus module initialized
Initializing nautilus-share extension
Starting gtk-window-decorator

** (nautilus:5695): WARNING **: Unable to add monitor: Not supported
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Unable to open desktop file /home/maria/Desktop/World of Warcraft.desktop for panel launcher: No such file or directory
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I/O warning : failed to load external entity "/home/maria/.compiz/session/default0"
  PID TTY          TIME CMD
 5675 ?        00:00:00 pulseaudio
```

---

### Post by mitchauer on 2008-07-25
Had the same problem, after removing KeyTouch and rebooting it's working as you would expect it to restart and shut down.

---

### Post by Mahinva on 2008-07-25
Seems that removing Keytouch appears to be a solution for me. However, I'd like to continue using Keytouch as it makes my keyboard fully functional - one button to open a media player, messenger, internet browser etc.

I am curious as to the workaround warp99 has mentioned - I would like to give that a try.

---

### Post by warp99 on 2008-07-26
> **Mahinva said:**
> I am curious as to the workaround warp99 has mentioned - I would like to give that a try.

Here is a bug report at Launchpad that discusses the various workarounds including mine:

[https://bugs.launchpad.net/ubuntu/+source/keytouch/+bug/186713](https://bugs.launchpad.net/ubuntu/+source/keytouch/+bug/186713)

---

### Post by Mahinva on 2008-07-27
Thank you, I have found a solution that works. I am not sure if it was what you posted, as I did not see a user "Warp99". I will update my opening post to reflect that this is solved, and what I followed to solve it.

---

