---
title: "Help with Feisty and Murrine"
date: 2007-05-17
forum: Desktop Environments
---

### Post by ironfistchamp on 2007-05-17
Hey all

Man I feel dumb asking about this but I just installed Feisty (upgrade borked something terrible) and I had a look at the Murrine GTK engine. The themes for it look amazing so I tried to get it installed. I downloaded a whole mess of crap. I got the engine from the repos, the gtk theme and the metacity theme. I put them where I thought they had to go but I couldn't get them to show up on the theme window. I installed the Murrine Configurator and guessed what the buttons meant as they still seem to be in Italian. Never mind. That got things moving but I am still stuck with my box looking like Human with green paint on it. 

I also tried building Murrine engine from source but it complained that I don't have GTK+-2.8 on my system. I looked in the repos and couldn't see anything.

Can anyone help me get this thing of the ground?

Thanks

Ironfistchamp

---

### Post by blackened on 2007-05-18
Getting Murrine working on Feisty is easy now (easier than on Edgy). All you should have to do is sudo apt-get install gtk2-engines-murrine, then download a theme and either drag-n-drop it onto the themes dialog (System -> Preferences -> Theme) or extract it to /home/*username*/.themes (or /usr/share/themes if you want it accessible to all users).

---

### Post by mikecon on 2007-06-09
I must admit to feeling equally dumb.
*(Sorry for jumping in on your thread, but it seemed a good idea to collect answers in one place)*

I've installed Murrine first using Synaptic and then using sudo (having first removed the original install via Synpatic), I haven't yet seen a menu item in System --> Preferences (which I'm sure I read that I should get).

I have extracted the Murrina Theme Pack into usr/share/themes and suing the standard Theme Preferences dialogue I can select the Murrina Themes in Customize --> Controls but that's the only place anything Murrine like shows up. I certainly don't get the Murrine dialogue boxes that appear on the Murrine home page.

Not really sure what to do next, any help would be greatly appreciated.

Mike

---

### Post by mcduck on 2007-06-09
> **mikecon said:**
> I must admit to feeling equally dumb.
*(Sorry for jumping in on your thread, but it seemed a good idea to collect answers in one place)*

I've installed Murrine first using Synaptic and then using sudo (having first removed the original install via Synpatic), I haven't yet seen a menu item in System --> Preferences (which I'm sure I read that I should get).

I have extracted the Murrina Theme Pack into usr/share/themes and suing the standard Theme Preferences dialogue I can select the Murrina Themes in Customize --> Controls but that's the only place anything Murrine like shows up. I certainly don't get the Murrine dialogue boxes that appear on the Murrine home page.

Not really sure what to do next, any help would be greatly appreciated.

Mike

Installing Murrine is not supposed to add anything into your menus. Murrine themes are selected and used just like any other GTK2 themes, through the Theme manager in System/Preferences/Theme.

I'm not sure what dialogue boxes you are talking about. I suppose you are talking about Murrine Configurator, which is a separate tool and not part of the Murrine theme engine itself. Ifyou install it, it appears in System/Preferences/Murrine Configurator. Also, you can only use it to edit Murrine themes stored in your own theme folder (~/.themes). Modifying themes stored in /usr/share/themes would require starting Murrine Configurator with root privileges.

By the way, installing with Synaptic is exactly the same thing as installing from command line with apt-get. Synaptic is just a graphical frontend for apt-get.

---

### Post by MilchFlasche on 2007-06-11
> **mcduck said:**
> I'm not sure what dialogue boxes you are talking about. I suppose you are talking about Murrine Configurator, which is a separate tool and not part of the Murrine theme engine itself. Ifyou install it, it appears in System/Preferences/Murrine Configurator. Also, you can only use it to edit Murrine themes stored in your own theme folder (~/.themes). Modifying themes stored in /usr/share/themes would require starting Murrine Configurator with root privileges.

No, I don't think he was referring to the Murrine Configurator. I also thought that after I have put some theme folders under ~/.themes I would be able to choose directly from System/Preferences/Themes, but actually they are only available in the "Customize...", "Control". Then I realized that a GNOME theme is composed of four parts of styles: "control", "color", "border", and "icons", and Murrine themes seems only to affect the "control" part. After choosing a Murrine theme for the control style and choosing other styles for border and icons, then such a bundle could be saved and named, thus be chosen directly in the Themes dialog.

Please instruct me if I have misunderstood the mechanism :o

---

### Post by mikecon on 2007-06-13
It was the Murrine Configurator, but I didn't know that at the time.
I also agree with with MilchFlasche that Murrine themes only seem to affect the Control part, but why then are they called themes?
*(I have some issues installing the configurator, but I'll keep trying and ask that question separately if I can't finish it successfully)*

Now, I think I'm starting to get my head around how this all hangs together, the architecture if you will.

Kernel
--> Shell
-----> X Windows
--------> GUI, e.g.
-----------> KDE (Qt)
--------------> I assume KDE has Window Managers
--------------> etc.
-----------> **Gnome** and Xfce (Gtk+)
--------------> Window Manager (e.g. beryl, compiz, metacity)
--------------> Theme Manager (e.g. GTK)
-----------------> Controls
-----------------> Colours
-----------------> Window Border
-----------------> Icons
--------------> Window Decorator (e.g. Emerald - which seems to be part of beryl but not dependent on it?)

I think Unbuntu uses metacity and GTK Theme Manager by default.

1) OK, so is Murrine a subset of the theme manager that does controls only?
Does Murrine replace the controls element of the theme manager?

2) What's the difference between Gtk+ that Gnome is built on and GTK that I think is the Theme Manager in Gnome?

