---
title: "installing E17 in 12.04"
date: 2012-04-26
forum: Desktop Environments
---

### Post by rmcellig on 2012-04-26
How can I install the E17 desktop environment in 12.04. I use to know how from the Synaptic Package Manager but now that SPM is gone in 12.04, I don't know what to do.

---

### Post by MG&amp;TL on 2012-04-26
```
sudo apt-get install e17
```

should do nicely. :)

---

### Post by rmcellig on 2012-04-26
That's easy! I wasn't sure if I had to install a PPA or not. Thanks!

---

### Post by Frogs Hair on 2012-04-26
To get the modules working you will need a PPA . The core packages are fine if you want to see what E17 is like.

---

### Post by rmcellig on 2012-04-26
Now that I ran sudo apt-get install e17 succesfully, what do I do next so that E17 is installed properly with the PPA etc...?

---

### Post by Frogs Hair on 2012-04-26
You should be able to select Enlightenment from the session list at login. To get the calendar, weather and other modules working you will need packages provided by the PPAS. You will have to search for 12.04 compatible PPAS. This is what I used with 11.10, but it has not been updated yet. [https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn)

---

### Post by worldwithoutgurus on 2012-04-27
@ rmcellig:

The packages from the Ubuntu repos are 2 years old and there are no PPAS for Ubuntu precise (yet).

The best way to get e17 (e + lots of modules & apps...) is via svn.

---

### Post by carranty on 2012-04-30
> **MG&TL said:**
> ```
sudo apt-get install e17
```should do nicely. :)

I'm trying to do the same but I just get the error "Unable to locate package e17"

**EDIT : Nevermind, it was just a proxy issue.  Apologies.**

---

### Post by worldwithoutgurus on 2012-05-12
**Update** &#8211; Recent binary packages for Ubuntu precise now available:
[https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn)

---

### Post by QIII on 2012-05-12
Jeff Hoogland at Bodhi Linux has what he says is a stable repo for his upcoming Bodhi 2.0, which is based on Precise.

He doesn't have even an Alpha out yet, but seems convinced that what he has should be stable enough to add the main repo to Precise -- which I assume has the E17 in it.

I'm going to install a clean Precise in a VM and add the repo to see if I can install E17 without having Precise barf all over.  I'll let you know what I find out.


Edit:  I got some dependency problems.  I'll try again later.

---

### Post by verdegal37 on 2012-08-26
> **worldwithoutgurus said:**
> **Update** – Recent binary packages for Ubuntu precise now available:
[https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn)

It works perfectly, but I recommend installing e17 with Lubuntu.
Image Lubuntu with E17:
[http://www.enlightenment.org/ss/e-5039df951ef4c9.55063093.jpg](http://www.enlightenment.org/ss/e-5039df951ef4c9.55063093.jpg)

Thanks!!!! Hannes ;)

Greetings:
Agust

---

### Post by vasa1 on 2012-08-26
> **verdegal37 said:**
> It works perfectly, but I recommend installing e17 with Lubuntu.
Image Lubuntu with E17:
[http://www.enlightenment.org/ss/e-5039df951ef4c9.55063093.jpg](http://www.enlightenment.org/ss/e-5039df951ef4c9.55063093.jpg)

Thanks!!!! Hannes ;)

Greetings:
Agust

Hi, why do you suggest installing E17 on Lubuntu and not other DEs?

---

### Post by rmcellig on 2012-08-26
I'm interested as well. I have Zorin 6 installed on my old Dell Dimension 3000 desktop (circa 2001). It's a bit sluggish and now you have peaked my interest in that Lubunu with E17 might be a better fit for my machine?

I have Puppy Linux installed and while it is blazing fast, I feel that I don't have the flexibility when it comes to apps that other distros have.

---

### Post by verdegal37 on 2012-08-26
> **vasa1 said:**
> Hi, why do you suggest installing E17 on Lubuntu and not other DEs?

From my experience of 7 years with E.
And:
E17 Tested in Ubuntu, Xubuntu and still say that the best option is Lubuntu.

Greetings and enjoy E.
Agust

---

### Post by verdegal37 on 2012-08-26
> **rmcellig said:**
> I'm interested as well. I have Zorin 6 installed on my old Dell Dimension 3000 desktop (circa 2001). It's a bit sluggish and now you have peaked my interest in that Lubunu with E17 might be a better fit for my machine?

I have Puppy Linux installed and while it is blazing fast, I feel that I don't have the flexibility when it comes to apps that other distros have.

Hi rmcelling , Try Zorin Lite, or Bodhi Linux and if you like Puppy try Macpup , more information here:

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)
And
[http://macpup.org/](http://macpup.org/)

Greetings and enjoy E.
Agust

---

### Post by rmcellig on 2012-08-26
I thought of Zorin Lite but I guess I was afraid of missing out some of the functionality of Zorin 6. My main concern is having access to the repos that Zorin accesses. I can install E17 in Zorin Lite to try it out? I tried Bodhi and Macpup and had issues with it. I'm willing to try them again though. 

As much as I love Puppy Linux, I always found it a pain tracking down pets for it even though the Puppy Forum have tons of them, it was still awkward for me.

---

### Post by verdegal37 on 2012-08-26
> **rmcellig said:**
> I can install E17 in Zorin Lite to try it out? 

Well rmcelling , right now I can only recommend what I'm trying and works well.

Is Lubuntu with E17.

Testing in mode Live cd , no?

For install E17 open Terminal with root copy and paste without quote:

"sudo apt-add-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
sudo apt-get install e17"

If you need help setting up your e17, let me know.

Greetings:
Agust

---

### Post by rmcellig on 2012-08-26
Thanks so much Agust!! I just booted my Dell Dimension 3000 with the live CD for Zorin 6 Lite, but now I think I may just take a look at Lubuntu again with your E17 instructions. I am somewhat familiar with E 17 having used it with Bodhi Linux.

---

