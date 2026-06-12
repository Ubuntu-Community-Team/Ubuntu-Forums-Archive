---
title: "dpkg interupted ?? Can't use updates now :("
date: 2009-02-03
forum: General Help
---

### Post by Windy Peaks on 2009-02-03
Ladies and Gentlemen of the forum:

I get this error message when I try to use the update manager or in Terminal mode "sudo apt-get update"

you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Has anyone found this bugs fix yet ??

Kind regards
Windy

---

### Post by Crafty Kisses on 2009-02-03
Run the following in Terminal:
```
sudo dpkg --configure -a
```

---

### Post by dcstar on 2009-02-03
> **Windy Peaks said:**
> Ladies and Gentlemen of the forum:

I get this error message when I try to use the update manager or in Terminal mode "sudo apt-get update"

you must manually run '**dpkg --configure -a**' to correct the problem. 
E: _cache->open() failed, please report.

Has anyone found this bugs fix yet ??

Kind regards
Windy

So you have done that command then (via sudo)?

---

### Post by kostkon on 2009-02-03
Close *Synaptic* or *Add/Remove* (or the *Update Manager*), if you have them open. Then open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give:
```
sudo dpkg --configure -a
```
it will ask you for a password, give yours.

Then, in the terminal again, give
```
sudo apt-get update
```
You should then be fine.

Hope that helps.

---

### Post by mb_webguy on 2009-02-04
We should really make some sort of sticky basic troubleshooting guide and have this problem posted in bold at the top of the list.  I see a thread just like this every couple of days...

---

### Post by Windy Peaks on 2009-02-07
Sorry My bad:
I did not include this part due to the fact that I was not sure that I was running this command properly.

I did try "sudo dpkg --configure -a"

but received 

"dpkg: ../../src/packages.c:221: process_queue: Assertion "dependtry <=4" failed."

"Aborted"

instead of a working update manager.

Windy

---

### Post by Windy Peaks on 2009-02-07
Hello David:

I am in Melbourne Australia as well and got the Ubuntu 8.10 off the internet at faster optus speed than I have ever since before are You the one that released it in late October 08 ??  
If so thanks

Windy

---

