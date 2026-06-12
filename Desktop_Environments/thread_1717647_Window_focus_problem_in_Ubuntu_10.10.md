---
title: "Window focus problem in Ubuntu 10.10"
date: 2011-03-30
forum: Desktop Environments
---

### Post by jander on 2011-03-30
Hello,

A few weeks ago I noticed some kind of window focus problems in my desktop.

When a new window opens, the focus doesn't change to it, remaining in the previous window. This happens now and then, not always.

Examples:

- In Nautilus, I double click on a PDF and the application starts as expected. If I press Ctrl-F4, the PDF viewer stays running and the Nautilus windows (which is hidden or partially hidden in the back) closes.

- In software updates, when a window opens requesting for the password, I have first to click on it, so it gains the focus, before typing my password.

Any hints on how to solve this?

Thanks in advance.

---

Ubuntu 10.10 with Compiz

---

### Post by Blasphemist on 2011-03-30
First, not sure I have your solution. My running Natty may make getting to it in Compiz slightly different. I also have to admit not having full understanding of the settings in Compiz, General settings. 

Look at your settings on the Focus & Raise Behavior tab. Is Auto-Raise selected? If so, de-select it. I don't yet understand the Focus Prevention Level and Windows settings but they might also affect the behavior you see.

---

### Post by jander on 2011-03-30
Hey, Jim

Setting the Focus Prevention to None solved my problem. Everything seems back to normal again.

Selecting or de-selecting Auto-Raise made no noticeable difference.

Thanks for pointing into the right direction.

*Jander*

---

### Post by Krytarik on 2011-03-30
> **jander said:**
> 
Setting the Focus Prevention to None solved my problem. Everything seems back to normal again.
I have set those option to "Low". Doesn't it work also at your system?
> **jander said:**
> 
Selecting or de-selecting Auto-Raise made no noticeable difference.

Those option affects if a window you mouse-over at gets auto-raised after the amount of time specified by the option "Auto-Raise Delay" (milliseconds).

---

### Post by jander on 2011-03-31
> I have set those option to "Low". Doesn't it work also at your system?

Unfortunately the only option that worked was 'None'...

> Those option affects if a window you mouse-over at gets auto-raised after the amount of time specified by the option "Auto-Raise Delay" (milliseconds).

I didn't mean this option had no effect at all... I just said it was irrelevant to the mentioned problem. :-)

Thanks!

---

