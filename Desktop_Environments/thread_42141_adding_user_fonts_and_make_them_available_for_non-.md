---
title: "adding user fonts and make them available for non-gnome apps ???"
date: 2005-06-16
forum: Desktop Environments
---

### Post by milou on 2005-06-16
Hi.
I want to add fonts as user : I just added some fonts to my personal .fonts directory, logged out and in again and got them available in gnome applications.

**However** these fonts don't get available to non-gnome apps, for instance openoffice, qt apps (scribus) etc...

What is the procedure to get such fonts available to any X apps installed on the linux box ??? 

Eric

---

### Post by l.tambiah on 2005-06-17
This is something i want to configure myself but havent got round to it as of yet. There is a guide here that may point you in the right direction:

[CookBook](http://dsl.org/cookbook/cookbook_6.html)

However OpenOffice can be cured quite simply:

Open Office Writer then do the following:

Open the "Tools -> Options -> OpenOffice.org -> View" dialog. Uncheck the "Screen font antialiasing" check box. Leave the dialog by pressing the "OK" button. The change should take effect immediately.

This solution can be found on the openOffice site.
[http://www.openoffice.org/FAQs/fontguide.html](http://www.openoffice.org/FAQs/fontguide.html) 

Hope this helps...

---

### Post by hw-tph on 2005-06-17
Fonts that you drop in ~/.fonts will be available to XFT aware applications such as the GTK 2.x programs that are part of Gnome.

You can make these apps available to non-XFT applications as well but it takes a little work. You can easily install the fonts globally, but since that's not the subject here I'll just outline installing them as a user without admin privileges.

First off, unpack the fonts in ~/.fonts (or any other location as long as you remember where you have them). Then run the **mkfontdir** command in that directory and optionally **mkfontscale** if you have scalable fonts (.ttf fonts, etc).

Then you need to add the full path of the directory to the X font path list. You do this by running the command **xset +fp /home/whatever/.fonts/** and then **xset fp rehash** to make the X server aware of the changes.

You can put these commands in a startup script such as ~/.xsession or ~/.xinitrc so you won't have to enter them each time:
```
#/bin/bash
# Filename: .xsession
xset +fp /home/hw/.fonts/ &
sleep 1
xset fp rehash &
exec gnome-session
```

Håkan

---

