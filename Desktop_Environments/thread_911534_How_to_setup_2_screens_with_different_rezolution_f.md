---
title: "How to setup 2 screens with different rezolution for Ubuntu"
date: 2008-09-05
forum: Desktop Environments
---

### Post by sorin.stirbu on 2008-09-05
I have :
#1 - Asus VW222U on DVI [1680/1050 @ 60Hz]
#2 - Sony SDM E95 on VGA [1280/1024 @ 75Hz]

When I connect only one of them [either] it works like a charm, but when they are connected togheter they have the same rezolution : 1280/1024 @60Hz. I have installed the win driver for Asus [the Sony driver is not on the site .. ?!?!] ... but the same. 

In "Screens and Graphics" it is only the Default display checked and the other boxes below are grey and canot be checked ....

Any ideas on how to make the rezolution good on each one ? I understood that I have to modify the xorg.conf for that but I do not know how.

10x !!

---

### Post by kjohansen on 2008-09-05
you will have to set up seperate x servers.

some video cards have guis for making the changes to xorg.conf.

i have an nvidia and used nvidia-settings from the repos to do this.

---

### Post by overdrank on 2008-09-05
> **sorin.stirbu said:**
> I have :
#1 - Asus VW222U on DVI [1680/1050 @ 60Hz]
#2 - Sony SDM E95 on VGA [1280/1024 @ 75Hz]

When I connect only one of them [either] it works like a charm, but when they are connected togheter they have the same rezolution : 1280/1024 @60Hz. I have installed the win driver for Asus [the Sony driver is not on the site .. ?!?!] ... but the same. 

In "Screens and Graphics" it is only the Default display checked and the other boxes below are grey and canot be checked ....

Any ideas on how to make the rezolution good on each one ? I understood that I have to modify the xorg.conf for that but I do not know how.

10x !!

Hi and what is the model of the graphics card and you say you have installed the win driver for what?

---

### Post by sorin.stirbu on 2008-09-06
installed the win driver for the Asus monitor [it works for Ubuntu] .... and I have a 8500GT Top nVidia card [but the driver is not installed...the xserver crashes when I install it]

---

### Post by sallywon on 2008-09-06
I have same problem:(

---

