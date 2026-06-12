---
title: "FCM archive for all issues?"
date: 2013-05-26
forum: Full Circle Magazine
---

### Post by stylintile on 2013-05-26
Hello everyone,
     I was wondering if there is an archive to download all issues of Full Circle Magazines to date.  On the issuu website I can only DL one at a time, and they are not in order.  I just learned of FCM and after reading a couple of them I would like to DL all of them as I still have a lot to learn.  Also, I think I saw something somewhere about an index of what is in each issue, but I can't find it again.

Any help would be greatly appreciated,
                                               stylintile

---

### Post by sisco311 on 2013-05-26
Hi,

You can download the issues (one by one) from [http://fullcirclemagazine.org/downloads/](http://fullcirclemagazine.org/downloads/)

At the top of the page there is a link to the special editions as well and at the bottom there is a link to a page where you can download a bunch of issues at once. It's beta and it didn't work for me.

Here is how you can download all of them with wget. wget is a CLI application so you have to run it in a terminal. 

By default, your current working directory is your home directory. So if you want to download the files somewhere else you have to change the working directory with the cd command. You can use mkdir to create a new one if you wish. For example:
```
mkdir ~/FCM
cd ~/FCM
```

Now you can use wget to download the files:
 ```
wget http://dl.fullcirclemagazine.org/issue**{0..72}**_en.pdf
```

This will download all the issues from 0 to 72.  You can change the range if you wish. For example **{10..15}** to download from issue 10 to 15 or **{1,5,10,71}** to download issue 1, 5, 10 and 71.

---

### Post by stylintile on 2013-05-26
> **sisco311 said:**
> Now you can use wget to download the files:
```
http://dl.fullcirclemagazine.org/issue**{0..72}**_en.pdf
```

This will download all the issues from 0 to 72.  You can change the range if you wish. For example **{10..15}** to download from issue 10 to 15 or **{1,5,10,71}** to download issue 1, 5, 10 and 71.

A HUGE THANK YOU!
     I used the wget with the url and they are downloading as I am typing this (already up to issue 39).  You saved me a bunch of time with that.

I'm still searching for the index I mentioned above.  I remember it said it wasn't complete, but that's okay, I can complete it as I read them.  Hopefully I can find it again, If not then I will index it and post it for any who are interested

     Thanks again.

---

### Post by fatharraxman on 2013-11-14
Hi 
just passed by and wanted to make the correct code for some people may like to paste that
> 
Now you can use wget to download the files:
```
http://dl.fullcirclemagazine.org/issue**{0..72}**_en.pdf
```


code is :
```
wget http://dl.fullcirclemagazine.org/issue**{0..72}**_en.pdf
``` 

replace 72 by 78 or the current issue or where you want to stop
Thanks

---

