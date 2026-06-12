---
title: "repartitioning without losing data."
date: 2009-04-08
forum: General Help
---

### Post by plounted on 2009-04-08
ive recently come to accept the usefulness of ubuntu and am past wanting to remove it from my hard drive, but one problem still remains. when ubuntu installed, it installed on the majority of my hard drive, so now 292 of the 300 gigs are under ubuntu formatting, the rest designated to windows which i also managed to fix. all i really need to do now is take a chunk of the empty space that ubuntu formatted and reformat it to the windows format so it can be available on the windows side of the partition. how can i go about doing this, in the most painless way, preferably. 
thanks ahead.

---

### Post by wolfen69 on 2009-04-08
you can use [gparted]("http://gparted.sourceforge.net/manual/gparted_manual.html") to resize the partitions.

insert a live cd of ubuntu, then 
```
sudo su
```
then
```
gparted
```

---

### Post by nothingspecial on 2009-04-08
One simple answer.

[SIZE="5"][COLOR="Red"]Back all your data up before messing with partitions[/COLOR][/SIZE]

---

