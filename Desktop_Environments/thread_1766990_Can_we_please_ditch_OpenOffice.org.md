---
title: "Can we please ditch OpenOffice.org?"
date: 2011-05-25
forum: Desktop Environments
---

### Post by usagiakumu on 2011-05-25
I am a huge Calligra (formerly named Koffice) user. It provides more bang for the buck as far as office applications go for me. It has more options that I actually use and works generally smoother with KDE 4.6 than does LibreOffice and OpenOffice.org. 

Not only does it run smoother, fonts line up in Kword and when I edit large documents they don't get all garbled up like in OOo and LOo; Kspread has a lot of the options of Excel that I actually use including in-line function calculations, in Calc I have to start an entirely new entry to impliment functions and then re-enter it into the line an entire extra step and doesn't even work properly, Kpresenter has options such as putting a video in the background and imports circle and pie charts from Kspread and portions of Kword which can be called in with as little as 4 or 5 mouse clicks. Not only that it includes things like Kivo and Karbon both of which don't even exist as far as I know for Open Office I mean sure Draw offers basic functionality, but if you want to get anything professional done in a sane amount of time, Kivo and Karbon really take the cake here. Open Office has nothing that can compare with Krita or Kexi. 

Size comparison
Koffice 2.3.1 - 72.18MB
OpenOffice.org 3.3.0 - 147MB
This means an extra 74.82 MB extra CD space for the installer, meaning extra room for other enhancements.

Somehow Koffice is smaller yet has 10X the options and functionality...

Need I go on? Yes it serves a purpose, on Gnome where it belongs for those who like that sort of thing. I am in no way going to deny the strengths of Open Office such as cross platform functionality and Microsoft compatibility that Koffice lacks without plugins (which are very easily added from the repos, mind), but for the sake of functionality, you know workflow and getting work done, please ditch Open Office on Kubuntu. Not to mention an "arguably" better laid out interface. But Calligra now runs on Windows and Mobile devices, OpenOffice "runs" but not well on Android and acceptably on MeeGo but Calligra runs smoothly on both platforms. It works very well on Windows too, which until recently has been OpenOffice.org's personal playground. When Tested I saved battery life when using Calligra vs OOo.

For those interested in seeing the workflow I speak of see [http://www.calligra-suite.org/news/calligra-2-4-snapshot-1-tour/](http://www.calligra-suite.org/news/calligra-2-4-snapshot-1-tour/)

Kwrite starts in 4.02 seconds cold
OOo Writer starts in 6.44 seconds cold
Kwrite peak ram usage 38.22mb
OOo Writer peak ram usage 69.88~71.22MB

Sure ram is cheap but more ram = extra processor cycles which means slower response times which one can actually feel. Just because something is the popular choice doesn't mean its the better one. Not to mention draining your battery in devices.

---

### Post by cespinal on 2011-05-25
In Kubuntu, what can we get from the repos? Calligra or Koffice? I am not a fan of OOo or LO so I woundt mind giving this a try.

---

### Post by usagiakumu on 2011-05-25
Calligra is Koffice 2.4. Koffice 2.3.1 will be the last version of KDE Office Suite with the name Koffice. And no it is missing from the repos, you have to download the snapshot deb from their website or extract the tar file and do a simple ./setup and it opens a graphical installer. The installer doesn't always work. You can compile it yourself or:

If you are super lazy, [http://forum.kde.org/viewtopic.php?f=139&t=92880](http://forum.kde.org/viewtopic.php?f=139&t=92880)

I personally use Git as it makes sure all your QT applications are squeeky clean and makes sure everything works together. Should an application try to take out QT, Git allows some padding and saves you from hassles. 

[http://techbase.kde.org/Development/Git](http://techbase.kde.org/Development/Git)

KDE still has power, but remember with power comes responsibility.

If you are unsettled with getting the keys to your car and driving yourself just yet you can assimilate Koffice 2.3.1 from the collective borg a.k.a. repos. sudo apt-get install koffice One thing that really bothers me about Gnome is that it robs you of the power that Linux used to be known for, and now with the new cutsey Unity and Gnome 3, I am thankful for 4.6.

---

