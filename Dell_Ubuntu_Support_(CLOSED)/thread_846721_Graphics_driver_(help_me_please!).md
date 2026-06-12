---
title: "Graphics driver (help me please!)"
date: 2008-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dougbe on 2008-07-01
I have a major problem: For whatever reason I couldn't get any videos to play in ubuntu. So I tried changing the video drivers. I selected what I thought was the appropriate one and the machine informed me that I needed to log out in order for the changes to take effect. Apparently I made a big mistake and now when I try to boot into Ubuntu I can only get to the terminal prompt (with no graphical log-in screen or anything). So my question is:

How can I find and setup the appropriate graphics driver from the terminal prompt?

My system looks like this:
Dell Inspiron 1520.
Dual booting Windows XP and Ubuntu 7.10
Mobile Intel(R)965 Express Chipset Family

I really need to be able to get back into linux to work on some important files! Please help me out and I promise never to mess with my graphics driver settings again.

---

### Post by dougbe on 2008-07-02
Okay, so after searching the forums for a while I found the solution. I ran the command

sudo dpkg-reconfigure xserver-xorg

Auto-detected everything and rebooted. This time I got my graphical log in screen back and things were back to normal.

---