If you visit [Gnome-Look]("http://www.gnome-look.org/") then the content is divided into various subsections including GTK 2.x, beryl, compiz, metacity, icon themes, etc.

3) Isn't Gtk 2.x just the toolkit?

4) Beryl, metacity and compiz as Window Managers are fairly high up the tree but icon themes are a single element of the Theme Manager - how come icons appear independent of the Window Manager?

5) Murrine themes come under Gtk 2.x, not one of the Window Managers - I don't get this? Unless, as per question above, Murrine replaces the controls element of the theme manager and works with any Gnome Window Manager?

Any, and I mean any help in understanding would be much appreciated :).

Thanks,

**Credits**
I got some [info]("http://ubuntuforums.org/showthread.php?mode=hybrid&t=460209&") from [Blazercist]("http://ubuntuforums.org/member.php?u=231783")
[Wikipedia]("http://en.wikipedia.org/wiki/Xwindows") was handy

Mike

---

### Post by blackened on 2007-06-13
The Window Manager handles how windows are displayed and act. Sometimes the WM also serves the role of Window Decorator (as is the case with Metacity), but sometimes these two jobs are distinctly separate (as is the case with Beryl {WM} and Emerald {WD}).

GTK+ only handles how the controls within the windows are drawn. 

Icon themes are set in the customize section of the Theme dialog. AFAIK each different portion of the DE is responsible for its own icons, so a check is made to see which theme is the chosen one, then the responsible piece of the DE picks the appropriate icons that it needs.

```

Gnome (Desktop Environment)
   ->GDM (Gnome Display Manager - this handles the login screen and associated backend stuff)
      ->Window Manager (Metacity, Beryl, Openbox, IceWM, {Sawfish was the original default WM in Gnome})
         ->Window Decorator (Emerald, Aquamarine, Heliodor)
      ->Theme Controls (GTK+ is the default, don't think this can be changed)
         ->Theme Engine (Murrine, Clearlooks, Smooth, etc., These tell GTK HOW the controls should be drawn)

KDE (Desktop Environment)
   ->KDM
      ->Window Manager (KDE window manager is the default, though Beryl or Compiz can also be used)
         ->Window Decorator (Same as above, KDE WM is also the decorator)
      ->Theme Controls (QT is the default in KDE, don't think this can be changed)
         ->Theme Engine (I'm not a KDE person, but I think there are some different ones Keramik, Plastik, etc.)

```

---

### Post by mcduck on 2007-06-14
GTK2 is the toolkit to program graphical applications. When drawn on screen, it uses GTK2 engines that define what kind of widgets you get. GTK2 themes are just text files that tell the GTK engine what colors to use etc.when drawing the widgets on the screen.

Murrine is a GTK2 engine, there are many others, like Ubuntulooks engine used by Ubuntu's default theme, Clerlooks which is used by Gnome's own default theme, Pixbuf which allows using pixmap images as part of the theme and Industrial, for example. The GTK theme can actually use many of these engines at the same time, for example to create a murrine-based theme with pixmap buttons. So, murrine doesn't replace anything, it just adds a new option.

GTK is not responsible of your window borders. That's window manager's job. Beryl is a window manager like Metacity is. It can also use different engines (called Window Decorators) to draw the actual window borders, and Emerald is one of them.

The Theme Manager just allows you to select themes for different things like your Icon theme, GTK2-theme (called 'Controls in the theme manager' and your Metacity theme (if you are running Metacity). All these themes are separate things, but you can save a combination of icon, GTK2 and Metacity theme. Sometimes you might also find downloadable 'complete' themesets.

---

