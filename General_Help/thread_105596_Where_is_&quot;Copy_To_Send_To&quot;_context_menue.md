---
title: "Where is &quot;Copy To /Send To&quot; context menue feature"
date: 2005-12-18
forum: General Help
---

### Post by coaxx on 2005-12-18
Hi,

on another Kubuntu mashine I saw this nice feature. Its like right-click+ "Send to..." in Windows. Does anybody know how to get this feature installed?

Thank You

---

### Post by ltmon on 2005-12-18
There's a whole lot of service menu's here: [http://kde-apps.org/index.php?xsortmode=high&page=0](http://kde-apps.org/index.php?xsortmode=high&page=0)

It may be in amongst that list.

L.

---

### Post by GoldBuggie on 2005-12-18
Which feature are we talking about? Sounds like the copy to or move to feature. Don't you have that one? I just right-click and whoops there it is. Or are we talking about some other thing?

---

### Post by coaxx on 2005-12-19
yeah thats the feature I mean! :) but I dont have it here :( I will try to have a look at ltmon's link. thx!

---

### Post by GoldBuggie on 2005-12-19
maybe it is in this package
```
sudo apt-get install konq-plugins
```
you got that one?

Do a search in synaptic/adept for "konq". You are probably missing some pacjage

---

### Post by limit223 on 2005-12-19
Go back to the default KDE profiles:

sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc

and:

rm ~/.kde/share/apps/konqueror/konq-kubuntu.rc
cp ~/.kde/share/apps/konqueror/konqueror.rc ~/.kde/share/apps/konqueror/konq-kubuntu.rc

---

### Post by coaxx on 2005-12-19
[QUOTE=GoldBuggie]maybe it is in this package
```
sudo apt-get install konq-plugins
```
[/QUOTE]
No its not ion there :(

---

### Post by coaxx on 2005-12-19
[QUOTE=limit223]Go back to the default KDE profiles:

sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc

and:

rm ~/.kde/share/apps/konqueror/konq-kubuntu.rc
cp ~/.kde/share/apps/konqueror/konqueror.rc ~/.kde/share/apps/konqueror/konq-kubuntu.rc[/QUOTE]

The first two line did the job, (3&4 gave me an error because of file not found). But anyway it did the job!

---

### Post by limit223 on 2005-12-19
Sorry..that's because probably I copied that file from the path given by line 2, some weeks ago ...I couldn't remember exactly where was from...
You may do it yourself for more features but don't forget to change the permissions' file.

---

