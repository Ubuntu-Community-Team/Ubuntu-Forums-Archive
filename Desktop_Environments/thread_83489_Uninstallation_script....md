---
title: "Uninstallation script..."
date: 2005-10-28
forum: Desktop Environments
---

### Post by escobar on 2005-10-28
I noticed that when I remove some apps, using 'aptitude purge' it does not always remove all the files it installed along with the program. I know this because whenever I install something I take a screeshot so I know everything to remove should I not want it anymore. On to my question.

Is there a way to create an uninstall script of some kind to make sure EVERYTHING that was installed is removed? I already have deborphan but that doesn't really catch anything. I know I may be asking for too much but thanks anyway.

---

### Post by Emerzen on 2005-10-28
Could it be that there are other programs that depend on the files it leaves behind?  I don't imagine that Synaptic would be any better at this than Aptitude, but it's worth a try using the "remove all" option.  It also has filters, one of which allows you to look for orphaned files...again, not sure it's going to be anymore functional than Aptitude.

---

### Post by escobar on 2005-10-29
[QUOTE=Emerzen]Could it be that there are other programs that depend on the files it leaves behind?  I don't imagine that Synaptic would be any better at this than Aptitude, but it's worth a try using the "remove all" option.  It also has filters, one of which allows you to look for orphaned files...again, not sure it's going to be anymore functional than Aptitude.[/QUOTE]

I would say no for the most part, as most of the files were installed along with the application.

For instance I just remove the package 'apt-listbugs'. Using aptitude purge, it removed only 'apt-listbugs' but other files like ruby1.8, libdpkg-ruby1.8, etc were installed along with it. So I run aptitude purge again to remove these. I guess it won't kill me to do this the long way. I just always try to work smarter, not harder.

---

### Post by Emerzen on 2005-10-29
Here's what you can do before removing things from your system to check dependencies.  For example, if you need to know what depends on ruby 1.8 you can do the following:

Open Synaptic -> Search and find ruby 1.8 -> highlight it -> click on 'Properties' -> click on the Dependencies tab (this will show you what ruby 1.8 depends on) -> select the drop-down menu that says 'dependencies' -> change it to 'dependent packages' (these are other packages that depend on ruby 1.8)

You should look through that list and make sure for each of the above packages you mentioned, that there are no packages depending on them.  If there's nothing depending on them, then you can remove the.

One other thing escobar.  I don't know if you're used to keeping your system clean from Windows; i.e., the vigilance necessary for the registry for example.  Unlike Windows, Linux's modular design doesn't get 'gunked up.'  In other words, if you need space on your hard-drive, then I guess I would try to remove these things.  However, if you're worried about system performance, orphaned packages won't be a detriment to your system.

---

