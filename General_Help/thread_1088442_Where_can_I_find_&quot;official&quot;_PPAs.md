---
title: "Where can I find &quot;official&quot; PPAs?"
date: 2009-03-06
forum: General Help
---

### Post by novafluxx on 2009-03-06
I've tried seaching in Launchpad and I come up with so many hits I have no idea what to do!

Just looking to get more 'bleeding edge' software for my 8.10 x64 installation.

My laptop doesn't have any important data, so I'd love to check out a kernel PPA for Ubuntu and check out the new kernels and such, programs like Berry for my blackberry, which I cannot find in Ubuntu's repos.

Thanks guys/gals!

---

### Post by novafluxx on 2009-03-06
*cricket, cricket*

Where is everyone? :P

Does anyone know where I can get a listing of PPAs??

---

### Post by Seq on 2009-03-06
[Launchpad's main PPA site]("https://launchpad.net/ubuntu/+ppas") gives you a search box, you could try there.

---

### Post by novafluxx on 2009-03-06
Hey thanks! Appreciate it!:popcorn:

---

### Post by Skripka on 2009-03-06
Also, enable the experimental/testing repos in Synaptic.

---

### Post by novafluxx on 2009-03-09
> **Skripka said:**
> Also, enable the experimental/testing repos in Synaptic.

How do I do that, I have multiverse and universe stuff enabled

You mean proposed updates and backports? Or is this something else entirely?

---

### Post by deepclutch on 2009-03-09
I think ,he meant for Debian!LOL! Only Debian got Testing ,Experimental Repostiories.and you may need apt-pinning for that.LOT of OT
--
For Kernel ,Why NOT Compile One Optimized for your PC?

---

### Post by ad_267 on 2009-03-09
You might be interested in enabling the backports repositories. There's a good guide to that here: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by novafluxx on 2009-03-09
> **ad_267 said:**
> You might be interested in enabling the backports repositories. There's a good guide to that here: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I turned on backports and all it offered was a new version of Gimp lol, not much else in there for updates! LOL I guess I should actually turn it on and search for packages not offered in the other repos, I thought backports was just for updates though!

Can I use Debian sid/unstable in Ubuntu? Won't APT and Synaptic keep me safe from dependancy issues?

---

### Post by deepclutch on 2009-03-10
No.Debian Dependencies are different.if for a new kernel(means you don't jump into compiling a kernel) ,may be ,getting Jaunty's kernel and core dependencies will do the job.

[http://packages.ubuntu.com/jaunty/linux-image-generic](http://packages.ubuntu.com/jaunty/linux-image-generic)
PS:if you are on proprietary drivers(graphics for eg:) or any other such things ,all will be broken and you need to install them manually.not recommended for someone new to Linux.

---

