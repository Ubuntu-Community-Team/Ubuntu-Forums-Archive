---
title: "Erased etc directory !!"
date: 2005-10-03
forum: Desktop Environments
---

### Post by jose3 on 2005-10-03
Hi guys, this is my first post and first of all I have to say I am very happy with Ubuntu cause it was my first step into linux world and I am really satisfied with the results I am having with it.

But.....the romance allways finishes. 

I had configured Nautilus to run on sudo as root and I had made a shortcut poiting "/". I accidentally erased etc directory.

Wich would be the best practice in this case? do i have to reinstall?
 
My guess would be to boot from knoppix FE and move the erased folder to its original place but I cannot boot dunno why...kernel panic!!! stuff.

Well its good to be here.
Thanks in advance.

jose

---

### Post by KingBahamut on 2005-10-03
Sadly, your looking at a reinstall.

---

### Post by logicaloperator on 2005-10-04
[FONT="Century Gothic"]:(  If u r a  just getting going, than just reload - there's nothing like learning from your mistakes[/FONT]

---

### Post by jose3 on 2005-10-05
Thanks for the answer guys, sure there is no better practice than learning from your own mistakes but....

Booted from ubuntu cd, I selected to see al the steps available and went to command usage, mounted the hda1 that had the erased etc directory, went to /root/.Trash/ and copied the directory to its original place. It worked enought for me to backup all the .confs and files.

Of chourse I solved after spending plenty of time investigating how to. Now I am facing a better scenario to recover my dear Ubuntu.

Thasnk indeed.

---

### Post by shakin on 2005-10-05
Once you placed /etc back it should be fine. No need to reinstall AFAIK. Good thing that .Trash directory is there :)

---

