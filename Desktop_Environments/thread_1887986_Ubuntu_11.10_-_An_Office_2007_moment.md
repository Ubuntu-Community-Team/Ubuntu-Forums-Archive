---
title: "Ubuntu 11.10 - An Office 2007 moment"
date: 2011-11-28
forum: Desktop Environments
---

### Post by ComicalEngineer on 2011-11-28
Not sure where to post this, or whether it will react the right people but...

I really hate the new interface. Sorry chaps but I have been running it off a live CD installation before installing and it's driving me potty.

Comments thus:

Toolbar down the left side: Great but can't customise it and the icons are too large hogging too much screen space on a smallish laptop.

New menu structure [Dash]: Can't seem to find anything that I need including the terminal window

The semi transparent dash just hogs screen space and in pretty much un-intuitive

Why has the maximise / Minimise / Close window icons moved to the left of the window? This is just plain annoying and pointless.

This release reminds me of a Micro$oft moment and is similar for me to what MS did to Office with the 2007 release when it simply annoyed all of the people who had put time into learning the old interface. If Ubuntu wants more users, this is not a good way to achieve it.

PLEASE, PLEASE, PLEASE can someone tell me in simple English how to get the classic Gnome interface back, otherwise I just won't be installing this distribution. Many thanks.

CE

---

### Post by bashishtha on 2011-11-28
You can just select  "classic gnome" option at the login screen (option button is at the right side of the user name) and enjoy simple (and even faster) and familiar interface.

---

### Post by ComicalEngineer on 2011-11-28
Thanks!

Using it off the CD doesn't give me this option but I will install it and try.

---

### Post by cybergalvez on 2011-11-28
Gnome killed the old classic look. Even gnome's attempt at a classic look in gnome3 is different from what your used to. Take a look at Mate, or give a different DE a try

---

### Post by MBybee on 2011-11-28
I also mourned the loss of Gnome 2's familiar interface. Xubuntu might be worth a shot. 

Gnome Shell is also nice - and there is even a tweak to get the classic drop down menu in the shell (like Gnome 2 had).

---

### Post by Dry Lips on 2011-11-28
> **bashishtha said:**
> You can just select  "classic gnome" option at the login screen (option button is at the right side of the user name) and enjoy simple (and even faster) and familiar interface.

No you cannot. Actually you have to install "classic gnome" before you choose this
at the login screen. You have to:
```

sudo apt-get install gnome-session-fallback
```

---

### Post by Nutria on 2011-11-28
> **ComicalEngineer said:**
> Not sure where to post this, or whether it will react the right people but...

I really hate the new interface. Sorry chaps but I have been running it off a live CD installation before installing and it's driving me potty.

Completely agree!

[snip]

> otherwise I just won't be installing this distribution.

Who says you have to?  I'm happily running a heavily-PPAed (to get the latest versions of the drivers and apps I care about) Maverick Meerkat 10.10 with a 3.0.6 kernel plucked from Oneiric and installed the same thing on my wife+kids' PC.

Maybe in a couple of years the GNOME & Unity developers will realize that all the world's not a tablet, but until then it's GNOME 2.32 for me!

