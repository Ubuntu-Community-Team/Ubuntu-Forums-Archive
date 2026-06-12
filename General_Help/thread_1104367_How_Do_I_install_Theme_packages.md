---
title: "How Do I install Theme packages"
date: 2009-03-23
forum: General Help
---

### Post by SINNISTER on 2009-03-23
Hey

I reali want to install theme packages to give my ubuntu that different spark

Could you please help me out

Thanx alot

---

### Post by oldos2er on 2009-03-23
[https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy)

---

### Post by Nano_ext3 on 2009-03-23
go to
> [http://www.gnome-look.org](http://www.gnome-look.org)

Download anything listed in the "gtk2.x" category, as you are most likely using the "2nd" version of GTK.  This, for instance is my theme: 
> [http://gnome-look.org/content/show.php/Darker+theme?content=32768](http://gnome-look.org/content/show.php/Darker+theme?content=32768)

Most theme's will be packaged as ".so" files.  For that theme I used I did have to "unzip" or "untar" the folder to get the .so file.  Once you have that .so file, go to System > Preferences > Appearance.  Go to Theme, and click install.  Now find your **THEME.so** file and open it.  It should now had added that theme in the main "theme" tab for you to select.

Cheers!

_Nano

---

### Post by SINNISTER on 2009-03-24
hey

OK well i downloaded the files from the site that i was given 

NOW how do i actually get the theme to show up on my theme manager coz it wants a .theme file and the themes i downloaded they dont have a .theme file in the theme, just all the files are seperat and i have no clue on how to covert all those loose files into My theme

HELP please

---

### Post by James_Lochhead on 2009-03-24
For a lot of themes (the ones packages as .tar.gz and tar.bz2) you can just download and then drag and drop into the System > Preferences > Appearance window.

---

### Post by mcduck on 2009-03-24
> **SINNISTER said:**
> hey

OK well i downloaded the files from the site that i was given 

NOW how do i actually get the theme to show up on my theme manager coz it wants a .theme file and the themes i downloaded they dont have a .theme file in the theme, just all the files are seperat and i have no clue on how to covert all those loose files into My theme

HELP please

Now, what is this "theme manager" you are talking about? And what theme did you download?

To install a GTK2, Metacity or icon theme, go to System/Preferences/Appearance and drag&drop the .tar.gz package to the window.

To Install a Emerald theme go to System/Preferences/Emerald Theme Manager, click the "Import"-button and find your theme file (.emerald) (you need to have desktop effects enabled and Emerald & Emerald Theme Manager installed to use these)

GDM themes are installed in System/Administration/Login Window.

---

### Post by Nano_ext3 on 2009-03-24
When you click "install" in Appearance, that .so is a theme file.  Just point to that file and click install.

Cheers

_Nano

---

### Post by mcduck on 2009-03-24
> **Nano_ext3 said:**
> When you click "install" in Appearance, that .so is a theme file.  Just point to that file and click install.

Cheers

_Nano

Seriously, what OS/Desktop are you running? ;)

I'm yet to find anything in Gnome (apart from USplash themes) that would come as .so file..

Gnome's themes are simple .tar.gz packages containing a theme directory with all necessary files and images. When installed through GUI the package shouldn't be extracted, but it is possible to just extract it's contents directly into the themes directory (~/.themes or /usr/share/themes). Emerald themes are the same, only the package has been renamed to ".emerald".

---

### Post by Nano_ext3 on 2009-03-25
My apologies, its a tar.gz file you click "install" on, I was having a bad day, you can understand right?  .so files are for "usplash" themes or "bootup themes".  [www.gnome-look.org](www.gnome-look.org)

---

### Post by mcduck on 2009-03-26
> **Nano_ext3 said:**
> My apologies, its a tar.gz file you click "install" on, I was having a bad day, you can understand right?  .so files are for "usplash" themes or "bootup themes".  [www.gnome-look.org](www.gnome-look.org)

No problem, that's what I was thinking about. :)

(By the way, I recommend using Startup Manager to install Usplash & Grub themes.)

---

### Post by Nano_ext3 on 2009-03-26
Yes , startup manager is excellent, its in Add/Remove

---

### Post by SINNISTER on 2009-03-27
Thank You Guys So much I finally got it installed

Man O man what would i Do without all you Guys I probbly would have Pulled my hair out long time ago :D

---

### Post by Nano_ext3 on 2009-03-27
Your quite welcome :)

---

### Post by jotavrj on 2009-03-27
Install emerald, compiz and compiz-fusion.
Then, go to gnome-look .org, download some themes and apply in the emerald theme.

If you r looking forward to a very good theme (and a theme that DOES NOT need the emerald-theme manager, search for GLASSY BLEU or HP MINI THEME in Google. That's REALLY great and i use it.

---

### Post by Nano_ext3 on 2009-03-29
Already suggested my friend , see above simply replying to a thread to up your post count (now at 5), is a little shallow or you did read any of the replies lol.  Either way be careful when posting :)

---

