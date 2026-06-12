---
title: "Gui GnomeBoy Advance Problem"
date: 2005-04-12
forum: Gaming &amp; Leisure
---

### Post by Sniffer on 2005-04-12
Hi,

I have just installed from ubuntu Rep the visualboy Advance..so far so good, tough and then i have downloaded the gnomeboy Advance gui in order to not use the terminal.....

But when installing gives me a dependecie error on python, telling me that this gui needs python 2.4 when ubuntu hoary comes by default with 2.4.1..so broken package in the end...

Anyone knows how to solve this one or even knows about any other gui that works as well..i don't have preference.. IF IT WORKS OFCOURSE  :grin: 


Thks 
Sniff.

---

### Post by ellgieff on 2005-04-17
Similar problem for me: I had Gnomeboyadvance and Visualboyadvnce working nicely on Warty ... then today updated to Hoary and suddenly Gnomeboyadvance is gone.

When I try to dpkg -i from the .deb, I get an unresolved dependency issue, same as above.  Reading the error more closely, it turns out that the problem is Gnomeboyadvance wants an _older_ Python than 2.4, and refuses to configure.

Help, please, someone ... my 10 year old wants to play, and I don't want to have to write a bunch of shell scripts ;)

*edit*  Proof that dog helps those who help themselves:  although it quits the dpkg, gnomeboyadvance seems to run fine.  Of course, it isn't in the menus (but then, tuxracer didn't drop itself in the menus either), but a launcher on the desktop will do just fine for my boy.

---

### Post by derrick1985 on 2005-04-17
[QUOTE=ellgieff]Similar problem for me: I had Gnomeboyadvance and Visualboyadvnce working nicely on Warty ... then today updated to Hoary and suddenly Gnomeboyadvance is gone.

When I try to dpkg -i from the .deb, I get an unresolved dependency issue, same as above.  Reading the error more closely, it turns out that the problem is Gnomeboyadvance wants an _older_ Python than 2.4, and refuses to configure.

Help, please, someone ... my 10 year old wants to play, and I don't want to have to write a bunch of shell scripts ;)

*edit*  Proof that dog helps those who help themselves:  although it quits the dpkg, gnomeboyadvance seems to run fine.  Of course, it isn't in the menus (but then, tuxracer didn't drop itself in the menus either), but a launcher on the desktop will do just fine for my boy.[/QUOTE]

Or, you can use Gnome Menu Editor, whatever your cup of java is.

---

### Post by ellgieff on 2005-04-19
Menu editor sounds like a good choice.

The problem now is that Synaptic insists that Gnomeboyadvance is broken, and wants to remove it.  Guess I have to remember how to tell the package system that I don't want it touched.

---

### Post by Sniffer on 2005-04-19
[QUOTE=ellgieff]Similar problem for me: I had Gnomeboyadvance and Visualboyadvnce working nicely on Warty ... then today updated to Hoary and suddenly Gnomeboyadvance is gone.

When I try to dpkg -i from the .deb, I get an unresolved dependency issue, same as above.  Reading the error more closely, it turns out that the problem is Gnomeboyadvance wants an _older_ Python than 2.4, and refuses to configure.

Help, please, someone ... my 10 year old wants to play, and I don't want to have to write a bunch of shell scripts ;)

*edit*  Proof that dog helps those who help themselves:  although it quits the dpkg, gnomeboyadvance seems to run fine.  Of course, it isn't in the menus (but then, tuxracer didn't drop itself in the menus either), but a launcher on the desktop will do just fine for my boy.[/QUOTE]


Just SOLVE the problem with the follow command:

dpkg --force-depends -i package.deb

Reboot

And voilá working and working :smile:

---

### Post by NTolerance on 2005-04-21
[QUOTE=Sniffer]Just SOLVE the problem with the follow command:

dpkg --force-depends -i package.deb

Reboot

And voilá working and working :smile:[/QUOTE]

I tried that an Synaptic and apt-get still complain about the broken package.

---

### Post by Sniffer on 2005-04-21
:) 

Yes thats correct and will complain all the time, this is a workaround for the gui to work and the follow command i post above it's to FORCE the configuration anyway...

