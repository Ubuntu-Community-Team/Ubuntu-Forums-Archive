---
title: "window title bar disappears"
date: 2009-03-31
forum: Desktop Environments
---

### Post by green69 on 2009-03-31
My window title bar disappear, but not only with firefox, in every types of windows. It's a such annoying thing, because every time a want to minimize a window I have to alt and drug that window, and to close I have to do it from the bottom pannel.

PLEASE can anybody help me?!?

---

### Post by Daddyo-613 on 2009-03-31
> **green69 said:**
> My window title bar disappear, but not only with firefox, in every types of windows. It's a such annoying thing, because every time a want to minimize a window I have to alt and drug that window, and to close I have to do it from the bottom pannel.

PLEASE can anybody help me?!?

Hi;

This issue has come up before. Check out this thread. I hope it helps.

[http://ubuntuforums.org/showthread.php?t=1107142](http://ubuntuforums.org/showthread.php?t=1107142)

---

### Post by drs305 on 2009-03-31
If you are running compiz, here is something simple you can try. Go to the CompizConfig Settings Manager (if installed): 
System > Preferences > CompizConfig Settings Manager (or *ccsm* in terminal).

Effects > Tick/enable 'Window Decoration'.

---

### Post by green69 on 2009-04-03
> **drs305 said:**
> If you are running compiz, here is something simple you can try. Go to the CompizConfig Settings Manager (if installed): 
System > Preferences > CompizConfig Settings Manager (or *ccsm* in terminal).

Effects > Tick/enable 'Window Decoration'.

No, the links above doesn't help and Window decoration is already enabled.

Anybody has other suggestion???

---

### Post by Daddyo-613 on 2009-04-03
Can you provide some information about your system?

**The Ubuntu Version:**
Open a terminal Applications>Accessories>Terminal and cut and paste the following code and press <enter> to verify what version of Ubuntu you are using.

```
cat /etc/issue
```**The Kernal Installed:**
Then cut and paste the following code and press <enter> to verify the kernal installed on your machine.

```
uname -r
```**Version of Compiz Configuration Settings Manager:**
Then cut and paste the following code and press <enter> to verify the version of your settings manager running on your machine.
 
```
ccsm --version
```**The Video Card:**
Then cut and paste the following code and press <enter> to display what video card is on your system.

```
lspci | grep -i vga
```**The Video Driver Installed:**
Then go to System>Administration>Hardware Drivers to display the video driver that you are using on your machine. It will be the one that has the green button lit up.

**Windows Manager:**
If you are running Ubuntu 8.10 Intrepid Ibex, by default the GTK Window Decorator is used unless you have install Emerald or some other manager.

**Windows Theme:**
Then go to System>Preferences>Appearance. The <Theme> tab will  tell you which Windows Theme has been selected and the <Visual Effects> tab will tell you which desktop environment has been enabled. To run the full gambit of Compiz effects the <Extra> button has to be enabled.

If you post this information you'll likely get the answer you're looking for.

---

### Post by green69 on 2009-04-22
> **Daddyo-613 said:**
> Can you provide some information about your system?

**The Ubuntu Version:**
Open a terminal Applications>Accessories>Terminal and cut and paste the following code and press <enter> to verify what version of Ubuntu you are using.

```
cat /etc/issue
```**The Kernal Installed:**
Then cut and paste the following code and press <enter> to verify the kernal installed on your machine.

```
uname -r
```**Version of Compiz Configuration Settings Manager:**
Then cut and paste the following code and press <enter> to verify the version of your settings manager running on your machine.
 
```
ccsm --version
```**The Video Card:**
Then cut and paste the following code and press <enter> to display what video card is on your system.

```
lspci | grep -i vga
```**The Video Driver Installed:**
Then go to System>Administration>Hardware Drivers to display the video driver that you are using on your machine. It will be the one that has the green button lit up.

**Windows Manager:**
If you are running Ubuntu 8.10 Intrepid Ibex, by default the GTK Window Decorator is used unless you have install Emerald or some other manager.

**Windows Theme:**
Then go to System>Preferences>Appearance. The <Theme> tab will  tell you which Windows Theme has been selected and the <Visual Effects> tab will tell you which desktop environment has been enabled. To run the full gambit of Compiz effects the <Extra> button has to be enabled.

If you post this information you'll likely get the answer you're looking for.

Ok, thanks a lot. I'll paste all the info.

Ubuntu 8.10 \n \l

2.6.27-11-generic

CCSM 0.7.8

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

VIDEO DRIVE:
no proprietary video drive

Windows theme:
it's a modified one but I have the same problem with all of them. (I tried to change them.



PLEASE CAN ANYBODY KEEP TO HELP ME????

---

### Post by HullDown on 2009-04-23
Had the same problem (it sounds like).  Also in Compiz, go to the Widows Management group > Place Windows.  Make sure the Enable Place Windows check box is checked and the placement mode set to Smart (or try one of the other settings).  

So far it has worked perfectly for me.

---

### Post by green69 on 2009-04-25
> **hulldown said:**
> had the same problem (it sounds like).  Also in compiz, go to the widows management group > place windows.  Make sure the enable place windows check box is checked and the placement mode set to smart (or try one of the other settings).  

So far it has worked perfectly for me.

please anyone can help us???

---

### Post by drs305 on 2009-04-25
> **green69 said:**
> please anyone can help us???

Can you post a picture of your problem?

I mentioned compiz's windows decoration feature earlier. If you run compiz you can take it a step further. This step shouldn't be necessary but I found it worked several versions ago: 
Open compiz, window decorations. With one of your 'problem' windows open, in compiz click on the " + " to the left of the 'Decoration windows' box that says "any". Then click on the body of the window of the problem app. It should add an entry into the compiz window. Select 'Back' and see if it fixed the title bar. If it works, instead of having to do this for each application, you can make an entry such as "!Title=FixMe" which would put the command into effect for any window not titled "Fix Me".

---

### Post by green69 on 2009-04-25
> **drs305 said:**
> Can you post a picture of your problem?

I mentioned compiz's windows decoration feature earlier. If you run compiz you can take it a step further. This step shouldn't be necessary but I found it worked several versions ago: 
Open compiz, window decorations. With one of your 'problem' windows open, in compiz click on the " + " to the left of the 'Decoration windows' box that says "any". Then click on the body of the window of the problem app. It should add an entry into the compiz window. Select 'Back' and see if it fixed the title bar. If it works, instead of having to do this for each application, you can make an entry such as "!Title=FixMe" which would put the command into effect for any window not titled "Fix Me".

First of all thanks so much for your help!

Anyway it doesn't solve my problem.
If I do what you say the title bars (of every kind of windows) disappear completely. Maybe you haven't understood exactly my problem, so I'll resume you:
 The title bars disappear because (when windows are maximized) they are hidden behind the top panel and minimize, maximize and close buttons are not reachable. Anyway when I ctrl + alt and drag the windows, it minimize and the title bar with the buttons appear again.
It is so unconfortable because every time you want to resize a windows youu have to "ctrl + alt and drag".

Any other clue? 

Thanks anyway

---

### Post by green69 on 2009-04-25
> **green69 said:**
> First of all thanks so much for your help!

Anyway it doesn't solve my problem.
If I do what you say the title bars (of every kind of windows) disappear completely. Maybe you haven't understood exactly my problem, so I'll resume you:
 The title bars disappear because (when windows are maximized) they are hidden behind the top panel and minimize, maximize and close buttons are not reachable. Anyway when I ctrl + alt and drag the windows, it minimize and the title bar with the buttons appear again.
It is so unconfortable because every time you want to resize a windows youu have to "ctrl + alt and drag".

Any other clue? 

Thanks anyway

I was forgetting... here is my problem picture!

---

### Post by drs305 on 2009-04-25
Ok, I understand your problem now. Sorry it took a while. One picture is worth a lot.

Here are 2 things to try:
1. Compiz, Workarounds, Legacy Fullscreen Support. Change the setting.

2. Turn off compiz and see if the problem remains.
Either with System, Preferences, Appearance, Visual Effects, None; or in terminal with "metacity --replace". 

If the problem goes away with #2 then we can isolate it to a compiz setting.

Months ago I played with a setting which prevented manually moving any window above the panel. I don't remember if it was via metacity, compiz or something else. I can't find my notes about it but I will continue looking.

---

### Post by green69 on 2009-04-25
> **drs305 said:**
> Ok, I understand your problem now. Sorry it took a while. One picture is worth a lot.

Here are 2 things to try:
1. Compiz, Workarounds, Legacy Fullscreen Support. Change the setting.

2. Turn off compiz and see if the problem remains.
Either with System, Preferences, Appearance, Visual Effects, None; or in terminal with "metacity --replace". 

If the problem goes away with #2 then we can isolate it to a compiz setting.

Months ago I played with a setting which prevented manually moving any window above the panel. I don't remember if it was via metacity, compiz or something else. I can't find my notes about it but I will continue looking.

Thanks.
I've just tried what you suggested.

1. Compiz, Workarounds, Legacy Fullscreen Support. is already checked. If I uncheck it the problem remain the same.

2. System, Preferences, Appearance, Visual Effects, None; it doesn't solve my problem, an if I type "metacity --replace" on pipe the command it doesn't finish to execute and strange things happens on the screen and I have to log out ang log in again to operate.

Any other suggestion?

---

### Post by ninjapirate89 on 2009-04-25
Try opening a terminal and typing in 
```

gtk-window-decorator

```

---

### Post by green69 on 2009-04-25
> **ninjapirate89 said:**
> Try opening a terminal and typing in 
```

gtk-window-decorator

```

With the disabled compiz it doesn't works. 
And if I check system - preference - appearence - visual effect - normal
and then type "gtk-window-decorator", the results is:

#
gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.#

---

### Post by ninjapirate89 on 2009-04-25
> **green69 said:**
> With the disabled compiz it doesn't works. 
And if I check system - preference - appearence - visual effect - normal
and then type "gtk-window-decorator", the results is:

#
gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.#

Sorry I couldn't help more. I had this problem once and that fixed it for me.

---

### Post by green69 on 2009-04-25
> **ninjapirate89 said:**
> Sorry I couldn't help more. I had this problem once and that fixed it for me.

Thanks anyway. Have anybody any other suggestion?
What do you think I should reinstall to solve this problem? It is possible to reinstalling ony the desktop environment? How can I do it? And will this solve my problem?

---

### Post by drs305 on 2009-04-26
If you decide to keep running compiz, I think this might keep your titles on the screen.

Make sure you are running compiz, then:

Compiz, Place Windows, Fixed Window Placement, Windows with Fixed Positions. 

Add a "class=any" by clicking the "+" and selecting Title. I am not sure if "Title=any" will work, but if it doesn't, use "!Title=FixMe" or something beginning with "!". That should keep all title bars within the viewing area. 

If a general setting doesn't work, try it on specific windows, and set the X Y positions to values that allow it to open within the window (start with 100 100 and experiment). 

Best of luck, I'm running out of ideas.  ;-)

---

### Post by green69 on 2009-04-26
I finally solve the problem with the help of Daddyo-613

In sessions preference (System - Preferences - Sessions) under the tab labeled "Startup Programs", “Window Manager” is already checked. A part this in my case “Maximus Window Management” is even already checked but “maximus” is not.

When I noticed it I try to uncheck “Maximus Window Management” and then log out and log in again. The problem was magically disappeared!

Hope this can help to other people!

Thanks everybody

---

### Post by theromanone on 2009-04-29
> **HullDown said:**
> Had the same problem (it sounds like).  Also in Compiz, go to the Widows Management group > Place Windows.  Make sure the Enable Place Windows check box is checked and the placement mode set to Smart (or try one of the other settings).  

So far it has worked perfectly for me.

wow. [SIZE="4"]THANK YOU[/SIZE]!!!!

---

### Post by 22by7 on 2009-10-04
If you are encountering this problem, probably Compiz is conflicting with Maximus Window Managment. Just remove Maximus Window Mgmt from startup applications and restart, your title bar will be back in place for all windows.

---

### Post by BagB on 2011-02-17
Even if this thread is a bit dated, here goes -

For my system - Ubuntu 10.04, with CompizConfig Settings Manager  installed. On the "CompizConfig Settings Manage" I had to select  "Preferences" on the left panel, and use for the "Backend" the option -  "Flat-file Configuration Backend". This freezes most inputs, so I had to  reset the machine by switching the power off. On restart I got back the  title bar and was back in business.
 
 I know its not an elegant solution, but it worked for me
(note: I also posted this on a newer thread)

---

