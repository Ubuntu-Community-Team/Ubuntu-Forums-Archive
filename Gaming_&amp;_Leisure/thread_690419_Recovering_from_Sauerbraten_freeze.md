---
title: "Recovering from Sauerbraten freeze"
date: 2008-02-07
forum: Gaming &amp; Leisure
---

### Post by BobLand on 2008-02-07
I've been playing Sauerbraten SP for a while and like it a lot.  However, it will often freeze up and I can't exit the game.  I usually have to hit a lot of keys before the system will reboot.

Is there a way to break out of a freeze without rebooting?

Thanks,
bobland

---

### Post by desertboy on 2008-02-07
ctrl+alt+backspace not work?

---

### Post by BobLand on 2008-02-07
That works most of the time but it wipes the desktop clean.  I was hoping to break out of the game and still retain the desktop.

bobland

---

### Post by DrMega on 2008-02-07
I you running it in Gnome? I used to and it froze very often. I now run it in XFce and while it still freezes occassionally, it is very rare.

---

### Post by nille on 2008-02-08
There's one more thing you can try: press Ctrl-Alt-F1 and see if you can reach the terminal (in that case: log in).

Then run **ps -A** (or similar) to list all processes. There will be lines such as this:
25810 ?        00:00:00 xterm

Then run **kill <pid>** where <pid> is the process id (in my example it's 25810), or, if it doesn't help: **kill -9 25810**.

You can also use **killall** or **pkill** if you like it better.

Then press Ctrl-Alt-F7 to get back to your desktop.

---

### Post by BobLand on 2008-02-08
nille,
Thanks for that tip.  I'll give it a try on the next freeze.

bobland

---

### Post by BobLand on 2008-02-10
Had another freeze.  Tried the Ctrl-Alt-F1 but got no response.  Ended up having to hard reset.  Not a big deal.  When I play the game I don't keep anything important on the desktop but it is annoying.

bobland

---

### Post by daigidan on 2008-02-14
BobLand, you might also try installing an SSH server if this keeps occurring so that you can remotely view your syslog and other logs. From your description, it sounds like Sauer may be causing a hardware lock somewhere. If that it the case, Sauer has a few workaround flags that might be relevant, especially if you have an ATI card. For best results, I recommend posting over in the Cube forums with detailed info about your setup: [http://cubeengine.com/forum.php4](http://cubeengine.com/forum.php4)

---

### Post by alejo0823 on 2008-02-14
I had a lot of freezes with sauerbraten it was the screen saver that was causing the problems, try to deactivate it maybe this could help.

---

### Post by daigidan on 2008-02-14
Yeah, if you're using Gnome then gnome-screensaver kicks in. You can fix the problem temporarily by doing:

```
sudo killall gnome-screensaver
```

To disable it completely, use:

```
gconftool-2 --type bool --set /apps/gnome-screensaver/idle_activation_enabled "false"
```

Or you can just use the GUI to disable the idle activation (set to zero, IIRC).

---

### Post by Vadi on 2008-02-14
I installed htop, and after a game freezes, do ctrl+alt+f1, login, do "htop", find the game, kill it, and ctrl+alt+f7 to get back into the desktop.

---

### Post by BobLand on 2008-02-14
When the game freezes, nothing breaks out except to power down.

Maybe it doesn't matter anymore.  Now, when I enter the game I get random and often stop/starts.  Funny that it happens to me but not the game.  A bunch of monsters will be approaching and I can't move.  They end up fragging me and I start over.  I turn and freeze for a second or two and they begin to beat the snot out me and I can't move.

Weird.  With this new development, the game is unplayable.
Too bad.  I really like it.

bobland

---

### Post by daigidan on 2008-02-14
Apologies if you already mentioned this and I missed it, but have you installed the patch for assassin edition:

[http://downloads.sourceforge.net/sauerbraten/patch-2007-12-27_linux.tar.gz?modtime=1198821947&big_mirror=0](http://downloads.sourceforge.net/sauerbraten/patch-2007-12-27_linux.tar.gz?modtime=1198821947&big_mirror=0)

Not sure if that will help or not, but it did bring me more stability. Also, do you see the same problems when you try multiplayer?

---

### Post by BobLand on 2008-02-14
Installed it.  No change.  I'm wondering if I installed something in the past few days that overwrote libs.  I installed tremulous and had the same problem but worse.  Could barely get the cursor to move enough to exit the game.

I may try and move my home dir to a different disk and re-install Gutsy but then I've got to hack thru all of the libs and drivers again...ugh....ugh.

bobland

---

### Post by daigidan on 2008-02-14
From your description, it does sound to me as if something might going on at a lower level. Unless you've disabled virtual terminals you should be able to hit CTRL-ALT-F3 and get to a terminal when a process hangs. The fact that you can't do that, and that CTRL-ALT-BACKSPACE doesn't restart your X display manager makes me wonder if it isn't a hardware lockup. Do you have a greatly tweaked Ubuntu setup by any chance? If so, then I'm probably off-base about mentioning hardware, and reinstalling is a possible solution.

Before you reinstall, though, have you checked your systems logs for any hints? (dmesg, /var/log/syslog, /var/log/messages)

---

### Post by BobLand on 2008-02-14
My installation is fairly new.  I've only added libs and drivers as they were needed.  The last piece of software that I recall installing was sshserver.  

I checked some of the logs, there are quite a few there but I didn't see anything that indicated errors.  A few warnings but that was about all.

One thing I did was connect and disconnect an XP drive a number of times but it did not appear to effect anything.

Also, I've logged out, rebooted and shut down the computer a number of times.  Nothing has changed.  I've run top and it says that out of my 2 Gb RAM about 1 G is used up.  That surprised me since I'm not aware of running anything out of the ordinary - browser, terminal.  I'm not familiar enough on the bare metal state to know what is safe to remove (or how to do it).

I'm reluctant to re-install Gutsy just for games.

bobland

---

