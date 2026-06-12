---
title: "Windows doesn't boot after I installed Ubuntu"
date: 2005-08-10
forum: Desktop Environments
---

### Post by sathya on 2005-08-10
I installed ubuntu on my sytem which had four partitions.
I was running windows professional XP on my system.Ububtu is new to me.I chose "expert: to insall ubuntu and followed the instructions
When i tried GRUB boot id didnt work, I opted for LiLO boot,after that there is now display of the Microsoft windows XP in the boot menu, infact the computer just by default boots to ubntu without giving me an option to chose the OS.
I have installed XP in partition 1 and ubuntu in partition 4. I have not erased the exixisting OS.But all my files are in XP and I am unable to work on it.
As I have important and crucial files which I need to work on I am really troubled.
Kinldy help me solve this probelm ? How to edit the master boot record ?
Please help.

---

### Post by MrCheese on 2005-08-10
[QUOTE=sathya]I installed ubuntu on my sytem which had four partitions.
I was running windows professional XP on my system.Ububtu is new to me.I chose "expert: to insall ubuntu and followed the instructions
When i tried GRUB boot id didnt work, I opted for LiLO boot,after that there is now display of the Microsoft windows XP in the boot menu, infact the computer just by default boots to ubntu without giving me an option to chose the OS.
I have installed XP in partition 1 and ubuntu in partition 4. I have not erased the exixisting OS.But all my files are in XP and I am unable to work on it.
As I have important and crucial files which I need to work on I am really troubled.
Kinldy help me solve this probelm ? How to edit the master boot record ?
Please help.[/QUOTE]

Firstly, I always recommend newbies use Midnight Commander (mc) to play with system files - the editor is really good and navigation is really easy.

Boot ubuntu, open Synaptic and install package "mc"
open a root terminal (use your password as the sudo root user).
run "mc" - type mc at the # prompt
navigate to /etc
find & highlight lilo.conf, hit f5 & copy to lilo.conf.sav (for safety)
hit f4 & edit lilo.conf
your windows entry should look like :

other = /dev/hda1
  label = Windows XP - doesn't matter what you call it
  table = /dev/hda

and somewhere at the top of the file , if you want it to boot XP by default, 

default=Windows XP

Hit F2 to save the edited lilo.conf, and ctrl-o to put mc into the background so you can see the console again.

run lilo (type type liloo at the prompt) and all being well the new boot sector will be written. Check the output - it should be something like 

added linux
           Windows XP *

the * means default, which will be the linux entry unless you set it to Windows XP.

Remember, if all else fails, boot your XP install cd, chose the recovery console (not Automated System Recovery) and type fixmbr - a new Windows boot sector will be written. You can then boot an ubuntu live cd to get at your ubuntu system & play futrher, safe in the knowledge that even if lilo screws up you can still get back to XP. Like you'd want to........

---

### Post by npaladin2000 on 2005-08-10
I thought being unable to boot XP was a "feature?" :)

---

### Post by sathya on 2005-08-10
thank you Mrcheese, I will try it .

---

