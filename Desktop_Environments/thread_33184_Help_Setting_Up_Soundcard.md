---
title: "Help Setting Up Soundcard"
date: 2005-05-09
forum: Desktop Environments
---

### Post by velayo on 2005-05-09
I decided to install kubuntu on my laptop. To my surprise everything worked flawlessly except for the soundcard.  The laptop is a AMS Tech Rodeo or Chicony 989.  I found a website with some information on how to setup linux to run on this kind of laptop.  However the site is in german and I can't understand the translation from Babelfish well enough to make it work. 

Please help me! This is the only thing keeping Kubuntu from running perfect on my laptop.  Let me know if you need any more information.

PS

Kubuntu keeps surprising me, every distro I tried on this laptop seemed to be too slow and had problems with various devices. Kubuntu however runs smoothly.  Cliking on a program brings it up almos instantly!!!!

---

### Post by defkewl on 2005-05-09
What's the name of your soundcard and what is wrong with it? Kubuntu didn't detect it? Or else?

---

### Post by velayo on 2005-05-09
Soundcard seems to be a Generic Yamaha YMF715.  Kubuntu didn't recognize it, I check the kernel modules and couldn't find anything for sound.  

Thanks for the fast reply!

---

### Post by wvslkr on 2005-05-09
[QUOTE=velayo]Soundcard seems to be a Generic Yamaha YMF715.  Kubuntu didn't recognize it, I check the kernel modules and couldn't find anything for sound.  

Thanks for the fast reply![/QUOTE]
 open console type [without quotes]  "sudo modprobe snd-opl3sa2" or "sudo modprobe snd-opl3sa2 isapnp=0"   if the first doesn'twork.  This should be the driver for your card.

Then go to control center and restart arts.  If all works, add the line to /etc/modules [without sudo]
and should work from restart. Good Luck:)

---

### Post by velayo on 2005-05-10
[QUOTE=wvslkr]open console type [without quotes]  "sudo modprobe snd-opl3sa2" or "sudo modprobe snd-opl3sa2 isapnp=0"   if the first doesn'twork.  This should be the driver for your card.

Then go to control center and restart arts.  If all works, add the line to /etc/modules [without sudo]
and should work from restart. Good Luck:)[/QUOTE]

Thanks for the help.  I tried the sudo command and it gave me an error.  The error said:
Failed to add device ... no such device exists.
And then gave me another error : Failed to install device ... device not found.

I have done more research and some people say that the soundcard is a Maestro 2 (ES1968), do you know a command for installing this card?

---

### Post by wvslkr on 2005-05-10
Your sound drivers are in /lib/modules/kernel/sound.  There is a couple of Maestro drivers listed.  All I can 
suggest is to try modprobe on different ones and see if they work.

If it accepts one without complaint  it should work.  You will then have to restart the soundserver and kmix.  
If you find one that works add to /etc/modules to make it permanent.

Hope that helps,Good Luck:)

---

### Post by mikecar52 on 2005-05-26
[QUOTE=velayo]Thanks for the help.  I tried the sudo command and it gave me an error.  The error said:
Failed to add device ... no such device exists.
And then gave me another error : Failed to install device ... device not found.

I have done more research and some people say that the soundcard is a Maestro 2 (ES1968), do you know a command for installing this card?[/QUOTE]
Did you get your sound card working? :???:

---

