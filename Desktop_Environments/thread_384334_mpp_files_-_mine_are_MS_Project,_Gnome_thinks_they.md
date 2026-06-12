---
title: "mpp files - mine are MS Project, Gnome thinks they are music"
date: 2007-03-14
forum: Desktop Environments
---

### Post by joncheyne on 2007-03-14
Hi folks

Just an annoyance really, using steelray viewer to look at the files from MS Project, all ok, but the default is for Gnome to think they are music, allocate a music icon and offer to preview the sound on hover over. :-)

How do I change this system wide? I can change one at a time using right click (although it still thinks they are playable) but not as a defailt.

I am assuming mime types but where to change this?

Many thanks

Jon

---

### Post by louis_nichols on 2007-03-14
When you right click the file, you will see an option "Properties". That will contain a tab "Open with". You can set there what app opens that file.

---

### Post by joncheyne on 2007-03-17
> **louis_nichols said:**
> When you right click the file, you will see an option "Properties". That will contain a tab "Open with". You can set there what app opens that file.
hi - yes, that I do already - I open them with my ms project viewer - but the icon stays a music symbol ( and if you hover it tries to preview) and surely I do not have to do this withr every new file that comes onto my laptop? 

Basically, nautilus or gnome thinks that it is a music file and still treats it as such, just allows me a choice of app. 

Cheers

Jon

---

### Post by louis_nichols on 2007-03-17
Make sure the checkbox is checked in the window. In the thumbnail I attached there is only one app, but in your case you should use the button Add to select gnucash and then click on its checkbox so it becomes the default. It will certainly work.

---

### Post by joncheyne on 2007-03-17
> **louis_nichols said:**
> Make sure the checkbox is checked in the window. In the thumbnail I attached there is only one app, but in your case you should use the button Add to select gnucash and then click on its checkbox so it becomes the default. It will certainly work.
It works, in that I have now selected to view my "Musepack Audio File" using my MS project viewer app - and yes globally. 

But, it still has a music icon ( a pair of green crotchets?) and on hover tries to "play" the file :-)

What I want is a place to edit what kind of mime type this is - from Musepack Audio to MS Project

I tried editing  /usr/share/mime/packages/freedesktop.org.xml but no change appeared
I grepped for mpp and musepack and found two references in /usr/share/mime/globs and in a related file. But these say DO NOT EDIt etc, updated by update-mime-database

So - I am thinking I have to go start editing some xml files to get this right?

Or is there some user friendly gnome application that help me?

Cheers all

Jon

---

### Post by joncheyne on 2007-03-17
ok, done it, well partly.

You create an Overrides.xml file in the mime/packages directory, put your blob in there and then run the update-mime-database command. For details [click here]("http://www.gnome.org/learn/admin-guide/latest/mimetypes-modifying.html#mimetypes-addmodify") 

Sorted in so far as no longer an audio file ... now for a default icon - off to modify another text file somewhere ...

While i know and respect that this is the unix tradition, I just feel that this needs fixed with a gui at some point as we head down(up?) the food chain of end user types and increased adoption beyond the early adopter ...

---

