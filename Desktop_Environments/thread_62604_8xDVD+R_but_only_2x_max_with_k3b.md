---
title: "8xDVD+R but only 2x max with k3b"
date: 2005-09-05
forum: Desktop Environments
---

### Post by ctdarksilver on 2005-09-05
As the title suggests, I am using kubuntu linux, burning DVD with k3b.

My hardware configuration is:
AMD Athlon64 2800+
512M DDR400
LG DVD burner with 8xDVD-R 8xDVD+R 4xDVD-RW

However, I get only maximum 2x speed when burning a 8xDVD+R disk (imation) and using up all CPU and memory.

I used to use 4xDVD-R and can achieve 4x speed, but when I use 4xDVD+R and 8xDVD+R, I get 2x maximum speed. However I am not sure whether it is because of the difference between DVD-R and DVD+R, as I did not burn much DVDs. The situation is that I found this problem recently when I am using DVD+R, and did not do any test and comparison between -R and +R after I found this problem.

I found these statements in k3b setting:
"DVD+R behaves like a multisession CD"
"k3b needs to burn multisession DVD+R on-the-fly"

what is the difference if I burn my DVD with multisession or not?
I tried both multisession and no multisession but get the same speed 2x

Can anyone help me solve this problem, thanx.

---

### Post by Steve1961 on 2005-09-05
Have you enabled dma as per instructions in the guide:

[http://amd64.ubuntuguide.org/#speedupcddvdrom](http://amd64.ubuntuguide.org/#speedupcddvdrom)

I presume you can do this with kubuntu

---

