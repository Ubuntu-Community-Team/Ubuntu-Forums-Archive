---
title: "Default fonts size problem"
date: 2004-11-13
forum: Desktop Environments
---

### Post by loucomballa on 2004-11-13
Hi,
Does anybody know why the font size of most of the apps I install on Ubuntu (such as xmms, mldonkey, Mplayer,...) is SO SMALL?? I cannot change it and its very difficult to read. Can it has something to do with gnome? 

I've configured the desktop fonts with:

Apps: Bitstream Vera Sans 10
Desktop: Bitstream Vera Sans 10
Windows: Bitstream Vera Sans 10
Terminal: Bitstream Vera Sans 10

But it stills happens... :-(
Thanks!

---

### Post by HiddenWolf on 2004-11-13
I think 10 is the default size, is it not?

Have you tried setting it to 11, or 12?

What is your screen resolution?

---

### Post by loucomballa on 2004-11-13
Yes 10 it's fine, and my default apps (Firefox, gnome...) look fine, the problem is with the apps I installed afterwards: xmms, mldonkey, Mplayer. For thes apps the font is not my Desktop font and its size is really tiny. Only Thunderbird and Sancho (a java GUI for mldonkey) has a font consistent with my desktop font (Bitstream Vera Sans).
It's as if these apps could not use the desktop fonts.

My screen's resolution is  1024x768. I must also say that my current system language is Catalan, not English (But I don't think that might cause this...)

Thanks!

---

### Post by nocturn on 2004-12-23
[QUOTE=loucomballa]Yes 10 it's fine, and my default apps (Firefox, gnome...) look fine, the problem is with the apps I installed afterwards: xmms, mldonkey, Mplayer. For thes apps the font is not my Desktop font and its size is really tiny. Only Thunderbird and Sancho (a java GUI for mldonkey) has a font consistent with my desktop font (Bitstream Vera Sans).
It's as if these apps could not use the desktop fonts.

My screen's resolution is  1024x768. I must also say that my current system language is Catalan, not English (But I don't think that might cause this...)

Thanks![/QUOTE]

I have not found a solution to this myself but....
The apps you mention are all GTK1, they are not affected by the font settings in Gnome 2.  

The .gtkrc and .gtkrc-1.2-gnome2 files control them.  Although I still have to find good values for these.

---

