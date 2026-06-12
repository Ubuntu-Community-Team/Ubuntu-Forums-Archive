---
title: "splash screen"
date: 2009-01-18
forum: General Help
---

### Post by optimistique1 on 2009-01-18
Hi I am not sure if this is possible or not but when you start up Ubuntu and you get the text saying 'starting , booting from and Grub etc...' before the splash screen, is there anyway to hide this so that I get no text showing at all?
Many thanks
GArry

---

### Post by bapoumba on 2009-01-18
Moved to General Help.

That would be using the hiddenmenu option in grub configuration file (uncomment it in /boot/grub/menu.lst). After that, the default kernel line is booted after the timeout, without seeing any additional text. To get to the menu if you need to, hit Escape.

[http://www.gnu.org/software/grub/manual/html_node/Hidden-menu-interface.html](http://www.gnu.org/software/grub/manual/html_node/Hidden-menu-interface.html)

---

### Post by optimistique1 on 2009-01-18
WOW thanks for that.
I am a bit of a newbie here so how do I edit the hiddenmenu option in grub configuration file?
Many thanks
Garry :-)

---

### Post by DeMus on 2009-01-18
> **optimistique1 said:**
> WOW thanks for that.
I am a bit of a newbie here so how do I edit the hiddenmenu option in grub configuration file?
Many thanks
Garry :-)


Applications | Accessories | Terminal

Type sudo gedit /boot/grub/menu.lst
type your password
Gedit is now opening the file menu.lst.
Look for the line that says #hiddenmenu. In front of the line is a "#" sign. Remove that sign.
Be careful not to change anything else or it might not work again.
Save the file

Reboot to see if it worked.

---

### Post by optimistique1 on 2009-01-18
Thanks for that I will give it a try when I get home.
Do I press CTRL + C to save the file when I have removed the '#'?
Many thanks
Garry

---

### Post by DeMus on 2009-01-18
> **optimistique1 said:**
> Thanks for that I will give it a try when I get home.
Do I press CTRL + C to save the file when I have removed the '#'?
Many thanks
Garry


No ctrl + c is for copying. You use ctrl + s (s as in save)
You can also use the toolbar to save the text file.

---

### Post by drs305 on 2009-01-18
Or to avoid manually editing menu.lst:
Install StartUp-Manager
```

sudo apt-get install startupmanager
```
Run it:
System, Administration, StartUp-Manager

Select the Boot Options tab. Untick "Show bootloader menu"

SUM can easily tweak many of menu.lst's settings. Refer to the link in my signature line for a tutorial.

---

### Post by DeMus on 2009-01-18
> **drs305 said:**
> Or to avoid manually editing menu.lst:
Install StartUp-Manager
```

sudo apt-get install startupmanager
```
Run it:
System, Administration, StartUp-Manager

Select the Boot Options tab. Untick "Show bootloader menu"

SUM can easily tweak many of menu.lst's settings. Refer to the link in my signature line for a tutorial.

Okay, you win. :)

---

### Post by drs305 on 2009-01-18
> **DeMus said:**
> Okay, you win. :)

The beauty of linux is that there are lots of ways to win. One solution is not inherently 'better' than another in most cases. One may wish to sacrifice speed for the opportunity to learn how the system really works... or not. ;-)

---

### Post by DeMus on 2009-01-18
> **drs305 said:**
> The beauty of linux is that there are lots of ways to win. One solution is not inherently 'better' than another in most cases. One may wish to sacrifice speed for the opportunity to learn how the system really works... or not. ;-)

And then they say: Linux is not Windows.
There is not so much difference after all. I mean also in Windows there are 100 ways of doing things.

---

