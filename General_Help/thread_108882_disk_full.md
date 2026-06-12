---
title: "disk full"
date: 2005-12-27
forum: General Help
---

### Post by myha on 2005-12-27
Hi all!

Can anyone please tell me which files or folders I can safely remove, like some cache, old debs, /var/cache... ? I have full disk and I need to delete some data... I have nothing im my home btw...

br

---

### Post by adie273 on 2005-12-27
Not sure what you could delete at all. But if you haven't done so, go into synaptic and goto settings in there somewhere (Sorry I can't be more specific, i'm not at my own computer at the moment to give more detailed instructions).

But in there somewhere is the option to delete all the temp packages you downloade. Meaning when synaptic downloads packages, it stores them somewhere and installs them, but the packages still remain where they were downloaded unless you tell synaptic to automatically delete them. I did this before and gave me an extra 400 to 500Mb believe it or not.

Hope that helps,

Adie

---

### Post by fordfan753 on 2005-12-27
Apt-get does cache debs...try:

```
sudo apt-get clean
```

---

### Post by ACK!! on 2005-12-27
[QUOTE=myha]Hi all!

Can anyone please tell me which files or folders I can safely remove, like some cache, old debs, /var/cache... ? I have full disk and I need to delete some data... I have nothing im my home btw...

br[/QUOTE]

Go to a terminal and do a df -k.

Which filesystem is full?

Then do a du -sk (path of filesystem that is full)

Which dir is filling up your drive?

Maybe its var or maybe its usr (which means you just got a ton of installed apps maybe you need to uninstall some crap you do not use).

If its temp then you probably got some out of control ass app filling up your drive with crap.  

Do this stuff and post the results.

---

### Post by myha on 2005-12-27
Hello,

I have gone through the system and I have 4,6GB in /var/log/   :/  I thought there was something strange in the fact that I was suddenly out of disk...
My colleague which has approx the same config has 9MB....

Can I delete the whole folder and everything in it?

---

### Post by myha on 2005-12-27
hi,

I managed to repair the problem....

The 4,6GB of data was in /var/log/gnump3d/something.log file.....   ?
I removed it, rebooted and now I have the space I had before. Strange....

Thanks for all your help,

br,
Miha

---

### Post by ACK!! on 2005-12-27
[QUOTE=myha]hi,

I managed to repair the problem....

The 4,6GB of data was in /var/log/gnump3d/something.log file.....   ?
I removed it, rebooted and now I have the space I had before. Strange....

Thanks for all your help,

br,
Miha[/QUOTE]

No, it makes perfect sense gnump3d is a mp3/media streamer.  

If it is mis-configured or configured badly by default it will probably write each stream to disk as a wav get a few people streaming off you using your server or if the server is not cleaning up very well and -bam!- /var fills up and you are effectively screwed.  

I would look into how the thing is handling its streaming.

---

