---
title: "read MS PowerPoint math equations"
date: 2009-08-18
forum: Education &amp; Science
---

### Post by nikosm on 2009-08-18
Hello,

I am trying to open [[COLOR="Blue"]this ppt file[/COLOR]]("http://www.cs.tau.ac.il/%7Ezwick/slides/sparse.ppt") with OpenOffice but many math symbols do not render correctly (e.g. second slide):

[ATTACH]125337[/ATTACH]

Is there a way to fix this?

I have tried: 
[LIST]
[*]installing powerpoint viewer and running under wine
[*]installing msttcorefonts + updating font cache
[*]uploading and opening as a google document
[/LIST]

none of which worked. Any ideas?

Thanks,
Nikos

---

### Post by Chronon on 2009-08-18
It looks like a font issue.  I have experienced similar problems even with different installations in Windows and transferring files from Windows to Mac (all using MS Office products).  The only reliable way to produce a portable document that I have found is to convert such expressions into images and embed the images.  I haven't done too many presentations with Open Office, but I would expect similar problems if the host machine lacks the fonts that were used in creating the presentation.

---

### Post by nikosm on 2009-08-18
> **Chronon said:**
> It looks like a font issue.  I have experienced similar problems even with different installations in Windows and transferring files from Windows to Mac (all using MS Office products).

Chronon, thanks for the reply. Any ideas what fonts that would be? Are there other common microsoft fonts besides the (already installed) msttcorefonts?

Thanks for any suggestions,
Nikos

---

### Post by Chronon on 2009-08-18
I don't have any idea about that, sorry.  I have seen many cases of people preparing a PowerPoint presentation on their PC then trying to give a talk only to find that the PC they are trying to use doesn't have the right fonts and you wind up with all of these bizarre substitutions that render all of the meaningful math expressions not very meaningful.  This is all with MS Office running on Windows but (apparently) different fonts installed on the two systems.  I am not at all surprised that you have encountered this when trying to open PowerPoint presentation on a Linux system in Open Office.  

My best advice is to contact the creator of the file and have them tell you what font is used or have them export it in a portable way (I believe it's possible to export slide images, for instance).  Otherwise you will just need to remove the offending text in your copy and fix the expressions on your end.

---