(Yes, I tried xbuntu but it's too different from Windows which I use at work.)

---

### Post by MBybee on 2011-11-29
Gnome shell with the menus works pretty well though

[http://www.webupd8.org/2011/11/install-gnome-shell-global-menu-in.html](http://www.webupd8.org/2011/11/install-gnome-shell-global-menu-in.html)

It's a shell extension. There are some for the 'places' menu too - might be worth a look

---

### Post by ComicalEngineer on 2011-11-29
> **Dry Lips said:**
> No you cannot. Actually you have to install "classic gnome" before you choose this
at the login screen. You have to:
```

sudo apt-get install gnome-session-fallback
```


I would but I can't find the blasted Terminal Window in the new Ubuntu Office 2007 interface.

Help! Please! Just tell me where I can find the terminal window. :(

---

### Post by Larkspur on 2011-11-29
> **ComicalEngineer said:**
> I would but I can't find the blasted Terminal Window in the new Ubuntu Office 2007 interface.

Help! Please! Just tell me where I can find the terminal window. :(

Either:

1) Press the Super key (it's the one that's probably got the Windows flag on it) and start typing "terminal".  After a couple of letters, the launcher for Terminal should appear.  Click on it, or drag it to the laucher bar in case you need it again.

or:

2) Hold down ctrl+alt+t

---

### Post by Nutria on 2011-11-29
> **Larkspur said:**
> Either:

1) Press the Super key (it's the one that's probably got the Windows flag on it) and start typing "terminal".  After a couple of letters, the launcher for Terminal should appear.  Click on it, or drag it to the laucher bar in case you need it again.

or:

2) Hold down ctrl+alt+t

Well that's intuitive...  ](*,)

---

### Post by ComicalEngineer on 2011-11-29
Thanks.

Much obliged for your help.

---

### Post by ComicalEngineer on 2011-12-04
Well folks, I have been using the new interface for a few days now in the interests of giving it a fair try but I'm no nearer liking it!

Issues for me:

* Still can't find half of what I need easily, most of this seems to be buried in the jazzy but unhelpful semi-transparent box with it's confusing collection of gadgets.

* Really HATE the huge icons on the left, much too big for even my 15" laptop never mind my 12" laptop!

* Why does the menu bar have to be locked to the top of the screen? Why can't I move it round like before?

* Whose bright idea was it to move the window buttons to the left when they have been on the right for years? That is just change for change's sake and downright annoying

* Even worse, Firefox menu has disappeared off the window and onto the fixed menu bar! Whaaaat? Why? When i have firefox in the bottom right corner of my screen, I now have to go all the way to top left to find the menu bar. That is a real Microsoft moment.

* Why isn't there an option for a classic interface instead of the new abortion?


And finally, how can I give some feedback where it will make a difference?

Yours and feeling alienated,

CE

---

### Post by ManualSparrow on 2011-12-05
I'd suggest trying out elementaryOS. It's based on Ubuntu 10.10, supports whatever apps you can find in Software Center, etc. 

