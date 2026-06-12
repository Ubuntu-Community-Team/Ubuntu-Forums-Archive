---
title: "Gnome Manager"
date: 2004-12-06
forum: Desktop Environments
---

### Post by Ste on 2004-12-06
Trying to get this all morning but to no avail.
Even tried compiling from source but still complained of broken dependences.

stephen@rfc1918:~ $ sudo apt-get install gnome-bluetooth
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-bluetooth: Depends: libbluetooth1 (>= 2.7) but it is not going to be installed
                   Depends: libgnomebt0 (>= 0.5.1) but it is not going to be installed
                   Depends: libopenobex-1.0-0 (>= 1.0.0-rel) but it is not going to be installed
  libbtctl1: Depends: libbluetooth1 (>= 2.7) but it is not going to be installed             Depends: libopenobex-1.0-0 (>= 1.0.0-rel) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
stephen@rfc1918:~ $ sudo apt-get -f install gnome-bluetooth
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-bluetooth: Depends: libbluetooth1 (>= 2.7) but it is not going to be installed
                   Depends: libgnomebt0 (>= 0.5.1) but it is not going to be installed
                   Depends: libopenobex-1.0-0 (>= 1.0.0-rel) but it is not going to be installed
  libbtctl1: Depends: libbluetooth1 (>= 2.7) but it is not going to be installed             Depends: libopenobex-1.0-0 (>= 1.0.0-rel) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
stephen@rfc1918:~ $


Thanks
Ste.

P.s. deb [http://people.no-name-yet.com/~jdub/warty](http://people.no-name-yet.com/~jdub/warty) ./ has been added to my /etc/apt/sources.list just like Jeff says.

---

### Post by Ste on 2004-12-06
Just realised my mistake.

I was adding packages after

# sudo apt-get -f install


Once again I'm loving Ubuntu.

---

