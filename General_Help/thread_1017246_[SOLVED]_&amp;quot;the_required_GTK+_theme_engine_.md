---
title: "[SOLVED] &amp;quot;the required GTK+ theme engine is not installed&amp;quot;???"
date: 2008-12-20
forum: General Help
---

### Post by Roger Allott on 2008-12-20
I've been playing around with some themes this evening and downloaded / installed some stuff from Gnome Art.

One that I particularly like is Aero, which is a glassy-metalic black controls arrangement. However, when I click on it in the Appearance > Customise > Controls screen, I get the message:

```
This theme will not look as intended because the required GTK+ theme engine is not installed.
```

So I pootled along to Synaptic to see what it had in the way of GTK+ theme engines and was a tad baffled by there being quite a few from which to choose. What's the difference between GTK+ and GTK2, for instance?

Has anyone got any idea as to which package(s) I should download and install to get that controls effect operational?

Whilst I'd like to have Aero sometime, I'm making do for the moment with a particularly 'in your face' set of controls called MardiGrasDeux-gtk2. It installed without trouble or error message and all programs inherit the theme as far as I can tell, except for Synaptic, which reverts to a very bland grey arrangement.

Is that likely to be a bug in Synaptic or an error in the theme? Whatever, how might I be able to rectify it?

---

### Post by binbash on 2008-12-20
link to the theme page, so we can tell the engine

---

### Post by Roger Allott on 2008-12-20
> **binbash said:**
> link to the theme page, so we can tell the engine

I've no idea where a theme page might be, as I downloaded and installed them using System > Preferences > Art Manager.

