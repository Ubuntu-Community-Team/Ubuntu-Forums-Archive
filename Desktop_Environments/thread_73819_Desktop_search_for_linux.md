---
title: "Desktop search for linux?"
date: 2005-10-10
forum: Desktop Environments
---

### Post by Laterix on 2005-10-10
Is there any Desktop search tools for linux? I know there is "Search for files..." in Ubuntu menu, but I don't mean that kind of search. I'm talking about indexing search like MSN Desktop search, Mac OSX spotlight and Google Desktop search.

---

### Post by Caboto on 2005-10-10
You should try [Beagle](http://www.beaglewiki.org/Main_Page). As far as I know it's something like an indexing engine. [Here's](http://www.beaglewiki.org/Ubuntu_Installation) a nice How-To in the Beagle Wiki.

---

### Post by Laterix on 2005-10-10
Thanks! This looks pretty much what I was looking for.

Couldn't get it work. :( I have backports, but it still says that can't find  libgmime2.1-cil package.

---

### Post by frodon on 2005-10-11
The easiest way i know to find a file in your computer is using the terminal. 
I use this command : ```
sudo updatedb
```It create a database of all the path of your computer. Then when you have updated your database just use the **locate** command. For example if i search the file picture.png i could use the locate command with just a part of the name like that : ```
locate pictu
```or with just an extension if i can't remember the name of the file : ```
locate .png
```
Also in order to update the database automatically i set a cronjob which run *sudo updatedb* command every day at 4 A.M. it's really useful, if you are interested i can tell you how set your cronjob, just tell me when you want to run updatedb.

Terminal is often more powerful and quicker than a software with a GUI !

---

### Post by kosmic on 2005-10-11
[quote=Laterix]Thanks! This looks pretty much what I was looking for.
 
Couldn't get it work. :( I have backports, but it still says that can't find libgmime2.1-cil package.[/quote]
 
To install breezy the easy way is to follow the wiki manual in the breezy page, if you use synaptic to install brezy it will not work because you will need other files before

---

### Post by wylfing on 2005-10-11
s/breezy/beagle

(I'm guessing that's what you meant.)

---

### Post by james4e on 2005-10-11
You can use this tool "gnome-search-tool". To run it, you just type those letters  in a terminal.

---

### Post by wylfing on 2005-10-11
[QUOTE=james4e]You can use this tool "gnome-search-tool". To run it, you just type those letters  in a terminal.[/QUOTE]

What the OP means by "desktop search" isn't the same thing as what the Gnome search applet does. Utilities like Beagle search both incredibly deeply and incredibly quickly. Results matching anything on your system are brought up as you type. You don't hit "Search" and wait for it to find results -- it's instantaneous -- and it covers everything from email to cached web pages to file names to text inside of files.

---

### Post by Laterix on 2005-10-13
Thanks for your answers. I'm very familiar with updatedb/locate and gnome-search-tool, but those really are not what I'm looking for. I tried this Beagle, but the backend seemed to be little buggy. Hopefully this kind of tool will be integrated part of the gnome some day.

To clarify things a little bit. Desktop search is not a regular file search tool which searches files by filename. It's much more. It search everything, not only files, but also e-mails, contacts, inside different documents, inside MP3 tags etc. It also does indexing background all the time when CPU is not heavily used. This way the search is much faster and results are shown almost instantly when you click search button.

---

### Post by vinodis on 2006-04-27
u may as well try [http://kat.sourceforge.net/](http://kat.sourceforge.net/)

---

