---
title: "compiz problem. Please need help"
date: 2009-06-27
forum: Desktop Environments
---

### Post by kxhitiz on 2009-06-27
Hello I had installed compiz in ubuntu and tried different effects but unfortunately all my desktop turns black. So I removed compiz from terminal and now when I tried to make the simple default effect which I used to do before installing compiz but it says compiz not installed. Even when I installed compiz again it says the same thing. 
       I am confused why it says compiz not installed even though I tried to make the normal desktop setting. All the setting in desktop effect are disabled . So please if any idea need help.

---

### Post by colau on 2009-06-27
> **kxhitiz said:**
> Hello I had installed compiz in ubuntu and tried different effects but unfortunately all my desktop turns black. So I removed compiz from terminal and now when I tried to make the simple default effect which I used to do before installing compiz but it says compiz not installed. Even when I installed compiz again it says the same thing. 
       I am confused why it says compiz not installed even though I tried to make the normal desktop setting. All the setting in desktop effect are disabled . So please if any idea need help.
How did you install compiz?

---

### Post by kxhitiz on 2009-06-27
I installed it from the debian package of compiz. It was named simple cvss .

---

### Post by UbuntuNerd on 2009-06-27
did you try installing any drivers under System > administration > hardware drivers?

---

### Post by colau on 2009-06-27
> **kxhitiz said:**
> I installed it from the debian package of compiz. It was named simple cvss .
Did you also do this?
```

sudo apt-get install compizconfig-settings-manager

```
System>Preference>

---

### Post by kxhitiz on 2009-06-28
> **colau said:**
> Did you also do this?
```

sudo apt-get install compizconfig-settings-manager

```System>Preference>
No i didn't. I only installed compiz using [ sudo apt-get install simple-ccsm ]
Here i have attached the image which is seen when I go to 
change desktop background > visual effect
Can u help out guys.

---

### Post by UbuntuNerd on 2009-06-29
compiz is installed by default in Ubuntu unless you remove it all you need it was CCSM(compiz config settings manager), If you did remove compiz to reinstall it go to synaptic package manager and search for compiz also look at this [guide](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy)

---

### Post by kxhitiz on 2009-06-30
> **UbuntuNerd said:**
> did you try installing any drivers under System > administration > hardware drivers?

in my hardware drivers there is no any device. it says "no proprietary   drivers are used in this system"
now what to do guys.
I did tried to re install compiz, and it installs successfully but still in visual effect tab, all are disabled as shown in my previous post image.

---

