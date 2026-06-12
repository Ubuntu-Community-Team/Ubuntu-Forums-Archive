---
title: "sound doesn't work on my dell ubuntu laptop"
date: 2009-10-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yu_zyy on 2009-10-09
Newly bought Dell Inspiron 15n labtop with Ubuntu 8.10.

There is no sound while watching on-line media using Firefox.

Any idea?

---

### Post by caro on 2009-10-11
I had the same problem with the 15n I got last week.  I was able to get some sound by opening up terminal and running

 ```
alsamixer
```

make sure all the controls are set to "00" and then make sure you have any other sound controls opened up pretty high.  

The 15n doesn't sound as good as my old E1505 but it is much better now.

---

### Post by yu_zyy on 2009-10-11
> **caro said:**
> I had the same problem with the 15n I got last week.  I was able to get some sound by opening up terminal and running

 ```
alsamixer
```

make sure all the controls are set to "00" and then make sure you have any other sound controls opened up pretty high.  

The 15n doesn't sound as good as my old E1505 but it is much better now.
Thanks for the top. Right now the sound is working now. 

However the mic and ear phone still doesnot work. 

Any luck with your ear phone and mic?

---

### Post by caro on 2009-10-13
I don't use an ear phone or a mic so I haven't tested that.  Sorry.

I plan on upgrading to 9.10 at the end of the month -- I wonder if the regular Ubuntu image will have different/more drivers than the Dell Ubuntu image and make the speakers sound better, which in my case means having more bass and not sounding so tinny.

---

