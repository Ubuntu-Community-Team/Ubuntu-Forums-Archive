---
title: "Metacity/ GTK: Border-less window theme?"
date: 2008-11-23
forum: Desktop Environments
---

### Post by hictio on 2008-11-23
Does any one know of any such theme or style?
By border-less I mean, without the border on the left, on the right and on the bottom, but *with* a title bar, just like the regular window on Os X ;) .

I know that on Emerald you can have those themes, but this is for a rather old box which has an old NVIDIA card no longer supported by Intrepid, so no Compiz and therefore, no Emerald; not to mention, Desktop Effects :)

Just for clarification, border-less, not with a transparent border when the window looses focus, etc.
I have Googled, and searched Gnome Look/ Art, etc, to no avail.

TIA

NOTE: I was going to post this on the Desktop Effect forum, there is a disclaimer that the forum is for effects and composite problems, so here it goes... Mods, feel free to move it :D

---

### Post by jrib on 2008-11-23
I like the same.  Personally I just copy /usr/share/themes/Mist to ~/.themes/Minimal and change ```
<distance name="bottom_height" value="5"/>
``` to ```
<distance name="bottom_height" value="1"/>
``` in metacity-theme-1.xml.  You should change the name in metacity-theme-1.xml too to make it easier to select in Appearances.  Then just hit "customize" in Appearances and choose the controls and icons you want.  For window border, choose "Minimal" or whatever name you gave it.

---

### Post by hictio on 2008-11-23
Thanks, I did something like that, and I was hoping that there were some other way, on the newer GTK engines.
I did it about a year ago, and on FreeBSD [Border-less windows for Gnome](http://oesediez.blogspot.com/2007/10/border-less-windows-for-gnome.html), the results were rather mix... Maybe I have edited the wrong parameters, or maybe it was an older version of Metacity.
I'll give it a shot and let you know.

---

