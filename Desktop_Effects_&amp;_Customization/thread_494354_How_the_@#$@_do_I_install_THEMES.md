---
title: "How the @#$@ do I install THEMES????"
date: 2007-07-06
forum: Desktop Effects &amp; Customization
---

### Post by Fenryr on 2007-07-06
Ok, this is really beginning to annoy me...I'm following the instructions in the bloody 'help' file in the Gnome theme manager, and I keep getting 'invalid file format' messages no matter WHAT...These are tar.gz files, as SPECIFIED, downloaded from a theme site I found in THIS forum, saved to disk, properly pointed to from inside the program, and the *won't install!!!*

C'mon, if you want this thing to compete with WinBlows, can't you make ONE THING friggin' SIMPLE??? Why does every damn thing in Ubuntu have to be such a PITA??? MOST users want things to WORK, they don't want to have to tweak everything every time they turn the bloody MACHINE on!

Ok, rant over...Seriously, though, someone care to tell me what I'm getting wrong? As I said, I'm following the directions, I read the f***ing manual, and this thing still won't install any new themes...I even RE-installed the THEME manager, ferchrissake...

---

### Post by Gremlinzzz on 2007-07-06
[http://www.msccompcasts.com/2005/05/how-to-install-themes.html](http://www.msccompcasts.com/2005/05/how-to-install-themes.html)

---

### Post by crimesaucer on 2007-07-06
If you have unpacked a theme into your home folder, then you can move it to you /usr/share/themes folder while in sudo. 

If you have the correct theme engine installed for the theme to use, your new theme should now show in your "User Interface Settings", and you should just be able to select it just like the default Human theme.

the command I use to move my themes is:

```
sudo mv ThemeName /usr/share/themes
```

---

### Post by hyperair on 2007-07-07
Well installing themes for me has always been pretty easy, just drag and drop. Perhaps you are trying to install an invalid theme file? What's this theme you're trying to install anyway and where did you get it?

---

### Post by j.miller565 on 2007-07-07
maybe extract the tar.bz file and then after extraction, you may find another tar.bz file.
Now try to install the theme with the extracted file. 

Hope this works!! :)

j.miller565

---

### Post by S.Peterman on 2007-07-07
I also do it by dragging and dropping, give that a shot ;-)

---

### Post by llamakc on 2007-07-07
One thing that helps people HELP you is to provide a link to what it is that does not work for you.

For example, if I were having problems with installing a theme and had exhausted all of my options, I would include a link to the theme that does not work for me. I'd also tell folks which version of Ubuntu I am using.

---

### Post by TLD321 on 2007-07-20
I am just as frustrated as you are.

I'm using Fiesty Fawn. The themes I've tried to install are:

[http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791](http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791)

and

[http://www.gnome-look.org/content/show.php/Relaxing+Water?content=48213](http://www.gnome-look.org/content/show.php/Relaxing+Water?content=48213)


I have tried dragging and dropping, extracting the files to my .themes directory, unzipping and rezipping, naming it different stuff, using different file types, and every other suggestion I have ever encountered. None work.

so what the hell.

---

### Post by hyperair on 2007-07-20
Well you're obviously dragging those themes into the wrong place. Those are GDM themes, skinning your **_[color=red]Login Window**_[/color]. You were using the Themes window which skins your Gtk controls, such as scrollbars, textboxes, buttons and so on.

Open System->Administration->Login Window, and drag the theme in.

---

### Post by TLD321 on 2007-07-20
what's the difference between GTK 1.x and GTK 2.x

GTK 2.x themes give me the same error, invalid file format.

GTK 1.x installs correctly, but when I click on that theme, my comptuer crashes ^^

boy I'm really starting to LOVE ubuntu!

---

### Post by Gremlinzzz on 2007-07-20
[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

---

### Post by Gremlinzzz on 2007-07-20
Select login window from GNOME menu/ System/ Administration/ Login Window (you will be asked for the root password 
Pull the file GDM.SOMETHING.tar.gz file from the GDM folder into the Login Window and accept the installation. Choose your newly installed theme as default then log out from GNOME to see your new theme in other words drag it to the themes window ===the folder
:guitar:

---

### Post by Gremlinzzz on 2007-07-20
> **Gremlinzzz said:**
> Select login window from GNOME menu/ System/ Administration/ Login Window (you will be asked for the root password 
Pull the file GDM.SOMETHING.tar.gz file from the GDM folder into the Login Window and accept the installation. Choose your newly installed theme as default then log out from GNOME to see your new theme in other words drag it to the themes window ===the folder
:guitar:

correction NOT the folder the tar.gz package

---

### Post by Gremlinzzz on 2007-07-20
ok here it is  click system /administration/login window/click local tab/drag 52791-Deo-GDMTHeme.tar.gz  to the theme s window it will ask you if u want too install thats it.
:guitar:

---

### Post by jhernandez1270 on 2007-07-20
You can select themes from [www.gnome-look.org](www.gnome-look.org)...
If you don't have Compiz, beryl, or compiz fusion installed you won't be able to use those types of themes...(in my experience anyway)...

Until I installed Compiz-Fusion i typically chose GDM, GTK, GTK2, Metacity themes...those files ususally end in tar.bz and decompress to a usable format (i.e NOT .emerald theme)....and you should be able to go to System>Preference>Themes and install it from there.

hope this helps

---

### Post by TLD321 on 2007-07-20
okay I have a login screen theme...but I want a theme for my desktop, icons...you know...like windows >_>

---

### Post by hyperair on 2007-07-21
Go look around for a GTK theme.[http://www.gnome-look.org](http://www.gnome-look.org) is a good place to begin.

---

### Post by TLD321 on 2007-07-21
I tried, but I dont know if I need a GTK 1.x or a GTK 2.x theme O_o

so far only a GTK 1.x theme has installed correctly, and when I clicked it my computer 'sploded O_o

---

### Post by boob11 on 2007-08-13
Now try to install the theme with the extracted file.

---

