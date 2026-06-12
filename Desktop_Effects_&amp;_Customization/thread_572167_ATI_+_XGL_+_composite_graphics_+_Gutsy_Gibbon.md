---
title: "ATI + XGL + composite graphics + Gutsy Gibbon"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by Silent Warrior on 2007-10-10
8-[

Lots of beta-software in there, eh? Well, why don't I just cut to the chase.
(Heads-up: The situation seemed to sort of change halfway through writing this. You might consider skipping to the end and use the rest as background-information. It doesn't mean I don't need help...)

I wanted to try compiz or its likes on my AMD64 and Radeon X1900-powered rig, and have gotten so far as installing XGL. Wheeey! And it seems I'm sort of in the dark from there. I have yet to find an XGL-guide for Gutsy, but I've cannibalised a guide for Feisty, and actually had some hints of success. (How's THAT for a 4-5 months' Ubuntu-n00b!)
Now, I also have a computer with a P4 (32-bit) and Radeon 9600, running Kubuntu, that I more or less use as a testbed in this matter. (What can I say? Those civil flight simulators...) I just saw a topic that suggested that my 9600... isn't a good starting point. But still, it'll all amount to sound exercise. (Following Gnome-oriented guides on a KDE-box is... exciting.) So, that sort-of-success I mentioned was thus:
After installing XGL (apt-get install xserver-xgl) and rebooting, the desktop came over rendering/running really really slow - I could follow the sort of diagonal screen-division when filling up a just-started application-window. I thought I'd try poking around with some guides, and found out that ATI/FGLRX has a habit of setting the display as something else entirely from what XGL is looking for. Some more poking, and it seems I get OpenGL output! Yaay! ... In a tiny little viewport at about 320x240 when the desktop itself maintains a comfortable 1024x768-layout (you'd better make sense of that, because that's the best explanation I can think of...). Hey, at least it ran well, with no apparent glitches or out-of-place borders.
After going back and forth between some different takes on modifications (hey, the machine still works - I'm writing from it) it did seem that XGL ran a little bit faster. Not as fast as straight X, but a fair sight faster than before - tooltip windows opened smoothly, mouse moved as it should, menus reasonably smooth. W3rd. And yet a while later, it seems I'm back in straight, normal X.

Surprise of the week: I'd appreciate some help sorting this out. If the 9600 is a no-go, the X1900 is always ready for a challenge.

```
fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.4 (2.1 Mesa 7.0.1))

```

```
fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```
*Twitch* That isn't, as they say, cool, is it? The version-strings, that is. Suspected cause: I think I have the ati-driver supplied through online repositories installed before, and I just installed ATI's more official drivers.

```
compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: Failed to load theme "ClearlooksAlternative": Failed to find a valid file for theme ClearlooksAlternative

Not initializing the Gtk-Qt theme engine

```
With this the console seems to... Uh... Wait, don't tell me I got it working?? Hm...

GAAAAH! WTF?? Wasn't I supposed to need XGL? I don't see any 3D anywhere... Heeeeeeeeelp! My computer defies the conventions of propriety!

---

### Post by Forlong on 2007-10-10
First of all: for which setup are you looking for help?

Because that makes a huge difference with these two graphics cards.

---

### Post by Silent Warrior on 2007-10-11
With all the 'funny' little tricks the other system is up to, maybe it's best to focus on the X1900-rig. If anyone has an idea of what's going on with the other one (though compiz does appear to work, as far as lack of DRI and actual compositing goes...), I'm all ears, but the X1900 sees more use.

Progress on that machine so far:
1. Installed XGL. (I've always used ATI's official drivers, so I'm not counting that. Presently on 8.40, I believe.)

This gives me a really sluggish desktop-rendering and a sort of load-screen before logging in - a black background with a cursor-like X in the center. fglrxinfo makes weird things happen... I tried -display :0 first, apparently not what I'm using. I then tried -display :1, and X restarted, just like that. Still, it seems display #1 is the way to the bells and whistles.
I have found some wiki-guides that I think I'll be able to follow, although they're not oriented towards Gutsy yet. Unless someone says otherwise reasonably soon, I'll wait for a while, then give them a try.

---

### Post by Forlong on 2007-10-11
Please post the output of ```
fglrxinfo
```

And did you do anything besides installing xserver-xgl?

---

### Post by Silent Warrior on 2007-10-11
fglrxinfo reports that it can't open display :0. And if I try to query display 1, I have so far had X subsequently restarting (crash?). Though I should get output that way. I'll just post this first, then try and see what happens and report back.

[Edit] Nope, -display :1 makes X apoplectic. ATI's CCC won't admit that the drivers are installed, either. Maybe if I dpkg-reconfigure those sods...

I'm really itching to do something to xorg.conf right about now.

---

### Post by Silent Warrior on 2007-10-13
*Bump*, or thereabouts.

I looked at my xorg.conf, and found what looked like duplicate entries for my monitor. Could that drive fglrxinfo up the wall?

---

### Post by Forlong on 2007-10-13
Yeah, do a backup of your config:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then:
```
sudo dpkg-reconfigure xserver-xorg
```
(chose ati when asked for a driver)

Afterwards, open it being root:
```
sudo gedit /etc/X11/xorg.conf
```
Change
```
        Driver          "ati"
```
to
```
        Driver          "fglrx"
```
and add
```
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```
Save. Reboot. Tell us if it worked. :)

---

### Post by Silent Warrior on 2007-10-14
Worked so-so, but then again, I didn't reboot properly, I just Ctrl+Alt+Backspaced. I thought "to hell with it" and uninstalled XGL. Otherwise a perfectly clean X.org installation and xorg.conf (it even recognised my screen, yo!). With the added bonus that I can actually run fglrxinfo as advertised!

fglrxinfo -display :0:
```
Error: unable to open display :0
```
fglrxinfo -display :1:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```
Until further word, I'll be looking through Synaptic for clues about XFree86-DRI.

(Also, on clean X, I get no garbled icons and desktop-performance is up by a fair few notches. I don't think this computer likes XGL all that much, really...)

---

### Post by undine on 2007-10-15
I have the same problem. It's not that your computer doesn't like XGL, -- it used to work fine on mine before Gutsy, -- but rather that the driver is not working proerply for whatever reason. If you were getting direct rendering, XGL would work fine for you.

---

### Post by Silent Warrior on 2007-10-16
Hm... Without XGL installed, I remember getting DRIconf to open without shouting angry things at me... With XGL, it's been 'You don't have a DRI-capable device, foo!' always. Still, considering the results I got on the other computer, the problem probably is that XGL is spiffing up the display I'm NOT using. I hope to find out.

I'll try installing XGL again later during the day and report back.

[Edit] XGL reinstalled, fglrxinfo again makes X11 kick me out. This time, though, fglrxinfo broke without adding -display :1. Maybe I've monkeyed around with DRIconf one time too many...?

[Edit 2] I've now followed this guide: [https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28Compiz%29](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28Compiz%29)
(Due to it being directed at Feisty Fawn, I had to sort of not follow many of the instructions, but the DRI-section is in, Composite extension is off, XGL is installed and giving me one slooooooooooow desktop.)

---

### Post by Silent Warrior on 2007-10-27
New day, new fglrxinfo-output:

-display :0 returns...
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6747 (8.40.4)

-display :1 can't be opened.

I saw some guide or other about this that I would have thought I followed, but maybe I haven't done so properly. Stay tuned...

Meh, all sorts of failsafe gunk in my xorg.conf...

---

