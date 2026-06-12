---
title: "Linux based cluster for Distributed Password Cracking"
date: 2006-12-20
forum: Education &amp; Science
---

### Post by Ted_Smith on 2006-12-20
Hi

I work in an area known as 'forensic computing' for the UK government - basically it's the investigation and submission to court of criminal evidence found on digital devices. 

Without giving too much away of course, we have a cluster of computers (100 or so) that run a special piece of software that enables distributed cracking of password protected documents. Basically, there's a master client that receives the password protected documents from the user, and then the 100 or so army of computers work to crack it 24/7.

Currently this is all Windows based - a Windows OS, and a Windows client on each of the machines. 

Is there anything in the Linux world that could do the same thing? I ask for the simple reason that if there is not, I might try to make one for my masters (MSc) project and then release it to the law enforcement community for free (as is often the case in forensic computing). A big deal, and probably beyond me (cause I aint no Einstein!), but it's worth giving some thought. Currently we pay a few thousand British pounds for an annual subscription to the software alluded to above. 

Any info, links, contact points warmly received. 

Thanks

Ted

---

### Post by msemtd on 2006-12-20
Do you have the source code for the distributed application? Or are you looking for a piece of distributed software that does the same job? There are a number of FOSS distributed frameworks to choose from. Basically you're handing out work packages to the available nodes. Nothing too difficult there if the application fits the bill.

---

### Post by Ted_Smith on 2006-12-20
Hi

Thanks for the response. 

> Do you have the source code for the distributed application? No, I do not have the source code for the software we use currently. It's a closed source Windows app that costs a few thousand. 

> Or are you looking for a piece of distributed software that does the same job? I am looking to **create** a piece of software that does the same job, for free, as my project, perhaps. 

> There are a number of FOSS distributed frameworks  Do you have links where I could read more about this? I'm not sure I understand what you mean when you say 'for you to choose from'? I'm aware of the various Grid computing apps like SETI@Home, etc, but I don't think this is what you mean, or is it? What is FOSS?

---

### Post by AtrejuT on 2006-12-20
reasonably easy if you want to implement your own distributed computing appliation is to use the MPI (Message Passing Interface). There's a couple implementations notably MPICH which is available here: [http://www-unix.mcs.anl.gov/mpi/mpich/index.htm#download](http://www-unix.mcs.anl.gov/mpi/mpich/index.htm#download)

using this you can acually mix operating systems however you like as long as this library is available. I started looking at this a bit for some physics calculations I might want to do (for my MSc...) but I don't really know much about it yet. (And I'm a physicist, not a software engineer....)

You'll still have to implement the cracking yourself though. This just helps you distributing it to the various computers involved.

atreju

---

### Post by az on 2006-12-20
I'm sure there are other apps like this in the repos:

[http://packages.ubuntu.com/edgy/admin/medussa](http://packages.ubuntu.com/edgy/admin/medussa)


Package: medussa (0.8-4) [universe]Distributed password cracking systemMedussa is a distributed password cracking system that can attempt various types of attacks to crypted passwords distributing the work on many machines.


Maybe your MSc project can be a migration plan?

---

### Post by msemtd on 2006-12-21
> **Ted_Smith said:**
> 
 No, I do not have the source code for the software we use currently. It's a closed source Windows app that costs a few thousand. 

 I am looking to **create** a piece of software that does the same job, for free, as my project, perhaps. 

OK, a few thousand seems appropriate for the software you describe (in the proprietary software world at least!) If you can get some sort of spec for the password cracking capabilities it has, I'm sure I (or Google) can point you at an equivalent free alternative.
> **Ted_Smith said:**
> 
 Do you have links where I could read more about this? I'm not sure I understand what you mean when you say 'for you to choose from'? I'm aware of the various Grid computing apps like SETI@Home, etc, but I don't think this is what you mean, or is it? 
Hmm, not to hand and certainly not up-to-date -- Google, freshmeat, and sourceforge are your friends here :) search for "distributed computing".
> **Ted_Smith said:**
> What is FOSS?
"Free Open Source Software" (see [http://en.wikipedia.org/wiki/Free_and_open-source_software](http://en.wikipedia.org/wiki/Free_and_open-source_software) if you haven't already :) )

---

