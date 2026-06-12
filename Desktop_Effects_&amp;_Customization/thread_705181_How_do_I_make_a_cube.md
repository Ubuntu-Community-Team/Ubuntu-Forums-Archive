---
title: "How do I make a cube?"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by the lemming on 2008-02-23
Hello

It's been a long time since I have been here but now that I have aquired a computer that will happily run Ubuntu 7.10 I have a question.  I have managed to get compiz to run and I have managed to get the cube effect to work but only sort of.

On my desktop I have two workspaces and when I press Control/Alt I only get to rotate a single 2D representation of the desktop that I am working on.  

Could somebody please tell me how I can add more workspaces and be able to create a 3D cube of all my workspaces?

Cheers

---

### Post by the lemming on 2008-02-23
I have solved how to make 4 workspaces by tinkering around.

However I do have a new question.

In a previous distro when I got the 3D cube to work all the windows on the workspace would come away in a sort of stack giving a representation of the order that they are stacked upon each other.

can the same be done in Ubuntu?

Cheers

---

### Post by Cresho on 2008-02-23
3d effect?  that plug in is not available by default in 7.10.  However, it is installable.  In the ubuntu heron 8 alpha 4, it is available by default.

you can install it but it is buggy.
[http://ubuntuforums.org/showthread.php?t=585491](http://ubuntuforums.org/showthread.php?t=585491)

---

### Post by AgentZ86 on 2008-03-15
I want the cube,

I have 7.10 fully updated, do I need more ? 

do I have to install compiz or some compiz manager ?

Is it in the add/remove section ? or synaptic ?

Please advise
Thanks

---

### Post by casalino.luca on 2008-03-15
You need to install compiz config setup manager:
sudo apt-get install ccsm

Go to System->Preferences->Advanced desktop effects settings
now you click on general options -> Desktop size (set the # of desktops = 4).
Then on the main windows of ccsm you will see cube desktop, tick it (will ask you to deactivate muraglia or whatever the english translation is, do it). Activate Rotate cube as well.
Now it should work

---

### Post by casalino.luca on 2008-03-15
sorry...compizconfig-settings-manager

sudo apt-get install compizconfig-settings-manager

:)

---

### Post by AgentZ86 on 2008-03-15
> **casalino.luca said:**
> You need to install compiz config setup manager:
sudo apt-get install ccsm

Go to System->Preferences->Advanced desktop effects settings
now you click on general options -> Desktop size (set the # of desktops = 4).
Then on the main windows of ccsm you will see cube desktop, tick it (will ask you to deactivate muraglia or whatever the english translation is, do it). Activate Rotate cube as well.
Now it should work

Coool thanks,

I actually installed it from applications/add/remove and then searched for compiz, and it was there, but I didn't realize it puts the advanced menu item in there so I did not realize I had it.

Thanks

---

### Post by AgentZ86 on 2008-03-15
I have the System/Preferences/Advanced Desktop Effects Settings ?

But when I select Cube, I don't seem to get a cube, should it happen instantly or do I have to turn on compiz or something ?

Please advise thanks

---

### Post by DXM31 on 2008-03-15
It is all in here
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)
and then some

---

### Post by AgentZ86 on 2008-03-15
Hey thanks,

works great

One thing, what is the settings for the mouse to be able to rotate the cube ? instead of selecting 1 of the 4 desktops ?

Please advise
Thanks

---

### Post by AgentZ86 on 2008-03-15
One last thing ?

How can I get a WINE program like lets say mt4 (metatrader) to run in one of the desktops, WINE programs seem to just run on their own and don't occupy any of the cube desktops ?

??

---

### Post by Zorael on 2008-03-15
> **AgentZ86 said:**
> One thing, what is the settings for the mouse to be able to rotate the cube ? instead of selecting 1 of the 4 desktops ?

There's a keybind for that in the Rotate Cube plugin. The default bind would be Ctrl+Alt+Hold left mouse button, I believe.

As for Wine programs; you want them to take up the entirety of the screen? Else you can just move the window to where you want it, then maximize if that's your wish.

---

### Post by AgentZ86 on 2008-03-16
Thanks for the tip, the ctrl+alt works perfectly this is a really nice feature, I think it's slowing my computer down a bit, but my specs are a little light for this also, 2MHZ Athalon,512MB,and 64MBvid, I am building a newer box, but perhaps I should at least put 1GB ram and 128vid might speed things up while I"m shopping for my next computer

it's not super slow it's just slower then without out it, which makes sense since there are now 4 desktops,

As far as the Wine programs go, or at least for my metatrader, it appear to take up the whole screen and I cannot really resize the main windows or move anything, I can live with it, but I was just wondering why? or how to fix

Basically once I run the metatrader it sort of runs on all desktops, and basically covers up the desktops, if I minimize the screen, it does not minimize until I restart the metatrader application, but the minimized screen is still on all desktops ?

So basically it's not the cube, problem but something to do with the way metatrader is working or Wine or something, I'll try another wine program and see how that goes to see if all my Wine stuff is doing that.

I'll post back.
Thanks

---

