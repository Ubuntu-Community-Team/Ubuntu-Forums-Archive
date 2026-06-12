---
title: "Adobe Connect Add-in for 64bit ubuntu - any luck getting it to work?"
date: 2011-10-06
forum: Desktop Environments
---

### Post by akvik on 2011-10-06
Hi,

I'm running oneiric 64 bit, and I've tried to install the Adobe Connect add-in for 64 that were released recently:
> 
Ubuntu Linux 10.04 64-bit Add-in now available

Adobe Connect now supports hosts and presenters using Ubuntu Linux 10.04 64-bit OS with a new Meeting Add-In.  This Add-in is not required for Adobe Connect 8 SP2 and is completely optional.  The Add-in can be downloaded here.

Quote picked from here:
[http://blogs.adobe.com/adobeconnect/2011/09/adobe-connect-service-pack-2.html](http://blogs.adobe.com/adobeconnect/2011/09/adobe-connect-service-pack-2.html)

I managed to install, but bump into problems when running it, which seems to come from lacking 32-bit libraries:

```


/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(connectaddin:4922): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

```

I get this after fixing the similar libcurl error I got - fixed that by installing libcurl3:i386. However, with this gtk-error I can't install the 32-bit libs without a major heap of libs and apps for 32-bit being installed.

Anyone with ideas on how to fix this?

---

### Post by Geremia on 2012-12-18
Adobe is about as Linux unfriendly as they get. They are stopping their Flash support for Linux, too.

The issue you're encountering is due to the fact that what Adobe says is a 64 bit executable is really a 32 bit executable. Run```
file /usr/local/connectaddin
```It probably says it's 32 bit.

Look at [this thread]("http://forums.adobe.com/thread/864930"). People have been noticing since January that Adobe is lying about their 32 bit executable being 64 bit. What a joke

---

### Post by oldos2er on 2012-12-18
Old thread closed.

---

