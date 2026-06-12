---
title: "adobe Flash"
date: 2009-03-04
forum: General Help
---

### Post by neer2005 on 2009-03-04
is there a way to get flash player for kubuntu 64x

---

### Post by fooman on 2009-03-04
well assuming its the same for ubuntu and kubuntu...here is how i did it in ubuntu:

first go here and download the "64 bit plugin for linux":

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

then search for and uninstall any flash/gnash items you may have installed already...use synaptic.

next,  extract the file you downloaded from adobe labs.  that should leave you a "libflashplayer.so" file.  copy that file to the "~/.mozilla/plugins" directory.

close firefox if it was open,  then reopen it again and see if it works.  you can check to see what version is installed by typing: 

```
 about:plugins 
```

in your firefox address bar.

it should show: Shockwave Flash 10.0 r22 

hope that helps.

---

### Post by neer2005 on 2009-03-04
sry knid of nub where is the file located in root

---

### Post by fooman on 2009-03-04
sorry,  i'll try and make it a little more clear...

open synaptic (system > administration > synaptic package manager).  click on the search button,  type flash in the space and press search.

right click on any entries of flash and gnash that are installed and choose "mark for removal" from the drop down list.  then click the "apply" button in synaptic's toolbar.

when that is done,  down load the file from adobe labs that i posted in my last post.  after it downloads,  right click on it and choose "extract here" from the list.

that should extract a file called "libflashplayer.so".  right click on that file and choose "copy" from the list.

next,  open your home folder (places > home folder), and in the toolbar, click "view" ...put a check next to "show hidden files".  then scroll down and find the .mozilla folder.  open it and you should see a folder called "plugins".  open that folder and right click on an empty space in it...choose "paste" from the dropdown menu.  that should place the "libflashplayer.so" into the /.mozilla/plugins folder and you should be set to go.

close any firefox that are open and then open firefox.  see if it is installed by typing into the firefox address bar:

```
about:plugins
```it should show "Shockwave Flash 10.0 r22" as installed.

then navigate to a site like youtube and see if flash videos work.

hope that helps you.

---

