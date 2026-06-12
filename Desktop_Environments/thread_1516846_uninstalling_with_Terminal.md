---
title: "uninstalling with Terminal"
date: 2010-06-24
forum: Desktop Environments
---

### Post by TXbirder on 2010-06-24
I installed the free AVG anti-virus.  Just thought I'd give it a try.  It's too much work- no GUI.  So I want to get rid of it.   

Following the uninstall instructions in the AVG manual I enter: **sudo dpkg -r avg85flx-r812-a3371.i386.deb**.   Terminal's response is: ** dpkg: you must specify packages by their own names, not by quoting the names of the files they come in.**

To make sure I got the name right I started a download, without clicking OK.  
The downloader says:  [FONT=Microsoft Sans Serif][SIZE=2]You have chosen to open[/SIZE][/FONT] **avg85flx-r812-a3371.i386.deb **[FONT=Microsoft Sans Serif][SIZE=2]which is a: Software package from......  etc etc.[/SIZE][/FONT]

If this is not the name of the package, how do I find the name?  I don't want to leave this unused program in my computer indefinitely.  Is there an entry that says "What is the name of the package that contains the software package **avg85flx-r812-a3371.i386.deb**?"

John

---

### Post by radddi on 2010-06-24
When uninstalling you need to use the package's name which is used in your system, not the file it comes from. You can find the package name in Synaptic: System >> Administration >> Synaptic Package Manager. The package should be listed there even if does not come from the Ubuntu repositories.

.:CheerS:.

---

### Post by Javich on 2010-06-24
The actual .deb file it's just not how the package manager finds it; as radddi said I'd recommend using synaptic.

Just open a console, type ```
sudo synaptic
```, then search for "avg", on the leftmost column (the ones that indicate if it's installed) click on it's title to make the installed packages go on top (or bottom), find AVG, then kill it!

Another approach would be to use only the command line to do so:
Step 1: find the package:

go to a terminal, then ```
sudo dpkg --get-selections | grep -i avg
``` the left column will tell the package name. If it shows in there, just type  ```
sudo dpkg --remove <the_package_name_in_here
``` where "the_package_name_in_here" may be something like "avg_server" or "avg something"

Cheers,
Javier

---

### Post by ThesaurusRex on 2010-06-24
Does it show up with aptitude?```
sudo aptitude remove avg
```It'll probably say "avg not found," but then give you a list of avg-like names you could remove.

---

### Post by TXbirder on 2010-06-24
I found it.  It is named avg85flx.  When I type  [FONT=Microsoft Sans Serif][SIZE=2]sudo dpkg --remove avg85flx[/SIZE][/FONT] .   Terminal responds: [SIZE=2] [/SIZE][FONT=Microsoft Sans Serif][SIZE=2]dpkg: status database area is locked by another process[/SIZE][/FONT].

I exited Terminal and tried again and got the same response.  What other process is locking it?   I'm the only user and the only thing I'm doing is this.

John

---

### Post by TXbirder on 2010-06-24
Never mind.  I think I got it.  I had the Synaptic Package Manager open while doing this so I'd be sure to get the name right.   I closed the SPM and the removal ran.

Thanks to you all.
John

---

