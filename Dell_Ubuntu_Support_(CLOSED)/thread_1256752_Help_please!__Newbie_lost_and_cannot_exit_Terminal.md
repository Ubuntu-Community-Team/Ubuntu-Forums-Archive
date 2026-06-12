---
title: "Help please!  Newbie lost and cannot exit Terminal..."
date: 2009-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Newbie804 on 2009-09-03
Hi,
I need help please!
I'm a ubuntu newbie  and I was trying to install Tor, Privoxy and Vidalia on my Dell Mini 9 Hardy.
It seems to have installed fine and indeed I try to use it and understand how it works.
Then I decided to reboot to check how could I load them automaticaly but I got a problem.  Now my netbook start in terminal asking user and password (okay I know them) but how can I load the original Dell's graphics?  I only have a terminal and I do not know but some few linux commands...  I suppose these apps changed and crashed the file that was used to "load" when I turn on Mini.  I already tryed to uninstall them with terminal commands but not sure I did it right...
So please, any help?
Thanks,
Jorge

---

### Post by sahabcse on 2009-09-03
#sudo /etc/init.d/gdm start

Follow below url for package management in command prompt

[http://ubuntulinux.co.in/package-installation-over-command-propmpt.php](http://ubuntulinux.co.in/package-installation-over-command-propmpt.php)

---

### Post by divague on 2009-09-03
Try

```
startx
```

---

### Post by Newbie804 on 2009-09-03
WOW this forum rocks!

Yes divague, startx worked fine!  It start my Dell as usual but will have to change or check any file now? :D

Thanks sahabcse, I will check those commands too. :)

---

### Post by Newbie804 on 2009-09-03
Hi,
the problem is solved.
I had to reinstall gnome.  I do not know what had happened.
Thanks, :D

---

