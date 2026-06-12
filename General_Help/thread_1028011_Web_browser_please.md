---
title: "Web browser please"
date: 2009-01-02
forum: General Help
---

### Post by JDV28 on 2009-01-02
Can somebody find me a guide to install anyw eb browser besides firefox. i hate firefox. and i have tried every browser known to google and i cant get any of them to work. please help

---

### Post by Slug71 on 2009-01-02
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by JDV28 on 2009-01-02
ok and what does "deb [http://archive.canonical.com/](http://archive.canonical.com/) intrepid partner" mean? how do i do that?

---

### Post by kgas on 2009-01-02
You can install opra browser thro' synaptic package manger. (System->Administartion->synaptic package manager)

when some one gives a guidance to use a deb http://<url> thing, you should add this to your software sources and then do an update. (add the link to your software sources . then 
sudo apt-get update; sudo apt-get intstall <package name> 

hope this is clear to you

---

### Post by TransitMan on 2009-01-02
You can also go to [http://www.opera.com/download/](http://www.opera.com/download/) and download the version for your OS.
Once you have it downloaded, double-click it, and gDEBi starts to install it. You will be prompted for your password for the installation.
When it is done, Opera will be available to you through the Applications > Internet menu.

This is fast easy and painless, and doesn't require you to mess with the sources.list

---

### Post by JDV28 on 2009-01-02
how do i add a link to my software sources?

---

### Post by TransitMan on 2009-01-02
> **JDV28 said:**
> how do i add a link to my software sources?

From terminal enter the following;
```
sudo gedit /etc/apt/sources.list
Enter you password.
```

When it opens. put the following at the bottom of your list, 
```
deb http://deb.opera.com/opera/ stable non-free
```

Save the file and then
```
sudo apt-get update
sudo apt-get install opera
```

Hope this helps.

---

