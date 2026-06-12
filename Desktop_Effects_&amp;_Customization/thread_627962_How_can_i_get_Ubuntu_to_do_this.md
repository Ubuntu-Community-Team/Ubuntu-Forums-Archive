---
title: "How can i get Ubuntu to do this"
date: 2007-11-30
forum: Desktop Effects &amp; Customization
---

### Post by Millerchamp on 2007-11-30
I want my Ubuntu to do this kinda of thing but i don't know how to make it do that heres a video of what i want it to do.
[http://www.youtube.com/watch?v=E4Fbk52Mk1w&feature=related](http://www.youtube.com/watch?v=E4Fbk52Mk1w&feature=related)
every effect in that video i would like to do on mine can any one help me?

Thank you

---

### Post by fragos on 2007-11-30
System-> Preferences-> Advanced Desktop Effects.  You will need a video card that support 3D rendering like those from Nvidia.

---

### Post by geirha on 2007-11-30
[https://help.ubuntu.com/7.10/desktop-effects/C/compiz-configure.html](https://help.ubuntu.com/7.10/desktop-effects/C/compiz-configure.html)
and
[https://help.ubuntu.com/7.10/desktop-effects/C/compiz-configure-advanced.html](https://help.ubuntu.com/7.10/desktop-effects/C/compiz-configure-advanced.html)

---

### Post by SunnyRabbiera on 2007-11-30
> **fragos said:**
> System-> Preferences-> Advanced Desktop Effects.  You will need a video card that support 3D rendering like those from Nvidia.

though if you have a generic intel one like me it will also do.

---

### Post by Millerchamp on 2007-11-30
Okay thank you for all the help and i got the stuff working now how do i get the 3D box thing?

---

### Post by -grubby on 2007-11-30
> **Millerchamp said:**
> Okay thank you for all the help and i got the stuff working now how do i get the 3D box thing?

go to the advanced desktop **settings**, go to general general options go to desktop size and change the horizontal virtual size to 4
(about "settings", it's the same as effects, sorry)

---

### Post by Millerchamp on 2007-11-30
> **nathangrubb said:**
> go to the advanced desktop settings, go to general general options go to desktop size and change the horizontal virtual size to 4

there is no advanced desktop settings

---

### Post by jken146 on 2007-11-30
```
sudo apt-get install compizconfig-settings-manager
```

This installs Advanced Desktop Settings.

---

### Post by Millerchamp on 2007-11-30
> **jken146 said:**
> ```
sudo apt-get install compizconfig-settings-manager
```

This installs Advanced Desktop Settings.


okay i entered that into the terminal and this is what it said



Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

---

### Post by -grubby on 2007-11-30
> **Millerchamp said:**
> okay i entered that into the terminal and this is what it said



Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

which Ubuntu version are you using?

---

### Post by Millerchamp on 2007-11-30
> **nathangrubb said:**
> which Ubuntu version are you using?


7.10 gusty

---

### Post by -grubby on 2007-11-30
is system>preferences> advanced desktop effect settings there? if it is then do what I said already)

---

### Post by Millerchamp on 2007-11-30
> **nathangrubb said:**
> is system>preferences> advanced desktop effect settings there? if it is then do what I said already)

Nope its not there

---

### Post by -grubby on 2007-11-30
> **Millerchamp said:**
> Nope its not there

open synaptic (under system>administration>synaptic) and search for "compiz", when you get there  checkmark compizconfig-settings-manager and click "apply"

---

### Post by Millerchamp on 2007-11-30
> **nathangrubb said:**
> open synaptic (under system>administration>synaptic) and search for "compiz", when you get there  checkmark compizconfig-settings-manager and click "apply"

it not there and it say all the compiz things are installed

---

### Post by oldos2er on 2007-11-30
Are all your repositories enabled?

---

### Post by sandysandy on 2007-11-30
> **Millerchamp said:**
> it not there and it say all the compiz things are installed

Hi

i also [COLOR="Blue"]do not have[/COLOR] the advanced desktop manager under [COLOR="Blue"]system>preferences> advanced desktop effect[/COLOR].

Compiz is already installed.

regards

---

### Post by -grubby on 2007-11-30
> **sandysandy said:**
> Hi

i also [COLOR="Blue"]do not have[/COLOR] the advanced desktop manager under [COLOR="Blue"]system>preferences> advanced desktop effect[/COLOR].

Compiz is already installed.

regards

have you tried installing from the terminal (```
sudo apt-get install compizconfig-settings-manager
```)

---

### Post by fragos on 2007-11-30
> **Millerchamp said:**
> there is no advanced desktop settings

Advanced Desktop Settings started with Gutsy 7.10.

---

### Post by sandysandy on 2007-11-30
> **nathangrubb said:**
> have you tried installing from the terminal (```
sudo apt-get install compizconfig-settings-manager
```)

thanks. the advanced desktop effect setting got installed. how do i use it. i have opened the CompizConfig setting manager in which some of the effects are selected. how do i get them to display on the desktop. I wanted to display the desktop cube.

regards

---

### Post by Millerchamp on 2007-12-01
Ok i got the compizconfig-setting-manager how do i use it?

---

### Post by lightstream on 2007-12-01
Just enable the features you want by making sure the tick appears in the checkbox. To tweak settings, click on the item's icon and, to quote another post, dink about in there.

Here's a useful run-down of the default keyboard/mouse shortcuts for using the various features: [http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/]("http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/")

---

### Post by Millerchamp on 2007-12-01
> **lightstream said:**
> Just enable the features you want by making sure the tick appears in the checkbox. To tweak settings, click on the item's icon and, to quote another post, dink about in there.

Here's a useful run-down of the default keyboard/mouse shortcuts for using the various features: [http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/]("http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/")

Okay thank you but what is the "super" key?

---

### Post by geirha on 2007-12-01
> **Millerchamp said:**
> Okay thank you but what is the "super" key? It should be the windows key (by default), the one between CTRL and ALT. It can be configured in System -> Preferences -> Keyboard.

---

### Post by Millerchamp on 2007-12-01
Okay now how do i get the Apple "Mac" thing at the bottom of the screen?

---

### Post by lightstream on 2007-12-02
> **Millerchamp said:**
> Okay now how do i get the Apple "Mac" thing at the bottom of the screen?

Buy an Apple Mac.

Ok seriously, what 'Apple Mac' thing?

---

### Post by geirha on 2007-12-02
> **lightstream said:**
> Buy an Apple Mac.

Ok seriously, what 'Apple Mac' thing?

I think he wants a gdesklets launchbar or kiba-dock. I found a howto for the kiba-dock here: [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

