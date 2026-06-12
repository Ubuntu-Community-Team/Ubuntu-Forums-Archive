---
title: "Blank Screen when Switching Workspaces"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by Shoot3r101 on 2007-09-04
Well I *just* installed Ubuntu and already encountered 1-3 errors and I will report those errors in their appropriate section. but anyway, installation went cool everything went OK! Then after adding 4 workspaces(in total of 4) I clicked on one and my panels just disappeared just gone! So im left with this wallpaper. Please help.

---------Basics-----------
Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
BIOS: Phoenix ROM BIOS PLUS Version 1.10 A01
Processor: Intel(R) Celeron(R) CPU 2.53GHz
Memory: 254MB RAM
---------Display-----------
DirectX Version: DirectX 9.0c (4.09.0000.0904)
Card name: Intel(R) 82865G Graphics Controller
Manufacturer: Intel Corporation
Chip type: Intel(R) 82865G Graphics Controller
Display Memory: 96.0 MB
Current Mode: 1024 x 768 (32 bit) (75Hz)
---------HDD-----------
Drive: C:
Free Space: 60.6 GB
Total Space: 73.2 GB
File System: NTFS
Model: ST380011A

Desktop effects are on ;).

---

### Post by aquavitae on 2007-09-04
Did you do a normal install, or is it installed in a virtual machine.  I ask this becaise you say your operating system in winxp.

Have you tried it with desktop effects off?  They are beta software, meaning they can easily cause problems so that might be it.

---

### Post by Shoot3r101 on 2007-09-04
ohhhh ehhh you know that system spec is old sorry! But I figured out the issue. thanks anyway.

---

### Post by scru on 2007-09-04
What's the issue? I have the same problem

---

### Post by kloine69 on 2007-11-18
I am having the same problem, it has started since i upgraded from feisty fawn. When i switch workspace all i see is the background, no toolbars and cannot get back to workspace 1. I have to restart. This si very annoying especially when i do it accidentally, I would appreciate some help on this, cheers.

---

### Post by aquavitae on 2007-11-19
Not sure what the problem is, but did you know if you press Ctrl-Alt-Backspace it will kill the display, effectively taking you straight back to log in.  Much faster that rebooting if something goes wrong.

Desktop effects? (see my comment in the previous post)

---

### Post by reghuram on 2007-11-19
Hi,

I'm having the same problem. Is there a workaround instead of pressing Ctrl-Alt-Backspace. Cause there are times when I accidentally switched over and my workspace 1 was still running some apps.

---

