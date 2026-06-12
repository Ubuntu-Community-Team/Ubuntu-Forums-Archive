---
title: "Unity3D top panel + left launcher COMPLETELY transparent"
date: 2012-09-24
forum: Desktop Environments
---

### Post by kovo1533 on 2012-09-24
Hello, I have problems setting top panel and launcher backgrounds ABSOLUTELLY transparent after two days googling and trying it seems that it is impossible. 

At first I tried using unity plugin in compizconfig manager. At low values like 0.01 it is still far away from transparent as you can see in first screenshot. Also tools like ubuntu tweak ao MyUnity did not help.

[IMG]http://kovo.webovka.eu/linux/ubuntuforum_transparency/1.png[/IMG]

Setting transparency to value zero makes panel completely transparent but causes another bug where previous "global app menu" stays at panel, see the second screenshot

[IMG]http://kovo.webovka.eu/linux/ubuntuforum_transparency/2.png[/IMG]

I saw some workaround to disable PNG and JPEG plugin in compiz but does not work

And also setting left panel ("unity launcher ??") will be useful, I had a Debian 6.0.5 before + DockbarX and it looked so nice, but there were some dependencies that was not installable, system is really stable comparing to ubuntu it is like windows verzus ubuntu, but was little bit outdated and applications i need to run cant run there.

P.S. I dont want to reinstall to gnome, for netbook where I need to run this I think it is the best choice and most user-frienly

---

### Post by kovo1533 on 2012-09-24
OH I forgot say, my ubuntu version is 12.04.1 LTS

---

### Post by zombifier25 on 2012-09-24
[The bug is somewhat fixed in Unity 6.0, which is in Ubuntu 12.10 beta.](https://bugs.launchpad.net/unity/+bug/924592) Hopefully, Unity 6 will be backported to 12.04. For now, go with 0.01 for transparency (it still looks pretty good IMO)

("somewhat" because according to the comments, the issue came back in the next testing version. They should be able to refix it soon)

---

