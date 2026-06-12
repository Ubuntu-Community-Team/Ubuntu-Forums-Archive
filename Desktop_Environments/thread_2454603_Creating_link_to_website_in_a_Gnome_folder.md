---
title: "Creating link to website in a Gnome folder"
date: 2020-12-02
forum: Desktop Environments
---

### Post by Edward_Diener on 2020-12-02
How can I create a link to a website in a Gnome folder which is on my desktop ? When I try to drag, from Firefox, a website URL to a folder I am told:

"Drag and drop is not supported. An invalid drag type is being used."

I tried Ctrl=Shift drag with the same result. What is the technique which will allow me to drag and drop a website URL in Firefox to a folder as a link ?

---

### Post by ActionParsnip on 2020-12-02
All I can suggest is to make a launcher that run

firefox [https://www.bbc.co.uk](https://www.bbc.co.uk) 

Or whatever URL it is. Maybe others can advise. The Gnome team don't want people to have desktop icons (I think it's messy too)

---

### Post by Edward_Diener on 2020-12-03
A sincere thanks ! But the fact that the Gnome team does not want people to have desktop icons I do find hilarious, since Gnome clearly allows folders to be created on the desktop through its GUI interface. So Gnome allows me to create a folder on my desktop but if I want to drag and drop a URL from Firefox into that folder it forbids it. Something about that logic just eludes me.

---

### Post by Holger_Gehrke on 2020-12-04
Actually the Gnome devs don't mind desktop items, but they don't like the file manager doing double duty as desktop manager. They mostly pulled the (old, crufty and hard to maintain) code for desktop stuff out of Nautilus but haven't (yet) built everything to replace that functionality.

You could try a [desktop file with "Type=Link"]("https://specifications.freedesktop.org/desktop-entry-spec/latest/index.html") in the desktop folder. Not as nice as simply drag-and-dropping an URL (which produces such a desktop file in XFCE ...) but AFAIK it should work.

Holger

---

### Post by Dennis N on 2020-12-04
I suggest you  make an html document for the links. The html file can then exist anywhere in your home folder. The nice thing is you can make this html document your home page so this page with favorite links displays when you start Firefox. No need for bookmarks or a forest of icons on your Desktop to web sites you frequently visit.

With a little creativity, you can include images, text, and links to additional local html pages you might make.

---

### Post by ActionParsnip on 2020-12-04
You don't have to use Gnome. Other desktop environments exist.....

---

