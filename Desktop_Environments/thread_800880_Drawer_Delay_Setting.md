---
title: "Drawer Delay Setting"
date: 2008-05-20
forum: Desktop Environments
---

### Post by brewstah on 2008-05-20
I have a few Drawer widgets added to my Gnome panels.  When clicking on them I must wait almost three seconds before the Drawer will expand.  I want to change this delay to ZERO seconds.  When right-clicking on a Drawer and selecting Properties, I find there is no setting to change this irritating behavior.

Is there a way to change the Drawer expansion to no delay?  If there is, how do I change it?

---

### Post by Hubi17 on 2008-05-28
I am wondering the same thing.
Is it even possible to change the delay settings?
Any help would be appreciated.

Edit:

I found a setting in gconf-editor, but I was only able to set the animation speed to "fast". if I completely disabled animations, the drawer would appear over the top panel, instead of the bottom right where its supposed to be.

To change the speed, open gconf-editor, navigate to apps->panel->toplevels->panel_0

there you can change the key for animation to fast.

(your draw may have a different name, depending on your added panel elements - I think O_o )

Hope that helps.
I try some more to completely disable the animations. Will post back if I figure it out.

---

### Post by geoken on 2008-05-28
Intersested in this as well. I tried using a drawer the other day to mimick the behaviour of the quicklanch menu in Window's but the slow animations made it useless. It was faster for me to navigate through the main menu than it was for me to wait for the panel animation to end.

---

### Post by MaxVK on 2008-10-11
Quite an old thread and not marked as solved - is there a resolution to this? Iv tried turning the animation off, but there seems to be no way to get it to appear above the drawer button, even though it appears nice and quickly.

Have we gone any further or is this abandoned now?

Cheers

Max

---

### Post by compu73rg33k on 2009-02-22
Wondering the same thing. I hope this gets fixed. When I unselect enable animations, when I open the drawer it appears in the upper left hand corner of the screen instead of near the bottom panel where the drawer is contained in.

---

