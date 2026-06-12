---
title: "floppy and CD disk filenames cut off"
date: 2005-05-27
forum: Desktop Environments
---

### Post by cinematography on 2005-05-27
I copied a file from my Windows computer to a floppy. When I load the floopy in Linux, this is how many of my filenames look: dock&s~1.doc

Is there a way to correct this? Or do I have to rename my files everytime. :(

---

### Post by jasmuz on 2005-05-27
[QUOTE=cinematography]I copied a file from my Windows computer to a floppy. When I load the floopy in Linux, this is how many of my filenames look: dock&s~1.doc

Is there a way to correct this? Or do I have to rename my files everytime. :([/QUOTE]
 And?
That means that windows uses a long name caracter attribution, wich linux sees it as simple...its the same file, and you will save it the same way.

Try saving the files with shorter names.

---

### Post by cinematography on 2005-05-27
[QUOTE=jasmuz]And?
That means that windows uses a long name caracter attribution, wich linux sees it as simple...its the same file, and you will save it the same way.

Try saving the files with shorter names.[/QUOTE]
I have hundreds, if not thousands, of document files on my Windows computer. You're telling me I have to rename all of them to shorter names just to use them in Linux?

---

### Post by cinematography on 2005-05-27
Here is the real solution: 

Enter the following into your terminal: 
[color=blue]*sudo gedit /etc/fstab*[/color]

Replace this line: 
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

With this line: 
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

Save and reboot.

---

