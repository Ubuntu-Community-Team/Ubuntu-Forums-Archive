---
title: "what is this command do"
date: 2009-01-05
forum: General Help
---

### Post by DarinB on 2009-01-05
what do these commands do?? before i mess things up

sudo dpkg-reconfigure -phigh xserver-xorg 

vs

sudo dpkg-reconfigure xserver-xorg

---

### Post by Elfy on 2009-01-05
It asks extra questions I believe.

If though you're trying to use it to deal with a video problem then from Hardy it doesn't do so anymore to my knowledge.

---

### Post by DarinB on 2009-01-06
i am using intrepid and i lost my refresh rate to 60hz and i had 800x600 res
i think it happened after i installed myst via wine i read that old games can mess up an mvidia geforce4 mx 420. so i tried adding a line to the xorg config, i ended up with a warning at the boot up of a parsing error do i want to use default i did and the res and refresh came back but then the next reboot was low res. 
i read about the dpk reconfigure.... so i tried it and it has been as good as new for the last few days.
i simply want to understand what the heck is going on. and did i actually fix it (by newbie luck of course)

---

### Post by adult swim on 2009-01-06
sudo dpkg-reconfigure -phigh xserver-xorg 
whenever you edited your xorg.conf, it messed it up so your session was launched in low graphics mode as a fall back.  dpkg-reconfigure is a command that reconfigures packages that have already been installed.  this means for you that it went back through and found your hardware, making changes as needed for it to work.  if you go back and look at your xorg.conf, the line you entered in is not there anymore.  the -phigh, read by the computer as -p high, is a flag that marks the priority of the questions that you are prompted with.

---

### Post by tuxxy on 2009-01-06
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

Carries out the same function as xfix from the recovery mode.

---

### Post by DarinB on 2009-01-06
so i got really lucky. 
I really am thankful for all your answers i spent some time trying to figure this whole mess out. 
much gratitude to all.

is it best to use the phigh or not???
i used the one with out.

---

### Post by adult swim on 2009-01-06
-phigh will pretty much do everything automatically.  remember all of those questions you had to answer in the terminal?  those wouldnt appear with the -phigh in there.  you could try both commands out to see the difference if you wanted. it wouldnt hurt anything.

---

### Post by dcstar on 2009-01-06
> **adult swim said:**
> -phigh will pretty much do everything automatically.  remember all of those questions you had to answer in the terminal?  those wouldnt appear with the -phigh in there.  you could try both commands out to see the difference if you wanted. it wouldnt hurt anything.

The -p attribute sets the Priority of questions the **debconf** package will ask you (dpkg-reconfigure uses debconf).

You can set the default value of this with:
```
sudo dpkg-reconfigure debconf
```

---

### Post by DarinB on 2009-01-07
thank you adult swim. i must have used the phigh because it was automatic. 
thank you to all. 
i don't understand the last post sudo dpkg-reconfigure debconf
what is that for? is it better or just something totally different?

---

