---
title: "starting UT2004"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by anonymous_user on 2008-02-08
If I try starting UT2004 in the terminal, it just says:

bash: ut2004: command not found

BTW I installed UT2004 to home/username/UT2004

So how can I start UT2004 and also create a launcher?

---

### Post by ericesque on 2008-02-08
you need cd to your ut2004 folder and run the command

```
./ut2004
```

or you could create a bash script for a launcher --there probably an easier way, but this works:

```
#!/bin/bash 
# 
cd /home/userNAME/ut2004
./ut2004
done 
done 
exit0

```

Just copy that to a text file, replace userNAME with your user name, make sure to set the properties to allow execution and double click when you want to play!

I just installed last night, btw.  Thanks for forcing me to figure this out!  :)

---

### Post by anonymous_user on 2008-02-09
Ok I did that and when I got the prompt I selected Run but then nothing happened.

Is something wrong with my UT2004 install?

---

### Post by Cappy on 2008-02-09
You need to first try running the script or running the program in a terminal so you can see the error output.

Linux is case sensitive so you need to be aware of that.

Try running it with
```
/home/$USER/UT2004/ut2004
```

If that works you can symbolically link it with
```
sudo ln -s /home/$USER/UT2004/ut2004 /usr/bin/ut2004
```
so that you can run it with just "ut2004"

---

### Post by anonymous_user on 2008-02-09
Looks like I needed to install libstdc++.5. Then your instructions worked fine. Thanks.

---

