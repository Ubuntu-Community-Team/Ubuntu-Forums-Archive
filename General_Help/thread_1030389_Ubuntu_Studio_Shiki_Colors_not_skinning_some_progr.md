---
title: "Ubuntu Studio: Shiki Colors not skinning some programs"
date: 2009-01-04
forum: General Help
---

### Post by propagation_of_sound on 2009-01-04
In ubuntu studio, I have installed the Shiki-Colors theme, and am currently using Shiki-Wise. 
However, some programs like synaptic and cruft remover don't skin. 
A friend using regular Ubuntu has no problems. 
Is there any way to skin these programs as well?
Thanks in advance.

---

### Post by davideotape on 2009-01-06
Hmm, I seem to be having a similar problem, but my openoffice 3.0 and create usb startup disk are also not skinning properly. It seems that the title bar of the application is skinning perfectly fine, but it is the toolbars and buttons in the app that are refusing to be skinned. I have attached my own screenshots of openoffice and usb startup disk.

---

### Post by Ivo Moelans on 2009-01-06
These are programs that run as root and so use the themes available to root (not to sure about OO 3.0 as I am still on 2.4, but you could try the solution anayway).
Solution: make the themes you use available to root. Open a terminal and type these three commands. They make a link in the home directory of root to respectively your themes, icons and your locally installed fonts (if any).

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

Let me know how it goes.

---

### Post by davideotape on 2009-01-07
Thanks a lot, that worked perfectly with synaptic, cruft and usb startup disk. However, openoffice is still the same. I'm sure I can live with it though, and thanks a lot Ivo :D

---

### Post by Ivo Moelans on 2009-01-07
Glad it worked for you.
I thought Open Office was going to be a problem. It uses its own icon set and its own engine for font rendering (with mixed results, to say the very least). It  also seems to only partially adhere to gtk (see the discussion at the bottom of this article: [http://www.linuxjournal.com/article/6437]("http://www.linuxjournal.com/article/6437")).
What I do find strange is that in my 2.4 version it themes the combo boxes and the scrollbars, which it doesn't seem to be doing in your 3.0 version. I don't think this will be resolved quickly as Open Office is a very complicated program and it would take an extensive rewrite.

---

### Post by propagation_of_sound on 2009-01-07
Great, worked perfectly :D Thanks a lot Ivo Moelans. :D

---

### Post by Ivo Moelans on 2009-01-07
You're very welcome.
Please mark this thread as "solved".

---

