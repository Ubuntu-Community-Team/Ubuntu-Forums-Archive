---
title: "February Screenshot Thread locking up FF"
date: 2013-02-09
forum: Forum Feedback &amp; Help
---

### Post by loukingjr on 2013-02-09
for some reason the February screenshot thread is locking up Firefox.

any thoughts?

---

### Post by xc3RnbFO8P on 2013-02-09
Maybe this (5 MB)

I can open the page in Firefox, but not in Chromium.

---

### Post by CharlesA on 2013-02-09
It was a nasty chunk of base64 code. It looks like someone tried to drag and drop a picture. It is removed now.

---

### Post by loukingjr on 2013-02-09
> **CharlesA said:**
> It was a nasty chunk of base64 code. It looks like someone tried to drag and drop a picture. It is removed now.
thanks.

---

### Post by coffeecat on 2013-02-09
Just a FYI - we see these occasionally. They're almost certainly all caused by a firefox bug:

[https://bugzilla.mozilla.org/show_bug.cgi?id=729587](https://bugzilla.mozilla.org/show_bug.cgi?id=729587)

Long story short - if you are using Firefox and drag and drop an image into the wysiwyg message editor, you will trigger this bug and a huge wall of text - base64 code - will be inserted into your post between [noparse][img] and [/img][/noparse] tags. This causes browsers to freeze, which causes big problems for forum staff trying to deal with it!

Please use the thumbnail attachment facility or link to offsite images (so long as these are not too large). 

Will this still happen when the forum is upgraded? Yes, it will. I've tested it in the test forum. It's a firefox bug.

---

### Post by loukingjr on 2013-02-09
it's interesting although I don't know why someone would try and drag and drop an image into the editor. just a note, when I first saw the problem I tried opening the thread with Chrome and it failed as well although it didn't lock up.

---

### Post by lisati on 2013-02-09
> **loukingjr said:**
> it's interesting although I don't know why someone would try and drag and drop an image into the editor. just a note, when I first saw the problem I tried opening the thread with Chrome and it failed as well although it didn't lock up.

<aside>In approx. 15 years of using systems with a GUI, it has been extremely rare that I've had the need to use drag-and-drop. I have, however, noticed a handful of situations in more recent months that seem to prefer it over the "traditional" way of opening up a dialog box and giving a file name.</aside>

---

