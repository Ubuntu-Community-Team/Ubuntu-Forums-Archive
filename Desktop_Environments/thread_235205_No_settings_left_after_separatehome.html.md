---
title: "No settings left after separatehome.html"
date: 2006-08-12
forum: Desktop Environments
---

### Post by petri on 2006-08-12
I did this: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) on my other computer (whithout reinstalling ubuntu, yet)

Well it worked, almost. I was able to boot up computer again but... my desktop background was gone, my bookmarks are gone and Swiftfox, my mail and settings are gone (Evolution), icons and catalogues has changed places on desktop. Some of the catalogues are empty ](*,) 

I thought that these things would be left even if I reinstall ubuntu? Or was it because i placed /home to a different hd? I haven't tried the rescue part in the guide yet because I would prefer have /home on separate partition from the root.

---

### Post by aysiu on 2006-08-12
If you mount your partition with a live CD, you should see a folder called *home_backup*. See if your files are still in there.

Then mount your newly created /home partition and see if it has the same contents.

---

### Post by petri on 2006-08-13
Yes they have same contents and the size is same too.

I meant some of the catalogues on the desktop are empty which they weren't before the new location to /home.

What next? I really want a separate home partition because I'm planning reinstalling ubuntu and hopefully whithout reconfiguring everything.

---

### Post by aysiu on 2006-08-13
I'm not sure what the problem is, actually. If all the contents are the same, presumably everything should be as it was before...

---

### Post by petri on 2006-08-13
Is it so that if I reinstall Ubuntu my  settings on Evolution Swiftfox etc. should be as before the reinstalling (that is if I didn't had this problem)?

---

### Post by aysiu on 2006-08-13
Well, if they're not working now, then I don't think they will be if you reinstall. You said some things on the desktop are missing. Have you tried Evolution and Swiftfox?

---

### Post by petri on 2006-08-13
Swiftfox has vanished, Evolution is empty meaning I have to create a count again. 

No, this time it ain't going to work I'm just wondering if I have understood it right.

Do you know what happens if I run the recovery part of separatehome.html? Or do you have a guess :)

---

### Post by aysiu on 2006-08-13
The recovery part marks your old /home folder your /home folder again. Theoretically, everything should work in that tutorial. I tried the first part myself, and it worked.

But if the first part didn't work for you, I'm not sure if the recovery will...

---

### Post by petri on 2006-08-13
Ok thanks aysiu, I'll try recovery first.

---

### Post by petri on 2006-08-14
Well, the files and all e-mail were left after the reinstallation of Ubuntu and reappeared like it was after the failure. I did have to reinstall some programs like Tomboy notes, ontv, tv's etc and of course the all the e-mail accounts which all were gone after the moving of /home to it's own partition. 

Swiftfox was gone probably because of a wrongfully installated by the accused from the beginning :rolleyes: And I think that might be the main reason to the failure.

Maybe there should be an partition for /opt too, I think. To keep programs like Swiftfox, Adobe reader etc.

---

### Post by aysiu on 2006-08-14
Programs are not stored in your /home folder or partition.

Only your user *settings* for those programs are stored in the /home folder. So if you reinstall, yes, Swiftfox and other programs will be gone.

---

