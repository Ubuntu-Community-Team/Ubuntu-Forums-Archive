---
title: "Window title bar doesn't match theme"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by saoirse1916 on 2008-03-16
Hello all -- I'm new to Linux in general, but am really enjoying Ubuntu so far.  I've got one purely cosmetic problem that's driving me nuts...no matter what theme I run, the title bar of the active window is always a deep red color.  I tried a printscreen but unfortunately that doesn't capture the active window title bar -- but I've tried different themes and it's always the same.

If it matters, I'm running Ubuntu 7.10 Gutsy, ATI X1300 video card, Emerald and Compiz.

Thanks very much!

---

### Post by saoirse1916 on 2008-03-18
Can someone tell me how to change the active window colors?  If there's something wrong with how my OS is displaying themes then perhaps I can at least edit the active window of the current theme to match.

---

### Post by Zorael on 2008-03-18
Compiz is a "window compositioner", and doesn't at all handle the way windows look. As such, a window decorator must be loaded alongside it to take care of that. You're likely running Emerald as your window decorator, which has its own theme manager.


If you wish to continue using Emerald, download the **emerald-theme-manager** package (I think that's what it's called, not sure if it's in the multiverse/universe repositories, which may need to be activated in Software Sources).

Then you could download and try some themes from these links - amongst others, of course.
[http://themes.beryl-project.org/](http://themes.beryl-project.org/)
[http://gnome-look.org/](http://gnome-look.org/)
[http://kde-look.org/](http://kde-look.org/)


If you wish to regain your Gnome-y look, you will need to specify in the Window Decorations plugin that it should use the gtk-window-decorator instead. Just enter 'gtk-window-decorator' in the Command field for that plugin. If you're running KDE you're a bit out of luck; there is a kde-window-decorator but it's buggy as heck, so I'd suggest you stick with Emerald in that case.

Now, this may need an X restart (Ctrl+Alt+Backspace, save your work or it'll be lost). And if it still doesn't work, try opening a run box (alt+f2?) or preferably a terminal, then enter 'gtk-window-decorator --replace'. That may work, and if it doesn't, at least it'll tell you why.

If you lose control of your windows after entering that, enter 'emerald --replace' to return to your red titlebars.

---

### Post by Therion on 2008-03-18
The following worked for me for a while, but later on I had no choice but to disable Emerald from auto-starting with Compiz at boot.  
Before we castrate Emerald, though, try this quick trick:

Install this [Compiz Switch](http://forlong.blogage.de/article/pages/Compiz-Switch) and add it to a panel.
Right-click on the Compiz Switch and turn OFF Compiz.
Change your theme using System/Preferences/Appearance.
Right-click on the Compiz Switch and turn Compiz back ON.
Cross your fingers that your chosen theme "sticks".

---

### Post by saoirse1916 on 2008-03-18
This is wild.  When I logged in to get to work on this issue, I noticed my active windows were still red, and my resolution was only 1024x768 instead of 1280x800.  So, after 3 BSODs I finally got everything back.  But during the brief moments when I could actually boot into X, I noticed that my active windows were the proper color, black.

Anyway, once my drivers and resolution were straight, of course the active windows were red again.  Zorael, the only thing I understood from your suggestion was to run 'gtk-window-decorator --replace' which I did.  That worked, until I rebooted.  Therion, I downloaded and installed Compiz Switch which does indeed work.  When I switch it off, my windows are the proper color but as soon as I turn it back on it screws up again.

Would a reinstall of compiz fix this perhaps?  If so, hopefully someone can walk me through how to do that because I have no idea.

---

### Post by saoirse1916 on 2008-03-18
Well, just for kicks I uninstalled and reinstalled compiz and emerald.  As soon as I click on Custom in Appearance Settings I get a popup asking if I want to confirm those settings -- with a red border.  Unreal.  Can anyone let me know what I'm doing wrong or does every custom theme always display the active window as red?  Since I can't screenshot it I suppose this could be happening to everyone and it's just considered normal.

---

### Post by Therion on 2008-03-18
The reason your window borders are red is because Emerald is being used by Compiz as your default Window Decorator (that's Beryl Red you're seeing, by the way).  You can either use Emerald to theme your Window Decorations, or you can use Metacity.  If you want to use Metacity, you have to stop Emerald from loading up along with Compiz.  Then Metacity will be the default Window Decorator, which will then use the GTK portion of your Metacity theme to theme your window decorations.  Clear as mud?

To prevent Emerald from starting up when you boot up:
```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
Obviously if you WANT to use Emerald as your default Window Decorator, you would not want to do this.

---

### Post by saoirse1916 on 2008-03-18
Ok, I did that -- now my windows look pretty cool again but I can't turn on any of the advanced desktop effects or else the title bar disappears completely.

And just so I understand completely, if you use Emerald your active window will always be red, regardless of theme?

---

### Post by FuturePilot on 2008-03-18
> **saoirse1916 said:**
> 

And just so I understand completely, if you use Emerald your active window will always be red, regardless of theme?
No. You need to change the theme through the Emerald Theme Manager. System&#8594;Preferences&#8594;Emerald Theme Manager.

---

### Post by saoirse1916 on 2008-03-19
Ok -- that's what I did and regardless of the theme, my active window was always red.  I'll try and reinstall Emerald again and see what happens.

---

### Post by saoirse1916 on 2008-03-19
I installed fusion-icon in the hopes that it would give me some better control over what was happening.  Turns out it just enabled Emerald which then removed the title bar from my windows and my windows were then immovable.

So I uninstalled Emerald through apt-get and now I have no idea what to do.  Somehow I've managed to make my system completely incompatible with Emerald, evidently, and the default window decorator seems unable to handle the "custom" option on Visual Effects.

Does anyone know how I can fix this?  I'm starting to think that I was being WAY to picky when all my themes drew a red active window!  That's the least of my problems now!

---

### Post by Therion on 2008-03-19
Well, do you WANT to use Emerald as your Window Decorator, or do you want to use Metacity?  

If you want to use Metacity put the Compiz-Fusion button on a panel.  Right-click on the button (in the panel).  Use that menu to turn OFF Compiz as your Windows Manager, right-click on it again and enable GTK as your Window Decorator.  After that, right-click on the button one more time to renable Compiz as your Windows Manager.  

If that doesn't solve your problem, most likely you need to stop Emerald from loading at startup with the Terminal commands I gave you earlier.

If you DO want to use Emerald as your Window Decorator, I can't help you as Emerald does nothing but give me problems.

---

### Post by saoirse1916 on 2008-03-19
Ideally I'd like to use anything that works.  When I run 'fusion-icon' from terminal, I get this:

* Using the GTK Interface
* Searching for installed applications...
/usr/bin/compiz.real
/usr/bin/ccsm
/usr/bin/compiz
/usr/bin/metacity
* gnome session
* Decorator "" is invalid.
*** Warning: no decorator found
* fglrx found, exporting: LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa
* Executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

And then the top of my window goes away and I can't move my windows.  I'm not sure where to go from here.

---

### Post by Therion on 2008-03-19
I didn't say anything about running Compiz Switch from a terminal.  

Drag the button onto a panel so you can access the context menu for it.  

Use that menu to switch off Compiz, enable Metacity, select a GTK theme and re-enable Compiz.

---

### Post by saoirse1916 on 2008-03-19
Ahh sorry -- I misunderstood which app you were talking about.  Ok, I installed the switch again and added it to the panel.  I clicked on it which presumably turned ON compiz because my title bar disappeared.  So I clicked it again, the top bar came back.  Now when I right click Compiz Switch my choices are "Launch", "Properties" (which seems to be just the command line and name), "Remove from Panel", "Move", and "Lock to Panel."  Where did I go wrong?

EDIT: Evidently I didn't have gtk-window-decorator installed because for kicks I ran that command at a prompt and it wasn't found.  So I installed it through Synaptic.  Now when I click the Compiz-Switch it alternates between having a drop shadow on my window and not having one...I'll assume that's GTK kicking in when the shadow comes on?

Also, does GTK not support the 4-sided cube?  I've got cube and rotate both enabled and under Visual Effects I select Custom, Preferences, General Options, set Horizontal Virtual Size to 4, but it doesn't save.  It keeps resetting to Normal or Extra and dropping my selections in Custom.

---

### Post by Therion on 2008-03-20
> **saoirse1916 said:**
> Ahh sorry -- I misunderstood which app you were talking about.  Ok, I installed the switch again and added it to the panel.  I clicked on it which presumably turned ON compiz because my title bar disappeared.  So I clicked it again, the top bar came back.  Now when I right click Compiz Switch my choices are "Launch", "Properties" (which seems to be just the command line and name), "Remove from Panel", "Move", and "Lock to Panel."  Where did I go wrong?

EDIT: Evidently I didn't have gtk-window-decorator installed because for kicks I ran that command at a prompt and it wasn't found.  So I installed it through Synaptic.  Now when I click the Compiz-Switch it alternates between having a drop shadow on my window and not having one...I'll assume that's GTK kicking in when the shadow comes on?

Also, does GTK not support the 4-sided cube?  I've got cube and rotate both enabled and under Visual Effects I select Custom, Preferences, General Options, set Horizontal Virtual Size to 4, but it doesn't save.  It keeps resetting to Normal or Extra and dropping my selections in Custom.
You need to  **RIGHT-CLICK** on the Compiz Switch in your panel to access the context menu. Turn OFF Compiz/select Metacity.  Change your theme via the Appearances Menu and then re-enable Compiz.  

If turning Compiz back on makes your window decorations go wonky: 

1.) Make sure you have the Window Decorations plugin turned "OFF" in the Compiz Config Settings Manager.

2.) Use the command line to prevent Emerald from loading with Compiz.

```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```

---

### Post by saoirse1916 on 2008-03-20
> **saoirse1916 said:**
>  Now when I right click Compiz Switch my choices are "Launch", "Properties" (which seems to be just the command line and name), "Remove from Panel", "Move", and "Lock to Panel."  Where did I go wrong?

That's the only menu I get when I right-click.  So either I've installed the wrong app (entirely possible) or there's some other thing that I need to enable in order to get this alternate menu to pop up.

---

### Post by Therion on 2008-03-20
Get yourself a handy-dandy Compiz Switch right [HERE](http://forlong.blogage.de/article/pages/Compiz-Switch).

---

### Post by saoirse1916 on 2008-03-20
Yep, that's the one I've got installed.  I used the deb package -- would it matter if I used that vs. the make install method?

---

### Post by Therion on 2008-03-20
Ack!  <face-palm> My mistake... 

Take a look at [this link](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/).  See the screenshot?  That's the right-click/context menu that allows you to switch between Compiz and Metacity and Emerald and GTK (under Window Decorators).  Now everything I've been saying should make sense.  My bad... I was thinking of the the wrong button, or icon, or whatever.  

Get this button on your panel, right-click on it, etc. etc. etc. ...  

Sorry for the confusion!

---

### Post by saoirse1916 on 2008-03-21
Ok, I installed that one.  I added it to the launcher but there must be some other way to add it because when I right click the icon I get the exact same menu as I did before.

---

