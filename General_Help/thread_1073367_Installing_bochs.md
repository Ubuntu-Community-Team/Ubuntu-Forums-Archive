---
title: "Installing bochs"
date: 2009-02-18
forum: General Help
---

### Post by Fudgey05 on 2009-02-18
Hi there

I'm trying to get a new release of bochs emulater installed on Ubuntu 8.10, however, when i do "./configure" it runs for a bit and then gives this message:

checking for wxWidgets configuration script... not_found
checking for wxWidgets library version... 
checking for default gui on this platform... x11
ERROR: X windows gui was selected, but X windows libraries were not found.
erik@ubuntu:~/Desktop/bochs-2.3.7$ 

I have done some digging and found that to get the libraries installed i need to do "sudo apt-get install xserver-xorg-dev"

which then gives me the following:

erik@ubuntu:~/Desktop/bochs-2.3.7$ sudo apt-get install xserver-xorg-dev
[sudo] password for erik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-dev: Depends: libpixman-1-dev but it is not going to be installed
E: Broken packages
erik@ubuntu:~/Desktop/bochs-2.3.7$ 


Any assistance would be greatly appreciated

ERIK

---

### Post by lha on 2009-02-18
Is there a reason you don't want to install bochs from the repositories? Intrepid has a package for the latest version (2.3.7).

---

### Post by Fudgey05 on 2009-02-18
My Ubuntu is set up using the university repositories, which for some strange reason doesn't have bochs.

I have bochs 2.3.6 installed but it doesn't have the VGABIOS libraries incuded which I need.

I tried installing VGABIOS seperately, but that didn't work either

---

### Post by lha on 2009-02-18
Could you try another repository mirror in case the one you are using is not working correctly? Another option is to download the .deb(s) from [http://packages.ubuntu.com/intrepid/bochs]("http://packages.ubuntu.com/intrepid/bochs"). It's not the perfect solution, but might be the easiest one.

---

