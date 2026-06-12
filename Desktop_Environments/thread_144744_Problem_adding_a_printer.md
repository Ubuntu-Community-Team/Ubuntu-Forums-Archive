---
title: "Problem adding a printer"
date: 2006-03-14
forum: Desktop Environments
---

### Post by jabster on 2006-03-14
Hi.

I am having a problem installing my Epson C86 under Kubuntu (all updates installed). It worked fine under Gentoo. It is hooked up via USB.

When I try to add the printer under KDE's add printer wizard, I am told I don't have permission to add the printer.

Here's the output from the konsole when I run sudo kontrol:
```
sudo kcontrol
Password:
ERROR: Communication problem with kcontrol, it probably crashed.
johnj@forbin:~$ kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix                                          the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
The driver database entry does not contain sufficient data to build a PPD file.
kdeprint: WARNING: PPD syntax error, PPD parse failed
```

I have been unable to figure out where to set LC_ALL. My locale IS set correctly (CST). Clock is set to local time.

Any idea what else I can check to get my printer installed?

Thanks,
john

---

### Post by benvdh on 2006-03-22
You could try the new gutenprint (formerly gimp-print) drivers, which make sure you have all locals. You can download the source from here:

[http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=143930&release_id=387201]("http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=143930&release_id=387201")

Then make sure you have some build tools available and some dev packages could also come in handy. Here's a package list:

libcupsys2-dev 
libcupsimage2-dev
libgtk1.2-dev 
libgimp2.0-dev 
libreadline5-dev 
libijs-dev 
debhelper 
zlib1g-dev 
flex 
gettext 
foomatic-db-engine 
chrpath 
dpatch
doxygen
build-essential
fakeroot

Then run the autogen.sh script in the gutenprint package. And use the build commands, make and make install.

Then retry adding the printer. I'm not sure if it works, but it could.

Regards,

Ben

ps. you could also try this the howto in this thread if compiling doesn't work: 

[http://www.ubuntuforums.org/showthread.php?t=119595&highlight=gutenprint]("http://www.ubuntuforums.org/showthread.php?t=119595&highlight=gutenprint")

---

