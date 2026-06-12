---
title: "How can I start a program after I installed it?"
date: 2006-03-31
forum: Desktop Environments
---

### Post by atheist on 2006-03-31
Hi,

I just installed Ubuntu 5.10 and using Sinaptic installed Kmail and Krusader. Unfortunattely, I could not find an icon to start the programs. I found that if I type in a terminal window the names of the programs they start, but I would prefer to have their icons in the accesories folder. Please, advice.

---

### Post by Perfect Storm on 2006-03-31
Make a launcher, when you do that you put a command line in it.


By the way any reason you use KDE stuff in Gnome? Just curious.

---

### Post by atheist on 2006-03-31
Thank you for unexpectedly fast reply. Do I have a launcher preinstalled in Ubuntu? 

For your question: I did not know that it was not ubuntu staff:( 
Kmail - I was told is the closest replacement for Outlook Express.
Krusader was an only replacement for Total Commander which I managed to install. Krusader crushed everytime I am trying to get into dev folder.
If you may suggest an "ubuntuier" replacement I would gladly swich.:)

---

### Post by Perfect Storm on 2006-03-31
Well KDE is also ubuntu stuff :). I figure out that you have installed ubuntu default which uses Gnome enviroment you might go with Gnome applications, though you can use KDE applications on gnome and noones hold you back to do so, this is just my opinion :).

You can also try Thunderbird or/and Evolution and then choose which one you prefer.

To make a launcher right click on the desktop and pick 'Create Launcher'. 
There you can fill out.
If you want it in your Application tab type:
```
smeg
```
Click in the left viewer in which category it shall appear in and then press the add button.

---

### Post by atheist on 2006-03-31
Thanks, It works! I was able to create clickable icons on the decktop. Unfortunately, I could not find the proper icons and as a substitute I used apples(green and red). Do you know where are original icons located?

And last thing: where do I type the "code" to add icons to accessories subfolder of applications folder?

---

### Post by Perfect Storm on 2006-03-31
uuhh..I don't have KDE apps, but you might check /usr/share/pixmaps or where the application is install, you can found out where it's install with a 
```
whereis <insert application name>
```
without the < and >


> And last thing: where do I type the "code" to add icons to accessories subfolder of applications folder?

I'm not sure I'm understands the question right. But I don't think it's possible with smeg you might try this menu editor instead: [http://ubuntuforums.org/showthread.php?t=82537](http://ubuntuforums.org/showthread.php?t=82537)

Download the .deb file to your Desktop

```
cd Desktop
sudo dpkg -i XXXXXXXXXX.deb
```

Where XXXX is the name of the package.

A launcher is created in accessories or you can launch it from terminal:
```
alacarte
```

This will replace smeg.

Oh...just remember that linux is case sensitive.

---

### Post by Perfect Storm on 2006-03-31
[QUOTE=Artificial Intelligence]uuhh..I don't have KDE apps, but you might check /usr/share/pixmaps or where the application is install, you can found out where it's install with a 
```
whereis <insert application name>
```
without the < and >




I'm not sure I'm understands the question right. But I don't think it's possible with smeg you might try this menu editor instead: [http://ubuntuforums.org/showthread.php?t=82537](http://ubuntuforums.org/showthread.php?t=82537)

Download the .deb file to your Desktop

```
cd Desktop
sudo dpkg -i XXXXXXXXXX.deb
```

Where XXXX is the name of the package.

A launcher is created in accessories or you can launch it from terminal:
```
alacarte
```

This will replace smeg.

Oh...just remember that linux is case sensitive.[/QUOTE]

alacarte will replace smeg in the next ubuntu release which will officially released the june 1.

---

### Post by atheist on 2006-04-04
I learn to install program, use launcher, but can not locate icons! 
Currently I am looking for icons for Kmail, Krusader and Skype. Please, help

---

### Post by mdsmith on 2006-04-04
Maybe I'm missing something but all of the KDE programs I have installed with Synaptic have shown up in the applications menu in the proper place with the Icon and name there. To get it on the desktop right click on the item and choose add to desktop. Like I said maybe I missed something in this thread, but that's the way it worked for me.

---

### Post by atheist on 2006-04-05
Thank you for pionting it out! After closer look I founr that Skype and XMMS added their icon to Applications. But I could not find Kmail and Krusader. Please, help!

---

### Post by Perfect Storm on 2006-04-06
Open synaptic package manager, do a search on the two of the applications. 
Hit the properties button when selected kmail/Krusader and go to 'Install files' tab. There you can see where to look for the icon(s).

---

