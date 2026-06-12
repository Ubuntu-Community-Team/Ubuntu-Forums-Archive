---
title: "Concepts: GTK, GTK Engine, Widgets, etc"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by eks on 2007-06-23
Hellos,

I'm kind of confused and Google hasn't been much helpful, so I thought that maybe a kind soul here could help me clarify all this mess in my head.

Compiz/Beryl/Fusion are window managers which add features and eyecandiness to the desktop experience. Right?

And what goes INSIDE the windows is outside the scope of Compiz/Beryl/Fusion and is handled by GNOME (???), and I can find configuration for this in the System/Preferences/Theme. (Right?)

Then I go to [http://www.gnome-look.org/](http://www.gnome-look.org/) and there's no "Gnome Theme", but GTK theme, Icon themes, etc. Which is great, more configuration options. But sometimes in the GTK area you find something that is a GTK Engine. What is it? And what is a [GTK]("http://en.wikipedia.org/wiki/Gtk")? I've read the wikipedia link but couldn't get a good picture.

And what is a widget? :)


eks

---

### Post by eks on 2007-06-24
no one...? :(

---

### Post by darkmaster on 2007-08-31
I'm sorry I only saw this now... many people here seem not to like helping people if what they ask can be found on google. Well, I'll help you anyway and don't like this approach of those people :D

GTK means Gimp Tool Kit, the Gimp theme created this engine for rendering buttons etc. for they're program. When the project Gnome started, to build a fully free desktop environment (There was only KDE ans QT libraryes it was built on where proprietary at that time, not opensourced, now they are), they decided to use the GTK engines to render buttons and the similar. For windows there's Metacity, you know, in Gnome. Now compiz and others can substitute Metacity, they're better for some meanings because they're composite manager too (Metacity by itself cannot act as a composite manager). COmpiz by standard renders windows using the current theme in Metacity but it can use another window manager, Emerald (I like both, sometimes I use Emerald and others I use Metacity, even with compiz).

Now, GKT is a library, it is not an engine. So GTK engines are built to render buttons and everything that is "Inside" a window using the GTK libraryes. That's why they're called GTK Engines. There are several GTK engines. For example, a gtk engine is pixmap, it is wuite heavy but nice looking and it uses images files (Like .png files) to render buttons, sliders and co. Another one is the wonderful Murrine gtk engine by Cimi (Italian like me :D ). This is an engine already contained in the repos of Feisty and is probably going to be the next default gtk engine for Gnome, that's because it is the fastest engine around, it doesn't use any image to render buttons but it can render incredibly nice effects similar to Mac OSX Aqua engine without any picture! Try it, you can find in gnome-look several Murrine (Singular Murrina). Those are just text files that the Murrine ENgine can use to render everything inside windows with different colors and effects..

Murrine is also incredible because it is almost fully customizable by Murrine COnfigurator, always in the repos of Feisty. Hope you understood now and have a nice hacking! Download and try several different engines and themes for those engines :)

(Another example of Engine built on the gtk libraryes is QT Curve, trying to unify KDE and Gnome looks. Infact there's a QT Curve built on QT librares, for KDE, and another one built on GTK, for Gnome. You can use a QT Curve both on Gnome and KDE! Also this is very configurable and is another great engine!)

---

