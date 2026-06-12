---
title: "[SOLVED] fonts:/// not a directory - can't import font"
date: 2006-09-13
forum: Desktop Environments
---

### Post by altonbr on 2006-09-13
I created a font in Windows lat year.. and I was just reminded of it recently so I want to install it on my Linux system.

I've used the simple drag & drop method of opening fonts:/// and my font collection and simple dragging them from point a to b... but it doesn't seem to work with this font I created; possibly it has to do with incorrect settings I used on export... amateur... or something else?

So I rebooted to see if it would come up afterwards (an ol' Windows trick), but it didn't.

I tried 'sudo cp /media/brett/fonts/BrettFont.ttf fonts:///' in bash.. but of course it complained because fonts:/// isn't a valid directory... and I also tried 'sudo nautilus' and drag & dropped again, but that didn't work.

So I have two questions:
1) Does anyone know of a workaround for this ttf problem?
2) What is fonts:/// anyway? I've seen Firefox using it when it opens up a file on your hard drive... AND I think Windows uses it for the Recycler.. but I'm not certain on that one. Is it a hidden absolute path (such as a shortcut) to a system folder?

Thanks for your help. :?

---

### Post by altonbr on 2006-11-14
I found this website explaining GnomeVFS (Virtual File System), and how "fonts:///" works if anyone is interested.

[http://developer.imendio.com/publications/writing_gnomevfs_modules]("http://developer.imendio.com/publications/writing_gnomevfs_modules")

---

