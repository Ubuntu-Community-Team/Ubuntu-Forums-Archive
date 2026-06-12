---
title: "RAR archives not extracting"
date: 2008-12-06
forum: General Help
---

### Post by shinkaide on 2008-12-06
Hi all...

I'm having trouble extracting RAR archives using File Roller (not extracting at all!). 

This seems to have started after I added the medibuntu repository to enable DVD/VCD playback (not saying it's what caused it, I don't really know). Now I can't extract the files at all. It used to work all right before I did the medibuntu thing.

Help, please?

---

### Post by binbash on 2008-12-06
suda apt-get install unrar (also you may need to add unrar-free and rar)

you can extract the files via file-roller or command line : 

unrar e asdasd.rar

---

### Post by shinkaide on 2008-12-06
the unrar package is already installed. Still can't extract archived files via File Roller

---

### Post by RuleMaker on 2008-12-06
```
sudo apt-get install rar
```
And right click on rar file and Extract Here.

---

### Post by shinkaide on 2008-12-06
> **RuleMaker said:**
> ```
sudo apt-get install rar
```
And right click on rar file and Extract Here.

Oh, thanks a lot, that worked! 

I'm just really curious though, can anyone tell me how to fix the problem with file roller? Because previously, I've able to just 2xClick on an archive, and drag the contents from the File Roller window into a folder of my choosing, and it will extract the archive so. Now it won't.

I'd love to know how to fix that problem, if anyone can help me. That would be much appreciated! :)

---

### Post by Acradon on 2009-02-04
I love Ubuntu forums. Thanks for this thread. It solved a conundrum I had for a while.

---

### Post by mb_webguy on 2009-02-05
7-zip works well for me both on its own and as a plugin for File Roller.  Type "sudo apt-get install p7zip-full p7zip-rar" in the terminal to install with rar support.

---

### Post by AGS on 2009-02-10
OK, I just had the same problem after re-installing 8.10. I searched Synaptic for everything RAR, but there was nothing. Why is it installable via apt-get but not per Synaptic??? Don't they use the same sources?

---

### Post by mb_webguy on 2009-02-10
I don't know what's causing it, but I've noticed a lot of people (including myself) having problems with the apt index.  The packages are available if you know what you're looking for, but searching for them is impossible.  Fortunately there's a simple fix: "sudo update-apt-xapian-index"

---

