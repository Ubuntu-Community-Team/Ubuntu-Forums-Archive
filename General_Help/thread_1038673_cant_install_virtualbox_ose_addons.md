---
title: "cant install virtualbox ose addons"
date: 2009-01-13
forum: General Help
---

### Post by thingy87654321 on 2009-01-13
my friends compaq presario laptop cant install the additions for virtualbox ose. the vm is running windows home edition. but when i click install additions nothing happens, also shared folders are not working, does the additions have to be installed first?

---

### Post by ajcham on 2009-01-13
Which version of VirtualBox is your friend running? (I presume it is the latest version from the repos - 2.04?)

How are you trying to install the additions? Again, I would expect you are installing from the repos. Do you get any error message telling you why it won't install?

> also shared folders are not working, does the additions have to be installed first? 
Yes, shared folders is one of the features added by the additions.

---

### Post by Hooya on 2009-01-13
If you're talking about "install guest additions", that's something that requires you to do something within the guest OS.

Typically I would expect the thing to autoplay, but when you start the "install guest addtions" it mounts a CD in the guest OS.  Run the installer on that CD from within the guest OS.  After that you'll restatrt the guest and then have the seamless integration you wanted.

---

### Post by thingy87654321 on 2009-01-13
ok, thank you it worked

---

