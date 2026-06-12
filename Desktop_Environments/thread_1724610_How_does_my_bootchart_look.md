---
title: "How does my bootchart look?"
date: 2011-04-08
forum: Desktop Environments
---

### Post by brandon1004 on 2011-04-08
Sorry, I don't really know what to look for in bootchart. Can someone tell me about mine, or show me some examples of what it should look like (for a fast boot up that is)? Thanks!
Edit: It seems the forums lowers the resolution. See this: [http://www4.picturepush.com/photo/a/5411682/img/Anonymous/UrsaMinor-maverick-20110408-3.png]("http://www4.picturepush.com/photo/a/5411682/img/Anonymous/UrsaMinor-maverick-20110408-3.png")

---

### Post by lithopsian on 2011-04-08
It looks slightly odd to me, but probably nothing bad.  Overall it is pretty fast.  Are you booting from an SSD?  Do you have masses of hard drive partitions?  Seems like you ought to be able to take maybe 5 seconds out of there with a few tweaks.

Two seconds before you even start, presumably due to a massive initramfs.  This is normal in Ubuntu but a fairly simply configuration change can usually knock a second or more off it by only including kernel modules likely to be needed on your system instead of including just everything and the kitchen sink.  Look in /etc/initramfs-tools/initramfs.conf.

Your root device seems to take forever to mount.  Is that normal for SSDs?  Also possibly other devices are slow to mount, but that could be because you have so many.  Seems like modprobe is really getting a workout.  Do you have dozens of kernel modules loaded (check with lsmod)?  Assuming you need all of them, the only way to cut down on that would be a kernel that had those essential modules built in.  A lot of work to knock a few seconds off your boot but fun if you like that sort of thing.

It all looks a bit single-threaded and bottlenecked once X starts.   Maybe X is loading a lot of drivers?  Multiple input devices?  Multiple graphics drivers?  I don't see a lot of services starting.  Very often there are a bunch of services that can be started after GDM and in your case could be started in parallel with X.  Or maybe you are doing that and they don't show because they are just so fast?

You may be able to tweak your readahead to profile a little longer and catch X and its drivers? Or maybe it already does, but X seems to be taking forever to start.  Four seconds before it hands off to Gnome is a long time with nothing significant running in parallel with it.

Make sure all your autostart processes are kicked off in the background so they can run in parallel.  Looks like many of them are already.  Have you got four cores?  You seem to have more scope for concurrency.

---

### Post by brandon1004 on 2011-04-08
Thanks! You've given me a great start.
1) Yes, I'm using an OCZ Agility 2 SSD. Installed it 2 days ago on my Dell XPS L501x. So far it's made a quite the difference, especially for loading huge programs.
2) I have 2 partitions, EXT4 and SWAP.
3) Searched a little online and no one's complained about slow mount time with SSD's. I'll look into that!
4) I don't have to many devices besides whats on the laptop. For storage I have an empty DVD drive, and the SSD, and an empty SD reader. The reader wont work unless it boots up with a card in it.
5) Attached is the lsmod output. Looks like I can get rid of a lot of those! :D
6) The only input device is the touchpad (most of the time). The graphics driver is kind of interesting. It's an nVidea GeForce GT 435M with a tv tuner. The tv tuner doesn't seem to be working (I don't really care about that) - not sure if that would somehow make it hang. I'll look into readahead.
7) I disabled quite a few services. I might put bluetooth back.
8) I have an i7-740QM, 4 hyper-threaded cores. Is there a way to encourage concurrency?

---

### Post by lithopsian on 2011-04-09
1.  Excellent seek time (zero!) on SSDs and pretty high data transfer rate.  You might experiment with turning readahead off.  Or is it even on?  Looks like it is from the bootchart.

2. I guess the long modprobe is to load all those kernel modules.

3. Your initial root mount in the initramfs is taking almost 1.5s and that  is too long, but I have a suspicion it is a "bug" in the script and it  may just be sleeping for too long while the drive has already mounted.

4. Don't worry about it.  Probably just those modules.

5. Pretty standard list for an Ubuntu installation.  Some you might be able to get rid of by disabling services you don't need like Bluetooth, but getting rid of them all means building a custom kernel.  I even have one on a machine here that has the nVidia kernel module built in!  Brought to you by the department of pointless "because I can" enhancements ;)

6. You really need to look into what's going on there.  My much slower CPU takes about a second for X to initialise and yours is taking over four.  Some of it might be IO that could be read ahead but a lot of just CPU.  I wonder if it is parsing some really complex configurations.

7. The only way to improve concurrency while X starts is to continue starting services that GDM doesn't depend on.  X itself just has to do its stuff and then Gnome can start.  Some examples from my machine are rsync, ssh, autofs, atd, cron, cups, and perhaps most importantly network manager.  By default many of these will be started before GDM but on most simple desktops you don't need them to get X going.

---

### Post by brandon1004 on 2011-04-10
Alright, so when I find some time, I'll look at readahead, shortening some of the kernal modules and checking out what X is doing (maybe I'll recompile and profile?). I might also try out different versions of initramfs, or just hope it's fixed by 11.04. Thanks guys, you were a great help. :KS

---

