---
title: "Visual Effects won't turn on after upgrade to 9.04. Help plz! =("
date: 2009-04-24
forum: General Help
---

### Post by Danish989 on 2009-04-24
I'm an ubuntu newb, and I just upgraded from 8.10 to 9.04.

However, now I can't use the Extra Visual Effects =(

Ever since I restarted after the upgrade, no more wobbly windows or anything.

I right-clicked desktop>>change desktop background>>Visual Effects and tried clicking on Extra to turn it on, but each time I get the message that says:

Searching for available drivers...
Desktop effects can not be enabled.

I need help! My desktop just isn't the same anymore =(

Thanks in advance!

---

### Post by linuxuser21 on 2009-04-24
What's your video card?

---

### Post by Danish989 on 2009-04-24
I tried running Terminal, to find out about my but my video card using lspci, but it just wouldn't start. A window would open that would say "Starting Terminal" but then it just disappears.

However, my graphic card is Intel Corporation Mobile GM965/GL960 Integrated Graphic Controller.

---

### Post by gus.ke on 2009-04-25
I have been having the same problem with an Intel X3100 card.

---

### Post by gus.ke on 2009-04-25
If this is any help, this did not occur when I was using the BETA release of 9.04.

---

### Post by turezky on 2009-04-25
Go to 'System -> Administration -> Hardware Drivers' and try to de- and then reactivate your drivers. Remember to reboot after each step. Then go to 'Appearance' menu again and try switching the effects on again.
Worked for me (nVidia Go 7400).
Also you might want to try to roll-back to previous driver version if they were working.

---

### Post by linuxuser21 on 2009-04-25
> **turezky said:**
> Go to 'System -> Administration -> Hardware Drivers' and try to de- and then reactivate your drivers. Remember to reboot after each step. Then go to 'Appearance' menu again and try switching the effects on again.
Worked for me (nVidia Go 7400).
Also you might want to try to roll-back to previous driver version if they were working.

I believe Ubuntu automatically does this when one selects "Enable extra effects".  I think that's the drivers it searches for when it says:
> **Danish989 said:**
> Searching for available drivers...

---

### Post by Old_Grey_Wolf on 2009-04-25
If you have the Intel graphics chip set try this link [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by Bob2893 on 2009-04-25
I have this  problem too since the upgrade to 9.04.

Seems to be wide spread. Nothing in theses replies works for me, hope the experts keep at it to help us all with more suggestions.

Bob

> **Danish989 said:**
> I'm an ubuntu newb, and I just upgraded from 8.10 to 9.04.

However, now I can't use the Extra Visual Effects =(

Ever since I restarted after the upgrade, no more wobbly windows or anything.

I right-clicked desktop>>change desktop background>>Visual Effects and tried clicking on Extra to turn it on, but each time I get the message that says:

Searching for available drivers...
Desktop effects can not be enabled.

I need help! My desktop just isn't the same anymore =(

Thanks in advance!

---

### Post by Old_Grey_Wolf on 2009-04-25
See if this link helps [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by nhshah7 on 2009-04-26
one of the links above worked for me! im on an hp dv6500 with intel x3100

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

follow these steps and when it asks u for more info in teh terminal hit yes
then when it asks to do something with the blacklist. hit yes. 

that did it for me!

---

### Post by Tipped OuT on 2009-04-26
Your card is probably black listed. You can  google a guide on how to enable Compiz Fusion on black listed cards.

---

### Post by ram4nd on 2009-04-26
I have the same problem, my card worked in previous versions, but not in 9.04. There is no driver for my video card in Hardware Drivers. I have ati x200m.

---

### Post by DracoJesi on 2009-04-26
> **Bob2893 said:**
> I have this  problem too since the upgrade to 9.04.

Seems to be wide spread. Nothing in theses replies works for me, hope the experts keep at it to help us all with more suggestions.

Bob

yep, I to have this bug, I'm running one of the Via UniChrome chipsets, forget which one, I have OpenChrome installed ye when I go to enable high visual effects, it tells me, driver not found and I get the same message...

I'll try the suggestions here and see what happens,

>  Your card is probably black listed. You can google a guide on how to enable Compiz Fusion on black listed cards. 

why would it all the sudden be black listed in 9.04 but not 8.10?

my terminal icon is gone btw, in place of Root Terminal, which crashes, the orginal program is still there though... I can use the key combo I set to open it, lucky me :)

---

### Post by DracoJesi on 2009-04-26
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y

```

and we have lift off!

thanks for the help :)



ok now who here still needs to get compiz running?

well not quite, I'm having problems with the cube,  locking up my workspaces, but this is nothing new, it's finicky with my driver/GPU which is probably why it was blacklisted, however, once it is configured and all... i i's good to go....

now how many times will I need to re-install compiz....

---

### Post by studiodude on 2009-04-26
On Acer Extensa with Intel X3100 the above method worked straight away after 9.04 update messed it up.


just incase its not  above anymore.....


[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

And thanks.....

---

### Post by captpicard12 on 2009-04-30
I've got the issue on an ATI Mobility radeon RV350 9600 M10.  I can't get compiz or xwinwrap or anything!!!

---

### Post by emarkay on 2009-04-30
Note: anyone with any display issue PLEASE tell us your video card type, PC type and Ubuntu version!

As for ATI and 9.04, there are some serious problems - see here: 

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by skyjap on 2009-05-16
Hi all, i also having the same problem with my graphic card.

Model:Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

It is solved after skip the blacklist using Compiz-Check!!!

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by orlox on 2009-05-16
personally, I think its more efficient to deactivate the blacklist myself

```

gedit ~/.config/compiz/compiz-manager

```
And add to the file this:
```

SKIP_CHECKS=yes

```
Save

---

### Post by entr3p on 2009-06-04
You can remove the blacklist yourself easily. You can even re-enable the blacklist as well. Hopefully this article helps you out.


[Fix Intel graphics on Ubuntu 9.04 - Enabling visual effects]("http://www.learningubuntu.com/articles/fix-intel-graphics-ubuntu-904-enabling-visual-effects")

---

### Post by FirstByté on 2009-10-19
For some reasons I'ld like to resurrect this thread.

I have issues getting Compiz Effect running. 

```
Gathering information about your system...

 Distribution:          **Ubuntu 9.04**
 Desktop environment:   GNOME
 Graphics chip:         **Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)**
 Driver in use:         **intel**
 Rendering method:      **AIGLX**

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ **[COLOR="Lime"]OK[/COLOR]** ]
 Checking for non power of two support...          [ **[COLOR="Lime"]OK[/COLOR]** ]
 Checking for composite extension...               [ **[COLOR="Lime"]OK[/COLOR]** ]
 Checking for FBConfig...                          [ [COLOR="Lime"]**OK**[/COLOR] ]
 Checking for hardware/setup problems...           [[COLOR="Red"]**FAIL**[/COLOR]]

