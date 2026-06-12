---
title: "Help!!! Accidently turned off touchpad in admin account 14.04"
date: 2015-07-29
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-07-29
Help!,

While changing the mouse pointer speed in a Flashback Compiz session in my admin account I accidentally
turned off the touch pad.

After changing the mouse pointer speed, I noticed an ON/OFF slider on the right.  It was a little ambiguous to
me whether the slider should show On or the slider should be "moved" to On.  Foolishly I "moved" it to On.
What a mistake that was!  The pointer stopped working alltogether.  I then tried pressing the TAB key hoping
that I would get focus on the menu and then be able to navigate the menu with the arrow keys.  All I could do
was raise a terminal with with Ctl + T.  Thank God I had another account to login to, or Id be scrambling to find
another system, which fortunately I have.  [COLOR=#ff0000][I]It occurs to me that an act such as turning off hardware should
require an alert, a system sound, the more shrill the better, and authentication.[/I][/COLOR]  Unfortunately, my folly hosed
my admin account, at least temporarily.

I suspect that there must be a way to turn this feature back on in System Settings > Preferences > Mouse and 
Touchpad from the terminal; but I'm not a huge command line guy, so I expect it to be pretty difficult.

Can one of you kind gentlemen please walk me through it?

Thanks, Hannibal

---

### Post by steeldriver on 2015-07-29
[I][B]
You should be able to TAB to the slider and then hit the spacebar to toggle it ON/OFF[/B][/I]

On my 14.04 box with a regular Unity session, the command-line version (using gsettings - you could also use dconf if you have it) seems to be

```

gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled 'true'

```

or, to reset ALL the touchpad settings, 

```

gsettings reset-recursively  org.gnome.settings-daemon.peripherals.touchpad

```

Hope this at least points you in the right direction - you can use something like

```

gsettings list-recursively | grep touchpad

```

to see if there are any other likely candidates.

---

### Post by coljohnhannibalsmith on 2015-07-29
It seems my guardian angel was with me today. While waiting for someone from the forum to 
get back to me, I decided to punt. I did a Google search for *[COLOR=#0000ff]"Ubuntu System Settings From Terminal."[/COLOR]*
Fortunately I found a thread that gave me the actual name of the System Settings command, which is
*[COLOR=#ff0000]"gnome-control-center." [/COLOR]*[COLOR=#ff0000][/COLOR]I tried launching this first from the terminal in my backup account.  After
System Settings came up, I pressed the Tab key; and the first item in System Settings received focus.
I was then able to navigate to Mouse with the arrow keys. When Mouse finally received focus, I pressed
the Return key and the Mouse controls window opened. I was then able to use the Tab key again, to give focus
to each Mouse control, until the ON/OFF slider finally received focus. Fearing that I might hose this account too,
I quickly pressed the Tab key again, so that I took the focus away from the slider.  Now, feeling fairly confident
that I could repeat this procedure in my admin account, I restarted and booted back to the Greeter, where I
logged into my admin account.  I then repeated the procedure I rehearsed in my backup account until the
ON/OFF slider again received focus. There I was stuck trying to remember how I sometimes selected an item
from a Terminal menu. I finally remembered that I was often instructed to use the Space Bar to select an item
from a Terminal menu; so I tried it.  The ON/OFF slider did indeed return to the correct position and pointer
control came back immediately, even before I closed the window.  *[COLOR=#0000cd]"God what a relief!"[/COLOR]*

I've documented this misadventure as thoroughly as possible, so that not only others will have this procedure
available to them; but also so that I will have it available if I ever run into a similar problem. I hope this [COLOR=#ff0000][I]"never"
[/I][/COLOR]happens again; but living on the bleeding edge of technology, like I usually am, it probably will.

Hannibal:guitar:

---

