---
title: "Persian Locale, persian (farsi) input"
date: 2009-01-25
forum: Desktop Environments
---

### Post by ellipsic on 2009-01-25
Hi all.  I have installed the persian locale on Ubuntu 8.10 (x86 64) on a Thinkpad X61. I want to be able to type in farsi in OpenOffice.  When I am in the persian locale, almost everything on my desktop is written in farsi; when I open an OpenOffice document, I see 'farsi' written at the bottom.  The text direction at this point is right to left; the cursor is on the right hand side of the screen. As soon as I begin to type, it's english text (written as if right justified), and 'farsi' changes to 'English - US' on the bottom.  What is going on?  Can someone please help me with this.  In an ideal world I would like something like scim input, that I could change anywhere at anytime.  

Thank you

---

### Post by adamitj on 2009-01-25
Hi ellipsic!

Did you tried to change the default language for OpenOffice at menu: Tools / Language Settings / Language ?

I had the same problem with PT_BR language, and after changing these settings all worked fine - altought I needed to install some extra packages from Synaptic for correct spelling checker.

---

### Post by ellipsic on 2009-01-25
yes, I did do that, and still nothing =(

---

### Post by adamitj on 2009-01-25
It must be some odd, but have you installed your right-to-left fonts as well?

> sudo apt-get install ttf-farsiweb ttf-freefarsi

---

### Post by ellipsic on 2009-01-27
Yeah, I had both of those installed (checked synaptic to be sure, and I have them both). Here's something funny, have a look at the attached pictures. 

In the first, I was able to type farsi into a small test box (which I wasn't able to do again later???), and paste it into open office. When I put the cursor in the middle of a word and began typing, it changed to english, and the letters even changed shape. Openoffice recognized taht it was farsi, but wouldn't input.  Any ideas?

---

### Post by adamitj on 2009-01-27
Hummm... as I see, you are using the english version of Ubuntu, and installed support for farsi input. Well, let me show you my own experience: I use an english version either, and did some changes to support Brazillian Portuguese spellchecking (it is better to me since I am a IT/IS architect/developer) and some letters (like "ç"). I did not need to change too much, since english and brazillian uses default latin characters.

BUT... to make accentuation and cedilla work perfectly, I had to change my default keyboard layout. My notebook is a HP DV6636NR with US keyboard and at Ubuntu installation I set it to "US", but the things started to work only when I changed to "US International - us_intl".


So, let's try to isolate the problem cause:

It is pretty sure that OpenOffice cannot recognize your inputs as Farsi, so the question is: in any other Ubuntu application (like Gnome text editor) you are able to type in Farsi mode?

If you can't, there is enough arguments to believe that your problem is at keyboard input. In this case, we need to find if there is a keyboard layout which can "split" Farsi into a US layout.

Unfortunately I can't do it right now, but I will try to install farsi elements in my computer and give you a feedback ASAP.

---

### Post by ellipsic on 2009-01-28
I tried Gedit, and even after going to Tools > Set language > Persian , I could only type in English.

---

