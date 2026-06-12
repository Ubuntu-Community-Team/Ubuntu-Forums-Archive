---
title: "gaim_2.0.0-1_i386.deb"
date: 2006-03-22
forum: Desktop Environments
---

### Post by ESPOiG on 2006-03-22
i downloaded the src.rpm format used alien to convert to .deb and then installed it seemed to work fine but i culdnt run it, it said sumthing like no such file/directory can sumone else try, i have hosted it :D

[gaim_2.0.0-1_i386.deb]("http://home.amnet.net.au/~collins/coregeek//downloads/deb_packages/gaim_2.0.0-1_i386.deb")

---

### Post by dermotti on 2006-03-22
Why not download if from ubuntu's repository? You really need  2.0?

---

### Post by ESPOiG on 2006-03-22
yeh why not, always good to try the beta version, and im using 1.5 who cares 2.0 is next version just wat i want, if i can get it working

---

### Post by ESPOiG on 2006-03-24
neone?

---

### Post by tymanthius on 2006-03-24
Instead of using alien, why not just compile from source?  That's what I did.

Be sure to have the build-essential package installed, then once you've untarred the source into a directory, run:

./configure

See if it complains about anything.  If it does, use apt-get or synaptic to install the missing bits.

THEN:

make

It should run fine

THEN:

checkinstall  (this way synaptic will see it too)

---

### Post by krusbjorn on 2006-03-24
I'm using the beta2 from their own repos. Works like a charm. Just add this line to /etc/apt/source.list
> deb [http://idefix.eup.uva.es/paquetes/gaim2.0/](http://idefix.eup.uva.es/paquetes/gaim2.0/) ./


---

### Post by ESPOiG on 2006-03-26
i get the error wen tryin to make .deb package that GLib is missin so i downloaded it, and now i dont know how to install it besides reading a lengthy installation guide
is there an easier way :D

thx

---

