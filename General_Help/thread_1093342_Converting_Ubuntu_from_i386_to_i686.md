---
title: "Converting Ubuntu from i386 to i686"
date: 2009-03-11
forum: General Help
---

### Post by Neo_The_User on 2009-03-11
I would like to convert / re-package every single package from i386 to i686. Is there a deb packager I can use to do that? It's fine if I could only do one at a time. I don't mind if it takes all day or all week.

---

### Post by thtrgremlin on 2009-03-11
Do you mean 64-bit?

The best solution is honestly to backup important data and do a clean install. Trying to "roll it over" can only create more problems and ake quite a bit more time.

Just my opinion.

---

### Post by MaxIBoy on 2009-03-11
No, he doesn't mean 64-bit.


i686 is i386 with a bunch of new instructions added. Programs compiled for i686 run faster on i686-enabled processors.

Pentium is i586, and the Core/Core 2 processors are i686.

---

### Post by Neo_The_User on 2009-03-11
MaxIboy, right on! The AMD K7 family of CPUs are also i686.

---

### Post by LowSky on 2009-03-11
Actual Core i7, Core 2 Duo, AMD Phenom, and such are all 64bit processors that have support of the x86 (386 and higher) instruction set.

there hasn't been  anything lower than 686 since the mid-1990's. I doubt the spped difference that great on today's processors... maybe 10 years ago this was an issue but today, not even an issue, we are all going form 32bit to 64, thats where concern is.

If your running a Phenom 2, why not use 64 Bit Ubuntu ?

---

### Post by kaivalagi on 2009-03-11
I think all packages would need re-compiling with the correct flags right?

It's a good point though, why does Ubuntu stick to compiling to i386? Why not go to i686 for 32 bit?

Not that I'm too bothered as I use 64 bit anyway, but Arch and Mandriva (I think) are i686 based for 32 bit...

---

### Post by MaxIBoy on 2009-03-11
> **kaivalagi said:**
> It's a good point though, why does Ubuntu stick to compiling to i386? Why not go to i686 for 32 bit?

Not that I'm too bothered as I use 64 bit anyway, but Arch and Mandriva (I think) are i686 based for 32 bit...
Hell if I know. Ubuntu actually compiles for i486, not i386, but you're not going to run Ubuntu (probably not even the server edition) on anything sub-Pentium1, so the logic of sticking with i486 escapes me.

---

### Post by Neo_The_User on 2009-03-28
oh yeah it is compiled for i486. as when i looked in the gcc folder in /usr, it was i486-linux-gnu. but.. why is every package marked as i386 when a .deb package?

P.S. i switched to arch so i didn't have to rebuild ubuntu for i686. XD

---

### Post by Slim Odds on 2009-03-28
Most every version of linux has been optimized for pentium class processors for quite some time now. The i386 just refers to the general architecture.

---

### Post by kaivalagi on 2009-03-29
> **Slim Odds said:**
> Most every version of linux has been optimized for pentium class processors for quite some time now. The i386 just refers to the general architecture.

Good move, you sound like the sort of person that will get a lot out of Arch...and it is lightening quick if you want it to be :)

I am still using ubuntu as my main OS though...too many script packages to support and I like deb stuff too

---

