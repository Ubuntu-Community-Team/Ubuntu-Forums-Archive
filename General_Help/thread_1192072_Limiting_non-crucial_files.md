---
title: "Limiting non-crucial files"
date: 2009-06-19
forum: General Help
---

### Post by dark2025 on 2009-06-19
I have Ubuntu set up on a computer with a very limited hard drive space. Is there a way to disable (or at least reduce) the system's use of space for non-crucial files? I cleaned up my system today and deleted about 130mb of archived installers and 40mb of crash logs. I also cleaned up about 50mb of various program caches, as well as getting rid of the non-English language files. How can I limit these kinds of files? And are there any other types of these files I can get rid of safely? Thanks.

---

### Post by pytheas22 on 2009-06-19
You should be able to delete everything in /var/log safely, as long as you don't mind not being able to view your system and application logs.  Of course, this directory will fill up again on its own unless you turn off all the logging features on your system (I don't know how to do that off the top of my head).

Ubuntu comes with files in /usr/share/example-content that you could delete safely.  They're just the stuff you see inside the "Examples" folder in your /home directory.

Otherwise, I think the best way to save space is just to remove applications.  OpenOffice takes up a huge amount of space.  You could also try replacing Gnome with a lighter desktop environment that uses less disk space.

You might also think about purchasing a USB stick to alleviate your space issues; it should be relatively cheap.  If you wanted, you could even set Ubuntu up so that an external USB flash drive is integrated into your system as /home or something like that.

---

### Post by dark2025 on 2009-06-19
Thanks for the reply. I deleted those things and now have some extra room (except for OpenOffice, I'll be needing that).

My good computer broke down recently so I'm forced to use this one. I will probably just get another computer in a while, but for now this is doing its job.

---

### Post by pytheas22 on 2009-06-19
Glad that helped a bit.

Another thought: you may be able to replace OpenOffice with something lighter like Abiword, depending on your needs.  Also, you could get rid of the parts of OpenOffice that you don't use (e.g., if you only use the word processor, delete Impress and Calc).

---

