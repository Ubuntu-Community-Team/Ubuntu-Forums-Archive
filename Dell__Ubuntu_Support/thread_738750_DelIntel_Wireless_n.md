---
title: "Del/Intel Wireless n"
date: 2008-03-28
forum: Dell  Ubuntu Support
---

### Post by bashveank on 2008-03-28
[SIZE=2]Does the "[/SIZE][FONT=arial][SIZE=2]Intel Next-Gen Wireless-N Mini-card" or the "[/SIZE][/FONT][FONT=arial][SIZE=2]Dell Wireless 1505 Wireless-N Mini-card" that Dell sells in their laptops work with Ubuntu? I've searched around and I assume that they do, but I want to be sure so that I don't end up stuck with a laptop that doesn't work properly.

edit: I don't know how to mark this as solved, but I edited [SOLVED] into the title.
[/SIZE][/FONT]

---

### Post by virtuallinux on 2008-03-29
Well, I know from personal experience that Intel wireless generally gets along well with Ubuntu, although I'm not 100% about the wireless N cards.  As for Dell, I have no idea.

---

### Post by sdennie on 2008-03-29
The Intel card should be a 4965 card and should work just fine with the iwlwifi drivers (I believe that as of Ubuntu 7.10, that driver and it's firmware is installed by default so it should work out of the box).  I don't know about the Dell branded card.  I'm sure it could be made to work but, non-Intel wifi cards can sometimes be a hassle on linux (google ndiswrapper) so, if it's an option, I would opt for the Intel card.

---

### Post by bashveank on 2008-03-29
Ok cool.
Thanks for the help.

---

### Post by akniss on 2008-03-29
I've got an Intel 4965AGN card in my m1330 and it does indeed work out of the box with Gutsy.  However, I've not tried it with an N network, so I can't speak to that directly.  The card works perfectly on WEP encrypted G networks, though.

---

