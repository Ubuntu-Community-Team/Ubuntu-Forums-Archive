---
title: "Oh #$%&amp; I just messed up my computer!"
date: 2009-01-09
forum: General Help
---

### Post by tgdane on 2009-01-09
I saw this thread:

[http://ubuntuforums.org/archive/index.php/t-907735.html](http://ubuntuforums.org/archive/index.php/t-907735.html)

I have a similar problem but i'm a total noob with ubuntu.

I tried to install gOS onto a usb drive from a livecd. 

First like an idiot I tried to just install it onto my empty flash drive. 

Then I followed this tutorial:

[http://www.pendrivelinux.com/create-a-portable-gos-3-flash-drive/](http://www.pendrivelinux.com/create-a-portable-gos-3-flash-drive/)

I got all the way through but now when I try to restart all I get is the error 21 and 17.

Please help me!!!! I don't want to system restore!

---

### Post by PmDematagoda on 2009-01-09
What drive did you install the image to? Also, what is the setup of your drives and partitions?

---

### Post by tgdane on 2009-01-09
Thanks for the response. I have a regular 60gb drive that XP is installed on. I tried to install the ubuntu onto a 4gb usb drive. no partitions.

---

### Post by caljohnsmith on 2009-01-09
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

