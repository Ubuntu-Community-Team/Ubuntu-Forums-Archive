---
title: "problem with dd backup - no such file or directory"
date: 2008-12-29
forum: General Help
---

### Post by gobbledigook on 2008-12-29
Hi!

i'm trying to use the dd command to create an image of my xp drive and place it on my local fileserver, the problem is i keep getting the error "no such file or directory"

i'm obviously doing something wrong! here are the commands and output:

```
dan@dan-desktop:~$ sudo dd if=/dev/sda | ssh server@192.168.1.120 /media/swap/sda.img
server@192.168.1.120's password: 
bash: /media/swap/sda.img: No such file or directory
dan@dan-desktop:~$ 
```

any help would be greatly appreciated:)

dan

---

### Post by scorp123 on 2008-12-29
> **gobbledigook said:**
> ```
dan@dan-desktop:~$ sudo dd if=/dev/sda | [COLOR="Red"]ssh server@192.168.1.120 /media/swap/sda.img[/COLOR]
server@192.168.1.120's password: 
bash: [COLOR="Red"]/media/swap/sda.img: **No such file or directory**[/COLOR]
``` Read the stuff highlighted in red again, please. You are trying to remotely execute a command with the name "/media/swap/sda.img" via SSH. The error is therefore correct.

As for what you really tried to achieve (I am fully aware of that ... been there and done that too :D ), please read here:
[http://ubuntuforums.org/showpost.php?p=4760998&postcount=5](http://ubuntuforums.org/showpost.php?p=4760998&postcount=5)

EDIT .... I overlooked the fact that you were using "dd" alone, without "tar". Hmmm, OK, maybe this link helps to correct your syntax then:
[http://karlherrick.com/dev/2008/09/12/dd-backups-over-ssh/](http://karlherrick.com/dev/2008/09/12/dd-backups-over-ssh/)

---

### Post by gobbledigook on 2008-12-30
Ahhh i see my error! 

Thanx Scorp! never used the dd command before and had great trouble finding the right syntax, thanks for pointing me in the right direction:)

dan

---

