---
title: "Getting Rid Of Some Leftovers"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Hyakutaro on 2006-08-28
I wanted to "experiment" this morning with KDE... so I installed it...
30 min later I removed the whole thing, goddamn I hated it :P

Anyway I managed to remove almost everything, as far as I can see there are some things that are left, and I'd really want to get rid of them

1. When I start Ubuntu I get that fugly blue Kubuntu logo... I want the orange one back

2. The login screen has changed, it uses the KDE one, I want the default one back.

3. When I click on Quit, I don't have restart or shutdown anymore anymore, just Log Out, Switch User, Hibernate and Lock Screen.

Cheers ;)

---

### Post by daller on 2006-10-05
Is this resolved?

---

### Post by guysmiley25 on 2006-10-06
I think i remember reading somewhere that if you install KDE by going

$sudo aptitude install kubuntu-desktop

that you can remove it all again with

$sudo aptitude remove kubuntu-desktop

the problem with it is that the kubuntu-desktop package is just a meta package so removing with

$sudo apt-get remove kubuntu-desktop

dose not work.

you login thing will probably be because you have the kdm installed. try removing that and installing the gdm

$sudo apt-get install gdm
$sudo apt-get remove kdm

Not sure about the rest sorry. Also not that I have not used ubuntu but only xubuntu and kubuntu.

Hope that helps.

**Edit:** Stubled across this site. Will help.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Also has pure kubuntu and xubuntu.

---

