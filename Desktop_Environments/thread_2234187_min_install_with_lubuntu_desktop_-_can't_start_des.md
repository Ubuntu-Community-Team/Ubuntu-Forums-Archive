---
title: "min install with lubuntu desktop - can't start desktop from cmd line"
date: 2014-07-13
forum: Desktop Environments
---

### Post by hbc2 on 2014-07-13
Hi,

I used the mini.iso to install ubuntu 14.04 and opted to go with Lubuntu destkop while installing.  

I only want the desktop for certain things, so I don't want it starting with I start my PC.

Clever me found from the internets that I can stop the desktop from loading by changing in grub

[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to "GRUB_CMDLINE_LINUX_DEFAULT="text"[/COLOR]

Great.  Only now I can't start it.  startx at command line does not work - the pc hangs on a black screen.   

Any tips on how I can start the desktop from the command line after booting?

Thanks.

---

### Post by sudodus on 2014-07-13
Try ```
sudo service lightdm start
```

and tell us if it works for you.


Edit 1: If not, you may have problems with the graphics chip/card. Please specify the brand name and model.


Edit 2: Do not use ```
[s]sudo startx[/s]
``` in a standard Lubuntu installation. I tried and borked my test system. I found that the following works for me in Lubuntu 14.04 LTS and I hope it works for you too :-)


***a. In a text screen***

Run this command ```
sudo service lightdm start
``` to *start* the graphical Lubuntu system.


***b. In the graphical desktop environment (Lubuntu)***

Start a text screen with a hotkey combination ***ctrl + alt + F1 .... F6***. Now you have both a text screen (for example at ***ctrl + alt + F1***) and the the graphical Lubuntu system (which you find with ***ctrl + alt + F7***).

Run this command ```
sudo service lightdm stop
```  to *stop* the graphical Lubuntu system.

---

### Post by Bucky Ball on 2014-07-13
startlxde

? For xfce4 it is:

startxfce4

... so there is some hope. :-k

---

### Post by will45 on 2014-07-13
If I remember rightly, you have to create a .xinitrc for LXDE to start with startx. To do this, do the following:

```
cd ~/
nano .xinitrc
```

We will now add the following to the .xinitrc:

```
exec startlxde
```

Then do CTRL+X, press y, then press enter. Now execute

```
startx
```


