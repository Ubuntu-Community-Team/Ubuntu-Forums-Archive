---
title: "Update Manager - How to prevent a package from being updated"
date: 2007-01-03
forum: Desktop Environments
---

### Post by Sohail on 2007-01-03
Hi,

I compile tora from source in Ubuntu Edgy, but the update manager keeps popping it up. I have another machine but thi problem does not appear there. Can anyone advise?

Thanks.

---

### Post by pay on 2007-01-03
Did you use checkinstall? If you want you could compile it with "sudo make install" so then apt doesn't even know that it is there.

---

### Post by az on 2007-01-03
> **pay said:**
> Did you use checkinstall? If you want you could compile it with "sudo make install" so then apt doesn't even know that it is there.

That's a bad idea.  The package manager would overwrite your manually installed application if you don't know what you are doing.

A better solution is to lock packages so that they do not get upgraded.  Use synaptic and right-click on the package in question.  Tell it to not use any other verion of that package.

---

### Post by paparucino on 2007-01-03
> **azz said:**
> 
A better solution is to lock packages so that they do not get upgraded.  Use synaptic and right-click on the package in question.  Tell it to not use any other verion of that package.
I beg your pardon, but since I'm interested in "that problem", I tried your suggestion but in my synaptic  (0.57.8) there is not that option or, better, I'm not able to find it.

---

### Post by az on 2007-01-03
I'm sorry that I am not in front of an ubuntu computer at the moment...  See here:

[https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415](https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415)

---

### Post by Sohail on 2007-01-03
Thanks for the response everyone.

I have locked the package but still update manager brings it up. I had compiled it into a .deb package and then installed it by dpkg. Seems some header info changes during "debian/rules binary" that forces update manager to recognize it as an outdated package or something. But this is just a wild guess of mine without any factual support.

Any other ideas?

Regards.

---

