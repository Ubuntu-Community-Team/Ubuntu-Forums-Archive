---
title: "Non-orange color theme to Ubuntu/Edubuntu 12.04.1 possible?"
date: 2012-12-16
forum: Desktop Environments
---

### Post by Vesa Paatero on 2012-12-16
Hi,

I noticed that you can change the background picture/color and the color of window headers in Ubuntu 12.04.1 but I have been unable to change the color of folders, highlighted items etc to anything else than that unfortunate orange.

This reminds me of Windows Vista where you can similarly set background and some things but the displeasing dark color in the launcher bar persists... but even there, you can choose a classical look whereby that problem can be circumvented.

Is there a way around the oranges of Ubuntu?

Thanks for any help,
Vesa

---

### Post by Frogs Hair on 2012-12-16
You can look at the Gnome 3.4 themes here. [http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

---

### Post by Vesa Paatero on 2012-12-19
Thank you for the link!   However, I already have made so much progress in customizing this system that I think I'll want to keep it... Just one major problem remains: 
 . . . The applications: Firefox, Thunderbird and some others still follow the orange color scheme, and I can't figure out where the colors could be specified. According to Firefox's documentation, color customizations like might be done in userChrome.css but there seems to be none. There is also an extension called "Ubuntu Firefox modifications 2.6", which I disabled but it didn't seem to make difference to the looks.  Any further ideas?

Best Regards,
Vesa

---

### Post by Vesa Paatero on 2012-12-19
Yes! I found the solution: The difference was that the interfaces of Firefox and Thunderbird are based on GTK+ 2 (unlike the other group of programs that were based on GTK+ 3), so I had to modified the files inside

/usr/share/themes/<theme name>/gtk-2.0/

whereas I had only modified those inside gtk-3.0/.

Happy and Merry Christmas to all of you who read this in time! :-)

Vesa

---

