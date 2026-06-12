---
title: "Changing the default ftp application in Gnome"
date: 2009-08-02
forum: Desktop Environments
---

### Post by penguintutor on 2009-08-02
Does anyone know how to change the default ftp application in Gnome? I've searched the past forums, but all I can find is someone asking the same question is 2006 with no useful replies.

My situation is as follows.
I created some ftp bookmarks to the upload of my websites. These bookmarks appear on the launch menus (Places -> Bookmarks) and in Nautilus (the Gnome file manager). If I choose the bookmarks in Nautilus then it opens within Nautilus which is great. But when I try and open the bookmark from the launch bar then it instead opens up in Firefox where I can read, but not write to the ftp site. In the past both of these used to use Nautilus - which is what I'm trying to get back to. 

I don't know what caused the behaviour to change I did install Firefox 3.5, but I think it changed sometime after that. I have also installed Knoqueror and gFTP as Nautilus doesn't appear to work with email addresses as usernames (eg. @ sign), but I don't think they changed it as it changed to Firefox rather than to the application I installed. 

The normal way to change an application from a file is the "application chooser", but I can't find anyway to get this for a link type rather than a file type.

Thanks
Stewart

---

### Post by grizzler on 2009-08-02
Feel free to ignore this if it doesn't help (I'm using Kubuntu, so I'm not that familiar with Gnome), but I had a similar problem some time ago. When I was looking through the search results of my query, I came across someone mentioning **~/.gnome2/panel2.d/default/launchers** as the location where Gnome stores its launch bar / panel files. Maybe you can find anything of use there?

By the way, it's definitely Firefox messing things up. I had a great time getting Firefox 3.5.1 to direct ftp urls to another application (Dolphin) instead of opening them... :(

Makes you wonder... Do the Mozilla developers actually *use* their own products?

> I have also installed Knoqueror and gFTP as Nautilus doesn't appear to work with email addresses as usernames (eg. @ sign)
I once managed to get round that by using **%40** instead of @ in the username. Mind you, that was with an entirely different application, so I have no idea whether that works with Nautilus.

---

### Post by penguintutor on 2009-08-02
Thanks - but still no joy. That directory is empty on my system. As I understand it's used for shortcuts for icons that are put onto the panel, whereas I'm just calling bookmarks. The bookmarks are in ~/.gtk-bookmarks but they are only urls (in this case to ftp: ) which just call the default handler.

For the ftp username issue I already tried %40, but that didn't help. I don't get an error, but I get a blank directory with no sign of my files. Not sure whether it's Nautilus or the ftp server that is not handling it correctly, but it works in gFTP. I prefer using it within my file manager, but gFTP does the job for now and it's not very often that I have to upload to that Windows ftp site. In fact I don't know why on earth the server uses @ as the domain part is just generic, it doesn't even relate to any email addresses I use. As the ftp url is supposed to include an @ as the separator between username and site address it seams silly to use it within an ftp username.  All the other ftp upload sites I use run on Linux and don't have @ in their usernames :D 

I'll keep looking.

---

### Post by grizzler on 2009-08-03
> **penguintutor said:**
> Thanks - but still no joy.

Darn. 

How about the xml file in ~/.gconf/desktop/gnome/url-handlers/ftp/ ?

---

### Post by penguintutor on 2009-08-08
~/.gconf/desktop/gnome/url-handlers/ftp/%gconf.xml

That's the one - thanks very much for your help - I've been searching for that for ages. 

I changed the command stringvalue from firefox to /usr/bin/nautilus and it's now working as it was before.

:KS

---

