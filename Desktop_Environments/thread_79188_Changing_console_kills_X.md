---
title: "Changing console kills X?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Vermyndax on 2005-10-19
I was logged into my new, squeaky clean Breezy Badger release and was demonstrating a few things to a friend.  I wanted to go to full screen text mode, so I hit ctrl-alt-f1 and went to a console.  Then when I came back to ctrl-alt-f7 to get to x windows, it restarted X!

So, was that a security decision?  Any way to put it back?

---

### Post by grj on 2005-10-19
Doing as you mentioned works fine for me. Do you have a vga=<number> for framebuffer in your grub configuration. I had that in Hoary and had to remove it or X was messed up when I came back.

---

### Post by Vermyndax on 2005-10-20
Now here's something even more bizarre.  It works fine on my Ubuntu machine at home  I guess I will see what it does at work again.

---

### Post by NewWithoutClue on 2005-10-20
Use the left alt and ctrl rather than the right



Regards,
Paul.

---

### Post by Vermyndax on 2005-10-20
Hi Paul... thanks for your reply.

I did use the left ctrl and alt... now here's the difference between my work and home machines.

My work machine, where this occurs (and still does) is the x86 install of Ubuntu.  My home machine is pure AMD64.

---

### Post by NewWithoutClue on 2005-10-21
So it did not work? or, did it?
I sort of freaked out when i couldn't switch back also...but tried the left and it worked...so when i saw your post i thought it might be of help.

if it did not work...as much as i hate saying this, i dont know how else to help you, i'm sorry.


Regards.

---

### Post by Riverside on 2005-10-21
[QUOTE=Vermyndax]I was logged into my new, squeaky clean Breezy Badger release and was demonstrating a few things to a friend.  I wanted to go to full screen text mode, so I hit ctrl-alt-f1 and went to a console.  Then when I came back to ctrl-alt-f7 to get to x windows, it restarted X!

So, was that a security decision?  Any way to put it back?[/QUOTE]I haven't tried this on Breezy, but traditionally Alt+F7 (not Ctrl+Alt+F7) is the way to get back to an X session from a virtual console.  Try that.

---

