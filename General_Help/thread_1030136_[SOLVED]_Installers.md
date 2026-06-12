---
title: "[SOLVED] Installers"
date: 2009-01-04
forum: General Help
---

### Post by DeMus on 2009-01-04
Hi,

The Linux community is so eager to have more and more fans. I also switched to Linux, more in particular Ubuntu.
What I don't understand is the way Linux, or should I say the distro, is organized. Why are there so many different ways to install software for example? There are the .deb files, the .rpm files, the .bin files, the .sh files, each with their own install methods. Pretty confusing, isn't it? No wonder people still think Linux is only for geeks who really dig in. I'm not a Microsoft fan but I do have to say in that system you download an .exe file, double-click it and 5 seconds later you have a running program.

Also, what is confusing, is when I install a program I do not get a link to that program in the Main Menu, nor on the desktop. So, where is it? How to find it? I can search and probably find a lot of files and directories but which one do I have to start? Files have no extensions like .exe, .txt. So when I click on a file I open a text file which I don't want, I want to start the program.

Isn't there a way to make things more standard so people understand it better,make things more user friendly by giving the links in the start menu? It would sure help a lot.

Also, the names of the directories? I do know they come from Unix but what do the names mean? In which directory can I find what? It's all so complicated.

DeMus

---

### Post by DeMus on 2009-01-04
Nobody? Hard to imagine.

DeMus

---

### Post by ugm6hr on 2009-01-04
Open source development means that people are free to improve the system in whatever way they want.  Hence the lack of standardisation.

The predominant method of installation is via a Package Manager (e.g. apt / Synaptic), hence making installation files completely unnecessary. A .deb behaves in a similar fashion to a Windows .exe.

If you use Gnome or KDE, the menu will be updated automatically, as described in the installed package.  If, for some reason a menu entry is not made, you can launch it from terminal with a simple command:
```
package_name
```

Programs are generally installed in /usr/bin if you want to find the icon to "double-click"

---

### Post by exploder on 2009-01-04
Limux is different. Synaptic is simple enough in my opinion, you can find thousands of applications using it. Windows applications for the most part are not free and there is of course an end user license to agree to.

Debs work similar to exe files when you think about it. You click on them and the installer runs. Linux does not use a registry like Windows. Ever try and remove registry entries from an application you removed in Windows? What a nightmare! When the registry becomes too large the whole system slows down.

In Ubuntu all of the executables are in /usr/bin/ and are not scattered all over the place. With Windows some things end up in Program Files and some end up in C:\.

People have to let go of the assumption that Linux should behave like Windows. People that are used to Windows did not instantly know how to do everything now did they? There is some learning no matter what operating system is used.

---

### Post by DeMus on 2009-01-04
> **ugm6hr said:**
> Open source development means that people are free to improve the system in whatever way they want.  Hence the lack of standardisation.

The predominant method of installation is via a Package Manager (e.g. apt / Synaptic), hence making installation files completely unnecessary. A .deb behaves in a similar fashion to a Windows .exe.

If you use Gnome or KDE, the menu will be updated automatically, as described in the installed package.  If, for some reason a menu entry is not made, you can launch it from terminal with a simple command:
```
package_name
```

Programs are generally installed in /usr/bin if you want to find the icon to "double-click"


Thank you for your answer and your help. I do understand Linux is a worldwide opensource software and it is developed by many. The lack of standardization is, at least to my opinion, a burden newbies have to go through.
I am aware of package managers and I also use Synaptic a lot.
The command line is, as you wrote, something people do not like to use anymore. The days of DOS are gone and people grew up with Windows using the mouse. In Linux it is partly the same thanks to the GUI's but the command line and the terminal are still used a lot. And that's not always easy. I mean simple commands okay, but sometimes in these forums I see commands pass by that make absolutely no sense to me. Commands with lots of options.
What is a good place on the net, or what is a good book to start with?

---

### Post by oldos2er on 2009-01-04
Any command should have a man entry, so if you see a command you don't understand, fire up a terminal, and type in "man [command]" where [command] is ldconfig, apropos, or whatever else you need info for. 

 The reason you see so many "code" blocks here is that it's so much easier than laboriously describing things to "click" in a GUI, not to mention the fact that there are many GUI environments you might need to describe "clicks" for. Bash is mostly universal.

 You might want to read this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

