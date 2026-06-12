---
title: "file name + file title"
date: 2011-06-09
forum: Desktop Environments
---

### Post by engine on 2011-06-09
Not much to ask, surely? I'd just like to be able to give my files &#8210; whatever their type &#8210; a short file name plus a not-too-long descriptive title, and then view both in Nautilus/Thunar or any other similar explorer.

All I can find so far is the option to add a Note, but then the only way to display the note seems to be one file at a time by right-clicking and accessing the Properties tab. Not enough!

---

### Post by engine on 2011-10-04
bump ...

---

### Post by Karlchen on 2011-10-04
Hello, engine.
> I'd just like to be able to give my files &#8210; whatever their type &#8210; a short file name plus a not-too-long descriptive title, and then view both in Nautilus/Thunar or any other similar explorer.To the best of my knowledge, there is no way of achieving your goal using Thunar, Nautilus, Gnome Commander or even Krusader or most other Linux file managers.

What you have in mind can be done e.g. on Windows with the help of the file manager [Total Commander]("http://www.ghisler.com/"). In Total Commander you can assign a so-called description - which in your terms would be the descriptive title - to each filename. Total Commander can copy/move/delete files including their descriptions.

As a matter of fact, the description functionality was actually introduced by [Jpsoft]("http://jpsoft.com/") and their 4DOS / 4NT command line shells. Total Commander adopted this functionality.

Total Commander can be used on Ubuntu as well, but you will have to run in under [Wine]("http://www.winehq.org/"), because it is a genuine Windows software.

Because a lot of Total Commander users miss their file manager on Linux machines, some developers started a project named [Double Commander]("http://doublecmd.sourceforge.net/"). The target of Double Commander is to implement all functions which Total Commander offers and maybe even some functions that it has not got and at the same time to create a file manager that exists as a native application on Linux and on Windows. Beware, currently Double Commander is still in its beta stage and not feature-complete, yet.

Nonetheless, as far as I can tell, there are only two ways to achieve your goal:

[LIST]
[*]either run Total Commander under Ubuntu on Wine (as e.g. I do)
[*]or use Double Commander even though it is still beta software.
[/LIST]
Beware, if you copy / move files which have been assigned a description using a file manager that is unaware of descriptions you may lose your descriptions.

Kind regards,
Karl

---

