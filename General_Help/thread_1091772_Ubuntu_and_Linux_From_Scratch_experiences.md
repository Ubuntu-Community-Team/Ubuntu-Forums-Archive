---
title: "Ubuntu and Linux From Scratch experiences"
date: 2009-03-09
forum: General Help
---

### Post by rocheteau on 2009-03-09
Hi, 

I have been planning to work my way through Linux From Scratch (LFS) to better understand the nuts and bolts of Linux etc. I was wondering if any of you out there have built LFS on a Ubuntu machine. I have a Ubuntu server install that I was thinking of using for this. I have read that some distributions have problems/incompatibilities as the host OS during the LFS process but Ubuntu was not mentioned. I would appreciate any and all feedback.
Thank-you, R.

---

### Post by Archimedes0212 on 2009-03-09
I too would be interested in learning a little more about this.  I'm interested in what people have to say.

---

### Post by bodhi.zazen on 2009-03-09
LFS will teach you a fair amount about compiling and building a base system.

It is a ton of ...

./configure && make && make install

---

### Post by rocheteau on 2009-03-10
Thanks for your comments. I have started looking into my Ubuntu server setup with a view to starting LFS. I inventoried the required packages with "dpkg -l" but am unable (or don't have the knowledge) for figuring out whether a few are present or what their versions are. Should I post specific items like this elsewhere or continue here?
The packages in question (with minimum versions) are:
bison (1.875)
gawk (3.0)
glibc (2.2.5)
I found a post elsewhere where the glibc version was found by looking in synaptic. Since I'm working on a server install I don't have this option and as far as I know dpkg is my only option? locate did not turn anything up so at this point I'm thinking of using apt-get to install the above (I have seen some posts complaining about glibc incompatibilities etc so am a little worried about that one).
Thanks in advance, R.

---

### Post by rocheteau on 2009-03-10
Found glibc version via:
/lib/libc.so.6 | head -n1 | cut -d" " -f1-7
The other items will have to be installed.

---

