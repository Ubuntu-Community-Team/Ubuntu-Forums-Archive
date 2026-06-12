---
title: "Error creating project with gnomemm libraries."
date: 2005-03-20
forum: Desktop Environments
---

### Post by jeffjj on 2005-03-20
Has anyone built a project with gtkmm toolkit using the gnomemm libraries successfully? 

Heres the disclaimer...I am new to programming in Linux. I have successfully figured out how to work the GTK+ toolkit and have been studying other peoples applications and building my own (fun stuff) the last few months. 

I wanted to try some of the other language bindings before deciding which specific toolkit to use. I see there are C++, Python and Mono bindings. I am a Java developer by trade, but am totally loving learning C and C++. Anyway, I use anjuta for my IDE and if I select the gtkmm project I build no problem. If I select the gnomemm project I cannot build even a simple hello world program. The reason is a gnomemm dependancy problem. 

The error I get is:

/usr/lib/libgnomeuimm-2.0.so: undefined reference to `Gnome::Canvas::Item::item_ construct(Gnome::Canvas::Group&, ...)'

Its not anjuta either because I have tried to build from the command line. The makefile looks fine as far as I can tell...anjuta builds a pretty simple makefile by default.

I have the libgtkmm libraries installed as well as the libgnomemm and libgnomecanvas libraries installed. What am I doing wrong? Or at least what can I do to try and figure this problem out? If nothing else if I know someone else is not having problems using the gnomemm libraries then I know its me and I can try to figure it out. Up till now everything has just worked by using apt and looking at the online documentation.



I also have another question about how the packages show up in apt. How come I have a libgtkmm2.0 and also a libgtkmm-2.4? Are they different libraries? Seems like I would only want the libgtkmm-2.4 package.



I am using Hoary if that makes any difference! Hard to believe this is a preview version...more solid than any other "official" version of anything I have run!!

---

### Post by Nirro on 2005-04-16
I have the exact same problem with gtkmm/gnomemm and anjuta in Hoary, and I'm also asking for help.
I also want to compile my program using the newest available version : 2.6 .

Regards,
Nir Misgav.

---

### Post by charlie763 on 2005-05-27
I am also having the same problem. I have no idea why.

---

### Post by loply on 2005-06-16
Same problem here, have tried to resolve by randomly removing and installing gnome libraries, no luck.

Would also like a solution if one is convenient.

---

