---
title: "mkdtemp: private socket dir: Too many links CANNOT LOGIN"
date: 2009-06-21
forum: General Help
---

### Post by alanwalterthomas on 2009-06-21
Repost. I'm using an acer aspire one.
Things quickly went bad after using lm-sensors (just checking, doesn't work with AAO) then installing the -13 kernel update. I restarted after installing the kernel & several other updates. I found that wireless stopped working. Ok, that sucks, go back to the old kernel, still doesn't work. Restarted with recovery mode, no help. I looked at ifconfig & it no longer showed wlan0, but ifconfig -a did. I tried ifconfig wlan0 up, did nothing. (after the next problem from tty01 wlan0 appeared in ifconfig, but still no connection)

Then I accidentally pressed the Print Screen key. I got a storm of screenshots! Gnome asked me as quickly as it could where to save the screenshot & even madly pressing cancel, cancel, cancel I couldn't keep up. After a minute I got some weird screen corruption & had to REISUB to reboot, but I don't think it worked quite right because even though I pressed alt-prtsc-u several times the ssd light was still on. Anyway, there wasn't anything to do but press the B key to reboot. On reboot it checked the filesystem, passed it, then stopped at the login screen. I typed in my username & password, started to login, then this appeared: (afterwards I was dumped back to the login screen)

(Translation, might not be perfect word-for-word)
Your session lasted less than 10 seconds. If you didn't end a session, this could mean there is some installation problem or that you are out of disk space. Try to start a recovery session to see if you can fix the problem.

See details (file ~/.xsession-error)

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_All linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Too many links

I looked at free & df & I have plenty of spare ram & disk space.
I figure too many links could have something to do with the screenshot storm (too many links ~ too many screenshot files?)
By the way, I can still log in through tty01, & I imagine I'd be able to ssh in through ethernet (still worked) as well.
Removed lm-sensors, didn't help.

If anyone can help out here that's wonderfull! I'd really rather not reinstall everything

already tried chmod a+w /tmp
didn't help
No one on IRC #ubuntu has a clue.

---

### Post by tashirosgt on 2009-06-21
I'm only a Ubuntu beginner, but that "less than 10 seconds" error message happens on other Linux distributions when a file related to the permissions or the configuration of the xserver or the window manager gets corrupted or deleted.  If you can get logged-in, look at the logs like /var/log/Xorg.0.log, ....Xorg.1.log and the logs in /var/log/gdm. 

 Unless you like tty0, try the "options" selections on the lower left of the login screen and see if you can pick a session type that will work..

---

### Post by alanwalterthomas on 2009-06-21
Tried different session types. The only one that works is xterm. Execute Xclient script gives the same problem as GNOME, & Gnome in secure (recovery?) mode give a blank black screen.
This is really weird. Any gurus around?

---

### Post by alanwalterthomas on 2009-06-22
#gentoo gurus helped out. The problem was the netbook couldn't make a new directory in /tmp. (maybe that has to do with inodes used up, cuz I saw no files there). Anyway, the solution was to boot from usb, (sdd unmounted) & type in terminal:
jfs_fsck -v -f /dev/sda1
That fixed it.
As for the wireless, I had accidentally pushed the switch that turns wireless on & off. I had tried that earlier but was too impatient to give it some time to start before pushing it again, but it now works too.

---

### Post by alanix on 2009-10-21
I want to confirm that this fix did indeed solve the problem described.  I received the same message today and had the same behavior.  I was able to boot from the Live CD that I used to install with and run the jfs_fsck -v -f /dev/sda* command, where * = the partition number.

The return code was  0 and exit code 1, indicating; according to the man page for jfs_fsck:
"File system errors corrected and/or transaction log replayed successfully."

Thanks to the OP for following up with a solution,

Alan

---

### Post by zebulon M on 2010-09-26
Thanks for leading me in the right direction, booting into recovery mode and simply fsck-ing from the menu solved the problem for me.

---

