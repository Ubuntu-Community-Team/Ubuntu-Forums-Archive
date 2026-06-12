---
title: "Machine will no longer start."
date: 2009-02-27
forum: General Help
---

### Post by Mark_thetrigeek on 2009-02-27
Hello all. I really hope you guys/gals can help me. 

Installed Ubuntu 8.10 and then added KDE 3.5. so now the log in shows Kubuntu. Everything has been running beyond perfect. After using a few other distros I landed here as was very happy. 

I shut the machine off last night, and everything was perfectly good. Today I went to start it up and I got some 

Starting NFS common utilities {fail} 

notice. So I reboot. It does it again and this time it tells me this. 

Starting NFS common utilities [fail]
Exporting directory NFS       [pass]
Starting NFS Kernel Daemon ....

And that is where it just hangs until it dumps me into the root prompt. No X, no startx, nothing. 

I type reboot and it starts up again and when I get to the Kunbuntu splash screen it tells me:

Unclean Shutdown Checking drives. 
/dev/sda1 3%(stage 1/5 125/2339)

It just hangs there until it dumps me into the root prompt again telling me this. 

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. fsck diead with exit status 4

* automatic file system check (fsck) of the root filesystem failed. 

So I run fsck and get told this. 

Error reading blok 4097337 (attempt to read block from file system resulted in short read) while getting next inode from scan. Ignore error? <y>

If I don't ignore it nothing changes. If I do ignore it... it then asked about force rewrite. As of this writing I have had to ignore 8 bad blocks for it to continue.

This is blowing me away, this is a brand new machine how and why is this happening?? How do I fix it and how do I avoid this in the future. I've been running linux since RH 6.2 and I have never had this issue ever before. 

My drives are SATA, the board ASUS, AMD chip, with 2gigs ram.

---

### Post by Psyphre on 2009-03-11
hey, just letting you know your not the only one with this issue. Just happened to me 20 mins ago. Totally out of the blue. Im surprised (and dissapointed) no-one has answered your thread. 

Since it's been a week how have you sorted -or not as the case may be- the problem?

My thread is here:
[http://ubuntuforums.org/showthread.php?p=6880358#post6880358](http://ubuntuforums.org/showthread.php?p=6880358#post6880358)

Hopefully someone will post there that will also help your issue aswell.
If I get it sorted I'll pm you. I hope you can do the same for me.

---

### Post by Mark_thetrigeek on 2009-03-12
It ran for 2 hours straight "fixing" things. It finally stopped but nothing was right. So I reinstalled. Not what I wanted to do but it works now. 

As for the forum not responding, oh well. The distro I ran before had an outstanding forum but it was alot smaller so it was easier for them to get to everyone. Maybe next time. 

Take care.

---

