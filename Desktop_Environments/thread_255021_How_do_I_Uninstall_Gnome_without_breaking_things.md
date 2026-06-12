---
title: "How do I Uninstall Gnome without breaking things"
date: 2006-09-10
forum: Desktop Environments
---

### Post by carlos1969 on 2006-09-10
Hi all, I am pretty much a noob. I have been using Ubuntu/Kubuntu for about six months or so. I really like it

I originally installed ubuntu. Wanted to try the KDE desktop so I used synaptic to install. Found that I liked it and preferred it to Gnome. 

Since I do not use Gnome anymore, how do I uninstall it without breaking things? 

thanks in advance.

---

### Post by meng on 2006-09-10
[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

---

### Post by carlos1969 on 2006-09-10
thanks 

I tried that but it then asks me that it is going to remove a bunch of things and asks me yes or no. I type y for yes
and then it tells me abort

---

### Post by meng on 2006-09-10
I would make sure that you aren't including any carriage return/new line/enter characters within that command (I assume you copied and pasted it), because that would cause apt-get to abort.

---

### Post by carlos1969 on 2006-09-12
ok, I tried all this and guess what???

 I deinstalled not only gnome but KDE!!!  ](*,) =D> 

So as I noticed that it was uninstalling things that I wanted, I did not want things to break thouroughly so I did a quick search and found a command

apt-get install kde kubuntu-desktop

so as soon as everything was uninstalled. I typed that command AND....

it installed things but I still did not see KDE come up

so as a crap shoot I did apt-get install kde to see what happened and it worked.

for the most part my system is ok but I do notice every time I restart it 

it asks me to restore I crashed session I dont know why everything is fine but besides that things look ok.

---

### Post by carlos1969 on 2006-09-12
by the way I did not stop the uninstall cause I was afraid that I would not be able to restart it without completely reinstalling ubuntu

so I figured I could re install a desktop without losing documents


I guessed right:grin:

---

