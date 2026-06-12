---
title: "Is there a way to tell Firefox to save specific filetypes to a certain directory?"
date: 2009-03-24
forum: General Help
---

### Post by Sonic Reducer on 2009-03-24
unfortunately, with firefox you can only choose where ALL files are saved, leaving you unable to specify if you want certain files in certain directories.

right now firefox is setup to open torrents with deluge, i figure i could tell it to open it with another file (a script that saves the torrent to a different folder) but i don't know what the script would be.

basically, i've set deluge on my desktop to autoload all torrents in a subfolder of my dropbox. i want to set my laptop up to save a torrent to that folder, so instead of downloading it locally it will begin downloading on my desktop.

so, how would you write a script to make the file in question move to a different folder?

---

### Post by lovinglinux on 2009-03-24
> **Sonic Reducer said:**
> unfortunately, with firefox you can only choose where ALL files are saved, leaving you unable to specify if you want certain files in certain directories.

Not true. You can specify what Firefox will do with each file type. If you setup a file type to be saved instead of opened with some application, then you will be prompted to choose the destination directory.

> **Sonic Reducer said:**
> basically, i've set deluge on my desktop to autoload all torrents in a subfolder of my dropbox. i want to set my laptop up to save a torrent to that folder, so instead of downloading it locally it will begin downloading on my desktop

You don't need a script. Just go to Firefox "Preferences", then select the "Applications" tab, then select "BitTorrent seed file" in the content type column, then select "Save File" in the action column. Firefox will prompt for the destination directory next time you click a torrent link.

If you want things to be even easier, then you could install "[Save File to]("https://addons.mozilla.org/en-US/firefox/addon/4902")" extension for Firefox, which allows you to save downloads to user-defined folders and their sub-folders straight from context menu. So instead of left-clicking the torrent link, just right-click on it and select the destination folder from the context menu.

---

### Post by Sonic Reducer on 2009-03-24
> **lovinglinux said:**
> Not true. You can specify what Firefox will do with each file type. If you setup a file type to be saved instead of opened with some application, then you will be prompted to choose the destination directory.



You don't need a script. Just go to Firefox "Preferences", then select the "Applications" tab, then select "BitTorrent seed file" in the content type column, then select "Save File" in the action column. Firefox will prompt for the destination directory next time you click a torrent link.

but i'd rather figure out how to make it save to ~/Dropbox/Torrents when i left-click it automatically

---

### Post by lovinglinux on 2009-03-24
> **Sonic Reducer said:**
> but i'd rather figure out how to make it save to ~/Dropbox/Torrents when i left-click it automatically

Then I guess you will need a script, but I don't know how to do it. Why don't you use  the "Save File to" extension? It's very simple to use and the result will be the same.

---

### Post by Sonic Reducer on 2009-03-24
> **lovinglinux said:**
> Then I guess you will need a script, but I don't know how to do it. Why don't you use  the "Save File to" extension? It's very simple to use and the result will be the same.

i already got it figured out in my head, just a script that moves whatever it's opened with to a specified directory.

the problem is what should the script should contain

---

### Post by mikeri on 2009-11-02
I realize this might be a bit on the late side, but I've done it like this:
```
#!/bin/bash
mv $1 ~/torrents/
rename 's/\[.*?\]//g' ~/torrents/$1
exit
```Save it as torrentsave.sh (or whatever you fancy), do a 
```
chmod u+x torrentsave.sh
```and point to it in the Applications-preferences for .torrent files in Firefox. The wierd stuff in the rename line is removal of site ads in square brackets, which seem to confuse rtorrent.

---

