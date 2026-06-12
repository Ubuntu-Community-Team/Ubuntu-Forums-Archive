---
title: "Got a little issue... Wrong Logo on the Bootloader."
date: 2006-10-27
forum: Desktop Environments
---

### Post by Khuzad on 2006-10-27
Hello all...

I am a complete noob!! Let me just get that out there...lol

Ok... I am running Ubuntu 6.06... I went into the Synaptic Package Manager and download a bunch of themes and such... while I was in there I saw the artwork for the Edubuntu version... I have 4 kids I thought some of it would be kewl... just wanted to check it out...

Well it is kewl... but it changed the some things I would like to change back... the very first screen ( i think its the bootloader ) now says EDUBUNTU... its the screen where it shows you what services are starting and such... it also changed the shutdown screens... as well as login and others...

I went in and completely removed all the edubuntu stuff via the synaptic tool... that worked pretty good... I have suceeded in restoring everything back to UBUNTU... accept for the grub bootloader screen...

Does anyone know how I can either change it back or display nothing at all...

Again.. I am a noob... lol... I will need simple instructions...

Thank You,

---

### Post by HeyGabe on 2006-10-27
I installed KDE and had the same thing happen. Now I have a kubuntu boot-splash. Waa!
It doesn't really bother me, but some insite into how it happened would be interesting.

---

### Post by Khuzad on 2006-10-27
I think the artwork came with the KDE build...

Since Kubuntu is KDE right??

I know its silly but I would like to be able to fix it...lol

---

### Post by bagofchickens on 2006-10-27
Take a look at the end of the first post [here]("http://www.ubuntuforums.org/showthread.php?t=205002") [HOWTO: correctly install/remove k/x/ed/ubuntu-desktop packages] (under "Helpful Stuff", "NOTE")

---

### Post by Khuzad on 2006-10-27
Hmmm...

That doesnt work for me... It says this..

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

and if I paste the next step in... it just sits there til i break it and then it says...

Not touching initrd symlinks since we are being reinstalled (2.6.15-27.48)
Not updating image symbolic links since we are being updated (2.6.15-27.48)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


hmmm

---

### Post by HeyGabe on 2006-11-10
Great! Worked great! Thanks!

---