EDIT: Confirmed and edited. Source: [https://wiki.archlinux.org/index.php/LXDE#Starting_the_desktop](https://wiki.archlinux.org/index.php/LXDE#Starting_the_desktop)               The ArchWiki is brilliantly documented, and works with most distributions. ;)

---

### Post by Bucky Ball on 2014-07-13
Did you install 'lxde' from the command line when you rebooted the machine to a prompt after the install, or did you choose a machine profile when you got to that bit of the install?

If you install everything manually there are a few things you really need. lxsession would probably be one of them, along with lightdm or another desktop manager and lxwm (I think it is) the lxde window manager. They might not come in by default (I use the mini with xfce4 and there's always a few niggling things I need to install manually).

---

### Post by will45 on 2014-07-13
@Bucky Ball, just saying, the LXDE window manager is not lxwm, it is Openbox.

I'd love to do a mini someday :D

---

### Post by sudodus on 2014-07-13
The OP 'opted to go with Lubuntu desktop while installing', so many of those things should be fixed already.

---

### Post by Bucky Ball on 2014-07-13
> **will45 said:**
> @Bucky Ball, just saying, the LXDE window manager is not lxwm, it is Openbox.

I'd love to do a mini someday :D

Cheers. Don't love lxde so don't use it, but I've learnt something today. ;)

PS: For me, mini the only way to fly. If you have a spare partition, give it a whizz. Just DON'T install *buntu-desktop anything as that defeats the purpose, obviously. You only want the desktop environments and add the rest manually.

---

### Post by will45 on 2014-07-13
> **Bucky Ball said:**
> Cheers. Don't love lxde so don't use it, but I've learnt something today. ;)

PS: For me, mini the only way to fly. If you have a spare partition, give it a whizz. Just DON'T install *buntu-desktop anything as that defeats the purpose, obviously. You only want the desktop environments and add the rest manually.

I never install the *buntu-desktop meta packages. I'll have a go in Virtualbox before hardware though. I used up 2 hard drives in my partitioning (I went partition mad for the first time lol!). I always like building from ground up though, hence I like Arch!

---

### Post by sudodus on 2014-07-13
***a. In a text screen***

Run this command ```
sudo service lightdm start
``` to *start* the graphical Lubuntu system.


***b. In the graphical desktop environment (Lubuntu)***

Start a text screen with a hotkey combination ***ctrl + alt + F1 .... F6***. Now you have both a text screen (for example at ***ctrl + alt + F1***) and the the graphical Lubuntu system (which you find with ***ctrl + alt + F7***)

Run this command ```
sudo service lightdm stop
```  to *stop* the graphical Lubuntu system.

*Edit*: you can make aliases to reduce the amount of typing in text mode, for example

alias Lup='sudo service lightdm start'
alias Ldn='sudo service lightdm stop'

---

### Post by hbc2 on 2014-07-14
Hi all,


Thanks for all the replys!  I'm away from my PC and will not be back to it until the weekend.  


From memory I know I tried startlxde from the command line as well as putting it in a file.  I can't be 100% sure it was ~/.xinitrx but I know I read that archlinux thread pointed to by will45. In any case, when I typed startx it ran the x.org stuff then is ran the config file with the "exec startlxde"  line and died with an error. I don't recall the error msg but I recall thinking "Well, that's an improvement, no black screen of death that I can't even ctrl-alt-delete from."   I suspect the error message was something like file not found because I recall search all around my install for startlxde  but could not find it.   I was doning something like cd /  <hit return> ls -R | grep startlxde  (yeah, i know that's probably not the official way to do it but see comment below.)


I'm pretty sure startlxde is not on my system and I KNOW i installed lubuntu desktop.


sudodus:
I'll give your suggestion "sudo service lightdm start" a try over the weekend.  looks promising.  One question:  pressing ctrl+alt+F1 then does not kill the desktop, you have to follow that with "sudo service lightdm stop"?  


Bucky ball:
you wrote "Just DON'T install *buntu-desktop anything as that defeats the purpose".  I want to give "sudo apt-get install xfce4 xfwm4 lightdm synaptic xorg lxterminal gdm" that you've suggested but, honestly, the sound driver stuff is giving me lots of hell.  So I need to stick with *buntu-desktop until i get it figured out.  I did try Xbuntu-desktop (as a result of googling for info on your xfce4 suggestion) and that is working better than the Lubuntu on the sound front.  One thing I noticed is that speaker-test actually works in Xubuntu without any command line params.  However, it seems I can only get sound working when the desktop is running  (what I mean is if I ssh into the host while the desktop is NOT running on the host I don't get sound from speaker-test) but with Lubuntu speaker-test over SSH works without the desktop running (but with some command line params).  


Anyway, this is enough info for ten posts.  I'll give sudodus' suggestion about lightdm a try when I get back and let you all know.
 




--------------------




Just a bit of background: I've been a linux noob since 1997 (started and quit so many times I lost count).  Only this time I'm fed up with the Windows TAX completely so I bought a nice new PC and decided to get Xen going with a music player and if/when I needed to I'll spin up Windows VMs.  


I'm still trying to get my base install going, thus this and a few other threads (order of business: base os with a light desktop, MDP (maybe XBMC but I don't think I want much) and then Xen).  Fun stuff!

---

### Post by steeldriver on 2014-07-14
This is what worked for me to add a minimal, manually started Lubuntu desktop to 14.04 server:

```

sudo apt-get install --no-install-recommends lubuntu-desktop

echo 'manual' | sudo tee /etc/init/lightdm.override

echo 'lxsession -e LXDE -s Lubuntu' > $HOME/.xsession

startx

```

If you're sure you never want to use the GUI display manager to login, you can replace lubuntu-desktop by lubuntu-core, which iirc doesn't include lightdm as a dependency

```

sudo apt-get install --no-install-recommends lxde-common lubuntu-core 

echo 'lxsession -e LXDE -s Lubuntu' > $HOME/.Xsession

startx

```

