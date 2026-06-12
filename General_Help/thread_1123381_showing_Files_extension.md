---
title: "showing Files extension"
date: 2009-04-12
forum: General Help
---

### Post by wolfheart_2001 on 2009-04-12
hi all,

how to show files extension in ubuntu using GUI and bash?

Regards

---

### Post by N_Nick on 2009-04-12
Are you using Gnome or KDE?

Correct me if i am wrong but Gnome does that by default

---

### Post by wolfheart_2001 on 2009-04-12
Its GNONE desktop interface,

i dont know, i just see the .gz extensions nothing more.

I also need to know how to do it using GUI + Command line

thanks pal

---

### Post by CatKiller on 2009-04-12
> **wolfheart_2001 said:**
> how to show files extension in ubuntu using GUI and bash?

Both of them show file extensions. Perhaps the files that you're looking at don't have extensions?

---

### Post by lovinglinux on 2009-04-12
Linux does not require file extensions to work properly, so lots of system files comes without them.

---

### Post by wolfheart_2001 on 2009-04-12
:confused:

sorry guys,thats new concept to me totally.

so how do i know the type of the file if it dont have an extension???how do i know the type of the application that can read the file properly??

and why some files have extensions like .deb , .gz and most files dont have extensions??

if file extensions are not important why some files do have one??

lot of questions i know;)

im still novice to linux

---

### Post by lovinglinux on 2009-04-12
> **wolfheart_2001 said:**
> so how do i know the type of the file if it dont have an extension???how do i know the type of the application that can read the file properly??

You can distinguish them through the icons and through the "Type" column in the file browser. Lots of files are just plain text documents, because Linux stores configurations in text files. Compare the "Type" column with the corresponding icon and soon you will be acquainted with each file type.

> **wolfheart_2001 said:**
> and why some files have extensions like .deb , .gz and most files dont have extensions??

Good question. I really don't know. If you remove the .deb extension they will still open with the package manager. If you remove an extension from a .gz, it will be opened with the archive manager but will give you an error. The same problem doesn't happen with zip tho.

> **wolfheart_2001 said:**
> if file extensions are not important why some files do have one??

It seems that some applications require file extensions.

---

### Post by mb_webguy on 2009-04-12
Linux uses the mime type to identify the file.  This is arguably better than relying on the file extension, since if the system relies on the extension, and the extension is changed, the file likely can't be opened.  And if you can't remember or don't know the original file extension, it can be a hassle to identify the file and restore the file proper file extension.  In Linux, it doesn't matter what you name the file or what extension you use, the system will always open the file with the correct application.  Also, by not relying on file extensions, an executable file, which could be anything from a binary executable to a script written in any of various languages, can be run like a command, with no extension necessary.

File extensions on Linux are really only to help users easily identify the file type.  If you view the files in List view in Nautilus, the Type column will identify the file type.  Also, you can view the mime type of the file by right-clicking the file and selecting Properties.  The mime type is the bit in parentheses in the Type line on the Basic tab.

---

