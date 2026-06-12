---
title: "How to remove Opera?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Darrin on 2005-11-10
I decided I dont want to use it. Firefox is fine for me. How do I remove Opera? 
I know its sudo rm....something....something.  :confused:

---

### Post by NewWithoutClue on 2005-11-10
apt-get remove {packagename}

Paul.

---

### Post by oly on 2005-11-10
that depends how you installed it, if you used a deb search synaptic for it and use that to remove the program.

---

### Post by Darrin on 2005-11-10
[QUOTE=NewWithoutClue]apt-get remove {packagename}

Paul.[/QUOTE]

Thank you. :smile: 

Would this command basically work for all packages not downloaded through synaptic?

---

### Post by cowlip on 2005-11-11
Well it removes anything in the apt database, which includes debs you install by hand

---

