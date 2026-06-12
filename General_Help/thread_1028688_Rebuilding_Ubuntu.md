---
title: "Rebuilding Ubuntu"
date: 2009-01-02
forum: General Help
---

### Post by AlanMacdonald on 2009-01-02
Hello,

I'm interested in building Ubuntu from source code with different optimisations e.g. specifically compiled for Intel processor rather than generic i586.

I have found that the source can be obtained at [http://cdimage.ubuntu.com/releases/8.10/release/source/](http://cdimage.ubuntu.com/releases/8.10/release/source/) but I'm not sure how I would go about rebuilding the distro from there.  Does anyone know how to do this?

How would I found the CCFLAGS that Ubuntu does actually use at the moment so I can just tweak them?  Presumably Kubuntu etc uses some easy rebuild process?

At the moment I am running Linux Mint 5 (based on Ubuntu) in case that affects how the build works.

Yes I do know Gentoo exists.

Many thanks,

Alan

---

### Post by dcstar on 2009-01-02
> **AlanMacdonald said:**
> Hello,

I'm interested in building Ubuntu from source code with different optimisations e.g. specifically compiled for Intel processor rather than generic i586.
........

Compiling kernels (Ubuntu is *not* a kernel, it uses a kernel) are covered in various HOWTOs that can be found in this forum and elsewhere.

I doubt there is little that can be gained from any Intel specific compilation, since the "Generic" kernel is essentially Intel based.

---

### Post by AlanMacdonald on 2009-01-07
> **dcstar said:**
> Compiling kernels (Ubuntu is *not* a kernel, it uses a kernel) are covered in various HOWTOs that can be found in this forum and elsewhere.

Thanks for taking the time to reply but I know Ubuntu is not the same as the kernel.  I want to rebuild the WHOLE distro not just the kernel.  I mentioned Gentoo as thats the closest distro which works by default like that and the link I provided was for the whole Ubuntu source not just the kernel.  But thanks again for replying none-the-less.

> **dcstar said:**
> 
I doubt there is little that can be gained from any Intel specific compilation, since the "Generic" kernel is essentially Intel based.

Actually I was once given a custom compiled build of Firefox for my CPU and I wasn't expecting much of an improvement especially since I figured most of the time spent waiting in a web browser was on waiting for servers to respond etc but it was considerably better.  Compiling for a specific CPU architecture can provide significant improvements, so I am interested in trying it for a whole distro.  I am fairly convinced that an easy build process must exist hence number of offshoots to Ubuntu itself. 

Thanks.

---

### Post by Slim Odds on 2009-01-07
> **AlanMacdonald said:**
> Actually I was once given a custom compiled build of Firefox for my CPU and I wasn't expecting much of an improvement especially since I figured most of the time spent waiting in a web browser was on waiting for servers to respond etc but it was considerably better.  Compiling for a specific CPU architecture can provide significant improvements, so I am interested in trying it for a whole distro.

I used to want to squeeze every last drop of speed out of my kernel, etc.

You might get a 5-10% increase maximum. But it'll be a lot of work and when you're done you'll say, "why did I waste my time with that?".

Just my thoughts.....  good luck....

---

### Post by Woody1987 on 2009-01-07
I often thought about doing this exact same thing but instead i moved to arch linux.

---

### Post by AlanMacdonald on 2009-01-07
> **Slim Odds said:**
> I used to want to squeeze every last drop of speed out of my kernel, etc.

You might get a 5-10% increase maximum. But it'll be a lot of work and when you're done you'll say, "why did I waste my time with that?".

Just my thoughts.....  good luck....

Thanks.  Yeah I was thinking about for my eeepc really.  I could use Gentoo but I've never tried it and beyond the initial installation I don't want newly downloaded apps to be compiled every time (probably not great for the flash hard drive) which I believe Portage mainly does but I could be wrong.

Aside from the performance gains as a technical geek I was just interested in the Ubuntu build process.  I started having a quick look at the linux from scratch site but you had to manually download packages and things and I figured someone has done the work to put this mechanism in places for most of the main distros.  I just believe there is bound to be an easy way to take those source packages I linked to and compile it yourself but again I could be wrong.

Cheers.

---

### Post by AlanMacdonald on 2009-01-07
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) is all about packaging in Ubuntu.  It does mention building dsc files which are the source packages on the cd images I linked to.  I think by thoroughly reading this I should be able to get somewhere though it looks like it's setup more for explaining specific package building rather than the whole distro but I may be able to work from that.

---

