---
title: "gnumeric Edgy -export charts"
date: 2007-03-05
forum: Education &amp; Science
---

### Post by MacD on 2007-03-05
Not sure if this is the best place to post this?

I'm having trouble exporting a chart from gnumeric.  .jpg and .png both result in "unknow errors".  the .svg files look ok- but print as all-black pages.

I've seen some references here and there to this problem, being specific to ubuntu... but no solution.  Should I finally figure out how to compile from source the latest gnumeric?

---

### Post by raja on 2007-03-05
I have experienced somewhat similar problems. One way to get around it is to open the svg files with inkscape and then save it in another format in the desired resolution. However there are other problems also with this gnumeric including not being able to add error bars for line and bar charts. Apparently the problem is fixed in the later versions. So if anyone is trying to compile from source for edgy, I am interested too.

---

### Post by MacD on 2007-03-06
Thanks, Raja.  That is good advice.  I pulled some hair out trying to compile different versions of gnumeric.  Thats not for me.  Inkscape is a neat program and makes it all work.  I really like gnumeric, and now that I can put it's charts in other documents, I am set.

---

### Post by MacD on 2007-03-07
Not as hard as it sounds.  

Download:
goffice 0.3.7, libgsf1.14.3, and gnumeric1.7.8 from gnumeric

follow these instructions:
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

and these:
[http://ubuntuforums.org/showthread.php?t=298484&highlight=build+source](http://ubuntuforums.org/showthread.php?t=298484&highlight=build+source)

multiple attempts at the ./configure stage will result in notification of needed dependencies- all available through synaptic.  And finally-it works.

My question now for someone more knowledgeable- How stupid was it to do this on the machine that I depend on for everyday productivity?  what is the chance of totally messing up other stuff?

---

### Post by jeremie on 2007-03-27
MacD, where exactly did you get the source packages on gnumeric?
I only found the older 1-6 branch...

---

