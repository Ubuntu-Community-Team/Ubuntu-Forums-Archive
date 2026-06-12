---
title: "forgot to install"
date: 2008-12-29
forum: General Help
---

### Post by mrfsrf on 2008-12-29
Hi, first time linux user so pls dont be harsh on me :o)
I installed ubuntu on apple powerbook using CD, but forgot to instal desktop enviroment as an additional package..so i find myself in bash after bootup is complete. I read in documenatation that i can run "apt" command for instalation of additional packages, right?, do i have to mount the cd before? TIA. 
Admins. you can move this thread to Apple subforum if you feel its more ontopic there.

---

### Post by howefield on 2008-12-29
Is this the server edition that you installed ?

No you don't need the cd, after logging in just use sudo apt-get install whatever to get your desktop of choice, eg ubuntu-desktop.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by mrfsrf on 2008-12-30
Hi, yes i have server version installed. I tried this command but cant find package ubuntu-desktop.

---

### Post by howefield on 2008-12-30
Ok, try

```
sudo apt-get update
```

then
```

sudo apt-get install ubuntu-desktop
```

---

### Post by Seks on 2008-12-30
that's odd, try 

```
wget http://mirrors.kernel.org/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.124_i386.deb
```

and

```
sudo dpkg -i ubuntu-desktop_1.124_i386.deb
```

---

### Post by mrfsrf on 2008-12-30
problem solved. thanks!

---

