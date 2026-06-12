---
title: "No help files for Gnomebaker in Dapper"
date: 2006-07-29
forum: Desktop Environments
---

### Post by nativesun on 2006-07-29
All,

I've tried to find the help files associated with Gnomebaker.  I went to /usr/share/doc/gnomebaker and doesn't seem to be anything there.  I then reloaded the program using apt-get install and synaptic as well.  It didn't change anything.  I couldn't find any bugs on the issue.  Is there something I am missing?

---

### Post by catlett on 2006-07-29
When do you get that error? Is it when you first open up the application or whne you select a file to copy?

---

### Post by nativesun on 2006-07-31
It happens when I select Help-->Contents from the menus.

---

### Post by catlett on 2006-07-31
The help manual in Gnomebaker is brought up by Yelp. It is a documentation viewer for gnome. It is mostly used for viewing help files.
So I wonder if this is a yelp issue. For the heck of it, run ```
sudo apt-get install yelp
```Or open up nautilus and try to access it's help contents and see if you get the same result. If you can recreate the error in Nautilus than it is a yelp issue. If not then it is a gnomebaker issue.
If it is gnomebaker, maybe you can find the help documentation here. [http://gnomebaker.sourceforge.net/v2/](http://gnomebaker.sourceforge.net/v2/)

---

### Post by nativesun on 2006-08-05
Installing yelp did the trick.  That's wierd yelp was not already be installed.  It works fine now.  Thanks for the help.

---

### Post by catlett on 2006-08-05
> **nativesun said:**
> Installing yelp did the trick.  That's wierd yelp was not already be installed.  It works fine now.  Thanks for the help.

That's strange. It appeared to be yelp because the help wasn't opening up but I didn't think yelp wouldn't be installed. That's why you try everything when you troubleshoot. Take care.

---

