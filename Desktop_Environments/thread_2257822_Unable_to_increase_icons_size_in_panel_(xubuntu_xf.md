---
title: "Unable to increase icons size in panel (xubuntu xfce4)"
date: 2014-12-22
forum: Desktop Environments
---

### Post by fkervin on 2014-12-22
Hi all,

I'm customizing xubuntu 14.04 and i'm using xfce4-panel that comes by default.

If I increase the height of the panel the start button increase its size proportionally but the icons of the applications (at left of the start button) have a maximun of around 40 pixels and no matter how hight I make the panel, the icons remains small. I have set those icons to not to have text (only icon) by disable "Show button labels" but even with this they remain small.

I've look at all the configuration options everywhere but I can't find this.

I've found many threads talking about a limit or 32 pixels or so and a way to increase a bit install xfce-taskbar-plugin, but I can't install this since it's not on repositories and after all, 42 pixels is still small for what I need (at least 60-70 pixels).

I really can't believe it can't be done.

Any help?

Many thanks in advance

---

### Post by Dennis N on 2014-12-22
I agree with your observations, except for launcher icons, which seem to be nicely scalable - I pushed them up to 80 pixels. But my launchers are kept on a separate autohiding vertical panel on the left side. Maybe that makes a difference. The panel font size is set by the default font size.

In Lubuntu, you can set both the panel height and icon size (affects all of them, including buttons and indicator icons). I went up to size 40 px icons and they behaved. The panel font size can be changed independently of font sizes elsewhere. No so in Xubuntu, so Lubuntu wins. Sounds like what you are looking for.

I don't have xfce-taskbar-plugin in my plugins list, and a check shows nothing matching xfce4-taskbar-* exists. Never heard of it. Lubuntu has a taskbar-plugin. Maybe they are confusing it with that.

---

### Post by fkervin on 2014-12-23
Thanks for your answer, Dennis N, I sill can't make them bigger, 80 pixels would be enought.

I'm still unable to solve this, I attach an image to clear ir:

[IMG]http://i59.tinypic.com/28ajpqu.jpg[/IMG]

the icons of the open applications can't be bigger than this, what is really tiny for me needs.

If someone can lend me a hand I will relly thanks.

Regards

---

### Post by Dennis N on 2014-12-23
If the larger icon size for all panel icons is the most important factor, you should use Lubuntu since it will allow increased size of the window button icons too. I attached a screen shot. Panel height and icon height are adjusted in the window dialog you see. I made them both 46 pixels. I haven't seen how to do that in Xubuntu. Also in Lubuntu, you can change the text size and color on the panel without affecting text anywhere else.

Also shown is the launcher on the left with some application launchers. Normally, this is set to automatically hide.

---

### Post by kerry_s on 2014-12-23
make sure the icon theme your using has scalable icons. there usually *.svg
if your using stock look in /usr/share/icons
if custom, just make sure there scalable

ps: the standard size for icons is 48 for *.png based themes. but if you want large icons i found if you put them on the desktop, you can resize them pretty large. but i haven't used xfce4 in a long while so i don't know if thats still true. i'm using ubuntu mate & have no issues resizing.

so maybe skip the panel?

---

### Post by Dennis N on 2014-12-30
> make sure the icon theme your using has scalable icons. there usually *.svg
In both Xubuntu and Lubuntu the themes in use do have a scalable set for applications. The minimum panel row size in Xubuntu is 16, and the icons on the window buttons in the window list will increase one time when you change panel row size to 18. After that, they do not increase further, no matter how large you set the panel row size. In Lubuntu the window button icons will continue to increase in size as shown in post #4.

---

### Post by kerry_s on 2014-12-31
you could use lubuntu panels in xubuntu or at least 1 just for your launcher icons. not sure why the xfce4-panels behave like that.

i installed the xfce4-panel & had no problem with icon size. perhaps deleting the panel & starting from scratch?

---

### Post by fkervin on 2014-12-31
Hi all,

I have to sorry for my delay in answer, I've been really busy those days.

I finally solved this problem using dockbarx, it can be used in way that integrates with xfce4-panel and is a replacement for the tiny icons I had by default.

Dennis N, I started with Lubuntu those days but I didn't like que "Windows 95 style" start menu and didn't found a good way to replace it with Whisker menu or similar, so I moved to xubuntu. Now I'm very hapy with the result.

Many thanks to all :)

---

