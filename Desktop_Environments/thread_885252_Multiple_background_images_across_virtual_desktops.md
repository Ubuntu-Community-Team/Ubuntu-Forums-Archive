---
title: "Multiple background images across virtual desktops"
date: 2008-08-09
forum: Desktop Environments
---

### Post by transitional on 2008-08-09
I've seen some Ubuntu screens of the Compiz-Fusion cube, in which each desktop had a different background image. I've looked around a fair bit in my settings, but I haven't found anything like it. I want to have a different picture for each desktop, but here's what my desktop wall looks like:
[IMG]http://i33.tinypic.com/2ryrktu.png[/IMG]

Any way to change this? Currently running Hardy.

---

### Post by Ptero-4 on 2008-08-10
In gnome and xfce AFAIK you need an extra utility to do that (dunno it's name). In KDE you set it in the background applet.

---

### Post by prshah on 2008-08-10
> **transitional said:**
> in which each desktop had a different background image.
Currently running Hardy.

Click on System-Preferences-Advanced Desktop Effects Settings-Desktop Cube-Appearance, the set the background images you want in "Background Images".

However, this may not give you what you want until you perform an additional step. You have to give drawing control of your backgrounds to Compiz. If you do this, you have to sacrifice desktop icons. If you are sure you want to do this; press Alt+F2, then ```
gconf-editor
```
then navigate to Apps/Nautilus/Preferences and uncheck (untick) "show_desktop".

---

### Post by FeTTo on 2009-08-15
> **prshah said:**
> Click on System-Preferences-Advanced Desktop Effects Settings-Desktop Cube-Appearance, the set the background images you want in "Background Images".

However, this may not give you what you want until you perform an additional step. You have to give drawing control of your backgrounds to Compiz. If you do this, you have to sacrifice desktop icons. If you are sure you want to do this; press Alt+F2, then ```
gconf-editor
```then navigate to Apps/Nautilus/Preferences and uncheck (untick) "show_desktop".

there is no such "advanced desktop effects settings" under preferences....and in compiz config and appearance they removed background images in jaunty....any other help would be great as ive been googling this for days now..wallpapoz is garbage and i cant find another way to make this work

---

### Post by ccnjim on 2009-08-15
I don't know if this will help. I can't remember the post this came from but it worked for me.

Fastest & Easiest way to make your 4 Workspaces with 4 different Wallpapers:

Keyboard: alt-f2
Run: gconf-editor
Head to: apps->nautilus->preferences, and uncheck the show-desktop box (this unfortunately removes your icons as well).
Head to System>Preferences>ccsm,

Search: wallpaper *Click it*
*Enable it, then inside there *Background* click *New*.. Add a Wallpaper Image for the current Workspace.

Change Workspace, Add another Background Image *New*... keep doing this till you have done all 4 Workspaces with each different Wallpaper Image...

You are done.

---

### Post by FeTTo on 2009-08-16
> **ccnjim said:**
> I don't know if this will help. I can't remember the post this came from but it worked for me.

Fastest & Easiest way to make your 4 Workspaces with 4 different Wallpapers:

Keyboard: alt-f2
Run: gconf-editor
Head to: apps->nautilus->preferences, and uncheck the show-desktop box (this unfortunately removes your icons as well).
Head to System>Preferences>ccsm,

Search: wallpaper *Click it*
*Enable it, then inside there *Background* click *New*.. Add a Wallpaper Image for the current Workspace.

Change Workspace, Add another Background Image *New*... keep doing this till you have done all 4 Workspaces with each different Wallpaper Image...

You are done.
you sir are the man

---

### Post by ccnjim on 2009-08-16
I'm glad it worked for you. I can't take credit for it. I copied it from a post I found into my massive Ubuntu how to file.

---

### Post by nealien on 2009-09-24
ccnjim and prshah are both right actually... it seems that it depends on which versions of software you're running. i tried ccnjim's way and searched wallpaper in ccsm and got a goofy smily who looked like he lost his kitten.....but prshah's way did work for me.  i would say try both and one of them will work! ;)


edit:  after playing around with this i've found it's a little buggy.  could just be my computer tho..

---

### Post by sw34963 on 2009-12-08
Thanks ccnjim...

I was starting to pull hair out,  all the other tutorials are saying to change the images within DecktopCube>Appearence>***,
which it isnt.   

Thanks again   =D>

---

### Post by locote on 2009-12-30
> **ccnjim said:**
> I don't know if this will help. I can't remember the post this came from but it worked for me.

Fastest & Easiest way to make your 4 Workspaces with 4 different Wallpapers:

Keyboard: alt-f2
Run: gconf-editor
Head to: apps->nautilus->preferences, and uncheck the show-desktop box (this unfortunately removes your icons as well).
Head to System>Preferences>ccsm,

Search: wallpaper *Click it*
*Enable it, then inside there *Background* click *New*.. Add a Wallpaper Image for the current Workspace.

Change Workspace, Add another Background Image *New*... keep doing this till you have done all 4 Workspaces with each different Wallpaper Image...

You are done.



Thanks it worked for me to

---

### Post by hdbdude on 2009-12-30
Just use kde. It looks much better.

---

### Post by nichpakaich on 2010-01-20
> **ccnjim said:**
> 

Search: wallpaper *Click it*
*Enable it, then inside there *Background* click *New*.. Add a Wallpaper Image for the current Workspace.

Change Workspace, Add another Background Image *New*... keep doing this till you have done all 4 Workspaces with each different Wallpaper Image...

You are done.

This one solve my problem, thanks for the tips :p

---

### Post by saeedmar on 2010-03-04
> **prshah said:**
> Click on System-Preferences-Advanced Desktop Effects Settings-Desktop Cube-Appearance, the set the background images you want in "Background Images".

However, this may not give you what you want until you perform an additional step. You have to give drawing control of your backgrounds to Compiz. If you do this, you have to sacrifice desktop icons. If you are sure you want to do this; press Alt+F2, then ```
gconf-editor
```then navigate to Apps/Nautilus/Preferences and uncheck (untick) "show_desktop".

Hi 
I did that and my right click on desktop is not working afterwards; and I can't change my desktop background either; please help; what can I do now to restore that, please don't tell me that I should reinstall ubuntu; ](*,) ; I have changed that show desktop stuff to the default tik kind but it does not works; help me please