### Post by aquavitae on 2007-11-19
I think its not a workaround you're loooking for, its a solution to the problem :) Ctrl-Al-Bkspc is really just for when things go wrong with the gui... e.g. compiz takes over too much resources so you can't even logout, the screen saver freezes (that's happened too me more often than it should), etc.

Are you using compiz (i.e. desktop effects.) If so, try without and see if it still happens.  It's not really a good solution, but it will help to find the problem.

---

### Post by Tteddo on 2007-11-19
I have this problem on one of my laptops also. The other works perfect, as does my desktop.
If I use the hotkey I setup to switch desktops (F1, F2, F3) it works fine, but if I click on another desktop's square in the workspace switcher the panels disappear and all I have is the wallpaper. I think it was fine last week when I was using it and just noticed today this problem.

---

### Post by Tteddo on 2007-11-19
Here's another clue. I noticed that if I have something open in the 1st window I can alt-tab to it.
More significantly, I noticed that after CTRL-ALT-Backspace after it comes back up if I right click on the workspace switcher and go to preferences it is only set for 1 column and 1 row instead of 3 columns and 1 row like it was set. 3 squares are still there though.

---

### Post by kloine69 on 2007-11-20
Thankyou all for your help, i changed my graphics card driver and installed compiz "Advanced Desktop Effects Settings" and this has solved teh problem for me. Dunno if this is any use to you but it should beat restarting even if you are not interested in the added functionality. If you want help with this here is a help guide: [http://ubuntu-tutorials.com/category/compizberyl/](http://ubuntu-tutorials.com/category/compizberyl/)

---

### Post by Tteddo on 2007-11-21
Now, after a couple of updates and a reboot, it is now like I have 6 desktops. If I use my hotkeys between them I get one set, and if I click on the squares in the desktop switcher I get 3 others!
Anyone else seeing this?

---

### Post by aquavitae on 2007-11-22
I remember something like that happeining in beryl - are you using beryl?  It was a bug, but could be fixed by turning of beryl, setting the number of desktops to 1, turning on beryl, and then setting the number of desktops you want within beryl.  Its something to do with beryl and the normal window manager (e.g. metacity, kwin) both trying to set the number of desktops so they got multiplied.

---

### Post by Tteddo on 2007-11-22
> **aquavitae said:**
> I remember something like that happeining in beryl - are you using beryl?  It was a bug, but could be fixed by turning of beryl, setting the number of desktops to 1, turning on beryl, and then setting the number of desktops you want within beryl.  Its something to do with beryl and the normal window manager (e.g. metacity, kwin) both trying to set the number of desktops so they got multiplied.

I am running Compiz, which Beryl merged with, right?
It's kind of confusing because Gnome calls it the Workspace Switcher, and you have multiple desktops, and in the Compiz settings it's called viewports in the Viewport Switcher and Faces in the Rotate Cube section. They all have the same hotkeys that change when I change in one section too. Thay all referring to the same thing, right?

What's even stranger is the original computer that I posted here about is back to normal without doing anything, and my desktop is doing the odd stuff now. My other laptop with the settings exactly the same as my desktop (as far as I can see) never had a problem.

---

### Post by Tteddo on 2007-11-27
I found it! If you go into the settings for GL Desktop, there is a page for workspaces. I went in and set it for classic, 1 workspace, then put it back and set the workspaces for 4 and now it is working properly with the cube like it used to. The GL Desktop must have a glitch with Compiz.

---

### Post by Enginirical on 2007-11-29
Hey I have just been having the same issues, But have now sorted it and here&#347; why and how:

If I clicked on viewport/desktop selection the menu&#347; would disappear. Furthermore all the windows tabs were annoyingly on all desktops regardless of where I opened them.

As someone mentioned on another thread there is a difference between desktops and viewports, as far as I understand, (Im a noob too) the result is the same but one is done through gnome-metacity and one is done through compiz fusion.

To fix your problem open up compiz theme manager (system>administration>appearence-->visual effects>preferences)

select General options then desktop size. Then reduce number of desktops to 1 and vertical virtual size to 1.

The Virtual horizontal size is the number compiz viewports, If you select you desired number of viewport (desktops) here i.e. 4 for a cube then it will work as you expect it too without menus disappearing.

I hope this helps, let me know how it goes...good luck!
__________________

---

### Post by kulturloseramerikaner on 2007-12-06
> **Enginirical said:**
> Hey I have just been having the same issues, But have now sorted it and here&#347; why and how:

If I clicked on viewport/desktop selection the menu&#347; would disappear. Furthermore all the windows tabs were annoyingly on all desktops regardless of where I opened them.

As someone mentioned on another thread there is a difference between desktops and viewports, as far as I understand, (Im a noob too) the result is the same but one is done through gnome-metacity and one is done through compiz fusion.

To fix your problem open up compiz theme manager (system>administration>appearence-->visual effects>preferences)

select General options then desktop size. Then reduce number of desktops to 1 and vertical virtual size to 1.

The Virtual horizontal size is the number compiz viewports, If you select you desired number of viewport (desktops) here i.e. 4 for a cube then it will work as you expect it too without menus disappearing.

I hope this helps, let me know how it goes...good luck!
__________________
It does help; thanks.  I've just been dealing with this issue lately as I have had no time over the past month or so to troll the forums looking for the solution, but this has done the trick!

---

