---
title: "Invalid ELF header"
date: 2006-04-12
forum: Desktop Environments
---

### Post by Zeroedout on 2006-04-12
Hello, I've got a problem that has stumped the **** outta me. Certain program don't start, and give me an error claiming there is an invalid ELF header. For example, if I run gedit, I get ```
  	 	  gedit: error while loading shared libraries: /usr/lib/libgnomeui-2.so.0: invalid ELF header
 
``` If I run kate I get ```
   	 	 	 	 	 	 	 	  kate: error while loading shared libraries: /usr/lib/libkatepartinterfaces.so.0: invalid ELF header
 
```

However, many other applications work fine, openoffice and firefox are running great, but I guess they don't use those libs. I tried booting with ide=nodma, and I also unprelinked my system, but same thing. I searched the forum and read through some  threads, but no one seemed to have any solutions, google was of no help either. If anyone has any ideas, I'de greatly appreaciate it.

---

### Post by rmjokers on 2006-04-12
A few suggestions to get you started:

1.  Verify that those files exist on your system
2.  Re-install the packages that include those libraries
3.  Use a tool like 'readelf' to verify that the libraries really are ELF

By the way, ELF is the object file format used by all linux executables and libraries so it is very important that any shared libraries used by the system are in a valid ELF format.

---

