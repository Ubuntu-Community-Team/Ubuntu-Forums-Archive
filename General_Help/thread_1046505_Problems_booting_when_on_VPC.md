---
title: "Problems booting when on VPC"
date: 2009-01-21
forum: General Help
---

### Post by czech_d3v3l0p3r on 2009-01-21
Hello, kind people.

Today I downloaded Microsoft Virtual PC 2007 with SP1, set it up and configured. Then I created a new virtual machine and mounted the Ubuntu 8.10 ISO I got from the download section.

It looks ok until I try to boot it. There just loads the main screen you got when you boot from CD. Then I press for example "Try Ubuntu without any change to your computer".

Then there's some bunch of something and at the end "[    0.856031] ---[ end trace 4eaa2a86a8e2da22 ]---" and then nothing else happens.

Any help appreciated.

Thanks in advance.

---

### Post by czech_d3v3l0p3r on 2009-01-22
Bump.

---

### Post by gTumba on 2009-06-18
Same problem... exact same error. I'm using the ubuntu-9.04-alternate-i386.iso. Any ideas on how to remedy this?

---

### Post by gTumba on 2009-06-18
Ah, figured it out. Remove the option "quiet splash --" and replace it with "vga=791 noreplace-paravirt" instead.

---

