---
title: "Quick and simple desktop search?"
date: 2009-08-21
forum: Desktop Environments
---

### Post by vickoxy on 2009-08-21
Hi,
i installed few days ago gnome-do which searches data and files really good. But the docky was to slow on my dell  mini 9 so i uninstalled it. Is there some good search tool for ubuntu 9.04?

I read that google desktop search is good, but i prefer some more suggestions...

Thanks

---

### Post by k3ttc4r on 2009-08-21
well, gnome does have a build-in search function. or you could use gnome-do, just not as a dock..

---

### Post by vickoxy on 2009-08-21
> **k3ttc4r said:**
> well, gnome does have a build-in search function. or you could use gnome-do, just not as a dock..

i just  added it in panel-but when i press it it opens new window-i would like it to have as bar.

Well, for the gnome do-needed to install to much things on my computer, and i do not know if i want that only for one search tool...

Thanks

---

### Post by vickoxy on 2009-08-21
I remember there was in dell´s ubuntu one quick search bar in gnome panel-never gave a try, but is there something like that for ordinary ubuntu?

Anyone used google-desktop?

---

### Post by vickoxy on 2009-08-21
Ok, i installed gnome-do. It performs just good. Still i can not change keyboard shortcut (super L i use to show desktop, and it won´t accept many keyboard tabs...?

Still i have one question more-is it possible to search inside text doc (pdf, doc...)? Does any search tool for ubuntu could do something like that?

---

### Post by vickoxy on 2009-08-22
> **vickoxy said:**
> I remember there was in dell´s ubuntu one quick search bar in gnome panel-never gave a try, but is there something like that for ordinary ubuntu?

Anyone used google-desktop?

So, i found finally that deskbar-applet. I installed and reinstalled beagle. Unfortunately, the beagle and gnome-do were showing not to many results for my comp. searching. E. g. integrated gnome-search -tool made job better (although not perfect-could not found hidden data). Still i would like to have gnome-search-tool integrated in deskbar-applet so that it instantly showing the results (so that i dont have to press in deskbar-applet "find", ,which opens new window). Is that possible?

Thanks

EDIT:
in gconf-editor i found handlers that deskbar applet is using-there is no gnome-search-tool. Is that maybe the issue? Can i add/and how gnome-search-tool to it?

---

### Post by vickoxy on 2009-08-22
Yes, the picture:

---

### Post by Copernicus1234 on 2009-08-22
In the preferences for the deskbar applet, you can add Files, Folders & Places to the Search. Is that the functionality you want?

You can also hook it up to a shortcut so when you press the keyboard combination and start typing, it will search right away for whatever you are typing.

---

### Post by vickoxy on 2009-08-22
> **Copernicus1234 said:**
> In the preferences for the deskbar applet, you can add Files, Folders & Places to the Search. Is that the functionality you want?

Yes, but it does not perform same search as gnome-search-tool. Actually it finds very small amount of files-still it points me in "action" to search needed file (e.g. work.doc)-then it open gnome-search-tool IN NEW WINDOW which finds needed file. 
So, i would like to have this finding in panel bar (as it does with beagle installeD, but beagle is too slow with indexing and my computer get too hot with beagle working behind)
Thanks

---

### Post by Copernicus1234 on 2009-08-22
Nope, think you will have to run Beagle to get Beagle-like functionality. :)

---

### Post by vickoxy on 2009-08-22
Any less hungry alternative for beagle?

Thanks

---

### Post by amsum on 2009-08-22
Here is my list of Desktop Search tools for Ubuntu
1) Google Desktop Search
2) Beagle
3) Tracker 
4) Locate

GDS and Tracker are definitely recommended

---

### Post by amsum on 2009-08-22
One more to add Recoll

---

### Post by amsum on 2009-08-22
> **vickoxy said:**
> Any less hungry alternative for beagle?

Thanks

I would suggest Tracker

---

### Post by vickoxy on 2009-08-22
One question more. In my home folder i have picture named green.jpg-in deskbar applet they are immediately shown-just click on them and they are open. But in the same folder i have my work.doc and it is not shown (not to mention others files and folders). I just don´t get it which criteria are there for desktop searching? Why some files are shown, some not?

