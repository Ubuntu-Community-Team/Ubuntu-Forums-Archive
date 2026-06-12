---
title: "thunar uses only one icon"
date: 2007-04-10
forum: Desktop Environments
---

### Post by szymon_g on 2007-04-10
hi.
i've installed FF beta as a command-line system.
i've installed my favourite window manager (icewm :-P), i've installed also a thunar.
and now i've got a problem: it uses only one icon- doesn't matter that file is a mp3, video, text or folder/directory
look here

[http://www.fotosik.pl/pokaz_obrazek/724167215a36fe46.html](http://www.fotosik.pl/pokaz_obrazek/724167215a36fe46.html)

any suggestions how can i change this?
if possible, could you tell me how can i change icons for this from rox-filer (i've found them mor esthetic than most thunar's/nautilus's)

thank You for any suggestions/help :-P

szymon

---

### Post by kerry_s on 2007-04-10
You use a ".gtkrc-2.0" file to specify the icons.

your-editor ~/.gtkrc-2.0

gtk-icon-theme-name = "Name-of-icon-set"
Example: gtk-icon-theme-name = "Tango"

---

### Post by szymon_g on 2007-04-10
ekh... it seems that i dont have this file... neither in my home folder, nor in /
is it possible to set one selected ico to a file according to it's mime-type?

---

### Post by kerry_s on 2007-04-10
You make the file, it won't be there by default. Just use my command but replace "your-editor" with the name of what ever editor you use.
Example:
leafpad ~/.gtkrc-2.0

or if you want to do it from terminal

nano ~/.gtkrc-2.0

ctrl and x and y and enter to save.

On a side note, gtk-theme-switch will also create a ".gtkrc-2.0" if you use that for your theming, then you need to use ".gtkrc-2.0-mine".

---

### Post by szymon_g on 2007-04-10
hm..
i've installed gtk-thame-switch, there are only 2 available : default and pixmap... even after selecting pixmap there is no icons in thunar...
could you show me your gtkrc-2.0-mine file? i don't have it. mayby i'll be able to copy and edit it :->

---

### Post by szymon_g on 2007-04-10
ok, i solved my problem
thanks

**** SOLVED ****

[http://thunar.xfce.org/pwiki/documentation/faq#why_does_thunar_display_the_fallback_icon_for_all_files_and_folders](http://thunar.xfce.org/pwiki/documentation/faq#why_does_thunar_display_the_fallback_icon_for_all_files_and_folders)

**** SOLVED ****

---

