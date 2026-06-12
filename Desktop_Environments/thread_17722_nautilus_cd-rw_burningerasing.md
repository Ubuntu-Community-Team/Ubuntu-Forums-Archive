---
title: "nautilus cd-rw burning/erasing"
date: 2005-03-02
forum: Desktop Environments
---

### Post by burlap on 2005-03-02
This is not a hardware issue! I can burn cds (cd-r and cd-rw) under CLI (cdrecord and cdrdao) or with other cdrecord frontends (xcdroast) and also cd-r burning works fine with nautilus cd-burner. I have a single combo drive (dvd+cd-r/rw), Ubuntu kernel (2.6.8.1-4-686, but it did not work with any previous Ubuntu kernels I used). 

The problem is: nautilus-cd-burner doesn't burn cd-rw (neither empty nor to-be-erased). First I thought (and posted on this forum only to get to know that I am not the only one) it was my only cd-rw record but today it was the same with a brand new one (though xcdroast recorded it without problems). 

Of course, I could stay with xcdroast but I like the idea of consistency and usability Ubuntu is based upon. And it is quite impossible to explain to newbies (I feel responsible for people that listened to me and now use Ubuntu) that they have to use different programs to record different cds. 

As nautilus-cd-burner depends on cdrecord I guess there should be a way to make  nautilus to use cdrecord the same way as xcdroast does. Or am I wrong?

---

### Post by amoser on 2005-03-02
easy burning in Ubuntu.  apt-get install cdda2wav, then go to [http://www.ubuntulinux.org/wiki/GnomeBaker](http://www.ubuntulinux.org/wiki/GnomeBaker) and download the warty package.
cd [browse to place it was downloaded to]
dpkg -i gnomebaker_0.3-1ubuntu1_i386.deb

bam, there you go, easy burning in Ubuntu

~Alan Moser

---

### Post by burlap on 2005-03-02
Again. Gnome-baker looks nice and all. I could give it a try. 

But that's not the point. 

The point is: why nautilus-cd-burner does not burn cd-rws (although cdrecord does)?

---

### Post by burlap on 2005-03-03
I have tried gnome-baker. Well, it does record cd-rws. 

But does not erase them (full or minimal). Back to post 1 then.

---

### Post by Jad on 2005-03-03
I think nautilus-cd-burner under development

---

