---
title: "(Macbuntu) fire burning effect not showing up in compiz config"
date: 2012-03-23
forum: Desktop Environments
---

### Post by razedafear on 2012-03-23
Hi 

I have installed Macbuntu 10.04 transformation for my ubuntu 10.04. 
However when i try to include the fire burning effect for closing windows, that option is not present in the pool of options in animations. Only fade and magic lamp options are there. 
Attaching a screenshot of my compiz manager. 
Plz help

---

### Post by razedafear on 2012-03-23
> **razedafear said:**
> Hi 

I have installed Macbuntu 10.04 transformation for my ubuntu 10.04. 
However when i try to include the fire burning effect for closing windows, that option is not present in the pool of options in animations. Only fade and magic lamp options are there. 
Attaching a screenshot of my compiz manager. 
Plz help
sorry, tried to attach the screenshot but seems like it does not show up... newbie :)

---

### Post by stinkeye on 2012-03-23
Been a while since I used 10.04 but I think you need to install **compiz-fusion-plugins-extra**
Terminal command to install...
```
sudo apt-get install compiz-fusion-plugins-extra
```
and then enable the **Animation Add-ons** plugin in ccsm.
May have to close and restart ccsm for the burn effect to 
show up in the **Animations** plugin.

---

### Post by razedafear on 2012-03-24
> **stinkeye said:**
> Been a while since I used 10.04 but I think you need to install **compiz-fusion-plugins-extra**
Terminal command to install...
```
sudo apt-get install compiz-fusion-plugins-extra
```
and then enable the **Animation Add-ons** plugin in ccsm.
May have to close and restart ccsm for the burn effect to 
show up in the **Animations** plugin.

Ran the command but looks like its already installed:

OUTPUT - 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-fusion-plugins-extra is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 382 not upgrade

---

### Post by stinkeye on 2012-03-24
...and the animation add-ons plugin is enabled in ccsm.

---

### Post by razedafear on 2012-03-24
no is was not enabled. I checked the animation option and now have the burn option but i think i need to provide some values in the fields when i click on "new" and select the burn option.

---

### Post by stinkeye on 2012-03-24
> **razedafear said:**
> no is was not enabled. I checked the animation option and now have the burn option but i think i need to provide some values in the fields when i click on "new" and select the burn option.
This is the default window match setting for "close animation" on my 11.10 install.
```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver) & !(name=gnome-screenshot)
```

---

### Post by razedafear on 2012-03-24
> **stinkeye said:**
> This is the default window match setting for "close animation" on my 11.10 install.
```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver) & !(name=gnome-screenshot)
```

yeah..bt what to select in the two options?

---

### Post by stinkeye on 2012-03-24
You can choose windows by clicking on the button to the right of
window match.
Choose the Type.
Then hit the grab window button to click on a window with the cross-hair cursor.

or
Just copy and paste the code in my previous post to the the window match box and
adjust the duration to around 300 or more.

The options box is just for overriding the default burn settings in the **Animations Add-on** plugin.
eg If you wanted the burn effect to be upwards when opening a window
you put this into the options box for the "Open Animation" 
```
fire_direction=6
```

So the close animation will use the default down direction while
the open animation will use an up direction.

Play around with it. If you mess up , just hit the default button.

---

### Post by razedafear on 2012-03-25
thanks..dis looks gud ..will try dis and let u knw.. \m/

---

### Post by stinkeye on 2012-03-25
> **razedafear said:**
> thanks..dis looks gud ..will try dis and let u knw.. \m/
Too hard to write in proper english?

---

### Post by razedafear on 2012-03-26
> **stinkeye said:**
> Too hard to write in proper english?

sorry for being lazy..too much into chat stuff.. Good news.. i finally got the burn effect.. awesome :) thanks a bunch. well this would sound too lame but is there something like this in windows??

---

### Post by stinkeye on 2012-03-26
> **razedafear said:**
> sorry for being lazy..too much into chat stuff.. Good news.. i finally got the burn effect.. awesome :) thanks a bunch. well this would sound too lame but is there something like this in windows??
No idea,sorry.
I haven't used windows for about 4 years.
:tongue:

---

### Post by razedafear on 2012-03-26
i switched to ubuntu a year back..and love the experience..just wish that ubuntu gets more supportive on the user end software..from CUI to more GUI..

---

### Post by stinkeye on 2012-03-26
> **razedafear said:**
> i switched to ubuntu a year back..and love the experience..just wish that ubuntu gets more supportive on the user end software..from CUI to more GUI..
It can seem a bit daunting to start with but with a bit more experience you'll
find the terminal commands are the best thing about Linux.
....and this is not from a programmers or developers perspective.
I knew zilch about this, and was just your typical windows user.
Through reading and getting help through these forums, I've learnt how to
use the terminal effectively and write simple bash scripts.

---

### Post by razedafear on 2012-03-27
thats good. I am getting to know it slowly. Although my probook4530s win7x64 has been giving me a tough time with graphics, vague touchpad detection, slow wifi :(. Still needs improvement though..

---

