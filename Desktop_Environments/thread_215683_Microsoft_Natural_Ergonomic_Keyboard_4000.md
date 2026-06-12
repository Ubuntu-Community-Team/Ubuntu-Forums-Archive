---
title: "Microsoft Natural Ergonomic Keyboard 4000"
date: 2006-07-14
forum: Desktop Environments
---

### Post by maubp on 2006-07-14
I've bought a UK version of this USB only keyboard, and as I rather expected while "the basics" work, lots of the extra keys don't.

I've done a fair amount of googling to get this far...

Problem One
===========
Undefined keymappings.  There is no suitable keyboard definition under System->Preferences->Keyboard->Layouts->Keybaord Model

I've tried the all the MS models, and while some get a few keys right, they either miss out others or get them wrong.

I've left my keyboard as "Generic 105 key (Intl) PC" and used xmodmap to define all the keys I could in file ~/.Xmodmap

> !! ~/.Xmodmap
!!
!! The leading `!’ is the comment sign.

!! Web/Home, search, mail (top left)
keycode 130 = XF86HomePage
keycode 122 = XF86Search
keycode 236 = XF86Mail

!! 1-5, favorites
!!not working, no xev code

!! zoom slider
!!not working, no xev code

!! mute, volume down/up, play/pause
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPlay

!! calculator
keycode 161 = XF86Calculator

!! equal sign, parenthesis left/right, backspace
keycode 157 = KP_Equal
!!left parenthesis not working
!!right parenthesis not working
!!backspace is exactly the same as normal backspace

keycode 234 = XF86Back
keycode 233 = XF86Forward

!!The F1 to F12 function keys should act normally,
!!but have special actions when the f-lock key is
!!toggled

!Function F1
keycode 245 = Help

!Function F2
keycode 135 = Undo

!Function F3
keycode 138 = Redo

!Function F4
keycode 137 = XF86New

!Function F5
!!keycode ? = XF86Open

!Function F6
!!keycode ? = XF86Close

!Function F7
keycode 228 = XF86Reply

!Function F8
keycode 142 = XF86MailForward

!Function F9
keycode 218 = XF86Send

!Function F10
!!keycode ? = XF86Spell

!Function F11
keycode 213 = XF86Save

!Function F12
keycode 185 = Print
!Note this will make it act just like PrtScn

!! End of ~/.Xmodmap
With that done, these symbols are recognised (for example) when using System->Preferences->Keyboard Shortcuts.

As I had hoped, the volume and mute controls "just work" and also Rhythmbox responds to the play/pause key.

Problem Two
===========
Some keys do nothing (e.g. when running the tool xev to get their keycodes), including:
* Zoom control (in center of keyboard)
* My favorites, and favourite keys 1 to 5 (top center)
* Extra brackets above the keypad on right
* Open (F5)
* Close (F6)
* Spell (F10)

I'm guessing these have to be fixed in the kernal driver...

---

### Post by maubp on 2006-07-14
There is also [this bounty thread](https://launchpad.net/bounties/natural-ergonomical-kbd-4000-zoom) open... with links to a [Jan 2006 patch by Liyu](http://www.ussg.iu.edu/hypermail/linux/kernel/0601.0/0893.html) (does the zoom keys, favourites, the missing function keys: spell, open, close - but not the extra brackets) and [March 2006 patch by John Zaitseff](http://www.ussg.iu.edu/hypermail/linux/kernel/0603.0/0359.html) (does the zoom keys, favourites, the missing function keys: spell, open, close, AND the extra brackets).

I've not tried them... but it looks like John Zaitseff's patch made it into Andrew Morton's kernel (mm-sources) as of [5 March 2006](http://www.lieberbiber.de/docs/mm-traffic13.htm#usb-key-codes-for-microsoft-natural-ergonomic-4000-usb-keyboard.patch).

---

### Post by maubp on 2006-07-24
Liyu has made a [new post](http://www.ussg.iu.edu/hypermail/linux/kernel/0607.3/0009.html) to the Kernel mailing list.

---

### Post by boom2k1 on 2006-07-30
I also have a Microsoft Ergonomic keyboard 4000. So what can we do right now?  Looking at the links above, it seems that they wrote some codes to make the buttons work. Does anyone know how to actually get it to work? (i.e. compile/install) ?

Or does anyone have a simpler approach to let the computer recognize those zoom keys and buttons?

Thanks!

---

### Post by zerwas on 2006-08-05
[HOWTO setup Microsoft Natural Ergonomic Keyboard 4000]("http://www.ubuntuforums.org/showthread.php?t=229559")

---

### Post by Wildboar on 2008-01-11
OMFG

Finally I can use my keyboard as a keyboard.  Thanks.  

Now if we can just get one of the nine pound heads (and I mean this in a completely complementary manner) to get full support for this popular keyboard implemented into the project I for one will be ecstatic.

With both my mouse and my keyboard ails being solved on the same day you'd think it was my birthday....  Wait a sec, it is my birthday.  Thanks, it's just what I wanted.

Bret.

---

