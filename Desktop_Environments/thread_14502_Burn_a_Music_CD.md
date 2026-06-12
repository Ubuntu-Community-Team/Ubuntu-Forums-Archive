---
title: "Burn a Music CD"
date: 2005-02-07
forum: Desktop Environments
---

### Post by defazn on 2005-02-07
I read/searched already.

I need clear directions


How do i burn a music cd?

---

### Post by scoon on 2005-02-07
[QUOTE=defazn]I read/searched already.

I need clear directions


How do i burn a music cd?[/QUOTE]

Hey there, 

It is easy enuff.  Open up a terminal.  type man cdrecord.  read.   8) 


scoon

---

### Post by defazn on 2005-02-08
i was thinking using k3b, or some burning software.
I checked out the nautilus burn, but that didnt burn music cds.

any more thoughts anyone or any links

---

### Post by scoon on 2005-02-08
[QUOTE=defazn]i was thinking using k3b, or some burning software.
I checked out the nautilus burn, but that didnt burn music cds.

any more thoughts anyone or any links[/QUOTE]

Hey there, 

So did you try k3b ?  

scoon

---

### Post by tim1 on 2005-02-08
There are two good options:

1) graveman (it's in universe)
2) gnomebaker ([debian package here](http://people.debian.org/~goedson/debian/packages/gnomebaker/gnomebaker_0.3-1_i386.deb))

greets, tim

---

### Post by scoon on 2005-02-08
[QUOTE=tim1]There are two good options:

1) graveman (it's in universe)
2) gnomebaker ([debian package here](http://people.debian.org/~goedson/debian/packages/gnomebaker/gnomebaker_0.3-1_i386.deb))

greets, tim[/QUOTE]

Hey there, 

Or try xcdroast found in this repository: 
Package: xcdroast
Priority: extra
Section: universe/otherosfs


scoon

---

### Post by SickBoy on 2005-02-08
[QUOTE=defazn]i was thinking using k3b, or some burning software.
I checked out the nautilus burn, but that didnt burn music cds.

any more thoughts anyone or any links[/QUOTE]
 Which problem did you had with k3b?

---

### Post by Poldi on 2005-02-08
[QUOTE=tim1]There are two good options:

1) graveman (it's in universe)
2) gnomebaker ([debian package here](http://people.debian.org/~goedson/debian/packages/gnomebaker/gnomebaker_0.3-1_i386.deb))

greets, tim[/QUOTE]

is this a gnomebaker version for Warty or Hoary?

has anybody managed to use gnomebaker 3.x of Warty? I have been very consequent up until now not to pollute my environment with non-Warty versions and looking in Synaptic I see I would need to upgrade A LOT of libs to Hoary versions if I user the repository named on gnomebakers homepage.

any suggestions? wait / ignore / retry?

kind regards,
Carsten

---

### Post by goedson on 2005-02-08
[QUOTE=Poldi]is this a gnomebaker version for Warty or Hoary?

has anybody managed to use gnomebaker 3.x of Warty? I have been very consequent up until now not to pollute my environment with non-Warty versions and looking in Synaptic I see I would need to upgrade A LOT of libs to Hoary versions if I user the repository named on gnomebakers homepage.

any suggestions? wait / ignore / retry?

kind regards,
Carsten[/QUOTE]

These packages were built for Debian Sarge so they are probably more suitable for Hoary.

You may rebuild the package from the sources available at the given repository, or you may try the warty packages available [here](http://people.debian.org/~goedson/warty/packages/gnomebaker/snapshots/) 

These are not as up-to-date as the ones available in the other repository, but they should work fine.

I'll try to make new packages for warty today and make them available [here](http://people.debian.org/~goedson/warty/packages/gnomebaker/releases)

---

### Post by Poldi on 2005-02-08
[QUOTE=goedson]These packages were built for Debian Sarge so they are probably more suitable for Hoary.

You may rebuild the package from the sources available at the given repository, or you may try the warty packages available [here](http://people.debian.org/~goedson/warty/packages/gnomebaker/snapshots/) 

These are not as up-to-date as the ones available in the other repository, but they should work fine.

I'll try to make new packages for warty today and make them available [here](http://people.debian.org/~goedson/warty/packages/gnomebaker/releases)[/QUOTE]

the 0.2 version did not work at all for me due to ATAPI dev configuration issues.

I would be very glad if you manage to build a current Warty. thank you very much.

regards,
Carsten

---

### Post by defazn on 2005-02-08
No ididnt try k3b, reason why i know that program is because i used it before in either fedora or suse i forgot...and it was easy to use. Thx for the advices gonna try it soon.

---

