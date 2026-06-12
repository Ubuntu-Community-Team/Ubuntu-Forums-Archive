---
title: "Open Office2 Crashing instantly"
date: 2005-11-03
forum: Desktop Environments
---

### Post by bengtfalke on 2005-11-03
I am trying to use Open Office 2 (core 1.9 129.0 lubuntu4 Fri Oct 7 18:39:57) on Breezy on a Sony Vaio TX1.

I lets me write one or maybe two characters before crashing hard. Does anybody else experience this?

Anybody got a clue?

It workes great on my other PC with WinXP.

regards/falke

---

### Post by Hairy_Palms on 2005-11-03
add this line to synaptic
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
and then update the openoffice2 componants.
Works well on my box but remember it is a set of test packages.
More info here:

---

### Post by bengtfalke on 2005-11-04
Thanks for the advice, mate. I have now upgraded to version (core 2.0.0-0ubuntu1) but still have the same problem.

I can use the menus and do all sorts of thing, but when I start to type Open Ofiice hangs after 1-3 characters amd I have to force termination.

Any advice?

regards/falke

---

### Post by MakubeX on 2005-11-04
How about secluding OpenOffice from other programs/processes.. let it be the only application running on your desktop.. then try testing it again..

You may also create another account/user and test it there..

---

### Post by bengtfalke on 2005-11-04
Thanks for the advices.

1. Same user no other programs running = Same result hangs after 1 character

2. Another user = OK !!! Now it suddenly works!

Hm, do you maybe have any idea why this is so? For your information, OO1 and ABIword works good.

This is so strange.....

regards/falke

---

### Post by magnusbb on 2005-11-04
Yes, that's strange, but there is clearly something wrong with your configuration. 

Just delete the hidden **openoffice.org2** directory in your home folder, and try starting OpenOffice again.

---

### Post by bengtfalke on 2005-11-04
Thanks mate! That did the trick!

This forum is unbeliveble.... now I only have one problem left.

My mouse wont work inside the DVD-programs like Xine, Kaffeine and Mplayer. Do you have any idea?

regards/falke

---

### Post by ofek on 2005-11-04
i wouldn't know because i don't have a dvd player. anyway my advice is that you should put this question as a new topic so more people might see it and help you out ;)

---

