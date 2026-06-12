---
title: "Setting width of panel items"
date: 2012-09-27
forum: Desktop Environments
---

### Post by werdnanoslen on 2012-09-27
How can I set the width of panel items, such as DateTime? My Datetime settings force a weird line break at its current width, so it needs to expand.

---

### Post by Toz on 2012-09-28
Hello and welcome to the forums.

If you right-click the applet and select Properties, what settings do you have enabled? I believe that if you use the "Date then Time" or "Time then date" formats, it will place it on two lines. You can change to "Date only" or "Time only", or create a custom command that will display on only one line.

---

### Post by werdnanoslen on 2012-09-28
> **Toz said:**
> Hello and welcome to the forums.

If you right-click the applet and select Properties, what settings do you have enabled? I believe that if you use the "Date then Time" or "Time then date" formats, it will place it on two lines. You can change to "Date only" or "Time only", or create a custom command that will display on only one line.

Well yeah, of course it would, but I want all that information there. I just need to know how to widen the space for it.

---

### Post by Toz on 2012-09-28
If you are referring to the 2-line display, the applet will widen enough to display the two lines - it won't create one line out of them.

You can reconstruct the information using a custom format (and it would appear on 1 line). I currently use:
```
%a %b %d - %l:%M %P
```
...but you can build on that to create whatever output format you would like.

The complete list of available formats can be found here: [http://manpages.ubuntu.com/manpages/precise/man1/date.1.html]("http://manpages.ubuntu.com/manpages/precise/man1/date.1.html").

---

### Post by werdnanoslen on 2012-09-28
> **Toz said:**
> If you are referring to the 2-line display, the applet will widen enough to display the two lines - it won't create one line out of them.

You can reconstruct the information using a custom format (and it would appear on 1 line). I currently use:
```
%a %b %d - %l:%M %P
```...but you can build on that to create whatever output format you would like.

The complete list of available formats can be found here: [http://manpages.ubuntu.com/manpages/precise/man1/date.1.html](http://manpages.ubuntu.com/manpages/precise/man1/date.1.html).

Ah, ok, I just had to crowd the whole thing into either the date or time field, and then select "date" or "time only." It seems kinda dumb, though, to force a new line between the two fields. :/

---