---

### Post by hhh on 2010-03-04
> **saeedmar said:**
> Hi 
I did that and my right click on desktop is not working afterwards; and I can't change my desktop background either;
Re-enable you Nautilus desktop the same way in gconf-editor, meaning put a check back in "show_desktop" and logout/login.

You can NOT have both multiple wallpapers and desktop icons/menus in Gnome (default Ubuntu). If you do want to sacrifice some funtionality, enabling the Wallpaper plugin in Compiz settings and adding walls there (and not in the Cube), then disabling the Nautilus desktop in gconf-editor has always worked for me.

By the way, you're not supposed to double-post (friendly hint)...
[http://ubuntuforums.org/showthread.php?t=1421554](http://ubuntuforums.org/showthread.php?t=1421554)

-edit- So, since you are struggling, and to be clear, if you want multiple backgrounds...
1) Go to Synaptics (System>Administration>Synaptics Package Manager), search for "compizconfig-settings-manager" and install it (if it's not already).

2) Go to Compiz Settings (System>Preferences>CompizConfig Settings Manager), enable the "Wallpaper" plugin (found in the "Utility" category) and add your walls there.

3) Untick the box in apps>nautilus>preferences>show_desktop.

---

### Post by strydervtx on 2010-05-10
> **hhh said:**
> 
-edit- So, since you are struggling, and to be clear, if you want multiple backgrounds...
1) Go to Synaptics (System>Administration>Synaptics Package Manager), search for "compizconfig-settings-manager" and install it (if it's not already).

2) Go to Compiz Settings (System>Preferences>CompizConfig Settings Manager), enable the "Wallpaper" plugin (found in the "Utility" category) and add your walls there.

3) Untick the box in apps>nautilus>preferences>show_desktop.

You also need the compiz-fusion-plugins-extra package to get the Wallpaper plugin, at least on Lucid. I also had to untick the box in desktop>gnome>background>draw_background in gconf-editor.

---

