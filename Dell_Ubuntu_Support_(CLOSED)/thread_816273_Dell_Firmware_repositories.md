---
title: "Dell Firmware repositories"
date: 2008-06-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Loranga on 2008-06-02
Hey guys,

Have you also tried the Dell Firmware Repositories, see [http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware) ?

I must say that I like the idea very much, to be able to have the latest BIOS and other firmwares installed in the desktops, laptops and servers I maintain, which runs Ubuntu. (Dimensions, Vostros and a few PowerEdge 2900).

I am though not that impressed by the implementation itself. Installing by running that shell script as root does not feel as a proper solution. Also, the fact that it installs tools for RPM- and Yum compability feels a bit sketchy and messes up the system unnecessarily. I am fully aware that it is still in beta stage, but I think the feedback needs to come anyway.

Of course I could contribute by paying for it, but I don't see if that is an option, neither from Dell or Canonical.

What are you other guys' opinon?

---

### Post by peterhoeg on 2008-12-12
I am using it now, as I have started buying Dell exclusively due to their strong Linux support.

If you take a look at the script you download and run, you will see that what it does for Ubuntu/Debian is actually pretty straight forward and it doesn't install any rpm/yum tools at all. It basically boils down to:

a) Create a temp source.list fragment for apt
b) Add relevant keys
c) Create two proper Dell source.list fragments for apt for firmware and tools respectively
d) Update the package list

And you're good to go.

While it's not perfect (the packages should be depending on the proper tool packages, which they don't) it is still FAR better than what any other vendor does.

---

