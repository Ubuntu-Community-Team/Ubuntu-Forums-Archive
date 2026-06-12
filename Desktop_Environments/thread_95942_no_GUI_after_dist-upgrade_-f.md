---
title: "no GUI after dist-upgrade -f"
date: 2005-11-27
forum: Desktop Environments
---

### Post by eljaco on 2005-11-27
Hey,

I recently upgraded to 5.10 (Breeze) and it was running fine. I don't remember why I did this (probably to install some program or because I read it in some post) but I called

> apt-get dist-upgrade -f

and it then asked me to restart. Once the system booted back up, I only got the command login. I tied running startx, but this comes up (same for gdm and kdm)

> sudo: startx: command not found

Please let me know if there is some diagnostic or troubleshooting steps I should follow in order to get this fixed.

Also, I just ran

> apt-get upgrade

and there seems to be a lot of dkpg errors. The summary at the end specifies errors encountered while processing postfix, mailx, mutt, and lsb-core.
I have no clue what to do.

---

### Post by Xian on 2005-11-27
You might start by posting the error messages.
Other than that, I really wouldn't know where to start.

$ sudo apt-get -f install

What is the ouput of this command in the terminal?

---

### Post by eljaco on 2005-11-27
[QUOTE=Xian]
$ sudo apt-get -f install

What is the ouput of this command in the terminal?[/QUOTE]

> 0 upgraded, 0 newly installed, 0 to move and 2 not upgraded


I ran apt-get upgrade and the result was:
> The following packages have been kept back: libclan2-sound  libopenexr-dev

I can't seem to reproduce the dpkg errors I got before. The only thing I've done is I ran apt-get install xorg* to see if I was missing an X component. Nothing changed. Still get > bash: startx: command not found

---

### Post by az on 2005-11-27
sudo apt-get install ubuntu-desktop

---

### Post by eljaco on 2005-11-27
w00t!
The ubuntu-desktop did the trick.

Thanks a bunch!

---

### Post by Xian on 2005-11-27
Love the hat, azz. :)

---

### Post by RevNomad on 2005-11-27
Can we reopen this discussion?:( 

I just attempted a blissfully ignorant update while at a hotel.  (my only source of fast connection.  

The upgrade did not work, I suspect it tried to upgrade the OS but don't know.  Now I have no gui.  As a new linux user I have no command of the command line.  

Help?  ::he said in a small voice:::confused:

---

### Post by RevNomad on 2005-12-07
Finally did a complete wipe and reinstall.  NTP

---

