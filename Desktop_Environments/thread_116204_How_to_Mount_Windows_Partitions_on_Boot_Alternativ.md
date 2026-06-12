---
title: "How to: Mount Windows Partitions on Boot Alternative way!!"
date: 2006-01-12
forum: Desktop Environments
---

### Post by linuxden on 2006-01-12
Ok my first How to in the Ubuntu Forums...

To all Linux Wizzards out there Stop reading the "how to" it aint for you....(just so you dont go "but i have a quicker way...")
Allthough constructive criticsim is cool...!

Ok for the noobs that want to mount windows partitions but dont want to use the command line or dont know how to get the fstab or just dont wanna...
Here it goes...:

For this how to you will need:

#your Ubuntu Install cd
#Ubuntu installed on your computer
#5 minutes

Ok now lets assume you have 2 partitions on your hard drive Hda1 and Hda2... Hda2 has linux and hda1 has windows...

ok insert the install cd into the drive and then reboot the computer and boot from CD (just the same as when you installed for the 1st time)

You get a prompt after a paragraph of text telling you to just press "enter" for the default installation.
Well just dont press "enter" yet.... Type ```
 rescue 
``` and then press "enter"....

You will boot into rescue mode...

Type ```
 install-grub hda2 
``` assuming that hda2 is where linux is installed...

The screen will ask you which partition you want to mount as / (<---root) select hda2 (once again assuming that hda2 is where linux is installed)

Let the grub installer install grub and once finished reboot...

Once you have rebooted you will see that your windows partition apears on boot up as hda1 (assuming hda1 is windows...)

Hope it helps anyone in need of an automated way top mount partitions on boot up....

---

### Post by linuxden on 2006-01-12
is my "How to" that pointless....??? that i get not even a "bad" response...??? 

I remember when i started using linux on a dual-boot mounting my win partition was a major thing....

Guess it isnt now days...

---

### Post by Thirsteh on 2006-01-12
I don't see the point of this how-to. It seems harder and more troublesome to do this than manually editing the fstab, or mounting manually. Re-installing GRUB will in no ways affect your fstab or ability to mount your windows partition - Your introduction is remarkably misleading. Additionally, if you do have a Windows partition, 9/10 times, GRUB will already have it listed when you've installed Linux.

Also, it is my opinion that you are being rather rude in the how-to. I doubt that newcomers seeking to broaden their knowledge of Linux like to be called "noobs" and talked at like they're... below you?

And lastly, the fact that you are telling experienced users to bugger off at the very top of the topic pretty much tells any person with "half a brain" that you don't really know what you're doing, or you're not sure if this is the appropriate thing to do.

Just my 5 cents. (And yes, it was constructive criticism)

---

### Post by aysiu on 2006-01-12
Does this HowTo mount Windows partitions or add Windows to the Grub menu?

I also think the HowTo is a bit self-defeating. A "noob" probably won't know if Windows is hda1 or hda2 or whatever.

---

### Post by linuxden on 2006-01-13
[QUOTE=Thirsteh]Just my 5 cents. (And yes, it was constructive criticism)[/QUOTE]

Errrr do i sense sarcasm... lol

Thanks for the constructive criticism... I dont see me calling Noobs noob being rude i myself am a noob with regards to networking and systems administration and do not find it rude if i am called so... If i offended anyone in doing so... My appologies.... 

[QUOTE=Thirsteh]
And lastly, the fact that you are telling experienced users to bugger off at the very top of the topic pretty much tells any person with "half a brain" that you don't really know what you're doing, or you're not sure if this is the appropriate thing to do.[/QUOTE]

The buggering off only comes from you... I am merely informing people that know how to edit fstab to stop reading for it is pointless to do so...
Also where does that show that i do not know what i am doing or the appropriate thing to do??? 

[QUOTE=Thirsteh]Your introduction is remarkably misleading. Additionally, if you do have a Windows partition, 9/10 times, GRUB will already have it listed when you've installed Linux.[/QUOTE]

Not so automaticly, otherwise there would be no threads in the forums asking how to mount win partitions on boot up...

I think also that you have not understood the point of my how to...
Its not to add windows to the grub boot loader... Its to "mount" the win partition on boot... ( it is remarkebly easy to do so using this method... Its automated...)

Or perhaps am completely confused as to what you were trying to say...

?????????????????

Anyways i just thought it might be useful to share something new...

Aysiu,

The how to is to mount win partitions on boot... Or any other OS i myself have 4 linux distros on my test lappy... so for me it was extra useful..

Point taken about the "new" Linux user perhaps not knowing what Partition windows was on...)

ps: sorry for the slow response time... wife doesnt like me to use Comp after dark... ;o)

---

### Post by Thirsteh on 2006-01-13
You are aware that your guide has absolutely nothing to do with mounting your NTFS partition, right?

---

### Post by art on 2006-01-13
I think the confusion is about naming conventions. I am pretty sure ubuntulifestyle means **booting** to Windows automatically, not **mounting** it while in linux, i.e. the default GRUB entry. Which could also be changed in /boot/grub/menu.lst, but...

---

### Post by linuxden on 2006-01-13
[QUOTE=ubuntulifestyle]
Once you have rebooted you will see that your windows partition apears on boot up as hda1 (assuming hda1 is windows...)

Hope it helps anyone in need of an automated way top mount partitions on boot up....[/QUOTE]


Ok Yes i am using the Grub installation from the rescue mode on the install CD But it also mounts partitions Automaticly... That is what the how to is about so it has absolutely everything to with mounting partitions....

I asked for constructive criticism not just telling me that i have no idea what i am talking about... :o

---

