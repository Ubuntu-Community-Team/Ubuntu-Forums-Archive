---
title: "open office..... unreadable text display!!!!"
date: 2009-02-06
forum: General Help
---

### Post by chinmaya_n on 2009-02-06
The text present in the menu bar of the open office is unreadable.....
I have to use it urgently plzz......... help me out !!!!

---

### Post by hyper_ch on 2009-02-06
can you attach a screenshot?

---

### Post by chinmaya_n on 2009-02-06
This is the link...........
"http://cid-33dc0103d6b24664.skydrive.live.com/self.aspx/photos/OpenOffice.org%20Writer%20.png"

---

### Post by hyper_ch on 2009-02-06
hmmm, seems like you changed the default font somehow....

try this:

(1) Close OOo
(2) Move the user config for OOo to something else
```

mv ~/.openoffice.org ~/openoffice.org.bak

```
(3) retry

---

### Post by chinmaya_n on 2009-02-06
It is showning like this .....!!!
```
chinmaya@chinmaya:~$ mv ~/.openoffice.org ~/openoffice.org.bak
mv: cannot stat `/home/chinmaya/.openoffice.org': No such file or directory

```

I applied even sudo !!

---

### Post by hyper_ch on 2009-02-06
open nautilius, make hidden files visible and then check in your home folder what the folder folder openoffice is. On my system it's /home/USER/.openoffice.org

---

### Post by abn91c on 2009-02-06
looks like the default office fonts were changed, click on the tools>options>fonts.
see attached for location

---

### Post by abn91c on 2009-02-06
also change it here

---

### Post by chinmaya_n on 2009-02-06
I tried as u said MR.abn91c .......... but it is of no use

I tried every font displayed in the drop box .....!!!!

---

### Post by chinmaya_n on 2009-02-06
i tried this too..... it didnt show me an error but....... the text didnt change........ remained same....```
$mv ~/.openoffice.org2 ~/openoffice.org2.bak
$
```

---

### Post by hyper_ch on 2009-02-06
then try:

```

sudo apt-get purge openoffice.org* && sudo apt-get install openoffice.org

```

---

### Post by chinmaya_n on 2009-02-06
```
chinmaya@chinmaya:~$ sudo apt-get purge openoffice.org* && sudo apt-get install openoffice.org
[sudo] password for chinmaya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice.org2.bak
chinmaya@chinmaya:~$ 

```

---

### Post by hyper_ch on 2009-02-06
there is something weird going on... open synaptic and mark all openoffice packages installed for complete removal

---

### Post by chinmaya_n on 2009-02-06
I just what u said....... is there any better substitue for office.......!!!(I'm not an advanced user.... but i need the presentations to be good enough...!!)

Can u suggest me plz....... is this open office is much better to me ????

---

### Post by hyper_ch on 2009-02-06
and after removing openoffice from synaptic reinstall it again.

---

### Post by chinmaya_n on 2009-02-06
Even after total reinstallation it is giving me same problem ...... I'm much irritated ........ plz help

---

### Post by hyper_ch on 2009-02-06
i have no clue... you might want to ask in the #openoffice.org channel on irc.freenode.org

---

### Post by mistypotato on 2009-02-06
[SIZE="5"]SAME Problem here [/SIZE]

---

### Post by mistypotato on 2009-02-06
[SIZE="4"]chinmaya_n

[SIZE="3"]Just curious, what graphics card are you using and what is your current Screen Resolution setting (if you know)

This may be a bug.

I have Office installed on several different computers in the same room and they are ALL exhibiting this behavior.
This is the first time they have been opened for use.
[/SIZE][/SIZE]

---

### Post by pickarooney on 2009-02-06
Is it only in openoffice or in the menus of other applications? What Desktop environment are you using?

---

### Post by mistypotato on 2009-02-06
ONLY Open Office.

No similar problem from any other application.

However, I use Open Office on WindowsXP and love it so I will not get irritated and give up I'll get it working.  It's a MUST have.  It's like the Porsche of Office Suites, no substitute.;)

---

### Post by pickarooney on 2009-02-06
Is **Use system font for user interface** ticked in Tools, Options, Openoffice.org, View?

---

### Post by mistypotato on 2009-02-06
> **pickarooney said:**
> Is **Use system font for user interface** ticked in Tools, Options, Openoffice.org, View?


Do you mean in the Open Office Application itseld?

hehe.... I can't see "Tools" "Options"

No words on any menus are visible at all (In Open Office only)

---

### Post by mistypotato on 2009-02-06
Here is what I see

---

### Post by chinmaya_n on 2009-02-06
i use GNOME.......... and some extra information ```
chinmaya@chinmaya:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
chinmaya@chinmaya:~$ 

