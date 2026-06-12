---
title: "Entrepid Heron/Hardy Ibex problem"
date: 2009-03-14
forum: Desktop Environments
---

### Post by afrodeity on 2009-03-14
I have a failed upgrade which resulted in part of my system becoming an Ibex but I still have the Hardy kernel. I cannot upgrade since the update manager now says: Upgrade from Intrepid to Hardy not supported.:confused:

technical details were posted [here]("http://ubuntuforums.org/showthread.php?p=6892152#post6892152")

My machine is seriously confused. Software sources app is not running, and a lot of stuff is not going to run in this environment.

Is there a way to force the upgrade to Intrepid to complete, or a means of getting back to a complete Hardy install without having to reformat?:(

---

### Post by afrodeity on 2009-03-14
I am currently trying this method to resolve the problem [http://www.linuxforums.org/forum/ubuntu-help/133620-stuck-between-hardy-intrepid.html](http://www.linuxforums.org/forum/ubuntu-help/133620-stuck-between-hardy-intrepid.html)

I have also received the following advice from a LoCo member:

Two things come to mind...  First, you can do the early alpha testing 
method of just reseting your repos to Intrepid.  Or, you can get an 
Intrepid alt-install and run the upgrade script on the CD.

Either way, tar up / to an external drive to revert back to partially 
broken.  As long as you don't reformat the partitions, you will not have 
any UUID problems to worry about.

---

### Post by afrodeity on 2009-03-15
Result - computer went through another upgrade process, installed files and xorg is now broken. Rebooted and the mouse and keyboard gone. I did a dpkg and there are some broken packages. Problem is the system wants to get these packages from Canonical, and there is no alternative if you are capped and on local bandwidth or using a proxy. I will have to wait until the end of the month until I get my cap back or figure out a way to purchase extra bandwidth so that the system can self-heal.

---

