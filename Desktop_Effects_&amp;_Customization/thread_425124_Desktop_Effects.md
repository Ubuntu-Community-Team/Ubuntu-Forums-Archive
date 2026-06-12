---
title: "Desktop Effects"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by mandela on 2007-04-27
I'd appreciate if anyone could give me a detailed tutorial on how to create and make my desktop look stunning. Thanks.

---

### Post by Aetherius on 2007-04-27
are you running feisty? (k)(x)ubuntu?

---

### Post by mandela on 2007-04-27
> **Aetherius said:**
> are you running feisty? (k)(x)ubuntu?
both...I mean Fiesty and Kubuntu!

---

### Post by hyperair on 2007-04-28
First, try enabling the desktop effects from system->preferences->desktop effects, and follow any instructions if given. That will set up your X server with the appropriate drivers needed. If you're satisfied with what you have there, then it's fine. Otherwise, install Beryl and use it instead:

```
sudo apt-get install beryl emerald
```
and when it's done, type:
```
beryl-manager
``` in your run dialog to start Beryl.

The Beryl icon will appear at your system tray, and from there you can access Emerald Theme Manager and Beryl Settings Manager by right clicking it.

---

### Post by mandela on 2007-04-28
Thankx..I'd enabled the desktop effects earlier and it was ok but on install beryl..it gave this message:
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: pixmap 0x3400254 can't be bound to texture
beryl: Couldn't bind thumb pixmap to texture


Is there anything I need to do or did not do correctly plus my other work-desk disappeared as well as the menu bar in my browser

---

### Post by hyperair on 2007-04-28
Are you sure you mean menu-bar? That can't be right, beccause Beryl doesn't touch the menubar, last I checked. Perhaps you meant window title? After that error does Beryl continue to work or crash immediately?

---

### Post by mandela on 2007-04-28
> **hyperair said:**
> Are you sure you mean menu-bar? That can't be right, beccause Beryl doesn't touch the menubar, last I checked. Perhaps you meant window title? After that error does Beryl continue to work or crash immediately?

By menu bar, I meant where you have the "File...Edit..View..." thing..After the error, I just closed the terminal. I log out and in again. It reappeared but definitely not the desired effects. Have you any beryl-settings that I can import in order to help with my learning curve. I'd appreciate. Thanx.

---

### Post by hyperair on 2007-04-28
Here you go: Import it using the small button ("Import") at the bottom of the Beryl Settings Manager.

Good luck with it. :)

---

### Post by mandela on 2007-04-28
Thanks mate...I will give u a feed back....

---

### Post by mandela on 2007-05-07
could anyone pls tell me what combination of keys start the cube desktop effects..not the ctr-alt/right/left ...its not working for me.

---

### Post by hyperair on 2007-05-08
Are you using Compiz or Beryl? If you are using Beryl then the file you downloaded and imported into Beryl Settings should allow you to use the mouse scroll near screen edges, and the ctrl+alt+left and ctrl+alt+right keys.

If you are using Compiz and that doesn't work, open your configuration editor (gconf-editor in the run dialog) and navigate to /apps/compiz/general/screen0. Change hsize to 4, and change number_of_desktops to 1.

---

### Post by davo8 on 2007-05-08
ctrl+alt+middle click

---

### Post by iamah on 2007-05-08
Desktop Effects its cool but it removes the window bar from all applications... the result its ugly and you cant change windows size... This also happened to me before when I manually installed beryl...

---

### Post by hyperair on 2007-05-08
It happens because of misconfiguration of your xorg.conf. You must have this line in your screen section:

```
Option "AddARGBGLXVisuals" "True"
```

---

### Post by mandela on 2007-05-10
Thankx hyper..its working great..so far so good....I'm using Beryl and Its so so beautiful...I'm loving it.I learn't there is also another way to get a cube (not with beryl/compiz)..thru the System->preference->Desktop Effects->enable workspace on desktop thing..you know what I'm talking about?

---

### Post by hyperair on 2007-05-10
Ah but of course! That'll be the Compiz that comes with the Ubuntu Feisty Fawn desktop edition. Well, brace yourself for a lil history lesson:

At the beginning, there was Compiz. Then one of the Compiz developers (QuinnStorm) decided to create a window decorator, and to spiffy things up a bit, creating a new build called Compiz-Quinn. It works with CGWD, which is the window decorator (the stuff that is in charge of the pretty window borders you see. After a while, they forked (or maybe they did before Compiz-Quinn came about, I'm not really sure about that part). Compiz-Quinn became Beryl. CGWD became Emerald.

From what I gather online, Compiz is the more stable of the lot, whereas Beryl utilizes hacks, allowing it to have better effects at the expense of stability. I, however have not seen this so called instability-it works fine on my computer. Compiz has no window decorator other than the gnome window decorator which follows the metacity theme. Personally I prefer Emerald as it's more customizable and whatnot.

Also, Compiz and Beryl have merged once again. Compiz having the stable engine, and Beryl having the flashy effects. They are yet to decide on a new name for the merged product though, and release their first version since the merger.

---

### Post by cumanzor on 2007-05-10
Yeah, actually, Beryl forums are read-only now, and you have to go opencomp.com or something like that.

When will this *merged product* be available?

---

### Post by diverbelow on 2007-05-10
Question, I tried searching ubuntuforums for the problem my brother has-
He turned on Desktop effects on his Feisty P3 400, intel based video card, laptop and his screen went black and unable to see his desktop. He reboot, he login shows up, then his screen goes black again. Where do I need to go to in terminal to turn off Desktop effect on his profile?

Thanks in advance,

---

### Post by hyperair on 2007-05-10
That was something I never really managed to find out. >< Perhaps it's inside the ~/.bash_profile or ~/.bashrc files. Could you post them?

---

### Post by rgraves22 on 2007-05-10
> **mandela said:**
> could anyone pls tell me what combination of keys start the cube desktop effects..not the ctr-alt/right/left ...its not working for me.

You can go into the Beryl settings manager > Desktop > Desktop Cube and you can select the combonation of buttons to enable the 3d cube.. Mine is set to where I press the middle button on my mouse and move the mouse, the desktop will turn into a cube and you are free to rotate it.

---

### Post by quickwitt on 2007-05-13
Can you revert to the previous settings after an import? 

i imported your file and I am having some problems.

Thanks!

---

### Post by hyperair on 2007-05-13
Go to General->Settings, Profiles and Desktop Integration. Select <Default> and click "Load/Activate"

---

