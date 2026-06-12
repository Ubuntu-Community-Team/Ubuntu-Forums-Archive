---
title: "Add/remove programs isnt working"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Owdy on 2005-09-04
It opens that Application installer/ Add or remove programs window, but it just keep loadig. Nothing appears. If i hit advanced, that works. Why basic version wont?

---

### Post by blueturtl on 2005-09-04
Have you installed Smeg Gnome Menu Editor?

Because I know it propably required you to update some library (I think it was PyXDG to version 0.14). Version of PyXDG 0.14 is not compatible with the current distro and breaks some things. You may want to downgrade back to the version that was released on-disc with Ubuntu.

This worked for me.

---

### Post by Owdy on 2005-09-04
[QUOTE=blueturtl]Have you installed Smeg Gnome Menu Editor?
.[/QUOTE]
Yes. Tryed to remove that. Not worked.

---

### Post by blueturtl on 2005-09-04
Removing Smeg doesn't help, because the library that was updated for it's install hasn't been downgraded (this is not done automatically). Here's what I want you to do:

Open Synaptic (System -> Administration -> Synaptic Package Manager)

Search python-xdg

If the installed version is different than 0.9-1, do the following:

Click on the menu Package -> Force version

Install (downgrade) the old Ubuntu version 0.9-1 and all will be well, you may need your Ubuntu CD for this. Hope this works!

FINNISH:

Eli sama suomeksi: asensit Smeg valikkoeditorin joka vaati tämän python-xdg tiedoston päivittämistä uudempaan versioon. Uudempi versio vain ei ole yhteensopiva Ubuntun varusohjelmien kanssa, joten sinun täytyy asentaa alkuperäinen versio tästä tiedostosta (minulla tuo näyttäisi olevan versio 0.9-1).
Minulla ei ole käytössä suomenkielistä Ubuntua, joten en osaa tarkkaan neuvoa miten nuo valikot suomeksi menee. Luulisin kuitenkin Package kääntyvän Paketti ja Force version kääntyvän Pakota versio.

---

### Post by Irony on 2005-09-04
Hey that great. I installed smeg and found it worked but have heard of its problems. So I uninstalled it and downgraded the python-xdg.

Add/Remove programs now works instead of loading forever.

---

### Post by TristanMike on 2005-09-04
But see, now the problem is that now, for all eternity, you must pay close attention to you updates and make sure that when you update something else, you don't update "python-xdg", plus as an added bonus you will always have the little update button in you taskbar, :( But wait, there is a solution, it can be found here.... [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

---

### Post by Owdy on 2005-09-05
blueturtl, it worked. Thanks! Kiitos!!

---

### Post by Owdy on 2005-09-05
[QUOTE=TristanMike] But wait, there is a solution, it can be found here.... [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)[/QUOTE]Hey, that worked also. Now it works with latest python also :D

[QUOTE=TristanMike]But see, now the problem is that now, for all eternity, you must pay close attention to you updates and make sure that when you update something else, [/QUOTE]That 'wrong' version came here:

> ## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restrictedShould i remove that from sources.list to be safe? Or how i do that? To get only offical updates what wont broke my ubuntu?

---

### Post by frodon on 2005-09-05
[QUOTE=Owdy]Should i remove that from sources.list to be safe? Or how i do that? To get only offical updates what wont broke my ubuntu?[/QUOTE] Up to you .... read that to make a choice :
[https://wiki.ubuntu.com/UbuntuBackports?highlight=%28backport%29](https://wiki.ubuntu.com/UbuntuBackports?highlight=%28backport%29)
[http://www.ubuntuforums.org/showthread.php?t=45047&highlight=backport](http://www.ubuntuforums.org/showthread.php?t=45047&highlight=backport)

---

### Post by Irony on 2005-09-05
I'm still new to this but where it says;

*the patched and compiled version of gnome-app-install to solve the smeg-problem*

at [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871) what do I do with the tar.gz file.

---

### Post by JurB on 2005-09-09
[QUOTE=TristanMike]But wait, there is a solution, it can be found here.... [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)[/QUOTE]

Txn, solved my problem! \\:D/

---

### Post by a8o on 2005-09-15
> **Irony]I'm still new to this but where it says said:**
> https://bugzilla.ubuntu.com/show_bug.cgi?id=11871[/url] what do I do with the tar.gz file.

Actually, I don't know either. Could someone enlighten us please?

---

