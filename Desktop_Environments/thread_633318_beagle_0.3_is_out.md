---
title: "beagle 0.3 is out"
date: 2007-12-06
forum: Desktop Environments
---

### Post by Psykotik on 2007-12-06
A new Beagle release, after 6 months of development, is available on beagle website : [http://beagle-project.org/Main_Page](http://beagle-project.org/Main_Page)

One of the most fancy features, so much awaited, the thunderbird indexing ability. Check the change log : [http://svn.gnome.org/viewvc/beagle/tags/BEAGLE_0_3_0/beagle/NEWS?view=markup](http://svn.gnome.org/viewvc/beagle/tags/BEAGLE_0_3_0/beagle/NEWS?view=markup)

Enjoy!

---

### Post by Psykotik on 2007-12-08
Is someone using beagle, or am I alone into the Ubuntu community? :)

---

### Post by shaitan on 2007-12-08
oh yes

I love beagle, but I'm still using 0.2.18...

did you already compile beagle 0.3?

---

### Post by Psykotik on 2007-12-08
I'm always somewhat lost when compiling such complex software. I'm still stuck with... 0.16.3!

Which is a shame, since this last update is so hot!

---

### Post by Espreon on 2007-12-08
I'd use Beagle if it did not leak memory. Are the memory leaks fixed yet in 0.3?

---

### Post by dbera on 2007-12-09
Maybe someone should ask the beagle packager to backport beagle to gutsy :) What is the backport policy for gutsy - are major updates allowed to be backported ?

---

### Post by gmaniac on 2007-12-09
Great news
I've dropped bugfull tracker long ago for the hound.

---

### Post by Psykotik on 2007-12-09
> **Espreon said:**
> I'd use Beagle if it did not leak memory. Are the memory leaks fixed yet in 0.3?

Well, according the changelog :

"Many speed and memory performance improvements in both indexing and  searching throughout the code."

and 

"Queries are run serially rather than in parallel, since most of the  search overhead is in disk IO.  Reduces memory usage considerably,  and helps prevent disk thrashing on large searches."

Work has been made in the memory issues...

---

### Post by shaitan on 2007-12-10
> **dbera said:**
> Maybe someone should ask the beagle packager to backport beagle to gutsy :)

in hardy, at the moment, there is still beagle 0.2.18 ;)

---

### Post by shaitan on 2007-12-10
Hi all,

I've installed it without problems...

I have to rebuild all indexes, but it seems quite quick 

I love thunderbird indexing :-D

---

### Post by Psykotik on 2007-12-11
> **shaitan said:**
> Hi all,

I've installed it without problems...

I have to rebuild all indexes, but it seems quite quick 

I love thunderbird indexing :-D

Hi Shaitan,

Would you like to share the debs, if it happens you are able to build them?

It has always been a pain to make them, and I'm quite eager to use the thunderbird indexing :)

---

### Post by shaitan on 2007-12-12
You can try this one [http://www.chela.it/deb/](http://www.chela.it/deb/)

You've to remove beagle-backend-evolution

I had to delete all my indexes (probably for a bug corrected in [0.3.1]("http://svn.gnome.org/viewvc/beagle/tags/BEAGLE_0_3_1/beagle/NEWS?view=markup")

Please be careful: i'm not a mantainer, nor an expert...debs could be dangerous :)

debs are created with dh_make 

configure option: i686

        Beagle version:           0.3.1
        Target OS:                linux
        Inotify:                  yes

        Prefix:                   /usr
        GNOME prefix:             /usr
        KDE prefix:               unknown; will guess at runtime

        evolution-sharp?          yes
        gsf-sharp?                yes
        galago-sharp?             no
        avahi-sharp               no (missing dependencies)
        wv1?                      yes
        libchm?                   yes

        Firefox Extension?        yes
        Epiphany Extension?       no (Epiphany not installed)
        Thunderbird Extension?    yes

        Local taglib-sharp?       yes

        Monitor screensaver       yes
        beagle-search GUI         yes

---

### Post by gborzi on 2007-12-12
Hello,
I'm using beagle too. I tried tracker on feisty and again in gutsy, but after some time turned back to beagle. I've made the .deb files for beagle 0.3.1 and libbeagle 0.3.0 by hacking the debian files of the gutsy version of beagle. Unfortunately libbeagle 0.3.0 doesn't provide libbeagle.so.0, which is required by nautilus, so I only installed beagle. I would share them, but I don't know how.

Regards.

---

### Post by Psykotik on 2007-12-12
> **shaitan said:**
> You can try this one [http://www.chela.it/deb/](http://www.chela.it/deb/)

You've to remove beagle-backend-evolution

I had to delete all my indexes (probably for a bug corrected in [0.3.1]("http://svn.gnome.org/viewvc/beagle/tags/BEAGLE_0_3_1/beagle/NEWS?view=markup")

Please be careful: i'm not a mantainer, nor an expert...debs could be dangerous :)


I installed your beagle 0.31 debs, and it runs very well!

Thanks a lot.

---

### Post by dbera on 2007-12-12
Maybe these guys won't mind using your debs (or might use your debs as a starting point):

[https://bugs.launchpad.net/getdeb.net/+bug/173623](https://bugs.launchpad.net/getdeb.net/+bug/173623)

---

### Post by dbera on 2007-12-27
BTW, beagle-0.3.1 is now available in debian-unstable. There might be ways to convert a debian deb to a  ubuntu deb or maybe even install the debian deb packages directly in ubuntu.

---

### Post by dbera on 2008-01-09
I just spotted beagle-0.3.2 in hardy.

---

### Post by Fleece Flamingo on 2008-01-09
Has anyone compiled it yet? And is it stable?

---

