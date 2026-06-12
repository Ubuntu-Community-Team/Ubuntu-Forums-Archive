---
title: "How to install new theme ?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by stonex on 2006-03-06
I'v download theme from net and unpack it into home folder . Now there is folder and some files in it . How to install.? Which file ?

---

### Post by risp on 2006-03-06
[QUOTE=stonex]I'v download theme from net and unpack it into home folder . Now there is folder and some files in it . How to install.? Which file ?[/QUOTE]

System -> Preferences -> Theme -> Install theme, and then choose the *compressed* file you downloaded.

---

### Post by Sutekh on 2006-03-06
Open up the **Themes** entry in the **Sytem** -> **Preferences** Menu

Then drag the theme.tar.gz into the window and it will install the new theme for you.

---

### Post by stonex on 2006-03-06
Thanks !

---

### Post by audax321 on 2006-03-06
Just a warning though. If you have a theme with multiple directories inside of it the drag method will only install the first folder it extracts. It's better in that case to just manually extract the file to /home/<your-username>/.themes

If you need some clarification, most themes are packaged like this:

theme.tar.gz
|__ theme folder in theme.tar.gz

But in some instances, they are packaged like this:

theme.tar.gz
|__ theme1 folder in theme.tar.gz
|__ theme2 folder in theme.tar.gz
|__ theme3 folder in theme.tar.gz

In the second instance you need to manually extract it to get all the themes in the compressed archive installed. Otherwise you'll only have theme1. Hope that wasn't too confusing :)

---

### Post by stonex on 2006-03-06
I'v try but it fails. When I try to drag or install into themes window I got message : Error " The file format is invalid " . 
It is package tar.gz from [www.gnome-look.org](www.gnome-look.org) ( themes " Edge greeter 1 " and " Manzana tux " ). Some bug maybe !?

---

### Post by Sutekh on 2006-03-06
[QUOTE=audax321]
In the second instance you need to manually extract it to get all the themes in the compressed archive installed. Otherwise you'll only have theme1. Hope that wasn't too confusing :)[/QUOTE]
Actually that makes good sense, and resolves some issues for themes I use, which have multiple colours.

stonex, you should extract the theme to /home/<username>/.themes as suggested above

---

### Post by stonex on 2006-03-06
First , in ONE package tar.gz is ONE theme . If I unpack that tar.gz into Home/stonex/themes , than I have one folder which contains a few files ( jpg , bmp etc. ) but then I can't do anything !
When I trying to install packeged theme onto system>preferences>themes>install new theme   or just drag into themes window there's error window " The file format is invalid " !  :(

---

### Post by Sutekh on 2006-03-06
Ok I think I found the themes

Are these the ones?

[http://www.gnome-look.org/content/show.php?content=27460]("http://www.gnome-look.org/content/show.php?content=27460")

[http://www.gnome-look.org/content/show.php?content=24128]("http://www.gnome-look.org/content/show.php?content=24128")

They are actually themes for your *Login Screen* not the desktop

Instead Open **Login Screen Setup** in **System** -> **Administration** and Install the theme there.

Like in this pic [http://shots.osdir.com/slideshows/slideshow.php?release=469&slide=35]("http://shots.osdir.com/slideshows/slideshow.php?release=469&slide=35")

Edit: audax :cool: didn't know about the GTK 2.x stuff, cheers!

---

### Post by audax321 on 2006-03-06
Okay, your themes won't work because they are GDM themes (apply only to the log-in screen). To install these go to System > Administration > Login Screen Setup. Then click the THEMED GREETER tab and use the Install Theme button.

The themes for Gnome itself are called GTK themes for the widgets (buttons, listboxes, etc.) and Metacity (for the window border only). Most themes on Gnome-look listed under GTK 2.x will include both a GTK and Metacity. These you extract to /home/<username>/.themes (make sure it is .themes and not just themes ... the dot is very important. The dot makes folders hidden, to see them, in Nautilus go to View > Show Hidden Files (or CNTRL+H).

EDIT: Sutekh, looks like you beat me to it :)

---

### Post by stonex on 2006-03-06
Thanks a lot . I'v been blind 'till now . Thanks again !  :)

---

### Post by ComplexNumber on 2006-03-06
there isn't much to know about gnome themes.

**GDM themes** - these go in /usr/share/gdm
these are  for the login mamager

**gtk themes** - these go in /usr/share/themes
many gtk themes contain the gtk theme, the metacity theme, and a index.theme file. sometime they may just contain the gtk2 and gtk1 theme. sometime they may contain the gtk2 themes and a metacity theme without an index.theme file. when you go to themes section in the gnome control centre, you will see some themes on the left hand side. **these are themes that contain, and are defined by, an index.theme file**. and this file contains the name of the theme(eg Clearlooks-DarkOrange), what gtk theme is used, what metacity theme is used, and what icon theme is used. you can easily create your own themes using this file. for example, suppose that you want to create a theme called 'DarkBlue', you would creat a directory in /usr/share/themes called DarkBlue. then create an index.theme file (i usually just get hold of another index.them file from another theme and copy it to use as a template). place the index.them file in the DarkBlue directory. suppose also that you want to use Tango icons, Clearlooks-DarkBlue gtk theme and Hierbia metacity theme. this is an example of what the index.theme file would look like:

[COLOR=RoyalBlue][I][Desktop Entry]
Name=DarkBlue
Type=X-GNOME-Metatheme
Comment=My made up dark blue theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Clearlooks-DarkBlue
MetacityTheme=Hierbia
IconTheme=Tango
[/I]
 [COLOR=Black]notice that if you go to the icon directory, the name of the tango icons are called 'Tango'. if you put 'tango', the icons won't be found.  same for the metacity and gtk themes. note that they are case sensitive.[/COLOR][/COLOR]


**metacity themes** - these go in /usr/share/themes
occassionally, metacity themes sometime come with the metacity theme and an index.theme file.


**icon themes** - these go in /usre/share/icons




its actually really straightforward.

---

### Post by stonex on 2006-03-06
Thanks again , I did it anyway !

---

### Post by ComplexNumber on 2006-03-06
[quote=stonex]Thanks again , I did it anyway ![/quote]
ahh well. i suppose you or anybody else could use what i've written there to create your own themes or whatever.

---

### Post by stanz on 2006-03-06
Hi All,
 Yes~ & Thanks much, ComplexNumber!
Thats a great cut&paste or printout for me...as i am still in the 'trash & reinstall', stage, of my learning Linux.
Nicely detailed and explained!!
Thanks again *

---

### Post by cherry316316 on 2008-01-22
ok , when i goto "System-> Preference -> Apperance"
I install the theme from there . and it says the theme was correctly installed,

But now I want to use it. and its not showing in Apperance with other themes (default themes).  

I check for the folder
/home/<username>/.theme 
and the theme which i installed was there 
but for some reason i am not able to use it :((

---

### Post by saverjack on 2008-05-31
i didnt find any option as themes in system>>preferences 
help me out

---

