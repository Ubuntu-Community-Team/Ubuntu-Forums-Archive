---
title: "Seeking for the best PDF reader for a newly installed XUBUNTU 32-bit on an old laptop"
date: 2017-05-19
forum: Desktop Environments
---

### Post by p-melas on 2017-05-19
Good day to the community

I have an old laptop, an [**Acer Aspire 1524WLMi**]("https://www.cnet.com/products/acer-aspire-1524wlmi-15-4-mobile-athlon-64-3400-plus-win-xp-home-512-mb-ram-60-gb-hdd-series/"), which has been recently upgraded from Windows XP Home to Xubuntu 32-bit.

I am looking for a good PDF reader (and editor/writer, if it is freely available), other than the one existing in the system (the "Document Viewer"). I knew that Adobe had a version for Linux of its Acrobat Reader in the past, but I' ve learned that this is no longer supported.

Is there anything out there, that will do the job?

Thanks in advance

---

### Post by orange2k on 2017-05-19
I think that the "Document Viewer" is actually **Evince**, which is a quite nice PDF reader, other alternative would be KDE's **Okular**. With these solutions, you don't get an automatic PDF editor, but you can export to PDF from many programs in all Ubuntu versions, including Xubuntu: thus you can export from **Libreoffice**, **Inkscape**, and even directly from plain text editors. 
To demonstrate that, you can install Vim or Vi (if it is not already on the system), by opening some text in Vi(m) and then running the following command inside it ```
**:1,$!groff -Tps | ps2pdf - vi-output.PDF**
```
It is even possible to prepare and format the text inside Vi(m) (with some Unix/Linux knowledge) before this command, thus you get an almost complete desktop publishing tool, even without the need for a graphical interface - using only the terminal.
Of course, you can use advanced editing tools for that purpose on Ubuntu, like **Scribus**, but I just wanted to point out the power of classic Unix tools.

---

### Post by ajgreeny on 2017-05-19
Many users who need editing facility for PDFs use xournal which is in the repos.  You open the PDF with that and then make changes as needed and finally export back to a new PDF.  It works very well for relatively minor edits, and no doubt if you work with it a lot, you could do almost anything.

If you're OK with commercial applications, though free to use with some limitations, a lot of users sing the praises of [Master-PDF-Editor]("https://code-industry.net/get-masterpdfeditor/"), though I have no need for it and therefore no experience of using it.

---

### Post by p-melas on 2017-05-19
> **orange2k said:**
> I think that the "Document Viewer" is actually **Evince**, which is a quite nice PDF reader, other alternative would be KDE's **Okular**. With these solutions, you don't get an automatic PDF editor, but you can export to PDF from many programs in all Ubuntu versions, including Xubuntu: thus you can export from **Libreoffice**, **Inkscape**, and even directly from plain text editors. 
To demonstrate that, you can install Vim or Vi (if it is not already on the system), by opening some text in Vi(m) and then running the following command inside it ```
**:1,$!groff -Tps | ps2pdf - vi-output.PDF**
```
It is even possible to prepare and format the text inside Vi(m) (with some Unix/Linux knowledge) before this command, thus you get an almost complete desktop publishing tool, even without the need for a graphical interface - using only the terminal.
Of course, you can use advanced editing tools for that purpose on Ubuntu, like **Scribus**, but I just wanted to point out the power of classic Unix tools.

Thank you so much for your immediate and complete reply, mate.

Since I am a newbie in the Linux environment, with very little knowledge from Mint and a slightly better knowledge of VI text editor from the first UNIX OS, which I was using back in the nineties and the early years of the new millennium, when I was working in a shipping company as a technical sup't, your mentioning of VI reminded me those days, when we were all using VI as our sole text editor with its dot commands, which we were supposed to know by heart.

I am not sure if I can use VI in a modern Xubuntu environment. In fact, I really don't know at all if the system offers this ability. I would be grateful if you or someone else can give me a simple guide how to go to that environment and install VI to use it (if it is not already installed).

Thanks again

---

### Post by p-melas on 2017-05-19
> **ajgreeny said:**
> Many users who need editing facility for PDFs use xournal which is in the repos.  You open the PDF with that and then make changes as needed and finally export back to a new PDF.  It works very well for relatively minor edits, and no doubt if you work with it a lot, you could do almost anything.

If you're OK with commercial applications, though free to use with some limitations, a lot of users sing the praises of [Master-PDF-Editor]("https://code-industry.net/get-masterpdfeditor/"), though I have no need for it and therefore no experience of using it.

Thank you too, mate for your advice. I will take it seriously into consideration.

---

### Post by orange2k on 2017-05-19
> **p-melas said:**
> I am not sure if I can use VI in a modern Xubuntu environment. In fact, I really don't know at all if the system offers this ability. I would be grateful if you or someone else can give me a simple guide how to go to that environment and install VI to use it (if it is not already installed).

Oh, yes you can! I think all Ubuntu flavors come by default with Vi(m) preinstalled (not sure about GVim - which is the GUI version of Vim, but with almost the same functionality), and if you're a Vi user, and already know some of it, then already you're a power Linux/UNIX user! Go ahead and test, try to run **vi** or **vim** from the terminal and see if its there, if not simply install it by **sudo apt install vim** in the terminal, and off you go (Vim stands for Vi IMproved - look for more info [here]("http://www.vim.org/")). GNU/Linux is based on Unix tradition and while its not Unix (GNU=Gnu is Not Unix), its almost identical, with all the Unix goodies (but not 100% compatible, worth mentioning), so you'll feel right at home.
With the modern Linux system comes also the bliss/curse of the desktop environment and because being spoiled by it (in the way they are spoiled by using Windows mostly), many people forget the long lasting CLI heritage, which is very powerfull, so novice users often neglect it.  
Vi(m) comes with the old keybindings which you are probably used to, if not, run the **vimtutor** from the terminal to remind yourself of the fundamental usage and functionality.
Vi(m) is an integral part and corner stone in every Linux pro user's arsenal (some people might argue with this statement) and one of the top text editors out there, regardless of the platform, and by now it has tons of available enhancements for every editing/programming task that you might imagine...So, by being forced to learn it by heart back in the 90-ties, you actually were given a favor! ;)

---

