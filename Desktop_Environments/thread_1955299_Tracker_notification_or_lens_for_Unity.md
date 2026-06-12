---
title: "Tracker notification or lens for Unity?"
date: 2012-04-09
forum: Desktop Environments
---

### Post by sambhogi on 2012-04-09
I am setting up a system for a friend, and I want to make it as easy to use as possible. With the advent of Unity there is no longer a default indexing search feature to search all files, which to me is a big step back for a modern OS, and so I am installing Tracker manually. However, there appears to be no replacement for the Tracker search bar which exists for the Gnome panel. Has anyone developed an indicator or lens for Unity?

While I like Unity overall, there are 2 things that I find real drawbacks: the lack of a convenient and obvious way to organize files/apps (for example, by tagging) that replaces the menu system, and the lack of an easily customizable panel - this must be one of the biggest annoyances across the board, because it makes it a pain to access some applications, of which the most important for me are CryptKeeper (which I have since figured out) and the Tracker search bar.

---

### Post by pt123 on 2012-04-11
I have found Tracker to be poorly maintained on Ubuntu, and the application is all over the place. It has numerous "applications" for different aspects, but none of them are referred or linked to each other.

---

### Post by sambhogi on 2012-04-11
Is there an alternative indexing search tool that you think is better? If not, my original question still stands.

---

### Post by kiirokurisu on 2012-04-11
Ubuntu/Unity uses Zeitgeist by default to index files and folders as well as recently used items. You can also install the zeitgeist-fts package to get full-text search features (searching file contents). This seems to cover most of the features of Tracker, at least the ones I used.

---

### Post by pt123 on 2012-04-11
> **sambhogi said:**
> Is there an alternative indexing search tool that you think is better? If not, my original question still stands.

I created a similar thread before
[http://ubuntuforums.org/showthread.php?t=1701012](http://ubuntuforums.org/showthread.php?t=1701012)

This page was suggested

[http://www.wikinfo.org/index.php/Comparison_of_desktop_search_software](http://www.wikinfo.org/index.php/Comparison_of_desktop_search_software)

Pinot looked promising but I couldn't install it because of a package conflict with LibreOffice ( this might have been fixed). Also Pinot's homepage is hosted on poor web server and there are security certificate exceptions. The have moved it to google but there are no screenshots on that page
[http://code.google.com/p/pinot-search/](http://code.google.com/p/pinot-search/)

---

### Post by sambhogi on 2012-04-11
Thanks for the tips. It appears zeitgeist-extension-fts is installed by default, but I cannot find where to configure it. It does not seem to index .doc, .odt, or .pdf files. Nor can I see how to set Zeitgeist to index the entire home directory.

---

### Post by pt123 on 2012-04-11
there is a privacy tool in 12.04 which lets you configure zeitgeist but it's bloody hard to find

---

### Post by gts on 2012-05-14
Here you can find something:
[http://hoheinzollern.wordpress.com/2011/11/21/unity-tracker-lens/](http://hoheinzollern.wordpress.com/2011/11/21/unity-tracker-lens/)

---

### Post by sambhogi on 2012-05-14
Thanks! 

That link also led me to this one:

[http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html](http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html)

Hopefully one of these will be included in Ubuntu by default in the future, or at least as an option during install.

---

