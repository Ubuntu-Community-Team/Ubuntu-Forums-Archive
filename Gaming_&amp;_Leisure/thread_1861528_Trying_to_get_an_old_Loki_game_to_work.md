---
title: "Trying to get an old Loki game to work"
date: 2011-10-15
forum: Gaming &amp; Leisure
---

### Post by Secret_Squirrel01 on 2011-10-15
I've  had a hankering to play Railroad Tycoon 2 again and I've been trying to  get my Loki version of it to work. I was able to get an updated loader  from from: [http://liflg.org/](http://liflg.org/)
That allowed me to install and run the game, only problem is no sound. I  get the following error message from the terminal: Warning: Unable to  open audio: No available audio device

I know this game came out during the old OSS sound days where as everything  now is pulse audio. I have both the alsa-oss and oss-compat packages. I  have tried running it with both the pulse audio suspender (padsp)  command and aoss. And get the same error and still no sound.

I'm not overly technical but I've been researching  this to try find an answer,  but I haven't been able to make any further progress on this.

If it helps I'm running Natty Narwhal 11.04 (64 bit), ASUS P6X68D-E motherboard, I7 processor and 12 gig of ram.

Thanks
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11345662")                                                                                    [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11345662")

---

### Post by thewarlock on 2011-10-17
I've had no luck getting sound for the old loki games for a while.

However, I *did* get it to work running an older version of mandrake in a virtual machine. Only way to get the old sound going that I've found.

(I used the oracle virtualbox.  this is on 11.04)

---

### Post by Secret_Squirrel01 on 2011-10-18
Thanks for the reply. I was hoping to avoid having to resort to trying a virtual box but I guess it's better than nothing. I'll give it a shot.

---

### Post by greyspammer on 2011-10-19
As far as I know, the OSS compatibility layer was removed from the Ubuntu kernel for some strange reasons (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300)). You might want to try a self-compiled kernel with OSS compat enabled.

Also, perhaps a peek at [thread=1862082]my problem with NWN[/thread] might help you. I have some strange problems with the 32bit-on-64bit dynamic linker system.

---

