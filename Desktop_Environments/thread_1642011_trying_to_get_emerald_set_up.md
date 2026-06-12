---
title: "trying to get emerald set up"
date: 2010-12-09
forum: Desktop Environments
---

### Post by iceman30ad on 2010-12-09
system acer aspire 5532 
os ubuntu 10.10

I have been trying to get emerald set up on my laptop and have lost all window boarders

to try and get them back i have uninstalled compiz and emerald and reinstalled deleated all the config files i could find

so now my question is two fold  one is  how do i recover and two how do i get emerald to work 

thanks in advance

---

### Post by stinkeye on 2010-12-09
Don"t know how much of this you know but these are the commannds

Use alt+F2 to run these commands.(If run in the terminal the borders will disappear when the terminal is closed)
Emerald only works with compiz.
To load emerald theme
```
emerald --replace
```


to revert back to default compiz borders
```
gtk-window-decorator --replace
```


To switch to Metacity
```
metacity --replace
```


To switch back to compiz
```
compiz --replace
```


**gtk-window-decorator** and **emerald** are window decorators.(ie titlebar and borders)
**metacity** and **compiz** are window managers.

Metacity uses the gtk-window-decorator.
Compiz can use the gtk-window-decorator or emerald.

If you install fusion-icon you can have a menu for all this in the notification area.


To reinstall compiz and emerald, and install fusion-icon
```
sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager
```

After reinstalling if your still having problems, open compizconfig-settings-manager > preferences
and hit the **reset to defaults** button.

---

### Post by iceman30ad on 2010-12-09
thank you  you have gotten me 90% there just having trouble with fusion icon

i run it in terminal and i get the following

> chris@chris-Aspire-5532:~$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
Backend     : ini
Integration : true
Profile     : default
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'
chris@chris-Aspire-5532:~$ 


Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 




---

### Post by iceman30ad on 2010-12-09
ok this is odd  i have the drivers for my video card installed  but  when i try to put them to use  the system says they don't exist and when i try to uninstall it says they cant be found

---

### Post by iceman30ad on 2010-12-09
ok this is odd  i have the drivers for my video card installed  but  when i try to put them to use  the system says they don't exist and when i try to uninstall it says they cant be found i guess i  really scr3w3d the pOOch

---

### Post by stinkeye on 2010-12-09
Were you running compiz before??
To run compiz as your window manager you need to install the propriertary drivers.
Check in System > administration > additional drivers

fusion-icon can be found in System Tools > compiz fusion icon

---

### Post by iceman30ad on 2010-12-09
yea i had compiz set up nicely  but i saw what emerald could do and i wanted to try that out  got to playing  evedently i got rid of something i shouldnt have would you say i just need to back up and reinstall

i had found fusion icon no prob but it wouldnt start thats why i went terminal

---

### Post by stinkeye on 2010-12-09
> **iceman30ad said:**
> yea i had compiz set up nicely  but i saw what emerald could do and i wanted to try that out  got to playing  evedently i got rid of something i shouldnt have **would you say i just need to back up and reinstall**

i had found fusion icon no prob but it wouldnt start thats why i went terminal

If you feel that's the easier option than trying to get the vid drivers working again, yes.

---

### Post by iceman30ad on 2010-12-09
> **stinkeye said:**
> If you feel that's the easier option than trying to get the vid drivers working again, yes.
i am trying to  learn the system and have already made mistakes (partitioned so  every thing is already backed up) i dont think i can  make it any worse so if you can  give me some pointers  as to how to find where the vid card drivers are located and  what to look for to get them working again . if i completely crash it its no biggie i as already mentioned thats already taken care of

---

### Post by stinkeye on 2010-12-09
I use nvidia and trouble shooting a driver problem isn't something I know enough about to give advice.
A forum search should find something if you want to have a go.

This post may help
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10166320&postcount=2[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10166320&postcount=2")

---

