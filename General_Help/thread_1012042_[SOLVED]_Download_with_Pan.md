---
title: "[SOLVED] Download with Pan"
date: 2008-12-15
forum: General Help
---

### Post by DeMus on 2008-12-15
Hi,

When I download from a news server I first download a nzb file with the table of contents of everything I want to download. This nzb file is connected to Pan so the download window of Pan will be started. First I have to tell Pan where to save the downloaded files.
Is there a way to tell Pan the default folder where to save the files? Now I have to change to my default folder every time.

Thanks,
DeMus

---

### Post by DeMus on 2008-12-29
Does nobody use Pan to download from Usenet? Hard to believe.
Come on, please help.
Thanks

---

### Post by editrix on 2008-12-29
Sorry this won't be much help, but my Pan just went nuts on me and started to save an article I wanted to read--without telling me where it's saving it to.

Now I can't find it, and see no way of configuring Pan to do anything. I used to use Knode which is much better, except once you've downloaded an article, it doesn't get written to the hard drive.

You might take a look at your /home/username/.pan2 directory. I've got a preferences.xml file in there, but it's empty.

---

### Post by DeMus on 2008-12-31
> **editrix said:**
> Sorry this won't be much help, but my Pan just went nuts on me and started to save an article I wanted to read--without telling me where it's saving it to.

Now I can't find it, and see no way of configuring Pan to do anything. I used to use Knode which is much better, except once you've downloaded an article, it doesn't get written to the hard drive.

You might take a look at your /home/username/.pan2 directory. I've got a preferences.xml file in there, but it's empty.


Write this in the preferences.xml file:
<string name='default-save-attachments-path' value='/home/jan/Pan/'/>
Of course with your own folder name. It works for me.
There are many more items which can be changed, but most of them are about how you set your screen, the different windows in the program, etc.

Good luck and thank for the tip about the xml file.

---

