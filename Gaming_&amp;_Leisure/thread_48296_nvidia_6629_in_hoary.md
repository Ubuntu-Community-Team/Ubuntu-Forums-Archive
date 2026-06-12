---
title: "nvidia 6629 in hoary"
date: 2005-07-11
forum: Gaming &amp; Leisure
---

### Post by zeromod on 2005-07-11
ok im so tired so please excuse any insults inadvertantly thrown toward the ubuntu distro, but for christ's sake i wish it would work for me lol. ok ive fallen a victim of the nvidia /xorg/ubuntu bug whereas my mouse is respondant but everything else "x" stops and locks up. however it appears as my hard drive is still moving along. so after some halfwit answers and numerous trial and error configs including adding the line 

option "render accel" "false" 

to my xorg.conf device section. I was ready to freak out and switch distros right now. but i like ubuntu and if not for this and this alone id be happy as a friggin lark with it. 
so i did this. i ran a sudo u name whatever command and grabbed my kernel source stuff with apt. then i downloaded the archived nvidia 6629 driver package. then ctrl alt f1 then sudo /etc/init.d/gdm stop  then sudo sh NVIDIA package whatever. it wanted to download the files but i know that they arent there so it compiled it itself. and gave a rivafb module warning after i started x again i boot fine ran a lsmod no sight of riva but nvidia is there i commented out the render accell in my config file. and so far (30 minutes) no lock up. but.. and a big one at that. i cant play some of my previously installed games. ie: criticalmass it segfaults,, foobillard it segfaults probably more. and biggest one cedega. segfaults no more gta3 and diablo? no way man ill bail quick lol. now i know its due to my downgrade but i cant have the new  driver if im gonna lock up cause it gives me a heartattack. ive tried using synaptic to "completely remove" these games including cedega. and reinstall them including a sudo dpkg -i cedega etc etc. but they still segfault for gods sake man tell me what i need to do to get my games back. thanks in advance

---

### Post by mp3guy on 2005-07-12
Remove any nVidia stuff you already have on, and use this 

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by zeromod on 2005-07-12
im not about to install that driver again. its buggy horrid id rather use nv or vesa thanks for the help but im trying to repair my 6629 driver isntall

---

