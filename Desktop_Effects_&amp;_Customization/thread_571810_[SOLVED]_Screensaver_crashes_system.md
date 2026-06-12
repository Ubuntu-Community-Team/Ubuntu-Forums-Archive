---
title: "[SOLVED] Screensaver crashes system"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by perixx on 2007-10-09
I hope that someone can help on this one:

Probably the first time the screensaver showed up, the screen went black and the system locked up with a line saying "calculating particles" or sth. similar. Only poweroff worked. 
When I tried many different other screensavers in the menu, they all seemed more or less perfectly working - apart from some graphic artifacts in the preview window in some cases. 

When I tried to select the 'bad' screensaver, the screen just froze and the system hung up. Now I cannot access the screensaver's menu anymore to change to a 'harmless' one, as the PC will crash every time I'm trying to do so...

Does anybody know about this problem and can confirm it?

I need to know where the settings file for the screensaver is located/what's it's name, so I can manually switch the screensaver application to a save one!


Please help...!


Configuration:
Athlon Thunderbird 1,2GHz
MSI MS-6330 Motherboard with 512MB SD-RAM and AC'97 onboard sound
ATI Rage 128
160GB Hitachi HDD
SD-M1502 Toshiba DVD
Level1 10/100 Mbit LAN card with DSL modem connected

---

### Post by JurB on 2007-10-10
I think you can change the screensaver by running gconf-editor and going to apps > gnome-screensaver.
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/106060") at Launchpad

---

### Post by perixx on 2007-10-10
Thanks, JurB for letting me know about the confirmed bug... I also suspected my graphics card being the cause of this mess, as it produces some strange side-effects in the screensavers preview window with some sc-effects.

I tried to follow your suggestion and use gconf-editor, but first have to install it. I use Xubuntu 7.04 - sudo apt-get install gconf-editor didn't work because there was no 'candidate' for such an application to find... maybe the update servers for this special app aren't specifiied? Where did you download it? Besides, don't you know where the configuration file for the screensaver settings can be found? That might be a fast way to accomplish....


Thanks so far!

perixx

---

### Post by JurB on 2007-10-10
Ah, i didn't know you were on Xubuntu.
My best bet is that your config file is somewhere in /home/yourusername/.config/xfce4/

---

### Post by perixx on 2007-10-10
Hell, what is this ??!! 

One could guess that the selection of a screensaver is to be found somewhere in a config file in plain text.

I've searched the entire installation for any sign of the screensaver settings file containing 'molecule'...

I've renamed 
/usr/share/xscreensaver/config/molecule.xml
and
/usr/share/applications/screensavers/Molecule

so one should think that 'molecule' cannot be started anymore..!

No effect, though :P
Also transferring the 'shells' extension behind the entry 'molecule' in the 
/home/username/.xscreensaver - file didn't change anything.

What finally led to success was changing the 'selected' value in this file!!! E.g. to 171...
Now I could access the screensaver-manager again without system lock-up and changed the mode to 'only one screensaver' - should work with 'mode=1' in the .xscreensaver - file also!

Mission accomplished!!

---

### Post by monoomni on 2007-10-11
I'm having the exact same problem.  Looks like it's something to do with the ATI Rage 128 cards.  I wonder, can you enable desktop effects?

---

### Post by perixx on 2007-10-11
Hi monoomni,


yes this bug seems to be linked to the ATI rage 128 pro... though I cannot imagine that no other GC's are affected...

What do you mean with 'Desktop effects' - translucency and those things? They worked with my PC setup but the performance was utterly bad after enabling it. So I disabled it again - who really needs those things anyways? ;-]

perixx

---

### Post by monoomni on 2007-10-11
under System->Preferences->Desktop Effects if I try to enable desktop effects I just get an error saying they can't be enabled.

Also, I don't know if this is a clue, but Device Manager says my graphics card bus type is PCI... even though it's an AGP card?

---

