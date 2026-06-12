---
title: "Firefox 4 on ubuntu?"
date: 2010-07-21
forum: Desktop Environments
---

### Post by miniclip22 on 2010-07-21
Hi all. I don't know if this is the correct spot to post his, but here it goes: I want to install Firefox 4, but when I download it it appears as a file tar.bz2... No executable file... I am a newbie to linux, so can someone create a firefox 4 package for me? Thanks!

---

### Post by Kellen0070 on 2010-07-22
In Terminal
Unpack the package using:
mv firefox-4.0b1.tar.bz2 ~
tar -xjvf firefox-4.0b1.tar.bz2

then run the executable:

~/firefox/./firefox

That should work.  I do not currently have linux installed on my computer but I have done this before with other versions of firefox.

---

### Post by lovinglinux on 2010-07-22
See Method #1 at the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

You can also use my extension [FoxTester]("http://foxtester-extension.blogspot.com"), which make easy to install, test and uninstall multiple versions of Firefox.

---

### Post by mahmudinashar on 2010-07-22
wow, evetualy firefox 4 come to ubuntu, sip .

---

### Post by lovinglinux on 2010-07-22
> **mahmudinashar said:**
> wow, evetualy firefox 4 come to ubuntu, sip .

Only in the next version of Ubuntu.

---

### Post by miniclip22 on 2010-07-22
I have unpacked, but cannot run the executable, "No Such File or Directory". Any ideas?

---

### Post by lovinglinux on 2010-07-22
> **miniclip22 said:**
> I have unpacked, but cannot run the executable, "No Such File or Directory". Any ideas?

If your original tar.bz2 has **source** in the name, then you have the wrong file (those are for compiling). If not, then browse the extracted folder and double-click the firefox file inside it.

BTW, are you planning to use it as your main browser? Is too soon for that. Most extensions won't work yet.

---

### Post by miniclip22 on 2010-07-24
> **lovinglinux said:**
> If your original tar.bz2 has **source** in the name, then you have the wrong file (those are for compiling). If not, then browse the extracted folder and double-click the firefox file inside it.

BTW, are you planning to use it as your main browser? Is too soon for that. Most extensions won't work yet.

Finally got it to install. Yes, I'm planning to use firefox as my main browser. I have the 4th version on Windows seven, but my question is: why isn't firefox's visual style equal to windows? It seems like firefox 3 and not that good looking firefox 4 on windows... Any ideas?

---

### Post by lovinglinux on 2010-07-24
> **miniclip22 said:**
> Finally got it to install. Yes, I'm planning to use firefox as my main browser. I have the 4th version on Windows seven, but my question is: why isn't firefox's visual style equal to windows? It seems like firefox 3 and not that good looking firefox 4 on windows... Any ideas?

Mozilla only included the new UI on the Windows version for now. I guess this is because of the new menu, that is inserted in the window border. I don't know how hard would be to implement that on Linux, specially considering there are several window managers. Nevertheless, it seems they will provide the new UI before Firefox 4 is officially released.

---

### Post by miniclip22 on 2010-07-25
> **lovinglinux said:**
> Mozilla only included the new UI on the Windows version for now. I guess this is because of the new menu, that is inserted in the window border. I don't know how hard would be to implement that on Linux, specially considering there are several window managers. Nevertheless, it seems they will provide the new UI before Firefox 4 is officially released.

OK, that's good news! Hope to see firefox as beautiful as it can be, letting Chrome with no power to fight back :D

---

### Post by lovinglinux on 2010-07-25
> **miniclip22 said:**
> OK, that's good news! Hope to see firefox as beautiful as it can be, letting Chrome with no power to fight back :D

hHehehe, I like that. Firefox 4 is really fast too.

---

