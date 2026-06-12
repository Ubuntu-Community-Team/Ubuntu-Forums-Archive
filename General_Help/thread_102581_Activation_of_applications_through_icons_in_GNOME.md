---
title: "Activation of applications through icons in GNOME"
date: 2005-12-12
forum: General Help
---

### Post by Rajan Varadarajan on 2005-12-12
I think I successfully installed ubuntu desktop on one of my machines. I want to try out Mono and so I installed the appropriate packages using the Synaptic Package Manager. But nothing shows up in the GNOME menus. How do I activate or create Windows like shortcuts to start applications like Mono?Do I have to go through the shell (or terminal) to start one of these applications every time, which would be an annoyance? I ran into the same problem with another machine where I installed SuSe 10 with KDE.

---

### Post by DrBair on 2005-12-12
Well we can either right click the desktop and make a launcher or use the menu editor to add something in there.  

Mono is sorta like a cross platform .NET. Its meant to run and develop software but is not an app in of itself.  I believe it has a debugger and a few compilers, bu t doesn't have any kind of IDE included with it.

And pressing Alt+F2 is much easier than starting a console if all you're looking to do is start an application by typing its name.

---

### Post by Dr. Nick on 2005-12-12
You may have to logout/ then back in . Or type **killall gnome-panel **from a terminal and then see if their is a new shortcut for you. I believe programs should make shortcuts, If they dont you may file a bug report to the makers of the application after checking if others have

---

### Post by magnusbb on 2005-12-12
[QUOTE=Rajan Varadarajan]I think I successfully installed ubuntu desktop on one of my machines. I want to try out Mono and so I installed the appropriate packages using the Synaptic Package Manager. But nothing shows up in the GNOME menus. How do I activate or create Windows like shortcuts to start applications like Mono?Do I have to go through the shell (or terminal) to start one of these applications every time, which would be an annoyance? I ran into the same problem with another machine where I installed SuSe 10 with KDE.[/QUOTE]

Those applications that need a menu entry, should, if bundled correct, appear in your GNOME menu. 

But for a framework like MONO, what should turn up? In Windows, what turns up for .NET? Nothing. It's a framework for you to run your software on. Should glibc need an entry?

To run your mono applications simply type "mono your-program.exe".

---

### Post by Rajan Varadarajan on 2005-12-22
Thanks for all your help. Over the course of last week, I installed a whole bunch of packages but am frustrated that they don't show up anywhere. I know the executables are tucked away in various file folders. I think this is one problem with all Linux distros - there is no consistent convention of where to put the executables; for example, Windows for all its flaws, puts programs under "Program Files", but in Linux they are all over the map.

I think there should be a cross-reference table (like a registry) somewhere and I should be able to at least read it. Then I can establish shortcuts (I still haven't figured out how yet) for the applications I need; I guess I can add them through the configuration manager.

Thanks in advance for pointing me in the right direction.

---

### Post by Dr. Nick on 2005-12-22
try this to fix the menu prolem, I get shortcuts automattically, Linux has improved on this aspect alot since a few years ago.
```
sudo apt-get install menu
update-menus
```To see where programs installed open synaptic, search for the package you want and right click it, hit properties and it shold show installed files

---

### Post by AgenT on 2005-12-22
If it is in your path, you can also use which like this:```
which <name of executable>
```Example:```
$ which firefox
/usr/bin/firefox
``` 
And actually Windows does not install everything in Program Files. If this were true, then the need for special uninstall programs (that *still* do a bad job) would not be needed because you would be able everything by just deleting the directory in Program Files. And everyone knows that this is just not viable if you would like to keep your system stable. Or at least as stable as Windows can be.

---

### Post by Rajan Varadarajan on 2005-12-27
A related question.. may not strictly belong to this thread.
Is there a way to display the name of the computer (which is assigned at the time of install) in GNOME menu bar or task bar. I moved by GNOME menu bar to the top so that I could visibly differentiate between that and the application task bar which is always at the bottom.

Thanks in advance for your help.

---

