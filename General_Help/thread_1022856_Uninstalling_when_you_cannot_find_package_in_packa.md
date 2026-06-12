---
title: "Uninstalling when you cannot find package in package manager"
date: 2008-12-27
forum: General Help
---

### Post by Jodha on 2008-12-27
Hi,

I've got an install of Xampp which I want to re-install due to lost privileges I cannot seem to find another way around.

Xampp does not appear in the "add/remove" package manager found Applications menu.

I've looked for it in the advanced Synaptic Package Manager, also missing from here.

Any advice on what I need to do please?

Many thanks! :)

---

### Post by taurus on 2008-12-27
Did you install xampp by hand or though add/remove, synaptic, apt-get, aptitude?

---

### Post by Jodha on 2008-12-27
I followed instructions from here:

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Basically, this command: sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

- I guess "by hand" is the short answer.

Later I followed the security instructions from the same thread:

sudo /opt/lampp/lampp security

I am not 100% sure, but I think from this point onwards I lost the CREATE privilege in MySQL admin... cannot create new user accounts or databases. This is a bit of a hinderence. I want to reinstall to see if it was setting the security. I've not done the security when I installed on my windows laptop, there I have full privileges...

---

### Post by taurus on 2008-12-27
Since you installed it by unpacking it in /opt, it will not appear in add/more or synaptic.  Therefore, if you want to remove it, you just have to remove the whole /opt/lampp.

---

### Post by Jodha on 2008-12-27
So, just delete the directory. Thats simple enough :)

Yep, all good.

Also, seems the hypothesis is true, I can now create databases again, and I assume (not tried yet) creation of new users will be just as possible.

Cheers Taurus :)

---

