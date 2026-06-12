---
title: "Associating applications with file types"
date: 2006-10-24
forum: Desktop Environments
---

### Post by racsw on 2006-10-24
Hello,
  I cannot find the correct place to associate file types with certain extensions with certain applications, such as:

*.pdf with Acrocread
*.txt with Gedit
*.htm or html with Quanta.
etc,etc..

Can someone help?

Thanks,
Robert

---

### Post by meng on 2006-10-24
Generally this is fixed by right-clicking on a .pdf file, then go Properties > Open With and choose Acrobat Reader. Then repeat process for .txt and .htm files. Does this work for you?

---

### Post by racsw on 2006-10-25
Yes, that did work fine, I can't believe I never tried it.
Problem is, although it works at the moment, how do I tell the system that whenever I click on a .pdf file, I want Adobe Acrobat (acroread) to open it?

Thanks,
Robert

---

### Post by ayoli on 2006-10-25
association made in Properties > Open With will work for all the file of the same type (ie: you have choosen Acrobat to open .pdf files, now all .pdf files will open with acrobat)

---

### Post by CatKiller on 2006-10-25
> **racsw said:**
> Yes, that did work fine, I can't believe I never tried it.
Problem is, although it works at the moment, how do I tell the system that whenever I click on a .pdf file, I want Adobe Acrobat (acroread) to open it?

Thanks,
Robert

In the Open With window, fill the radio button next to Acroread.

---

### Post by Oleg Petrov on 2007-06-27
This works for me too, but who knows where (in which file) these association are stored?

---

### Post by ComplexNumber on 2007-06-27
> **Oleg Petrov said:**
> This works for me too, but who knows where (in which file) these association are stored?
you'll find most of them in **/usr/share/applications** and **~/local/applications** and  in your home directory. each one of the files contains the association between the application and type of file that it is (eg text, audio-mp3, etc).

---

### Post by Copter on 2007-07-19
> **ComplexNumber said:**
> you'll find most of them in **/usr/share/applications** and **~/local/applications** and  in your home directory. each one of the files contains the association between the application and type of file that it is (eg text, audio-mp3, etc).

Well, actually it is /usr/share/applications and **~/.local/share/applications**. Any way is there any app that can help setting proper file associations for GTK **and** QT apps? Maybe to handle mimeinfo or something?

copter :]

---

