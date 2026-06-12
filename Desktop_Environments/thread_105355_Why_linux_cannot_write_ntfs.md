---
title: "Why linux cannot write ntfs?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by forlog on 2005-12-18
Hi,

I know that it's possible only to read ntfs partitions in linux, I know that there is captive driver which is slower than handwriting, but why? Why linux cannot write ntfs?

---

### Post by GeneralZod on 2005-12-18
NTFS is a proprietary Microsoft file system and they have never released the specs, nor are they likely to.  The only way to get native NTFS writing is by reverse-engineering the file system, which is *immensely* difficult.

---

### Post by Rackerz on 2005-12-18
I can't an indepth reason why. You just can't, it can mess up the partition if you do. I would also like a good reason as to why you can't.

---

### Post by kosmic on 2005-12-18
Simple answer... ask microsoft why they decided to make ntfs closed source and not revel how the ntfs filesystem works :)

---

### Post by el3ktro on 2005-12-18
Simply said, because Microsoft doesn't tell us how it works! The NTFS driver devs would have to find out by themselves HOW NTFS writes files with "trial-and-error", this is called "reverse engineering" ... and this is pretty difficult and for a file system driver, this reverse engineering has to be 1000% perfect if you don't want any data loss.


Tom

---

### Post by rlange on 2005-12-18
We are getting closer.

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

[http://www.enterpriseitplanet.com/networking/features/article.php/3465141](http://www.enterpriseitplanet.com/networking/features/article.php/3465141)

---

### Post by void_false on 2005-12-18
I dont know what to say but SUSE 10 writes on NTFS perfectly for me.

---

### Post by Rackerz on 2005-12-18
[QUOTE=void_false]I dont know what to say but SUSE 10 writes on NTFS perfectly for me.[/QUOTE]

So you can copy files from your Linux partition to your Windows NTFS?

---

### Post by rklauco on 2005-12-18
[QUOTE=Rackerz]So you can copy files from your Linux partition to your Windows NTFS?[/QUOTE]
Well, using the latest captive I was able to write to NTFS, but only to non-encrypted disk and with some limitations and the speed was terribly slow.
But it worked...;)

---

### Post by forlog on 2005-12-18
Is it possible to mount one partition twice in different directories using different drivers (build-in ntfs and captive)?

---

### Post by britjm on 2005-12-18
I'm not sure how it was working but when I was still playing with my 5.10 install,  Root had no problem writing to NTFS. My reg user couldn't do it no matter what. Also, I created a FAT32 partition and Root could write to that as well, but my reg user couldn't. I was wondering why that would have happened. I tried changing permissions but nothing happened.

In any case, it's possible, just not great.

---

### Post by Rackerz on 2005-12-18
So in some cases its a matter of you can, but a your own risk.

---

### Post by HermanAB on 2005-12-18
Yes, IIF the one is Read Only, though I have never done this, so I cannot really help, except encourage you to do some Googling.

---

