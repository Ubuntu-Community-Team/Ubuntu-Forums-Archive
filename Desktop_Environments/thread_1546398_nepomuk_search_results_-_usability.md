---
title: "nepomuk search results - usability?"
date: 2010-08-05
forum: Desktop Environments
---

### Post by barna on 2010-08-05
Hi,

I am wondering how one can use the nepomuk/strigi file indexing service. I started up dolphin, and typed the search string in the upper right corner, and clicked Search. 

The search result is a long list of files. The one I need is a PDF file. When I select this file, on the right hand side there is the following info:
'Is part of: 15.2 GiB Removable Media' which is clearly wrong, since this file resides in my home directory, which is on a 200 GiB partition. If I double-click this file to open in okular, I get an error message: 
```

Could not open nepomuksearch:/nepomuk_3A_2Fres_...... Reason: Please insert the removable medium "15.2 GiB Removable Media" to access this file

```

I guess this is some old result from nepomuk's cache (in the meantime I have had to repartition my hard disk, and restore my home directory from a backup copy on an external hard drive - but this has been many months ago, so I would expect that nepomuk have had the time to recognize this)

If this is the case, how can I reset/clear nepomuk's cache?

Thanks

---

### Post by Kilroy2011 on 2011-02-22
> **barna said:**
> 

<snip>
If this is the case, how can I reset/clear nepomuk's cache?

Thanks

(may be outdated by now, but would have helped me a month ago)

I remove the [COLOR=Purple]nepomuk directory[/COLOR] in $HOME/.kde/share/apps
With a [COLOR=Purple]restart of the computer[/COLOR] indexing starts again.

Kilroy

---

