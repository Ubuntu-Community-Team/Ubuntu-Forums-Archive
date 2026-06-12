---
title: "Locations other than ~/.recently-used.xbel storing recent files info"
date: 2010-12-11
forum: Desktop Environments
---

### Post by wi0 on 2010-12-11
Hi,

As mentioned here [http://www.watchingthenet.com/ubuntu-tip-clear-disable-recent-documents.html](http://www.watchingthenet.com/ubuntu-tip-clear-disable-recent-documents.html)  even with writing to .recently-used.xbel is disabled, recently used files list is stored somewhere else, as it is written to this file once writing is enabled again.

That article doesn't go into any details on this, but I find this behaviour very odd.

Where is is somewhere else, and for that matter, why does it exist?

Thanks

---

### Post by AlphaLexman on 2010-12-11
Take a 'cat' look at each of the files from:
```
ls -a ~/.recently-used*
```

---

### Post by wojox on 2010-12-11
It exsists to open recent documents. To turn that off clear your recent docs, open a terminal enter these commands and reboot.


```
gedit ~/.gtkrc-2.0
```

Add:

```
gtk-recent-files-max-age=0
```

---

### Post by wi0 on 2010-12-11
Thanks for the quick replies.

> **AlphaLexman said:**
> Take a 'cat' look at each of the files from:
```
ls -a ~/.recently-used*
```
No other files appear in the directory. I can see what is stored in there, but this is not the only place the information is stored at as described below.
> **wojox said:**
> It exsists to open recent documents. To turn that off clear your recent docs, open a terminal enter these commands and reboot.

I understand the purpose of the file in title. I was wondering about where else this is stored.

> ```
gedit ~/.gtkrc-2.0
```Add:

```
gtk-recent-files-max-age=0
```That works very well. Thank you.

When this option is off, deleting .recently-used.xbel does not erase the list. When it is recreated upon opening another file, the files that were opened before the deletion are still listed. But choosing "Clear recent documents" option clears it.  This means that this information is stored elsewhere and that elsewhere is cleared by the "Clear..." option. I wonder where this elsewhere is.

---

### Post by wi0 on 2010-12-23
I don't suppose a bump after a week is unreasonable...

---

### Post by wi0 on 2011-02-07
If there's a specific source where I can read about this, please let me know. Otherwise, this question is still relevant, and certainly doesn't seem inane to me.

---

### Post by darwinacitizen on 2011-02-21
I'm too stuck wit the same problem in ubuntu 10.10 netbook.. Where is the another copy of recently used files being stored?! What exactly is done when we "clean the recent documents"?! Anybody out there with the answer or at least a bit of help...?

---

### Post by wi0 on 2011-05-05
In 11.04 there is no ~/.recently-used.xbel. I suppose this is because Zeitgeist completely replaces that functionality? At least we know where its data is stored: ~/.local/share/zeitgeist/activity.sqlite. Hey, maybe Zeitgeist was also in 10.10, and that was where the data was stored?

Correction: in 11.04 the location is ~/.local/share/recently-used.xbel that behaves the same as before (at least in "ubuntu classic"), so the question remains: where on earth is recent files list stored?

---

