---
title: "no cube effect"
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by haZZe08 on 2007-09-23
jus downloaded compiz fusion onto fiesty. enabled the cube and other effects but they dont work. Any ideas?

---

### Post by ayenack on 2007-09-23
Not sure if you've tried this if not. ctrl_alt left mouse button to rotate cube. You know compiz is already on Feisty?

ayenack.

---

### Post by QueenN00B on 2007-09-23
Oi! This happened to me as well. It worked well until I disabled the desktop effects (by mistake) and enabled them. SInce then, I've gone through gconf-editor, changed hsize to 4 and umm..  yeh. lol I just want to see the darn cube.

---

### Post by haZZe08 on 2007-09-23
still nothing. I only have 2 work spaces, no cube even tho its on in compiz config. I know the controls to work the cube. But for some odd reason it doesnt turn it on

basically NOTHING works in compiz

---

### Post by QueenN00B on 2007-09-23
Holy moly.. I fixed it. lol I just pressed reload window manager. Weird..  -_-

---

### Post by phelixnyc on 2007-09-23
Use this tutorial [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by dynamethod on 2007-09-23
if any of you guys is running an ATI X800 XT agpx8 and got compiz-fusion working, please tell me how you got it to run, ive read almost every how-to out there, and its not working, ive tried almost every how-to with the latest ATI driver and earliers one too, no luck though :S

---

### Post by jkwarras on 2007-09-23
Same here: Cube doesn't work when I've upgrade from Compiz to Compiz Fusion.

---

### Post by Forlong on 2007-09-23
> **dynamethod said:**
> if any of you guys is running an ATI X800 XT agpx8 and got compiz-fusion working, please tell me how you got it to run, ive read almost every how-to out there, and its not working, ive tried almost every how-to with the latest ATI driver and earliers one too, no luck though :S
First of all: that's really not the right thread for this.
Then: there's nothing wrong with your graphics card.
Since you used a lot of different How-Tos I guess you just messed with your install. That's why you can't get it to work. But I can only guess, because there's really not much input. Start your own thread and we'll see what we can do for you. Or just search for an existing thread with similar symptoms (which this is not).

---

### Post by Forlong on 2007-09-23
> **jkwarras said:**
> Same here: Cube doesn't work when I've upgrade from Compiz to Compiz Fusion.
That's just because it's configured differently. See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) in the section *Getting the cube*.

---

### Post by Mujay on 2007-09-23
When I first installed compiz fusion, the cube was working.. and then it just stopped, some plugins work and other don't.. I don't know how to fix this? Someone please help. Thanks in advance =]

---

### Post by Mujay on 2007-09-23
posted two posts and don't how to delete sorry =]

---

### Post by 005david on 2007-09-23
> **phelixnyc said:**
> Use this tutorial [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

i used that and it doesn't work for me.

---

### Post by Forlong on 2007-09-23
Could you please be a *little* more specific?
And more importantly did you follow the link in the How-To to the set-up guide?

---

### Post by 005david on 2007-09-23
> **Forlong said:**
> Could you please be a *little* more specific?
And more importantly did you follow the link in the How-To to the set-up guide?

yes, i used the link, i followed the instructions exactly to the point where it says Getting the cube

Firstly, enable the following plugins (by checking the box next to them):

    * Desktop Cube - to actually use it, we might have to disable some other plugins (just follow the popup)

    * Rotate Cube - that is necessary to spin the cube

    * Viewport mouse switch (optional) - if you want to change desktops with the mousewheel

    * Cube Caps (optional) - lets you use an images on top and bottom of the cube


Secondly, we have to increase the number of the virtual desktops to 4
at General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size
(the other two options have to be left at 1)

Now we can switch desktops via [Ctrl]+[Alt]+[Left]/[Right] and spin the cube via [Ctrl]+[Alt]+[Left Mousebutton] (or via middle-click on the desktop). 

and when i do press [ctrl]+[alt]+[left] or [ctrl]+[alt]+[right]  it doesn't do anything.

---

### Post by Forlong on 2007-09-23
With more specific I meant like: is anything else working for you?
Is the cube the only thing that's not working?

In other words: are you sure Compiz is running at all?
Maybe you should post the output of
```
compiz --replace
```
in a terminal.

---

### Post by 005david on 2007-09-23
Checking for Xgl: not present. 
Blacklisted 'via' driver is in use 
aborting and using fallback: /usr/bin/metacity

---

### Post by 005david on 2007-09-23
oh, and none of the features work.  i tried wobbly windows, and everything else really.  nothing.

---

### Post by Forlong on 2007-09-23
> **005david said:**
> Blacklisted 'via' driver is in use
Your graphics card is not capable of running Compiz.

---

### Post by 005david on 2007-09-23
as i suspected, this computer sucks.

---

### Post by Mujay on 2007-09-24
hello, can someone please help me? all the other effects work except for the cube! I can't even shift from one work space to another!

---

