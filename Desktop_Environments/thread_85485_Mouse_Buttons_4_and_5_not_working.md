---
title: "Mouse Buttons 4 and 5 not working"
date: 2005-11-02
forum: Desktop Environments
---

### Post by kalarr on 2005-11-02
This is a weird one and I'm not really sure how to describe it.

My Father has an optical mouse with 5 buttons. 3 across the top (including the wheel) and then one on either side of the mouse. In Mandrake 10.1 before I switched him to Breezy, he had th button on the left side of his mouse (thumb side) set to go "back" in the browser (Firefox and Netscape 7.x) and file manager (Konqueror on Mandrake.) The button on the right side of the mouse, the 'pinky' button, was set to go forward in the same instances.

Now in Breezy (Ubuntu Gnome, not Kubuntu KDE) this doesn't happen. In fact, the buttons on the side of the mouse are dead and don't work at all.

I thought it might be the driver. Its currently set at ExplorerPS/2. This is not a Microsoft mouse but a generic brand from the local version of a Radioshack store. In every other way the mouse works fine. However, my father is stuck in his ways and wants this to work in Breezy as well.

Ironically, after I had done the migration from Mandrake to Breezy, I waited 2 days and asked him what problems he was having. This is the only problem he could give me, but its also the one thats frustrating him the most. ;-)

Any ideas folks? This one has stumped me. I didn't think about this before I took Mandrake off his computer, so I have no idea how it was done there. I don't use KDE at all, and am not familiar enough with it to know if this is a feature of the KDE mouse settings or not.

I'd really appreciate the help people. :-)

If you'd like to see the mouse details, they're available at

[http://www.dse.co.nz/cgi-bin/dse.storefront/43694c3f018aaf94273fc0a87f990723/Product/View/XH1893](http://www.dse.co.nz/cgi-bin/dse.storefront/43694c3f018aaf94273fc0a87f990723/Product/View/XH1893)

---

### Post by iH8forcedRegistration on 2005-11-02
I had the same problem early on in my still-not-over mouse configuration ordeal.

Open up a terminal and type 'xev'

it should bring up a white window with a black box in it. If you move the mouse over that window, it'll print a whole bunch of text in the terminal about the motion events. Flip the mouse over (so it's no longer sending motion events) and start pressing buttons, turning wheels, etcetera. You should be able to figure out what button number is being associated with what physical action on the mouse.

Once you've done that, close xev, go back to the terminal, and type this:
```
xmodmap -pp
```

It'll show you a table of all the button mappings the computer is using. On my machine, there's 12. Then, you'll want to type something similar to
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10 11 12"
```

What you're really doing there is filling in the left column of the table it displayed eariler, so instead of having them in sequence like that, shuffle them around so that whatever the 'back' button was will be the 6th thing, and the 'forward' button will be the 7th.

I hope that made sense.

---

### Post by mxyzptlk on 2005-11-02
try this

dpkg-reconfigure xserver-xorg

then you will get to the mouse options and check for the matches of your device

hope it helps

---

