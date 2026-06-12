---
title: "Konqueror doesn't run Java applets"
date: 2007-11-19
forum: Desktop Environments
---

### Post by clintr on 2007-11-19
Hello,

I've installed Kubuntu 7.10 from the "alternate" CD, on an old computer.  In Konqueror, I was pleased to see that the Flash plugin was simple to install and works fine, and pdf files seem to work with no need to install a plugin.  However, it doesn't run java applets in web pages.  For example, see the attached "applets_no_workie.png".

I've attached "java_settings_1.png" and "java_settings_2.png" to show Konqueror's java settings.  Also, I tried typing "java" at the command line to see if the command "java" actually runs some sort of java - please see attached "java_is_there.png".  (Is gij Kubuntu's version of java?)

Can anyone help me to get Konqueror to run java applets?

Thanks,
Clint.

---

### Post by hollaburoo on 2007-11-19
Not sure about the specifics of your system but theres a [howto here]("http://www.konqueror.org/javahowto/") on enabling java.

The most important thing they mention is enabling the java console to see if java starts.
I don't know if this can be done with GIJ (Gnu's version of Java) so try using Sun's java if you still can't get it to work.

You can do that by enabling the multiverse repostory and then doing ```
sudo apt-get install sun-java6-plugin 
```

---

### Post by clintr on 2007-11-20
Hello hollaburoo, thanks,
I don't know how to enable the java console (not sure what that is) but I tried installing Sun java and that worked!
Wondering, should I be reporting this as a bug to someone?
Thanks for your help!
Clint

---

