---
title: "mount iso file?"
date: 2015-10-10
forum: Desktop Environments
---

### Post by macstl on 2015-10-10
Im running ubuntu 12.04 desktop LTS. When I right click on .iso file I select archive mounter and nothing happens. Isn't it suppose to open the .iso. Trying the kali386.iso.

---

### Post by yancek on 2015-10-10
Never used that method.  In your /home/user directory create a mount point such as 'kali' by typing the following while you are in that directory.  mkdir kali
Then while in that directory type:  mount -o loop /home/user/Downloads/kali386.iso /home/user/kali
You need the exact name of the kali iso in the command and the command above needs the kali iso in the Downloads directory so you will need to change the command if that is not the case.

---

### Post by macstl on 2015-10-10
I do that stuff at the cli and it says its mounted as loop. Now what? Is kali suppose to be on the screen?

---

### Post by grahammechanical on 2015-10-10
> [COLOR=#000000] Is kali suppose to be on the screen?[/COLOR]

I do not think so.

[http://askubuntu.com/questions/43469/how-can-i-graphically-mount-isos](http://askubuntu.com/questions/43469/how-can-i-graphically-mount-isos)

---

### Post by oldfred on 2015-10-10
If in Nautilus is it then not on the left side as another mounted device?

I usually use archive manager to look at contents of an ISO. 

But neither is an install or installer. You have have to boot the ISO. Either by copying to DVD, flash drive, hard drive or directly boot with grub2's loopmount.

---

### Post by macstl on 2015-10-10
Ok , it is mounting and I can see in on the left side of nautilus and open it and see whats in it. And it works graphically with the archive mounter by rt clicking .  I also had a misconception about what was suppose to happen when mounting the iso. All is solved to me Thank you both.

---

### Post by joe.koenig on 2015-10-12
Just off the top of my head: what does

```
 $ mount
```

say?  What's in /etc/fstab?

---

