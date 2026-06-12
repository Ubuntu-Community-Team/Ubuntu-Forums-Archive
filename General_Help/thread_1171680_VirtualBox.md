---
title: "VirtualBox"
date: 2009-05-27
forum: General Help
---

### Post by Mackeri on 2009-05-27
Hello i have a problem :D

I'm dual-booting XP and Ubuntu. When i'm running ubuntu i don't want to restart the computer, wait... wait.... and wait for xp to fully start. So i wanted to use "virtualbox" to run xp inside ubuntu.... here is the problem:

I cant find any help for running an alrdy installed OS in Virtualbox. (When i bought the computer, XP was alrdy installed) So i don't have any CD or USB thingy to install it with because it's alrdy installed. ( no i cant get a CD )

Could anyone help explain how to run an alrdy installed OS?

Would be so glad if someone helped me and solved this "problem" :D

Merk42's question: What are you using Windows XP for? : Running "simple" programs as CS3 photoshop (not games)

Answer: [http://milinddev.wordpress.com/2009/04/14/how-to-start-exsisting-windows-xp-from-ubuntu/](http://milinddev.wordpress.com/2009/04/14/how-to-start-exsisting-windows-xp-from-ubuntu/)  : and : [http://mesbalivernes.blogspot.com/20...-existing.html]("http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html") :  :p explains nearly every detail.

[SIZE=3]**** To get root access in terminal write sudo -i ** needed for the **[/SIZE][FONT=courier new]VBoxManage internalcommands createrawvmdk -filename ./WinXP.vmdk -rawdisk /dev/sda [B][SIZE=3]thing!!

Could someone maybe link or/and make a video for this... rly hard to understand
[/SIZE][/B] [/FONT]

---

### Post by XCan on 2009-05-27
Interesting question. Virtualbox isn't really made to run an already installed OS by default since the container it creates is essentially an empty computer. However, I would imagine that you should be able to clone your Windows installation and restore the clone into your Vbox container.

---

### Post by Merk42 on 2009-05-27
This should work.
[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

What are you using Windows XP for?
Keep in mind you'll take a bit of a performance hit with RAM (since some RAM needs to be used for Ubuntu) as well as not being able to fully use 3D acceleration.

---

### Post by kyphi on 2009-05-27
While I cannot help directly, I can tell you that running programs such as CS3 and PhotoImpact X3 in XP in VirtualBox works great.

When you have finished using your graphics program, you can "save the machine state" and the next time that you want to use it you can re-open it in a matter of seconds.

There is very little, if any, difference in functioning of the above mentioned graphics programs and using "the Gimp" - except that past habits are hard to break.

---

