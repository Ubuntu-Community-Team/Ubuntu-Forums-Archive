---
title: "help me in getting the proper drivers"
date: 2006-08-25
forum: Desktop Environments
---

### Post by vilto on 2006-08-25
ok here is my problem.......
my cpu usage is very high when the screensaver is on and so on with gnome.......i think the problem is with nvidia driver ..........i have GIGABYTE GA-K8N51GMF-9 mother board which has inbuilt graphics accelerator

here u can find more discription about my motherboard

[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1939&ProductName=GA-K8N51GMF-9](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1939&ProductName=GA-K8N51GMF-9)

[http://www.hardwarezone.com/articles/view.php?cid=1&id=1753](http://www.hardwarezone.com/articles/view.php?cid=1&id=1753)


now how do i install the proper nvidia drivers suted for me.......
one more thing i installed 32 bit version of ubuntu.....and installed the k7-smp kernel as mine is amd athlon x2 3800+.....im now using k7 kernel

the problem is same in both kernels


AND IF THERE ARE ANY OTHER DRIVERS SUTABLE FOR MY MOTHERBOARD PLZZ TELL....


PS: IM NEW TO LINUX

---

### Post by masnevets on 2006-08-26
I assume your computer is recent, so this should work:

```
sudo apt-get install nvidia-glx
nvidia-glx-config enable
```

---

### Post by vilto on 2006-08-27
thanx i will let u know once i have tried

---

