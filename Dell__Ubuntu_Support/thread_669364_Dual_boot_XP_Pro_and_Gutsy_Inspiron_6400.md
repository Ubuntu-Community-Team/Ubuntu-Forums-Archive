---
title: "Dual boot XP Pro and Gutsy Inspiron 6400"
date: 2008-01-16
forum: Dell  Ubuntu Support
---

### Post by alejobar on 2008-01-16
I installed without problems my dual boot with xp Pro an Ubuntu Gutsy. Here is how I did it:

1- Resize your disc to create an unlocated space of 6gb (you can use more if you want, but after installing all that I need I still have 3gb free on the disc) with Acronis, you can do it from windows or boot from the acronis cd

2- Boot in to xp to let windows adjust to the new partition, xp will run a disk check up, let it finish and log in to windows, make sure that everything runs ok.

3- Boot from Ubuntu cd make sure you are connected to the internet open firefox to see if you can access the internet, once you are sure that ubuntu have internet connection proceed to install, when the partitioner starts do it manually. First create a swap partition of 300mb in the unlocated space that you create with Acronis, Second create a ext3 partition and on the size window don't forget to put an "/" to create a root file, then continue to install your ubuntu in this partition.

4- Because you start the installation with internet connection on, Ubuntu will find the drivers for the ATI card and also for the wireless, the firt time you boot in to Ubuntu it will ask you to install these drivers, make sure you do it!, reboot and voila!

5- You will have to do some tweaks in order to activate the extra desktop animations,if you want all the animations enable follow this steps: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz) 
And to improve the touchpad:
[http://www.ubuntu1501.com/2007/04/configure-synaptic-touchpad-settngs.html](http://www.ubuntu1501.com/2007/04/configure-synaptic-touchpad-settngs.html)

also maybe you had some problems with the Ubuntu splash screen at start up, download and install startup manager and follow this instructions:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen) 

I have an ATI x1400, first I follow the steps in the guide, then with startup manager I change the splash res to 1024 x 768 at 16bit and it worked!
 
Hope you can find this helpfull enjoy it!:guitar:

---

### Post by fred17 on 2008-01-22
> **alejobar said:**
> I installed without problems my dual boot with xp Pro an Ubuntu Gutsy.

New here. I was wondering if you still have MediaDirect from Dell installed on your laptop after all those steps, as I have the same laptop as you do, and am interested in dual booting Ubuntu and XP.

If so, it didn't mess up your laptop to have more partitions along with MediaDirect and XP partitions?

Thanks in advance

---

### Post by fred17 on 2008-01-24
Scratch that, I made it working!! :)

Thanks for your information in your guide, seems I made few mistakes when I first tried dual booting.

I can now confirm you can dual boot Vista Ultimate and Ubuntu in Dell Inspiron 6400/E1505 along with MediaDirect (works with its dedicated button), booting from Grub beautifully. I followed alejobar's guide, along with few tips from this website:
[HTML]http://www.users.bigpond.net.au/hermanzone/[/HTML]

There's only 2 small exceptions :
- For enabling visual effects, Ubuntu didn't ask me to enable Compiz, and I can't enable visual effects.
- It seems I needed a bigger swap partition because Suspend and Hibernate don't work. It's obvious you need at least the size of you memory ram for you swap partition (I have 1.5 gb).

Just a piece of advice, always backup your files! (shame on me...)

---

### Post by alejobar on 2008-02-01
Fred don't worry about the hibernation part, that doesn't work yet in our laptops, theres still a bug for that. And in order to ativate your compiz you need to install XGL just follow these steps: [http://ubuntuforums.org/showthread.php?t=541163](http://ubuntuforums.org/showthread.php?t=541163)

and don't forget to install your compiz manager to customize your effects :guitar:

---

