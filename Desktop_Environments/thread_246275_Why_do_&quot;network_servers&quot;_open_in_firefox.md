---
title: "Why do &quot;network servers&quot; open in firefox (swiftfox)"
date: 2006-08-29
forum: Desktop Environments
---

### Post by mwolfe on 2006-08-29
alright i saved an ftp site by going to palces->connect to server. This always opened up in nautilus before.. I havent connected to the server in over a month probably but today when i tried it opens in firefox.. So i created another one and it opens in firefox as well.
i tried gnome-open [ftp://servernamehere](ftp://servernamehere)
and the same thing happens..
How can i fix this so it opens in nautilus.. for the meantime i'll have to use gftp or something.. 
Thanks in advance

---

### Post by mssever on 2006-08-29
Launch gconf-editor and drill down to /desktop/gnome/url-handlers/ftp. Change the command key to whatever you want.

[rant]Why can't Gnome provide a decent interface for tasks as basic as choosing a default handler? The Gnome people seem to be dead set on removing as much configurability as posible.[/rant]

---

### Post by mwolfe on 2006-08-30
Thanks for the help.. but by the way, do you know what the default handler is supposed to be.. something like /usr/bin/nautilus "%s"
?

---

### Post by mssever on 2006-08-30
That seems to work for me. I could have sworn that Nautilus was the default file handler for FTP, but when I looked in gconf to give you the proper path, I noticed that Firefox was the default on my laptop, as well--my desktop has '/home/scott/bin/install/swiftfox/firefox "%s".' I wonder if it has something to do with clicking yes on Firefox's "Do you want to set FF as the default browser" dialog.

---

### Post by mwolfe on 2006-08-30
hmm.. yeah that could be the culprit..

I tried /usr/bin/nautilus "%s"

and it works the way it used to.

---

