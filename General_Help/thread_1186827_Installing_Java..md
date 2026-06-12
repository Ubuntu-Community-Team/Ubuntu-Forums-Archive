---
title: "Installing Java."
date: 2009-06-13
forum: General Help
---

### Post by Im A Ninja on 2009-06-13
Hi, i only just installed ubuntu. So i'm very new to it. I searched java for ubuntu and downloaded a file called: jre-6u14-linux-i586-rpm.bin

when i double click it, it says: the file is of an unknown type. How do i install this? Or have i downloaded the wrong file? If i downloaded the wrong file please link me to the right java download. thanks

---

### Post by ActiveFrost on 2009-06-13
Terminal :
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by synapsys on 2009-06-13
Don't install that. Go to System >> Administration >> Synaptic package manager

Type sun-java6 in quick search at top.

Highlight all except -doc

Right click and check mark for installation.

Hit apply at top.

You may want to read this.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)

---

### Post by jenkinbr on 2009-06-13
> **Im A Ninja said:**
> Hi, i only just installed ubuntu. So i'm very new to it. I searched java for ubuntu and downloaded a file called: jre-6u14-linux-i586-rpm.bin

when i double click it, it says: the file is of an unknown type. How do i install this? Or have i downloaded the wrong file? If i downloaded the wrong file please link me to the right java download. thanks

You downloaded the wrong file.

Open a termial and run the command ActiveFrost Posted

To open a terminal, go to Applications >> Accessories >> Terminal

Run the command below:

> **ActiveFrost said:**
> Terminal :
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

Enter your password when promted.`

---

### Post by synapsys on 2009-06-13
lol 

```
echo lastpost
```

---

### Post by kpkeerthi on 2009-06-13
> **Im A Ninja said:**
> Hi, i only just installed ubuntu. 

[http://www.ubuntupocketguide.com/index_main.html]("http://www.ubuntupocketguide.com/index_main.html")

[https://help.ubuntu.com]("https://help.ubuntu.com")

---

### Post by Im A Ninja on 2009-06-13
i done what synapsys said and it worked. thanks:D

---

