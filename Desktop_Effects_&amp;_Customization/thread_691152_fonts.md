---
title: "fonts"
date: 2008-02-08
forum: Desktop Effects &amp; Customization
---

### Post by tone33 on 2008-02-08
Forgive me if this is a double post as I can't seem to find my original post...

What font packages do you recommend?  I'm running Ubuntu with the highest level of desktop graphics and the default fonts are just ok.

Thanks.

---

### Post by kwambus on 2008-02-08
It depends what you like, good starting points are the Microsoft True Type
Core Fonts for the Web which are available from your package manager under "msttcorefonts" or from the command line:

sudo apt-get install msttcorefonts

Another alternative (and the ones I personally like and use) are the Red Hat Liberation true type fonts. I could not find these in the Ubuntu repositories but they are freely available at:

[https://www.redhat.com/promo/fonts/](https://www.redhat.com/promo/fonts/)

Hope this helps.

---

### Post by ebsbox on 2008-02-08
msttcorefonts only contains a small smathering of the hundred or so that come with a Windows install.

If you still have a computer with Windows:

copy all the fonts you want from C:\Windows\fonts onto a CD or flash drive.

Now, in Ubuntu, create a directory: /home/yourName/.fonts

copy all the fonts you plundered from Windows to you newly created .fonts directory.

Log-out and back-in or run the command:

fc-cache -rv

Enjoy!

---

### Post by frankos44 on 2008-02-08
$ sudo apt-get install msttcorefonts
$ wget [http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz](http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz)
$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Log out
Log back in

Its a must!

---

### Post by Therion on 2008-02-08
[Over 300 Fonts]("http://ubuntu.wordpress.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/") for Ubuntu to choose from.  Take your pick.

---

### Post by erfahren on 2008-02-08
a good list here: [Free Font Resources for Free Open Source Operating Systems](http://www.geocities.com/hartke01/)

---

### Post by tone33 on 2008-02-09
> **ebsbox said:**
> msttcorefonts only contains a small smathering of the hundred or so that come with a Windows install.

If you still have a computer with Windows:

copy all the fonts you want from C:\Windows\fonts onto a CD or flash drive.

Now, in Ubuntu, create a directory: /home/yourName/.fonts

copy all the fonts you plundered from Windows to you newly created .fonts directory.

Log-out and back-in or run the command:

fc-cache -rv

Enjoy!

This worked great with my root/main user, but when I try it with a second user the fonts don't show up - I've even restarted.  Any ideas?

---

### Post by erfahren on 2008-02-09
> **tone33 said:**
> This worked great with my root/main user, but when I try it with a second user the fonts don't show up - I've even restarted.  Any ideas?
see #2 - [http://penguinfonts.com/howto/ubuntu.php](http://penguinfonts.com/howto/ubuntu.php)

---

### Post by FrankVdb on 2008-02-09
> **frankos44 said:**
> $ sudo apt-get install msttcorefonts
$ wget [http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz](http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz)
$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Log out
Log back in

Its a must!

Do you mind explaining what fontconfig.tbz does? Is this a Centos-only file which happens to work on Ubuntu?

---

### Post by frankos44 on 2008-02-09
> **FrankVdb said:**
> Do you mind explaining what fontconfig.tbz does? Is this a Centos-only file which happens to work on Ubuntu?

Im not sure but it seems to install the corefonts into fontconfig director and makes the fonts available to all users in one easy step.

---