So when you go to your menu you have gnomeboy advance to choose in games and automatic config the path to visualboy advance..tough Synaptic complain because the package (gnomeboy advance) has the instruction to use python 2.4...instead of the 2.4.1 that we are using at hoary....

Sniff

---

### Post by NTolerance on 2005-04-22
[QUOTE=Sniffer]:) 

Yes thats correct and will complain all the time, this is a workaround for the gui to work and the follow command i post above it's to FORCE the configuration anyway...

So when you go to your menu you have gnomeboy advance to choose in games and automatic config the path to visualboy advance..tough Synaptic complain because the package (gnomeboy advance) has the instruction to use python 2.4...instead of the 2.4.1 that we are using at hoary....

Sniff[/QUOTE]

Have any idea why I can only run Gnomeboyadvance as root?  If I run it as a regular user it tells me that I need 3 different Python packages which I already have.

---

### Post by ellgieff on 2005-04-24
*shrugs* I've managed to get it to install, multiple times, using both the --force-depends and the --ignore-depends=python switches for dpkg.

Synaptic still complains, and insists on removing gnomeboyadvance whenever I install anything else.  I've tried extracting the .deb, and attempting to remove the depends for python from the control file, but dpkg-deb borks everytime complaining about problems with the control file.

*sighs* So, I just have to remember to install it everytime it gets removed.

---

### Post by NTolerance on 2005-04-26
[QUOTE=ellgieff]*shrugs* I've managed to get it to install, multiple times, using both the --force-depends and the --ignore-depends=python switches for dpkg.

Synaptic still complains, and insists on removing gnomeboyadvance whenever I install anything else.  I've tried extracting the .deb, and attempting to remove the depends for python from the control file, but dpkg-deb borks everytime complaining about problems with the control file.

*sighs* So, I just have to remember to install it everytime it gets removed.[/QUOTE]

This would be easily solved if there was a way to disable certain package errors in apt/synaptic.

---

### Post by NTolerance on 2005-04-27
I've found that installing Gnomeboy Advance from source will get around apt/Synaptic complaining about the package.  Unfortunately you can only run it as root, but that's probably less annoying than apt/Synaptic uninstalling the program everytime you go to install/remove packages.

---

### Post by Sniffer on 2005-04-27
That's interesting...

But did you try with alien make a deb package from the source (tgz)??? Will try this tomorrow if i have sometime.

Thks for the tip.

---

### Post by jldugger on 2005-04-28
Is gnomeboy advance still in Hoary? I've tried searching with apt-cache but I didn't get anything.  It would be really nice to find a GUI to set up the config, since I have no clue why vba's running too damn fast at the moment (aside from having a wicked amd64 3000+ processor ;) ).  Any hints?

---

### Post by Sniffer on 2005-04-28
[QUOTE=jldugger]Is gnomeboy advance still in Hoary? I've tried searching with apt-cache but I didn't get anything.  It would be really nice to find a GUI to set up the config, since I have no clue why vba's running too damn fast at the moment (aside from having a wicked amd64 3000+ processor ;) ).  Any hints?[/QUOTE]

No , Gnomeboy advance NEVER was on Ubuntu Rep, so you need to download directly yourself the package from here:

http://freshmeat.net/projects/gnomeboyadvance/?branch_id=37447&release_id=159817

Tough when installing it will give you a python dependecy error, as you can read on this thread...
We have seek for some solutions, but they are not perfect..will try to convert from the source a deb package for this...

Let's see...

---

### Post by Sniffer on 2005-05-16
[QUOTE=Sniffer]No , Gnomeboy advance NEVER was on Ubuntu Rep, so you need to download directly yourself the package from here:

[http://freshmeat.net/projects/gnomeboyadvance/?branch_id=37447&release_id=159817](http://freshmeat.net/projects/gnomeboyadvance/?branch_id=37447&release_id=159817)

Tough when installing it will give you a python dependecy error, as you can read on this thread...
We have seek for some solutions, but they are not perfect..will try to convert from the source a deb package for this...

Let's see...[/QUOTE]


One member from the community just have done this, and it available already in the ubuntu rep.

Thks for all the work.

Problem Solved.

---

