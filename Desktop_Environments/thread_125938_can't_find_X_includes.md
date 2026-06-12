---
title: "can't find X includes"
date: 2006-02-05
forum: Desktop Environments
---

### Post by manubreizh on 2006-02-05
hi,
sorry for asking maybee a silly question but i have this problem for a long time (since i install kubuntu in fact) and i'm rather a newbie...
when i try installing a program that is not in the repos (i know how to do it when it's in synaptic...) i have frequently this error message : 
"configure: error: Can't find X includes. Please check your installation and add the correct paths!"
i really don't know how to solve it (this occured once again 5 minutes ago, trying to install Klamav).
any help will be appreciated
sorry if it's an over-answered question, but i do some search and it doesn't match anything...

---

### Post by GeneralZod on 2006-02-05
It comes up pretty often, yes, but it's a pretty tricky one to search for :)

Do

```

sudo apt-get install libx11-dev

```

you will probably be asked for further libraries next time you run configure; you should hopefully be able to guess what they are by searching synaptic.  Nearly all of the files required for compiling end in "-dev".  Good luck, and ask again if you get stuck!

---

### Post by manubreizh on 2006-02-05
hi general zod,
i installed libx11-dev, but it doesn't solve the problem...
any other idea ?
thanx in advance

---

### Post by JAwuku on 2006-02-09
Hi there, do you have the package **kde-devel** installed? If not, then install it in adept or apt-get.

---

### Post by manubreizh on 2006-02-11
thanxa lot,
it solved this problem
i've edited the post to mark it as solved, for the ones who search answers
have a nice day

---

