---
title: "Apt-get Problems"
date: 2006-10-05
forum: Desktop Environments
---

### Post by flummoxed on 2006-10-05
E: Problem parsing dependency Depends
E: Error occurred while processing kcontrol (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

All of a sudden I'm getting this error when I start synaptic, and I can't download and install any packages. I'm not quite sure what went wrong. Anyone know what's broken, and how to fix it?

---

### Post by Naegling23 on 2006-10-05
try running 

sudo dpkg -configure -a

(I think thats the command)

See if that works.

---

### Post by flummoxed on 2006-10-05
I don't think that's the right command. What's it supposed to do?

---

### Post by moore.bryan on 2006-10-05
*can you apt-get from term?*

---

### Post by flummoxed on 2006-10-05
Nope. Gives me an error at reading package lists.

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing kcontrol (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by moore.bryan on 2006-10-05
*well, at least we know the problem isn't with synaptic alone.  have you tried aptitude?*

---

### Post by flummoxed on 2006-10-05
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing kcontrol (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing kcontrol (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

That was with aptitude. Whats the diff between apt-get and aptitude anyways?

---

### Post by flummoxed on 2006-10-05
Weird, I just ran automatix... didn't download anything, and let it restore my original list, and it fixed apt...

---

### Post by moore.bryan on 2006-10-06
*hey, don't knock serendipity!  some people will say aptitude is better than apt-get because of its advanced dependencies resolution mechanism... i've had weird circumstances where apt-get and synaptic won't work, but aptitude will.  whatever the cause, i'm glad it's back to working for you...*

---

