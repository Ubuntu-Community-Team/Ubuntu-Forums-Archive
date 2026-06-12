---
title: "Preload a pdf document"
date: 2014-09-26
forum: Desktop Environments
---

### Post by mIXpRo on 2014-09-26
hi ,
i have a pdf documents their sizes between 7-15 mb each file contains between 7-10 pages (each page is a picture with text in it like a scanned lectures) . 
i tried qpdfviewer (lite multitabs) and default document viewer in ubuntu to open them but they only display first page and when i scroll to the next page they have to load the page before they can display it , 
and its very annoying that you have to wait each time you scroll a page for it to be displayed , is there a way to tell the viewers to load all the document from the beginning  ?

---

### Post by tgalati4 on 2014-09-26
Open a terminal:

```
man evince
```

There is a page switch.  Perhaps you could put in the last page or a middle page and that will load more of the document.  Linux has a preload facility, but it only preloads modules and libraries (to my knowledge) to improve snapiness, not user data.  Perhaps write a script to load two instances of evince with *--page-index* set to two different values.

Try this:

```
evince --page-index=50 my-50-page-document.pdf
```

close it.

```
evince --page-index=10 my-50-page-document.pdf
```

Time how long it takes for the second invocation.  Is it faster?

---

### Post by mIXpRo on 2014-09-26
i tried it only load evince with the specified page :/ 
maybe its a memory thing since my pdfs are kindda large compared to regular pdf ,and i tried opening a smaller pdf and the page loading is much faster, is there a way to give the viewers more ram ?

---

### Post by tgalati4 on 2014-09-26
You can speed some programs up by creating a RAMdisk at boot and copying your files to it during bootup.  The downside is that RAM is always locked up so it lowers RAM for other applications.  Older versions of Firefox (with extensive cache reads and writes) benefitted from a [RAMdisk]("https://wiki.archlinux.org/index.php/Firefox_Ramdisk").

It's a lot of work to set up.  It may or may not help your Use Case.  Only testing will tell.

All programs in Linux can take as much RAM as they require.  There may be a buffer preference in evince, but you will have to search for it.  How much RAM do you have?

```
free
```

---

### Post by mIXpRo on 2014-09-26
8 GB ram

---

