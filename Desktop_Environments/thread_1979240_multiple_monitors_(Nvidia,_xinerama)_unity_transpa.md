---
title: "multiple monitors (Nvidia, xinerama) unity transparency lost and other effects also"
date: 2012-05-13
forum: Desktop Environments
---

### Post by SuppoTaalasmaa on 2012-05-13
Hi,

I just made a fresh install of 64-bit 12.04, and everything was pretty much as it should be after installation, except my second monitor was black.
So I first enabled it in the nvidia control panel, and still everything was working as it should. Only the screen was extended to another monitor, but since the second is smaller, I have rotated it 90degrees, and wanted to adjust the Ubuntu for this.

I understand that there is no other way to get that working, except using Nvidia's Xinerama feature, and I enabled it, and did some xorg configuration changes.
Now, all works as it should, except that for some reason Unity has lost some of it's eyecandy. 
Most of the transparency seems missing (for example the help text on icons in the launchbar looks like this: 
[http://postimage.org/image/u8k7ilnsl/]("http://postimage.org/image/u8k7ilnsl/")

As you can see from the launcher, it's not transparent, and on the sides you see that "grey with white dots" edge, which is the color or most "transparent boxes", such as help text when mouse is hovering over launchbar icons.. 

So, I wonder what I should do to get Unity working as it should again? 
My xorg.conf: [pastebin link]("http://paste.ubuntu.com/984926/")

Thank you for all the suggestions!

---

### Post by SuppoTaalasmaa on 2012-05-13
Just for followup, this might be this bug here:
[https://bugs.launchpad.net/ubuntu/+source/libxinerama/+bug/973419]("https://bugs.launchpad.net/ubuntu/+source/libxinerama/+bug/973419")

---

