---
title: "Beryl/Compiz/Compiz fusion questions"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by Ptero-4 on 2007-06-29
Hi. I'm about to try beryl and compiz and wanted to know a few things.
I heard that compiz uses metacity themes, Is that true? if it is does it means that the window borders tab in the themes control panel will still be present and using it to change themes changes your compiz theme? also Is beryl capable of using metacity themes? and finally does compiz fusion uses metacity themes?

---

### Post by Mr Greencastle on 2007-06-29
Compiz uses Metacity (or at least something similar) as its window decorator, and Beryl can use Metacity as well. To answer that question, yes, changing your theme changes Compiz's aswell.

However, Beryl usually comes with Emerald (which Compiz can use now too) as its window decorator, which has more configuration abilities than Metacity's.

To install Emerald:
sudo apt-get install emerald emerald-themes

And launch it with: emerald --replace
(You may want to add this to your startup)

To find themes for Emerald, visit: [www.gnome-look.org](www.gnome-look.org) (under the 'Beryl' tab).

If you are using KDE, I'm not sure if is the same thing... Someone else would have to tell you, as I'm not very familiar with it... (Though KDE4 looks bangin'!)

Regards,
Mr Green

---

