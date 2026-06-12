---
title: "Easy Ubuntu Error Message - Confused"
date: 2006-07-31
forum: Desktop Environments
---

### Post by hambro on 2006-07-31
So I am trying to install applications on Linux which is a lot different than I expected.  Nonetheless I figured it's a computer, if you follow the instructions correctly you cannot fail.  Apparently not so.  I have repeatedly botched the Easy Ubuntu (ironic isn't it) and ATI driver installs.   The error output for EU is as follows:
> 
ralfi@lemonade:~$ wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
--21:55:58--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
           => `easyubuntu-3.022.tar.gz.3'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92,665 (90K) [application/x-tar]

100%[====================================>] 92,665       143.79K/s

21:56:00 (143.36 KB/s) - `easyubuntu-3.022.tar.gz.3' saved [92665/92665]

ralfi@lemonade:~$ tar -zxf easyubuntu-3.022.tar.gz
ralfi@lemonade:~$ cd easyubuntu
ralfi@lemonade:~/easyubuntu$ sudo python easyubuntu.in
System sanity check: Failed!
Errors:
--------
/usr/share/gconf/schemas/panel-global.schemas:4767: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xF0 0xBD 0x91 0xE0
&#3942;&#3851; &#3924;&#3962;&#3851;&#3923;&#3953;&#3939;&#3851;&#3921;&#3962;&#3851; &#3939;&#3964;&#3906;&#3851;&#3936;&#3906;&#3964;&#3851;&#3926;&#3929;&#3956;&#3906;&#3942;&#3851;
                                                                               ^dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 2.14.2-0ubuntu1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-panel (>= 2.12.1-1); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
 gnome-applets
E: Sub-process /usr/bin/dpkg returned an error code (1)

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors:
--------
/usr/share/gconf/schemas/panel-global.schemas:4767: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xF0 0xBD 0x91 0xE0
&#3942;&#3851; &#3924;&#3962;&#3851;&#3923;&#3953;&#3939;&#3851;&#3921;&#3962;&#3851; &#3939;&#3964;&#3906;&#3851;&#3936;&#3906;&#3964;&#3851;&#3926;&#3929;&#3956;&#3906;&#3942;&#3851;
                                                                               ^dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 2.14.2-0ubuntu1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-panel (>= 2.12.1-1); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
 gnome-applets

EasyUbuntu will not run before these errors are fixed. Please fix them and try again
ralfi@lemonade:~/easyubuntu$



My system does not pass the sanity check.  I do not know what this means although it is not difficult for me to conjecture.  If anybody is capable of pointing me in the right direction that's great, if this is just a naive question then I apologize for wasting time.

---

