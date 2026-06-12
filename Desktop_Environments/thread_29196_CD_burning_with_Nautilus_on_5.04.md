---
title: "CD burning with Nautilus on 5.04"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Johank on 2005-04-23
Hey all, newby question again

I have mounted my windows NTFS drive and, using Nautilus, copied files from the NTFS drive to burn:///. 
Next I clicked on 'Write contents to CD' and....well....keeps on asking for a blank CD or CD with enough space. 
I never see it actually accessing the CD. 
Also, if I click in the CD icon on the desktop, it simply brings up burn:///   ... what am I doing wrong? I followed the steps in the help to no avail..

---

### Post by tread on 2005-04-23
Try dragging the folders you want to burn in the burn:// window. Or install gnomebaker through synaptic. (look at the ubuntu unofficial guide for new repositories to add)

In fact look at the unofficial guide anyway, it might answer a lot of questions.
Its available at ubuntuguide.org


Also, important point:
If your cd burning process (once you get it started) quits halfway .. like mine did, you need to do this:

Go to Applications->System Tools->Configuration Editor

click apps, scroll down to nautilus-cd-burner and check the burnproof box.
(if you have a similar problem with gnomebaker, do the same there)

---

### Post by Johank on 2005-04-23
Thanks - I'll try.

---

### Post by guyforget on 2005-04-23
Are you sure theres enough space on your media for what you want to burn?  I get that error sometimes, but only when Im over the capacity on the DVD Im trying to burn to...

---

### Post by doc_holiday on 2005-06-06
I'm using gnomebaker, but when I drag folders in to in it just burns the files in the rootfolder of the dvd.

---

### Post by jobezone on 2005-06-06
[QUOTE=doc_holiday]I'm using gnomebaker, but when I drag folders in to in it just burns the files in the rootfolder of the dvd.[/QUOTE]
 Also try Coaster . It's in Universe, I think.

---

### Post by Roberto75 on 2005-06-16
+++QUOTE
Also, important point:
If your cd burning process (once you get it started) quits halfway .. like mine did, you need to do this:

Go to Applications->System Tools->Configuration Editor

click apps, scroll down to nautilus-cd-burner and check the burnproof box.
(if you have a similar problem with gnomebaker, do the same there)[/QUOTE]
++++QUOTE

I had problem writing to my scsi burner: nautilus kept on asking for a blank cd. followed the above instructions and also marked for overburn just in case. Nautilus stopped asking about a blank Cd and burned right away.

hope this can help others.

---

