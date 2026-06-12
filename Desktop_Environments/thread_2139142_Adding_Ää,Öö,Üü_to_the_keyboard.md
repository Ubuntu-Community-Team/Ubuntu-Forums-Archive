---
title: "Adding Ää,Öö,Üü to the keyboard"
date: 2013-04-26
forum: Desktop Environments
---

### Post by totallynuts on 2013-04-26
Hi folks,

I need to add the three letters Ää,Öö,Üü to my keyboard. I followed this tutorial [http://ubuntuforums.org/showthread.php?t=188761](http://ubuntuforums.org/showthread.php?t=188761), but modifying the layout file didn't change anything whatsoever. I have been trying a lot of stuff in the last 2 hours but it just won't work, so I'm asking for help about this issue.

I have modified my usr/share/X11/xkb/symbols/us file in the very first section(English (US)) according to the tutorial,
..
key <AC01> {[a,A,adiaeresis,Adiaeresis]};
..
 so the key where aA used to be should actually now print aA and äÄ, but it doesn't, not even after a reboot. As a layout I chose "English (US)" (which I modified).

I am using Ubuntu 12.10 with Gnome Classic (might that be the problem?).


Thank You!

---

### Post by sudodus on 2013-04-26
You can use German keyboard
```
setxkbmap de
```
ü is on the key right of p (pee)
öä are on the keys right of l (ell)
z and y are swapped (qwertz keyboard layout) compared to the English US keyboard.

Or you can use Swedish keyboard
```
setxkbmap se
```
ü must be written with a key combo, second key right of p, followed by u.
öä are on the keys right of l (ell), the same place as the German keyboard.
z and y are in the normal places (qwerty keyboard layout).

---

### Post by totallynuts on 2013-04-26
Oh, my bad there. I actually am german, but I prefer the english keyboard layout because of the parenthesis I need a lot for programming. However when writing emails it is quite annoying to copy and paste these special letter everytime I need them. I know there are different english keyboard layouts with the characters I need but all of them use dead letters for other characters, and I don't like double tapping a key for a single character to be printed.

Any further help?

Thanks

---

### Post by sudodus on 2013-04-26
It's easy to swap layout with

```
 setxkbmap de
``` and ```
 setxkbmap us
``` whenever you need the other layout. You can even get a small panel app to toggle the layout.

"**[FONT=courier new]setx TAB de|us[/FONT]**" if you use tab completion.

---

### Post by totallynuts on 2013-04-26
Allright, thanks, that actually helps a lot. But is there a way to truly fix my problem?

---

### Post by sudodus on 2013-04-26
Let us hope someone with experience of remapping keys will read this thread.

Good luck :-)

---

### Post by schragge on 2013-04-26
> **totallynuts said:**
> the key where aA used to be should actually now print aA and äÄ, but it doesn't, not even after a reboot.You should also have added ```
include "level3(ralt_switch)"
``` at the end of the section. IMHO, a better aproach would be writing your own layout variant rather than modifying an existing one.

---

### Post by totallynuts on 2013-04-26
include "level3(ralt_switch)"

That did it! Great thanks.

---