```

---

### Post by mistypotato on 2009-02-06
Wow...Ubuntu can get really strange sometimes.

In my APPLICATIONS, I have Open Office Spreadsheet, Write and another OO app.

HOWEVER....

OPEN OFFICE (according to Synaptic Package manger) is NOT installed? :(



How can the OO applications be available on the Applications menu if they're NOT installed according to Synaptic ?

---

### Post by abn91c on 2009-02-06
Ok this should work```
sudo apt-get remove openoffice.org-gnome
```

---

### Post by chinmaya_n on 2009-02-07
What should i do know??

---

### Post by abn91c on 2009-02-08
> **chinmaya_n said:**
> What should i do know??
```
sudo apt-get remove openoffice.org-gnome
```

---

### Post by marcojulia on 2009-02-08
Hi, I have the same identical problem, just after have changed the sk video, I had ait 7000 and openoffice was workin perfect,
I used abit siluro 64 for the game xmoto becouse wase'nt work, now xmoto is workink but I got openoffice problem . 

Angelo ](*,)

---

### Post by heatblazer on 2009-02-08
Why not delete your /home/ilian/.openoffice.org2/user for example? When starting OO2 it will make a default new one. It helped me a lot back then, simple way to solve problems. However losing all of your settings and options.:KS

---

### Post by marcojulia on 2009-02-08
I'em not able to unistall openoffice, I write sudo apt-get remove openoffice.org-gnome but did not work :(
angelo

---

### Post by marcojulia on 2009-02-08
I use OO 3.0

---

### Post by marcojulia on 2009-02-08
I unistalled e reinstalled openoffice 3.0 but I still have the same problem .
](*,)
angelo

---

### Post by mike2357 on 2009-02-08
This problem seems to be caused by the interplay of openoffice, compiz and in some cases, drivers for older Nvidia cards. The solution is pretty simple, and easy to reverse if it doesn't work: change your font setting as follows:

System -> Preferences -> Appearance -> Fonts

In the Rendering section, click on the "Subpixel smoothing (LCDs)" radio button.

---

### Post by marcojulia on 2009-02-08
=D> It works, thanks a lot .
ciao
Angelo:popcorn::guitar:

---

### Post by chinmaya_n on 2009-02-09
I don't know how ......... but the following way it worked :popcorn:....... see the code below carefully......
```
chinmaya@chinmaya:~$ sudo apt-get remove openoffice.org-gnome
[sudo] password for chinmaya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  antlr libsvga1 libggi2 libgii1 liblzo2-2 libantlr-java libgii1-target-x
  libggi-target-x
Use [COLOR="Red"]'apt-get autoremove'[/COLOR] to remove them.
The following packages will be REMOVED:
  openoffice.org-gnome
0 upgraded, 0 newly installed, 1 to remove and 70 not upgraded.
After this operation, 340kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170062 files and directories currently installed.)
Removing openoffice.org-gnome ...


chinmaya@chinmaya:~$ sudo apt-get remove openoffice.org-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-gnome is not installed, so not removed
The following packages were automatically installed and are no longer required:
  antlr libsvga1 openoffice.org-gtk libggi2 libgii1 liblzo2-2 libantlr-java
  libgii1-target-x libggi-target-x
Use [COLOR="Red"]'apt-get autoremove'[/COLOR] to remove them.
0 upgraded, 0 newly installed, 0 to remove and 70 not upgraded.


chinmaya@chinmaya:~$ sudo apt-get autoremove openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org is not installed, so not removed
The following packages were automatically installed and are no longer required:
  antlr libsvga1 openoffice.org-gtk libggi2 libgii1 liblzo2-2 libantlr-java
  libgii1-target-x libggi-target-x
The following packages will be REMOVED:
  antlr libantlr-java libggi-target-x libggi2 libgii1 libgii1-target-x
  liblzo2-2 libsvga1 openoffice.org-gtk
0 upgraded, 0 newly installed, 9 to remove and 70 not upgraded.
After this operation, 5087kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170055 files and directories currently installed.)
Removing antlr ...
Removing libantlr-java ...
Removing libggi-target-x ...
Removing libggi2 ...
Removing libgii1-target-x ...
Removing libgii1 ...
Removing liblzo2-2 ...
Removing libsvga1 ...
Removing openoffice.org-gtk ...
Processing triggers for python-support ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
chinmaya@chinmaya:~$ 


```

after the first part of code, i checked if OOffice was removed but it didnt happen......... then i tried again with the same command it showed me to use [COLOR="Red"]autoremove[/COLOR] ..... then i used it ...... Now OpenOffice was not removed but the font is now back ........!!!!!
:guitar:

Hmm....... I'm very much happy now !1@#$%%^;)
Thanks folks!!

---

### Post by mikeymike on 2009-02-11
> **mistypotato said:**
> Here is what I see

Yes, I am having this problem as well.

---

### Post by irvotheturbo on 2009-02-13
> **mike2357 said:**
> This problem seems to be caused by the interplay of openoffice, compiz and in some cases, drivers for older Nvidia cards. The solution is pretty simple, and easy to reverse if it doesn't work: change your font setting as follows:

System -> Preferences -> Appearance -> Fonts

In the Rendering section, click on the "Subpixel smoothing (LCDs)" radio button.

Screen was good until my NVidia FX5600 crashed yesterday. Since I put my old NVidia MX400 in OO went wacko!
Just remembered gFTP gave me problems too (much alike), fixed now as well.

Thanks for the fix, it'll do for now :)

---

### Post by paggeau on 2009-02-13
im having the same problem i guess but NO FONTS whatsoever in open office, no text on any tabs just lines, any idea,s?

---

### Post by irvotheturbo on 2009-02-14
Setting Fonts to "Subpixel smoothing (LCD)" didn't work for you?

I'm still having the same problem, but now in Wine. No text whatsoever, unless I turn off Visual Effects. Then it gives me text all scrambled up. Any ideas?
EDIT: Fix / Workaround provided here   -> [http://bugs.winehq.org/show_bug.cgi?id=16146](http://bugs.winehq.org/show_bug.cgi?id=16146)

---

