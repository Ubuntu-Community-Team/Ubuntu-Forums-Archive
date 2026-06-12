---
title: "ATI drivers"
date: 2005-06-02
forum: Gaming &amp; Leisure
---

### Post by Dark Damo on 2005-06-02
Ok i found the X.Org 6.8 radeon drivers but they are .rpm can ubuntu use rpm?

---

### Post by Janne on 2005-06-02
[QUOTE=Dark Damo]Ok i found the X.Org 6.8 radeon drivers but they are .rpm can ubuntu use rpm?[/QUOTE]
Im a total linux newbie but maybe this link will help you out [http://www.ubuntuguide.org/#convertrpmtodebfile](http://www.ubuntuguide.org/#convertrpmtodebfile)

---

### Post by Dark Damo on 2005-06-02
[QUOTE=Janne]Im a total linux newbie but maybe this link will help you out [http://www.ubuntuguide.org/#convertrpmtodebfile](http://www.ubuntuguide.org/#convertrpmtodebfile)[/QUOTE]
 Thank you i will look at that now :D

---

### Post by ernstp on 2005-06-02
Ey, slow down! Ubuntu allready has the drivers packaged. (and probably installed on your computer?)
The package is called xorg-driver-fglrx. Install that!

Otherwise, there's plenty of tips on the forum allready, use the searchfunction!

If you want the latest version of the driver, check out this:
HOWTO: ATI drivers 8.12.10:
[http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)

---

### Post by Dark Damo on 2005-06-02
[QUOTE=ernstp]Ey, slow down! Ubuntu allready has the drivers packaged. (and probably installed on your computer?)
The package is called xorg-driver-fglrx. Install that!

Otherwise, there's plenty of tips on the forum allready, use the searchfunction!

If you want the latest version of the driver, check out this:
HOWTO: ATI drivers 8.12.10:
[http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)[/QUOTE]
 what would i type in terminal to install that lol ima linux noob :D

---

### Post by DarkKnight on 2005-06-02
[QUOTE=Dark Damo]what would i type in terminal to install that lol ima linux noob :D[/QUOTE]
 sudo apt-get install xorg-driver-fglrx 

Read the link he posted, it lists everything step by step. :)

---

### Post by Janne on 2005-06-02
[QUOTE=DarkKnight]sudo apt-get install xorg-driver-fglrx 

Read the link he posted, it lists everything step by step. :)[/QUOTE]
I'll be trying that too. I've already followed like 3 how-to's without success. Pretty soon I'll be busting up my damn ATI card for not working  ](*,)

---

### Post by Curlydave on 2005-06-02
The drivers on the site are the newest ones, the packaged ones you're being told to DL are older ones.

I tried for days to get the ones on their site to work, but I couldn't do it. There's a tutorial available, but it just gave me errors durring several steps. Double-clicking on a .exe or a script file just isn't happening here either.

---

### Post by Dark Damo on 2005-06-02
[QUOTE=Curlydave]The drivers on the site are the newest ones, the packaged ones you're being told to DL are older ones.

I tried for days to get the ones on their site to work, but I couldn't do it. There's a tutorial available, but it just gave me errors durring several steps. Double-clicking on a .exe or a script file just isn't happening here either.[/QUOTE]
 argh why make it so hard? i might aswell as trade in my 9200se for some NVIDIA card

---

### Post by Dark Damo on 2005-06-03
[QUOTE=Dark Damo]argh why make it so hard? i might aswell as trade in my 9200se for some NVIDIA card[/QUOTE]
 ok the command  sudo apt-get install xorg-driver-fglrx doesnt work

---

### Post by Dark Damo on 2005-06-03
[QUOTE=Dark Damo]ok the command  sudo apt-get install xorg-driver-fglrx doesnt work[/QUOTE]
 says something bout E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Curlydave on 2005-06-03
[QUOTE=Dark Damo]says something bout E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/QUOTE]

Yep, same problem here. I did a million things to try to fix it, but still got the E: error. I dont' even have an E drive.

---

### Post by Dark Damo on 2005-06-03
[QUOTE=Curlydave]Yep, same problem here. I did a million things to try to fix it, but still got the E: error. I dont' even have an E drive.[/QUOTE]
 hehe i dont either

---

### Post by DarkKnight on 2005-06-04
[QUOTE=Dark Damo]says something bout E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/QUOTE]
 sudo apt-get install xorg-driver-fglrx

Should work fine... o_O
Try enabling Universe in synaptic.

Also, the E: is just to tell you it's an error ;)

---

### Post by Curlydave on 2005-06-04
Dark, that gives you the older drivers, which are easy to get/install. They're even in the package manager. The problem is trying to get the new drivers available on the ATI website.

---

