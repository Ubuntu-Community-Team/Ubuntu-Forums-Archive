---
title: "How to install themes??"
date: 2009-04-21
forum: General Help
---

### Post by mubbashar on 2009-04-21
i download themes in tar.gz extention please tell me how to install them

---

### Post by stilling on 2009-04-21
> **mubbashar said:**
> i download themes in tar.gz extention please tell me how to install them

go to system-> preferences-> appearance - > install go to where is the theme.tar.gz and open that is it

---

### Post by mubbashar on 2009-04-21
the theme installed but it show that required gtk+ theme engine is not installed ..so what can i do for this.

---

### Post by stilling on 2009-04-21
> **mubbashar said:**
> the theme installed but it show that required gtk+ theme engine is not installed ..so what can i do for this.

try this in terminal 
sudo apt-get update
sudo apt-get install gtk2-engines
sudo apt-get install gtk2-engines-smooth only if it need it !!!

---

### Post by mubbashar on 2009-04-21
thanksssssssssss

---

### Post by David C. on 2009-04-21
I am experiencing the same issue. However, when I did what was suggested System > Preferences > Appearance and selected install I clicked on the tar.gz file (which I saved to the Desktop) and received this error: Can't move directory over directory. 

I'm lost here...I extracted the files and saved them to the desktop, but still was not able to install the theme. What am I doing wrong?

---

### Post by stilling on 2009-04-22
> **David C. said:**
> I am experiencing the same issue. However, when I did what was suggested System > Preferences > Appearance and selected install I clicked on the tar.gz file (which I saved to the Desktop) and received this error: Can't move directory over directory. 

I'm lost here...I extracted the files and saved them to the desktop, but still was not able to install the theme. What am I doing wrong?

do not extract the archive simply open appearence drag and drop the tar.gz over the other themes and tell me what happend or says and give me the link  from where you download the theme please

---

### Post by David C. on 2009-04-22
> **stilling said:**
> do not extract the archive simply open appearence drag and drop the tar.gz over the other themes and tell me what happend or says and give me the link  from where you download the theme please

That's a negatve. Received the same error "can't move directory over directory" I even deleted the tar.gz and re-downloaded from  [**Gnome Art Metacity**]("http://art.gnome.org/themes/metacity") got the same error.

---

### Post by stilling on 2009-04-22
So most Metacity themes are one theme packaged as a .tar.gz you can drag and drop to theme manager window. if that one isn't a theme but a theme pack, meaning it's a .tar.gz full of other themes. So double-click the .tar.gz and extract it. If you see a bunch of folders, copy them to /home/username/.themes.If you don`t have it create it. If you see a bunch of other .tar.gz files, drag those to the theme manager window.
and there must complain if needs any gtk+ engine or something.
Hope This Will Help You

---

