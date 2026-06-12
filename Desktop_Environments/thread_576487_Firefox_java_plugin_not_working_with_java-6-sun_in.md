---
title: "Firefox java plugin not working with java-6-sun in Feisty"
date: 2007-10-15
forum: Desktop Environments
---

### Post by thewoolleyman on 2007-10-15
Hello,

I just upgraded to the sun java6 jdk, and now I can't get the firefox java plugin to work.  I have both libjavaplugin_oji.so and libjavaplugin.so symlinked to /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so.  

Yes, the jdk is working fine from command line (intellij idea starts).

I have removed the standard gij java stuff (probably incorrectly and incompletely), but should this have any effect if the sun java6 version seems to be working?

Thanks,
--Chad

---------------------------
woolley@chadlin:~$ cat /etc/issue
Ubuntu 7.04 \n \l

woolley@chadlin:~$ ls -al /usr/lib/firefox/plugins/
lrwxrwxrwx 1 root root      39 2007-10-15 06:13 libjavaplugin_oji.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root      39 2007-10-15 05:13 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

woolley@chadlin:~$ ls -al /etc/alternatives/firefox-javaplugin.so 
lrwxrwxrwx 1 root root 64 2007-10-15 05:22 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by cinematography on 2007-11-03
type this to install the plugin:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

and enter this to remove the plugin that conflicts with the java plugin
```
sudo apt-get remove gcjwebplugin
```

---

### Post by thewoolleyman on 2007-11-06
Thx for the response.  I have the stuff you listed already installed/uninstalled properly.  Is there a certain file in gcjwebplugin that might be hanging around and causing problems?  I'm not sure how to see what files are included in a non-installed package - is it on the web somewhere?

---

### Post by whmitty on 2007-11-14
After significant Googling to no avail I stumbled across the following at [_http://plugindoc.mozdev.org/linux.html#Java_]("http://plugindoc.mozdev.org/linux.html#Java") which allowed me to get the JRE working with Firefox and Ubuntu Feisty. Hopefully it will help someone else who falls into this hole.

Java Runtime Environment
Version: 1.4.2 or later
SeaMonkey 1.0: Supported
Firefox 2.0: Supported
FAQ: Java FAQ

1. Install Java Runtime Environment.

2. Make a symbolic link to libjavaplugin_oji.so in your Mozilla Plugins directory. Use the copy located in the plugin/i386/ns7 directory of JRE 5.0 or later, or plugin/i386/ns610-gcc32 if you are using JRE 1.4.2.

**Important!** Do not copy the plugin to your plugins directory. If you do, Mozilla will crash any time you attempt to view a page containing a Java applet.
Note: The instructions listed here are for the Sun Java Runtime Environment. Other Java Runtime Environments, such as those available from IBM and the Blackdown project, can also be used.

---

### Post by thewoolleyman on 2007-11-19
OK, I've fixed this - sort of.  All my links in /usr/lib/firefox were OK.

I had an old /opt/firefox directory hanging around (I found this by doing 'locate' for the plugin .so file).  

When I deleted this dir, flash started working in firefox.  

Unfortunately, the standard links in my gnome menu (which is just 'firefox') don't work.  But, I can still start firefox from the command line, so I guess this is OK.  

Dunno how the old opt/firefox got there, maybe a manual installation years ago, and also not sure how this broke the menu links.  Maybe this is where ubuntu puts it, and /usr/lib/firefox is wrong? No time to research now...

-- Chad

---

### Post by thewoolleyman on 2007-11-19
update: 

dpkg -L seems to show /usr/lib/firefox as the "right" location for the ubuntu package.  

Still no idea why deleting /opt/firefox broke my gnome menu links, but I replaced the menu command with the absolute path (/usr/lib/firefox/firefox) and it works.  

Good enough for me, but I still think this is some bug in the package or paths...

-- Chad

---

### Post by Dragonlaw on 2008-04-05
cinematography THANK YOU SO VERY MUCH. I spent 8 hours on the Java because I could not find out how to solve this damn thing. YOUR ADVICE HELPED SO MUCH! THANKS

---

