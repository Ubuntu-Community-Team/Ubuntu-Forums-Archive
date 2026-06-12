---
title: "Nautilus uses wrong icons"
date: 2006-06-03
forum: Desktop Environments
---

### Post by waffen on 2006-06-03
Hello,

I update my Breezy via: update-manager -d command, its work fine. 

But when I open the nautilus if show me wrong icons for some extensions: .py, .xml, .bz  etc (See the attachment)

Its a bug??

Thanks!

---

### Post by sawjew on 2006-06-04
There's nothing wrong, it's just that the latest theme update has different icons than the previous ones.  Ubuntu is now using Tango icons as the default.  I really like the Tango icons but I find them sadly lacking for mimetype icons. :(  

Your .py file is showing a generic text icon and your .xml has no associated icon so it's showing a generic icon.  I have edited some of the mimetype icons in mine by going into /usr/share/icons/Tango/scalable/mimetypes and replacing the icons with ones I like better making sure the name is identical.  

If you don't want to go to all that hassle you could just try using a different icon theme with better mimetype support or try adding extra mimetype icons from a different suite.  check out [www.gnome-look.org]("www.gnome-look.org") for other icon suites.

hope this helps.

---

### Post by waffen on 2006-06-04
[QUOTE=sawjew]There's nothing wrong, it's just that the latest theme update has different icons than the previous ones.  Ubuntu is now using Tango icons as the default.  I really like the Tango icons but I find them sadly lacking for mimetype icons. :(  

Your .py file is showing a generic text icon and your .xml has no associated icon so it's showing a generic icon.  I have edited some of the mimetype icons in mine by going into /usr/share/icons/Tango/scalable/mimetypes and replacing the icons with ones I like better making sure the name is identical.  

If you don't want to go to all that hassle you could just try using a different icon theme with better mimetype support or try adding extra mimetype icons from a different suite.  check out [www.gnome-look.org]("www.gnome-look.org") for other icon suites.

hope this helps.[/QUOTE]

Hi,

Thanks for your response.

Uhm... I dont know, I change only the Icon Set in the Theme editor to Gnome and not show the correct, see the new atachment. Any idea?

Thanks!

---

### Post by frying_fish on 2006-06-04
To  change which iconset gnome is using go to system-->preferences--> themes,

click on theme details and then the icons tab, and you can choose between some pre-designed ones.

---

### Post by sawjew on 2006-06-04
I tried changing the icon themes myself and it seems that none of the themes have an icon for .xml .py.  I think you will either have to put up with it, try and find a more complete icon set or add some extra icons yourself.  I find that the biggest drawback with Gnome is the incomplete icon sets.  KDE seems to have more complete sets.

just try some other icon sets from Gnome Look and see how you go.

---

### Post by waffen on 2006-06-04
Yes, I make that (see my post below) but the Gnome Icon set not show the correct Icon for the sames mime types....

---

### Post by waffen on 2006-06-04
[QUOTE=sawjew]I tried changing the icon themes myself and it seems that none of the themes have an icon for .xml .py.  I think you will either have to put up with it, try and find a more complete icon set or add some extra icons yourself.  I find that the biggest drawback with Gnome is the incomplete icon sets.  KDE seems to have more complete sets.

just try some other icon sets from Gnome Look and see how you go.[/QUOTE]

Hi,

I tried that, in my second post I show you an screenshot with the result of this operation.

Changes the icons, but Nautilus dont show me the correct icons for the same mime types and the icons for .py .xml etc are in the correct path, I check this...

I think then error is a nautilus bad config but I dont know how fixed it ](*,) . Any idea?

Thanks!!!!

---

