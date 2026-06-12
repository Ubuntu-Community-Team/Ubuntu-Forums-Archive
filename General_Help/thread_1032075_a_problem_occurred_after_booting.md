---
title: "a problem occurred after booting"
date: 2009-01-06
forum: General Help
---

### Post by e777ng on 2009-01-06
i have a problem in istalling ubuntu 8.10
after booting Of ubuntu bootable CD , It boot successfuly 
then allow me to choose the language and some chooses appeare 

the frist allow me to try it without any loss of information

and the second is istall ,when i choose one of them , the cd drive run for a while and a black screen appeare with the DOS prompt and the computer hange 

i used a desktop , proccessor amd 4600+ Athlon 64 X2 Daul
2.41Ghz , 2 gb ram , 250 Gb hard disk sataII ,DVD sataII

10 Gb frist partion for windows 
10 Gb Fat32 emty partion to choose it for ubuntu

there is another problem , 
the CD boot successfuly .. But when i lob into Dos system .. the Dos can't recognize the letter Of CD Driver .. and can't read the CD .. that's in Dos 

thx for help

---

### Post by thedarkwinter on 2009-01-06
hi

when you get to the menu where you can choose "try without installing" or "install" etc, there are some options at the bottom of the screen. I think pressing F4 (?) will bring up a menu where you can choose "safe graphics mode". This should enable you to boot into the live CD. After installing, the first boot should work fine too.

For the record, linux does not use "dos" so the commands are different. For instance, 

Also when you say you go into DOS, i think you meen the Linux command line interface. In this case, the cdrom does not have a drive letter, it is located in /media/cdrom

to view the contects:
```
ls /media/cdrom 
```

hope this is helpful to you.

cheers,
michael

---

### Post by e777ng on 2009-01-06
> **thedarkwinter said:**
> hi

when you get to the menu where you can choose "try without installing" or "install" etc, there are some options at the bottom of the screen. I think pressing F4 (?) will bring up a menu where you can choose "safe graphics mode". This should enable you to boot into the live CD. After installing, the first boot should work fine too.

For the record, linux does not use "dos" so the commands are different. For instance, 

Also when you say you go into DOS, i think you meen the Linux command line interface. In this case, the cdrom does not have a drive letter, it is located in /media/cdrom

to view the contects:
```
ls /media/cdrom 
```

hope this is helpful to you.

cheers,
michael

thx michael much , but " safe graphics mode " doesn't work ..
still black screen and Dos prompt appeares ..

my friend teel me that i must active xforcevesa Or use this command , but i don't know how can i use it ..

the command line appeare when i press F6 for more Option ..

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity intired=/casper/initrd.gz quiet splash --

can help me in that ..

thaaaanks

---

