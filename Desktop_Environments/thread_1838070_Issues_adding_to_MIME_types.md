---
title: "Issues adding to MIME types"
date: 2011-09-02
forum: Desktop Environments
---

### Post by shmibs on 2011-09-02
I was trying to add MIME types and default icons for gnome 2.32 using this tutorial:
[https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes)
and am running into some baffling results.

first, i edited /etc/mime.types to include my new file extensions, and checked to see if they had been successfully added through 

grep '[filetypes]' /etc/mime.types

which they had been. then i added 48*48 .png's with the naming conventions the tutorial said to use to 48*48/mimetypes under both the gnome icon set and the one i was currently using, and then did the same with .svg's under scalable/mimetypes for both. after restarting gnome, this had no effect whatsoever on the appearance of the files, which still had the generic icons they had before.

i would have assumed i was doing something stupid somewhere along the way and left it at that, but i tried the example given in the tutorial, adding an svg image for .py files, and had the same result. i've made sure to follow every instruction given in that tutorial, going over it multiple times, with no results.

does anyone have any clue what might be going on? i'd give more information, but i don't know what to include.

---

