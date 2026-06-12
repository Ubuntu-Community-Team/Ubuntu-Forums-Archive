---
title: "Desktop effects could not be enabled in ubuntui 7.10"
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by ramanand on 2008-04-07
here is my outpout for compiz

foss@foss-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


plz some one help me...:(

---

### Post by chewearn on 2008-04-07
What graphics card do you have?  Why do you add a poll to your support request?

---

### Post by warbread on 2008-04-08
> **ramanand said:**
> here is my outpout for compiz

foss@foss-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


plz some one help me...:(

First of all, make sure you have your card's drivers installed.  Second, the command you want to use is:

:~$ compiz --replace

---

### Post by FuturePilot on 2008-04-08
"compiz" is the same as "compiz --replace" now with the implementation of the Compiz wrapper script.

---

### Post by warbread on 2008-04-08
I see.  So behind the times am I.

---

### Post by ramanand on 2008-04-08
my graphic card is Intel  845
and driver installed is "vesa-generic VESA-compliant video cards"

sill i get same problem 
i used compiz --replace

foss@foss-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

help me out:confused:

---

