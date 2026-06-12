---
title: "Ubuntu and Windows XP Will Not Boot"
date: 2008-12-31
forum: General Help
---

### Post by ram2008 on 2008-12-31
For the past couple of weeks I have been running Ubuntu 8.04, having installed it using Wubi.  Everything was fine until this morning.  I used both Windows and Ubuntu last evening and both systems were shut down normally and there was no indication of any problem.  This morning neither XP nor Ubuntu could be booted.  Normally I get the Grub menu that gives me a choice to boot to another Linux distribution or Windows.  I choose Windows and then have a choice of Windows or Ubuntu.  Neither of those menus appeared this morning.  Instead I got the same menu that you get when the Ubuntu CD is inserted, but there was no CD in the drive.  I tried two or three times with the same result.  I finally put the Ubuntu CD in the drive and booted Live.  That's how I'm operating now.

I'm assuming something happened to the boot record.  Is there a way of fixing the problem without permanently damaging my XP installation as well as Ubuntu?  Any help will be much appreciated.

---

### Post by Jammanuser on 2008-12-31
> **ram2008 said:**
> For the past couple of weeks I have been running Ubuntu 8.04, having installed it using Wubi.  Everything was fine until this morning.  I used both Windows and Ubuntu last evening and both systems were shut down normally and there was no indication of any problem.  This morning neither XP nor Ubuntu could be booted.  Normally I get the Grub menu that gives me a choice to boot to another Linux distribution or Windows.  I choose Windows and then have a choice of Windows or Ubuntu.  Neither of those menus appeared this morning.  Instead I got the same menu that you get when the Ubuntu CD is inserted, but there was no CD in the drive.  I tried two or three times with the same result.  I finally put the Ubuntu CD in the drive and booted Live.  That's how I'm operating now.

I'm assuming something happened to the boot record.  Is there a way of fixing the problem without permanently damaging my XP installation as well as Ubuntu?  Any help will be much appreciated.

Please post the output of "sudo fdisk -l" (and that last letter is a lowecase L, not a capital i), without the quotes, so we can take a look at the setup of your partitions, and will be better able to figure out what your problem is. ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by caljohnsmith on 2008-12-31
I agree with Jammanuser, it would be helpful to see the fdisk output, but it would be good to know a few more details about your setup; so in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Jammanuser on 2008-12-31
> **caljohnsmith said:**
> I agree with Jammanuser, it would be helpful to see the fdisk output, but it would be good to know a few more details about your setup; so in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

Ah yes! :) I forgot about that little nifty result.txt file that you and Meierfra came up with...funny too, since I just created one just recently to aid me with my tri-booting problem (which is now fixed, btw, and I now have posted a tutorial on it!:))!

Cheers! :popcorn:

-Jam man

:guitar:

P.S. In case you want to check out my tutorial (to make sure I didn't say something wrong), here it is: [http://ubuntuforums.org/showthread.php?t=1024929](http://ubuntuforums.org/showthread.php?t=1024929) :D

---

### Post by ram2008 on 2008-12-31
Thanks guys for responding to my message.  As soon as I hve dinner I will see if I can get the information you requested and post it here.

---

