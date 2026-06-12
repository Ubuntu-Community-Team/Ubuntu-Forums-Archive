---
title: "How to update Java installed?"
date: 2009-05-04
forum: General Help
---

### Post by stpike on 2009-05-04
I recently installed 8.04LTS Hardy Heron and want to update to Java 6.13.  I have installed the jre in my home directory, and have followed the instructions, restarted firefox,  but when I view the plugins using 'about:plugins' it reports 1.6.0_07.  Where have I gone wrong?

Thank you in advance.

---

### Post by kryptikos on 2009-05-04
Sounds as if firefox is still referencing the older libjavaplugin_oji.so. 

Since you have downloaded java manually instead of via Synaptic or apt-get you'll just reference your home directory instead of the traditional /usr/lib/jvm...

Open up a terminal and create a softlink from your home directory to the firefox plugins directory:

**sudo ln -s <your home directory java>/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so /usr/lib/firefox-<version number>/plugins/libjavaplugin_oji.so**

Restart Firefox to make it pick up its new values. That's usually the method I use when manually switching between java versions. 

Hope that helps... :)

---

### Post by stpike on 2009-05-05
Unfortunately, that didn't work.  Is there something special I need to do because I am using 8.04LTS?

I refreshed the Synaptic Package Manager and it displayed that I had 6-07-3ubuntu2 and that was the latest available.

I also modified the link in /usr/lib/jre from: java-6-sun -> java-6-sun-1.6.0.07 to: java-6-sun -> /home/username/java/jre1.6.0_13 and now, firefox does not see Java at all.

regards,
Steve

---

### Post by stpike on 2009-05-05
And I did restart firefox after the changes were made.

---

