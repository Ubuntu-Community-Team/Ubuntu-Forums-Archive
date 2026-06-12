---
title: "Explaining desktop effects"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by sprucio on 2007-09-14
Can someone explain what the differences are between compiz, beryl, compiz-fusion, xgl and aiglx? When I first attempted to play with this, it was really just xgl and compiz (I don't even know the difference between the two) but now there is beryl and compiz-fusion.

From what I've read, I thought that beryl and compiz had merged together but I'm not sure if this is true.

---

### Post by Surkow on 2007-09-14
Yes Beryl and Compiz merged and therefore you should install Compiz Fusion. XGL is a layer on top of X to be able to run Beryl/Compiz. This layer is not needed when graphics card drivers use an extention for X called aiglx. This makes Beryl/Compiz a lot faster.

---

### Post by sprucio on 2007-09-14
So aiglx would be the better choice?

---

### Post by Surkow on 2007-09-14
> **sprucio said:**
> So aiglx would be the better choice?

Yes, but you currently need an nVIdia graphics card. If you have an Ati/AMD graphics card you will have to wait for a few months till it's supported.

---

### Post by pointone on 2007-09-14
First it was just Compiz. Beryl forked from the Compiz project because they wanted to do crazy wacky things the Compiz developers weren't so keen on. After some time, the two projects decided to re-merge to form Compiz Fusion.

Xgl is an X server that can use OpenGL for acceleration features. AIGLX is an indirect way of providing acceleration featuers (rather than using a new X server, it just passes information to the existing server). Unfortunately, AIGLX isn't supported in AMD's (ATI) latest drivers, so users of these video cards must use Xgl.

This is a VERY general overview. I'd suggest Google or Wikipedia if you want more information.

---

### Post by sprucio on 2007-09-14
I did read up on wiki but it looks like the last post made perfect sense. Thank you.

---

