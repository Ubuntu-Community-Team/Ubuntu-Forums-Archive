---
title: "Desktop Environments Confusion"
date: 2012-05-09
forum: Desktop Environments
---

### Post by Shadius on 2012-05-09
Hey all, 

I am so confused about all the different types of Desktop Environments and I'm looking for some helpful explanations about them. 

My first confusion is between GNOME and GNOME Shell. Is there a difference? And what is GTK? Does it relate to GNOME? 

Please help me understand! I'm so confused! :(

---

### Post by lykwydchykyn on 2012-05-09
GNOME is a collection of technologies built on the GNOME libraries, that include things like a window manager, launchers, file browsers, web browsers, configuration utilities, etc.

GNOME Shell is a particular component of GNOME that provides a desktop interface.  It's the default for GNOME, AFAIK.  GNOME is designed in such a way that there can be multiple desktop interfaces built on the same basic core, and so you have other variants (like GNOME fallback).

GTK is a set of graphics widget libraries for writing graphical applications.  The GNOME libraries are built on top of GTK, and GNOME is subsequently built from those libraries.

---

### Post by cortman on 2012-05-09
> **iMurshaq said:**
> I see you are running 12.04. That means that you are not running GNOME by default. You are running Unity.

Now we start splitting hairs. :) Unity is a variation of Gnome, similar to gnome-shell or gnome-fallback. It's a custom interface built on the Gnome libraries, etc.

---

### Post by Shadius on 2012-05-09
> **lykwydchykyn said:**
> GNOME is a collection of technologies built on the GNOME libraries, that include things like a window manager, launchers, file browsers, web browsers, configuration utilities, etc.

GNOME Shell is a particular component of GNOME that provides a desktop interface.  It's the default for GNOME, AFAIK.  GNOME is designed in such a way that there can be multiple desktop interfaces built on the same basic core, and so you have other variants (like GNOME fallback).

GTK is a set of graphics widget libraries for writing graphical applications.  The GNOME libraries are built on top of GTK, and GNOME is subsequently built from those libraries.

Thank you so very much for your explanation! Definitely clears my confusion up a bit. So is GTK the Window Manager for GNOME? I've seen things mentioning the words "GTK+ Themes". For instance, some of the categories on GNOME-look.org confuse me even more. I'd like to get to the point of where I understand Desktop Environments enough to try to install different ones and play around a little.

---

### Post by 3Miro on 2012-05-09
A toolkit is a collection of libraries allowing people to create programs that are visually and functionally consistent (i.e. common themes, menus, drag/drop features). The most common toolkits are GTK and QT.

A desktop environment is a collection of programs like panels, menus, settings services etc. Probably the most notable component is the Windows Manager that lets you manipulate opened windows. In fact, many people use a "stand-alone" Windows Manager as a desktop environment.

Gnome 3 is one DE and Gnome-shell is the windows manager and interface. Ubuntu uses Gnome 3, but it replaces Gnome-shell with compiz windows manager and Unity interface.

KDE is the only full DE build using QT toolkit. KDE is very customizable.

XFCE is a very light environment with lots of customizations and functionality. IMO it is the best balance between functionality and speed.

LXDE is even faster and lighter, although it lacks some of the XFCE features.

It is hard to describe the different DE. You can install them all and play with them to see which one you would like. Here is a good tutorial on how to switch between DE:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by Shadius on 2012-05-09
> **3Miro said:**
> A toolkit is a collection of libraries allowing people to create programs that are visually and functionally consistent (i.e. common themes, menus, drag/drop features). The most common toolkits are GTK and QT.

A desktop environment is a collection of programs like panels, menus, settings services etc. Probably the most notable component is the Windows Manager that lets you manipulate opened windows. In fact, many people use a "stand-alone" Windows Manager as a desktop environment.

Gnome 3 is one DE and Gnome-shell is the windows manager and interface. Ubuntu uses Gnome 3, but it replaces Gnome-shell with compiz windows manager and Unity interface.

KDE is the only full DE build using QT toolkit. KDE is very customizable.

XFCE is a very light environment with lots of customizations and functionality. IMO it is the best balance between functionality and speed.

LXDE is even faster and lighter, although it lacks some of the XFCE features.

It is hard to describe the different DE. You can install them all and play with them to see which one you would like. Here is a good tutorial on how to switch between DE:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)


Ohhhh, thank you for that explanation. I'm beginning to get a better understanding now.

---

