---
title: "Enablin extra repositories"
date: 2009-02-19
forum: General Help
---

### Post by Embun_pagi on 2009-02-19
I'm installing ubuntu server 8.04 without GUI. I would like to enable extra repositories, how am I gonna do that without GUI?
thanks

---

### Post by taurus on 2009-02-19
You need to remove the **#** in front of the lines that start with deb in /etc/apt/sources.list.

```
sudo nano -Bw /etc/apt/sources.list
```
Save the changes and exit with <Ctrl>x.

---

### Post by staf0048 on 2009-02-19
Type:  sudo vim /etc/apt/sources.list

and uncomment out the repositories you want to add.  There is a little description of the packages before the deb http//etc. etc. lines.  Just take out the # symbol.

---

### Post by Embun_pagi on 2009-02-19
FYI, my PC didn't connect to the internet because ubuntu can't detect NIC. I'm trying to install build-essential unfortunately always come up with these

[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package
[/I]

build-essential_11.3ubuntu1_i386.deb located in /tmp
I find in this forum that I should enable extra repositories and I've already did that. But the problem still the same

---

### Post by staf0048 on 2009-02-20
Unfortuneately, enabling extra repositories isn't going to do any good if you're not connect to the internet, which is why you're getting "Couldn't find package."

So you'll need to get the complete pacakge from a computer that is connected to the net (does not need to be a linux box), burn to disc, then install the file on the other computer.

Go to [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) and find the package you're looking for (I'm not sure what heading build essential is under) and make sure to get all of the dependencies as well.

Hope this helps!!

---

### Post by Embun_pagi on 2009-02-20
Thanks.... a lot

---

