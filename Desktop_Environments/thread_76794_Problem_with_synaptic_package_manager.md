---
title: "Problem with synaptic package manager"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Redindian on 2005-10-15
Yesterday i upgraded my hoary to breezy,

1. Whenever i login gnome, the following error message pops-up "Failed to load image synaptic.png" Details: icon not found.

2. I dont see synaptic package manager in my applications menu. But i do have a synaptic icon in my panel, whenever i click that, it gives me the following error "Failed to run /usr/sbin/synaptic as user root: child terminated with 1 status". 

3. I dont know what went worng with my installation. If i want to reinstall, do i need to remove anything before reinstallation or how can i do the complete reinstallation of breezy?

Thanks.

---

### Post by ebridge2001 on 2005-10-15
I upgrade my ubuntu 5.04 to 5.10  ,the Synaptic cannot to use too.

I can run it,but when pop a windows input for pasword.then input ok,  the programe still cannot run.

I remove it,and the install again . It still cannnot run.

who can helo me ?   Thanks.

---

### Post by az on 2005-10-15
Open a terminal and type
sudo apt-get -f install

sudo apt-get update

sudo apt-get install ubuntu-desktop


And if that still doesn't do it for you,

sudo apt-get install synaptic.

---

### Post by ebridge2001 on 2005-10-15
[QUOTE=azz]Open a terminal and type
sudo apt-get -f install

sudo apt-get update

sudo apt-get install ubuntu-desktop


And if that still doesn't do it for you,

sudo apt-get install synaptic.[/QUOTE]


:(   All above the thing ,I had done.

But The synaptic still cannot work.    

Do you have any other mothed ?  Thank you?

---

### Post by Rory on 2005-10-15
I've had the same problem.  It has occurred after I've updated my sources.list via terminal and saved it.  Synaptic seems to choke on the new repositories and it won't open.  However, if I change the repositories via Synaptic, I'm fine.  

Does this sound like it may the be issue you're experiencing?

One thing that worked for me was removing synaptic via apt-get and then re-installing.  Seemed to do the tricks.

---

### Post by ebridge2001 on 2005-10-16
[QUOTE=Rory]I've had the same problem.  It has occurred after I've updated my sources.list via terminal and saved it.  Synaptic seems to choke on the new repositories and it won't open.  However, if I change the repositories via Synaptic, I'm fine.  

Does this sound like it may the be issue you're experiencing?

One thing that worked for me was removing synaptic via apt-get and then re-installing.  Seemed to do the tricks.[/QUOTE]


Now I can only via 'Add Aplications' to change the new repositories. Becases I cannot open Synaptic.

Becase my sources.list I had via terminal saved it.How I via your method to chang it?  Thank you!

---

### Post by Rory on 2005-10-16
You'd be typing in terminal something like.

sudo apt-get rm synaptic
... and then uninstalling all of it.

Then:
sudo apt-get install synaptic
... to install everything and pick up the new sources.list

However, google a bit about terminal commands first as I'm pretty lame at commands and am going from memory, so I don't want to mislead you.

As well, this is how I resolved the issue.  There may be an easier way, which someone will post about.

---

### Post by yage on 2005-10-16
To remove synaptic completely use the purge flag.
```
sudo apt-get remove --purge synaptic
```

---

