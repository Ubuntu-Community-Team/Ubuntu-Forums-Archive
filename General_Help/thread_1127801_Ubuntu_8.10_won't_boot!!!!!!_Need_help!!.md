---
title: "Ubuntu 8.10 won't boot!!!!!! Need help!!"
date: 2009-04-16
forum: General Help
---

### Post by FruitRocks on 2009-04-16
First off, I didn't install the *normal* way. I inserted the disk from windows, and then selected "Install inside of windows." The install went okay, and I managed to do the same with kubuntu. After that, I set up my network, etc. 

Today, however, when I booted up into vista to install updates, and restarted. I selected my ubuntu partition, but then when I selected it, it booted up into kubuntu (i kept on trying for about ten minutes and then gave up). I've got around 40 gigs of data, which I haven't backed up. Please help!!!!!!!!
:(

---

### Post by Svensk023 on 2009-04-16
can you get into your Ubuntu partition form Kubuntu?

---

### Post by codeseer on 2009-04-16
Check your /boot/grub/menu.lst

---

### Post by meierfra. on 2009-04-16
In order to get a clearer picture of your setup, I suggest to boot into Kubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by codeseer on 2009-04-16
That's a pretty slick shell script; I'll have to remember that.

---

### Post by Svensk023 on 2009-04-18
Ya i agree with codeseer. I am going to write that one down. Kudos Meierfra

---

