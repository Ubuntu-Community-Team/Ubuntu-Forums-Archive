---
title: "need help -- quanta editor -- lost toolbars"
date: 2006-10-02
forum: Desktop Environments
---

### Post by emretemp on 2006-10-02
hi,

I'm using QUANTA editor for coding. Today , somehow I lost my toolbars,
there are how can i make toolbars appear again?

at this point, program becomes totally unusable. I cannot see highlight tab, encoding tab, and the other important menus. 

Pls help !

I really need this to be solved. 

here is the picture,
[IMG]http://i9.tinypic.com/29p6m47.png[/IMG]


PS: I even removed quanta from package manager, then reinstalled it, but still cant see the toolbars :(

---

### Post by emretemp on 2006-10-02
here i find smt like this, 

not a perfect solutiion but this will do the trick. 

after searchng a lot i got this
try pressing CTRL+M to toggle main toolbars. 

then use toolbar section to do any further modifications. 


anyway maybe someonelse gonna hit with this problem 
i hope, this topic will be helpful to him/her in the future.

---

### Post by dunnerz on 2006-10-27
I had this problem - rather then solve it - i brute fixed it..... 

rm -Rf ~/.kde/share/apps/quanta

(actually, i backed this up first!)

restarted quanta and all by toolbars were back

I recomened backing up this directory after you have quanta all setup the way you want it (and after any config chagnes) then if anything goes wrong, just restore this directory :)

---

