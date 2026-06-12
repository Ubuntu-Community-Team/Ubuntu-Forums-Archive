---
title: "Help Me Make My Windows Transparent Please:-)"
date: 2009-04-05
forum: Desktop Environments
---

### Post by Granny_Geek on 2009-04-05
The title says it all. It is very easy to do in Kubuntu...can you tell me how to do it in Ubuntu? Thanks, Granny

---

### Post by Pasdar on 2009-04-05
You mean like Windows VISTA? You would need to install Emerald via package manager, and then download a vista theme for it from [www.gnome-look.org](www.gnome-look.org)

---

### Post by binbash on 2009-04-05
which window are you trying to make transparent ?.You can set any window (with name class etc ) transparent at compizconfig settings manager > opacity, brightness and saturation plugin

---

### Post by blackened on 2009-04-05
Since CompizConfig Settings Manager is not installed by default, to install it via the terminal use:
```
sudo apt-get install compizconfig-settings-manager
```

It will then be available as System -> Preferences -> CompizConfig Settings Manager.

---

### Post by Granny_Geek on 2009-04-05
> **binbash said:**
> which window are you trying to make transparent ?.You can set any window (with name class etc ) transparent at compizconfig settings manager > opacity, brightness and saturation plugin
Ok, but how do I set name,class,etc? I have no clue, could you give an example, lets say for the text editor?

---

### Post by Granny_Geek on 2009-04-05
> **Granny_Geek said:**
> Ok, but how do I set name,class,etc? I have no clue, could you give an example, lets say for the text editor?
By the way, thanks for all your replies, I have Compiz & the Compiz Settings Manager, but I don't know much about making the windows transparent. Granny

---

### Post by blackened on 2009-04-05
> **Granny_Geek said:**
> Ok, but how do I set name,class,etc? I have no clue, could you give an example, lets say for the text editor?

Open a Gedit window, then in CCSM in the Window Specific Settings of the Opacity plugin, click "New". In the Edit dialog that comes up, click the "+" button.

In the "Type" dropdown box, select how you want to match the window, then click the "Grab" button and click on the Gedit window you opened earlier. Click the "Add" button, then set the required opacity in the "Edit" dialog before closing it.

---

### Post by Granny_Geek on 2009-04-05
> **blackened said:**
> Open a Gedit window, then in CCSM in the Window Specific Settings of the Opacity plugin, click "New". In the Edit dialog that comes up, click the "+" button.

In the "Type" dropdown box, select how you want to match the window, then click the "Grab" button and click on the Gedit window you opened earlier. Click the "Add" button, then set the required opacity in the "Edit" dialog before closing it.
Will try, I'll post how it comes out.

---

### Post by Granny_Geek on 2009-04-05
Ok, I got the effect I wanted by using the Trailfocus plugin and going into appearance and setting opacity from there but I am going to clip this info blackened because I may need the instructions when I decide to change up,which is quite often:-) Thanks, everybody for your replies! Granny:-)

---

### Post by blackened on 2009-04-05
> **Granny_Geek said:**
> ...I am going to clip this info blackened because I may need the instructions when I decide to change up,which is quite often:-) ...

I know the feeling. Tinkering is less a hobby, more a way of life.

---

### Post by abn91c on 2009-04-05
> **Granny_Geek said:**
> The title says it all. It is very easy to do in Kubuntu...can you tell me how to do it in Ubuntu? Thanks, Granny
If you have Kubuntu  8.10 you did not need the compiz settings manager to get transparemn menus, all you had to do is:
 system settings>desktop>desktop effects>advanced>composting type and change to **XRender**

---

### Post by miegiel on 2009-04-05
Once enabled in compiz I just hold left-Alt and roll my mouse wheel to change a window's opacity. Though [_**blackened**'s post_]("http://ubuntuforums.org/showthread.php?p=7020001") seems the way to go if you want the opacity set everytime you run the program.

---

### Post by blackened on 2009-04-05
> **abn91c said:**
> If you have Kubuntu  8.10 you did not need the compiz settings manager to get transparemn menus, all you had to do is:
 system settings>desktop>desktop effects>advanced>composting type and change to **XRender**, here is what mine looks like this

Don't you come around trying to pimp your DE in a perfectly good Gnome thread.

No really, it is much more out of the box in KDE, but they almost do a better job than Compiz in nesting the settings so deep that finding them is near impossible.

---

### Post by Nathanael Culver on 2009-04-06
Maybe I'm missing the obvious, but I just enabled "Opacity, Brightness and Saturation" under Accessibility in Compiz Settings Manager; <Ctrl>-<Shift>-<Super>Up and Down increases or decreases the current window's transparency. I use this especially for terminal apps such as PowerShell which use pseudo-transparency (I HATE that).

If you want a particular app always transparent, go with the other solutions offered here. However, they don't allow you to control the level of transparency on-the-fly.

--Nathanael

---

### Post by Granny_Geek on 2009-04-06
> **blackened said:**
> I know the feeling. Tinkering is less a hobby, more a way of life.
lol...yes! For us Linux users.Granny:-)

---

### Post by blackened on 2009-04-06
> **Nathanael Culver said:**
> ...However, they don't allow you to control the level of transparency on-the-fly...

Very true, though I've never come across an instance where on-the-fly transparency setting was a necessity. I suppose it depends heavily on how you're used to interacting with the machine.

---

### Post by Nathanael Culver on 2009-04-06
> **blackened said:**
> Very true, though I've never come across an instance where on-the-fly transparency setting was a necessity. I suppose it depends heavily on how you're used to interacting with the machine.

Also true. I find <Alt> plus a quick spin of the mouse wheel is quite useful for getting a quick peek at what's behind the current window. This is most useful to me when working in a terminal window -- e.g., increasing transparency temporarily to see the web tutorial I'm trying to follow (much easier than Alt-tabbing back and forth), then reducing it again so I can read the terminal's output. In general, the level of transparency of a terminal window depends on what's behind it. And, while gnome-terminal supports true transparency, my terminal of choice (MXVRT) doesn't (only "pseudo-transparency", which I HATE). 

But, yes, it depends on your own usage patterns.

--Nathanael Culver

---

