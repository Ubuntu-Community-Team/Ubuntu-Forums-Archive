---
title: "Error"
date: 2005-09-28
forum: Desktop Environments
---

### Post by carlyoung on 2005-09-28
I installed Ubunto in duel boot my problem is I can't set the time or download any updates when it ask for my password none of my passwords work what am I doing worng  it also said that the files where hidden if this can't be fix is there a way to uninstall Ubunto and reinstall it?:(

---

### Post by mlomker on 2005-09-28
It should be the same password that you use to log in with.  If that doesn't work then [give this a try.]("http://www.ubuntuforums.org/showpost.php?p=312761&postcount=6")

---

### Post by Claudia Park on 2005-09-29
I also have an error, "user" (me) made a HUGE mistake and cannot access  2 folders that I moved into my Ubuntu system from WinXp. I placed them "outside" of the Home folder, into another "home" folder, into a second folder. I cannot change the permission setting and each time I start up the "home" folder is ignored.
These folders cannot be moved, cannot be deleted and cannot be viewed...it says I am not the "root" user. I tried being the root user, and it still didn't work.

Any suggestions on what to do would bel appreciated. What would be the best way to repair the faulty file system?

Thanks
Claudia

---

### Post by mlomker on 2005-09-29
> Any suggestions on what to do would bel appreciated. What would be the best way to repair the faulty file system?


**sudo chmod -R 777 /folder/name** should fix it from a terminal prompt.  You'll need to put in the proper path to the folder.  

Basically, whenver you get an error about not being root you can try putting **sudo** in front of the command that you are using.  The password that it asks for should be the same as your password.

---

### Post by Claudia Park on 2005-09-29
Thank you.
I was getting frustrated with this. Once I get the file system back where it should be eveything will be ok. This linux was crashing because of this problem, and only crashed when I tried to access these folders. Everything else is working except for my scanner, but that is just a question of finding the proper driver. The driver manager identifies it in the usb port but it isn't working. My printer did that (Dell 1700) and I put in HP Laser 4 and it works like a charm.

Thank you

I am loving linux more and more each time I use my computer.

Claudia

---

### Post by Claudia Park on 2005-10-03
HI,
I finally had to reformat the hard drive. I have said this before, and will say it again...I DO NOT like windows, especially XP. My Hard drive was messed up, XP did that to me a lot. It just wouldn't stay put. I now have  a squeeky clean hard drive, no windows just Linux. I forgot to copy some songs onto a CD, but that doesn't really matter.

I have set up the video, and media player, and now my only problem is to get my scanner working.

Thank you so much for your help, Linux is a learning or re-learning process for me. I know MsDos well but until I learn all the commands (where to find them too) I will be pretty disoriented.

Claudia

---

### Post by mlomker on 2005-10-03
> I know MsDos well but until I learn all the commands (where to find them too) I will be pretty disoriented.


You're very welcome.  You'll actually find linux a lot more comfortable than someone that is graphically oriented.  Most of linux's power is at the terminal prompt even today, but the graphical tools are improving every year.

---

### Post by Claudia Park on 2005-10-03
I started my adventures with computers with an Amega, and a Tandy, where you had change the floppy disk for each action and program. I then bought an IBM PS2 with what I considered a fast processor @ 25Mhtz, and a huge hard drive of 125 mb. I now own a Pentium 4 @ 2.2, and a 30G hd. It's a laptop. I loved windows 3.1 because you could control and change things in the dos, and if you knew how to "lie" to windows the configurations worked just fine. I dislike WinXp, but it came with this laptop and it's still on warranty, but I took the plunge with Linux anyway!

I had everything fixed except for the scanner error, and I went and tried a new "Easy Ubuntu" setup, and now I have to correct the error in the Totem again. 

Is there anyway to reconfigure the Device Drivers? 

I would also like to find out more about the terminal, the "how to" for beginners doesn't seem to have a section on this?

Thanks.
Claudia

---

### Post by mlomker on 2005-10-03
> Is there anyway to reconfigure the Device Drivers? 

Most things are loaded automatically by the hotplug service.  Everything that is manually loaded is in /etc/modules.

> 
I would also like to find out more about the terminal, the "how to" for beginners doesn't seem to have a section on this?


The command line in Ubuntu is the bash shell.  Here's a really [nice tutorial]("http://linux.org.mt/article/terminal").  It's for command-line newbies but you can search Google and find many others.

---

### Post by Claudia Park on 2005-10-03
Thanks,
That manual will be very useful. I wasn't sure where the main files were, this information is very useful.

Claudia

---

### Post by oddflux on 2005-10-03
I'm happy that the linux community extends beyond boarders. Claudia, try learning some shell scripting and other things. Good luck on your quest.

---