There has been (at least) one error detected with your setup:
[COLOR="Red"] Error:[/COLOR] Software Rasterizer in use 

```
my lspci reports:
```
~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)

```

I just reverted to xserver-xorg-video-2.4 to fix my FF draggy issue. Which has been fine but no more Compiz Effects. 

I have once gotten round the blacklist after my upgrade to Jaunty by commenting the blacklist checking in

**/usr/bin/compiz**
```
 **[...]**
# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
[COLOR="Red"]#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"[/COLOR]  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
**[...]**
```

before but it doesn't seem to be doing the trick again.

Note: **I've been to kernel 2.6.31-14** and now, had to purge my system of it because, the WiFi was totally broken and I couldn't get any way around Broadcom's 'wl; so **I'm back to kernel 2.6.28-15**

---

### Post by Old_Grey_Wolf on 2009-10-20
> **FirstByté said:**
> For some reasons I'ld like to resurrect this thread.

I have issues getting Compiz Effect running.

Try this thread if you have done what I suggest below already [http://ubuntuforums.org/showthread.php?t=1018240](http://ubuntuforums.org/showthread.php?t=1018240)

Try reverting the Jaunty Xorg intel driver to 2.4:

Add the following lines to your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```

Import the appropriate GPG key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
```

Install the driver:
```
$ sudo apt-get update
$ sudo apt-get install xserver-xorg-video-intel-2.4
```

Restart the computer.

Check that the CompizConfig Settings Manager is installed.

---

### Post by FirstByté on 2009-10-21
> **Old_Gray_Wolf said:**
> Try this thread if you have done what I suggest below already [http://ubuntuforums.org/showthread.php?t=1018240](http://ubuntuforums.org/showthread.php?t=1018240)

Try reverting the Jaunty Xorg intel driver to 2.4:

Add the following lines to your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```

Import the appropriate GPG key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
```

Install the driver:
```
$ sudo apt-get update
$ sudo apt-get install xserver-xorg-video-intel-2.4
```

Restart the computer.

Check that the CompizConfig Settings Manager is installed.

Thanks greatly **Old_Grey_Wolf**,

I took a peek at the Ubuntu 9.10 beta today but couldn't resist it's functionality and aesthetics. I've upgraded to Ubuntu 9.10 which HAS SOLVED ALL MY (mojor) ISSUES [and added beauty]: Graphics, WiFi & Compiz Effects. ALL OUT-OF-THE-BOX. Other issues like my laptop remote, Fingerprint reader etc. can wait till forever.

I may keep the kernel 2.6.28-15 hanging in there to try and solve some of it's issues when I can following the link you posted. Hopefully it would help those who like me didn't want to move to Koala 9.10 due to skepticisms. I WAS SO WRONG AND NAIVE!

Thanks once again.

**I FEEL IN-LOVE with Ubuntu 9.10 right from the splash screen!**


[SIZE="5"][COLOR="Red"][FONT="Courier New"]**Thanks Ubuntu guys and Canonical. YOU GUYS ROCK THE EARTH!!!**[/FONT][/COLOR][/SIZE] :popcorn: :guitar:

I'll buy you all Nasi Lemak!!!

---

