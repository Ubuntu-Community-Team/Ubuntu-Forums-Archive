---
title: "Complete newbie versus three issues... Help needed!"
date: 2005-12-02
forum: Desktop Environments
---

### Post by Lord Skeletor on 2005-12-02
Hi,

This is my first post here, and I am quite a bit intimidated.

I don't like to create new threads, but I don't exactly know how to find the info I'm looking for. So i'm posting here in the hope that this is the right forum, and some Ubuntu Guru/Wizard might lend me some advice/info.

I am more-or-less a complete newbie in regards to Ubuntu, and Linux.

I DO NOT have the Internet (No apt-get for me I'm afraid).

I have juste upgraded from 5.04 to 5.10, and there are three issues which I could use some help about.

- I'd like to read DVD's using Totem. Do I need a Decss plugin or something to that effect?

- My USB MP3 (yeah, I know) player is supposed to have a total available size of 128 Mb (134217728 bytes). For some reason, I have lost some available size on it. I would like to try :

```
sudo mkdosfs -c -I /dev/sda
```, as well as specifying the formatting to take 134217728 bytes.

However, I can't do it when /dev/sda is mounted on /media/usbdisk.

If I ```
sudo umount /dev/sda
```, I cannot mkfs it hereafter.

Do you have any suggestions (or should I buy a new, larger, better, .ogg player)?

- I'd like to install Secure-delete. I just can't seem to compile the source code properly. Is there any package available for Breezy?


Thx for your help.

---

### Post by meborc on 2005-12-02
to find out more about dvd's - [this is the place]("https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b") .... in other quiestions, i's as n00b as you :D ... read [ubuntu wiki]("https://wiki.ubuntu.com") for more help

---

### Post by tedius on 2005-12-02
With regard to you last point (losing space on you USB key), I might have a solution.

I had this problem when I deleted stuff from it in Nautilus.  What happens is that Nautilus crates a hidden directory ".trash_can" (I think) where it puts the files, instead of deleting them.  To delete them properly you need you empty your trash can by (I believe) right clicking on the trash can in the bottom right and select empty..

---