---

### Post by amsum on 2009-08-22
> **vickoxy said:**
> One question more. In my home folder i have picture named green.jpg-in deskbar applet they are immediately shown-just click on them and they are open. But in the same folder i have my work.doc and it is not shown (not to mention others files and folders). I just don´t get it which criteria are there for desktop searching? Why some files are shown, some not?

GDS and Tracker they work on "Indexing". It means they index all the files first to their database and this whole process takes some time. You can see the indexing status there.
Also, sometimes they do miss some files and that is the reason why they are not so perfect.

I think th ebest Desktop Search Tool is X1 from yahoo but it has no linux version. Also, its paid application.

---

### Post by vickoxy on 2009-08-22
> **amsum said:**
> GDS and Tracker they work on "Indexing". It means they index all the files first to their database and this whole process takes some time. You can see the indexing status there.
Also, sometimes they do miss some files and that is the reason why they are not so perfect.

I think th ebest Desktop Search Tool is X1 from yahoo but it has no linux version. Also, its paid application.

Yes i realized that the indexing takes more time-but i am talking here about default ubuntu gnome-search-tool. It had just enough time to index all what is needed. So-my point is-deskbar-applet has quick search and some data/files are shown immediatelly, but some never.

---

### Post by vickoxy on 2009-08-22
Ok, i installed "recoll"-it performs well and fast-question-how to integrate it in deskbar-applet quick search?

---

### Post by vickoxy on 2009-08-22
> **vickoxy said:**
> Ok, i installed "recoll"-it performs well and fast-question-how to integrate it in deskbar-applet quick search?

found the answer here:
[http://sheehantu.wordpress.com/2007/05/30/enable-tracker-live-search-in-ubuntu/](http://sheehantu.wordpress.com/2007/05/30/enable-tracker-live-search-in-ubuntu/)

So, now i have tracker integrated in deskbar-applet, but i couldn´t set it to search all system (home is set by default), and if i add datasystem-soon as i close the setup window, all setups are gone by next time i open tracker setup window.

Does anyone knows how to adjust these preferences? (can i add just / to search all computer, or should i add /usr/ /tmp/-for each folder one line?) 


Sorry-i reinstalled recoll and instead installed tracker-so i am talking about tracker here.

---

### Post by vickoxy on 2009-08-22
> **amsum said:**
> Here is my list of Desktop Search tools for Ubuntu
1) Google Desktop Search
2) Beagle
3) Tracker 
4) Locate

GDS and Tracker are definitely recommended

Tried Tracker-very good and fast, but it seems it can not search hidden files.

So, i have some additional question:

a) does any desktop search tool searches for hidden files?
b) does e.g. Google desktop search performs indexing every time after restart?
c) tracker seems also to indexing after every restart again all data-it takes long and it is draining my weak dell mini9. Do i have any alternative to my wishes (hidden files/integrated in deskbar or panel bar/fast, quick and not hungry for resources)?

Thanks

---

### Post by vickoxy on 2009-08-22
P.S. Does gnome-do search hidden files?

---

### Post by amsum on 2009-08-23
> **vickoxy said:**
> Tried Tracker-very good and fast, but it seems it can not search hidden files.

So, i have some additional question:

a) does any desktop search tool searches for hidden files?
b) does e.g. Google desktop search performs indexing every time after restart?
c) tracker seems also to indexing after every restart again all data-it takes long and it is draining my weak dell mini9. Do i have any alternative to my wishes (hidden files/integrated in deskbar or panel bar/fast, quick and not hungry for resources)?

Thanks
a) There must be some settings in Preference option where you can ask it to search hidden files. Though can't say for sure
b) GDS doesn't index from scratch everytime you start. It just looks for new added or deleted files to update its indexing. You can always turn-off it (there is setting for that).
c) The above applies to Tracker also ... If you dont want your system to slow down, you just pause indexing.

---

### Post by vickoxy on 2009-08-23
It seems that tracker is searching hidden files. Still i have one question-i want to make him index all computer/files. There are two possibilities there where can i add it: something like: "places to index" and "place only one time to index"-do not remember it. So, whre should i add "COMPUTER". 

