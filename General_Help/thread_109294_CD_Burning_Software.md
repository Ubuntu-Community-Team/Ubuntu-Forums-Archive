---
title: "CD Burning Software"
date: 2005-12-28
forum: General Help
---

### Post by dwessell on 2005-12-28
Hi all..

I burn a LOT of CD's...

And I'm looking for a really good piece of software for it.. :-)

Really, I burn multiple copies of different files.. So I might burn 3 copies of one file, the 4 copies of another, etc. etc..

Does anyone know of a piece of software, that would let me at the beginning of a burning run, specify that I want to burn x copies of this file, then x copies of another etc... Without having to select which file between burnings.. Ie, do it all at the beginning, then serial burn from there on out.

Thanks
David

---

### Post by anil_robo on 2005-12-28
Nerolinux

---

### Post by VR6Pete on 2005-12-28
[QUOTE=anil_robo]Nerolinux[/QUOTE]

Second that!

---

### Post by psusi on 2005-12-28
Search through synaptic, there are plenty of gui front ends to burning, as well as the command line cdrecord.  In the past I have used xcdroast, and a number of people talk about k3b.  

As for Nero, I never liked it.  In windows it allways installed some retarded driver that caused all kinds of odd problems ( WTF does it need a damn driver for anyhow?! ).  There are plenty of free alternatives so I'd say save your money.

---

### Post by dwessell on 2005-12-28
Hey all.. Thanks for the responses..

Has anyone run across a program that would let me, specify to burn 4 CD's with file x on it, then 10 CD's with file y... Without having to reload files in between?


Am I even explaining that properly? It's early, and I'm searching for words :-)

---

### Post by d11wtq on 2005-12-28
[QUOTE=anil_robo]Nerolinux[/QUOTE]

Can I get this with apt-get ?  I'm not having much look finding things with apt-get :(  Does the repository have even close to the amount of things Gentoo's portage has?

Things I've search for and failed (using `apt-cache search foo') are:

thunderbird
amarok (Hmm... OK that's KDE based)
k3b (Same again)
mplayer
nerolinux

:(

---

### Post by d11wtq on 2005-12-28
[QUOTE=dwessell]Hey all.. Thanks for the responses..

Has anyone run across a program that would let me, specify to burn 4 CD's with file x on it, then 10 CD's with file y... Without having to reload files in between?


Am I even explaining that properly? It's early, and I'm searching for words :-)[/QUOTE]

I don't think K3B can do that... you'd need to do it on command line with bash and cdrecord I guess :)

---

### Post by anil_robo on 2005-12-29
[quote=d11wtq]Can I get this with apt-get?[/quote]
No. It's a proprietary software copyrighted by Nero, and you can download it from this page: [http://www.nero.com/en/NeroLINUX.html]("http://www.nero.com/en/NeroLINUX.html")

> I'm not having much look finding things with apt-get :(  Does the repository have even close to the amount of things Gentoo's portage has?
Things I've search for and failed (using `apt-cache search foo') are:

thunderbird
amarok (Hmm... OK that's KDE based)
k3b (Same again)
mplayer
nerolinux

:( 
I assume you're using GNOME. I'd suggest you use synaptic to search for the packages. It's much more convenient than apt-get. To run synaptic, type **gksudo synaptic** in a terminal and press enter. To run synaptic from menu, go to Applications--> Add applications.
Synaptic has a search button - use that! You'll find more than what you want!

And remember, the  repositories are growing constantly! Especially through the backports!

---

