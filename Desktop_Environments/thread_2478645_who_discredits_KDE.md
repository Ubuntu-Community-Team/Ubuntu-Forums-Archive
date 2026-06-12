---
title: "who discredits KDE?"
date: 2022-08-31
forum: Desktop Environments
---

### Post by darkshvein2 on 2022-08-31
Hello.
This is beaty DE, more than gnome3.
but.
now in ubuntu 22.04 broken search in launcher menu,
broken images preview in Dolphin, "open files" dialog window.
Well, I search in google
TL;DR 
all those bugs long time ago already fixed!
... ofc, fixed in mainstream kde.
ubuntu packages have no fresh updates.

who compromising KDE? whyyyy

sudo apt install plasma-desktop
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
plasma-desktop is already the newest version (4:5.23.3-0ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


&#128560;&#128560;&#128560;

---

### Post by Frogs Hair on 2022-08-31
Not seeing any of these problems on a Kubuntu 22.04 installation. Are you using Kubuntu or have you installed a second desktop on gnome ? If you want the latest or cutting edge KDE packages you might want to consider [KDE Neon]("https://neon.kde.org/download"). I don't understand the question in the thread title

---

### Post by darkshvein2 on 2022-09-01
> **Frogs Hair said:**
> Not seeing any of these problems on a Kubuntu 22.04 installation. Are you using Kubuntu or have you installed a second desktop on gnome ? 
I use ubuntu, not a kubuntu. with kde DE.
Kubuntu have another repos sources for kde, than ubuntu?

---

### Post by Frogs Hair on 2022-09-01
Mixing desktop environments can be problematic on some systems , you may be better off with a Kubuntu installation. 22.04 is a long term support release and includes stable tested packages. If you want the latest KDE packages I would suggest a different Linux distribution.

---

### Post by mikewhatever on 2022-09-01
Looks like it is your fault. How exactly did you get plasma-desktop 5.23.3-0ubuntu1 in 22.04, when the default is 5.24?
Kubuntu 22.04 has worked very well for me too, so do try it.

---

### Post by darkshvein2 on 2022-09-02
> **mikewhatever said:**
>   in 20.04 

wat?

---

### Post by ActionParsnip on 2022-09-02
What is the output of
```

apt-cache policy plasma-desktop

```
Thanks

---

### Post by darkshvein2 on 2022-09-02
> **ActionParsnip said:**
>  ```

apt-cache policy plasma-desktop

```
Thanks

apt-cache policy plasma-desktop
plasma-desktop:
  &#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;: 4:5.23.3-0ubuntu1
  &#1050;&#1072;&#1085;&#1076;&#1080;&#1076;&#1072;&#1090;:   4:5.23.3-0ubuntu1
  &#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1074;&#1077;&#1088;&#1089;&#1080;&#1081;:
 *** 4:5.23.3-0ubuntu1 500
        500 [http://mirror.muvhost.com/ubuntu](http://mirror.muvhost.com/ubuntu) jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by SeijiSensei on 2022-09-03
You're using 5.23.3. I don't know exactly what the 4: prefix means, but it's not part of the version number.

As I see it, you have three options:

Install Kubuntu and accept the software versions that come with it

Install Kubuntu, then add the kubuntu-backports PPA: [https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports](https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports). That will give you the most recent releases of KDE applications directly from the KDE developers.

or,

Install KDE Neon instead. [https://neon.kde.org/](https://neon.kde.org/)

I used Neon for a while but went back to Kubuntu 22.04 with the backports PPA added. Some little niggly diferences between Neon and Kubuntu became annoying over time.

---

### Post by mikewhatever on 2022-09-03
Right, you have 22.04, my bad, but still, the same question remains, because 22.04 has version [5.24.4-0ubuntu1]("https://packages.ubuntu.com/jammy/plasma-desktop"). 
So, how did you manage to get 5.23.3-0ubuntu1???
PS: AFAIK, version 5.23.3-0ubuntu1 isn't in any of the Ubuntu repositories.

---