### Post by perixx on 2007-10-11
Well, I'm not sure about this.... do you maybe have the 'Assign IRQ for PCI' instead of AGP enabled in your BIOS?

Or 'Init Display first' for PCI, not for AGP?


I have German localization and cannot completely follw up your way through the menus, but I suppose you have Ubuntu or Kubuntu installed? Mine is Xubuntu, using Xfce...

I can enable the 'Compositing' effects under Applications > Options > Window-Manager-Tweaks > Compositor (translated menu options!)
That's where I can enable Compositing with translucent Windows and stuff like that. Didn't work too well for me, though.

Another idea: what kind of driver do you have installed in your /etc/X11/xorg.conf? Might be the reason aswell. It should be "ati" in your 'Device' section (that is, if you use Xubuntu, at least). If this one doesn't work, you maybe can install the 'ATI restricted drivers' under Applications > System > Restricted Drivers Manager... I don't need and cannot do that, for I use Xfce.

regards

perixx

---

### Post by monoomni on 2007-10-12
turns out the pci thing is not biggie... i guess pci:1:0:0 is the agp slot.

i am using the ati drivers.

has anyone figured out _why_ the molecule screensaver causes a crash?  it seems to be related to the ati rage pro card...

my main concern is being able to use Gwyddion (image processing program).  the computer locks-up everytime i try to use 3D view.

---

### Post by perixx on 2007-10-12
Sorry, cannot help you there...

Maybe you can give some ATI open source drivers a shot (no idea what the "ati" one is exactly). Don't ask me how to compile them for Ubuntu, though.

perixx

---

### Post by perixx on 2007-10-12
Some supplementary info concerning the 'molecule' screensaver crash:


1. /home/USERNAME/.xscreensaver contains the list and option to select the active screensaver-app 

The three digit number 'selected' points directly to the malfunctioning 'molecule' app in the list below; just enter another number and delete the line 'molecule'. You  can choose a working screensaver again and you're save from accidentially selecting the faulty app again,


2. /etc/X11/app-defaults/XScreenSaver-gl 
contains following info:

"These resources, when placed in the system-wide app-defaults directory
! (e.g., /usr/lib/X11/app-defaults/XScreenSaver) will provide the default
! settings for new users.  However, if you have a ".xscreensaver" file in
! your home directory, the settings in that file take precedence."  

I don't know what's the 'system wide app-defaults directory' of Xubuntu and I only have 1 user-account. So, if sbd. would like to set a default without the bad 'molecule' screensaver, I guess he would either have to:

1. edit the etc/X11/app-defaults/XScreenSaver-gl accordingly, or
2. copy and rename this file to /usr/lib/X11/app-defaults/XScreenSaver + edit it, or
3. copy the adjusted home/USERNAME/.xscreensaver file to the new username's directory manually each time.

Just an idea from where to start best - I probably won't use several user-accounts, thus not investigating this any further... 


perixx

---

### Post by perixx on 2007-11-05
UPDATE:

AVOID "ENDGAME" (197) as well !!! Bound to also crash your system....


perixx

---

### Post by Nietzsche Keen on 2008-04-18
I read this solution to the Molecule screensaver freeze problem, and as a n00b just didn't understand it. So I'm reposting a simpler solution from elsewhere on this site:

1. go into the Terminal application (under Accessories)
2. enter:
gedit .gconf/apps/gnome-screensaver/%gconf.xml
3. in the box that pops up you'll see:
screensavers-molecule
4. change "molecule" to one of the working screensavers, such as:
screensavers-sonar
5. restart
The message from Xan 2007-12-03 up above suggests a way to remove molecule, but I haven't tried it.
Good luck

---

### Post by perixx on 2008-05-21
> Ah, i didn't know you were on Xubuntu.
My best bet is that your config file is somewhere in /home/yourusername/.config/xfce4/

Could it be, that this also refers to you? :] My solution here (a little detailed, granted) is for those Xubuntu-freaks. But maybe not many affected by this anymore, unless other cards than the Ati Rage 2000 Pro are, too. 

perixx

---

