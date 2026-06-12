---
title: "avant - customize to replace &quot;quicklaunch&quot; ?"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by Hawk__0 on 2007-09-04
I dont know what its technically called in linux, but the quicklaunch area (when you install ubuntu its just right of the system button, and firefox is there by default) i want to have moved onto my avant window navigator.  and not show open windows.  is this possible?

---

### Post by Inxsible on 2007-09-04
If you mean you want to create a launcher in avant then you can simply drag the firefox icon from Applications --> Internet--> Firefox Web Browser into Avant and you should be good to go :D

---

### Post by Hawk__0 on 2007-09-04
hm that doesn't seem to work.. i cant even right click the whitespace in it to bring up a menu.

---

### Post by Inxsible on 2007-09-04
> **Hawk__0 said:**
> hm that doesn't seem to work.. i cant even right click the whitespace in it to bring up a menu.Do you have Compiz or Beryl running ?

AWN needs a composite manager to run

---

### Post by Hawk__0 on 2007-09-04
compiz-fusion, yes... whats a composite manager?
i jsut ran it with alt+f2 and "avant-window-navigator"

---

### Post by Inxsible on 2007-09-04
> **Hawk__0 said:**
> compiz-fusion, yes... whats a composite manager?
i jsut ran it with alt+f2 and "avant-window-navigator"
CF or Beryl is the composite manager.

Are you sure you are dragging the icon and placing it in AWN ?

---

### Post by Hawk__0 on 2007-09-04
yea, i drag it (icons following the mouse), and i move it onto an empty AWN bar, right in the middle, and it zooms back to the app menu :S

---

### Post by Inxsible on 2007-09-04
what applets do you already have in your awn bar ?

can you pull up the awn manager ?

---

### Post by Hawk__0 on 2007-09-04
currently, kopete and firefox.  what do you mean pull up the AWN manager? i ran advant-config or something allong those lines before

---

### Post by Inxsible on 2007-09-04
> **Hawk__0 said:**
> currently, kopete and firefox.  what do you mean pull up the AWN manager? i ran advant-config or something allong those lines before

you can get to the awn manager by

System --> Preferences --> Awn Manager

or by running ```
awn-manager
``` in the terminal

or by right clicking some empty area on the bar and then selecting preferences

---

### Post by Hawk__0 on 2007-09-04
ok i cannot right clikc an empty area, it does nothing, awn-manager doesn't work, but i can see (in preferences) advant preferences
> steve@steve-desktop:~$ awn-manager
bash: awn-manager: command not found


---

### Post by Inxsible on 2007-09-04
> **Hawk__0 said:**
> ok i cannot right clikc an empty area, it does nothing, awn-manager doesn't work, but i can see (in preferences) advant preferences
hmmmm ....how did you install awn again ?

its 3 am here now...so I m off to bed...be back tom to help you further..

---

### Post by Hawk__0 on 2007-09-04
I installed it following this guide: [http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

In the end i want it to be like this one: [http://www.thelinuxvault.net/images/6/6b/ModifiedUbuntuScreenshot.png](http://www.thelinuxvault.net/images/6/6b/ModifiedUbuntuScreenshot.png)
I like how the backgrond has that 3d-looking effect to it, and i have no idea how to customize this thing at all

---

### Post by Inxsible on 2007-09-04
you do realize that that's an old howto which came out before Feisty and was meant for Edgy.

Now I am not saying that it shouldn't work. Obviously it works for you.

But I installed it using syzygy repos from tuxfamily and I can easily drag and drop my launchers and also get the 3D look.

If you do go this route, however, you will first need to completely un-install your current version. I am not even sure if you want to do that tho.

---

### Post by JBAlaska on 2007-09-04
> **Hawk__0 said:**
> I installed it following this guide: [http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

In the end i want it to be like this one: [http://www.thelinuxvault.net/images/6/6b/ModifiedUbuntuScreenshot.png](http://www.thelinuxvault.net/images/6/6b/ModifiedUbuntuScreenshot.png)
I like how the backgrond has that 3d-looking effect to it, and i have no idea how to customize this thing at all

Right click on the awn bar until you see preferences (It might take a couple of rt clicks until you find the right spot on the bar) Go to the bar appearance tab and change "look" to 3D Look, also you can click the "separator"  check box and see where you have to drag your launchers to get them to stick (On the left).

---

### Post by Hawk__0 on 2007-09-04
i dont have those options.
I want to try a guide for fiesty now, this one is old or something i guess. however i cannot remove it!

```
steve@steve-desktop:~$ sudo aptitude remove avant-window-navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  mencoder 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
steve@steve-desktop:~$
```

note: also tried removing with apt-get

also, i found AWN in the package manager, is that a good one to install?

---

### Post by Inxsible on 2007-09-04
That link suggests that you compiled from source. So you will have to remove it that way too.

In the source folders, try```
sudo make uninstall
``` and see if that works.

---

### Post by Hawk__0 on 2007-09-04
> 
steve@steve-desktop:~/avant-window-navigator$ sudo make uninstall
Password:
make: *** No rule to make target `uninstall'.  Stop.
steve@steve-desktop:~/avant-window-navigator$ 


??

edit: i got it, i had 2 AWN folders :P

now when i install the one from the package manager this happens:

> steve@steve-desktop:~/avant-window-navigator-0.1.1$ awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 149, in __init__
    self.setup_font(TITLE_FONT_FACE, self.wTree.get_widget("selectfontface"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 267, in setup_font
    font_btn.set_font_name(self.client.get_string(key))
TypeError: GtkFontButton.set_font_name() argument 1 must be string, not None
steve@steve-desktop:~/avant-window-navigator-0.1.1$ 


edit:  ok i had to have awn running.  now im ready to roll to change this to my launch bar.  how do i make it not display tasks?

---

### Post by Hawk__0 on 2007-09-04
bump (just need to know how to make avant NOT display open windows, and just my launchers)

---

