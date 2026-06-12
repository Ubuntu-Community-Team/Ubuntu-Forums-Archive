---
title: "moving from kubuntu to xubuntu"
date: 2009-02-16
forum: Desktop Environments
---

### Post by Loetje on 2009-02-16
Hi,

After trying kubuntu for a while I finally faced the truth in seeing that my computer was too slow for kubuntu, so I installed de xfce desktop (xubuntu) on top of kubuntu and tried that for a while and i'm quite satisfied with the overall performance. Since i don't intend to use kubuntu anymore i want to remove it, and i found a how-to about it here:

[http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce")

Can anyone tell me if this will work, because when i start up my computer i still see a kubuntu logo (I just changed my settings to automatically log in to the xubuntu desktop environment). I'm afraid that i won't be able to start up my computer anymore...

Thanks

---

### Post by x33a on 2009-02-16
that method should work, but even if you don't remove kubuntu stuff, at the most it's eating a few hundred megabytes. if that doesn't mean much, you can leave it alone.

as for the kubuntu loading screen, to change it to xubuntu's
```
$sudo update-alternatives --config usplash-artwork.so
```

this will provide you with an option to select the one you want.

---

### Post by Loetje on 2009-02-16
Ok, thanks x33a!

I really need those megabytes so I will remove the packages. And thanks for the additional splash tip!

---

### Post by Loetje on 2009-02-17
one last (noob) question: I really like k3b (cd/dvd burning program). If i uninstall all kde recources will k3b still work?
I'm not so crazy about brasero, can anyone give me advice about a nic burning program for gnome/xfce?

---

### Post by northwestuntu on 2009-02-17
i use nero most the time, but you have to buy it.

---

### Post by x33a on 2009-02-17
if you want to install k3b, i think it'll download all its dependencies (if you do that from the repos). give it a try.

as for other burning software, you can give imgburn+wine a try. a real nice combo.

---

