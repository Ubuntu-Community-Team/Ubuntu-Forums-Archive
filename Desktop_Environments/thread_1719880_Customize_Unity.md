---
title: "Customize Unity"
date: 2011-04-02
forum: Desktop Environments
---

### Post by Frogs Hair on 2011-04-02
I will be installing 11.04 when it is released , my question is will I be able to customize Unity or will I have to use the Ubuntu default themes and icons ? I know the Classic Gnome desktop will be available if I want to use it.

---

### Post by Copper Bezel on 2011-04-02
Themes and icons can be changed and do apply to the panel. The panel's RGBA transparency and the Launcher's icon size and hide behavior can also be changed through CCSM.

---

### Post by Frogs Hair on 2011-04-02
> **Copper Bezel said:**
> Themes and icons can be changed and do apply to the panel. The panel's RGBA transparency and the Launcher's icon size and hide behavior can also be changed through CCSM.

Thanks , I thought I may have to use ambiance and radiance themes and what ever else comes with 11.04 .

---

### Post by pbpersson on 2011-05-03
I there an article somewhere on how to re-size the icons in Unity and make other changes?  I have spent days looking (5 minutes a day is all I can spare) and I cannot find an icon anywhere for Unity settings and don't know where to find the Compiz control panel

---

### Post by marcio_mi on 2011-05-03
here's what you need: [http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

also check [http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

cheers ):P

---

### Post by pbpersson on 2011-05-03
> **marcio_mi said:**
> here's what you need: [http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

also check [http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

cheers ):P

WOW!  Thank you!  At five minutes a day I have enough there to keep me busy for a while ;)

---

### Post by pbpersson on 2011-05-03
In Gnome I used to be able to simply drag and drop an application to the "startup applications" section.

This is not happening in Unity.

When I drag and drop the application to the "startup applications" section nothing happens, it will not add the item.

I was going to add it manually but I cannot right-click on the item in the dash and get any info that would tell me the parameters to add it manually.

I also tried to drag and drop the icon to the desktop and also to a folder to get the information that way but it gives me a silly error message like "cannot get information on /"

What is the correct procedure to accomplish this?

---

### Post by 3rdalbum on 2011-05-03
Nicely-spotted regression. You should report a bug against Unity for this.

You can add startup applications by clicking on the Add button in the Startup Applications panel and navigating to /usr/bin where your programs are located.

---

### Post by karmila on 2011-05-04
> **marcio_mi said:**
> here's what you need: [http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

also check [http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

cheers ):P
Thanks, this is help me much.

One question, can we change opacity of side panel/launcher?
When I set the panel transparent that is a little bit strange to see the side panel/launcher is darker.

---

### Post by srinig on 2011-05-04
> **karmila said:**
> Thanks, this is help me much.

One question, can we change opacity of side panel/launcher?
When I set the panel transparent that is a little bit strange to see the side panel/launcher is darker.

Looks like according to the Unity nomenclature, 'launcher' means the left hand side bar that slides in, and 'panel' means the top bar. And looks like you can only change the opacity of panel (top bar) and not the launcher (side bar).

---

### Post by neilmaclennan on 2011-07-13
I like Unity overall the only thing that is driving me up the wall is that the drop down menus for each window is not on the window itself when the window isn't maximized but instead is transported to the upper taskbar. I like window switching on hover but this is tedious and really annoying when I go to the drop menus and hover over another window on the way and it switches the menu to the new menu This really gets tedious when I have one maximized window and a terminal open too. Can someone tell me how to change that and how to reposition the unity launcher to another location, I don't like it on the left hand side, or how I can build a secondary unity bar for more apps or app types. I would like one for my study apps. Like Python and the related gui's and shells etc... Thanks 

If there is no way to change this how do I remove Unity and revert to the old style, like it is before you install the driver for a third party video card? I don't want to revert the graphics quality if I don't have to. And I don't want to uninstall or remove the wrong package(s) by mistake if I have to do this.

I have tried to find the answers myself but haven't found anything via settings and right clicking isn't doing anything for the launchers properties and how to build a secondary one. I'm also new to Ubuntu and am transitioning from windws sorry for any errors):popcorn:

---

### Post by jjb2011 on 2011-07-13
My first reaction when I heard of Unity is Great! Finally an object dock where you simply drag and drop, right-click for settings, move icons around. 

Ouch. I hope this is only a set of bugs:

1. Wine programs won't "stick" to the object dock. Mac will let you stick whatever (ditto object dock for Windows). You can "search for applications, click again to see all, find Microsoft Word - or whatever) and then it will appear on the launcher ONLY WHEN YOU HAVE THE PROGRAM OPEN!!). It appears as a Wine symbol (not Word which can attach to Docky, BTW). Then it disappears when you shut down. 

2. Can't move icons/shortcuts up and down. They just won't move. 

The work arounds defeat Ubuntu's efforts to get something working "out of the box" for the "mainstream." How many people are going to do this:

[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

I realize this is a project in the making but if it isn't as good as docky, I hope we can just pin the thing away and still use Docky. 

If there is a solution that doesn't require all the hacking of above (and no mention of Wine programs?) then I'll just stick with 11.04 for a while and then ditch Ubuntu for something else. It's a shame: "snatching defeat from the jaws of victory," as they say. 
Not many! Docky is easier to configure, much easier. 

But I would like an easy way to do #1 (not mentioned in Ubuntu help) or #2 (says you can move but I can't on my 64-bit machine and OS).

---

### Post by Frogs Hair on 2011-07-13
2. Your Icons should be able to move in Unity 3D , as in drag and drop to change positions . Try this command and see if they move . You may have to add your applications again after using it.```
unity --reset-icons
```

---

