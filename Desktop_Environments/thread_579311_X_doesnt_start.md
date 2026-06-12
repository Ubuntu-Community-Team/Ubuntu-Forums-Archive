---
title: "X doesnt start"
date: 2007-10-18
forum: Desktop Environments
---

### Post by Monarch2007 on 2007-10-18
Dear all,
X doesn't start on my ubuntu system. I have 2 ubuntu systems on separate disk partitions. One of them works perfectly. The other one stopped working recently. I tried copying the xorg-xconf file from the first system to the second, but that didnt work. I tried dpkg-reconfigure, apt-get install ubuntu-desktop, apt-get install xserver....but of no avail. Upon booting, it just goes to tty1 (no graphics mode). When i try to start x manually by startx, it comes back to tty1. Ctrl-Alt-F7 doesnt take me to graphics screen. When I run gdm restart, it generates a cryptic message: gdm shutdown [ok], gdm restart [fail]. When I run X manually, it goes to a graphics screen, but nothing is displayed except the x mark, the mouse cursor. Can some one please help me? Is there any file that has been corrupted so that I can copy the same from the working partition? Any file to be deleted??
Thanks a lot, appreciate your response.

---

### Post by vob on 2007-10-18
On my system there are two log files with respect to X:
~/.xsession-errors
/var/log/Xorg.0.log

I'm not an expert when it comes to X, but maybe these two file might give you (or somebody else) a hint why X fails.

Note two things:
1) The first file is a hidden file, you will need to use 'ls -a' to see it in a dircetory listing.
2) The second one is created anew each time X is invoked. The proevious version is moved to /var/log/Xorg.0.log.old . Maybe you'll need to look at both Xorg.0.log and Xorg.0.log.old

Good luck!

---

### Post by Monarch2007 on 2007-10-18
Thank you so much!
Yes, I did take a look at both. There were a couple of differences in the Xorg.0.log in both the systems. I couldnt make out much out of them; also I have used the same xorg conf file. Here are the differences:
(--) I810(0): Display dimensions: (320, 240) mm : Success case
(++) I810(0): DPI set to (100, 100) : Fail case


(II) I810(0): [drm] added 8192 byte SAREA at 0xd03a4000:Success case
(II) I810(0): [drm] mapped SAREA 0xd03a4000 to 0xb7b4a000:Success case
(II) I810(0): [drm] added 8192 byte SAREA at 0xd042b000:Failed case
(II) I810(0): [drm] mapped SAREA 0xd042b000 to 0xb7b37000:Failed case

Also the failed log has these additional lines:
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xd042b000 at 0xb7b37000
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
	the saved state
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

---

### Post by Monarch2007 on 2007-10-18
Here is the output of .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "monarch"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

**Here it is when I login as root:**
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
SESSION_MANAGER=local/monarch-desktop:/tmp/.ICE-unix/4529

** (gnome-session:4529): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (update-notifier:4623): WARNING **: not starting because user is not in admin group

evolution-alarm-notify-Message: Setting timeout for 56186 1192406400 1192350214
evolution-alarm-notify-Message:  Mon Oct 15 05:30:00 2007

evolution-alarm-notify-Message:  Sun Oct 14 13:53:34 2007
(gnome-panel:4601): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
gnome-screensaver-Message: Screensaver is not running!
gnome-screensaver-Message: Screensaver is not running!

(gnome-screensaver-command:4697): gnome-screensaver-WARNING **: Unknown option --throttle
(gnome-screensaver-command:4889): gnome-screensaver-WARNING **: Unknown option --throttle

** (firefox-bin:4983): WARNING **: Wrong permissions for /tmp/orbit-root

** (firefox-bin:4983): WARNING **: Wrong permissions for /tmp/orbit-root

** (firefox-bin:4983): WARNING **: Wrong permissions for /tmp/orbit-root

(gnome-screensaver-command:5074): gnome-screensaver-WARNING **: Unknown option --throttle

(gnome-screensaver-command:5123): gnome-screensaver-WARNING **: Unknown option --throttle
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
alarm-notify.c:366 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:302 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:241 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1871 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Mon Oct 15 05:30:00 2007
 
alarm-notify.c:272 (alarm_notify_finalize) - Finalize 
 alarm-queue.c:1942 (alarm_queue_done)

** (gconftool-2:5155): WARNING **: Wrong permissions for /tmp/orbit-root

---

### Post by Monarch2007 on 2007-10-19
Any suggestions please? I am eagerly waiting for your inputs.
Thanks so much for your timer and patience..

---

### Post by mabovo on 2007-10-19
I'm not an expert in Ubuntu but looking to these log files I couldn't figure out wich versions of Ubuntu do You mean if Gutsy, Feisty or Dapper. I know that if You move one xorg.conf file from one distribution to another it doesn't help so much. Another problem I have read in the forum is that when You create a new user into the system some problems begins to happen with the other users of the system. It must be investigated because is a recent bug in Gutsy only.
Should be a good help if You could inform what kind of graphics card are You using too.
Anyway, take a look in the releases notes of Your distribution to see if an option like usplash or disabling some parameter like dri can resolve this problem.
You can also try sudo gdm --replace or gdmsetup to clean the gnome session.

---

### Post by mabovo on 2007-10-19
Another question to investigate is related to the group users and permissions for both systems. Although they are Ubuntu distributions doesn't mean that they share the same enviornment area with the same users for both system like I saw people trying to share Ubuntu with MacOs in a Macbook Pro and found those kind of problems. I think this apply when You have only one /home directory sharing files.

---

### Post by mskadu on 2007-10-19
Hi,

I am facing the same problem. However, mine is a fresh v7.10 install. A few quick things I noticed are:

a) The installer works much slower than it did before.
b) It takes ages for the login screen to come up
c) X stalls after i login (even Ctrl + Alt + Backspace doesnt work, but mouse is active). I dont get to a desktop. Oh, and I do hear the start up music (just in case it helps)

Maybe it's just me. Anyway, any suggestions?

---

### Post by Monarch2007 on 2007-10-20
Thanks a lot for your inputs.
I apologize - I didnt make a few things clear in my earlier post.
I have the same ubuntu version - Edgy on both the partitions. The reason for creating a new ubuntu partition was to get more disk space. Otherwise, the setups are identical. Currently, I am the only one using it. That's why I am a little surprised what could have gone wrong. In fact, when I created the second partition, i simply copied everything from the first and I was able to use it for about 5 months now...
Once again, thanks a lot and I appreciate your suggestions. I will try sudo gdm -replace and post my findings.

---

### Post by Monarch2007 on 2007-10-21
Finally, I was able to solve the problem. Looks like there were two issues. After reinstalling gdm, gdm started reporting that /var/lib/gdm is missing. Although it was there. I figured out that +x permission on the root FS was missing for the others! I was always logging in as root (to solve this problem) and hence didnt notice this problem..I hope this would help someone in future..Thanks everyone.

---

