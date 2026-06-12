---
title: "From Hoary to Dapper: should I?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Steve S. on 2006-06-05
Suggestions and opinions time:

1. I'm pretty sure I'm under the Hoary distro (I was pretty new when I first installed.  Not much more experienced now, but a little;) ).  How do I check?

2. Assuming I am under Hoary distro (pretty sure) is it worth it for me to change to Dapper?  Would like to take advantage of some of the new stuff, but of course hear some complaints...

3. If I do change, are there specifics that I need to know to go from Hoary to Dapper?  I've read [http://www.psychocats.net/ubuntu/dapper.php](http://www.psychocats.net/ubuntu/dapper.php) and it seems pretty straightforward, but isn't that going from breezy to dapper?

4. If I don't change, but want to upgrade from Hoary to breezy, how do I do that now that dapper is out?

---

### Post by oyvindaa on 2006-06-05
1. In terminal:

```
cat /etc/issue
```

2. I've never tried Hoary myself, but I think Dapper is better than Breezy. Dapper's not perfect though.

4. [http://mirror.trivini.no/ubuntu-iso/5.10/](http://mirror.trivini.no/ubuntu-iso/5.10/)

I think I've read somewhere it'd be wise not to skip any distro's when you upgrade. If you just burn the .iso onto the cd, it shouldn't be a problem though.

---

### Post by Steve S. on 2006-06-05
Thanks, oyvindaa, very appreciated!

---

### Post by ed_agamemnon on 2006-06-05
Hoary was (for me at least) actually significantly better than Breezy. Now i've gone from Breezy to Dapper things're even better :)

---

### Post by mnl88 on 2006-06-05
Hoary was how I started with Ubuntu, and if I remember correctly, it worked a bit better than Breezy (what with hardware compatibility, etc).  Dapper is quite an improvement on Breezy, though.  I'd say it's certainly worth it.

---

### Post by netron on 2006-06-05
[QUOTE=Steve S.]
4. If I don't change, but want to upgrade from Hoary to breezy, how do I do that now that dapper is out?[/QUOTE]

open up /etc/apt/sources.list  and change all references of hoary to breezy

i.e. if you have a line entry like:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **hoary** universe

change it to :
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **breezy** universe
save the file 
then type (in terminal)

sudo apt-get update
sudo apt-get dist-upgrade


its generally not recommended that you skip versions during upgrades - like going from hoary straight to dapper.

As for how good Dapper is?  Well, I'm a long term Mandrake user - and i've finally converted my main box with this release. It really is **that** good.

---

### Post by Steve S. on 2006-06-05
[QUOTE=netron]
As for how good Dapper is?  Well, I'm a long term Mandrake user - and i've finally converted my main box with this release. It really is **that** good.[/QUOTE]

That's what I needed to know...thanks again, all!

---