And yes:
b) GDS doesn't index from scratch everytime you start. It just looks for > new added or deleted files to update its indexing. You can always turn-off it (there is setting for that).
c) The above applies to Tracker also ... If you dont want your system to slow down, you just pause indexing. 
Beagle seems to index only once all computer and (i read) it uses > inotify to add only new/changed files into index. Is there something like that for metatracker/tracker (so, once installed that i do not have to worries about it)?

---

### Post by vickoxy on 2009-08-23
So, does anyone know if tracker indexes all computer files after each restart, or it makes complete indexing only once, and update changes?

Thanks

---

### Post by vickoxy on 2009-08-24
No, tracker does not search for hidden files:

[http://ubuntuforums.org/showthread.php?t=520853&page=3](http://ubuntuforums.org/showthread.php?t=520853&page=3)

---

### Post by Ric_NYC on 2009-08-24
Thanks for posting this thread.
I'm also looking for an efficient search tool in Ubuntu since the buit-in search tool is very slow.

I'll try Google Desktop.
 
My plan is to install something that doesn't slow the computer.

Any suggestions?

---

### Post by vickoxy on 2009-08-24
I tried google-desktop search-indexing take very long time, but it does not search hidden files. Tried also beagle-no hidden files (or i couldn´t find it) and indexing was very slow. Tried gnome-do-best looking and very fast and intuitive-but it is limited on indexing 3000 files (you can disable it in gconf-editor, but then the computer is realy, reaaaly slow...) and it has no built in metadata searching (inside of documents-it is metadata called?).

So for now i am just satisfied with **tracker** which i combine with **deskbar-applet** (installed libdeskbar-applet to make work tracker with deskbar). If you uncheck in deskbar setup option "stick to panel", deskbar is working the same way as gnome-do (not so fancy looking, but still efficient)-you can point keyboard shortcut to activate it, just like with gnome-do. Tracker is fast and it searches metadata-still found that some files it does not show, but the search results are impressive-and it has live search-very useful with deskbar)

Still  searching good tool that searches hidden files and if some knows any...

---

### Post by vickoxy on 2009-08-24
And tried recoll-gave good results but i uninstalled it because it has no deskbar integration.

UPDATE: if you point tracker to search hidden files-it will do it, but not very deep (e.g. /home/yourname/.config/, but if you point to search whole computer ("/") it will not search hidden files.

So, i hope to find some tool which would search whole computer with hidden files, so that do not have to point all hidden files...

---

### Post by vickoxy on 2009-08-25
UPDATE: i reinstalled yesterday tracker and installed beagle again. Why? Actually, i add some additional folder for tracker to search, and it takes much time to indexes it all-still it is fster than beagle, but tracker performs searching/indexing after each restart/hibernate. I use netbook, so most of the time is then search tool for me useless.

Beagle makes only initial indexing (which takes long time), but after that it just updates changes. So after each restart/hibernate you can use your search tool. And i made some tests-beagle performs little bit better metadata searching-points more results. No big difference, but noticed that...
But live search in deskbar is slower with beagle.

Yes, does anyone knows how to make deskbar to show thumbnails/icon when displaying beagle quick search results? Tracker had that little icons...


So, it seems that every search tool has some pros and cons... Well see now how will beagle work...

---

### Post by vickoxy on 2009-08-25
UPDATING my monologue;

i don´t know how i  didn´t notice it before but **gnome-do** has **tracker-plugin**. So this is interesting. Something more interesting is that beagle plugin is maybe coming:

[http://blog.wurzt.de/index.php/2008/02/26/gnome-do-xesamsearch-beagle-suche-plugin/](http://blog.wurzt.de/index.php/2008/02/26/gnome-do-xesamsearch-beagle-suche-plugin/)

So, please, when someone find something like that, post it somewhere here...

---

### Post by Brazen on 2011-09-13
Just read this because I'm looking into desktop and file server indexing.  It seems like Xapian is the up-and-coming search backend, which is used by Recoll, which you mentioned.  I was also hoping to find some deskbar integration, so I'm probably going to give Tracker a try.

Update: I just found that there is another project called Pinot that also uses Xapian.  Pinot does include deskbar integration, so I might have to try out Pinot and Tracker and see which one I like better.

---

