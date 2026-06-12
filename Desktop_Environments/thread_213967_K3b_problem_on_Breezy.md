---
title: "K3b problem on Breezy"
date: 2006-07-12
forum: Desktop Environments
---

### Post by jrev on 2006-07-12
Hi all, 

I was trying to save my Documents folder with K3B in order to install Dapper on my hard disk when I hit the following problem :

At the start of the burning process I got the message :
"could not determine size of resulting image file":mrgreen: 

And after pushing the debugging button :
mkisofs:unofficial.
incorrectly encoded string (  4mois) encountered. Possibly creating an invalid Joliet extension -Aborting-

So What am i going to do now ?

Thanks for your help. This K3b was working fine before and of course, I don't use it every day ;)

---

### Post by bikeboy on 2006-07-12
You could try making the iso yourself then burn using k3b or nautilus, not as simple as k3b only but it's a workaround. Have a look at mkisofs here: [http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

---

### Post by jrev on 2006-07-17
Thanks, 

the problem was K3b is checking the files encoding before burning the CD
and I had badly encoded photos !

Very simple and K3b was not responsible for it...

---

### Post by BRB on 2006-08-03
I have the exact same problem, and am glad the original poster was able to find a solution.

Could you elaborate on the solution? I don't know what having 'badly encoded photos' means, or what needs to be done to fix the problem. Sounds like it is 'very simple', but not if you don't know where to start.

Any clarification greatly appreciated. 

Thanks,

-- B.

---

### Post by elcu on 2006-08-08
My assumption is that "incorrectly encoded string ( 4mois) encountered." means that there is a file somewhere called X4mois, where X is a bad character ... hence why it's showing up blank.  Renaming it, removing the bad character should hopefully fix the issue.

---

