---
title: "Wubi doesn't work"
date: 2009-06-22
forum: General Help
---

### Post by revan86 on 2009-06-22
Hi everyone!
 
I'm having issues with the Wubi installer: I downloaded the 9.04 version of Kubuntu and Wubi. The installation seemed to work fine, but after rebooting my machine, the GRUB menu didn't show up. I looked inside the "Ubuntu' folder, and it was like 700 megabytes tops. At first I thought the stand alone installer is broken so I used Daemon Tools to mount the LiveCD and tried that Wubi.exe, but to no avail. I could easily uninstall the 700mb Kubuntu, though.
I have a brand new 500gb HDD ( 2 days old), no fragmentations or alike. I would like to install Kubuntu to a 100gb partition next to XP, but Wubi doesn't let me do it.
 
Any ideas? :(

---

### Post by Idefix82 on 2009-06-22
There is some confusion going on. Wubi is precisely the thing that you want to use if you don't want to install Ubuntu on a separate partition. Wubi installs Ubuntu as if it was a Windows application.

For installing on a separate partition, restart the computer with the CD in the drive, seconds after the computer starts hit the appropriate F-key to boot from CD, then say that you want to install and take it from there.

You might also want to shrink the Windows partition from within Windows before you do all that.

---

### Post by revan86 on 2009-06-22
Sorry for the misunderstanding, let me explain it: my HDD is divided into a 400gb and a 100gb partition( this is where Windows is installed). I'd like to install Kubuntu on the same partition as Windows (the 100gb one), so both OSs can see the 400gb partition. That's why I tried to use Wubi in the first place. What am I doing wrong?

---

### Post by Idefix82 on 2009-06-22
I have no experience with Wubi myself and I don't know why installing it didn't work for you. But why don't you create a separate partition for Ubuntu (say 100 out of the 400 GB) and install Ubuntu there? It will still see the other two partitions and you will be able to read them and write to them. Also, if Windows breaks (it's shocking but it's said to happen ;) ) then you can still boot into Ubuntu and recover the data or continue working, which won't work with a Wubi installation.

---

### Post by Spaceman7o on 2009-06-22
Ive used wubi and my friend recently installed wubi as of yesterday and we never got that problem. The only thing i could suggest is delete wubi using windows add/remove prgrams in control panel and deleting all the files. Then re-installing wubi then try again this is an annoyance i know but its the only way i can see to even try and solvethis.

Although i now have partitioned my drive and use ubuntu seperatly as its easier if something goes wrong and faster.

---

### Post by revan86 on 2009-06-22
Thanks for all your answers, I'm now downloading **Wubi 9.04 (r134RC), **maybe that will help.

---

### Post by james.brantley on 2009-06-22
> **revan86 said:**
> Thanks for all your answers, I'm now downloading **Wubi 9.04 (r134RC), **maybe that will help.

[SIZE=3]Not to talk bad about Wubi but you would have a much faster and stable machine if you did not use it. When you're using Wubi you have two OS's running at the same time! See how this could slow you down? I started out with Wubi but learned quickly it is not the best way to go![/SIZE]

---

### Post by hibliss on 2009-06-22
> **james.brantley said:**
> [SIZE=3]Not to talk bad about Wubi but you would have a much faster and stable machine if you did not use it. When you're using Wubi you have two OS's running at the same time! See how this could slow you down? I started out with Wubi but learned quickly it is not the best way to go![/SIZE]

That is not really true. When you use Wubi and boot in to Ubuntu, Windows is not running, you are just using shared space and the Windows bootloader, and Wubi makes the Ubuntu install think it is on a proper EXT partition (when it is actually on an NTFS partition).

I have used Wubi in the past when I was first trying Ubuntu, and it ran just fine. The biggest issue with Wubi is that it is dependent on the health of your Windows install, which is a dangerous dependency, and if the Windows filesystem has any fatal problems, so will your Ubuntu install. Another downside (a large one) of Wubi is that if your Windows partition is fragmented, it will degrade the performance of the OS.

Wubi is not a Virtual Machine, read the FAQ here - [http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php")

What you are talking about seems to be running Ubuntu in Virtual Machine, which IS running one OS inside another.

---

### Post by james.brantley on 2009-06-22
> **hibliss said:**
> That is not really true. When you use Wubi and boot in to Ubuntu, Windows is not running, you are just using shared space and the Windows bootloader, and Wubi makes the Ubuntu install think it is on a proper EXT partition (when it is actually on an NTFS partition).

I have used Wubi in the past when I was first trying Ubuntu, and it ran just fine. The biggest issue with Wubi is that it is dependent on the health of your Windows install, which is a dangerous dependency, and if the Windows filesystem has any fatal problems, so will your Ubuntu install. Another downside (a large one) of Wubi is that if your Windows partition is fragmented, it will degrade the performance of the OS.

Wubi is not a Virtual Machine, read the FAQ here - [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

What you are talking about seems to be running Ubuntu in Virtual Machine, which IS running one OS inside another.

I suppose it is a personal opinion about Wubi, _*in my experience *_using Wubi does slow things down greatly. Wubi is not a true install. (ok, I'm wrong about the install) It is ran as a Windows application. I am a user, not an expert and I learn something new about Ubuntu/Linux on a dialy basis. I just know that my machine ran much faster after I got rid off Wubi and did a true install.


> **Is this running Ubuntu within a virtual environment or something similar?**

             No. This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition. Thus we spare you the trouble of creating a free partition for Ubuntu. And we spare you the trouble to have of havi
ng to burn a CD-Rom.
Ok so it is a true install, but in my case the difference between Wubi and full install was night and day! Even Firefox ran faster under a full install! I'd be curious to hear from others who have experienced faster systems with a full install!

---

