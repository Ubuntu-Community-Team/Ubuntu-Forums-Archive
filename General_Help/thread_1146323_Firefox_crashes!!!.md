---
title: "Firefox crashes!!!"
date: 2009-05-02
forum: General Help
---

### Post by groosam on 2009-05-02
Trying to upgrade to Firefox 3, went to a couple sites and copied some things in command line without really knowing the result.

Then I try and restart firefox and I get a 'Send Error to Mozzila' window.

Any ideas on what to do?  I tried completely uninstalling through Synaptic and reinstalled but nothings working

I think I installed a beta and changed some directories around accdidently, but I other than that I have no idea how to fix the problem

Thanks

---

### Post by codeseer on 2009-05-02
Rename ~/.mozilla and try again.

---

### Post by groosam on 2009-05-02
There were two ~/.mozilla files.  I deleted one, but unable to delete or rename the empty locked file.  When reinstalling it does not recreate a new directory.

I deleted a couple files and reinstalled firefox.  It now just doesn't even open

When I run it in terminal I get:

Gtk-Message:Failed to load module "canberra-gtk-module": /usr/lib/gtk-2./modules/libcanberra-gtk-module.so: Wrong ELF class: ELFCLASS64

---

### Post by codeseer on 2009-05-02
Yep. See here: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498)

What you can try to do is roll back the ia32-libs to a version or two older and see if that works for you.

---

### Post by groosam on 2009-05-02
how would i go about doing that?...im new to linux

---

### Post by codeseer on 2009-05-02
> **groosam said:**
> how would i go about doing that?...im new to linux

Do a 'complete remove' from Synaptic, then try one of these, starting with 2.7ubuntu5.

[https://launchpad.net/ubuntu/jaunty/amd64/ia32-libs](https://launchpad.net/ubuntu/jaunty/amd64/ia32-libs)

Edit:

System->Administration->Synaptic, click search, type 'ia32-libs', hit enter, click on 'ia32-libs' in the listings, right-click it, choose 'mark for complete removal', click apply, close Synaptic, download the .deb package from the link to your Desktop, double-click it, install, give it another try. If that doesn't work, do the same again, but with 2.7ubuntu4.

---

