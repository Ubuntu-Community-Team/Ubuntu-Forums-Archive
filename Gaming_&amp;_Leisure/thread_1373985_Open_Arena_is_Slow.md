---
title: "Open Arena is Slow"
date: 2010-01-06
forum: Gaming &amp; Leisure
---

### Post by Xoanan on 2010-01-06
Hi All

I have a new pc now with Xubuntu 9.10 and a Gig of RAM. Everything runs fine except for Open Arena.  It's really slow for some reason. It used to run fine on 8.10 on a machine that only had 348 MB of ram.  

Could it be the server?

---

### Post by notyrock on 2010-01-08
Hi
Just read out entire post,well the friends working in ubuntu and just give me these solution,
Have you checked if direct rendering is enabled ? After running 'glxinfo' you should see something like this:Hope its work out.
ecimon@sigonmobile:~$ glxinfo | grep direct
direct rendering: Yes
ecimon@sigonmobile:~$.

---

### Post by Xoanan on 2010-01-08
> **notyrock said:**
> Hi
Just read out entire post,well the friends working in ubuntu and just give me these solution,
Have you checked if direct rendering is enabled ? After running 'glxinfo' you should see something like this:Hope its work out.
ecimon@sigonmobile:~$ glxinfo | grep direct
direct rendering: Yes
ecimon@sigonmobile:~$.

Not sure I understand;  I should see something like what?  
Thanx for the info btw; just need a little clarification

---

### Post by 5nak3 on 2010-01-08
I think what he means is to paste the following into terminal (applications -> Accessories -> Terminal)

```
glxinfo | grep direct
```

You should get the output reading:

direct rendering: Yes

If not that would seem to suggest that the 3D drivers are not working correctly and that could be the problem.

---

### Post by Xoanan on 2010-01-09
> **5nak3 said:**
> I think what he means is to paste the following into terminal (applications -> Accessories -> Terminal)

```
glxinfo | grep direct
```

You should get the output reading:

direct rendering: Yes

If not that would seem to suggest that the 3D drivers are not working correctly and that could be the problem.

Ah! Thanx.  I will try it when I get home.

---

### Post by Xoanan on 2010-01-09
> **Xoanan said:**
> Ah! Thanx.  I will try it when I get home.

```
xoanan@ubuntu:~/Desktop$ glxinfo | grep direct
direct rendering: Yes
xoanan@ubuntu:~/Desktop$ 

```

---

### Post by Xoanan on 2010-01-10
Open Arena is fine now. Thanx!

---

