---
title: "[SOLVED] Windows XP/Ubuntu boot problem"
date: 2007-12-06
forum: Desktop Environments
---

### Post by Browner87 on 2007-12-06
My problem seems very different from most I've found on the Internet. I installed Ubuntu (XP was installed a few days ago) on my laptop, and everything works great. BUT, after the exact same procedure on my computer, I can't get GRUB to boot, only the Windows XP screen. HOWEVER, if I boot to the live CD, then select 'boot to first hard drive', everything works fine - it lists 3 Ubuntu options, then Windows XP. This is on an Intel Q6600 in an ASUS P5N32-E SLI Plus on a 500 GB Seagate Barracuda with 2 WD Caviars off to the side for storage. Windows XP and Ubuntu both are installed on the Seagate. How can I get the list that shows Ubuntu to show?


BTW I've tried the whole terminal->sudo grub->root (hd2,3)->setup (hd0) thing. No luck. :(

---

### Post by meierfra on 2007-12-06
Post the output of 

```
sudo fdisk -l
```

If you can access the ubuntu partition from the LiveCD, (there might be an icon on the Desktop, otherwise look in "Places->Computer"), try to find the file /boot/grub/menu.lst and post its content.

Do you boot directly to Windows or do you get the Grub Menu (and only Windows works at the Grub Menu)?


Try changing the boot order and see whether it makes a difference.

---

### Post by Browner87 on 2007-12-06
Wow. It just hit me. I need Setup (hd2)!

Now I get the grub screen, but when I pick Ubuntu, I get an 'Operating system not found' or something like that message. But, if I boot from the LiveCD and select 'Boot from Hard Drive', it all works fine. Any ideas?

EDIT: Sorry, didn't refresh - I missed your post. I've got the GRUB screen showing up now, but i get something like 'not found on this disk' or something suggesting the OS isn't where it should be. I'll reboot now and get the exact message. Thanks for the fast reply!

---

### Post by Browner87 on 2007-12-06
Error 22: No Such Partition
Press Any Key to Continue...

That's the exact error.

---

### Post by meierfra on 2007-12-06
You need to edit the file "/boot/grub/menu.lst":


At the grub menu at boot up select  ubuntu. But do not press "enter". Press "e" instead.
Press "e" again. You should get a screen with just one line:

root (hdx,y)  

here x and y are some numbers. Probably its "root  (hd2,3)"
change it to

root (hd0,y)

So if you got "root (hd2,3)" change it to  "root (hd0,3)"

Press "Enter" and then "b".

This should boot you into ubuntu.


You now have to make these changes permanent:

Open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Change

"#groot (hdx,y)" to "#groot (hd0,y)"

(So probably "#groot (hd2,3)" to "#groot (hd0,3)"

(if you have a windows item you need to edit that too. If you need help for that, post "menu.lst" and the output of "sudo fdisk -l")

Save and close the file. 

In the terminal

```
sudo update-grub
```

Reboot.

---

### Post by Browner87 on 2007-12-06
THANK YOU SO MUCH! I changed it permanently in menu.lst so I'm going to reboot in a sec and make sure it worked, but I'm pretty confident it did. Thank you again - it's reassuring that venturing into linux won't be impossible with nice, smart people around to help ;)

EDIT: Works great! Thx again! *gives you a cookie*

---

### Post by meierfra on 2007-12-06
> EDIT: Works great! Thx again! *gives you a cookie*

You are welcome and thanks for the cookie.

---

### Post by Browner87 on 2007-12-08
:Þ

---

