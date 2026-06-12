---
title: "&quot;No resume image, doing normal boot...&quot;"
date: 2007-04-23
forum: Desktop Environments
---

### Post by 42Wired on 2007-04-23
It says this every time I start up Feisty. I have to switch to the terminal to see it. GNOME just stays black until I switch to the console.

I installed it clean over Dapper (instead of upgrading). I have a Toshiba Portege M200, Pentium M 1.70 Ghz, 2GB DDR RAM, Intel 855 series graphics card.

It seems to be a minor issue, except for the fact that because of this, Feisty takes much longer to start up than Dapper did.

---

### Post by garlik42 on 2007-04-23
That message is totally normal, it's for use when hibernating.

As far as feisty taking longer to boot, I don't think this will have that much of an effect, there are more "doodads" and supported hardware types in feisty, and the kernel is a bit fatter, that might be why your boot is slower.

The gnome-power-manager is I believe the program that is handling this, maybe there is a way to disable it.

---

### Post by 42Wired on 2007-04-23
OK, I'll look into it.

I wouldn't have given it any thought, except that until I switch to the console, there is nothing on the screen (not even the splash screen), and *then* everything works fine.

---

### Post by garlik42 on 2007-04-24
All the boot messages are on one of the other consoles, (I think it's Alt-f6 or Alt-F7) but like I said, it's nothing to worry about, and even if you disabled it I don't think it would save much time.

---

### Post by 42Wired on 2007-05-01
I found out that I was just happening to hit any key at the time it would have booted anyway.

But I still don't think that it's normal for the screen to be completely blank for 60-80 seconds after the splash screen before anything else happens.

I'm also having trouble with Suspend mode. When I put it into suspend, everything shuts off, but the fan runs at full speed until I hold in the power button (even though the light on the power button is off already).

Then when I try to resume, it tells me there was an error resuming, and to hit any key. But no matter which key I press (keyboard or mouse) nothing happens, and I'm forced to shut it down manually again.

Could the delayed startup and the Suspend mode problems be related?

---

### Post by 42Wired on 2007-05-29
I'm still having these problems.

Toshiba Portege M200
Intel Centrino 1.70 Ghz
2GB DDR RAM
Intel 82852/82855 on-board video card

---

### Post by 42Wired on 2007-05-31
It paused when I restarted X-Server with Ctrl-Alt-Backspace, so it seems to be an X-Server problem.

Does anyone have any ideas?

---

### Post by venik212 on 2007-06-01
Did you resolve it?  I have the same problem, but mine is worse:  it refuses to restart the window manager, and stays in "terminal mode".  I can use startx to get X going, but nothing more.
What do I do?  must I reinstall the OS?

---

### Post by RedSquirrel on 2007-06-01
I would suggest having a look at what's going on during boot.

Check if something is failing in an obvious way. Run this in a terminal:

```
dmesg | grep -i failed
```or save dmesg output as a text file and read it to see if there's something fishy going on.

```
dmseg > dmesg.txt
```Then open "dmesg.txt" with the editor of your choice.

If you spot a strange error or something that looks unusual, try searching ubuntuforums for that error (or a portion of it) and also search on launchpad because it may be a known issue where some solutions have been discovered:

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

If you see something unusual, you could post it here (this thread) as well.

---

### Post by venik212 on 2007-06-02
I said what was wrong: Kinit could not find a Resume Image to load, so it reverted to a Normal Boot (CLI).  My problem was that I was unable to restart KDM, although X started OK after I typed startx.
Anyway, I re-installed, and all is fine.  It is worrying, though, that the OS (kubuntu) will do this on its own.

---

### Post by 42Wired on 2007-06-04
> **RedSquirrel said:**
> I would suggest having a look at what's going on during boot.

Check if something is failing in an obvious way. Run this in a terminal:

```
dmesg | grep -i failed
```or save dmesg output as a text file and read it to see if there's something fishy going on.

```
dmseg > dmesg.txt
```Then open "dmesg.txt" with the editor of your choice.

If you spot a strange error or something that looks unusual, try searching ubuntuforums for that error (or a portion of it) and also search on launchpad because it may be a known issue where some solutions have been discovered:

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

If you see something unusual, you could post it here (this thread) as well.

Well, I have the Hibernate and Suspend Mode Problems under control using uswsusp and some scripts that [this]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/") nice person wrote.

It still pauses for 60-90 seconds before actually starting X.

---

### Post by d_deniz on 2008-04-20
it is better to give a try to memtest, this may occur because of an ram error

---

