---
title: "Apt-get problem!"
date: 2006-04-16
forum: Desktop Environments
---

### Post by Dambrosio on 2006-04-16
My apt-get install always checks in E:\ (CD Drive) when is do sudo apt-get install
Is there a way I can reset this or something.
Thanks,
Dan

---

### Post by towsonu2003 on 2006-04-16
you can disable the CD "repository" (install CD):
Synaptic > Settings > Repositories > Uncheck "Ubuntu CD 5.10"

---

### Post by eriefisher on 2006-04-16
Open a terminal and type:sudo gedit /etc/apt/sources.list

Your sources.list will open up in a text editer. Find the line with the CD(on top)and comment it out(place a # in front of the line). Click on save and then close.

Run sudo apt-get update to reload.

eriefisher

---

### Post by towsonu2003 on 2006-04-16
just got your pm :)
 
check this for enabling repositories (ubuntu will need network/internet):
[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)

cli means command line (terminal) interface. open aterminal, what you see is cli.

---