There is of course the GNOME Art website listing various controls themes at [http://art.gnome.org/themes/gtk2]("http://art.gnome.org/themes/gtk2"), but I see that neither of the ones I'm discussing are shown there.

---

### Post by Ivo Moelans on 2008-12-21
Maybe this could help: [http://ubuntuforums.org/showpost.php?p=6130341&postcount=4]("http://ubuntuforums.org/showpost.php?p=6130341&postcount=4")

---

### Post by Roger Allott on 2008-12-21
> **binbash said:**
> link to the theme page, so we can tell the engine

Aha, I've now found a webpage that covers the Aero theme.

[http://themes.freshmeat.net/projects/aero/]("http://themes.freshmeat.net/projects/aero/")

---

### Post by Roger Allott on 2008-12-21
> **Ivo Moelans said:**
> Maybe this could help: [http://ubuntuforums.org/showpost.php?p=6130341&postcount=4]("http://ubuntuforums.org/showpost.php?p=6130341&postcount=4")

Thanks. I've looked at the file suggested by that post (gtkrc) and in the comments section at the top it says:

```
Depends on GTK+ 2.x and pixmap engine
```

The problem I've still got though is that there seem to be numerous packages in Synaptic that are described as GTK2 engines!

---

### Post by Vadi on 2008-12-21
I think pixmap engine is built in. It's giving a warning for no reason, as the screenshot and what I get looks the same really

---

### Post by Roger Allott on 2008-12-21
> **Vadi said:**
> It's giving a warning for no reason, as the screenshot and what I get looks the same really

Ah, thanks for testing it. Indeed, when I try adding Aero the applications running at the time all seem to inherit the style. So why give the warning??? Seems a bit daft to me.

Have you tried applying the theme and then seeing whether Synaptic inherits it as well? For some bizarre reason Synaptic doesn't inherit theme styles of any theme I download, but instead has a style that's very bland.

I've tried a few other progs to see if they inherit a new theme. All of those I've tried so far do inherit it OK, but Synaptic is the only one that doesn't.

---

### Post by Vadi on 2008-12-21
Applications that are started by root won't get the style, you mean.

This will help you: [http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

---

### Post by Roger Allott on 2008-12-21
> **Vadi said:**
> Applications that are started by root won't get the style, you mean.

This will help you: [http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

That does indeed fix the problem! Many thanks.

---

### Post by Vadi on 2008-12-21
You're welcome. Click on 'Thread Tools' and 'Mark Thread as Solved'

---

### Post by BazookaAce on 2009-01-10
Hi, 

The link provided by Vadi does not work in my terminal. When i'm trying 

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

Nothing happens. I also tried this; 

```
mv ~/.themes/* /usr/share/themes
```

But all i'm getting then is, ```


steffen@steffen-laptop:~$ mv ~/.themes/* /usr/share/themes
mv: cannot move `/home/steffen/.themes/Black-Diamond' to `/usr/share/themes/Black-Diamond': Permission denied
mv: cannot move `/home/steffen/.themes/BlackWhite' to `/usr/share/themes/BlackWhite': Permission denied
mv: cannot move `/home/steffen/.themes/Dust' to `/usr/share/themes/Dust': Permission denied
mv: cannot move `/home/steffen/.themes/Dust Aurora' to `/usr/share/themes/Dust Aurora': Permission denied
mv: cannot move `/home/steffen/.themes/Dust Bordered' to `/usr/share/themes/Dust Bordered': Permission denied
mv: cannot move `/home/steffen/.themes/Dust Burnt' to `/usr/share/themes/Dust Burnt': Permission denied
mv: cannot move `/home/steffen/.themes/Dust Sand' to `/usr/share/themes/Dust Sand': Permission denied
mv: cannot move `/home/steffen/.themes/gnome-theme--1298214448.gtp' to `/usr/share/themes/gnome-theme--1298214448.gtp': Permission denied
mv: cannot move `/home/steffen/.themes/gnome-theme--1753184875.gtp' to `/usr/share/themes/gnome-theme--1753184875.gtp': Permission denied
mv: cannot move `/home/steffen/.themes/gnome-theme--2121894028.gtp' to `/usr/share/themes/gnome-theme--2121894028.gtp': Permission denied
mv: cannot move `/home/steffen/.themes/Laza' to `/usr/share/themes/Laza': Permission denied
mv: cannot move `/home/steffen/.themes/Moomex-Ultimatum' to `/usr/share/themes/Moomex-Ultimatum': Permission denied
mv: cannot move `/home/steffen/.themes/Neutronium DeepBlack' to `/usr/share/themes/Neutronium DeepBlack': Permission denied
mv: cannot move `/home/steffen/.themes/willibex' to `/usr/share/themes/willibex': Permission denied
mv: cannot move `/home/steffen/.themes/willibex_brown' to `/usr/share/themes/willibex_brown': Permission denied

```

I've already tried this command as root, but it won't work. What am i doing wrong?

Please help me ;)

---

### Post by Vadi on 2009-01-10
Nothing should happen (well, I mean it doesn't say "command done successfully"), but after you do that and restart Synaptic, the theme should be applied.

---

### Post by BazookaAce on 2009-01-10
Yeah, i noticed that. But when i'm applying a theme it still says "GTK+ theme engine is not installed". Should it?

---

### Post by Vadi on 2009-01-10
Yeah. Do you know what gtk engine it wants?

---

### Post by BazookaAce on 2009-01-10
This is what it says: 
> 
This theme will not look as intended because the required GTK+theme engine is not installed

---

### Post by Vadi on 2009-01-10
Which theme is it? Have a link to where you got it from by chance?

---

### Post by BazookaAce on 2009-01-10
Here yo go! [http://gnome-look.org/content/show.php/BlackWhite?content=68803](http://gnome-look.org/content/show.php/BlackWhite?content=68803)

---

### Post by Vadi on 2009-01-10
That engine is already installed with Ubuntu by default, so you can ignore the warning. Dunno why it comes up.

Applying the theme made it resemble the screenshots provided, so I think you're OK.

---

### Post by Ivo Moelans on 2009-01-10
Go to */home/<username>/.themes/BlackWhite/gtk-2.0*. Open the file *gtkrc* with text editor.
Go to line 1727 where is says

```
engine ""
```

change that to

```
engine "pixmap"
```

Save the file and reload your theme.

For a more complete explanation see _[here]("http://ubuntuforums.org/showpost.php?p=6148824&postcount=14f")_

---

### Post by BazookaAce on 2009-01-10
Thanks guys :)

But the strange thing here is that under "Engine", in the textfile, it already says "Engine Pixmap" :confused:

Sooo... Then, i'm really lost.. 

But screw it. I don't NEED to use that theme! I can make it so it's nearly the same as the original. I'm skeptical about that, but i don't want you guys to use your free time on this cr@p ;) 

I'll survive! :)

---

### Post by pelle.k on 2009-02-12
Use grep to show *what* line (there are probably more than one) is missing the "<value>".
```
grep -n engine /home/<username>/.themes/BlackWhite/gtk-2.0
```
If you use gedit you can show line numbers (preferences menu), but you can also see what line you're on at the bottom-right of gedit as well (statusbar). As for using nano, ctrl+c will show what line number you're on.

---

### Post by BazookaAce on 2009-02-12
I managed to make it work. I'm using GTK-ChTeme now. It's much better then the buildt-in "appearance"-thingy :)

---

### Post by burntresistor on 2009-04-02
I'm trying to make a custom theme using Kreski -Lines-  [http://art.gnome.org/themes/icon?page=2](http://art.gnome.org/themes/icon?page=2) it says I need gtk+ theme engine. I tried looking in packet manager but just found variations no one file. I'm using unbuntu 8.10

---

