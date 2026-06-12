---
title: "can't set xprop:   WM_CLASS"
date: 2009-08-12
forum: Desktop Environments
---

### Post by vainhero on 2009-08-12
I'm trying to set the WM_CLASS xWindow Property for a specific window.

Here is what im trying to do. Gedit has the name "Gedit". As such, it minimizes on my dock according to its name "Gedit". Say I want to minimize Gedit with a different name.
Well, I can type 
```
gedit --name magic --class magic
```Now, I type xprop, (in another prompt), click on Gedit window and I get 
```
WM_CLASS(STRING) = "magic", "magic"
```This means that Gedit will now minimize with other applications with WM_CLASS = magic
keep in mind,  class is the first string in WM_CLASS and name is the second string.



This is what im trying to do, and I wish I could launch all my programs being able to specify  --name and --class. (I think class isn't as important with my panel "cairo-dock")

ok...
This doesnt work, for example, when I launch a crossover office 'wine' program. These exec commands dont take  --name or --class.


so... i resorted to reading up on xprop. and tried forcing WM_CLASS to fix name and class

Apprantly, you can set xproperties 

```
xprop -f WM_CLASS 8s -set WM_CLASS "magic"
``````
output:
WM_CLASS(STRING) = "magic"
```This should set the window class to "magic". Unfortunately, my window manager only cares about the 2nd string in WM_CLASS, not the first string. So that code above is useless.
 I CANT FIGURE OUT HOW TO SET 2 STRINGS TO WM_CLASS!!! the xprop manual tells me that WM_CLASS consists of 2 consecutive null terminated strings. It doesnt tell me how to set them though.

I tried this:  notice the 8ss.   2 8-bit strings 
```
xprop -f WM_CLASS 8ss -set WM_CLASS "magic" "magic"
``````
xprop -f WM_CLASS 8ss -set WM_CLASS "magic.magic"
``````
xprop -f WM_CLASS 8ss -set WM_CLASS magic||magic
``````
xprop -f WM_CLASS 8ss -set name "magic" 
```nada, nilch,  nothing, zip
it only takes the first string. Im trying to foce WM_CLASS in xprop to read
```
WM_CLASS(STRING) = "magic", "magic"
```that comma in there is crucial! it means that the field contains 2 strings.
I dont know how to specify 2 strings though. Does anyone?

---

### Post by onyxwolf on 2009-11-24
Bump! Same issue I want to set my Win XP VBox Launcher for Cairo to be specifically for That VM not for the VBox Controller I've tried EVERYTHING (to include the above) but can't get it to work. It would be nice if the Launcher could go by title as well as class (like CCSM can) then would be able to go by the windows title but nope tried, and it doesn't work. Anyone have any ideas?!?

---

### Post by fabounet on 2009-11-25
Hi,
can you provide the result of ```
xprop | grep CLASS
```
on the different windows you want to be distinguished ?
Thanks.

---

### Post by onyxwolf on 2009-11-25
All are WM_CLASS(STRING) = "Qt-subapplication", "VirtualBox"
BTW I'm not using XFCE, but GNOME.

---

### Post by fabounet on 2009-11-26
so then, there is no way to distinguish between them (you can't rely on the name of the window, since it can change at anytime).

You may want to fill a bug report to Virtualbox, saying they should set a proper name/class property on their window.
The "Qt-subapplication" name is just useless, they could do like wine, who sets the name of the .exe running.

---

### Post by onyxwolf on 2009-11-27
Yeah I'll do that. So there is no way to change the class of a window for a session, without the mfg doing it? That sucks.

---

