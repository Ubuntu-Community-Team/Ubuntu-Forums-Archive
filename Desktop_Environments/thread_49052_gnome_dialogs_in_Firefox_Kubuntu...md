---
title: "gnome dialogs in Firefox Kubuntu..???"
date: 2005-07-14
forum: Desktop Environments
---

### Post by Loungefly on 2005-07-14
Hey all :)

When I save files in Firefox I'e noticed the "save" dialog/GUI is gnome rather than KDE. Is there any way of getting rid of this so I will get the standard save dialog/GUI that's appropriate for KDE? 

I realize Kubuntu is still a little rough around the edges but I was hoping to get rid of these unwanted gnome leftovers (for lack of a better word) that seem to be present in Kubuntu.

Any help would be greatly appreciated. :)

---

### Post by dave9191 on 2005-07-14
Firefox is made using GTK which is the same stuff that gnome uses. KDE uses Qt. Since you are running kde, you dont need to have the firefox version that is in the repositories and you might as well isntall the one from the firefox home page. That way you will have the most up to date one and without gnome optimistations. And also intsall a nice theme for firefox like Plastikfox Crystal SVG, that will blend with KDE a lot nicer. 

Dave

---

### Post by Loungefly on 2005-07-14
Thanks so much for that. I'll go ahead and download it straight from mozilla.org then.

I rarely ever download apps without using apt-get. Does it matter what folder I download the tar file to? Also, I'm assuming that when I click to install it will ask me for the directory to install it into. If this is the case, what directory should I install Firefox in?

Sorry for so many questions. I'm fairly new to Linux and I'm still a little clueless when it comes to downloading and installing stuff properly without Synaptic and apt-get ](*,)

---

### Post by flying_icarus on 2005-07-14
I would suggest installing it in /usr/local/firefox... and then creating a symlink in /usr/local/bin/ to point to the installed binary (something like the following)
```
$root@/usr/local/bin# ln -s ../firefox/firefox firefox
```

And then you can put it into the KDE menu with the menu editor.

But maybe someone has a better idea. ;)

---

### Post by dave9191 on 2005-07-15
Personally all the software that I install by hand (exluding stuff I compile myself) I put that into my /opt dir. So firefox in my case hides in /opt/firefox/firefox. And thats the command I run to start it up. Dont forget to add a menu item for it later :)

And like flying_icarus said, you can make a sym link for it , but be sure that you dont already have another version of firefox flying around your system first :) 

Dave

---

### Post by GeneralZod on 2005-07-15
Note that a KDE-ified version of Firefox was being worked on by Zack Rusin a while back (with really good integration, from using Qt instead of GTK, to using the KDE file dialogues, to using KWallet etc) but he never finished in and moved on to other things.  Rumours are that he'll start work on it again one day, but I don't think it will be for a while, alas :(

---

### Post by dave9191 on 2005-07-15
Well this is a shot of my firefox (ignore the window manager, im using fluxbox). But this is the same firefox theme i used under kde. 

Dave

---

