---
title: "Change the Panel Background with GTK theme"
date: 2008-12-23
forum: General Help
---

### Post by MaJoRa on 2008-12-23
I am currently using a theme which I have installed, and when I add a panel background it decides to place the background itself, but not on the applets inside of it. The result is I end up with a beautiful panel with big white blocks in it, which isn't very attractive.

I know some themes do not colour these areas, does anyone have any advice to change the theme file itself? I have been looking in /home/USERNAME/.themes/THEMENAME in the GTKRC file and I am having trouble working it out.

Thank you.

---

### Post by Ivo Moelans on 2008-12-23
Good luck with that.
I suppose you want to define a panel background through right clicking on the panel and setting it in *Preferences&#8594;Background*. It is not so much the theme as some panel applets that are not well behaving here.

What you could try is this:
1) Look in the gtk-2.0 directory of your theme to locate the background the theme is using. (Usually *panel-bg.png* in a subdirectory *Panel* or something like that.)
2) Replace it with the panel you want. Adjust the png to the dimensions of the original background and give it the same name. (Work on copies and keep a backup of the original)
3) See which applets are *still* misbehaving (if any) and report back with the name of the theme you are using and the misbehaving applets.

---

### Post by MaJoRa on 2008-12-23
I have done this, and the misbehaving applets are the quicklounge, tray area, window list, and the taskdock I am using. 

The theme I am using is the Aero-Clone found on Gnome-look.org

EDIT: It would seem it is using the image I want, however it doesnt show the transparencies in it that you get by adding the background using the GUI. Is there any way to have it show this transparency or perhaps have no images for it at all so it shows the transparent background?

---

### Post by Ivo Moelans on 2008-12-23
I've looked at it. This theme is very, very complicated. It tries to offer a lot of choices and that complicates it immensely. Furthermore, there are a lot of things wrong with it - not only the panel. There is a missing theme engine, radio buttons aren't rendered correctly and the names are confusing: a button that is in fact blue is called *panelbutton_gray_1.png*. Functions are distributed more or less randomly across rc files. All this makes it very hard to try to repair this theme, if it is at all possible.
I'd like to help, but this is almost impossible unless you're the author of the theme.
May I suggest that you look out for other themes? If you really like the Aero look, there are others on gnome-look.org, but this [http://www.gnome-look.org/content/show.php/Aero-LiNsta?content=57915]("http://www.gnome-look.org/content/show.php/Aero-LiNsta?content=57915") seems to have the same problems, although the panel seems better.
Sorry that I couldn't be more helpful, but if you decide to try another theme, feel free to signal any problems. If I can I will help.
Good luck.

---

### Post by MaJoRa on 2008-12-23
Well I would like to thank you for your help, and I have succeeded in doing what it was I wanted, I just commented out a few lines here and there (mainly the image ones that draw the background at all), and now I find myself with the effect I want.

To show you what I have achieved, and what this was for:
[IMG]http://img.photobucket.com/albums/v173/Zeldamo/Windows7TaskCopy.png[/IMG]

---

### Post by Ivo Moelans on 2008-12-23
Congratulations! A simple solution: remove all the pictures. I was looking in the other direction: how to make all applets play nice with the background, but like I said: not simple to do with this theme and you seem to have found a perfectly good solution.
Please don't forget to mark this thread as solved.

---

