---
title: "Help with fstab mounting cifs"
date: 2008-11-06
forum: Desktop Environments
---

### Post by sauce345 on 2008-11-06
I need help with fstab mounting some windows shares.  I previously wrote a bash script that took care of this easy but i wanted to put it in the fstab so i don't have to run the script all the time.  The problem comes with a few of the shares have spaces in the name.  In the bash script i just put quotes around the name and it worked no problem.  Now in the fstab i have something like:

//192.168.1.101/"High Def Movies" /mnt/HighDefMovies cifs iocharset=utf8,credentials=/home/sauce/Documents/Random/.smbcredentials,uid=1000 0 0

The command line returns:

[mntent]: line 17 in /etc/fstab is bad

I don't understand why it works in a bash script but not in the fstab.  It also works for changing directory's on the command line.

Any help would be great, i have been at this for a few hours.

---

### Post by dmizer on 2008-11-06
Please see the second link in my sig :)

---

### Post by sauce345 on 2008-11-06
Thanks, i actually saw your thread earlier and did not scroll down far enough to find the part about mounting with spaces.  Just for my own knowledge is the \040 the ASCII value for a space or?

Thanks again

---

### Post by dmizer on 2008-11-07
> **sauce345 said:**
> Thanks, i actually saw your thread earlier and did not scroll down far enough to find the part about mounting with spaces.  Just for my own knowledge is the \040 the ASCII value for a space or?

Thanks again

Yes it is the octal for space in ascii. More information here: [http://wls.wwco.com/ref/ascii.html](http://wls.wwco.com/ref/ascii.html)

---

