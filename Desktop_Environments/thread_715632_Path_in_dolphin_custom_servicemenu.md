---
title: "Path in dolphin custom servicemenu"
date: 2008-03-05
forum: Desktop Environments
---

### Post by egalua on 2008-03-05
Hi, 

I made a custom service menu in dolphin, namely the following:

-----------------------------------------------
[Desktop Entry]
X-SuSE-translate=true
Encoding=UTF-8
ServiceTypes=inode/directory
Actions=compressHere

[Desktop Action compressHere]
Name=Zip
Exec=zip -r %u %u
Icon=ark
-----------------------------------------------

with name
~/.kde/share/apps/d3lphin/servicemenus/ark_compress.desktop

It is modified from the original
/usr/share/apps/d3lphin/servicemenus/ark_compress.desktop

This way I have a menu item to zip a folder.

The problem is: in the zip file, names get the full path, instead that the relative path which I get issuing from console the command

zip -r mydir mydir

So: how do I get my custom menu to zip with relative names? 
I tried both %u and %U, but I get the same... :(

Thanks a lot

Fabio

---

