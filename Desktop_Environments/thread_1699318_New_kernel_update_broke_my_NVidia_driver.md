---
title: "New kernel update broke my NVidia driver"
date: 2011-03-03
forum: Desktop Environments
---

### Post by genjix on 2011-03-03
When I upgraded to a new kernel, my graphics driver 'nvidia' broke. I had to boot my old kernel, uninstall the drivers, and then boot the new one and reinstall under the new kernel using KDE's 'Hardware Drivers' program.

Now flash crashes, firefox locks up, my desktop becomes corrupted occasionally..etc. 

How can I fix this?

---

### Post by bsntech on 2011-03-03
Might be worth a try -

But go to the nVidia website and download the drivers from there.  It should be a file that ends with ".run".

Save the file and make it executable (chmod +x <filename>).

Then completely close out of the GUI (Ctrl+Alt+F1) and run the file (./<filname>.run).

This is provided directly from nVidia and should compile everything needed.

Brian S.
[http;//www.bsntech.com]("http://www.bsntech.com")

---

### Post by gsgleason on 2011-03-03
If you manually install the nvidia module using the .sh script, you will have to do it again every time the kernel is updated.

Using the repo version should not.

---

### Post by genjix on 2011-03-04
> **gsgleason said:**
> If you manually install the nvidia module using the .sh script, you will have to do it again every time the kernel is updated.

Using the repo version should not.

It was/is the repo version.

I do not want to install the NVIDIA drivers from script. How can I fix this?

---

### Post by Hippytaff on 2011-03-04
If you go to System -> Administration -> Alternative(or is it suggested) Drivers. If you Nvidia driver is there install it again.
 
Edit -> I completely missed the fact you are using Kubuntu - the path to the additional drivers might be different, but the results shoud be the same

---

### Post by gmargo on 2011-03-04
No need to install by hand; the latest nvidia drivers are conveniently packaged in this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

