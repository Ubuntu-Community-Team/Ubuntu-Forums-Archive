---
title: "Converting Ubuntu into Kubuntu"
date: 2007-06-30
forum: Desktop Environments
---

### Post by bgenc on 2007-06-30
Hi all,

I have been a loyal ubuntu user for the last few years but everybody needs a change once in a while ;)
So I decided to convert my laptop into kubuntu without a fresh install. 

I installed kubuntu-desktop and got my kde environment working without a hassle. But now, I realized that as long as the old gnome apps are there, I won't get used to the new kde based ones. So, I decided to remove ubuntu-desktop. However, I am not sure if this is a good idea. This box was installed from a dapper cd and upgraded to feisty. What happens if I remove ubuntu-desktop from synaptic? Is it better to use aptitude? Will that remove all related gnome packages or just the dummy ubuntu-desktop package? What is the best way to proceed?

---

### Post by Richard Kut on 2007-07-01
> I installed kubuntu-desktop and got my kde environment working without a hassle. But now, I realized that as long as the old gnome apps are there, I won't get used to the new kde based ones. So, I decided to remove ubuntu-desktop. However, I am not sure if this is a good idea. This box was installed from a dapper cd and upgraded to feisty. What happens if I remove ubuntu-desktop from synaptic? 


Synaptic lists this message when you query for ubuntu-desktop"

> This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.


So it's probably not a good idea, because you might find that you still need some of the Gnome bits in the future. I would recommend that, unless you really need to reclaim the space, you keep Gnome for now. That way, if you find that KDE is not "your cup of tea", then you can always resume using Gnome. That's just my 0.02$.

---

### Post by bapoumba on 2007-07-01
[http://psychocats.net/ubuntu/purekde]("http://psychocats.net/ubuntu/purekde")
Please read this.

---

