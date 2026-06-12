---
title: "Problems moving from Kubuntu to Ubuntu"
date: 2007-03-20
forum: Desktop Environments
---

### Post by dragobr on 2007-03-20
Hello all.. im having a problem here and i hope i can find some help

i installed kubuntu in my pc and, after a few days, i decided that i prefer gnome.. so i installed it by using apt-get install ubuntu-desktop

but when i login in gnome, some strange things are happening... the windows doesnt seem to have the gtk decoration.. the "ok" and "cancel" buttons looks like the ones in kde, and the colors of highlited menu itens are blue, as in kde... in Themes configuration i have everything configured to Human..

any ideas of why this is happening?

---

### Post by Arby on 2007-03-21
I'm not sure why it happens, although I have heard of it before. If you have decided you don't want the kde stuff then the simplest solution is probably just to remove it. This page has instructions on how to do that [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by y0ssarian on 2007-03-21
Kubuntu was messing up my gtk font size(menus, buttons, panel font) and i was able to fix this by editing the ~/.gtkrc and removing the parts that dealt with font. Trying to fix another problem, I just deleted the file and nothing bad happened to my system. Take a look at the file and see if something there doesn't look right. If not, try posting it to the forums.

---

### Post by dragobr on 2007-03-25
tank you very much for you both... i deleted ~/.gtkrc and everything was normal :D

im deleting the kubuntu packages now...

---

