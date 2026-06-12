---
title: "[SOLVED] Fonts"
date: 2008-12-03
forum: General Help
---

### Post by Grolsche on 2008-12-03
Hi,

I have just installed photoshop using wine.

Now when I use photoshop it displays a message about not being able to read the fonts.

How do I install the fonts I need so photoshop can recognise them?

---

### Post by ashmew2 on 2008-12-03
I think you need Tahoma : 

> Search on Google for the Tahoma font with the following string:

tahoma filetype:ttf

Save it on your desktop, then move it to the Wine fonts folder (full path -> /home/yourusername/.wine/drive_c/windows/fonts).



I found this here : [Softpedia]("=http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml")

---

### Post by kerry_s on 2008-12-03
> **Grolsche said:**
> Hi,

I have just installed photoshop using wine.

Now when I use photoshop it displays a message about not being able to read the fonts.

How do I install the fonts I need so photoshop can recognise them?

install the microsoft fonts.
**sudo apt-get install msttcorefonts**

---

### Post by Grolsche on 2008-12-04
Thanks Kerry. That trick works a treat and so far works with every other program whetehr it uses wine or not.

---

