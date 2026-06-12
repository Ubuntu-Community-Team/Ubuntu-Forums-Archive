---
title: "Need help deciding?"
date: 2006-11-20
forum: Desktop Environments
---

### Post by Al3xanR0 on 2006-11-20
Over the past week I have written serveral posts concerning my difficulties with the famed Beryl desktop effects. Each post has effectively gone unanswered the last I checked. I am not upset with that; I obviously must have posted questions to which no one had answers  -my response, no big deal you can't know everything right? The posts are listed below chronologically for anyone who is interested in setting me straight. If not, it is no big deal as I mentioned previously. I am a reasonably experienced user meaning I had enough sense to back up important config files contingent upon unsuccessful attempts. We have established that I am no expert, thankfully skilled enough to still have a working system. Now that we have moved passed that, let us go directly to heart of the matter, the reason for today's post.

I need help with a decision I do not like to make uninformed decisions they often result in calamity. In light of my recent troubles with getting Beryl to function properly 

> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I decided to explore other options. These options as you would imagine may have subsequent consequences, that dear reader is where you come in.

Choice 1: Add edgy repos to my dapper sources.list, upgrade to the latest nvidia-glx package caveated by the removal of linux-headers. I am ok with that with the exception of the fact that my Vmware install at one point relied on the linux-headers package, how will this impact vmware install if any?

Choice 2: Download and install the nvidia beta drivers caveated by the removal of linux-restricted-modules which the ipw3945 driver relies on, how will this impact my intermittent wireless conectivity if any?

By the way here are the unanswered posts

[post#1]("http://www.ubuntuforums.org/showthread.php?p=1698975#post1698975")
[post#2]("http://www.ubuntuforums.org/showthread.php?t=298467")
[post#3]("http://www.ubuntuforums.org/showthread.php?t=302171")
[post#4]("http://www.ubuntuforums.org/showthread.php?t=302409")

---

### Post by sethmahoney on 2006-11-20
Is there any particular reason you don't want to switch to Edgy?  If you're after Beryl effects, its probably the way to go...

---

### Post by Al3xanR0 on 2006-11-20
> **sethmahoney said:**
> Is there any particular reason you don't want to switch to Edgy?  If you're after Beryl effects, its probably the way to go...

I am certainly not opposed to making the switch to edgy; however, I am not opposed to the security of longevity ala ubuntu 6.06 LTS. I just assumed that I could play it safe by cautiously selecting necessary packages from edgy mirrors ala debian, essentially using dapper repos as stable and edgy as unstable or testing. The thought of having to upgrade every six months is an especially daunting prospect on a machine I consider to be somewhat of a production box. I don't mind upgrading; I am always interested in recent developments, I just prefer to do it less frequently. What are your thoughts on this perspective?:-k

---

### Post by sethmahoney on 2006-11-20
> **Al3xanR0 said:**
> I am certainly not opposed to making the switch to edgy; however, I am not opposed to the security of longevity ala ubuntu 6.06 LTS. I just assumed that I could play it safe by cautiously selecting necessary packages from edgy mirrors ala debian, essentially using dapper repos as stable and edgy as unstable or testing. The thought of having to upgrade every six months is an especially daunting prospect on a machine I consider to be somewhat of a production box. I don't mind upgrading; I am always interested in recent developments, I just prefer to do it less frequently. What are your thoughts on this perspective?:-k

The Ubuntu packages generally work kind of as a whole, so it can sometimes cause bizarro results if you're working with Dapper and try to install the occasional Edgy package.  And its not like Edgy is unstable - I've actually had fewer issues with it than with Dapper.  Its just not long term.  If you're going for eye candy, though, Edgy has all the x.org stuff ready to go for Beryl or Compiz (it also boots like 1000x faster), whereas Dapper takes some tweaking.

---

### Post by Al3xanR0 on 2006-11-20
> **sethmahoney said:**
> The Ubuntu packages generally work kind of as a whole, so it can sometimes cause bizarro results if you're working with Dapper and try to install the occasional Edgy package.  And its not like Edgy is unstable - I've actually had fewer issues with it than with Dapper.  Its just not long term.  If you're going for eye candy, though, Edgy has all the x.org stuff ready to go for Beryl or Compiz (it also boots like 1000x faster), whereas Dapper takes some tweaking.

Sound advise thank you:-D 
I'll see you in edgy

Regards,

Al3xanr0

---

### Post by Quietlife on 2006-11-20
Hi,
Re : Choice 1 and VMWare

FWIW
For as long as you do not upgrade the kernel you will not need the headers as you probably won't need to re-compile the bits that vmware uses to tie itself into the system.

I run a custom kernel (had to to get agpgart to work along with some ide dma patches) and find that swapping kernels requires a re-build of the vmware stuff to match the current running kernel.

In short if you don't plan to upgrade your kernel you *should* be fine.

---

### Post by Al3xanR0 on 2006-11-20
> **Quietlife said:**
> Hi,
Re : Choice 1 and VMWare

FWIW
For as long as you do not upgrade the kernel you will not need the headers as you probably won't need to re-compile the bits that vmware uses to tie itself into the system.

I run a custom kernel (had to to get agpgart to work along with some ide dma patches) and find that swapping kernels requires a re-build of the vmware stuff to match the current running kernel.

In short if you don't plan to upgrade your kernel you *should* be fine.

Thank you for your contribution, Quietlife.

Regards, 

Al3xanr0

---

