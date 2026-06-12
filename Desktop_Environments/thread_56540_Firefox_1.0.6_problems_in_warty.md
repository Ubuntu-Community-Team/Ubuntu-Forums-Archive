---
title: "Firefox 1.0.6 problems in warty"
date: 2005-08-12
forum: Desktop Environments
---

### Post by WW on 2005-08-12
I'm having a few problems with Firefox 1.0.6 in warty:

1. When I download a file, the download manager window appears, but it doesn't show anything. However, the file *is* downloaded.

2. The first time I try to open a new tab, nothing happens.  After that, new tabs open fine.

3. When I use the search function (Edit->Find in this page, or Ctrl-F), and enter some text, the browser does not move to the text that it finds.  I have to use the "highlight" option, and manually scroll through the page, looking for yellow highlights.

Is anyone else having these problems?

---

### Post by gurdy on 2005-08-15
[QUOTE=WW]I'm having a few problems with Firefox 1.0.6 in warty:

1. When I download a file, the download manager window appears, but it doesn't show anything. However, the file *is* downloaded.

2. The first time I try to open a new tab, nothing happens.  After that, new tabs open fine.

3. When I use the search function (Edit->Find in this page, or Ctrl-F), and enter some text, the browser does not move to the text that it finds.  I have to use the "highlight" option, and manually scroll through the page, looking for yellow highlights.

Is anyone else having these problems?[/QUOTE]

I am having exactly the same problems. 

I had downloaded Firefox 1.0.6 from mozilla.org directly and installed it manually in my home directory, and it worked fine. When Firefox 1.0.6 finally appeared in Synaptic, I upgraded the version previously installed by Synaptic, and that's when the above problems appeared. And now the version I installed in my home directory won't run at all.

Help! Anyone have any suggestions?

---

### Post by WW on 2005-08-16
gurdy,

I did the opposite of you.  I have removed Ubuntu's firefox and installed the version from the mozilla web page.  I installed it in /usr/local/mozilla-firefox, and copied the plugins from /usr/lib/mozilla-firefox/plugins to /usr/local/mozilla-firefox/plugins.  I also made a symbolic link in /usr/local/bin to /usr/local/mozilla-firefox/firefox.  So far it is working fine.

WW

---

### Post by WW on 2005-08-16
For what it's worth, I filed bug reports at [http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/).  The reports are 13528, 13529 and 13530.

---