### Post by Equiflux on 2009-06-09
[https://bugs.launchpad.net/gnome-panel/+bug/108951](https://bugs.launchpad.net/gnome-panel/+bug/108951)

We're not the only ones who hate this problem. Seems like this has been going on for a while. This problem hasn't been addressed after how many major releases? I do agree that this delay almost makes the drawer completely useless.

---

### Post by MaxVK on 2009-06-09
I forgot about this since the drawer seemed useless, however, Iv recently upgraded to Jaunty so I just tried again but the drawer is just as useless. I certainly wish someone would get their act together and sort this out - its such a good idea, but its of no use as it is.

---

### Post by AaronWyatt on 2009-07-29
This bug has been around since April 2007, and has been confirmed but not yet fixed.  See: [https://bugs.launchpad.net/gnome-panel/+bug/108951](https://bugs.launchpad.net/gnome-panel/+bug/108951)

---

### Post by lunatico on 2009-10-09
It looks like if you disable compiz the delay is shorter... if I have to choose between compiz and drawer believe me, I go for compiz.

---

### Post by adamantivm on 2010-08-14
Just leaving my note here as another user interested in finding a workaround or solution to this.
I really need usable drawers. I also really need compiz. I so much wish I could get rid of that delay

---

### Post by compu73rg33k on 2010-08-15
> **adamantivm said:**
> Just leaving my note here as another user interested in finding a workaround or solution to this.
I really need usable drawers. I also really need compiz. I so much wish I could get rid of that delay
So you don't use compiz and it's still a bad delay for you?

Does anybody have any idea WHY the delay exists? Is it a deliberate "feature" by the developers? Or is it some delay in loading libs to enable the drawer? I have a hard time believe the latter, but I'm so confused why any developer would spend effort implementing the former.

What language is the drawer app written in? What package is it?

---

### Post by kerry_s on 2010-08-15
you can use apwal as a launcher. the bad is manualy doing the launcher, no drag & drop like the drawer.

but with apwal you can do your own style layout, you can run more then 1, it even can do sub menus.

to me it's much better then a drawer. i'm using it on tint2's clock click.

---

### Post by lunatico on 2010-08-15
> **adamantivm said:**
> Just leaving my note here as another user interested in finding a workaround or solution to this.
I really need usable drawers. I also really need compiz. I so much wish I could get rid of that delay

What I did was to create my own menu to use a drawer.
So if you right-click Applications -> Edit Menus you can add a folder there and add the applications you want and arrange it as you like.
Then right-click the panel and Add to Panel and add an Application Launcher, then choose the folder you just created. Finally. you could assign the drawer icon to that folder so that it looks as similar as possible to the real useless drawer.

---

### Post by odyniec on 2010-09-16
I worked around this irritating little bug by hardcoding the drawer animation time to 0 in gnome-panel sources, as per the attached patch. It's a hacky workaround and not a proper solution, but if the problem is as annoying to you as it was to me, then go ahead and try it.

How to recompile gnome-panel with the patch (Ubuntu 10.04, gnome-panel 2.30.2):

```
sudo apt-get build-dep gnome-panel
apt-get source gnome-panel
cd gnome-panel-2.30.2
patch -p1 < gnome-panel.drawer.patch
cd ..
apt-get source --compile gnome-panel
```

This will produce a .deb package -- install it, and enjoy the instantly-opening drawers.

---

### Post by MaxVK on 2010-09-16
I ended up with the 'file-browser-applet'.

Its not a drawer and instead allows you to create additional menus (which was kind of the objective in the first place!)

The menus are simply folders with documents or shortcuts in them. Its working well for me at the moment.

---

### Post by miststlkr on 2010-11-14
I know this thread is older than old, but I came across it while looking for a solution tot he same problem.  I ended up setting up a new menu under Applications, then adding that menu to the panels where I wanted it.

Right click on Applications and click on "Edit Menus".  This will give you a "Main Menu" popup.  In the popup, click the first option on the far right: "New Menu".  Fill in the Name and Comment and click on the folder icon if you would like to change the icon.  When you are done, click OK.  In my case, I wanted an easy way to organize/access my remote connections, so I named it accordingly and gave it the Humanity icon for vinagre, just because I like their icon.  Now in the left panel of your popup you will see your new menu, all non-bold and italicized because there is nothing in it to display.  Click on it [in the left panel, not the right] and you will get a blank panel on the right.  Click the "New Item" button on the far right and add in the info for your launcher.  Repeat this step for each item you want in new useful drawer.  In my case, I threw in a couple of FTP launchers, a few VNC launchers and an RDP launcher or two.   Now on the panel you want a useful drawer, right click and click on "Add to Panel..."  then click on the second option "Application Launcher...".  Click "Forward" then find the menu you just created.  Click it once and "Add".  

This seems to work wonderfully for me so far.  You may also want to bury your new menu somewhere so it doesn't get in the way of the main menu.  Unfortunately, it does have to visible using this method, I had tried to make the menu but hide it on the main menu, but it didn't like that and I ended up with an empty drawer.


So I hope this can help someone out, cheers to Lunatico for the answer!

---

### Post by compu73rg33k on 2010-11-14
> **MaxVK said:**
> I ended up with the 'file-browser-applet'.

Its not a drawer and instead allows you to create additional menus (which was kind of the objective in the first place!)

The menus are simply folders with documents or shortcuts in them. Its working well for me at the moment.
I installed this applet and I'm incredibly happy with it. Super awesome.

Thanks to others who posted other solution(s) as well. :) This thread will live a long time hehe.

---

### Post by miststlkr on 2010-11-14
Certainly until they fix the drawer delay or make it user-variable, that's for sure :-P

[edit]  You may want to make the thread [SOLVED] though, so people realize that it holds the/a solution... [/edit]

---

