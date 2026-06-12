---
title: "Help with Quicklists?"
date: 2011-06-04
forum: Desktop Environments
---

### Post by Phaze08 on 2011-06-04
Ok, so I'm trying to do this:
[http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html)

The problem is, when I get to the part where I have to open the file in gedit, it says it can't open it, file not found, or something or other..So, when I manually browse to the directory '.local/share/..' there is no folder named 'applications,' only a text file. When I open it, it appears to be the home launcher file, but its in the wrong place and has the wrong name. What's going on? Shouldn't there be a folder there with my applications in it? Anyone know anything?

---

### Post by Frogs Hair on 2011-06-04
Run the first command terminal . Copy , paste and enter the second line in the terminal and the file will open in Gedit automatically . Continue with the rest of the instructions .

They way the instruction is worded , it reads as though you're to search for a file , when in fact you are opening the file with the second command.

---

### Post by Phaze08 on 2011-06-04
Actually, I tried that, it opens gedit, but it says the file/directory cannot be found, which is what prompted me to search for the file manually.

---

### Post by Frogs Hair on 2011-06-04
I don't know what's happening then , I just added the software center quick list using the same instructions.

---

### Post by Phaze08 on 2011-06-04
Yeah its pretty weird...I did it a while back with success but then I accidentally deleted my ubuntu partition instead of my windows partition. X] Ever since then its been doing this. Maybe if I could find the file that backed up and move it back to the right directory? I looked and I can't find it in my home directory.

---

### Post by Frogs Hair on 2011-06-04
I found Nautilus-Home.desktop  in the file system and the the quick list is actually in .local /share / applications in my hidden / home folder. This doesn't look like the file I opened when creating the quick list.

---

### Post by Phaze08 on 2011-06-05
My probem is, THERE IS NO /applications folder in /.local/share lol. Also, when I search in my file system, it doesn't find the file....nor is there is a hidden .home directory in file system or home folder. I wasnt sure which one it was in so I checked both....to no avail.

---

