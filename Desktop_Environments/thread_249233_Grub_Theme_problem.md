---
title: "Grub Theme problem"
date: 2006-09-02
forum: Desktop Environments
---

### Post by w1z4rd on 2006-09-02
Dont know what I am doing wrong, but I am about to pull my hair out. None of the grub spash images I try (outside of the default few) work.

First I download : [http://www.gnome-look.org/content/show.php?content=35754](http://www.gnome-look.org/content/show.php?content=35754) , and copy the gz file to /boot/grub/splashimages/

I then nano my menu.1st file in /boot/grub/menu.1st, and do the following:

```
# Splashimage line added by kubuntu-grub-splashimages package
##splashimage=(hd1,0)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz
splashimage=(hd1,0)/boot/grub/splashimages/jose.xpm.gz
```

I get an error, its unable to load/find it.

So I try another one I downloaded off the website. It also doesnt work. Same error.

I change it back to the default one, and the default one works fine. So I try one of the other default ones, and it also works fine.

Where do you think I am going wrong?

I have 2x SATA drives.

Drive A has windows
Drive B has linux

Just incase that has some relevant, and I dual boot off the two.

---

