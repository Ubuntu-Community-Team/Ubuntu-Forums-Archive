---
title: "Unable to find or access cairo-clock configuration files"
date: 2009-01-18
forum: General Help
---

### Post by sofasurfer on 2009-01-18
I installed cairo-clock. I can run it from terminal and apply some preference settings. I want to configure it further, such as specifying desktop location of clock.

I do a '$ locate cairo-clock' and am unable to open any of the display files. For instance... '/usr/share/doc/libcairo2/README.gz' shows this message...
```

Could not open the file /usr/share/doc/libcairo2/README.gz.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

```

In places>search-for-files I search for cairo-clock and get this result...
```

cairo-clock.desktop /usr/share/app-install/desktop
cairo-clock.png     /usr/share/app-install/icons

```

I can view the icon file but the desktop file give the following error...
```

Could not open document cairo-clock.desktop.
There is no install viewer capable of displaying the document.

```

I have had no trouble viewing documents till now.

EDIT::
I now have it set up in session to start when I boot up.

---

### Post by BigCityCat on 2009-01-18
I am relatively new to linux but the way I got my cairo clock to start up where I wanted it to. Was to download the style of cairo clock I wanted from.... 

[http://www.gnome-look.org/index.php?xcontentmode=186](http://www.gnome-look.org/index.php?xcontentmode=186)

Extract it to the desktop.

Go to the command line and type gksudo nautilus. A file browser with root privileges will pop up. Navigate to usr/share/screenlets/clock/themes. Then copy and past the style of cairo clock file that you downloaded and extracted into that file.

If you don't have screenlets just download it. Then just open screenlets and select the clock. Check mark start stop and auto start. The when the clock pops up you can move it, size it, theme it and all that.

I hope this helps.

I just remembered. If you have cairo clocks installed. You can just navigate to usr/share/cairoclocks and copy the clocks from there and then just navigate to usr/share/screenlets/clocks/themes and paste. then do the other steps. At least save you from having to download them.

---

### Post by BigCityCat on 2009-01-18
I know you want to edit your cairo clock files and you can do that with the same command a gave you but I know that there is a quirk with auto starting cairo clock from the program itself. I bypassed all of that by putting the style of clock I wanted into screenlets because screenlets does not have that problem.

I remember the problem I had was. If you go to sessions and add new and write the command cairo-clock, it will start up, but always on the left side and I couldn't figure out how to make it start where I wanted to so I used the work around and it works better anyway.

---

### Post by sofasurfer on 2009-01-18
I installed screenlets and the cairo-clock theme. And I just found out how to change the appearance by switching the .svg files in the themes directory. I think I might even try editing them now that I know how they work. Cool!!

---

### Post by BigCityCat on 2009-01-18
So this solution worked for you?

---

### Post by misswham on 2009-08-13
I am trying to download new cairo clock themes and I am trying to follow the instructions above.  What is a command line?  I assume it is the terminal so I posted that command in the terminal and this is what i got

is a browser folder that says root then a desktop folder that is empty.  I see a lot of cairo clock themes on gnome look site just dont know how to download them and i have done a lot of research can anyone help.

---

