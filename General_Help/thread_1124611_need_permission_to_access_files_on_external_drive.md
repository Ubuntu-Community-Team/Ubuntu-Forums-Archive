---
title: "need permission to access files on external drive"
date: 2009-04-13
forum: General Help
---

### Post by GlennW on 2009-04-13
I have a bit of a conundrum. I had to recently re-install 8.10 due to some crazy bit of keystroke genius whereby I made root disappear. Don't ask cuz I don't know. I had bapoumba helping me out and even then I was hooped. 

The current situation may be the fallout from all of that. Anyway, the re-install was successful. I had copied crucial files to an external 160 Gb Thermaltake HDD which I had formatted to ext3 before. 

I was having trouble accessing the HDD but managed to do it via, again, my keystroke genius. I copied most of the files back to where they belong and, oh the joy! Here's the bizarre thing: some of the files are hidden. No problem, click Show hidden files. But, I can't access them - I don't have permission! 

I attempted to use Nautilus to rectify the situation but the files still being on the external HDD aren't read by Nautilus. (Is there something wrong with my Nautilus?) 

Question: how can I change permission of the hidden files on the HDD so that I can access them and restore some of my apps?

Sorry, I'm still quite a noob. I am discovering, however, that I know just enough to be dangerous! That I found out the hard way...

Thanks...

---

### Post by ajgreeny on 2009-04-13
I'm sure you could read them all if you start nautilus with root privileges ```
gksudo nautilus
``` but the problem must be the permissions of the files.  When you reinstalled did you keep the same username and password?  If you did, I think the files should already be yours, so I suspect the problem is that the external usb drive is mounted automatically by the system on /media and that drive mount point is no longer owned by you, but by root.  You can find out using nautilus and right clicking on that folder (with the ext disk plugged in and mounted, of course) and checking the permissions tab.  It will be owned by root I think, and if so you will need to use the terminal to change owner with ```
sudo chown -R yourusername:yourusername /media/mountpoint
```

Good luck!  I hope this works for you.

---

### Post by GlennW on 2009-04-13
> **ajgreeny said:**
> I'm sure you could read them all if you start nautilus with root privileges ```
gksudo nautilus
``` but the problem must be the permissions of the files.  When you reinstalled did you keep the same username and password?  If you did, I think the files should already be yours, so I suspect the problem is that the external usb drive is mounted automatically by the system on /media and that drive mount point is no longer owned by you, but by root.  You can find out using nautilus and right clicking on that folder (with the ext disk plugged in and mounted, of course) and checking the permissions tab.  It will be owned by root I think, and if so you will need to use the terminal to change owner with ```
sudo chown -R yourusername:yourusername /media/mountpoint
```

Good luck!  I hope this works for you.

That was precisely it! Thank you so much for your prompt response.

---

### Post by ajgreeny on 2009-04-14
My pleasure.  I had a similar problem once a long time ago, and reinstalled to overcome it.  If only I'd known then how easy it is to use the command line!

---

