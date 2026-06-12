---
title: "External browser setup in Bluefish 1.0.7"
date: 2009-04-16
forum: General Help
---

### Post by Andrew_P on 2009-04-16
(This posting is a memorandum, based on what I discovered from archived threads here and by poking around on my own, rather than a request for help.)

As-installed, the "View in browser" button in Bluefish doesn't seem to do anything.  I'm using SeaMonkey 1.1.16 as my default Web browser in Ubuntu 8.10, although Firefox 3 is, of course, pre-installed.

In Edit > Preferences > External programs, I clicked on the +Add button for the Browsers section, then entered the Label "SeaMonkey", along with the following Command:

```
/usr/bin/seamonkey "%s" & -new-tab
```

The command must be *exactly* as shown to get SeaMonkey to start up correctly and read the file.  If it isn't *exactly* as shown, SeaMonkey may not start at all, or it may not find files with spaces in the filename.

After the command is pasted or typed into the Command window, press "Enter" on the keyboard.  Drag the new SeaMonkey entry with the mouse to the top of the list:  The "View in browser" button on the Main Toolbar only accesses the first browser in the list.  Click the "Apply" button and then click the "OK" button.

_Note:_  I installed SeaMonkey using the [[COLOR="Blue"]Ubuntuzilla script[/COLOR]]("http://ubuntuzilla.wiki.sourceforge.net/"), not the Ubuntu Add/Remove tool. (This was done because the Add/Remove tool installed SeaMonkey in such a way that I was unable to upgrade SeaMonkey or  remove SeaMonkey the one time I tried it.  I ended up having to blow away the entire Ubuntu installation and start over to remedy the problem, but that's another story.)](*,)  The Add/Remove tool may install SeaMonkey in a different fashion. If the Bluefish external browser command doesn't work, it may be because SeaMonkey was installed in a path other than /usr/bin.  To discover the path, type the following command in a terminal window:

```
which seamonkey
```


Similarly, add Firefox as another external browser.  The command code is as follows:

```
/usr/bin/firefox -new-tab "%s" &
```

Again, I found experimentally that the command must be *exactly* as shown for the browser to start up reliably and also handle files with spaces in the name.

Note that the "-new-tab" parameter may be replaced with "-new-window" if you prefer that Bluefish document previews are displayed in a separate browser instance, instead of a tab in an existing browser instance.;)

---

### Post by andrew.46 on 2009-04-17
Hi Andrew_P,

Thank you very much for taking the time and making the effort to publish this information!

All the very best,

Andrew

---

### Post by Fastjack77 on 2010-07-09
Hi Andrew,

I could not preview my local pages (no LAMP set), even with the predefined command lines for other browsers (many I don't have installed).

Using the Firefox example you are giving, it's working fine. Thank you for sharing!

[On Ubuntu 10.04 Desktop AMD64, using BlueFish 1.0.7]

---

### Post by MasterNetra on 2010-09-28
Created a more through thread if needed:
[http://ubuntuforums.org/showthread.php?p=9900812#post9900812](http://ubuntuforums.org/showthread.php?p=9900812#post9900812)

---