(it seems to be necessary to install lxde-common explicitly in order to get the lxsession binary - see [http://ubuntuforums.org/showthread.php?t=2222849](http://ubuntuforums.org/showthread.php?t=2222849) ). Alternatively, if you just want to run an LX session (rather than the Lubuntu desktop themed one specifically) you should be able to do

```

sudo apt-get install --no-install-recommends lxde-common lxde-core 

echo 'lxsession -e LXDE -s LXDE' > $HOME/.Xsession

startx

```

---

### Post by Bucky Ball on 2014-07-14
If you're going to install *buntu-desktop anything, I repeat, just install the OS that belongs to that desktop. I.e. if you're installing ubuntu-desktop into a mini install you have defeated the purpose because you have now effectively installed Ubuntu. Same with lubuntu-desktop. If you're going that route, just install Lubuntu. No different and a waste of time going to the bother of a mini install. Save yourself some time and just install the full OS in the first place. ;)

---

### Post by sudodus on 2014-07-14
> **hbc2 said:**
> ...
sudodus:
I'll give your suggestion "sudo service lightdm start" a try over the weekend.  looks promising.  One question:  pressing ctrl+alt+F1 then does not kill the desktop, you have to follow that with "sudo service lightdm stop"?  


I tested it with 14.04 LTS, and it works like that for me:*** ctrl+alt+F1*** does *not* kill the desktop, you have to follow that with

```
sudo service lightdm stop
```

Run the command in the text screen!

---

### Post by will45 on 2014-07-14
> **hbc2 said:**
> Hi all,


Thanks for all the replys!  I'm away from my PC and will not be back to it until the weekend.  


From memory I know I tried startlxde from the command line as well as putting it in a file.  I can't be 100% sure it was ~/.xinitrx but I know I read that archlinux thread pointed to by will45. In any case, when I typed startx it ran the x.org stuff then is ran the config file with the "exec startlxde"  line and died with an error. I don't recall the error msg but I recall thinking "Well, that's an improvement, no black screen of death that I can't even ctrl-alt-delete from."   I suspect the error message was something like file not found because I recall search all around my install for startlxde  but could not find it.   I was doning something like cd /  <hit return> ls -R | grep startlxde  (yeah, i know that's probably not the official way to do it but see comment below.)


I'm pretty sure startlxde is not on my system and I KNOW i installed lubuntu desktop.


sudodus:
I'll give your suggestion "sudo service lightdm start" a try over the weekend.  looks promising.  One question:  pressing ctrl+alt+F1 then does not kill the desktop, you have to follow that with "sudo service lightdm stop"?  


Bucky ball:
you wrote "Just DON'T install *buntu-desktop anything as that defeats the purpose".  I want to give "sudo apt-get install xfce4 xfwm4 lightdm synaptic xorg lxterminal gdm" that you've suggested but, honestly, the sound driver stuff is giving me lots of hell.  So I need to stick with *buntu-desktop until i get it figured out.  I did try Xbuntu-desktop (as a result of googling for info on your xfce4 suggestion) and that is working better than the Lubuntu on the sound front.  One thing I noticed is that speaker-test actually works in Xubuntu without any command line params.  However, it seems I can only get sound working when the desktop is running  (what I mean is if I ssh into the host while the desktop is NOT running on the host I don't get sound from speaker-test) but with Lubuntu speaker-test over SSH works without the desktop running (but with some command line params).  


Anyway, this is enough info for ten posts.  I'll give sudodus' suggestion about lightdm a try when I get back and let you all know.
 




--------------------




Just a bit of background: I've been a linux noob since 1997 (started and quit so many times I lost count).  Only this time I'm fed up with the Windows TAX completely so I bought a nice new PC and decided to get Xen going with a music player and if/when I needed to I'll spin up Windows VMs.  


I'm still trying to get my base install going, thus this and a few other threads (order of business: base os with a light desktop, MDP (maybe XBMC but I don't think I want much) and then Xen).  Fun stuff!

If startlxde didn't work, I think I know why. And if you want text login, starting lightdm isnt the way to go as it is a display manager. (Just to say, im typing this on my tablet at the moment and im not good with touchscreen typing with big hands :))

Make sure lxsession is installed.
```
sudo apt-get install lxsession
```

Then replace ```
exec startlxde
``` in the .xinitrc with ```
exec lxsession
```

Hope it works

Will

---

### Post by hbc2 on 2014-07-20
I just tried both sudodus's and will45's suggestions.  Both worked.  Thanks!

I'm now in the process of rebuilding from scratch more in favor of  Bucky Ball's & steeldriver's approach of installing the desktop after doing a min install.  Steeldriver's suggestion of not needing a GUI login screen is what I will aiming for now.

Thanks for all your input.  I've learned a lot.

---

