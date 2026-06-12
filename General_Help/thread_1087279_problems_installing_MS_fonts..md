---
title: "problems installing MS fonts."
date: 2009-03-04
forum: General Help
---

### Post by NJ0E on 2009-03-04
I did the install function and this is what I got back. Also ried it in Synaptic manager. Any work around? I am not dual booting. Using 


nj0e@nj0e-laptop:~$ sudo apt-get install msttcorefonts
[sudo] password for nj0e: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 247 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.5) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility". This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now everytime I install a package, I get the machine trying to install the fonts and get the same error again.  

How can I fix this so that 
a: I have the fonts, 
and b: I have no more error messages?

Thanks

---

