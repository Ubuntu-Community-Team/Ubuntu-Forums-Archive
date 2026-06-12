---
title: "Thunar and mimetypes, spec. .doc"
date: 2011-03-25
forum: Desktop Environments
---

### Post by Copper Bezel on 2011-03-25
Hello all.

I love Thunar - it's the koi pond to Nautilus' English garden - but it's giving me a bit of trouble with text document mimetypes, or more properly extensions, since Thunar looks at extensions first. It recognizes .xml and opens gedit, it recognizes .docx and .odt and opens OpenOffice, etc., but if I right-click a .doc file and select Properties, it tells me that I'm looking at a Plain Text Document. If I select OpenOffice as the default application, then all Plain Text Documents load in OpenOffice, which is a bit of a pain in the *** if I'm loading a system configuration file or a plaintext shopping list made up in GEdit. 

For compatibility reasons at school, I have to use .doc for certain things, and I have a lot of old files saved in .doc format. The obvious solution would be to use .odt whenever possible and leave the Plain Text Document type associated with GEdit, but I don't want to have to right-click and select OpenOffice or drag files to my dock every time I want to open a .doc file. Is there any way to get Thunar to distinguish these extensions from one another?

Thanks for any help.

---

### Post by Krytarik on 2011-03-25
Hi Copper Bezel,

I just yet tried to reproduce the described behaviour, but it works as expected at my system.

1.) I created a new "Empty File", appended ".doc" to its name, and it gets recognized by both Nautilus and Thunar as "Word document", automatically associated with "OpenOffice.org Word Processor".

2.) The same is true for some old *real* .doc-files.

---

### Post by Copper Bezel on 2011-03-25
Well ****. What did I screw up? Oy ... I guess I'll live with it, then. = (

Thanks. = )

---

### Post by Krytarik on 2011-03-25
But Nautilus recognizes the mimetype of .doc-files correctly?

---

### Post by Copper Bezel on 2011-03-25
Yeah, but it's a completely separate system. Nautilus ignores extensions entirely, using only mimetype information, and it respects and sets Gnome's preferred applications instead of storing its own. If both Thunar *and* Nautilus were having problems with this, I would simply have to accept it as the will of the gods. = )

---

### Post by Krytarik on 2011-03-25
Could that be the solution? Do you have KDE installed?:
[https://bbs.archlinux.org/viewtopic.php?pid=551655#p551655](https://bbs.archlinux.org/viewtopic.php?pid=551655#p551655)

---

### Post by Copper Bezel on 2011-03-26
Yeah, I have parts of KDE installed. That fixed it - thanks! = )

---

### Post by Krytarik on 2011-03-27
> **Copper Bezel said:**
> Yeah, I have parts of KDE installed. That fixed it - thanks! = )
Great!

Then please mark this thread as "solved". LOL:D

---

### Post by Copper Bezel on 2011-03-27
Oh, right. :redface:

---

