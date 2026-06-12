---
title: "Change folder/text highlighting bar color, but NOT icons ?"
date: 2014-02-09
forum: Desktop Environments
---

### Post by typos1 on 2014-02-09
Just upgraded to 13.10 and I dont like the biege colour it uses for folders and and text highlighting (like if youre copying text or the sqaure for the date in calender). 

I know how to change the colour of folders in themes, but this means all the icons change and I prefer the ubuntu-mono-dark icons. 

Is there anyway of changing just the folder and text highlight colour ? 

I ve tried adding "orange" to the folder names in usr/icons (pretty sure it was there can double check), but therye still grey.

(hope US users understand "colour" and "grey" lol)

---

### Post by Dennis N on 2014-02-09
> Is there anyway of changing just the folder and text highlight colour ? 

(in themes, highlight color = selected background color)

You need to change settings in two theme sub folders found inside **/usr/share/themes/theme-name**:

in folder gtk-2.0: file: **gtkrc** (in here, look for **selected_bg_color:#XXXXXX** where XXXXXX is a color code you can change)
in folder gtk-3.0: files: **gtk.css**, **settings.ini**

Logout and Login is sufficient to see the changes.

---

### Post by typos1 on 2014-02-10
Thanks.

Selected background colour for what exactly ?

What I want, essentially, is ubuntu-mono-light theme, but using ubuntu-mono-dark icons. 

I  ve looked in usr/share/themes/theme-name, but there is no folder for ubuntu-mono-dark or light. I lloked in the folder marked "default" but in the gtk-2.o file it says:

#
# Default keybinding set. Empty because it is implemented inline in the code.
#

and nothing else.

---

### Post by Dennis N on 2014-02-10
ubuntu-mono-dark and ubuntu-mono-light are both icon themes in /usr/share/icons. They are collections of icons for folders, programs icons, etc. and you can't modify those yourself. You can swap them for another icon theme, like Faenza, or Humanity, or something else you have installed in /usr/share/icons.

You can only make color changes to appearance themes like Ambiance, Radiance... whatever is in /usr/share/themes.

---

### Post by typos1 on 2014-02-10
I see, maybe I could copy them ?

I m even more confused now - mono dark and mono light dont all have the same things but in different colours in light has things that dark doesnt. 

I cant find any folder icons either (other than ones for home) so no chance of copying as Ic ant find what to copy. 

It seems like it would be do-able as I can copy folders from mono-dark and paste into mono-light if I open the folder as administrater.

Plus some themes which are listed in icons and themes dont appear to be installed according to Ubuntu Tweak and in settings/appearance.

---

### Post by Dennis N on 2014-02-10
> **typos1 said:**
> I see, maybe I could copy them ?

Originally you said:
> Is there any way of changing just the folder and text highlight colour ? 

Copying won't help.

Heres the two things you can realistically do:

1) You can only change the color of the folder icons by using another icon theme, but then other icons will change as well. 
Changing just the folder color is not possible. When you use a new icon theme, you use them all.

2) You can change the colors used by many appearance themes by changing a color code as mentioned in post #2. 

I seem to remember changing Ambiance was a problem, so I changed my theme to Zukitwo Dark (I had to install it), and was able to modify the selected item color (what you are calling the highlight color) of that theme. I am looking at Ubuntu 12.04 here, and I made the changes soon to it soon after it came out - almost 2 years ago. I am using the Faenza icons, and was satisfied with that combination.

You can look in the **Ubuntu Software Center** or at **gnome-look.org** at icon themes and see if there is anything that appeals to you. If so, download it, icon themes are fairly easy to install. Appearance themes are trickier for Ubuntu Unity. First you have to find a theme that has a version for Unity - there are certainly some at gnome-look.org you could check out. It should say if it works for Unity on the theme's page and give directions for installing.

I have My Unity and Ubuntu Tweak installed, and they help change and apply the themes. I suggest you use one of those to help.

---

### Post by Dennis N on 2014-02-10
> **typos1 said:**
> I see, maybe I could copy them ?

I m even more confused now - mono dark and mono light dont all have the same things but in different colours in light has things that dark doesnt. 

I cant find any folder icons either (other than ones for home) so no chance of copying as Ic ant find what to copy. 

It seems like it would be do-able as I can copy folders from mono-dark and paste into mono-light if I open the folder as administrater.

Plus some themes which are listed in icons and themes dont appear to be installed according to Ubuntu Tweak and in settings/appearance.

I don't know how this would work. Never attempted something like that. There is a way to experiment by copying the entire icon theme folder from /usr/share/icons to ~/.icons and do your experimenting on the copy. In this location, you can make changes and see the result, but the original set is safe in /usr/share/icons. If you mess it up, just delete the folder in ~/.icons and the computer will use the other set.

[B]That said, I would recommend what I said in the previous post: find an icon set that you like in the Ubuntu Software Center (best way) or at gnome-look.org and try it out. Maybe gnome-colors would appeal to you as it has several colors of folder icons to use. I used to use it myself.
[/B]

---

### Post by Dennis N on 2014-02-10
Just to add:

**gnome-colors** is in the Ubuntu Software Center. You get several icon sets. Why not install it and try them out?

**Faenza Icon Them**e is in the Ubuntu Software Center too. You should get that and try it . Very good icons.

Much easier to get your icons through the Software Center because they are automatically installed. Strongly recommended.

---

### Post by typos1 on 2014-02-10
Thanks, tried it.

I ve had all those options availbale before and never removed them, they must have been removed by an upgrade. 

All the icons change to ones I dont like when I try those themes.

All I want is what I had before upgrading to 13.10 !!

---

### Post by Dennis N on 2014-02-10
I haven't seen Ubuntu 13.10. I am happy with 12.04 and will use it until April 2017 when it loses support. Too much time spent customizing to do it all over!

---

### Post by vasa1 on 2014-02-10
> **typos1 said:**
> ...
(hope US users understand "colour" and "grey" lol)
An image of what you see and what you want would help *US* users, wherever we are, understand better ;)

---

### Post by typos1 on 2014-02-15
Well, opened  the icons folder as root, copied mono dark and mono light, replaced all the mono light items with mono light icons, put into a folder named "ubuntu-mon-light-modified", put this into usr/share/icons, and now I have exactly what I want !

Perfect !!

---

### Post by typos1 on 2014-02-16
Well, almost, the ibus keyboard icon is a white box with a red circle in - ie broken, just like the settings cog symbol was in some icon packs on 12.10. I m sure there was a problem with an icon in 13.10 aswell, but cant remember which one now.

I ve looked in ubuntu mono dark and light folders and the ibus-keyboard.svg icon is broken and locked, but it still works when the pc is using those icon packs ( - was going to put the icon from those packs in my modified ubuntu mono light folder).

So I downloaded another ibus-keyboard.svg icon and put that in my modified mono light folder, but when its in there it shows as broken and locked aswell, strange.

---

