---
title: "Open Office version in repo unstable?"
date: 2006-04-06
forum: Desktop Environments
---

### Post by stig on 2006-04-06
Hi!
I have had a problem with Open Office and posted it in the OO forum. They asked what version I used. I am using the latest I can find in the Ubuntu repository - 1.9.129.

But the response in the OO forum was "1.9.129 is a development version, very old and unstable. Try the last stable version 2.0.2".

Is this true? If so, why does the repo have an unstable version when there is apparently a later version which is more stable?

Thanks!

---

### Post by manicka on 2006-04-06
[http://doc.gwos.org/index.php/Install_Ooo2](http://doc.gwos.org/index.php/Install_Ooo2)

---

### Post by Sef on 2006-04-06
> Is this true? If so, why does the repo have an unstable version when there is apparently a later version which is more stable?


The repositories are updated only every six months with the release of the next upgrade.

---

### Post by stig on 2006-04-06
Thanks manicka and Sef - I didn't even know about the UDSF so I've learnt a lot from this already! I will try the "Installation from repositories" option.

I currently have the old 1.4x version which I had been working on and had added the 1.9.129 alongside. I customised the toolbar with a number of buttons for macros etc in the old version. Is there a file I can save and use again in v.2 so that I keep my customising?

---

### Post by stig on 2006-04-07
[QUOTE=Sef]The repositories are updated only every six months with the release of the next upgrade.[/QUOTE]

If I follow manicka's UDSF page and change my source file to include the OpenOffice v.2 line, what happens at the end of the 6 months if the repo then includes this version?

Would there be any problem with already having it in the source file? Would I need to delete it from the source file? Sorry to appear dumb about this but I'm not very familiar with the way Linx and Ubuntu work!

Thanks for the help!

---

### Post by Sef on 2006-04-07
> Would there be any problem with already having it in the source file?

1) You installed Dapper from a disk, then there shouldn't be any problem because you delete the root, swap, and fat32 partitions, if added.  The home partition is left alone.  Then you would reinstall the partitions deleted.  Then there is no problem.

2) If you do an upgrade via net, I am not sure if there will be a conflict or not.

> Sorry to appear dumb about this but I'm not very familiar with the way Linx and Ubuntu work!

Since you asked a question, you aren't dumb, just learning.

---

