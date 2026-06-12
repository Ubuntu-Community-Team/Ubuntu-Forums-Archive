---
title: "PDF garbled, missing fonts?"
date: 2005-10-30
forum: Desktop Environments
---

### Post by helwitch on 2005-10-30
I'm trying to view a pdf (this one in particular- [http://www.udc.edu/docs/downloads/udc_class_schdl.pdf](http://www.udc.edu/docs/downloads/udc_class_schdl.pdf) ) and I can't, most of the text is horribly garbled. I'm guessing this is a missing font problem, as the exact same file displays just fine on windows. And I know it's not a corrupt download, because the file was saved to my USB disc, so it really was the exact same file being looked at on both windows and kubuntu.
So, how do I find out WHICH fonts this PDF wants that I lack, and install them? Thanks.

---

### Post by Staesys on 2005-10-30
I get the same garbling in kpdf. Not all of it's garbled, but mostly the stuff in black boxes. However, I viewed the same file in Adobe Acrobat Reader 7 and it rendered perfectly.

From looking around the forum, I've noticed othe people having similar issues with kpdf. I hear xpdf works, as well as evince. Although I can't personally reccomend these as I've not used them.

I think it's time someone filed a bug report on this issue.

---

### Post by shinygerbil on 2005-10-30
Works better in Xpdf... it's all readable but the text looks like it's not on a straight line. Very odd...

Steve

---

### Post by helwitch on 2005-10-30
Ok, so I know what progs to use to read it. Which is helpful, thanks!
I am still curious tho, as to how I would go about finding out what font it wants that is missing, and installing that font. Or am I wrong about the problem being a missing font?

---

### Post by foxy123 on 2005-12-05
I've got the same problem with KPDF. The file looks horrible there  and fine in evince. The trouble is that I like kpdf more than evince, especially its search function. Any way to fix it?

---

### Post by NerftheSmurf on 2005-12-17
I'm having this problem too. I found this: [https://bugs.kde.org/show_bug.cgi?id=110117](https://bugs.kde.org/show_bug.cgi?id=110117) bug report which suggests that it's something screwy in the font packaging. 

Any solutions for this?

---

### Post by mlmurray on 2005-12-17
It looks like viewers based on xpdf have trouble with some pdf files.  However, Adobes own **Acrobat Viewer** works as does any viewer based on **Ghostview** such as **kghostview,** or **gv,** to name a few.

---

### Post by NerftheSmurf on 2005-12-17
Actually I've found that the pdf's that show up garbled in kpdf work fine in xpdf.

---

### Post by Pekkalainen on 2005-12-18
Distro bug, time to beat up the guy who packaged it ;)

---

### Post by MichaëlVD on 2006-01-07
Are there any plans for an update for this?

---

### Post by angrykeyboarder on 2006-01-08
[QUOTE=MichaëlVD]Are there any plans for an update for this?[/QUOTE]

I'd guess - quite possibly.  I'm running Dapper at the moment and had no problem viewing that PDF file in Konqueror (via KPDF).

---

