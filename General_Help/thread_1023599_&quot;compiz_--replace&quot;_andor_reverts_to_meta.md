---
title: "&quot;compiz --replace&quot; and/or reverts to metacity"
date: 2008-12-28
forum: General Help
---

### Post by buzzbo on 2008-12-28
Even though I've been running Ubuntu since Feisty, sometimes I feel like a nOOb.:( In past releases I've had intermittent problems running compiz, along with getting the nvidia driver working.  I decided to give it another go.

I have an HP Pavilion dv9000 running Intrepid, with the nvidia-177 kernel module (Geforce 6150 Go).  It was originally crashing on "compiz --replace" and I started from scratch with the compiz configuration utility.  I seem to have success with a few basic things including Desktop Cube and Rotate cube.

When I logout or ctrl-alt-[backspace], I find that I have metacity again (ps aux |grep metacity).

Am I missing something?
Buzz

---

### Post by rudihawk on 2008-12-28
Go to System -> Pref -> Sessions 

Click add in the command box type:
```
compiz --replace 
```

Click add again, 

Cntrl - Alt - Backspace

It should be running when you login again :)

Hope this is what you were looking for?

---

### Post by buzzbo on 2008-12-28
> **rudihawk said:**
> Go to System -> Pref -> Sessions 

Click add in the command box type:
```
compiz --replace 
```Click add again, 

Cntrl - Alt - Backspace

It should be running when you login again :)

Hope this is what you were looking for?

this has worked!  ah thanks!

---

