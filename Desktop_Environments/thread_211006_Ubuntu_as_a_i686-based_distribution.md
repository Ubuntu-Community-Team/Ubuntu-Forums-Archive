---
title: "Ubuntu as a i686-based distribution?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Biffy on 2006-07-07
When downloading the Ubuntu ISO install CD, you can choose between i386 or amd64. I know that there are some i686 distributions out there (Arch Linux for example) and people say theese are very fast.

Will Ubuntu ever come as a 686 distribution?

---

### Post by vem0m on 2006-07-07
well i am not sure if it will come as one but u can always upgrade your kernel to a i686 version i have following [This Guide]("http://ubuntuforums.org/showthread.php?t=85917") it made it easy and works great :)

---

### Post by Max Luebbe on 2006-07-07
Yeah. Upgrading your kernel is pretty simple.
Search synaptic for 'linux' and your kernel type '686' or 'k7' etc

there's a package with both appended together that will keep your system updated with the latest kernel for your hardware.

It's probably a good thing that ubuntu comes in 386 and amd64 flavors as they are fundamentally different architectures.

Your 686 will run the 386 kernel, just not as fast.
I like the simplicity of current versioning, rather than having 6 or 7 choices for isos. Makes it simple for linux noobs who dont know how to get started either.

---

### Post by kpkeerthi on 2006-07-07
Not to start a flame. But I saw no difference in performance on my machine switching over to a 686 kernel. And there is no benchmark to prove the increase in performance. Installing 686 from the repo is just a snap. It just works and no need to compile, if you are not into that kind of business. But 386 is just as good and I'm happy. Oh...well... thats just me.

---

### Post by Biffy on 2006-07-08
Yes, i am using the 686 kernel. But why not an 686 version of Ubuntu to make it as fast as Arch and Gentoo? If "noobs" can't choose the right ISO, just get some text there explaining it to them.

I sure hope this is something the devs are aware of.

---

### Post by MetalMusicAddict on 2006-07-08
Search the forum Biffy. There were/are MANY chats about this.

---

### Post by Biffy on 2006-07-10
> **MetalMusicAddict said:**
> Search the forum Biffy. There were/are MANY chats about this.

Yes, but i can't find a reason WHY there is no 686 version of Ubuntu. Is this something that is on the way? In my eyes, it would make Ubuntu complete.

---

### Post by aysiu on 2006-07-10
I think it was to support as many machines out there as possible.

I, like kpkeerthi, have tried several kernels and noticed no speed or performance difference. I tried 686. I tried K7 (which is supposed to be "ideal" for my AMD processor). The same as i386--both of them.

---

### Post by Biffy on 2006-07-10
> **aysiu said:**
> I think it was to support as many machines out there as possible.

I, like kpkeerthi, have tried several kernels and noticed no speed or performance difference. I tried 686. I tried K7 (which is supposed to be "ideal" for my AMD processor). The same as i386--both of them.

Sure, just keep the 386 version. But there sould be a 686 version too, for us that know what we are doing.

Im also using 686 kernel, not noticing any difference from the 386.

---

### Post by vem0m on 2006-07-10
rthe differance lies in its support for SSE, and other cpu specific otimizations its not so noticable to the point u'll see ur computer fly but its there if used under heavy stress

---

### Post by elettronicha on 2006-07-10
Here it is why Ubuntu chose i386 optimization: [http://ubuntuforums.org/showthread.php?t=169422](http://ubuntuforums.org/showthread.php?t=169422)

In fact just a 686-optimized kernel doesn't speed up the system so significantly, and I would be very happy if someone posted some benchmarks to prove the opposite :) It just adds supports to the new architecture and to newer hardware.
Instead it is true that a system with the whole packages optimized for 686 archs (or at least a subset of packages, such as gcc, glibc, binutils, X and the Desktop Env) is faster.

---

### Post by Biffy on 2006-07-10
And it would also be great if Ubuntu came with prelinking out of the box.

---

### Post by Biffy on 2006-07-10
> **elettronicha said:**
> 
Instead it is true that a system with the whole packages optimized for 686 archs (or at least a subset of packages, such as gcc, glibc, binutils, X and the Desktop Env) is faster.

Yes, im talking about the whole system being 686. All the packages you fetch from APT is 686, not only some of them.

---

### Post by vem0m on 2006-07-10
hmmmm never had a problem with any of that thing is prelinking is a optimization that varies per user according to what they have installed and what they acually want linked in otherwords its users custom work and effort if they was to do it automatically it would be alot of scripting and certian things that need not be linked might end up that way just cuz it was there to do so with i think it should remain the users choice with these things as the way it is is of course the most compatible between platforms

its i386 as its most compatible between all platforms instead of hey i gotta d/l this one for this computer, this other one for this other computer of mine, and this one over here needs this one? isn't much better to be able to d/l one and use it with all ur computers then update and go from there?

---

### Post by aysiu on 2006-07-10
> **Biffy said:**
> And it would also be great if Ubuntu came with prelinking out of the box.
That was hotly debated [in this thread](http://www.ubuntuforums.org/showthread.php?t=203854). Some agree with you--others don't.

---

### Post by Biffy on 2006-07-10
> **aysiu said:**
> That was hotly debated [in this thread](http://www.ubuntuforums.org/showthread.php?t=203854). Some agree with you--others don't.

I know that people are warned before trying it out, but if it came right out of the box (like in Suse) i think it would be really neat. :eek:

---

### Post by vem0m on 2006-07-10
well seeing u are talking about a BOGGED down distro i used it before ubuntu its a system resource hog and slower then ubuntu by far wrong comparison to use methinks :P

---

### Post by Biffy on 2006-07-10
> **vem0m said:**
> well seeing u are talking about a BOGGED down distro i used it before ubuntu its a system resource hog and slower then ubuntu by far wrong comparison to use methinks :P

Hehe, sorry about that.

Well, people are saying that i686-based distros does not make them faster. But then i wonder, what is making ArchLinux so fast? Is it NOT that it is an i686 distro?

---

### Post by vem0m on 2006-07-10
i thinks that its due to the DE but i am unsure also might be due to thier lack of real software that it comes with but once again i am unsure i am however pretty certain with a lil work (K)ubuntu could be as fast if not faster linux takes time and is a work of the users art showing what they can do and make linux do for them and that is the way it should be u get what u put into it :)

---

