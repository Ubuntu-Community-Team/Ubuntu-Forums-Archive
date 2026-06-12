---
title: "dual-boot DELL's distro and 8.10 Netbook Remix on mini 9"
date: 2008-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gregconquest on 2008-10-21
After seeing the [lengthy discussions]("http://ubuntuforums.org/showthread.php?t=910487") on Ubuntu's Netbook Remix and DELL'S customized distribution for the mini 9, I've decided I want to **run both**. So, please review my strategy and help me get ready. My mini 9 is scheduled to ship 10/30.

1st: I make **backup images** of the SSD as it comes to me -- using CloneZilla. (I have BootIt NG also, and it works great for this sort of thing, but I want to avoid proprietary images and apps if at all possible...)

2nd: I **customize DELL's disto** -- get it working the way I like, then I make another backup image.

3rd: I shrink the DELL OS and **create a second partition**.

4th: I **install Ubuntu into the second partition**. Image again. Customize the new OS (including running the netbook remix scripts). And image again.

From then on, I can boot into either OS and eventually delete one or the other depending on how the distros develop.

**Outstanding questions**:
- Can I put **my home directory on my 16GB SDHC card** and have both OS's share it with no problems?
- How do I set up **a boot manager**? Do I need to move DELL's grub from the MBR to root on the existing DELL distro before installing the second OS?
- Once I've got images of the default system, can I delete the other partitions DELL has added (recovery partitions, etc...)?
- Once I have both systems up and running, can I **extract the multimedia codecs** from the DELL distro and "install" them into netbook remix?

Thanks for any help.
Greg Conquest

---

### Post by yakker.yak on 2008-10-22
> **gregconquest said:**
> 
**Outstanding questions**:
- Can I put **my home directory on my 16GB SDHC card** and have both OS's share it with no problems?
- How do I set up **a boot manager**? Do I need to move DELL's grub from the MBR to root on the existing DELL distro before installing the second OS?
- Once I've got images of the default system, can I delete the other partitions DELL has added (recovery partitions, etc...)?
- Once I have both systems up and running, can I **extract the multimedia codecs** from the DELL distro and "install" them into netbook remix?

Thanks for any help.
Greg Conquest

Sharing a single home directory on an SDHC card should work, but to be on the safe side I wouldn't recommend it since it'll contain application settings. Hypothetical problem scenario: one of the apps customized for the Dell Ubuntu writes/needs settings that are clobbered by the vanilla Ubuntu application equivalent. Seems safer to have a separate /home for each and then share a global 'Files' directory on the SDHC where you actually keep your files that can be safely shared across the two. You could create links/shortcuts to this directory from each /home.

The second install should recognize the first partition install when it writes the MBR.

If you want support from Dell, seems like a good idea to keep the diagnostic tools so that you can run these when on the phone with support.

I don't think you'll be able to extract the codecs from the Dell CDs, since it looks as though the two platforms (386 vs. lpia) don't play nice. The codecs will be compiled for lpia, not 386.

---

### Post by gaussian on 2008-10-22
> **yakker.yak said:**
> Sharing a single home directory on an SDHC card should work, but to be on the safe side I wouldn't recommend it since it'll contain application settings. Hypothetical problem scenario: one of the apps customized for the Dell Ubuntu writes/needs settings that are clobbered by the vanilla Ubuntu application equivalent. Seems safer to have a separate /home for each and then share a global 'Files' directory on the SDHC where you actually keep your files that can be safely shared across the two. You could create links/shortcuts to this directory from each /home.

The second install should recognize the first partition install when it writes the MBR.

If you want support from Dell, seems like a good idea to keep the diagnostic tools so that you can run these when on the phone with support.

I don't think you'll be able to extract the codecs from the Dell CDs, since it looks as though the two platforms (386 vs. lpia) don't play nice. The codecs will be compiled for lpia, not 386.


For Codecs, try the following (in the Dell side):
1. First figure out the name of package containing those codecs (using synaptic search for fluendo, media, dvd and other such things).
2. Once you have figured out the name of the package (say fluendo-codecs) do:
dpkg-query -L fluendo-codecs
This will list the files it installs
3. Copy the files over to your plain vanilla Ubuntu side (to same location), while keeping track that you don't overwrite anything and hope for the best*

*if you were to overwrite anything, I would compare the files in the two locations manually to see the changes to be committed.

---

### Post by anjilslaire on 2008-10-22
What would be great is if Canonical would just release a lpia-based  ISO of vanilla Ubuntu. That way it could be used on several Atom-based systems, including the eee & the Mini 9, among (I'm sure) others.

Then we could truly have the OS of our choice on the hardware of our choosing :)

---

### Post by rosskarchner on 2008-10-28
> **anjilslaire said:**
> What would be great is if Canonical would just release a lpia-based  ISO of vanilla Ubuntu. That way it could be used on several Atom-based systems, including the eee & the Mini 9, among (I'm sure) others.

Then we could truly have the OS of our choice on the hardware of our choosing :)

It looks like they're working on it:
[http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)

I tried to install that on my Mini, and it didn't leave me in a bootable state though.

---

