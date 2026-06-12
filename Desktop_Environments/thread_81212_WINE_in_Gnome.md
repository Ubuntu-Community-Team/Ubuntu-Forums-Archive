---
title: "WINE in Gnome"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Mosey on 2005-10-23
So basically I'm attempting to get a few games running in my version of Breezy.

I installed wine, xwine, libwine and libwine-dev and I can't figure out how to run the program.

I don't know the console/terminal command to run a program and it's not in my applications drop down.

Can anybody help? Also...do I need to run a setup program?

---

### Post by Sutekh on 2005-10-24
[QUOTE=Mosey]So basically I'm attempting to get a few games running in my version of Breezy.

I installed wine, xwine, libwine and libwine-dev and I can't figure out how to run the program.

I don't know the console/terminal command to run a program and it's not in my applications drop down.

Can anybody help? Also...do I need to run a setup program?[/QUOTE]

Yeah this one confused me too.  Just go to the folder/location of the application you want to run/install and open it.  Wine will take care of the rest.  You can also configure how wine functions using winecfg, there you can choose how you want wine to work.  

I think that's all you need to do (this is off the top of my head, but I installed and used wine just the other day)

Check out the wine documentation for more complex uses:
[http://www.winehq.com/site/docs/wineusr-guide/index]("http://www.winehq.com/site/docs/wineusr-guide/index")

---

### Post by Iandefor on 2005-10-24
If you just want to run games, I would strongly suggest running [Cedega]("https://wiki.ubuntu.com/Cedega") rather than WINE (Seeing as how WINE only recently went beta). However, To run a Windows application using Wine, type in ```
wine [program] [arguments]
``` For more detailed information, consult the manual page. you should also install winesetupk.

---

