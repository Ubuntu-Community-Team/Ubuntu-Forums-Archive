---
title: "Installing K3B?"
date: 2005-07-07
forum: Desktop Environments
---

### Post by Stag on 2005-07-07
Dear All,

Linux newbie here and struggling.

Having trouble burning DVD's and would like to try K3B instead.  Can anyone provide me some clues or sites where I can read about how to install this software.  I am from Windows worls until a week ago and not finding the transition easy.

Many thanks for any help.
Much appreciated
Stag  :???:

---

### Post by jasmuz on 2005-07-07
[QUOTE=Stag]Dear All,

Linux newbie here and struggling.

Having trouble burning DVD's and would like to try K3B instead.  Can anyone provide me some clues or sites where I can read about how to install this software.  I am from Windows worls until a week ago and not finding the transition easy.

Many thanks for any help.
Much appreciated
Stag  :???:[/QUOTE]
 Do on your console

sudo apt-get install k3b

---

### Post by tread on 2005-07-07
And if you don't want to use the console, on the top menu click:
System->Administration->Synaptic

and then search for k3b.

---

### Post by Stag on 2005-07-07
Thanks Guys,

2 things

1) would I be able to install this across a dial-up connection?  My first thought was the amount of data woud be too large.

2) my machine only seems to see the CD it cannot see the outer world through synaptic?

Stag

---

### Post by tread on 2005-07-07
Start a terminal, and then type
sudo gedit /etc/apt/sources.list

Uncomment the remaining repositories (remove the #before the addresses)
Start synaptic, reload package information, and search again.

---

### Post by Stag on 2005-07-07
Thanks, I have implemented your suggestions and the machine can now see the outside world.  Thank you. :smile:

---

