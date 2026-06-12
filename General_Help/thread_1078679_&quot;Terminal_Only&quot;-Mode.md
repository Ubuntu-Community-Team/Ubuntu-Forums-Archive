---
title: "&quot;Terminal Only&quot;-Mode"
date: 2009-02-23
forum: General Help
---

### Post by Glakke on 2009-02-23
Hello.

First of I was not quite sure where to put this thread, so feel free to move it.

I have Ubuntu 8.10 Desktop Edition (Wubi at the moment, but that shouldn't matter?). I'm right now using it for normal work, but as well as hosting Left 4 Dead server (Game-server, which runs in terminal only).

So, I'm wondering if it is possible to run Terminal-Only-mode. Since this server requires quite a lot of CPU at some points, I'd like to dedicate the whole computer to this. 
Is it possible to start Ubuntu (or change desktop, something), and only see the terminal; but still be able to access Wireless (WPA2, password, and so on. And still be able to access files on the computer (in sudo).

To put it simple, a performance mode, just for the terminal and other important services/programs.
I do know there is a Recovery-mode which almost does what I want, but I don't think that is recommended - and I don't think Wireless/Internet works.

Thank you, hopefully this wasn't to messy. ^^

---

### Post by mb_webguy on 2009-02-23
I'm not familiar with Wubi, but if it uses GRUB, then you can [edit the GRUB menu to add a console login]("http://ubuntuforums.org/showpost.php?p=6782289&postcount=2").  This will be pretty much exactly like using the terminal, except that it's all there is.

You may have to add a script to automatically connect you your wireless network.

---

### Post by Glakke on 2009-02-23
> **mb_webguy said:**
> I'm not familiar with Wubi, but if it uses GRUB, then you can [edit the GRUB menu to add a console login]("http://ubuntuforums.org/showpost.php?p=6782289&postcount=2").  This will be pretty much exactly like using the terminal, except that it's all there is.

You may have to add a script to automatically connect you your wireless network.

Okay, yeah, it makes use of GRUB.
I'm trying that right now. 

But now the biggest problem is how to do that Wireless script. :/

EDIT:

Actually, the script wasn't needed. It connected to my Wireless automatically, great, works like a charm!
Thanks a lot. :)

---

### Post by Glakke on 2009-03-15
Hello again, I'm back, with another question.
This mode works great, but the font is a bit big (or the resolution a bit too low). Is it possible to change this?

Right now I'm without a GUI. And all I want is smaller font or higher resolution. Guess the resolution is the better solution (see what I did there? ;)).

Thanks.

---

### Post by fcuk112 on 2009-03-15
try this:
[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)

---

### Post by Glakke on 2009-03-15
Thanks, works great. It's not the correct resolution (since the screen is widescreen), but a lot better.
And it's called TTY, makes sense, was quite hard to find any info about it when I didn't know the correct name. :)

Thanks.

---

