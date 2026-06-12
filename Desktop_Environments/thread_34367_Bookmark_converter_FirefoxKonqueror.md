---
title: "Bookmark converter Firefox/Konqueror"
date: 2005-05-14
forum: Desktop Environments
---

### Post by drx on 2005-05-14
Dear Kubunters,
can you recommend a tool that converts or merges bookmarks in between Forefox and Konqueror. I am using different computers with different setups and could really use this.
Thanks again,
drx

---

### Post by mveers on 2005-05-14
>  can you recommend a tool that converts or merges bookmarks in between Forefox and Konqueror 
You can try this:

- Open Konqueror
- Bookmarks->Edit bookmarks
- File->
    Import->Import Mozilla Bookmarks
    then locate /home/USER/.mozilla/firefox/PROFILE/bookmarks.html
    or
    Export->Export Mozilla Bookmarks


or you can take a look at:
[http://bookmarkbridge.sourceforge.net/index.html]("http://bookmarkbridge.sourceforge.net/index.html")
[http://pyxml.sourceforge.net/topics/xbel/]("http://pyxml.sourceforge.net/topics/xbel/")
[http://www.extensionsmirror.nl/index.php?showtopic=15]("http://www.extensionsmirror.nl/index.php?showtopic=15")
[http://www.extensionsmirror.nl/index.php?showtopic=1366]("http://www.extensionsmirror.nl/index.php?showtopic=1366")

Hope this helps.

---

### Post by drx on 2005-05-16
Thank you!
At the moment i am happy with the import/export functions of Konqueror. I tried to get bookmarkbridge, but it will not compile, claiming i do not have QT libs installed. I know this is off-topic, but what packages are needed to compile such a QT application?

I have installed:
libqt3c102
including 
-ibase
-mt
-headers
-mt-dev

plus
qt3-apps-dev
qt3-dev-tools

Still i did not manage to build a QT application yet.
I wasn't able to find something in the forum, so if somebody could help me out i would be grateful.

Greets,
drx

---

### Post by mveers on 2005-05-17
[QUOTE=drx]
 I tried to get bookmarkbridge, but it will not compile, claiming i do not have QT libs installed. I know this is off-topic, but what packages are needed to compile such a QT application?

I have installed:
libqt3c102
including 
-ibase
-mt
-headers
-mt-dev

plus
qt3-apps-dev
qt3-dev-tools
[/QUOTE]

I have the same packages,
bookmarkbridge complained about qt, but after

 ```
 ./configure --enable-mt --with-qt-dir=/usr/lib/qt3/ --with-qt-includes=/usr/include/qt3/
``` 

it compiled without problems :)

Edit: lol, after all  "apt-get install bookmarkbridge" was enough :)

---

