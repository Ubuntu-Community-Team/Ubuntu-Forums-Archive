---
title: "What is the Directory for GAP Packages?"
date: 2009-07-13
forum: Desktop Environments
---

### Post by jrolland on 2009-07-13
OK, I've pulled my hair out for about long enough on this one; time to post.

GAP is a computer program for working with mathematical objects called "groups" (a discussion of what a group is is far beyond the scope of this posting). The name GAP stands for "Groups, Algorithms, and Programming".

GAP 4 is included in the Ubuntu repository; for this, I am grateful.

However, I am attempting to install packages for GAP, and they are failing to load. I am installing the packages in /use/share.

Could someone pretty-please tell me what is the correct directory in which to install GAP packages for Intrepid? I would be eternally grateful if someone would point me in the right direction on this one. Installing the GAP packages is step 0 out of approximately infinitely many steps in what I need to do with GAP for my thesis.

Thanks in advance for any assistance you can provide.

---

### Post by rafita on 2009-07-13
If I understood correctly your question...

For me, it works if I indicate the location of the folder with the -l option.
I have GAP packages in /home/rafael/gaplocal/, and then the last line of the GAP executable 
is 

exec "$GAP_DIR/bin/$GAP_PRG" -m $GAP_MEM -l "$GAP_DIR;/home/rafael/gaplocal/" $*

Hope it helps

---

### Post by jrolland on 2009-07-14
Thanks for replying!

Actually, it turns out /usr/share/gap/pkg/ *is* the "correct", default directory for GAP packages. (One *can* install in other directories, as you have done, but this requires telling GAP where the packages are located.)

It turns out that some of the packages have (at times, circular) dependencies on other packages; once I installed all the "depending" packages, the package in which I was interested loaded.

Now, I can't get the package "nq" to compile, but that's a posting to another forum. (It would sure be nice if someone made Ubuntu .debs to install these packages, but I know that's wishing for the stars)

Thanks again for replying.

---

