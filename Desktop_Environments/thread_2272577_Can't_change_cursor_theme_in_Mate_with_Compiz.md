---
title: "Can't change cursor theme in Mate with Compiz"
date: 2015-04-07
forum: Desktop Environments
---

### Post by Tuxclear on 2015-04-07
Hello everyone! I've installed Ubuntu 12.04 with Mate and Compiz as a Window Manager. The problem is that I can't change certain cursor themes in no way! For example I want to use Griffin Embers Cursors, but whenever I add this value on any editor, I get a simple black cursor. If I use the ```
update-alternatives --config x-cursor-theme
``` command it doesn't list the theme anywhere.

This thing drives me mad for a few hours .](*,) Any helpful advice is appreciated.

---

### Post by CantankRus on 2015-04-07
A downloaded cursor theme needs to be installed to alternatives first for you to be able to choose it.
If it's [**_[COLOR="#B22222"]this theme[/COLOR]_**]("http://gnome-look.org/content/show.php/Griffin+Embers+Cursors?content=100252") you will need to create a cursor.theme file.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2221942&p=13028225#post13028225").

I tried to test this cursor theme but I couldn't get it to display the correct pointer.
I renamed the theme (Griffin-Embers) without spaces and created a cursor.theme file and it now works.
Try the attached theme.
Download and extract.
Move the Griffin-Embers folder to **/usr/share/icons**.

Then run...
```
CURSOR=Griffin-Embers
```
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme 20
```
```
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme
```

---

### Post by Tuxclear on 2015-04-08
Thank you a lot, that worked! But how can someone create a custom cursor.theme file?

---

### Post by CantankRus on 2015-04-08
The link I posted earlier explains.
Namely this [**_[COLOR="#B22222"]post#7[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2221942&p=13018154#post13018154")
If you navigate to **/usr/share/icons/DMZ-White** you can see how a theme folder should look.

After downloading a theme, extract, create a cursor.theme file if necessary and then move the theme folder to **/usr/share/icons**
Run the 3 commands shown using your theme's name in the first command and log out and back in.

Go to [**_[COLOR="#B22222"]gnome-look.org[/COLOR]_**]("http://gnome-look.org/index.php?xcontentmode=36") and use [**_[COLOR="#B22222"]the forum post[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2221942&p=13028225#post13028225") as a guide when downloading and installing a theme.
You'll find most of the recent themes are created with cursor.theme files so you just need to 
extract, move folder and run the 3 commands....logout back in....done.

---

### Post by Tuxclear on 2015-04-08
Yeah, I'm sorry. I was looking on the wrong page. Anyway, thank you for everything!

---

