---
title: "how to add ttf font?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by goatflyer on 2006-08-22
I am trying to add a .ttf file containing the canadian characters for languages like cree and inuktitut.  The repositories dont have such a font, but I found a free one here:

 [http://www.languagegeek.com/](http://www.languagegeek.com/)

Gnome help says I can add a font by opening the font folder (opened in System>Preferences>Font) and copying my font file to it.  This does not work.

Copy and paste does nothing (it doesn't copy the file and it gives no error feedback).

Thinking it might be permission related, i opened a terminal and did a sudo cp of the file to /usr/share/fonts/truetype/mstcorefonts (where there are plenty other .ttf files).  The file copies, and has the same permissions as all the other files, but still the font isn't recognized by Gnome (or OOo, or gedit)

So how does one install a .ttf file?

---

### Post by QUASAR_FREAK on 2006-08-22
you must copy the file to /usr/share/fonts and then rebuild your font cache with:
sudo fc-cache -f -v

---

### Post by majesticturkey on 2006-08-22
I was just looking over GNOME's roadmap, and making it easier to add fonts is on the ToDo. Just thought I'd throw that in there in case you were thinking "that's annoying." So do the devs :P

---

### Post by goatflyer on 2006-08-22
Thanks for your help, it worked like a charm!

---

### Post by Kodiak3000 on 2006-09-03
Me too - ACE!

---

### Post by notarikon on 2006-10-01
For the record, you can also copy the fonts into your /home/username/.fonts/ folder (create it if it doesn't exist) and then rebuild the font cache with

sudo fc-cache -f -v

---

### Post by Vorticon on 2006-10-02
I'm trying to copy a whole folder with fonts into this directory but that doesnt work. I use this command:

sudo cp /home/username/Desktop/ttf-eigen /usr/share/fonts

but for some reason the folder gets skipped :( help!

---

### Post by Vorticon on 2006-10-02
Thanks to someone on the irc channel i found out how to install a whole folder :)

installing a folder of fonts:

sudo cp -a /path-to-folder /usr/share/fonts
sudo fc-cache -f -v

---

### Post by Eglo on 2007-07-07
i have with sudo cp -a /path-to-folder /usr/share/fonts add .ttf Font but i'll remove it.
how can i that?

Thanks

---

### Post by Eglo on 2007-07-07
?????

:(

---

### Post by zednanref on 2008-03-06
Thanks alot that did the trick

---

### Post by roboghast on 2008-03-24
> **QUASAR_FREAK said:**
> you must copy the file to /usr/share/fonts and then rebuild your font cache with:
sudo fc-cache -f -v

nice - you left out a step - that is, how do you give yourself permission to copy it there? the "share" right click option doens't do much - guess you have to go back and type some more "DOS commands" eh? How nice I logon and give my password and the OS stills thinks im not a super user even though I logged it as it ... need to change that too....guess its so I dont do something stupid like cut and paste font files...


ubuntu linix needs to move away from the terminal commands if anyone is going to really use it. Most of us only use something like "giving yourself permission to cut and paste files " only once in a blue moon - then we have to hunt and search all those "forums" in the "community" and try something that ANYONE writes and usually leaves out a step (or three) they ASSUME everyone knows. 

And usually the thing you are trying to do is so irrelevant and stupid that its not worth an hour to try to RE-figure out all the cryptic "DOS commands" in the terminal. Like all I was trying to do is add shadowbane true type fonts because they MIGHT look cool - so I end up messing around with this for an hour reading every lame forum and searching the community with its UNGOOGLY search, that brings up nothing or some thread that sounds like what you want but is useless. 

I am giving up - guess ill go back to stumble on my firefox browers on ubuntu - which is bugged and wont put the button icons at the top of the screen - and has a graphics glitch in the customize menu - the whole row of buttons are there and overlapping in the menu - its messed up - and yet I couldnt re-install firefox to fix it cause - I guess someone decided to make it uninstallable.

---

### Post by kryrinn on 2008-03-25
> **roboghast said:**
> nice - you left out a step - that is, how do you give yourself permission to copy it there? the "share" right click option doens't do much - guess you have to go back and type some more "DOS commands" eh? How nice I logon and give my password and the OS stills thinks im not a super user even though I logged it as it ... need to change that too....guess its so I dont do something stupid like cut and paste font files...


ubuntu linix needs to move away from the terminal commands if anyone is going to really use it. Most of us only use something like "giving yourself permission to cut and paste files " only once in a blue moon - then we have to hunt and search all those "forums" in the "community" and try something that ANYONE writes and usually leaves out a step (or three) they ASSUME everyone knows. 

And usually the thing you are trying to do is so irrelevant and stupid that its not worth an hour to try to RE-figure out all the cryptic "DOS commands" in the terminal. Like all I was trying to do is add shadowbane true type fonts because they MIGHT look cool - so I end up messing around with this for an hour reading every lame forum and searching the community with its UNGOOGLY search, that brings up nothing or some thread that sounds like what you want but is useless. 

I am giving up - guess ill go back to stumble on my firefox browers on ubuntu - which is bugged and wont put the button icons at the top of the screen - and has a graphics glitch in the customize menu - the whole row of buttons are there and overlapping in the menu - its messed up - and yet I couldnt re-install firefox to fix it cause - I guess someone decided to make it uninstallable.

You can uninstall firefox - go to synaptic, mark the packages for uninstall, apply, (and to reinstall: mark them for installation, apply...)

If you don't like ubuntu - no one is forcing you to use it...  Mac and Windows are widely available.

There's some of us that like having an alternative, and that's what ubuntu is here for.  There's more of a learning curve - but some of us think it's worth it.  If you don't, feel free to stop by pretty much any store, and they'll have Mac and Windows machines for you.

---

### Post by QUASAR_FREAK on 2008-03-25
> **roboghast said:**
> nice - you left out a step - that is, how do you give yourself permission to copy it there? the "share" right click option doens't do much - guess you have to go back and type some more "DOS commands" eh? How nice I logon and give my password and the OS stills thinks im not a super user even though I logged it as it ... need to change that too....guess its so I dont do something stupid like cut and paste font files...


ubuntu linix needs to move away from the terminal commands if anyone is going to really use it. Most of us only use something like "giving yourself permission to cut and paste files " only once in a blue moon - then we have to hunt and search all those "forums" in the "community" and try something that ANYONE writes and usually leaves out a step (or three) they ASSUME everyone knows. 

And usually the thing you are trying to do is so irrelevant and stupid that its not worth an hour to try to RE-figure out all the cryptic "DOS commands" in the terminal. Like all I was trying to do is add shadowbane true type fonts because they MIGHT look cool - so I end up messing around with this for an hour reading every lame forum and searching the community with its UNGOOGLY search, that brings up nothing or some thread that sounds like what you want but is useless. 

I am giving up - guess ill go back to stumble on my firefox browers on ubuntu - which is bugged and wont put the button icons at the top of the screen - and has a graphics glitch in the customize menu - the whole row of buttons are there and overlapping in the menu - its messed up - and yet I couldnt re-install firefox to fix it cause - I guess someone decided to make it uninstallable.

maybe mac os x is the right system for you or windows, i dont know. For my type a bunch of commands isn't a hard thing to do, and maybe there is some GUI to doit but i dont know that either, its more simply for my use the command line.

if you want to do something usefull you can just vote in ubuntu brainstorm for a font gui, and fill a bug report to mozilla for that problem in firefox, or fixit yourself if you have the skills, that is the power of the opensource you know? :lolflag:

for admin permissons use the command sudo, or read a unix for dummies book =)

(for copy with nautilus you can use the run dialog and use gksu nautilus)

---

