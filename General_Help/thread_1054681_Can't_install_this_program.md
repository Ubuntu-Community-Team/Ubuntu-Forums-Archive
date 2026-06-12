---
title: "Can't install this program"
date: 2009-01-29
forum: General Help
---

### Post by psyoptic on 2009-01-29
I'm trying to install WiCD as an alternative to Network Manager but I keep getting this error when I open up the .deb package on my desktop.

[IMG]http://i42.tinypic.com/2lkr9di.png[/IMG]

Even after I uninstall Network Manager from "Add/Remove Programs" I still get the same message.

Any suggestions as to what I'm doing wrong or how I can install WiCD?

---

### Post by Partyboi2 on 2009-01-30
Open a terminal and try removing the network-manager-gnome package as well.
```
sudo apt-get remove network-manager network-manager-gnome

```
Then change directory to where you have the wicd deb eg
```
cd ~/Desktop
```
then install with
```
sudo dpkg -i package.deb
```
*change package to actually package name.

---

### Post by hyper_ch on 2009-01-30
add the WICD repo - it's provided on sourceforge and then just:
```

sudo apt-get install wicd

```

---

### Post by psyoptic on 2009-01-31
> **Partyboi2 said:**
> Open a terminal and try removing the network-manager-gnome package as well.
```
sudo apt-get remove network-manager network-manager-gnome

```
Then change directory to where you have the wicd deb eg
```
cd ~/Desktop
```
then install with
```
sudo dpkg -i package.deb
```
*change package to actually package name.

That was perfect. Running Wicd without wifi issues now :)

You seem to really know your stuff. Hope I can be that knowledgeable about Ubuntu and the terminal commands one day. Got any tips for a noob?

---

### Post by Partyboi2 on 2009-01-31
> **psyoptic said:**
> That was perfect. Running Wicd without wifi issues now :)

You seem to really know your stuff. Hope I can be that knowledgeable about Ubuntu and the terminal commands one day. Got any tips for a noob?
I have my days :lolflag:
Actually the Beginners Team Education Focus group has started putting together some classes for beginners which  start very soon on irc you are welcomed to check them out.
[http://ubuntuforums.org/showthread.php?t=1048980](http://ubuntuforums.org/showthread.php?t=1048980)


You can also download a free beginners guide in pdf from [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

The more you use Ubuntu's terminal the quicker you will pick up the different terminal commands.

---

