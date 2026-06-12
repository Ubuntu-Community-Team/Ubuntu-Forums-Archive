---
title: "Amarok, k3b...all k apps all huge and ugly."
date: 2005-12-08
forum: Desktop Environments
---

### Post by Joey French on 2005-12-08
Hi,
Why are the kde apps, when run in gnome or xfce, so huge and ugly? I love amarok and k3b, but when in xfce or gnome they dominate the screen with huge text and guis that extend off the screen. Is there a way to compile them with a different look? Just something I have set up wrong? Or is that just the way it is?

---

### Post by kairu0 on 2005-12-08
See [http://www.ubuntuforums.org/showthread.php?t=56630](http://www.ubuntuforums.org/showthread.php?t=56630).

Read post #1, then #53.

---

### Post by aysiu on 2005-12-08
I wonder if it's something as simple as running *kcontrol* and adjusting the screen resolution in KDE.

---

### Post by Joey French on 2005-12-08
Yeah, but those two apps are the ones I really use in all the desktops, k3b and amarok. The ones they said were unaffected by the configuration. Am I missing something?

---

### Post by Joey French on 2005-12-09
[QUOTE=aysiu]I wonder if it's something as simple as running *kcontrol* and adjusting the screen resolution in KDE.[/QUOTE]

Man, I'm gonna try that when I get back to my box.

OK, I gotta ask, not being a programmer or whatever, is there no way to compile programs with a specific frontend? Is there even such a thing? Why do certain programs only have a frontend for Gnome, KDE, etc? I don't understand, help me out...

---

### Post by mad_phoenix on 2005-12-09
> OK, I gotta ask, not being a programmer or whatever, is there no way to compile programs with a specific frontend? Is there even such a thing? Why do certain programs only have a frontend for Gnome, KDE, etc? I don't understand, help me out...

It really all goes back to the graphical toolkit that the program was written in.  For KDE apps like amarok and k3b, there's a graphics/widgets library called QT that makes up all of the controls/textboxes/buttons etc. for the GUI.  In Gnome, the toolkit is called GTK (Gimp Toolkit).  So a programmer could write an interface with both of those libraries and give you the option to compile either in, but most don't.  Most options are decided at compile time by the user running the configure script.  To install a program from source, the basic method is to run the configure script, then the make script, then the make install script.  You can supply options to configure (such as --use-backend=gstreamer or --frontend=qt) that activates different options or support for different protocols.

That's a really simple and incomplete explaination, but hopefully it'll get your mind pointed in the right direction.

---

### Post by rubengs on 2005-12-09
The simple way is to run kcontrol and adjust the fonts for kde apps (usually are set bigger than gnome apps), but you can always go far than that and follow the mentioned guide in post #2, install the polymer theme.

---

### Post by Joey French on 2005-12-09
[QUOTE=mad_phoenix]It really all goes back to the graphical toolkit that the program was written in.  For KDE apps like amarok and k3b, there's a graphics/widgets library called QT that makes up all of the controls/textboxes/buttons etc. for the GUI.  In Gnome, the toolkit is called GTK (Gimp Toolkit).  So a programmer could write an interface with both of those libraries and give you the option to compile either in, but most don't.  Most options are decided at compile time by the user running the configure script.  To install a program from source, the basic method is to run the configure script, then the make script, then the make install script.  You can supply options to configure (such as --use-backend=gstreamer or --frontend=qt) that activates different options or support for different protocols.

That's a really simple and incomplete explaination, but hopefully it'll get your mind pointed in the right direction.[/QUOTE]

So, what you're saying is, there may be away for me to compile these apps with options to compile them with a different frontend? That would be great. How many apps do you think this option is available for? Would k3b and amarok be able to be compiled, by me, with these GTK options? I know this is a lot of questions, but I am really curious now.

Thanks,
Joey

---

### Post by kairu0 on 2005-12-09
[QUOTE=Joey French]So, what you're saying is, there may be away for me to compile these apps with options to compile them with a different frontend? That would be great. How many apps do you think this option is available for? Would k3b and amarok be able to be compiled, by me, with these GTK options? I know this is a lot of questions, but I am really curious now.

Thanks,
Joey[/QUOTE]

You won't be able to port k3b and amarok to GTK. What it comes down to is that kde uses a different DPI setting than gnome sometimes. Oh, and the fonts are different, too. You shouldn't have to recompile a thing.

---

