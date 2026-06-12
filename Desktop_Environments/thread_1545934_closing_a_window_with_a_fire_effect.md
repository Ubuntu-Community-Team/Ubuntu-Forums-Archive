---
title: "closing a window with a fire effect"
date: 2010-08-04
forum: Desktop Environments
---

### Post by mesaphlin on 2010-08-04
Hello everyone,

I am new to ubuntu and compiz - so far so good on the compiz effects but I couldn't figure out the fire effect when you close a window in compiz.

I looked everything in the compiz fusion menu but still couldn't find that effect out.. I have every plug-ins I believe in the compiz)

Could you help me please how I could do that effect...?

Thanks in advance...

;)

---

### Post by tgalati4 on 2010-08-04
Open a terminal:

apt-cache search compiz

I think you need:

compiz-fusion-plugins-extra - Collection of extra plugins from OpenCompositing for Compiz

sudo apt-get install compiz-fusion-plugins-extra

---

### Post by mesaphlin on 2010-08-04
> **tgalati4 said:**
> Open a terminal:

apt-cache search compiz

I think you need:

compiz-fusion-plugins-extra - Collection of extra plugins from OpenCompositing for Compiz

sudo apt-get install compiz-fusion-plugins-extra

it spitted out...

pil@Pil:~$ sudo apt-get install compiz-fusion-plugins-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-fusion-plugins-extra is already the newest version.
The following packages were automatically installed and are no longer required:
  librrd4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pil@Pil:~$


But still I cannot find it in the compiz-fusion settings...

Where is it exactly?

:(

---

### Post by howefield on 2010-08-04
Enable the effect in the Animations Add-on plugin.

---

### Post by mesaphlin on 2010-08-04
> **howefield said:**
> Enable the effect in the Animations Add-on plugin.

After I enabled the Animations add-on plug-in, there are many sections on top of the window like Open animations, close animation, minimize animation, etc...

I searched them but there is no fire plug-in effect...

Besides, in the animation selection, there is the window match section which I dont know how to write the code... :(

Any help is so much appreciated...

](*,)

---

### Post by realzippy on 2010-08-04
> **mesaphlin said:**
> After I enabled the Animations add-on plug-in, there are many sections on top of the window like Open animations, close animation, minimize animation, etc...

I searched them but there is no fire plug-in effect...

Besides, in the animation selection, there is the window match section which I dont know how to write the code... :(

Any help is so much appreciated...

](*,)

in the *animation selection* you are right("window match section")You do not need any code,just right-click on the first line,choose *edit*,then a window opens
where you can select the burn option (or any other) in the first line.

---

### Post by howefield on 2010-08-04
After enabling the Animations Add-ons plugin, go into Animations and select the tab that you wish to enable with the Burn Effect, let's say you want to close a window with the burn effect...

Select the Close Animation tab and highlight the first line in Animation Selection window, then press the edit button, then select Burn from the Close Effect drop down menu, and close your way back out.

---

### Post by mesaphlin on 2010-08-04
Thank you all!!!...

I have the burn effect now...

But I did a stupid thing which is I deleted all the examples in the animation selection and created new examples like burn or fade .. etc... But now my examples have no window match codes...

Where could I get those window match codes or if I leave them blank - is that okay?

Thanks so much in advance...

:?

---

### Post by realzippy on 2010-08-04
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)


(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)


(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd) 


are my vanilla codes.

---

### Post by howefield on 2010-08-04
> **mesaphlin said:**
> Where could I get those window match codes

Here are my default codes for that option.

---

### Post by realzippy on 2010-08-04
Mine are better.

:D

---

### Post by mesaphlin on 2010-08-04
Thank you so much everyone...

The last question is that how can I understand those window match stuff in order to write my own instead of just copying and pasting?

And the same question also applies to the .conkyrc file too... I want to go deeper in the code in order to write my own but I don't know where to start...

:)

---

### Post by howefield on 2010-08-04
> **realzippy said:**
> Mine are better.

Took you a while to sort out your copy/paste ability :-)

---

### Post by mesaphlin on 2010-08-04
> **howefield said:**
> Took you a while to sort out your copy/paste ability :-)


Should I start to learn The C Language ?

:p

---

### Post by howefield on 2010-08-04
> **mesaphlin said:**
> And the same question also applies to the .conkyrc file too... I want to go deeper in the code in order to write my own but I don't know where to start...

Plenty reading in these ubuntuforum threads to start you off with conky, but if you have specific questions, probably best to start a new thread seeing as it is a different topic to this one.

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
[http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)

---

### Post by realzippy on 2010-08-04
> **howefield said:**
> Took you a while to sort out your copy/paste ability :-)

not as long as your copy & paste inability :p

---

### Post by howefield on 2010-08-04
> **realzippy said:**
> not as long as your copy & paste inability :p

Don't follow you, you'll need to explain.

---

### Post by realzippy on 2010-08-04
> **howefield said:**
> Don't follow you, you'll need to explain.

OFFTOPIC:

Maybe due to my bad English,translated "sort out" to kind of "realize","recognize" ..I thought you were joking like:

"Took you a while to realize your copy/paste ability"

---

