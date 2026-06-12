---
title: "Looking for guidance! :)"
date: 2005-01-22
forum: Desktop Environments
---

### Post by midnightfxgt on 2005-01-22
Hey everyone,

I am VERY VERY new to linux, about 24 hours new.  I took a basic course in school on a linux machine, but I want to learn more, and that was a year ago.

I am looking to, right now, find out the basics.  Such as: What is a repository? Why are all these commands neccessary just to install a small plug-in etc, and what are they doing? etc etc

Does anyone know of any really good beginner's guides, or anything that would be usefull?  I was looking at gDesklets for some neat features, and even there install looks a bit more than I want to try right now.  :oops: 

Thanks for any links or suggestios!

~JOHN

---

### Post by Perfect Storm on 2005-01-22
Hiya !

You might check this page: [http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)
Lots of useful stuff :-)



.:=The AI Dude=:.

---

### Post by macewan on 2005-01-22
[http://www.ubuntulinux.org/wiki/ApplicationHowTos](http://www.ubuntulinux.org/wiki/ApplicationHowTos)

Handling software - installing and whatnot [http://www.ubuntulinux.org/wiki/SynapticHowto](http://www.ubuntulinux.org/wiki/SynapticHowto) for the repositories [http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)

---

### Post by midnightfxgt on 2005-01-22
[QUOTE=macewan][http://www.ubuntulinux.org/wiki/ApplicationHowTos](http://www.ubuntulinux.org/wiki/ApplicationHowTos)

Handling software - installing and whatnot [http://www.ubuntulinux.org/wiki/SynapticHowto](http://www.ubuntulinux.org/wiki/SynapticHowto) for the repositories [http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)[/QUOTE]
 Thanks for the help guys... I have looked throught those guides.  Although helpful, they are kinda over the new guys head.  I have had Linux installed for about a day on my WinXp machine, and like it, but there is a serious lack of beginner tools.

The how-tos that have been posted in this thread are great, and I have looked over them, but trying to follow some of the steps are hard for someone with little to no experience.  Setting up a repository is great, not if you dont know what it is LOL :)

Also, I see the synaptic installer, but havent used it yet.  I downloaded the SideCandy utility from gDesklets (again, no How-to for beginners) and managed to extract it to my desktop.  How do I install from here? :s 

Sorry for all the questions.  I am looking to learn, so any help is appreciated, and any links or beginner sites are welcome.

~JOHN

---

### Post by Perfect Storm on 2005-01-22
If it's display you downloaded for gdesklets shall move to /usr/share/gdesklets/Displays

Extract the file

open the terminal

cd /where/you/extracted/the/file
sudo mv <the extracted folder name> /usr/share/gdesklets/Displays

Now press the 'application' tab and click 'run application'
and write 'gdesklets' and press the run button.

Now you have to choose which on (or more you want of the displays to run on your desktop. eg. you could open the browser and look in the /usr/share/gdesklets/Displays/<folder>

Lets say you want  It-pager to run on your desktop (/usr/share/gdesklets/Displays/lt-pager)
Open then 'run application' and write: 

gdesklets /usr/share/gdesklets/Displays/lt-pager/LTPager.display
(it's the .display files you want to start the specific theme/object for gdesklets)

Now it appears and moving around with your mouse, left click to put it on the desktop (you can move it again with the middle mouse button)

To make sure that it appears next time you start ubuntu you have to log out. At the logout memu theres a box called 'save current setup' make sure it's marked. Now logout/reboot.


.:=The AI Dude=:.

---

### Post by midnightfxgt on 2005-01-24
Thanks AI!

I am just trying to install gDesklets even.  Which sucks for a newb lol.  I have installed GDK-pixbuf, libgtk2.0  and Python dev paks etc etc.  It gets where I would presume is almost the end and hangs up with this:

configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Not really impressed so for.  Seems loike a ton of tweaking just to install an app  :-({|= lol..... I think its just me  ;) 

~JOHN

---

### Post by lukem on 2005-01-24
[QUOTE=midnightfxgt]

Also, I see the synaptic installer, but havent used it yet. 
~JOHN[/QUOTE]


Try it, you'll like it.  It might eliminate the errors you're getting and doesn't involve a lot of command line.

---

### Post by midnightfxgt on 2005-01-25
[QUOTE=lukem]Try it, you'll like it.  It might eliminate the errors you're getting and doesn't involve a lot of command line.[/QUOTE]

Thanks Luke, actually I have been trying it for the gDesklets, as it requires a buncha stuf to be installed. :mrgreen:   It looks more for adding utilities from the OS.  It doesn't appear to be something of use for getting apps of the net and installing them, although I could be very wrong :)

~JOHN

---

### Post by Buffalo Soldier on 2005-01-25
[QUOTE=midnightfxgt]Not really impressed so for.  Seems loike a ton of tweaking just to install an app  :-({|= lol..... I think its just me  ;) 

~JOHN[/QUOTE]Apt-get / synaptic handles all of that problem (what most people call "the dependencies hell") and any application installation would only take as long as it takes to download it from the internet + 3 seconds.

An introduction to apt-get at NewsForge.com [http://www.newsforge.com/article.pl?sid=04/12/02/1710208](http://www.newsforge.com/article.pl?sid=04/12/02/1710208)

And synaptic is basically a GUI for the apt-get command.

An example of an apt-get command to install Gdesklet:```
sudo apt-get install gdesklets
```

---

### Post by midnightfxgt on 2005-01-25
[QUOTE=Buffalo Soldier]Apt-get / synaptic handles all of that problem (what most people call "the dependencies hell") and any application installation would only take as long as it takes to download it from the internet + 3 seconds.

An introduction to apt-get at NewsForge.com [http://www.newsforge.com/article.pl?sid=04/12/02/1710208](http://www.newsforge.com/article.pl?sid=04/12/02/1710208)

And synaptic is basically a GUI for the apt-get command.

An example of an apt-get command to install Gdesklet:```
sudo apt-get install gdesklets
```[/QUOTE]

You guy have been a HUGE help.  I have learned a lot over the last few days.  I have gDesklets installed an my first desklet (iWeather) from [HERE.](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=165)  But it doesnt work right :p.  It autmoatically displays at the top under the top panel :(  geez, this isnt too easy, but hey, at least I am learning! LOL.

~JOHN

---

### Post by Perfect Storm on 2005-01-25
You can move it, hold left and right mouse button over it/ or if you have a mouse with 3 buttons then use the third button to move the desklet

---

### Post by midnightfxgt on 2005-01-25
Thats what I am doin.  I can see it move, but when I release the mouse button it snaps where it wants to be lol.  Not it is in the center.  It will move horizontally, but not vertically.  Almost as if it is snapped there.  I am almost ready to give up with gDesklets etc.  I downloaded and unzipped SideCandy.  I tried the Synaptic and apt-get.  Neither would install  :neutral:

---

### Post by midnightfxgt on 2005-01-25
I removed the display and brought it back.... but same deal, but not the "Horizontal" snap point is lower, and I can live with it,  Now to find out my location code  :???: . (doesnt look good for us Canadians lol)

So when downloading programs, like SideCandy, should I simply type "sudo apt-get install SideCandy"?  It told me it couldnt find the file.  I even ran from that directory.  How would Synaptic perform this?

~JOHN

---

### Post by Perfect Storm on 2005-01-25
Did you tried with another gdesklet display and see if it behave the same way?

I havn't seen an option to lock a display, but check anyway, right click on it and choose configure

---

### Post by midnightfxgt on 2005-01-25
AI, I will grab another display later tonight, as I am at work now.

Thanks again for all your help.  Any suggestions on my installing questions :)

~JOHN

---

