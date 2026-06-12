---
title: "evince"
date: 2015-04-16
forum: Desktop Environments
---

### Post by Skaperen on 2015-04-16
is there a keyboard or mouse operation in evince (PDF reader) to jump all the way to the top/start of the document?

---

### Post by TheFu on 2015-04-16
Perhaps I don't understand.  HOME/END keys work here in evince v3.10.3 (Ubuntu openbox/WM 14.04.2)

BTW - I don't understand your tag, but may be able to help if you explain - did you look at Blackmagic or Hauppauge 1212 devices?  Don't understand "i-frame-only" part.  Capture the whole video, then grab the i-frames in post.

---

### Post by ajgreeny on 2015-04-16
Try **Home** and **End**, just like most other applications.

---

### Post by Skaperen on 2015-04-18
> **ajgreeny said:**
> Try **Home** and **End**, just like most other applications.
nothing happened with those

---

### Post by TheFu on 2015-04-18
Try reinstalling evince - doubt it will help, but can't hurt.
Check the system key mappings.

---

### Post by Skaperen on 2015-04-18
> **TheFu said:**
> Perhaps I don't understand.  HOME/END keys work here in evince v3.10.3 (Ubuntu openbox/WM 14.04.2)
those did not work for me

> **TheFu said:**
> BTW - I don't understand your tag, but may be able to help if you explain - did you look at Blackmagic or Hauppauge 1212 devices?  Don't understand "i-frame-only" part.  Capture the whole video, then grab the i-frames in post.
i want to take SDI-HD input and have each frame individually compressed to a single i-frame (no p-frames) so i can easily play back just selected frames instead of a big group. e.g. GOP=1. this is to minimize the work my CPU needs to do. the card doing the compression so the data size is smaller.  all that i have found so far either do full compression to a high GOP level (usually mp4 which is OK) or do no compression at all (handling that data leaves little CPU time to do other stuff and needs 2 disks to keep up with it or needs more RAM).

[http://en.wikipedia.org/wiki/Group_of_pictures](http://en.wikipedia.org/wiki/Group_of_pictures)

i have seen software that does this .. an editor output for some other OS ... i need to do it in hardware for the injested stream and work with Linux.

i have seen NO support for VP8 or Dirac on the market (not a big issue but these would be easier to work with).

---

### Post by TheFu on 2015-04-18
[https://www.blackmagicdesign.com/products/ultrastudiousb3](https://www.blackmagicdesign.com/products/ultrastudiousb3) ?
" Work with full broadcast quality 10-bit video in compressed and uncompressed quality,"
Their website doesn't say "Linux" for this specific device, but they do support Linux solutions on most others - perhaps it is an oversight on the webpage?

---

### Post by Skaperen on 2015-04-19
> **TheFu said:**
> [https://www.blackmagicdesign.com/products/ultrastudiousb3](https://www.blackmagicdesign.com/products/ultrastudiousb3) ?
" Work with full broadcast quality 10-bit video in compressed and uncompressed quality,"
Their website doesn't say "Linux" for this specific device, but they do support Linux solutions on most others - perhaps it is an oversight on the webpage?
i don't see enough technical data to see how it does compression

---

### Post by Skaperen on 2015-04-19
i was trying to do it during a search and does not work there.

i tried **HOME** outside of a search and it went to the first index page ... page 3 of the python library reference PDF.  i _still need to scroll up from there to get to the real top_, where the table of contents is.  i was trying to do that search on the table of contents.

---

### Post by TheFu on 2015-04-19
Perhaps if you click with mouse anywhere inside the doc first, then try "HOME"?  
If I recall correctly, searches work from the approximate point clicked - either up or down depending on the search direction used.

As to the blackmagic using compression or not.  Seems clear to me they do or they don't depending on a setting.  These guys provide hardware for professional video production houses.

---

