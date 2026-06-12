---
title: "Which image software can sort by dimensions?"
date: 2009-06-21
forum: General Help
---

### Post by IRTxert on 2009-06-21
Is there any software that can list (or preview) images (from a folder, or even from a indexed collection) by dimensions? It would be nice to choose / sort / filter wallpapers this way (and to get rid of low res pictures). I tried picasa before but didn't seem to find this option..

---

### Post by kaibob on 2009-06-21
> **IRTxert said:**
> Is there any software that can list (or preview) images (from a folder, or even from a indexed collection) by dimensions? It would be nice to choose / sort / filter wallpapers this way (and to get rid of low res pictures). I tried picasa before but didn't seem to find this option..
IRTxert

You are clearly looking for something with a GUI, and I don't know of one that will fit your needs. Hopefully, another forum member will see your post and have a solution. 

If not, you may want to consider a short bash script using the Imagemagick Identify utility:

```
width=$(identify -format %w filename.png)

height=$(identify -format %h filename.png)
```

Creating a list of images in a folder sorted by width and then by height (or the other way around) would be easy.

kaibob

---

### Post by michy99 on 2009-06-21
gthumb will sort by size, but i assume that means file size rather than image dimensions.

---

### Post by IRTxert on 2009-06-21
> **kaibob said:**
> IRTxert

You are clearly looking for something with a GUI, and I don't know of one that will fit your needs. Hopefully, another forum member will see your post and have a solution. 

If not, you may want to consider a short bash script using the Imagemagick Identify utility:

```
width=$(identify -format %w filename.png)

height=$(identify -format %h filename.png)
```

Creating a list of images in a folder sorted by width and then by height (or the other way around) would be easy.

kaibob

Not exactly what I'm looking for, but cool.. I can use that to make a bunch of symlinks and view those in a file browser, and use thunar's custom actions to launch the script. Although what would be better though is if I can directly feed the file browser a list of files. Do you know any plugin that does that?

---

### Post by kaibob on 2009-06-21
Sorry, but I'm not familiar with Thunar and don't know of any plug-ins that would do what you want. Perhaps, with this bump, someone else will see this thread and be able to help.

---

### Post by d.j.yotta on 2011-10-27
This earlier post of mine may help...

This feature is one of the things I miss about Windows.
I did find a cool program though which will search through all the  photos in a folder(s) and copy/move them to folders by dimension.
Really fast and is a good enough way to 'sort' them by dimension.
(It's a windows program but works easy peasy with WINE)

Dimensions2Folders (Name in case link breaks)
[http://skwire.dcmembers.com/wb/pages/software/dimensions-2-folders.php](http://skwire.dcmembers.com/wb/pages/software/dimensions-2-folders.php)

---

