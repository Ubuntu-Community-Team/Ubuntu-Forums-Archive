---
title: "Really new have no idea hwat im doing!"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by tallbus1 on 2007-10-03
Ok, um really stupid how this whole linux thing goes, got it like 3 hours ago.

In running linux on a Virtual Machine, but it works fine

The thing i s i followed a guide how to make Beryl work, but i dont know if it worked.  Wheveri try to start Beryl my whole entire Ubuntu shuts down, and has to reboot.  Please help.

---

### Post by peabody on 2007-10-03
Good luck trying to run something like Beryl through a virtual machine, I've never heard of anyone doing that before (not saying it isn't possible, I just doubt it's common or easy).

Beryl is one of those things that likes to have hardware acceleration, I'm not sure whether vmware can provide that or not.

---

### Post by tallbus1 on 2007-10-03
Well, thats what i think may be messing it up, becuase in this one file, forgot what it was, but you knwo the one where it talks about ur modules, anddevices, my video device doesnt say ATI Radeon (which is my video card)  it talks about VMware, but my friend some how got Ubuntu on his computer with XP with Vista, and kept his files, but i really do wnat to find a way to make Beryl work in my VM

---

### Post by tallbus1 on 2007-10-03
bump

---

### Post by peabody on 2007-10-03
Can't help you man.  I've never run beryl myself.  You might try searching the forums for Beryl and VMWare.

---

### Post by defrex on 2007-10-03
I've never done it (and I'm not sure if you can), but you would need to get vmware to give your vm direct access to the video card. If you can do that, you can probably get it running by the standard methods.

---

### Post by taehC on 2007-10-04
the best thing to do is a dual-boot...
there are guides all over the place but if u dual-boot u can have ubunut AND windows and keep ALL files.  just make sure you follow the instructions carefully or u might lose a lot of files...

---

### Post by tallbus1 on 2007-10-04
Cool, but the only thing is, the dual boot, can you link me a guide, and is it that hard?

---

### Post by nawitus on 2007-10-04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

There are plenty of guides, just use google. I would recommend defragmenting your hard-drive, downloading PartitionMagic and creating 2 partitions, a big partition of type ext3, and a partition the size of your ram of type swap. Then just put the Ubuntu cd and boot and follow instructions. Be sure to select the ext3 partition as '/'.

---

### Post by Chymera on 2007-10-04
dual boot means you just install ubuntu as another operating system, it's really kindergarten-easy. As for beryl:
1) i recommend you get compiz, since beryl has died anyway.
2) Depending on your ati model, you may have have a hell of a lot of work to do before getting it to run a composite manager...

---

### Post by meindian523 on 2007-10-04
> **Chymera said:**
> dual boot means you just install ubuntu as another operating system, it's really kindergarten-easy. As for beryl:
1) i recommend you get compiz, since beryl has died anyway.
Seconded....
> **Chymera said:**
> 2) Depending on your ati model, you may have have a hell of a lot of work to do before getting it to run a composite manager...

Not necessarily....I didn't need to run around too many trees to get C-F working....

---

### Post by Chymera on 2007-10-04
that's why I added depending on your model. Older ati cards are well supported, however for newer models, especially some of the x series, you will have to tweak your xgl... manually, which is a rather sad turn seeing as this is supposed to be the just-works linux distro :(

---

### Post by Rupertronco on 2007-10-05
> **Chymera said:**
> that's why I added depending on your model. Older ati cards are well supported, however for newer models, especially some of the x series, you will have to tweak your xgl... manually, which is a rather sad turn seeing as this is supposed to be the just-works linux distro :(

That has nothing to do with linux or the distro, in addition, compiz is still alpha. If you want to point fingers, point them at ati for having a crappy driver (fglrx) that doesn't have it's own TFP and requires the outdated xgl for 3d support. 

This will be fixed in due time now that the ati driver information is open source.

---

### Post by Chymera on 2007-10-05
im not saying that it would work on any other distro... just that if i were using gentoo i probably wouldn't complain about having to configure xgl by hand, because i'd expect to do things that way from the beginning... however in ubuntu i really would have solid reason to complain because it's supposed to just work, and since compiz (not compiz fusion) comes with ubuntu, it should be covered by "just work"

as for pointing fingers...  ati still has crappy drivers even for windows, why should it bother to make better drivers for linux? also, i doubt most drivers used by open source programs stem from manufacturers...

---

