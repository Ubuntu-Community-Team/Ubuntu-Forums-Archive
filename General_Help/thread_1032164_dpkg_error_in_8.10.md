---
title: "dpkg error in 8.10"
date: 2009-01-06
forum: General Help
---

### Post by lukemack on 2009-01-06
I'm getting the following error from any apt-get command:

dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Is a directory

I get the same error if I do:

sudo dpkg --configure -a

I'm un Ubuntu 8.10 desktop. I;ve also tried 'sudo apt-get upgrade' and 'sudo apt-get update' and 'sudo apt-get clean'. All return the same error.

Is there a way to reinstall the package management system without reinstalling ubuntu?

thanks,

Luke.

---

### Post by Enselic on 2009-01-06
For me that file contains a info for a great number of packages. Since it is a directory for you, what files does it contain? If it doesn't seem to contain anything important I would try to remove the directory in an attempt to force the packaging system to reconstruct the file.

---

### Post by lukemack on 2009-01-06
its empty and if i remove it I get an error to say that it doesnt exist

---

### Post by stoneage on 2009-01-06
You could try this, but it is old so I don't know if it will work out -
[http://ubuntuforums.org/showthread.php?t=191323](http://ubuntuforums.org/showthread.php?t=191323)

---

### Post by lukemack on 2009-01-07
thanks - i removed the directories 'available' and 'available-old', created a new file as root called 'available' and that sorted it.

thanks for your help!

---

