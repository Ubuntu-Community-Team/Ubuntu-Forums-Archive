---
title: "Bootloader Issues!"
date: 2009-01-02
forum: General Help
---

### Post by rancor37 on 2009-01-02
I've been using Ubuntu for about a month now, and have come across a few problems. I know there have probably been multiple posts about the following topics but I've been scavenging for awhile and haven't found a suitable solution. 
My main issue concerns grub. I had one of my friends install Ubuntu on my windows (vista) machine and my windows partition ended up being temporarily inaccessible; the entry was there but some sort of segmentation fault occurred every time I attempted to boot into windows. I used the vista recovery CD and was able to successfully boot into windows, but only after grub took me to the longhorn loader... My goal is to use grub as the primary boot loader and not have to go through longhorn as an intermediate step.

Other than that, i recently noticed that my sound doesn't work when i use youtube! If the fix is simple let me know, otherwise I'm sure i can google it some more or something. My main concern is the loader issue! My menu.lst file is attached. 

Thanks so much!

---

### Post by caljohnsmith on 2009-01-02
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.

If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

