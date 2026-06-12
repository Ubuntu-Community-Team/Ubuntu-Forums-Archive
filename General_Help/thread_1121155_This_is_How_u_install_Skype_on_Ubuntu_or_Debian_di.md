---
title: "This is How u install Skype on Ubuntu or Debian distros..."
date: 2009-04-09
forum: General Help
---

### Post by El1iP3S01D on 2009-04-09
I finally did it and manage to install skype correctly for the 6 sixth time...And this is how i did it...

First, download gspcav1-20071224.tar.gz and the patch gspcav1-2007508_v3.patch from this website [http://forum.skype.com/index.php?showtopic=127561](http://forum.skype.com/index.php?showtopic=127561)  Before u download the files create a tmp directory like this ie: /home/yourname/tmp/SKYPE and download the files to this Directory and download skype-common and skype-static-oss_2.o.o.72  

Second, change to your SKYPE Directory like above example: And untar gspca*.gz and change to gspca directory. Then use the patch like this patch -p1 < ../gspcav1-20070508_force_using_hardware_mode_v3.patch once that is done... Then u sudo ./gspca_build and your finish building the module for your cam...

Third, sudo dpkg -i skype-common, once done...sudo dpkg -i skype-static-oss and voila!

now lets, put to the test! call ur girlfriend or mom or dad and let me know if my how was successful for u as well? 

Good luck to everyone ok! And let me know if it worked?

---

### Post by dmizer on 2009-04-13
How is this different/better than using the [Debian and Ubuntu packages](http://www.skype.com/download/skype/linux/choose/) available from skype?

---

