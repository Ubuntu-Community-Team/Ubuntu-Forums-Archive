---
title: "Restoration of NTFS files deleted in Ubuntu"
date: 2009-04-29
forum: General Help
---

### Post by Alphx on 2009-04-29
Hi folks. My problem is that I deleted some work (thankfully not the only draft) when I was clearing out some folders on an NTFS partition when I  was booted into into Ubuntu. The catch is that Ext2/3 file recovery tools won't help me here because the drive I had mounted with the files NTFS-formatted drive I usually use through Windows.

I tried some windows-based file recovery tools and while they displayed some old junk off these drives, they didn't have the recently deleted files. I hadn't written to this drive since that day and it's not a system partition of any sort.

Long story short I now need to try and get this work back, and while I've heard of photorec/testdisk I'm thinking that this tool is a little outside my scope of knowledge.

I'm hopefully one of you clever folks/gals might be able to point me towards some file recovery project/application, either Windows or Linux-based (Preferably linux-based :P), that can throw up a folder-tree-type view of NTFS drives and let me attempt to recover files that have specifically been deleted using Linux.

Anyway I'll admit that while I might have a slightly more-than-rudimentary understanding of file systems in general, I'm guessing that the way the NTFS drivers that ship with Ubuntu files hard drive space for overwriting is slightly different than the Windows drivers. Any help in helping me get these files back would be most appreciated, thanks.

---

### Post by blackmail on 2009-04-29
i had the same problem, and i am certain that with 10-15 minuutes spent on the case you will be able to recover your data with photorec, you could youse gparted since it gives you detailed info about your partition, it will help while using photorec. There is only one problem, if your data is fragmented, photorec doseny't recover the whole file t recovers the fragment, but all your lost data will be recovered, i have had a 70% success.
so first you install testdisk/photorec
```
sudo apt-get install testdisk
```
after that you start photorec
```
sudo photorec
```
and for some help please read [this]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") tutorial, will be of great help if you need advice, ,but please give it a try, i hezitated also at first but after that i was shocket how simple it was and rthe results where quite goot.

:lolflag:Now what i can't give help with is that you want to recover files from a specific folder, but if i find something better i will return.

---

### Post by blackmail on 2009-04-30
please do try hiren's boot cd, google for it, you download the image fry a cd and give it a go, read about it at first so you don't mess up thins more than they are.
best regards

---

