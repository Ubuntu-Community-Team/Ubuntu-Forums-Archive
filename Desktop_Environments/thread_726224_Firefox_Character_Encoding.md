---
title: "Firefox Character Encoding"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Ingla on 2008-03-16
Hello.

Firefox allows a choice of character encodings, but auto-detect doesn't seem to be among them. I'm looking at a page whose source specifies charset=iso-8859-1, which the browser should be reading correctly as that is the default., but only switching to UTF-8 works. 

Does anyone know how to get auto-detect to work or know what else might be wrong?

Thanks.

---

### Post by scragar on 2008-03-16
view > character encoding > auto detect > western/universal

---

### Post by Ingla on 2008-03-16
Thanks.

> view > character encoding > auto detect > western/universal

I have: view > character encoding > auto detect > universal as an option. I set it for that and restarted Firefox.

Strange! The problem persists. The page source says it's iso-8859-1 and view>character encoding indicates that's what it's reading. But it only displays correctly if I change it to UTF-8!

It's as if Firefox can't read the correct encoding and wants it to be UTF-8. Then it displays OK even though the page is encoded iso-etc.

Weird!

Any ideas?

---

### Post by patrickjlbyrne on 2008-04-02
I seem to have the same problem. Everything was fine until I selected a different character encoding. After that, whatever I set in the menu doesn't seem to persist, and the screen fills with mandarin on the next screen refresh.

Hyalp!

---

### Post by TWO on 2008-04-07
I have the same problem at the moment as well. I sometimes look at websites in French and I have the really annoying problem of c's with cedillas underneath appearing as either a question mark or some other odd symbol. Even with auto-detect set to 'universal' in Firefox, it just doesn't seem to do the trick.

---

### Post by ichi@YUKI on 2008-04-10
In some pages i get &#12461; instead of s.. Do you think Firefox needs an update? Enabling auto detect doesn't seem to do anything aside from making the page load slower.

---

### Post by guitarthrasher on 2008-04-10
> **Ingla said:**
> Thanks.



I have: view > character encoding > auto detect > universal as an option. I set it for that and restarted Firefox.

Strange! The problem persists. The page source says it's iso-8859-1 and view>character encoding indicates that's what it's reading. But it only displays correctly if I change it to UTF-8!

It's as if Firefox can't read the correct encoding and wants it to be UTF-8. Then it displays OK even though the page is encoded iso-etc.

Weird!

Any ideas?

Reinstall maybe? Do you have a recent release? You may have found a bug.

---

### Post by chimiasanchi on 2008-06-02
Hardy, Firefox 2. character encoding auto-detection is also not working for me, though Auto-Detection is selected in View -> Character Encoding -> Auto-Detect -> Universal. 

I'll post back here if I find the solution

---

