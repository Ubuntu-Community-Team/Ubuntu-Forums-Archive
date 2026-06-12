---
title: "Nautilus crashes when clicking file Properties"
date: 2009-06-18
forum: General Help
---

### Post by inspired on 2009-06-18
I've been having this issue for some time now. It started when I upgrade to 9.04 from 8.10
I get a hunch that something I added to Nautilus for tagging files on 8.10 is incompatible on 9.04. Thing is, I have no idea what I added or how... it was a long time ago now.

When I bring up the context menu on ANY file and click PROPERTIES Nautilus crashes (all icons on desktop also vanish).

I'd greatly appreciate some help on how to resolve this. I use the Properties a lot.

Thanks,
Jonathan

---

### Post by prem1er on 2009-06-18
Run Nautilus from the terminal and follow the same steps you do to make it crash.  If it crashes again the terminal will output the error messages. Post them back here.

---

### Post by inspired on 2009-06-18
> **prem1er said:**
> Run Nautilus from the terminal and follow the same steps you do to make it crash.  If it crashes again the terminal will output the error messages. Post them back here.

Thanks. I have since solved this.
I googled keywords for all the various changes I may have made to Nautilus back on 8.10
Finally figured out it was a python script I had added for editing tags on files, which are then searchable on Tracker.
Since I had to disable tracker completely after upgrading to 9.04 (due to a widely experienced bug where Tracker bombs out with a DB corruption error every time it runs), I won't be needing the tagging for now anyway.
If and when the tracker issue is fixed (it may be already, haven't checked in a while) it would be nice to be able to add and edits tags on the properties pane... so if anyway has any suggestion on how to implement that on 9.04 I'd love to know.

Regards,
Jonathan

---

### Post by Dahaniel on 2009-06-24
Hey, I am having the same problem and remembered that I also installed the tracke python script.

So I tried to remove the 2.py files from ~/.nautilus/python-extensions/ and restarted my system but nautilus still keeps crashing...
Is ther something else I have to do in order to delete the script? Some config file I missed maybe?

---

### Post by Dahaniel on 2009-06-24
Aaaah, helped myself,
I had the two scripts also in "/usr/lib/nautilus/extensions-2.0/python", after deleting them everything is fine again.
Thank you for this thread I was near to setting up the system from zero!!!!

---