### Post by Shadius on 2012-05-09
> **iMurshaq said:**
> I see you are running 12.04. That means that you are not running GNOME by default. You are running Unity.

Right, I am running 12.04, but I have installed Gnome Tweak Tool and log in using GNOME Classic. 

Just to be clear, since 12.04 comes with Unity by default. Unity would be considered the Desktop Environment, correct? The Windows Manager would be Compiz? Am I getting it? LOL

---

### Post by overcast on 2012-05-09
Gnome classic or gnome panel has it's limitation like you can't do much settings with it like you used to do in gnome 2. you're just using it in case if the hardware is not supporting unity or gnome 3. Compiz is not window manager, it is effects engine or say it is graphics engine for window manager.

---

### Post by Shadius on 2012-05-09
> **overcast said:**
> Gnome classic or gnome panel has it's limitation like you can't do much settings with it like you used to do in gnome 2. you're just using it in case if the hardware is not supporting unity or gnome 3. Compiz is not window manager, it is effects engine or say it is graphics engine for window manager.

Yeah, I'm using GNOME Classic because I found Unity to be slow for my computer. 

So Compiz is a graphics engine for the Windows Manager? So then, what is the Windows Manager for Unity?

---

### Post by lykwydchykyn on 2012-05-09
Compiz is a window manager.  It has built-in compositing and effects, but it is most definitely a window manager.

---

### Post by overcast on 2012-05-09
Unity is modification of gnome window manager. Say it's like topping over gnome from canonical.

---

### Post by 3Miro on 2012-05-09
> **Shadius said:**
> Right, I am running 12.04, but I have installed Gnome Tweak Tool and log in using GNOME Classic. 

Just to be clear, since 12.04 comes with Unity by default. Unity would be considered the Desktop Environment, correct? The Windows Manager would be Compiz? Am I getting it? LOL

Unity has almost all of Gnome, hence it is correct to say that you are using the Gnome DE with Unity interface. Often times people would just say Unity as Gnome + Unity is the only option (although one should be careful since 11.04 is still around and that used Gnome 2 as opposed to Gnome 3).

Gnome-shell is Gnome DE with Gnome-shell interface, or if you prefer Gnome Default, or even Gnome Pure.

Gnome-fallback is something made for people with low graphics machines. You can say that you are using Gnome in fallback mode or Gnome with Classic interface.

---

### Post by Shadius on 2012-05-09
> **3Miro said:**
> Unity has almost all of Gnome, hence it is correct to say that you are using the Gnome DE with Unity interface. Often times people would just say Unity as Gnome + Unity is the only option (although one should be careful since 11.04 is still around and that used Gnome 2 as opposed to Gnome 3).

Gnome-shell is Gnome DE with Gnome-shell interface, or if you prefer Gnome Default, or even Gnome Pure.

Gnome-fallback is something made for people with low graphics machines. You can say that you are using Gnome in fallback mode or Gnome with Classic interface.

Oh okay, thank you for the clear explanation.

---

### Post by Shadius on 2012-05-09
Okay, focusing on Unity: is it correct to say that Unity is an extension of GNOME 3, which is the Desktop Environment, and Unity being the interface of GNOME 3, and the Window Manager for GNOME 3 with the Unity interface is Compiz? Am I getting there yet? LOL

---

### Post by lykwydchykyn on 2012-05-09
> **overcast said:**
> Unity is modification of gnome window manager. Say it's like topping over gnome from canonical.
GNOME is not a window manager.

> **Shadius said:**
> Okay, focusing on Unity: is it correct to say that Unity is an extension of GNOME 3, which is the Desktop Environment, and Unity being the interface of GNOME 3, and the Window Manager for GNOME 3 with the Unity interface is Compiz? Am I getting there yet? LOL

It's better not to think of GNOME as a single program, but as a collection of programs written from the same libraries and built to interact on a common framework.  

Unity takes bits of GNOME and combines it with Compiz (compiz is the window manager, and things like the dash and launcher are compiz plugins).

---

### Post by Shadius on 2012-05-09
> **lykwydchykyn said:**
> GNOME is not a window manager.



It's better not to think of GNOME as a single program, but as a collection of programs written from the same libraries and built to interact on a common framework.  

Unity takes bits of GNOME and combines it with Compiz (compiz is the window manager, and things like the dash and launcher are compiz plugins).

Ah, that makes sense to me now.

---

### Post by Shadius on 2012-05-09
Okay, I think I have a fair grasp of Unity and GNOME now thanks to all your replies. :) Now, I'd like to know what Metacity and Emerald are? I'm thinking Window Managers? Am I correct?

