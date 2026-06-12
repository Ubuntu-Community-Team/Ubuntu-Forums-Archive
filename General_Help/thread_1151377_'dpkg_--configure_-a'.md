---
title: "'dpkg --configure -a'"
date: 2009-05-06
forum: General Help
---

### Post by 1parria on 2009-05-06
I keep getting this weird error message whenever I try to add remove programs.

_**Error Message**_[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

I'm not very used to ubuntu and I am having some problems figuring it out. I have Ubuntu 9.04 Running on a HP desktop. It has an Intel Pentium 4 Processor. 


Any help would be greatly appreciated.

---

### Post by Seventh Reign on 2009-05-06
Your system probably crashed while updating or installing a package.

Run 'dpkg --configure -a' in the terminal like it says. 

Minus the 2 '

---

### Post by kostkon on 2009-05-06
Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give:
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

---

### Post by Seventh Reign on 2009-05-06
When I say Run I mean Type or Copy and Paste 

dpkg --configure -a

into your terminal

---

### Post by jflaker on 2009-05-06
> **1parria said:**
> I keep getting this weird error message whenever I try to add remove programs.

_**Error Message**_[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

I'm not very used to ubuntu and I am having some problems figuring it out. I have Ubuntu 9.04 Running on a HP desktop. It has an Intel Pentium 4 Processor. 


Any help would be greatly appreciated.

Click on APPLICATIONS then ACCESSORIES then TERMINAL

Type
```
sudo dpkg --configure -a
```

It will ask for your password...type it in and that should fix your problem.

---

### Post by 1parria on 2009-05-06
Nevermind, I forgot the "Sudo". It worked, thanks for the help.

---

