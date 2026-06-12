---
title: "X Crash!!!! Help !!"
date: 2006-07-28
forum: Desktop Environments
---

### Post by visvak on 2006-07-28
my x has crahed. whenever i try to boot,
the Assembling RAID arrays always fails


 and then it says,

 ur x server has crashed. this is bcoz it is not cinfigured properly. restart gdm when u fix it. do u want to see detailed output of xserver ?

the error seems to be something like this -

mounting or loading (not sure) device  /dev/wacom/
no such device exists

this i am pretty sure is my fault. i added some extra repos (rarewares, debian-multimeida ) last time i was using ubuntu. and updated. evr since then i'm not able to access x.

pls tell me that there is some way to save my ubuntu install ?

i'm still able to login to a textbased ubuntu.

if there is no way to save it now, can anyone tell me how to backup my data thru the command line and burn it onto a cd for a reinstall ?

i'm posting this from my LiveCD which i really can get used to after my fully tweaked and customized ubuntu install. so pls i need help. fast !!

---

### Post by Tomosaur on 2006-07-28
> **visvak said:**
> my x has crahed. whenever i try to boot,
the Assembling RAID arrays always fails


 and then it says,

 ur x server has crashed. this is bcoz it is not cinfigured properly. restart gdm when u fix it. do u want to see detailed output of xserver ?

the error seems to be something like this -

mounting or loading (not sure) device  /dev/wacom/
no such device exists

this i am pretty sure is my fault. i added some extra repos (rarewares, debian-multimeida ) last time i was using ubuntu. and updated. evr since then i'm not able to access x.

pls tell me that there is some way to save my ubuntu install ?

i'm still able to login to a textbased ubuntu.

if there is no way to save it now, can anyone tell me how to backup my data thru the command line and burn it onto a cd for a reinstall ?

i'm posting this from my LiveCD which i really can get used to after my fully tweaked and customized ubuntu install. so pls i need help. fast !!

A wacom is a tablet peripheral. The device doesn't exist simply because you do not have one, I wouldn't worry about it.

Luckily, this little line should (hopefully) fix your problem.

Restart your computer and boot normally (so that X crashes)

Type this in at the command line (which is called a terminal):

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you for your password. Once you put it in, just follow the onscreen instructions to configure X. When you're finished, restart your computer. X should, hopefully, start normally, and everything will be back to normal.

---

### Post by DantePasquale on 2007-04-25
Hi, I've had a similar problem. reconfigure xserver-org same result. Weird thing is I get a "spinner" that moves with the mouse but then nothing. This was after a / file system crash. Any Ideas ???

---

### Post by DantePasquale on 2007-04-26
RESOLVED:

By re-installing ubuntu LTS! Too many files were corrupted could not run most shell commands so I couldn't edit or restore any files that I knew were bad. Culprit is memory errors brought on, most likely, by my laptop overheating because acpi doesn't see the fan.

Dante

---

