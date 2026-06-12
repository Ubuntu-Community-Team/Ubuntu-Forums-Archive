---
title: "Bad scaling in Unity 7.4 on UHD screen, perfect in Unity 7.5"
date: 2018-01-24
forum: Desktop Environments
---

### Post by fellerts on 2018-01-24
I recently got a Dell XPS 9560 with the UDH (3840x2160) screen and I have been rocking Ubuntu 17.04 with Unity 7.5 for a while. I am completely new to Linux. The desktop scaling has been awesome, with only some third-party applications not scaling correctly. I have also become a big fan of Unity. 17.04 has reached its end of life, however, and I would like to downgrade to 16.04 as I am unable to get Gnome in 17.10 to scale correctly. Unfortunately, neither does Unity 7.4 on Ubuntu 16.04. See the two screenshots below for a comparison between Unity 7.4 and 7.5 with the same display settings (Displays > "Scale for menu and title bars" = 2):

[CENTER][ATTACH=CONFIG]278301[/ATTACH]
[B]Ubuntu 16.04 with Unity 7.4

[/B]

[ATTACH=CONFIG]278302[/ATTACH]
**Ubuntu 17.04 with Unity 7.5**[/CENTER]

This might come across as shallow, but the scaling issues on 16.04 are deal-breaking for me. Screen elements such as sliders and radio buttons seem to be stuck at 100 % scale, forcing me to squint and lean forwards in order to see anything.

Is there anything I can do? Can I install Unity 7.5 on Ubuntu 16.04? If not, can I somehow set the scale factor for some elements, such as the navigation buttons in Nautilus?

---

### Post by greg2lapa on 2018-01-24
Anybody know if the scaling work that was started for GNOME 3.26 has continued so that it will be offered in Ubuntu 18.04? Are the Ubuntu devs still working on this or has the work been abandoned?

---

### Post by mc4man on 2018-01-24
Maybe try 16.04 (16.04.3 image), after install update it fully, reboot. 
Then enable the proposed repo in Software & Updates > Developer Options  & upgrade unity packages to 7.4.5+16.04.20171201.3 
Also upgrade compiz & nux if there are packages available..
Log out in & see how it goes. If ok then keep 16.04 but disable the proposed repos.

---

### Post by fellerts on 2018-01-25
> **mc4man said:**
> Maybe try 16.04 (16.04.3 image), after install update it fully, reboot. 
Then enable the proposed repo in Software & Updates > Developer Options & upgrade unity packages to 7.4.5+16.04.20171201.3 
Also upgrade compiz & nux if there are packages available..
Log out in & see how it goes. If ok then keep 16.04 but disable the proposed repos.

Wow, this worked! Ubuntu 16.04 scales perfectly! Thank you.

For the record, this is what I did:
[LIST]
[*]Checked "Pre-released updates (xenial-proposed) in Software & Updates > Developer Options
[*]Launched Software Updater and installed everything it had to offer
[*]Rebooted
[*]Almost spilled my coffee after seeing how well everything scaled
[*]Unchecked the "Pre-released updates" option in Software & Updates
[/LIST]

This list shows what was installed:
 ```

$ cat /var/log/dpkg.log | grep "unity" | grep " install"
...
2018-01-23 23:11:05 status installed unity8-desktop-session-mir:all 1.0.12+15.10.20150609-0ubuntu1
2018-01-23 23:11:05 status installed unity8:amd64 8.12+16.04.20160401-0ubuntu1
2018-01-23 23:11:05 status installed unity8-common:all 8.12+16.04.20160401-0ubuntu1
2018-01-23 23:11:06 status installed unity8-private:amd64 8.12+16.04.20160401-0ubuntu1
2018-01-23 23:11:11 status installed unity-scope-click:amd64 0.1.1+16.04.20160330-0ubuntu1
2018-01-23 23:11:12 status installed unity-scope-mediascanner2:amd64 0.2+16.04.20160225-0ubuntu1
2018-01-23 23:11:12 status installed unity-plugin-scopes:amd64 0.5.7+16.04.20160317-0ubuntu1
2018-01-23 23:11:12 status installed libunity-scopes1.0:amd64 1.0.4+16.04.20160402.4-0ubuntu1

```

I never explicitly installed the source package you referred to.

Again, thank you!

---

### Post by mc4man on 2018-01-25
> **fellerts said:**
> 


I never explicitly installed the source package you referred to.

Again, thank you!
I would expect you got the newer version... For example it's shown here (blue) though I've a 7.5 version installed here in 16.04 that I built in april (orange)

> $ apt-cache madison unity
    [COLOR="#FF8C00"] unity | 7.5.0+17.04.20170407.1-0ubuntu1~xenial1 | [http://ppa.launchpad.net/mc3man/xerus-prop/ubuntu](http://ppa.launchpad.net/mc3man/xerus-prop/ubuntu) xenial/main amd64 Packages[/COLOR]
    [COLOR="#0000CD"] unity | 7.4.5+16.04.20171201.3 | [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-proposed/main amd64 Packages[/COLOR]
     unity | 7.4.0+16.04.20160906-0ubuntu1 | [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
     unity | 7.4.0+16.04.20160415-0ubuntu1 | [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
     unity | 7.4.0+16.04.20160415-0ubuntu1 | [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main Sources
     unity | 7.4.0+16.04.20160906-0ubuntu1 | [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Sources
    [COLOR="#FF8C00"]unity | 7.5.0+17.04.20170407.1-0ubuntu1~xenial1 | [http://ppa.launchpad.net/mc3man/xerus-prop/ubuntu](http://ppa.launchpad.net/mc3man/xerus-prop/ubuntu) xenial/main Sources[/COLOR]

---

