---
title: "quiet apt-get"
date: 2005-08-06
forum: Desktop Environments
---

### Post by Razvan on 2005-08-06
hi folks,

i want to use apt-get in a script without lots of talking from apt-get. In fact, i want it to be completely quiet.

I tried to run it with -qq wich is supposed to make it quiet but it didnt help much.

 i was able to throw the output from apt-get to /dev/null with 

apt-get -b -y -qq > /dev/null 

and so get it behave well till it wants to compile. because then it runs dpkg which simply prints to the console all the gcc stuff that i dont want to see

does anyone know a trick to make the dpkg process that apt-get starts silen too?

thanks in advance, Martin

---

### Post by fabiand on 2005-08-08
[QUOTE=Razvan]hi folks,

i want to use apt-get in a script without lots of talking from apt-get. In fact, i want it to be completely quiet.

I tried to run it with -qq wich is supposed to make it quiet but it didnt help much.

 i was able to throw the output from apt-get to /dev/null with 

apt-get -b -y -qq > /dev/null 

and so get it behave well till it wants to compile. because then it runs dpkg which simply prints to the console all the gcc stuff that i dont want to see

does anyone know a trick to make the dpkg process that apt-get starts silen too?

thanks in advance, Martin[/QUOTE]
 hey,

mybe you need to redirect errors too!?
here you go:
apt-get -b -y -qq > /dev/null 2>&1

---

### Post by Razvan on 2005-09-01
yay! thanks!

---

