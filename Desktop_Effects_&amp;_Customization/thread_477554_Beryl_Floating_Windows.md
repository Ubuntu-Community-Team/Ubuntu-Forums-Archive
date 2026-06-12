---
title: "Beryl Floating Windows?"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by JonE8 on 2007-06-18
Hi All 

I'm new to Ubuntu and finding it great I haven't booted into Windows for over a week now and can't see my self doing so for a while.

I've got Beryl up and running and still sit and stare in amazement at the 3D cube but after looking round at screen shots would like to have the windows floating off the cube like this [http://customisinglife.files.wordpress.com/2007/01/beryl-3d-desktop.jpg](http://customisinglife.files.wordpress.com/2007/01/beryl-3d-desktop.jpg) I have searched Google,Wiki and several forums but couldn't seem to find anything. Any help would be much appreciated.

Cheers

Jon

---

### Post by andrewsomething on 2007-06-18
In Beryl Setting Manager, go to Visual Effects > 3D Effects and play around with the setting there. You can see mine in the screen shot.

---

### Post by JonE8 on 2007-06-18
Cheers Andrew I have tried that but still don't have the floating windows is there anything else  I need to enable or change.

Jon

---

### Post by JonE8 on 2007-06-18
Do I need to use a keyboard shortcut to make the windows float or should they be floating when I start the cube.

Cheers

Jon

---

### Post by adewale on 2007-06-18
plz i love it but i also couldn't get it also

---

### Post by TnTSCS on 2007-06-18
Beryl Settings Manager > Visual Effects > 3D Effects

Make sure 3D Effects is "checked" and then adjust the "space between windows" to your desire.. I have mine set to 0.0500

Play around with the others settings too... lose yourself in the settings area and you'll find TONS of options to customize your desktop experience

:)

---

### Post by JonE8 on 2007-06-19
Still can't get it to work 3D effects are enabled and I have played around with the settings but still no joy.

---

### Post by timcredible on 2007-06-19
the open windows that 'move away from the desktop while turning' is activated by clicking on Visual Effects -> and checking the box marked '3D Effects', just like the other posters said.  then to activate the cube, put your mouse over the desktop without a window, hold down the scroll wheel of your mouse and move the mouse around to spin the cube.  if no scroll wheel mouse, hold down alt-ctrl and the left mouse button and move the mouse.  if it doesn't work, then i would say your graphics card and/or beryl isn't setup quite right.

---

### Post by JonE8 on 2007-06-19
Here is a screen shot of my settings can you see anything wrong? I can move the cube it is just the floating windows I cannot seem to get.

---

### Post by orb9220 on 2007-06-19
Goto Visual Effects>3D Effects> and the** Space between windows**.
and also make sure** Enable window depth** is enabled down from **Space between windows**

---

### Post by JonE8 on 2007-06-19
I think I will give up as the screen shot shows I have those settings enabled and still no luck.

Thanks Anyway

Jon

---

### Post by Lightcap on 2007-06-19
Don't give up man, I don't think you disabled anything too drastic.  and one guy here already had it.  Go to beryl manager / visual effects/ make sure the 3D box is checked and under that box increase the space between windows slider to around 0.2000.  Thats it  I have checked and unchecked enable window depth a couple of times but it didn't seem to change anything.
Keep on keeping on though I have been playing around with this baby for like a week and just keep finding incredible things.

---

### Post by gigaferz on 2007-06-19
dont feel bad, for x reason my beryl doesnt show a skydome, or a custom image on the lower cap, everything else looks fine....

---

### Post by orb9220 on 2007-06-19
Had this problem had to make sure they were .png format and for skydome to make sure they are in 1024x1024,2048x1024,4096x1024 in dimensions.

jpegs are not supported.

---

### Post by JonE8 on 2007-06-20
I think it is just one of those things thats not going to work in Beryl for me. I might try reinstaling Beryl and see if that works.

Cheers

---

### Post by gigaferz on 2007-06-21
ok, ill give it a try,,,

whats up with fixing the windows border (minimize,max,close)?
either  i have to enable desktop effects in system preferences, or do a metacity replace in terminal,

I do not have emerald or anything else but beryl by itself.

Does anybody knows a solution to this "bug"?

---

### Post by dan1_m1 on 2007-12-17
Hi I&#8217;m new in Linux 
But I manage to install it and to make it work however I don&#8217;t know how enable the floating windows effect. If someone knows how to enable it in Compiz-Fusion please share that knowledge whit me and the rest of new Ubuntu lowers :-) .    
Thank you very much.

---

### Post by ronmarley1 on 2007-12-17
> **dan1_m1 said:**
> Hi I&#8217;m new in Linux 
But I manage to install it and to make it work however I don&#8217;t know how enable the floating windows effect. If someone knows how to enable it in Compiz-Fusion please share that knowledge whit me and the rest of new Ubuntu lowers :-) .    
Thank you very much.

A few misc. notes...
One, welcome to Ubuntu!
Two, this is an old thread, so you are probably better off making a new post and asking your question.  This thread discusses Beryl, which is no longer being developed.  Beryl re-merged with Compiz and became Compiz-Fusion.
Three, 3D windows is not in the current version of Compiz-Fusion.  I believe it's being re-written.  However, I've read where folks have compiled the plug-in on their own and got it to work.  You should be able to find how-to's for 3D Windows by searching this forum.

---

### Post by Ice_cone on 2007-12-17
```
#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```
I found this code somewhere in this forum and it works for me.
After running it, go to the compiz fusion settings and enable 3D windows plugin

---

### Post by dan1_m1 on 2007-12-17
Thank you very much you are extraordinary to answer me so fast, thank you. I’ll try that to see if it works for me to and if not I’ll make some more researches on this theme. Thanks again.
:)

---

### Post by dan1_m1 on 2007-12-17
guys I need help again
I did the script above, I downloaded and installed all the files needed for the plugin, I even downloaded the 3d.tar.gz but when i type the command tar -xvvzf '3d.tar.gz' i receive the following error

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed form previous errors 

and nothing happens any more 
Please help me with some ideas
Thanks  :)

---

