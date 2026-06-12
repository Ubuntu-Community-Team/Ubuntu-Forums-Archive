---
title: "The new GUI installer from ati"
date: 2005-06-22
forum: Gaming &amp; Leisure
---

### Post by Dark Damo on 2005-06-22
apparently they have a driver installer with a GUI i tryed to download it on windows but it leads me to a page with alot of text and no download?

---

### Post by afonic on 2005-06-22
[QUOTE=Dark Damo]apparently they have a driver installer with a GUI i tryed to download it on windows but it leads me to a page with alot of text and no download?[/QUOTE]
 I suggest you stop X before installing the driver and then use the text interface from the console.

---

### Post by Dark Damo on 2005-06-22
[QUOTE=afonic]I suggest you stop X before installing the driver and then use the text interface from the console.[/QUOTE]
 how come?

---

### Post by afonic on 2005-06-22
[QUOTE=Dark Damo]how come?[/QUOTE]
 Well it's a measure to ensure the installation will be ok. I've seen various weird problems even if this GUI install is supposed to work.

Or just follow one of the HOW-TOs in this forum.

---

### Post by Dark Damo on 2005-06-22
[QUOTE=afonic]Well it's a measure to ensure the installation will be ok. I've seen various weird problems even if this GUI install is supposed to work.

Or just follow one of the HOW-TOs in this forum.[/QUOTE]
 kk ty for info :)

---

### Post by holr on 2005-06-23
[QUOTE=Dark Damo]apparently they have a driver installer with a GUI i tryed to download it on windows but it leads me to a page with alot of text and no download?[/QUOTE]

Ive had that happen to me. It seems like the browser is trying to 'open' the contents of the file as a text document intead of saving it. Just right click the link and do save as (in firefox) and then store it wherever you want.

go to the directory (in a terminal ) and type: sudo sh ./name_of_file.run

Be warned, afterwards, there is a prog called aticonfig (i think) that will modify your xorg.conf file. Good idea to back this up first:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by Dark Damo on 2005-06-23
[QUOTE=holr]Ive had that happen to me. It seems like the browser is trying to 'open' the contents of the file as a text document intead of saving it. Just right click the link and do save as (in firefox) and then store it wherever you want.

go to the directory (in a terminal ) and type: sudo sh ./name_of_file.run

Be warned, afterwards, there is a prog called aticonfig (i think) that will modify your xorg.conf file. Good idea to back this up first:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak[/QUOTE]
 ah so backup my conf file? what does this file do?

---

### Post by Burgundavia on 2005-06-25
The best way to install the ATI drivers is still from the repos, as can be seen here:

[http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)

Corey

---

### Post by afonic on 2005-06-25
[QUOTE=Burgundavia]The best way to install the ATI drivers is still from the repos, as can be seen here:

[http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)

Corey[/QUOTE]
 Hi,

the Ati I have was my laptop, but aren't the drivers in the repos kind of old?

Ati has impoved the drivers a lot in the latest version.

---

### Post by Dark Damo on 2005-07-01
[QUOTE=afonic]Hi,

the Ati I have was my laptop, but aren't the drivers in the repos kind of old?

Ati has impoved the drivers a lot in the latest version.[/QUOTE]
 ok i installed the drivers

now whats that flgrx command i run?

---

### Post by Dark Damo on 2005-07-01
[QUOTE=Dark Damo]ok i installed the drivers

now whats that flgrx command i run?[/QUOTE]
 fglrxconfig this gives me alot of crap i dont know about.... what should i do?

---

### Post by holr on 2005-07-04
[QUOTE=Dark Damo]fglrxconfig this gives me alot of crap i dont know about.... what should i do?[/QUOTE]

Hi mate!

Sorry, been getting lost in all the posts and missed the question you asked about fglrx and ati graphicsdrivers.

the xorg.conf file stores all your settings for the video display and monitor configuration (as well as mouse / keyboard settings). Think of it as what you'd get if you didnt have the nice display menus on windows - they are frontend gui's for a config file somewhere in windows!

Unfortunately, in linux you have to edit this file manually :-( but thats linux for ya!

So make sure you back up your /etc/X11/xorg.conf before doing anything. Cause if you screw up this file you won't get the window manager (gnome in ubuntu) up and only had a dos-like terminal to do stuff with.

With regard fglrxconfig, this is ati's solution to "help" you configure xorg.conf to enable 3d acceleration. Its fairly straightforward, you can normally just use the default suggested options, but you will need to refer to your monitor manual to find out the horizontal and vertical refresh of your screen. This would be something done automatically in windows.

Ultimately, play around with the settings. If everything goes tits-up, delete your /etc/X11/xorg.conf and replace it with the BACKUP you made, and restart the system ;-)

---

### Post by Dark Damo on 2005-07-06
[QUOTE=holr]Hi mate!

Sorry, been getting lost in all the posts and missed the question you asked about fglrx and ati graphicsdrivers.

the xorg.conf file stores all your settings for the video display and monitor configuration (as well as mouse / keyboard settings). Think of it as what you'd get if you didnt have the nice display menus on windows - they are frontend gui's for a config file somewhere in windows!

Unfortunately, in linux you have to edit this file manually :-( but thats linux for ya!

So make sure you back up your /etc/X11/xorg.conf before doing anything. Cause if you screw up this file you won't get the window manager (gnome in ubuntu) up and only had a dos-like terminal to do stuff with.

With regard fglrxconfig, this is ati's solution to "help" you configure xorg.conf to enable 3d acceleration. Its fairly straightforward, you can normally just use the default suggested options, but you will need to refer to your monitor manual to find out the horizontal and vertical refresh of your screen. This would be something done automatically in windows.

Ultimately, play around with the settings. If everything goes tits-up, delete your /etc/X11/xorg.conf and replace it with the BACKUP you made, and restart the system ;-)[/QUOTE]
 "but you will need to refer to your monitor manual to find out the horizontal and vertical refresh of your screen."


lol problem is my monitor didnt come with a manuel :(

---

### Post by ghostrifle on 2005-07-08
> 
 "but you will need to refer to your monitor manual to find out the horizontal and vertical refresh of your screen."


lol problem is my monitor didnt come with a manuel 


You don't really need to know it. Just use some standard settings, like the ones you can find in your original xorg.conf   ;-)

---

