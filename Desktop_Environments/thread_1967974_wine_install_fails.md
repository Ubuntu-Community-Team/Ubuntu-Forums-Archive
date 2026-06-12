---
title: "wine install fails"
date: 2012-04-28
forum: Desktop Environments
---

### Post by eyelessfade on 2012-04-28
Wine doesn't seem to want to get installed
```
$ sudo aptitude install wine
The following NEW packages will be installed:
  gettext:i386{ab} gettext-base:i386{ab} libasn1-8-heimdal:i386{a} libasound2:i386{a} 
  libavahi-client3:i386{a} libavahi-common3:i386{a} libc6:i386{a} libcapi20-3:i386{a} 
  libcomerr2:i386{a} libcroco3:i386{a} libcups2:i386{a} libdb5.1:i386{a} libdbus-1-3:i386{a} 
  libdrm-intel1:i386{a} libdrm-nouveau1a:i386{a} libdrm-radeon1:i386{a} libdrm2:i386{a} 
  libelf1:i386{a} libexif12:i386{a} libexpat1:i386{a} libffi6:i386{a} libfontconfig1:i386{a} 
  libfreetype6:i386{a} libgcc1:i386{a} libgcrypt11:i386{a} libgd2-xpm:i386{a} 
  libgettextpo0:i386{a} libgif4:i386{a} libgl1-mesa-dri:i386{a} libgl1-mesa-glx:i386{a} 
  libglapi-mesa:i386{a} libglib2.0-0:i386{a} libglu1-mesa:i386{a} libgnutls26:i386{a} 
  libgomp1:i386{a} libgpg-error0:i386{a} libgphoto2-2:i386{a} libgphoto2-port0:i386{a} 
  libgpm2:i386{a} libgssapi-krb5-2:i386{a} libgssapi3-heimdal:i386{a} 
  libgstreamer-plugins-base0.10-0:i386{a} libgstreamer0.10-0:i386{a} libhcrypto4-heimdal:i386{a} 
  libheimbase1-heimdal:i386{a} libheimntlm0-heimdal:i386{a} libhx509-5-heimdal:i386{a} 
  libice6:i386{a} libieee1284-3:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} 
  libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} 
  libkrb5support0:i386{a} liblcms1:i386{a} libldap-2.4-2:i386{a} libllvm3.0:i386{a} 
  libltdl7:i386{a} libmpg123-0:i386{a} libncurses5:i386{a} libopenal1:i386{a} liborc-0.4-0:i386{a} 
  libp11-kit0:i386{a} libpciaccess0:i386{a} libpcre3:i386{a} libpng12-0:i386{a} 
  libroken18-heimdal:i386{a} libsane:i386{a} libsasl2-2:i386{a} libsasl2-modules:i386{a} 
  libselinux1:i386{a} libsm6:i386{a} libsqlite3-0:i386{a} libssl1.0.0:i386{a} libstdc++6:i386{a} 
  libtasn1-3:i386{a} libtiff4:i386{a} libtinfo5:i386{a} libunistring0:i386{a} libusb-0.1-4:i386{a} 
  libuuid1:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} libwind0-heimdal:i386{a} 
  libx11-6:i386{a} libx11-xcb1:i386{a} libxau6:i386{a} libxcb-glx0:i386{a} libxcb1:i386{a} 
  libxcomposite1:i386{a} libxcursor1:i386{a} libxdamage1:i386{a} libxdmcp6:i386{a} 
  libxext6:i386{a} libxfixes3:i386{a} libxi6:i386{a} libxinerama1:i386{a} libxml2:i386{a} 
  libxpm4:i386{a} libxrandr2:i386{a} libxrender1:i386{a} libxslt1.1:i386{a} libxt6:i386{a} 
  libxxf86vm1:i386{a} wine wine-gecko1.4:i386{a} wine1.4{a} wine1.4-amd64{a} wine1.4-common{a} 
  wine1.4-i386:i386{a} zlib1g:i386{a} 
0 packages upgraded, 113 newly installed, 0 to remove and 0 not upgraded.
Need to get 91.5 MB of archives. After unpacking 336 MB will be used.
The following packages have unmet dependencies:
 gettext-base : Conflicts: gettext-base:i386 but 0.18.1.1-5ubuntu3 is to be installed.
 gettext-base:i386 : Conflicts: gettext-base but 0.18.1.1-5ubuntu3 is installed.
 gettext : Conflicts: gettext:i386 but 0.18.1.1-5ubuntu3 is to be installed.
 gettext:i386 : Conflicts: gettext but 0.18.1.1-5ubuntu3 is installed.
Internal error: the solver Install(grub-common:i386 1.99-21ubuntu3 <grub-emu:amd64 1.99-21ubuntu3 -> {grub-common:amd64 1.99-21ubuntu3 grub-common:i386 1.99-21ubuntu3}>) of a supposedly unresolved dependency is already installed in step 275
Internal error: the solver Install(grub-common:i386 1.99-21ubuntu3 <grub2-common:amd64 1.99-21ubuntu3 -> {grub-common:amd64 1.99-21ubuntu3 grub-common:i386 1.99-21ubuntu3}>) of a supposedly unresolved dependency is already installed in step 275
Internal error: the solver Install(grub-common:i386 1.99-21ubuntu3 <grub-pc-bin:amd64 1.99-21ubuntu3 -> {grub-common:amd64 1.99-21ubuntu3 grub-common:i386 1.99-21ubuntu3}>) of a supposedly unresolved dependency is already installed in step 275
Internal error: the solver Install(grub-pc:i386 1.99-21ubuntu3 <kde-config-grub2:amd64 0.5.0-0ubuntu3 -> {grub-efi-amd64:amd64 1.99-21ubuntu3 grub-efi-amd64:i386 1.99-21ubuntu3 grub-efi-ia32:amd64 1.99-21ubuntu3 grub-efi-ia32:i386 1.99-21ubuntu3 grub-pc:amd64 1.99-21ubuntu3 grub-pc:i386 1.99-21ubuntu3}>) of a supposedly unresolved dependency is already installed in step 363
Internal error: the solver Install(grub-pc:i386 1.99-21ubuntu3 <grub-gfxpayload-lists:amd64 0.6 -> {grub-pc:amd64 1.99-21ubuntu3 grub-pc:i386 1.99-21ubuntu3}>) of a supposedly unresolved dependency is already installed in step 363
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4 <ijsgutenprint:amd64 5.2.8~pre1-0ubuntu2 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4 ghostscript:i386 9.05~dfsg-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 633
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4 <gs-cjk-resource:amd64 1.20100103-3 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4 ghostscript:i386 9.05~dfsg-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 633
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4 <ghostscript-x:amd64 9.05~dfsg-0ubuntu4 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4 ghostscript:i386 9.05~dfsg-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 633
Internal error: the solver Install(gvfs-daemons:i386 1.12.1-0ubuntu1 <gvfs-backends:amd64 1.12.1-0ubuntu1 -> {gvfs-daemons:amd64 1.12.1-0ubuntu1 gvfs-daemons:i386 1.12.1-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 874
Internal error: the solver Install(gvfs-daemons:i386 1.12.1-0ubuntu1 <gvfs:amd64 1.12.1-0ubuntu1 -> {gvfs-daemons:amd64 1.12.1-0ubuntu1 gvfs-daemons:i386 1.12.1-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 874
Internal error: the solver Install(gvfs-daemons:i386 1.12.1-0ubuntu1 <gvfs:amd64 1.12.1-0ubuntu1 -> {gvfs-daemons:amd64 1.12.1-0ubuntu1 gvfs-daemons:i386 1.12.1-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 874
The following actions will resolve these dependencies:

       Keep the following packages at their current version:                   
1)       gettext:i386 [Not Installed]                                          
2)       gettext-base:i386 [Not Installed]                                     
3)       libasn1-8-heimdal:i386 [Not Installed]                                
4)       libasound2:i386 [Not Installed]                                       
5)       libavahi-client3:i386 [Not Installed]                                 
6)       libavahi-common3:i386 [Not Installed]                                 
7)       libc6:i386 [Not Installed]                                            
8)       libcapi20-3:i386 [Not Installed]                                      
9)       libcomerr2:i386 [Not Installed]                                       
10)      libcroco3:i386 [Not Installed]                                        
11)      libcups2:i386 [Not Installed]                                         
12)      libdb5.1:i386 [Not Installed]                                         
13)      libdbus-1-3:i386 [Not Installed]                                      
14)      libdrm-intel1:i386 [Not Installed]                                    
15)      libdrm-nouveau1a:i386 [Not Installed]                                 
16)      libdrm-radeon1:i386 [Not Installed]                                   
17)      libdrm2:i386 [Not Installed]                                          
18)      libelf1:i386 [Not Installed]                                          
19)      libexif12:i386 [Not Installed]                                        
20)      libexpat1:i386 [Not Installed]                                        
21)      libffi6:i386 [Not Installed]                                          
22)      libfontconfig1:i386 [Not Installed]                                   
23)      libfreetype6:i386 [Not Installed]                                     
24)      libgcc1:i386 [Not Installed]                                          
25)      libgcrypt11:i386 [Not Installed]                                      
26)      libgd2-xpm:i386 [Not Installed]                                       
27)      libgettextpo0:i386 [Not Installed]                                    
28)      libgif4:i386 [Not Installed]                                          
29)      libgl1-mesa-dri:i386 [Not Installed]                                  
30)      libgl1-mesa-glx:i386 [Not Installed]                                  
31)      libglapi-mesa:i386 [Not Installed]                                    
32)      libglib2.0-0:i386 [Not Installed]                                     
33)      libglu1-mesa:i386 [Not Installed]                                     
34)      libgnutls26:i386 [Not Installed]                                      
35)      libgomp1:i386 [Not Installed]                                         
36)      libgpg-error0:i386 [Not Installed]                                    
37)      libgphoto2-2:i386 [Not Installed]                                     
38)      libgphoto2-port0:i386 [Not Installed]                                 
39)      libgpm2:i386 [Not Installed]                                          
40)      libgssapi-krb5-2:i386 [Not Installed]                                 
41)      libgssapi3-heimdal:i386 [Not Installed]                               
42)      libgstreamer-plugins-base0.10-0:i386 [Not Installed]                  
43)      libgstreamer0.10-0:i386 [Not Installed]                               
44)      libhcrypto4-heimdal:i386 [Not Installed]                              
45)      libheimbase1-heimdal:i386 [Not Installed]                             
46)      libheimntlm0-heimdal:i386 [Not Installed]                             
47)      libhx509-5-heimdal:i386 [Not Installed]                               
48)      libice6:i386 [Not Installed]                                          
49)      libieee1284-3:i386 [Not Installed]                                    
50)      libjpeg-turbo8:i386 [Not Installed]                                   
51)      libjpeg8:i386 [Not Installed]                                         
52)      libk5crypto3:i386 [Not Installed]                                     
53)      libkeyutils1:i386 [Not Installed]                                     
54)      libkrb5-26-heimdal:i386 [Not Installed]                               
55)      libkrb5-3:i386 [Not Installed]                                        
56)      libkrb5support0:i386 [Not Installed]                                  
57)      liblcms1:i386 [Not Installed]                                         
58)      libldap-2.4-2:i386 [Not Installed]                                    
59)      libllvm3.0:i386 [Not Installed]                                       
60)      libltdl7:i386 [Not Installed]                                         
61)      libmpg123-0:i386 [Not Installed]                                      
62)      libncurses5:i386 [Not Installed]                                      
63)      libopenal1:i386 [Not Installed]                                       
64)      liborc-0.4-0:i386 [Not Installed]                                     
65)      libp11-kit0:i386 [Not Installed]                                      
66)      libpciaccess0:i386 [Not Installed]                                    
67)      libpcre3:i386 [Not Installed]                                         
68)      libpng12-0:i386 [Not Installed]                                       
69)      libroken18-heimdal:i386 [Not Installed]                               
70)      libsane:i386 [Not Installed]                                          
71)      libsasl2-2:i386 [Not Installed]                                       
72)      libsasl2-modules:i386 [Not Installed]                                 
73)      libselinux1:i386 [Not Installed]                                      
74)      libsm6:i386 [Not Installed]                                           
75)      libsqlite3-0:i386 [Not Installed]                                     
76)      libssl1.0.0:i386 [Not Installed]                                      
77)      libstdc++6:i386 [Not Installed]                                       
78)      libtasn1-3:i386 [Not Installed]                                       
79)      libtiff4:i386 [Not Installed]                                         
80)      libtinfo5:i386 [Not Installed]                                        
81)      libunistring0:i386 [Not Installed]                                    
82)      libusb-0.1-4:i386 [Not Installed]                                     
83)      libuuid1:i386 [Not Installed]                                         
84)      libv4l-0:i386 [Not Installed]                                         
85)      libv4lconvert0:i386 [Not Installed]                                   
86)      libwind0-heimdal:i386 [Not Installed]                                 
87)      libx11-6:i386 [Not Installed]                                         
88)      libx11-xcb1:i386 [Not Installed]                                      
89)      libxau6:i386 [Not Installed]                                          
90)      libxcb-glx0:i386 [Not Installed]                                      
91)      libxcb1:i386 [Not Installed]                                          
92)      libxcomposite1:i386 [Not Installed]                                   
93)      libxcursor1:i386 [Not Installed]                                      
94)      libxdamage1:i386 [Not Installed]                                      
95)      libxdmcp6:i386 [Not Installed]                                        
96)      libxext6:i386 [Not Installed]                                         
97)      libxfixes3:i386 [Not Installed]                                       
98)      libxi6:i386 [Not Installed]                                           
99)      libxinerama1:i386 [Not Installed]                                     
100)     libxml2:i386 [Not Installed]                                          
101)     libxpm4:i386 [Not Installed]                                          
102)     libxrandr2:i386 [Not Installed]                                       
103)     libxrender1:i386 [Not Installed]                                      
104)     libxslt1.1:i386 [Not Installed]                                       
105)     libxt6:i386 [Not Installed]                                           
106)     libxxf86vm1:i386 [Not Installed]                                      
107)     wine [Not Installed]                                                  
108)     wine-gecko1.4:i386 [Not Installed]                                    
109)     wine1.4 [Not Installed]                                               
110)     wine1.4-amd64 [Not Installed]                                         
111)     wine1.4-common [Not Installed]                                        
112)     wine1.4-i386:i386 [Not Installed]                                     
113)     zlib1g:i386 [Not Installed]                                           

       Leave the following dependencies unresolved:                            
114)     libgphoto2-2:i386 recommends udev:i386 (>= 0.175)                     
115)     libgphoto2-2:i386 recommends libgphoto2-l10n:i386 (>= 2.4.13-1ubuntu1)
116)     libncurses5:i386 recommends libgpm2:i386                              
117)     wine1.4-i386:i386 recommends libfontconfig1:i386 | libfontconfig:i386 
118)     wine1.4-i386:i386 recommends libsane:i386                             
119)     wine-gecko1.4:i386 recommends wine1.4-i386:i386                       


Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
localepurge: checking for existence of /var/cache/localepurge...
localepurge: checking for existence of /var/cache/localepurge/localelist...
localepurge: checking system for new locale ...
localepurge: processing locale files ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: processing man pages ...
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: processing Gnome files ...
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: processing Omf files ...
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: processing KDE files ...
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB
```

---

