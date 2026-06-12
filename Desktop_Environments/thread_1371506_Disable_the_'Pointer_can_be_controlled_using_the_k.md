---
title: "Disable the 'Pointer can be controlled using the keypad' function"
date: 2010-01-03
forum: Desktop Environments
---

### Post by stoneage on 2010-01-03
Can anyone tell me how to permanently disable the 'Pointer can be controlled using the keypad' accessibility function?

There was a post about it on launchpad, that I used before and since updating to 9.10 I can't find it.

It may be a Gnome bug, and its getting very irritating - maybe 10 - 12 times a day.......

Any useful help is appreciated - esp if you can name it so I can uninstall it :)

---

### Post by falconindy on 2010-01-03
It may help your search to know that this isn't a Gnome feature -- its builtin functionality from The X server.

---

### Post by Kraust on 2010-01-03
Alt+Shift+Num Lock

I had this issue and I wanted to look up a solution for you. Really is annoying when you want to use the Numpad but can't.

Edit: Also System > Assistive Technologies > Keyboard Preferences > Mouse Keys will solve the problem.

---

### Post by stoneage on 2010-01-03
@falconindy, thanks, that narrows it down a bit, though it also means curing might not be easy. Do you happen to know how to disable it?

@Kraust, I know, but that only toggles it on and off, it doesn't prevent it re-enabling itself. There is a bug present somewhere and I just want to kill the whole damn feature. I'm completely fed up with it turning itself on.

---

### Post by falconindy on 2010-01-03
> **stoneage said:**
> @falconindy, thanks, that narrows it down a bit, though it also means curing might not be easy. Do you happen to know how to disable it?
Sadly, I do not. You might try binding something else to it via compiz or xmodmap.

---

### Post by stoneage on 2010-01-04
Hello again, I found it.....

For anyone else it is here:-

> Ond&#345;ej Buriánek wrote on 2009-11-21: #52 Hello fellow earthlings daily beaten by this bug.
I used this workaround to permanently disable mousekeys shortcut shift+num-lock, alt+shift+num-lock etc...
gksudo gedit /usr/share/X11/xkb/compat/complete
-or-
sudo nano /usr/share/X11/xkb/compat/complete
and comment out lines for mousekeys and accesx(full) (for full keyboard accessibility purge)
resulting file /usr/share/X11/xkb/compat/complete:
// $XKeyboardConfig$
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "complete" {
include "basic"
augment "iso9995"
//augment "mousekeys"
//augment "accessx(full)"
augment "misc"
augment "xfree86"
augment "level5"
};
Wish you a lot happy days without moving mouse by keypad
Greets Ondrej

[https://bugs.launchpad.net/xorg-server/+bug/192508](https://bugs.launchpad.net/xorg-server/+bug/192508)

---

### Post by fooey on 2010-02-26
> **stoneage said:**
> Hello again, I found it.....

For anyone else it is here:-

THANK YOU!!!!!! My God this has bugged me for years. I just finally got fed up & started to google around for it. I really appreciate people, like yourself, coming back to leave an answer for others who come across similar problems.  [IMG]http://www.acurazine.com/forums/images/smilies/thumbsup.gif[/IMG]

---

### Post by kieloS. on 2012-05-11
Thank you very much. I had the same problem on Arch Linux, that one fixed it!

---

### Post by grahammechanical on 2012-05-11
There is another, simple way that has been around for a while. It is in 12.04 and I am sure that it is in 11.10.

System Settings>Univeral Access> Pointing and Clicking tab. There we can turn off Control the Pointer Using the Keypad.

Regards.

---

