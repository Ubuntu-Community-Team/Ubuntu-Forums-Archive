---
title: "kwin-baghira"
date: 2006-08-09
forum: Desktop Environments
---

### Post by souteneur3190 on 2006-08-09
kwin-baghira: Depends: kdelibs4c2a (>= 4:3.5.2-1) but 4:3.5.2-0ubuntu18.1 is t o be installed
                Depends: konqueror (>= 4:3.5.2-1) but 4:3.5.2-0ubuntu27 is to be  installed
                Depends: kwin (>= 4:3.5.2-1) but 4:3.5.2-0ubuntu27 is to be inst alled
                Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be install ed
                Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be in stalled
                Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be inst alled
                Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be insta lled
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).

Thats the error i get when trying to install baghira, what should i do?

---

### Post by wieman01 on 2006-08-10
Are you trying to install the package that comes with Ubuntu (kwin-baghira) or do you install from source (sourceforge)?

Synaptic's "kwin-baghira" package should install without hickups... although it's lacking the nice (Mas-OS style) finder.

I had this problem before when I installed from source. If you're trying to do that as well, then I need to get back to you later... Need to check how I resolved this.

---

### Post by aysiu on 2006-08-10
Dependency problems come from conflicting repositories.

Get a fresh list: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again: ```
sudo aptitude update
sudo aptitude install kwin-baghira
```

---

