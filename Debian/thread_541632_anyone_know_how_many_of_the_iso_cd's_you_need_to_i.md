---
title: "anyone know how many of the iso cd's you need to intall"
date: 2007-09-03
forum: Debian
---

### Post by ry4n on 2007-09-03
????????

---

### Post by ry4n on 2007-09-03
becaues there is 21 cd's and i wounder if i need them all.... i hope someone knows

---

### Post by kerry_s on 2007-09-03
you only need 1.

this is the net installer, it can be used to install anything, a straight install will give you a gnome DE->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

this is for kde->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-kde-CD-1.iso)

this is for xfce4->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)


i use the net installer most of the time, i like to do my own build ups, so when it comes to the software part, i uncheck everything to get a base install, than i just apt-get from there. :)

forgot just hitting enter will use the text install, if you want the pretty installer type> installgui <than enter

---

### Post by ry4n on 2007-09-03
thank you

---

### Post by maybeway36 on 2007-09-03
Can you use the KDE#1 CD without the others?

---

### Post by buzzmandt on 2007-09-03
> **maybeway36 said:**
> Can you use the KDE#1 CD without the others?

yes

---

### Post by ry4n on 2007-09-03
I installed it this morning, I really like it other than i need to refresh my self on building things from source. 


it=debian

---

### Post by kerry_s on 2007-09-03
> **ry4n said:**
> I installed it this morning, I really like it other than i need to refresh my self on building things from source. 


it=debian

why do you have to build from source? debian has 20000+ packages(software) in the repo.

in a terminal> **su** < then type> **apt-get update**
then
**apt-get install synaptic**
then just open synaptic and you can see everything in the repos, you might want to turn on more repo's, but we'll save that for later.

what version did you go with?

---

### Post by ry4n on 2007-09-03
the newest one, 4.0 which i think is etch? 

i will have to look at the synaptic thing i just thought that i was going to have to build things from source. I still would like to get better at it. I have yet to get it to work with Firefox. so i don't know. 

P.S don't send me links about building things from source

---

### Post by kerry_s on 2007-09-03
> **ry4n said:**
> the newest one, 4.0 which i think is etch? 

i will have to look at the synaptic thing i just thought that i was going to have to build things from source. I still would like to get better at it. I have yet to get it to work with Firefox. so i don't know. 

P.S don't send me links about building things from source

no, i mean which desktop you chose? gnome, kde, xfce4

firefox in debian is called iceweasel. you can get it by using the terminal or synaptic>
su
apt-get install iceweasel

but it should already be installed, look under network.

---

### Post by ry4n on 2007-09-03
I picked gnome I love gnome. I don't know why but the other's never did anything for me. but i'm not hating on the kde kids i just like gnome better.

---

### Post by kerry_s on 2007-09-03
> **ry4n said:**
> I picked gnome I love gnome. I don't know why but the other's never did anything for me. but i'm not hating on the kde kids i just like gnome better.

you should have both epiphany and iceweasel to play with if you went with gnome. iceweasel is firefox so you don't need to install that. epiphany uses the same gecho engine, but is very limited in configuration. it's really tied into gnome, so in gnome it's pretty responsive, as in fast startup, but no where near as good as a setup as iceweasel/firefox. epiphany is for people who can't handle a real browser.

---

### Post by Pancetilla on 2007-09-04
You should try Epiphany before installing iceweasel/firefox, I apt-geted iceweasel, tried for a week and went back to epiphany. Try Epiphany and if you don't like it, then go for iceweasel.

---

### Post by ry4n on 2007-09-04
> **kerry_s said:**
> you should have both epiphany and iceweasel to play with if you went with gnome. iceweasel is firefox so you don't need to install that. epiphany uses the same gecho engine, but is very limited in configuration. it's really tied into gnome, so in gnome it's pretty responsive, as in fast startup, but no where near as good as a setup as iceweasel/firefox. epiphany is for people who can't handle a real browser.

I installed iceweasel the moment after i posted last and liked it very much, I do like it becaues it is.... well.... firefox, and i really enjoy using firefox. I did use epiphany for a while (before you told me about iceweasel) and it just felt like i was using plain bland web browser ( i don't know if i am conveying my self properly, but that is what i felt like).

---

### Post by kerry_s on 2007-09-04
> **ry4n said:**
> I installed iceweasel the moment after i posted last and liked it very much, I do like it becaues it is.... well.... firefox, and i really enjoy using firefox. I did use epiphany for a while (before you told me about iceweasel) and it just felt like i was using plain bland web browser ( i don't know if i am conveying my self properly, but that is what i felt like).

yeah, i tested epiphany for a month on various platforms and setups. i just absolutely hated how locked down it was, it felt like using IE in linux. given it does have a fast start time in gnome, but thats only because it is so tied in, just like IE. it feels so much like proprietary software, you got to get into the guts to change simple things. uhh, hate it. :lolflag:

---

### Post by ry4n on 2007-09-04
> **kerry_s said:**
> yeah, i tested epiphany for a month on various platforms and setups. i just absolutely hated how locked down it was, it felt like using IE in linux. given it does have a fast start time in gnome, but thats only because it is so tied in, just like IE. it feels so much like proprietary software, you got to get into the guts to change simple things. uhh, hate it. :lolflag:

when i was posting my last one that was on the tip of my (finger tips i guess). It really does feel like IE. I just didn't want to put that because i didn't want to piss anyone off. But since it was said: i must say, I agree.

---

### Post by Ptero-4 on 2007-09-21
A question. Which one of the 4 DVDs would you need to get Xfce4?

---

### Post by Pancetilla on 2007-09-21
> **Ptero-4 said:**
> A question. Which one of the 4 DVDs would you need to get Xfce4?

You'll get it in the first DVD.

---

