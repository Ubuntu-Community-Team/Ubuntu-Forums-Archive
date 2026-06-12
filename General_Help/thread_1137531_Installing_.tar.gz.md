---
title: "Installing .tar.gz"
date: 2009-04-25
forum: General Help
---

### Post by apparle on 2009-04-25
I want to install the software called IPMessenger
[http://www.ipmsg.org/index.html.en](http://www.ipmsg.org/index.html.en)
So I downloaded the file
[http://www.ipmsg.org/archive/g2ipmsg-0.9.6.tar.gz](http://www.ipmsg.org/archive/g2ipmsg-0.9.6.tar.gz)

Could you pleaase guide, what all should I do to install the software

I extracted it and run the configure script............this is what I get

```
ap@PARLE:~/g2ipmsg-0.9.6$ sudo sh ./configure
checking for doxygen... no                   
configure: WARNING: doxygen not found - will not generate any doxygen documentation
checking for perl... /usr/bin/perl                                                 
checking for a BSD-compatible install... /usr/bin/install -c                       
checking whether build environment is sane... yes                                  
checking for a thread-safe mkdir -p... /bin/mkdir -p                               
checking for gawk... no                                                            
checking for mawk... mawk                                                          
checking whether make sets $(MAKE)... yes                                          
checking whether to enable maintainer-specific portions of Makefiles... no         
checking for style of include used by make... GNU                                                                                                                                 
checking for gcc... gcc                                                                                                                                                           
checking for C compiler default output file name... a.out                                                                                                                         
checking whether the C compiler works... yes                                                                                                                                      
checking whether we are cross compiling... no                                                                                                                                     
checking for suffix of executables...                                                                                                                                             
checking for suffix of object files... o                                                                                                                                          
checking whether we are using the GNU C compiler... yes                                                                                                                           
checking whether gcc accepts -g... yes                                                                                                                                            
checking for gcc option to accept ISO C89... none needed                                                                                                                          
checking dependency style of gcc... gcc3                                                                                                                                          
checking for library containing strerror... none required                                                                                                                         
checking for gcc... (cached) gcc                                                                                                                                                  
checking whether we are using the GNU C compiler... (cached) yes                                                                                                                  
checking whether gcc accepts -g... (cached) yes                                                                                                                                   
checking for gcc option to accept ISO C89... (cached) none needed                                                                                                                 
checking dependency style of gcc... (cached) gcc3                                                                                                                                 
checking for gcc... (cached) gcc                                                                                                                                                  
checking whether we are using the GNU C compiler... (cached) yes                                                                                                                  
checking whether gcc accepts -g... (cached) yes                                                                                                                                   
checking for gcc option to accept ISO C89... (cached) none needed                                                                                                                 
checking dependency style of gcc... (cached) gcc3                                                                                                                                 
checking for intltool >= 0.31... 0.37.1 found                                                                                                                                     
checking for xgettext... /usr/bin/xgettext                                                                                                                                        
checking for msgmerge... /usr/bin/msgmerge                                                                                                                                        
checking for msgfmt... /usr/bin/msgfmt                                                                                                                                            
checking for perl... /usr/bin/perl                                                                                                                                                
checking for XML::Parser... ok                                                                                                                                                    
checking how to run the C preprocessor... gcc -E                                                                                                                                  
checking for grep that handles long lines and -e... /bin/grep                                                                                                                     
checking for egrep... /bin/grep -E                                                                                                                                                
checking for ANSI C header files... yes                                                                                                                                           
checking for special C compiler options needed for large files... no                                                                                                              
checking for _FILE_OFFSET_BITS value needed for large files... 64                                                                                                                 
checking for sys/types.h... yes                                                                                                                                                   
checking for sys/stat.h... yes                                                                                                                                                    
checking for stdlib.h... yes                                                                                                                                                      
checking for string.h... yes                                                                                                                                                      
checking for memory.h... yes                                                                                                                                                      
checking for strings.h... yes                                                                                                                                                     
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dirfd... yes
checking for asctime_r... yes
checking for localtime_r... yes
checking for pkg-config... /usr/bin/pkg-config
checking OpenSSL options with pkg-config... no
checking for gdi32... no
checking for CRYPTO_lock in -lcrypto... no
checking for CRYPTO_add_lock in -lcrypto... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for G2IPMSG... configure: error: Package requirements (libgnomeui-2.0 >= 2.14
                        gtk+-2.0 >= 2.4
                        glib-2.0 >= 2.8) were not met:

No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables G2IPMSG_CFLAGS
and G2IPMSG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

ap@PARLE:~/g2ipmsg-0.9.6$

```


Please tell me what to do next.
I am on Kubuntu so I might not have basic gnome libraries installed, though I have installed some gnome softwares installed

---

### Post by mc4man on 2009-04-25
Not sure about using kubuntu and you didn't mentioon if your still using hardy. Anyway, (everything should be in adept or synaptic if you've installed it

[http://packages.ubuntu.com/hardy-updates/libglib2.0-dev](http://packages.ubuntu.com/hardy-updates/libglib2.0-dev)
[http://packages.ubuntu.com/hardy/libgnomeui-dev](http://packages.ubuntu.com/hardy/libgnomeui-dev)
[http://packages.ubuntu.com/hardy-updates/libgtk2.0-dev](http://packages.ubuntu.com/hardy-updates/libgtk2.0-dev)

[http://packages.ubuntu.com/hardy/doxygen](http://packages.ubuntu.com/hardy/doxygen)

---

### Post by apparle on 2009-04-26
thanks insalled it

---

### Post by apparle on 2009-04-26
Now I have a funny problem.
When I run
```
make install
```
It shows some error and says permission is denied.

So I use the command
```
sudo make install
```

Now the install is complete.

But whenever I have to start the program I have to use sudo.
Also the program treats /root as the home folder and whichever files are created by the program are not accessible to normal user.
So is there a way I can install it into my normal user without getting permission denied

---

### Post by 3rdalbum on 2009-04-26
You may need to change permissions on the program so that other users are able to run it.

```
sudo chmod a+x /usr/local/bin/ipmessenger
```

In future, don't run the configure script with *sudo*. The only step of compiling that requires you to be root is the "make install". Remember, you only need root if you are modifying files within the filesystem.

---

### Post by apparle on 2009-04-26
I removed the installed ipmsg.

Then I configured it without sudo, and installed it as you said.
But when I run it I get "segmentation fault" and if I run it using sudo then it works fine. What to do

---

### Post by apparle on 2009-04-27
After reboot it is working fine

---

