---
title: "Does anyone know how to build ioquake from source"
date: 2009-09-11
forum: Gaming &amp; Leisure
---

### Post by metalf8801 on 2009-09-11
first you should know I have no experacne with building software from source but I would really like to learn how to do it.

Has anyone been able to build ioquake3 from source?  If so how? 

I found this site [http://ioquake3.org/](http://ioquake3.org/)   

and I found these instructions:
 
> We all can compile it ourselves:

   1. Agree to the EULA and grab the
      updated pk3 files. Extract it to some place like
      /opt/quake3.
   2. Change into the top level directory (it contains the ui and code directories.)
   3. Run make.  [COLOR="Red"]Sadly I'm already lost[/COLOR]
   4. Set $COPYDIR to the directory you installed Quake3 to and make the copyfiles target. Make sure you are changed to the owner of this path (probably root). COPYDIR="/opt/quake3" make copyfiles

if anyone can help me I would really appreciate it 
Thank you 
Dan

---

### Post by noerrorsfound on 2009-09-11
Assuming you're in a terminal and step 2 is done, running make literally means to run *make*, which is done by typing it at the terminal just like your other commands.

---

