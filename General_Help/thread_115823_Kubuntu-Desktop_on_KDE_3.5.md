---
title: "Kubuntu-Desktop on KDE 3.5"
date: 2006-01-11
forum: General Help
---

### Post by wizzkid on 2006-01-11
I am currently using KDE 3.5, before this. I installed ubuntu from ground-up and install kde, kdm and kubuntu-desktop, then I finally decided to update my KDE 3.4 to KDE 3.5 and some application like KDevelop doesnt work, unless i type in terminal kdevelop3. then I check my Adept and look for Kubuntu-desktop, its not install.  when I install this, my kde 3.5 still remains? or it will be using the kde 3.4?

what will i get on kubuntu-desktop? over kde 3.5?

thank you

---

### Post by noigeaR on 2006-01-11
which repositories are in your sources.list?

---

### Post by Neo Ex on 2006-01-11
Follow [this]("http://kubuntu.org/announcements/kde-35.php"), and if you try installing kubuntu-desktop it will keep KDE 3.5, but I think that if you have KDE 3.5, you have just done it.

---

### Post by wizzkid on 2006-01-12
my kde respo is :
## Ubuntu 5.10 KDE 3.5 Repository
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

I was successfully install the kde and its running fine. But upon check adept, the kubuntu-desktop is NOT installed. My Kdevelop is not working when I check the icon, i  have to go to terminal and type kdevelope3 then it runs. I guess this has something to do with kubuntu-desktop not being installed.

What do you guys think? do I have to install the kubuntu-desktop even I a runing kde 3.5? also what makes a difference when I installed kubuntu-desktop or not? 

Need help here,, im newbie :)

---

### Post by GoldBuggie on 2006-01-12
You do not need to have kubuntu-desktop installed. It is only a meta-package cointaining references to other packages and one of the references, anode or something, is of wrong version and type so kubuntu-desktop with kde 3.5 is a no go.

For kdevelop try
```
sudo ln -s /usr/share/apps/kdevelop3 /usr/share/apps/kdevelop
```

---

