---
title: "Old thumbnails"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Frostmourne on 2006-08-03
I noticed in the home directory there is a hidden folder called .thumbnails containing cached PNGs for files. However, many of the cached thumbnails are for files I have deleted before. Is it safe to wipe the entire .thumbnails/normal directory, or at least the files in there that point to old files? Is there any automatic way of deleting uneeded thumbnails from the directory?

It's not like those PNGs are taking a lot of space or anything, but I am obsessive-compulsive about things like this >_>

---

### Post by aweller on 2006-08-03
I am a little the same way! You can delete these, no problem. You may see some of the 'thumbs' on your desktop disappear (if you have jpegs, etc, on there), but they will return soon enough...

---

### Post by bruenig on 2006-08-03
this command will delete all the files in the .thumbnail
```
rm -rf /home/username/.thumbnails/*
```
if you want to make a script that says that or whatever you want to do with that, go ahead. I have put it with my trash deleting script so it clears out all of that stuff at the same time.

---

### Post by ciscosurfer on 2006-08-03
You can safely remove any cached file under the .thumbnails/normal or .thumnails/fail directories that you don't need/want anymore.  You can either be selective, or remove the entire contents of the directory (they will rebuild whenever you open a folder that has icons).

An easy way to do remove all cached files in the .thumnails/normal directory (files that were good, that is, they didn't fail):```
sudo rm -rf ~/.thumbnails/normal/*
``` And you can remove the failed icons like this:```
sudo rm -rf ~/.thumbnails/fail/*
``` You can descend into either direcotry and remove specific ones by double tapping the tab key (tab-tab) once you get to this point and then subsequently choosing which files you'd like to remove```
sudo rm -rf ~/.thumbnails/normal/*<tab-tab>*
``` Likewise for the fail directory```
sudo rm -rf ~/.thumbnails/fail/*<tab-tab>*
``` 
EDIT: bruenig, you beat me to it!

---

