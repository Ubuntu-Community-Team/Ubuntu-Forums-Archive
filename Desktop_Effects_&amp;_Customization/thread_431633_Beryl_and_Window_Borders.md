---
title: "Beryl and Window Borders"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by handyguy33 on 2007-05-03
OK, here's what I broke today. I tried to get Beryl and Gdesklets to work together (all I really had to do was turn off wobbly windows) and to get them to start at boot. Well I got as far as running them simultaneously, and got Beryl to start at boot. When I restarted to test the start at boot thing, I got a terminal window on my desktop apparently running beryl (all the effects working) and I could even turn on Gdesklets and everything was happy and good. Then I closed the terminal window and BLAM! - no more windows borders. I've tried several fixes from the forums. I now have my windows borders, Beryl and Gdesklets all working, but I have to keep the terminal open or I lose my borders. How do I fix this and how do I get rid of that terminal at boot. Please make your answer step-by-step because I'm not nearly as intelligent as I sound (an intelligent person wouldn't try to run Beryl _and_ Gdesklets in the first place, lol).

---

### Post by GrueTamer on 2007-05-03
Beryl is very unstable for most people, so it just may be that until they fix some of the glitches, you can't run them both.  There are a lot of people that can't run beryl because of weird technical glitches, so it's not really your fault.

With that said, I think that if the solutions on the forum didn't help you, then there's not much else you can do, as the forum solutions looked good to me.  But I'm no beryl expert, hell, I don't even run beryl, I'm a compiz person, which I only run to show off my desktop, so I really don't know what to try.  But I'm betting it's just beryl freaking out on you.

---

### Post by starcraft.man on 2007-05-03
Did you set beryl and emerald to boot with the Sessions menu? If so, the terminal really shouldn't be openning up...

System > Preferences > Sessions

Start up tab is first, both these should be listed there.
```
beryl-manager
emerald --replace
```

Is that whats there?

Edit: Hey, Grue, Beryl is stable enough since 2.0, I leave it on all day long and I rarely crash. >.>

---

### Post by handyguy33 on 2007-05-03
OOO, I almost forgot. Here's the contents of that persistant terminal window:

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
Checking maximum texture size                   : passed (2046x2046)

Reloading options

That's it. The options are permanently reloading? Please help me. I'm so close to the perfect desktop environment that I can taste it.

---

### Post by starcraft.man on 2007-05-03
Thats very odd, you shouldn't be getting that........

Can you please open up your sessions menu like above and tell me if you have beryl-manager and emerald --replace in the list?

If both are there, lets try something as a diagnostic... Push the add button, and type "beryl" into the terminal line. Then just reboot. Tell me if it comes up again.

---

### Post by handyguy33 on 2007-05-03
beryl-manager and emerald --replace are both there (I had to add emerald --replace) and I added beryl. Now, Beryl manager starts at boot, but not Beryl. The terminal window shows up at boot but it's blank, and my homepage in Firefox doesn't come up. I don't even know if that's related, but it's odd behavior, so I'll mention it. Instead of my homepage address, this is in the address bar: [http://www.%u.com/](http://www.%u.com/)

i'll be here all day, so drop me a line whenever you think of something.

---

### Post by handyguy33 on 2007-05-03
i think i've got it working. a few tweaks and several reboots later and everything is on and no problems. my home page is set to deviantart, but when i open firefox i still get the above in the address bar. i can live with that but if anyone knows how to fix it, i would appreciate it

---

### Post by aeiah on 2007-05-04
for your firefox problem, you could try right clicking your ubuntu menu and selecting 'edit menus'

from there find your firefox shortcut, right click it and select properties

the command should read *firefox %u*. im guessing thats why your homepage has the %u thing in it. try deleting the %u part and see if it makes a difference (or if your command reads something different, enter *firefox %u*)

---

