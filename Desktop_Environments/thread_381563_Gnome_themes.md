---
title: "Gnome themes"
date: 2007-03-11
forum: Desktop Environments
---

### Post by thypeacefrog on 2007-03-11
Okay. I've given up on fvwm because I realized you can just change your gnome theme. I'm wanting to change to this one [http://www.gnome-look.org/content/show.php?content=54395](http://www.gnome-look.org/content/show.php?content=54395)

It's a GTK+2.X theme/style.

This is the pic they give : [IMG]http://www.gnome-look.org/CONTENT/content-pre1/54395-1.jpg[/IMG]

Can someone tell me if the theme will make my gnome look exactly like that?

O and I tried opening system>preferences>themes I click install theme select the tar.gz file and it tells me it's been installed correctly but it doesn't come up on the list.

So is there a tutorial floating around on this subject that I haven't been able to find, or if it's a case of me needing GTK+2.X how do I do that? I've been trying but can't quite get it.

---

### Post by ComplexNumber on 2007-03-11
the icons will be different because the author has handpicked his own to match the theme. its not a complete icon set - its just icons that hes selected from many different themes in order to match the theme. thats how i understand it anyway.

 when i install Human_reloaded, mine looked mostly similar to that...but the theme is too similar to one by the same author called Field.....and i prefer Field.

---

### Post by thypeacefrog on 2007-03-11
So how did you actually install it though?

---

### Post by chavo on 2007-03-11
You also need to make sure you have the correct gtk2-engine installed. This theme uses the pixbuf engine, so apt-get install gtk2-engines-pixbuf. If you want to save yourself some trouble later on go ahead and install all of the engines. This way you'll be sure to have the correct engine when trying out some themes.

---

### Post by thypeacefrog on 2007-03-11
Like is it okay to use the tar.gz file or should I extract and use the result

---

### Post by ComplexNumber on 2007-03-11
> **thypeacefrog said:**
> Like is it okay to use the tar.gz file or should I extract and use the result
i don't know what you mean. if you're wanting to know where to install the actual theme, just extract it and place it in .themes in your home directory.



and yes, as chavo says, you need to install the actual theme engine that draws the theme. otherwise the theme is going to look very weird (ie all grey and not themed at all).

---

### Post by thypeacefrog on 2007-03-11
I'm trying to place it in the themes folder but it wont let me saying I don't have permission. How do I log in as sudo to be able to control it?

---

### Post by ComplexNumber on 2007-03-11
> **thypeacefrog said:**
> I'm trying to place it in the themes folder but it wont let me saying I don't have permission. How do I log in as sudo to be able to control it?
a normal user doesn't have permission to place themes in /usr/share/themes. you have to be root to place them there. you can either go to where the theme is and type the following on the commandline:
sudo cp -R <theme-name> /usr/share/themes

OR

you can do 'gksudo nautilus' on the commandlie and then copy and paste the theme from your home directory to /usr/share/themes





why don't you just place it in .themes in your home directory. note the "." before it - that means that its a hidden file. if you can't see hidden files in nautilus, fire up nautilus, then go to 'Edit', then 'Preferences' in the menu. then tick 'show hidden and bacup files'.

---

### Post by thypeacefrog on 2007-03-11
I did that and it's still just not working, they don't show up in my system>preferences>themes. I'm adding them exactly as I dl them (.tar and .tar.gz files) should I be doing something else? I also tried extracted folder but it still didn't work.

---

### Post by ComplexNumber on 2007-03-11
> **thypeacefrog said:**
> I did that and it's still just not working, they don't show up in my system>preferences>themes. I'm adding them exactly as I dl them (.tar and .tar.gz files) should I be doing something else? I also tried extracted folder but it still didn't work.
where did you put the theme?

---

### Post by thypeacefrog on 2007-03-11
In the .theme folder in my homefolder via cut and paste

---

### Post by ComplexNumber on 2007-03-11
so in your .themes directory, you should see Human_reloaded. is that correct? and when you open the contents of the Human_reloaded folder, you should see 2 directories(ie gtk-2.0 and metacity-1) and a index.theme file, right?.

---

### Post by thypeacefrog on 2007-03-11
Yes they're all there and so is a text file called Human_Reloaded.

---

### Post by ComplexNumber on 2007-03-11
then there is nothing wrong. it should show up on the left hand side in your theme manager. have a look in the controls tab for human_relaoaded.

---