---

### Post by 3Miro on 2012-05-09
> **Shadius said:**
> Okay, I think I have a fair grasp of Unity and GNOME now thanks to all your replies. :) Now, I'd like to know what Metacity and Emerald are? I'm thinking Window Managers? Am I correct?

Metacity was the default Windows Manager for Gnome 2. There is a current version of Metacity for Gnome 3 that is the Windows Manager of Gnome-fallback (or Gnome-classic).

Emerald is an addition to compiz. Every Windows Manager has its own "windows decorator" that shows the borders of the windows. Compiz is the only WM that I know of that is modular, i.e. it can use more than one decorator. Currently Compiz + Unity uses the Unity decorator, formally known as GTK decorator, which basically uses Metacity themes. Emerald is a decorator designed specifically for compiz, but it is no longer supported and I don't think it works on current versions of compiz (or at least it is rather buggy). Emerald was cool, but very resource intensive.

---

### Post by Shadius on 2012-05-09
> **3Miro said:**
> Metacity was the default Windows Manager for Gnome 2. There is a current version of Metacity for Gnome 3 that is the Windows Manager of Gnome-fallback (or Gnome-classic).

Emerald is an addition to compiz. Every Windows Manager has its own "windows decorator" that shows the borders of the windows. Compiz is the only WM that I know of that is modular, i.e. it can use more than one decorator. Currently Compiz + Unity uses the Unity decorator, formally known as GTK decorator, which basically uses Metacity themes. Emerald is a decorator designed specifically for compiz, but it is no longer supported and I don't think it works on current versions of compiz (or at least it is rather buggy). Emerald was cool, but very resource intensive.

Okay, so since I've switched from Unity to GNOME Classic, I could use Metacity to change how my windows look, right? GNOME Classic is made to look like GNOME 2, but without all the functionality, right?

---

### Post by 3Miro on 2012-05-09
> **Shadius said:**
> Okay, so since I've switched from Unity to GNOME Classic, I could use Metacity to change how my windows look, right? GNOME Classic is made to look like GNOME 2, but without all the functionality, right?

If you are using Gnome-classic and you want to change the decorations around your windows, you need to look for Metacity themes. Gnome-classic does use Metacity.

Gnome-classic has almost all functionality of the old Gnome 2, there were a few things that couldn't be ported to the new system. Originally it was supposed to be something temporary for people with slow graphics cards, but later more developers joined and now most of the old Gnome 2 functionality is included in Gnome-classic.

---

### Post by Shadius on 2012-05-09
> **3Miro said:**
> If you are using Gnome-classic and you want to change the decorations around your windows, you need to look for Metacity themes. Gnome-classic does use Metacity.

Gnome-classic has almost all functionality of the old Gnome 2, there were a few things that couldn't be ported to the new system. Originally it was supposed to be something temporary for people with slow graphics cards, but later more developers joined and now most of the old Gnome 2 functionality is included in Gnome-classic.

You are the man! Your explanations are awesome! 

So these Metacity themes would be under the Metacity category from GNOME-look.org, right? That would be the best start for a beginner like me? Also, GNOME Classic can **only** use Metacity themes, or is it open to other Windows Managers? I noticed you said **was** the default manager for GNOME 2, did it change, and if so, did it change for GNOME Classic too? 

I realize I'm asking **a lot** of questions and that can get annoying to a person. I appreciate all the knowledge you're offering me and your time in helping me understand this topic, so I sincerely hope I'm not annoying now. :)

---

### Post by zombifier25 on 2012-05-10
> **Shadius said:**
> You are the man! Your explanations are awesome! 

So these Metacity themes would be under the Metacity category from GNOME-look.org, right? That would be the best start for a beginner like me? Also, GNOME Classic can **only** use Metacity themes, or is it open to other Windows Managers? I noticed you said **was** the default manager for GNOME 2, did it change, and if so, did it change for GNOME Classic too? 

I realize I'm asking **a lot** of questions and that can get annoying to a person. I appreciate all the knowledge you're offering me and your time in helping me understand this topic, so I sincerely hope I'm not annoying now. :)

Well, Metacity themes provide the window borders (which Metacity and Compiz can use). Full-fledged GNOME themes are usually referred to as GTK themes. When you set themes for your desktop, you can specify the GTK theme (which will affect the overall look and feel of the desktop EXCEPT for windows borders) and the window borders.

---

### Post by kansasnoob on 2012-05-10
Is any of this helpful to you:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

