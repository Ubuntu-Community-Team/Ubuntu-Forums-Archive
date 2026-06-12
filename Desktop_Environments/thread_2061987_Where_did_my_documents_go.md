---
title: "Where did my documents go?"
date: 2012-09-23
forum: Desktop Environments
---

### Post by yogyakor on 2012-09-23
I have installed gnome-shell alongside Unity last night. Now, when I press the super key and type in the key word to pull up some file, I get nothing in the search result. Gnome shell is just pulling up applications. No 'Documents' section, no 'Recent files', etc...

I thought it might be an indexing problem, so I manually opened and closed the file 
through nautilus a couple times. When I tried to do 'Windows/meta key', 'file name',
still nothing.

I only have 300 MB of personal files on this computer, so I don't think it's an indexing issue. 

I had a similar problem on another Gnome distribution, it was working fine at first and then one day simply stopped showing documents.

Does anyone know how to get the documents to show in searches?

Thanks for any suggestions.

---

### Post by Cheesemill on 2012-09-24
I thought that this was only a Unity feature.

I've used Gnome Shell on several different distros and the search has only ever shown applications.

---

### Post by yogyakor on 2012-09-24
No, actually I've used Gnome 3 in Fedora 16 and 17, and it definitely shows documents in searches, as well as recently opened files. Fedora uses vanilla Gnome,
so this feature should be present in other distros if everything is set up correctly.

At one point documents just disappeared from my searches in fedora, which
was the reason I moved to Ubuntu. I figured, Gnome shell becomes very impractical without showing you files in searches. Going through Nautilus every time I want to open a file is very time consuming.

---

### Post by yogyakor on 2012-09-24
```
sudo apt-get install gnome-documents
```Install Tracker Search from [https://extensions.gnome.org](https://extensions.gnome.org).

Reboot.

All the files in my computer showed up in searches immediately after reboot.
  To fine tune indexing you can open 'Search and Index' app.

Happy times, back to functional desktop. :guitar:

---

