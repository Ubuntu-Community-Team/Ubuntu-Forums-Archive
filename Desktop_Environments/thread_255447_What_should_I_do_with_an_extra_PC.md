---
title: "What should I do with an extra PC?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by dboot on 2006-09-11
Hello,

I have an extra PIII with a small HD that's not being used. It was an ubuntu webserver, but now I want to know my other options. Does anyone have suggestions?

Thanks!

---

### Post by hw-tph on 2006-09-11
Unless you really have any use for it, consider giving it (or loaning it) to a relative or a friend who would need a computer. Having a server running at home just for the sake of it may be fun the first couple of years until you realize why your power bills are so high, or when the computer in the closet catches fire and fills the entire building with smoke.

I have given away my fair share of hardware and then some, and all these computer still run Linux today.


Håkan

---

### Post by dboot on 2006-09-11
That's a good idea, but not aplicable for me. ;)  

I've thought about making it a Squid Proxy server, or MythTV Media Server, or something along those lines...

---

### Post by madmetal on 2006-09-11
what are your needs?
some suggestions.. 
media center is good..
proxy server and/or file server.
folding maybe?

---

### Post by OffHand on 2006-09-11
Use it to test Edgy ... or any other distro for that matter.
 ;) :twisted:

---

### Post by dboot on 2006-09-11
I don't exactly have a need for it...I just want to spend as much time experiencing different functionalities of Linux as possible. I'm currently dual booting with XP and Ubuntu, I play with Suse 10.1 on my laptop, and work with Solaris 10. So, I think I'm "testing" enough OS's (for now). :mrgreen: 

It has a small HD (4GB at most) so I decided against a file server. Even though I could always buy a larger HD, I'd like to find a use for it as is.

Keep 'em coming! :D

---

### Post by madmetal on 2006-09-11
mythtv for mediacenter,iptables and squid for firewall and proxy are worth trying i think...

---

### Post by dboot on 2006-09-11
I was thinking about MythTV, especially since they just came out with a new version.

I'm not sure how helpful a squid firewall and proxy would be. Anyone?

---

### Post by dboot on 2006-09-12
I tried installing MythTV last night. I decided it's better to have more than a 4GB HD...

Any other suggestions?

---

### Post by diggitydank on 2006-09-12
Do you have any use for a firewall? Why not install something like Smoothwall on it. I am piecing together a firewall box right now. I do not necessarily need more firewall than what is built into my wireless router or computers, but it is more a "proof of concept" deal for me. The spare computers I have are not useable by any of my family or friends, so this is my best option to tinker.

---

### Post by dboot on 2006-09-12
Smoothwall sounds interesting. Why did you choose it for your firewall box?

---

### Post by dboot on 2006-10-05
:bump:

Any new ideas? :-k

---

### Post by Iowan on 2006-10-05
"Services" box - DHCP, DNS, (mail?), (domain controller?). I also like the idea of a separate router/firewall.

---

### Post by tribaal on 2006-10-05
Whatever you choose, don't forget to install the BOINC distributed calculation package, and subscribe your machine to crunch for a generally useful project, like [rosetta@home]("http://boinc.bakerlab.org/rosetta/").

:)

- trib'

---

### Post by madmetal on 2006-10-05
> **tribaal said:**
> Whatever you choose, don't forget to install the BOINC distributed calculation package, and subscribe your machine to crunch for a generally useful project, like [rosetta@home]("http://boinc.bakerlab.org/rosetta/").

:)

- trib'


=D>

---

### Post by AgenT on 2006-10-05
If you want to experience Linux in the sense of learning more about Linux itself:[LIST=1]
[*]install [Gentoo]("http://www.gentoo.org/") from scratch and in a manual way - do not use automatic helper scripts or applications if they are available - and make sure everything works on your system that can possibly work (doing this manually and fixing things will teach you a lot very quickly)
[*]remove Gentoo - install [LFS]("http://www.linuxfromscratch.org/"). Like Gentoo, but even more hardcore (but not very useful except for teaching purposes) ;)[/LIST]Using this computer for something like a DNS server or firewall seems overkill. It needs too much (energy) power and has too much CPU power, etc. for that kind of job. Hopefully that helps you.

---

### Post by dboot on 2006-10-05
> **AgenT said:**
> install [Gentoo]("http://www.gentoo.org/") from scratch and in a manual way - do not use automatic helper scripts or applications if they are available - and make sure everything works on your system that can possibly work (doing this manually and fixing things will teach you a lot very quickly)

This sounds interesting...
How do you install Gentoo from scratch? Are you suggesting that I install the [minimal CD]("http://www.gentoo.org/main/en/where.xml")?

---

### Post by BLTicklemonster on 2006-10-05
Go to a local school, and ask if they have a computer teacher, then ask if they know of any disadvantaged students who seem as if they would really shine if they had a computer. If so, then make it an anonymous donation, though tech support for this kid might be something you would want to provide, so anonymously donating it may not be the best thing to do. You might become a kid's hero and be able to help a young person on the way to a career in hacki- I mean computers.

---

### Post by AgenT on 2006-10-05
> **dboot said:**
> This sounds interesting...
How do you install Gentoo from scratch? Are you suggesting that I install the [minimal CD]("http://www.gentoo.org/main/en/where.xml")?

In truth, it has been a few years since I used Gentoo. I installed it when it was pure console hacking and a *very* minimal manual (it just explained how to mount your system to begin install, then how to use portage, the gentoo "package" manager). Back then, there was only one CD and no LiveCD. :) I installed using stage3 tarball. Back then, there were 3 stages. But the *only* difference was that the larger the stage, the more source code tar files were included. This meant less downloading during install. But the install was exactly the same no matter which stage one chose. I had to setup everything, even the initial init scripts and chroot! ;) Everything was done through the console. No GUI nonsense! ;)

Taken from their website:
 The Installation CDs that we currently provide are:[LIST]
[*]     The Gentoo Minimal Installation CD, a small, no-nonsense, bootable      CD which sole purpose is to boot the system, prepare the networking and      continue with the Gentoo installation.
[*]     The Gentoo Installer LiveCD contains everything you need to install     Gentoo. It provides a graphical environment, **a graphical as well as console     based installer which automatically carries out the installation for you**,     and of course, the installation instructions for your architecture.[/LIST]Automatic installation? That is no fun! Go for minimal, although it might be that you will end up with automation sooner or later regardless. I cannot vouch for this. If you can, combine starge3 and minimal so that you have less downloInsert booklet has 1 inch crease on bottom-right side. ading to do later.

But do this only if you are not willing to donate to a good cause. Donating your hardware or your time is still the better option (as mentioned by others). Or combine both: after you are finished with installing Gentoo, LFS or whatever else, give it to someone with Ubuntu pre-installed. Maybe a family member, or someone else who would appreciate this gesture. The point being: use it if you have a decent purpose for it. If it will become some firewall that you do not really benefit from, give it to someone that will benefit from it more. Share the experience of Linux with others so that they may benefit from Linux just like you have. It is the Ubuntu way, after all.

---

### Post by CaveRat on 2006-10-05
Plus 1 for the donation to a worthy child. There are many very bright children in school who's parents cannot afford to go out and buy their kids a needed computer. Ubuntu would be a perfect learning experience to teach a child how to use the brain for more than playing kill games.

---

