---
title: "Can't use 'Misc-Fixed' fonts"
date: 2005-11-26
forum: Desktop Environments
---

### Post by z-vet on 2005-11-26
Hi all.
I reinstalled Kubuntu today and now can't use 'Misc-Fixed' fonts: it does not appears in any of font-selection dialogs, even when i know they are installed:
```
zvet@3g0:~$ xlsfonts | grep misc
-misc-fixed-bold-r-normal--0-0-100-100-c-0-iso10646-1
-misc-fixed-bold-r-normal--0-0-100-100-c-0-iso10646-1

(very long list of available fonts here...)

-misc-nil-medium-r-normal--2-20-75-75-c-10-misc-fontspecific
-misc-nil-medium-r-normal--2-20-75-75-c-10-misc-fontspecific

```
I downloaded ucs-fonts from [this page](http://www.cl.cam.ac.uk/~mgk25/ucs-fonts.html) and installed them following instructions in included README, but it still doesn't work. Any ideas?

---

### Post by thingy on 2005-11-26
Hi,

I think you need to enable the use of bitmap fonts with defoma.

Do a "sudo dpkg-reconfigure fontconfig"

Answer the questions it asks and when it asks for enable use of bitmap fonts...say yes.

This suggestion is only valid if we assume you've properly installed the fonts!

jin

---

### Post by z-vet on 2005-11-26
It works! I spent a whole day in search for solution...thanks a lot.

---

### Post by sab231 on 2007-05-17
Hi,

I'm a newbe in linux and specially in ubuntu/kubuntu, I installed kubuntu feisty today and I see that I can't use the misc-fixed fonts.
I read the post and I do "sudo dpkg-reconfigure fontconfig", you write that I should answer some question about use of bitmap fonts, but in my case no question was appears.

Any suggestion?

Thanks in advance.

---

### Post by adam.hawthorne on 2007-06-26
> **sab231 said:**
> Hi,

I'm a newbe in linux and specially in ubuntu/kubuntu, I installed kubuntu feisty today and I see that I can't use the misc-fixed fonts.
I read the post and I do "sudo dpkg-reconfigure fontconfig", you write that I should answer some question about use of bitmap fonts, but in my case no question was appears.

Any suggestion?

Thanks in advance.


I found another post that showed the changed command to be:

```
sudo dpkg-reconfigure fontconfig-config
```

This asked the questions as noted above. Hope that helps,

Adam Hawthorne

---

### Post by haizaar on 2008-05-13
More clean solution: [https://wiki.kubuntu.org/console8x16](https://wiki.kubuntu.org/console8x16)

---

