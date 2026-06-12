---
title: "Online repositories"
date: 2009-04-08
forum: General Help
---

### Post by RedSingularity on 2009-04-08
Is there a website i can install items that are usually available in the package manager?  Say i want to get dependencies of some software and put them on a flash drive to transfer them to a computer with no internet.

---

### Post by taurus on 2009-04-08
[http://www.getdeb.net/](http://www.getdeb.net/)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by RedSingularity on 2009-04-08
Ah very good......this has dependency packages as well?

---

### Post by benj1 on 2009-04-08
i thought there was an option in synaptic for just downloading but not installing, but i can find it.
you could look in man apt-get see if anythings there or alternatively if you select the packages you want to download in synaptic and then go to 'file' then 'generate package download script' 

another option ive just thought of is to download aptoncd then put the packages you want on to a cd, thats probably the easiest, because if your other pc isn't connected to the internet you'll have to get lists of what packages are available for download, and transfer them over which is a pain.

in summary try aptoncd (its in the repos)

---

### Post by RedSingularity on 2009-04-09
Oh is there a place where i can download all the Repo's?  Lets say its for a system not connected to the internet but i want to update it.  Can i download them somewhere and save them to a flash drive for the computer not connected to the internet?

---

### Post by hyper_ch on 2009-04-09
all official repos are about 30 GB

---

### Post by benj1 on 2009-04-09
> **Shadow121 said:**
> Oh is there a place where i can download all the Repo's?  Lets say its for a system not connected to the internet but i want to update it.  Can i download them somewhere and save them to a flash drive for the computer not connected to the internet?

im fairly certain aptoncd sorts out updates, it also just creates an iso that you can put on your thumb drive to transfer, im certain you can mount isos in linux, but i think if you download aptoncd here 
[http://aptoncd.sourceforge.net/download.html]("http://aptoncd.sourceforge.net/download.html")
install that before the iso on your non internet pc then you can open the iso inside aptoncd (youll find it in 'system, administration')
it has instructions on there i think, and there will be on the internet, let me know if you have any problems.

re getting the repos you may just find it easier to buy the dvds online they only cost a few £/$/(select your currency)

---

### Post by RedSingularity on 2009-04-09
Oh that looks nice!  Very easy to use.  Thanks. :)

---

### Post by Rofii on 2009-04-09
> **benj1 said:**
> i thought there was an option in synaptic for just downloading but not installing, but i can find it.
you could look in man apt-get see if anythings there or alternatively if you select the packages you want to download in synaptic and then go to 'file' then 'generate package download script' 

another option ive just thought of is to download aptoncd then put the packages you want on to a cd, thats probably the easiest, because if your other pc isn't connected to the internet you'll have to get lists of what packages are available for download, and transfer them over which is a pain.

in summary try aptoncd (its in the repos)

```
apt-get -d install [software]
```

---

