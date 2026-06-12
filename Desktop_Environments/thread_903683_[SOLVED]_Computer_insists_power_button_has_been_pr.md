---
title: "[SOLVED] Computer insists power button has been pressed"
date: 2008-08-28
forum: Desktop Environments
---

### Post by prshah on 2008-08-28
Hello,

I'm facing a small but irritating issue over the past couple of days.
> 
$ dmesg | tail
Aug 28 22:32:30 desktop -- MARK --
Aug 28 22:52:30 desktop -- MARK --
Aug 28 22:56:44 desktop gnome-power-manager: (user) GNOME interactive logout. Reason: The power button has been pressed.
Aug 28 23:12:30 desktop -- MARK --
Aug 28 23:15:39 desktop gnome-power-manager: (user) GNOME interactive logout. Reason: The power button has been pressed.
Aug 28 23:32:30 desktop -- MARK --
Aug 28 23:42:43 desktop gnome-power-manager: (user) GNOME interactive logout. Reason: The power button has been pressed.


My desktop, at random intervals, pops up the "quit" options (as thought the quit/poweroff button has been pressed.)

The poweroff button (on the tower case) has not been pressed, and i've checked it for shorts, getting stuck etc, it's in perfect condition, no problems.

I usually leave the system on 24/7, and, after a long period (6-12 hours) these dialogs seem to be "queued" up, one after another, as though the power button has been pressed multiple times. (And, dmesg shows that the power button seems to have been pressed, at random intervals). I have to press ESC to cancel them one by one. But I'm dead sure that no one has pushed the power button. It also happens when I'm working, suddenly the screen goes dark (not "not responding" dark), and the quit options dialog box pops up on the screen. I can dismiss it with cancel and everything continues to work fine.

A point I suspect, but have not yet had the time to confirm it 100%, is that this is happening only when Transmission/Deluge is active; otherwise it doesn't seem to have a problem (Eg, I ran it without any torrent clients for three-four hours, and received no button press events).

Live CD works fine, but then again, I didn't run any torrent clients at that time.

Questions:
a) Is anyone else facing something similar?
b) Is it possible that I've opened up some esoteric port access in the computer that allows a remote shutdown signal to be sent? (I'm behind hardware firewall and iptables, no remote access).
c) Who'm I gonna call? The GhostBusters?

All suggestions, comments and requests will be scrutinized and appreciated.

---

### Post by TransitMan on 2008-08-28
Check the settings in the torrent applications you have. Make sure you don't have shut-down after completion is done.

Another choice, remove completely all torrent applications and reboot. Then see if the problem pops up.

Then call "Ghostbusters". :lolflag:

---

### Post by druhboruch on 2008-09-05
I have exactly the same problem.
My server has been doing this for the last 3 days.
If I am logged in, it displays logout window, but if GDM login screen is on, then the server simply shuts down.

Prints the same messages in the log.

I tried to disable ACPI "button" in /etc/default/acpid and now it happens less frequently, but it still happens...

I don't run any torrent-related apps on this server.  It only has samba, bacula, apache+php, mysql and vsftpd installed.  No aps of any kind, not even OpenOffice.

If you can cast some light on this intriguing problem, I would much appreciate it.

Boruch

---

### Post by prshah on 2008-09-05
> **druhboruch said:**
> 
If you can cast some light on this intriguing problem, I would much appreciate it.


I have not yet found any solution/workaround to this problem, but that's mainly because I've not find the time to space. 

However, I'm going to be attacking it over this weekend, so if I find anything, I will definitely post back here.

And, yes, the frequency has reduced for me as well; but I've not done anything!

---

### Post by druhboruch on 2008-09-06
I just blacklisted "button" kernel module and hope it is going to fix this problem.

If it doesn't work i will sign-up to this ghostbusters.com forum.

I will let you know in a few hours.

---

### Post by druhboruch on 2008-09-07
It has been over 22 hours and my server is working OK.

1. modprobe -r button 
2. blacklisted button module in /etc/modprobe.d/blacklist

Another scientific explanation of a supernatural event :)

---

### Post by prshah on 2008-09-24
> **prshah said:**
> 
My desktop, at random intervals, pops up the "quit" options (as thought the quit/poweroff button has been pressed.)


OK it's cleared; after a fashion.

Apparently, connecting the IR remote receiver of my "Mercury" brand TV card causes these "quit" / "power button pressed" signals. It has nothing to do with any IR signals, I suspect a short in the wire. (Remote is without batteries).

Unplugging the remote receiver wire from the TV tuner card cleared this up (but in parting, gave me 113 power-off signals! It's no joke dismissing so many "quit" option dialogs!)

Solved.

---

