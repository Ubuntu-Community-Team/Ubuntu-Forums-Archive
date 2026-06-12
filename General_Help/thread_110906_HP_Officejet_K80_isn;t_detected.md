---
title: "HP Officejet K80 isn;t detected"
date: 2006-01-01
forum: General Help
---

### Post by jdcaserockies on 2006-01-01
It's connected via USB, and it won't be detected at all. I was told I need to run hplip and hpijs, but i don't know how or what they are. Please help!

**EDIT**

Ok, well I was able to get it to install, but it won't print anything at all. cupsd is running, and hplip is running, what am i doing wrong?

---

### Post by audax321 on 2006-01-01
Have you restarted CUPS? It sometimes helps detect the printer:

```

sudo /etc/init.d/cupsys restart

```

Then go to System > Administration > Printing and go through the New Printer wizard.

---

### Post by jdcaserockies on 2006-01-01
Still doesn't work, although it recognized the printer as K80 instead of just Officejet...

---

### Post by Sef on 2006-01-04
Check out this post, I helped me to get my printer working:

[http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1600]("http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1600")

From it, Wondering Jew wrote in part (about his 1610 PSC)

> sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

---

