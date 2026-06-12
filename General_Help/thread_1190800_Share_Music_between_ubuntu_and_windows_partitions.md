---
title: "Share Music between ubuntu and windows partitions"
date: 2009-06-18
forum: General Help
---

### Post by LeChacal on 2009-06-18
OK so I have ripped all of music on to my ubuntu partition but I still have to duel boot windows for school. I don't want to keep a copy of all my music on both partition because my window partition is full of all my school work (I am a BioME so I have to use SolidWorks, Matlab, Maple, LabView, Working Model, NX3/5 not small output files all the time nor small installs) so I was looking for a way that I could share my music with my windows partition so I could listen to it while I was doing school work under windows.

Some notes: I am going to do a clean install of my whole machine (ubuntu and windows) in a couple of days when I get home so I am open to anything. Wine isn't an options not all that software will run fully under it. Vbox also isn't an options because I run Vista 64bit so I can use all 6GB of RAM on my machine and I have had to make my page file bigger so I could run both SolidWorks and NX3/5 at the same time, a very hardware intensive thing not suitable for a vmachine. Thank you for you help.

---

### Post by TeoBigusGeekus on 2009-06-18
Create a separate partition for storage in which you can put all your music, movies, pdfs, etc. and format it as ntfs. 
In this way it will be accessible from both Ubuntu and Vista.

---

### Post by LeChacal on 2009-06-18
I was kind of looking/thinking about that only I was going to just make it a /home partition, can I make a /home partition and have it with a NTFS file system? And if I did that I would just make "Documents and Settings" also point to these/this folders/partition under window and just have one "My Documents" for both OSs. How does that sound?

---

### Post by TeoBigusGeekus on 2009-06-18
I wouldn't do it because I wouldn't want vista to be able to access any part of Ubuntu. 
It would be susceptible to corruption and viri...

---

### Post by ajgreeny on 2009-06-18
No you can't have a /home partition on an ntfs filesystem as the permissions will not be correctly retained for your ubuntu home.  You need your /home for all the hidden config files and folders on ext3, and a data partition, which you mount at boot time with a line in fstab, for all your documents, letters, music, videos etc etc on ntfs.

---

### Post by Cheesemill on 2009-06-18
I would set up a separate NTFS partition for all your shared data.

You can then set up symlinks in your home folder pointing to directories on the NTFS partition. This way when you click on Music (for example) in your home folder it would open the Music folder on your shared partition.

On Vista you can also change the default location of the My Music folder to point to this as well.

---

### Post by LeChacal on 2009-06-18
Ok so it looks like a separate NTFS partition with Symbolic links to things in linux and change default folder locations in windows is what I am going to do. Thank you all. And if anyone has further suggestions they are more then welcome.

---