Take a tour: [http://elementaryos.org/discover](http://elementaryos.org/discover)

---

### Post by Mark Phelps on 2011-12-07
> **ComicalEngineer said:**
> Well folks, I have been using the new interface for a few days now in the interests of giving it a fair try but I'm no nearer liking it!

Issues for me:

* Still can't find half of what I need easily, most of this seems to be buried in the jazzy but unhelpful semi-transparent box with it's confusing collection of gadgets.
That's how the new "dash" works.

> * Really HATE the huge icons on the left, much too big for even my 15" laptop never mind my 12" laptop!Install UbuntuTweak and use it to shrink down the icons to 32 pixels.

> * Why does the menu bar have to be locked to the top of the screen? Why can't I move it round like before?
That's how Unity works.

> * Whose bright idea was it to move the window buttons to the left when they have been on the right for years? That is just change for change's sake and downright annoyingHas been this way for a while now -- not new with 11.10

> * Even worse, Firefox menu has disappeared off the window and onto the fixed menu bar! Whaaaat? Why? When i have firefox in the bottom right corner of my screen, I now have to go all the way to top left to find the menu bar. 
That's how Unity works.

> That is a real Microsoft moment.Given that Microsoft does NOT force the Applications menu on the top row of the desktop, fail to see what this has to do with Microsoft!

> * Why isn't there an option for a classic interface instead of the new abortion? Yes there is, but it's not available as a default.

> And finally, how can I give some feedback where it will make a difference?
What makes you think any feedback will make a difference?  Any causal glance at the computer news for the last six months reveals article after article complaining about "Unity" -- and Canonical is still pushing this on us all as the "future way".

---

### Post by Nutria on 2011-12-07
> **Mark Phelps said:**
> Install UbuntuTweak and use it to shrink down the icons to 32 pixels.

And if we want 36x36 or 48x48 pixel icons?

> Has been this way for a while now -- not new with 11.10

New with 11.04.

> That's how Unity works.

I'm sure it works great on that tablet I don't own...  :(

> What makes you think any feedback will make a difference?  Any causal glance at the computer news for the last six months reveals article after article complaining about "Unity" -- and Canonical is still pushing this on us all as the "future way".

Sadly true.  Viva the Meerkat!

---

### Post by cortman on 2011-12-07
I don't like Unity either. But I'm excited that there are so many different DE options. It's totally awesome that we Linux users can choose between Gnome, Unity, XFCE, LXDE, KDE, Gnome fallback, E17, and many others I don't have time to name.
After using Gnome 2 off and on for several years, and a little adjustment and learning curve, I'm totally Gnome Shell (3.2). If you learn a little about how gnome works you find out how much you really can customize on it.

---

### Post by kurt18947 on 2011-12-07
I prefer Gnome-shell myself.  There are extensions to change the default function.  You might also take a look at Mint 12 or install Gnome-shell then add the MSGE (I think) extension to make Mint's shell available in addition to Unity, Unity 2D and Gnome-shell.  You can select different user interfaces when you log on by clicking the little gear-looking thing to the right of your user name.  I think there'll be a utility to change Unity settings easily on the 12.04.  I've read about it but haven't installed 12.04 yet to play with it.

> **ComicalEngineer said:**
> Well folks, I have been using the new interface for a few days now in the interests of giving it a fair try but I'm no nearer liking it!

Issues for me:

> * Still can't find half of what I need easily, most of this seems to be buried in the jazzy but unhelpful semi-transparent box with it's confusing collection of gadgets.
You can either tap the super 'windows' key or stick the mouse cursor on the left side of the screen and type in the search box what you're looking for.  When I type 'pri' for instance printers comes up.  Or type 'wri' and LibreOffice writer comes up.  Attach your most frequently used stuff to the launcher bar.  Two ways to do that. One is to right-click on the app's icon in the window and click 'add to launcher'.  The other is when an app is launched its icon is added to the launch bar.  If you right-click the icon in the launch bar, you can select 'keep in launcher' or words to that effect.

[QUOTE]* Really HATE the huge icons on the left, much too big for even my 15" laptop never mind my 12" laptop!
There is a way to change the icon size.  I don't know how to do it and very seldom use Unity so I'm not going to spend the time to learn.  This will probably be easier in 12.04.


> * Why does the menu bar have to be locked to the top of the screen? Why can't I move it round like before?I think they did that because they did away with one line. The new buttons are on the same line as the controls and indicators on the right.  Gnome-shell has a means via gnome-tweak-tools to restore the buttons on the right.

> * Whose bright idea was it to move the window buttons to the left when they have been on the right for years? That is just change for change's sake and downright annoying
see above

> * Even worse, Firefox menu has disappeared off the window and onto the fixed menu bar! Whaaaat? Why? When i have firefox in the bottom right corner of my screen, I now have to go all the way to top left to find the menu bar. That is a real Microsoft moment.My FireFox menu hides and shows when I move the cursor over top bar.  Right beside those accursed maximize/minimize/close buttons.:)

> * Why isn't there an option for a classic interface instead of the new abortion?People have worked on this.  There is a thread somewhere entitled 'Gnome classic mega thread' or something similar.  A lot have also gone to Xubuntu or added Xfce-desktop from the repositories.  This will get back to a more traditional desktop. It won't be exactly like Gnome 2 but it can come pretty close apparently.


And finally, how can I give some feedback where it will make a difference?

Yours and feeling alienated,

CE[/QUOTE]

I sound like a Unity FanBoi. I'm not, I wish Ubuntu/Canonical had worked with the Gnome developers rather than creating yet another UI. I'm sure there were politics & egos involved, I have no idea about details.

---

