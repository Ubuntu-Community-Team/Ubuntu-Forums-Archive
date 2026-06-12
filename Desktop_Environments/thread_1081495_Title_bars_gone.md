---
title: "Title bars gone?"
date: 2009-02-26
forum: Desktop Environments
---

### Post by slammed87d21 on 2009-02-26
I know this has probably been posted before, but I've lost my window title bars after installing a theme. How do I get them back?

---

### Post by dbbolton on 2009-02-26
> **slammed87d21 said:**
> I know this has probably been posted before, but I've lost my window title bars after installing a theme. How do I get them back?
Which desktop environment are you using? (Gnome, KDE, Xfce, etc.)

---

### Post by slammed87d21 on 2009-02-27
Gnome

---

### Post by dbbolton on 2009-02-27
> **slammed87d21 said:**
> Gnome
See if you can reset the Metacity theme by going to System > Preferences > Appearance > Theme > Customize > Window Border

---

### Post by slammed87d21 on 2009-02-27
I just noticed in the Appearance Preferences windows, it says this theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed. Does this have anything to do with it? If so, where do I get it from?

---

### Post by dbbolton on 2009-02-27
> **slammed87d21 said:**
> I just noticed in the Appearance Preferences windows, it says this theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed. Does this have anything to do with it? If so, where do I get it from?
That shouldn't have to do with the window theme. But if you want, you can install the package called gtk2-engines-ubantu looks:
```
sudo aptitude install gtk2-engines-ubuntulooks
```By the way, what is the name of the theme you are trying to use? If you selected a preconfigured theme, it could be that it includes a window theme which you haven't installed.

---

### Post by slammed87d21 on 2009-02-27
Actually, I just realized that I didn't have the Fusion Icon running. I started it, and my title bars reappeared instantly. I'm using the Jaunty Human Green theme off [www.gnome-look.org](www.gnome-look.org). I finally got it set up properly, but how do I change the splash screen?

---

### Post by slammed87d21 on 2009-02-27
Also, this is the only theme I've seen do this, but in Pidgin, or any open window, the text is unreadable unless its highlighted. I can't figure out how to fix that too.

---

### Post by dbbolton on 2009-02-27
> **slammed87d21 said:**
> Actually, I just realized that I didn't have the Fusion Icon running. I started it, and my title bars reappeared instantly. I'm using the Jaunty Human Green theme off [www.gnome-look.org](www.gnome-look.org). I finally got it set up properly, but how do I change the splash screen?
I have noticed that the window decorations sometimes don't show up when using fusion-icon (even on Hardy and Intrepid)

Could you post a screenshot of the Pidgin window, and a link to where you got the theme?

---

### Post by slammed87d21 on 2009-02-27
Theme link - [http://www.gnome-look.org/content/show.php/Jaunty+Human+Green?content=100022]("http://http://www.gnome-look.org/content/show.php/Jaunty+Human+Green?content=100022")

Screenshot of Pidgin - [IMG]http://4.bp.blogspot.com/_NXuUygTHqi4/SagQIZ8Q9jI/AAAAAAAAANM/uYZiRyr87s0/s1600/Screenshot.png[/IMG]

---

### Post by Therion on 2009-02-27
I'm assuming you're running Compizfusion. 

If so, make sure the "Window Decoration" is enabled in the Effects section of the Compiz Config Settings Manager.

Next, go to Preferences/Sessions and add a new entry with the command **compiz --replace**.

This should solve your title-bars issue.

---

### Post by dbbolton on 2009-02-27
> **slammed87d21 said:**
> Theme link - [http://www.gnome-look.org/content/show.php/Jaunty+Human+Green?content=100022]("http://http://www.gnome-look.org/content/show.php/Jaunty+Human+Green?content=100022")

Screenshot of Pidgin - [IMG]http://4.bp.blogspot.com/_NXuUygTHqi4/SagQIZ8Q9jI/AAAAAAAAANM/uYZiRyr87s0/s1600/Screenshot.png[/IMG]
This link is for a GDM (login screen) theme. Your applications like Pidgin use GTK themes.

Also, the screenshot isn't showing up.

---

### Post by slammed87d21 on 2009-02-27
Is there a way I can just change my font color?

---

### Post by slammed87d21 on 2009-02-27
[IMG]http://4.bp.blogspot.com/_NXuUygTHqi4/SagQIZ8Q9jI/AAAAAAAAANM/uYZiRyr87s0/s1600/Screenshot.png[/IMG]

---

### Post by dbbolton on 2009-02-27
> **slammed87d21 said:**
> Is there a way I can just change my font color?
The font color is determined by the gtkrc file of the current Gtk theme. If the current theme has an unlocked color scheme, its colors can be edited with Gnome Color Chooser.

---

### Post by slammed87d21 on 2009-02-27
> **dbbolton said:**
> This link is for a GDM (login screen) theme. Your applications like Pidgin use GTK themes.

Also, the screenshot isn't showing up.

Also, I tried over a dozen GTK themes, and none are useable. Says not a theme file. But most of the same GTK themes work on my desktop.

---

### Post by dbbolton on 2009-02-27
> **slammed87d21 said:**
> Also, I tried over a dozen GTK themes, and none are useable. Says not a theme file. But most of the same GTK themes work on my desktop.
If a theme isn't packaged a certain way, you have to install it manually. The key is the folder structure. Gnome will look for themes in /usr/share/themes/ and ~/.themes/ (~ being your home folder). Inside those folders, the theme's "gtkrc" file must be in a folder called gtk-2.0 which is inside a folder with the theme's name. For example:

```

~/.themes/ExampleTheme/gtk-2.0/gtkrc

```So if you want to manually install a theme, you can extract the archive it's in and then move the folder containing the gtk-2.0 folder to ~/.themes

---

### Post by slammed87d21 on 2009-02-27
Ah. That's good to know.

---

### Post by slammed87d21 on 2009-02-27
Ok. I just finished installing a GTK theme. I can actually read text now, even though everyhting seems to have a grey background with white text. But it works. With this theme, it has icons that need to be installed, but I'm not completely understanding where they go. Also, in the appearances window, it now says the required GTK engine isn't installed, but does not say which. Here's the link to the theme. [http://www.gnome-look.org/content/show.php?content=80092&forumpage=0]("http://www.gnome-look.org/content/show.php?content=80092&forumpage=0")

---

### Post by dbbolton on 2009-02-27
After you extract the archive, there should be a folder called "80092-Black Plastic 2". Open it. You should see a file called "icons.tar.gz". Now extract it. This will create a folder called "icons" containing the icon files that were mentioned in the theme description. He was suggesting that you can use them to replace some icons in an existing icon theme. Icon themes are found in ~/.icons/ 

The only engine this theme requires is "pixmap", which you can get by installing the package called "gtk2-engines-pixbuf".

The GTK engine error is likely due to line 1472 of the gtkrc file, which says:
```
{ engine "" { } }
```There is no Gtk engine called "", so you aren't missing anything. The author probably did this intentionally, so I wouldn't be too worried about it.

---

### Post by Therion on 2009-02-27
This page might help you get a handle on how to modify your Ubuntu install. 

For a quick start though, look under the "Customize" button of the Appearance manager/Theme tab.  

It's an easy thing to overlook and presents you with a LOT of options for tweaking any currently installed theme.

For more see this page: [http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/)

Go nuts.

---

