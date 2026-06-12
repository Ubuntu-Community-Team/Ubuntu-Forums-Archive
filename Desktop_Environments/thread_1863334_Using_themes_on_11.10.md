---
title: "Using themes on 11.10"
date: 2011-10-17
forum: Desktop Environments
---

### Post by DevEight on 2011-10-17
Hi guys,

I've been using the "darklooks" theme which is included in gnome-themes-extras. After upgrading to 11.10 with a clean install today, I haven't been able to use this theme (in the "Appearance" menu) after installing said package. 

How do I get themes like this one working? If it's not compatible, where can I find themes which are?

Thanks a lot!

---

### Post by maravingian on 2011-10-17
It has to be GTK 3.0 themes that will only work with Ubuntu 11.10.  You can get themes downloaded from:

[http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=f3aa5d9fb5475a1393037a206b55e99d](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=f3aa5d9fb5475a1393037a206b55e99d)

I just haven`t figured out how to use Terminal to integrate it into the theme options menu so you can change it.

If anyone else knows how to, I`d appreciate some input.

Cheers

:guitar:

---

### Post by BazookaAce on 2011-10-17
Everything about Gnome Shell and theming can be found here: 

[http://maketecheasier.com/install-custom-gnome-shell-themes/2011/09/27](http://maketecheasier.com/install-custom-gnome-shell-themes/2011/09/27)

---

### Post by DevEight on 2011-10-18
Thanks for the guide!

I can however not get this to work, either.
When running "sudo apt-get install gnome-tweak-tool gnome-shell-extensions-user-theme" it says it cannot locate the package.
If I try to go on with the guide anyway it's not possible to change any options under "Shell Extensions" in the tweak utility.

Any ideas on how to get it working?

Thanks.

---

### Post by mcduck on 2011-10-18
gnome-tweak-tool is available in Ubuntu's own repositories, but the shell extensions aren't so make sure to add the PPA repository.

Also the instructions on that web site miss a rather important step, you must run "*sudo apt-get update*" after adding the repository before you can run the command to install the packages. Otherwise apt won't have any idea about the existence of the shell extension packages.

---

### Post by DevEight on 2011-10-18
> **mcduck said:**
> gnome-tweak-tool is available in Ubuntu's own repositories, but the shell extensions aren't so make sure to add the PPA repository.

Also the instructions on that web site miss a rather important step, you must run "*sudo apt-get update*" after adding the repository before you can run the command to install the packages. Otherwise apt won't have any idea about the existence of the shell extension packages.

That did the trick! :)
Thanks a lot.
I'll add a comment to the article saying this, hopefully it'll help others as well.

---

