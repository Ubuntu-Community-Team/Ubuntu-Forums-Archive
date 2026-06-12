---
title: "Sony Ericson w715 in Ubuntu"
date: 2009-05-27
forum: General Help
---

### Post by ajmannen on 2009-05-27
Hello! I have bought at Sony Ericson W715 ..but can't figure out how to transfer music / podcasts to it via Ubuntu, and have to use windows which is horrifyingly slow. Any ideas?

---

### Post by larsman on 2009-06-24
Hi.

You just plug in the phone and choose the "Mass storage" option on the phone. The phone will then restart and both the phone memory and the memory card will be mounted as devices automaticly in Ubuntu. Then you can use Rythmbox or just the gnome file manager to copy songs to the location you want.

---

### Post by h0bbe on 2009-09-04
Is calendar and contacts synching between Evolution and SE W715 possible?

---

### Post by eazylip on 2010-02-04
Sorry,  Tried this and can see the file "Phone" and "Phone Card", but not able to mount volume or view files inside.  Any suggestions?

eazylip

---

### Post by tgalati4 on 2010-02-04
Immediately after plugging in the phone, go to a terminal and output the following:

dmesg | tail -40

---

### Post by tanpopo_chan on 2011-03-02
Hi, I have the same phone and I'm using Ubuntu 10.10 x64.

Sometimes, it doesn't connect correctly so you have to make sure that you first plug in the USB and THEN connect the phone, if not the phone won't react.

Secondly, Sony Ericcson, being the wonderful guys they are, have set up the phone for use with Linux distros. When you connect the phone it'll tell you that it's trying to connect with Windows but that **you need to press cancel to connect to other types of storage devices or OS**.

So hit cancel on your phone and a new list shows up. On the list there's the option "Other OS e.g. MacOS, Linux". Hit that and it'll automatically mount in Ubuntu.

Ubuntu will detect it as TWO cameras. One is the phone memory and the other is the memory card.

---

