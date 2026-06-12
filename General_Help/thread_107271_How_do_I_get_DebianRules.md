---
title: "How do I get Debian/Rules?"
date: 2005-12-22
forum: General Help
---

### Post by Game_Ender on 2005-12-22
I am trying to install the comedi-source packages with the command
```
sudo module-assistant auto-install comedi
``` 
and one of the scripts it runs says that there is no such thing as "debian/rules".  I know there is way to get because I have seen it referenced a couple of places on the wiki.  Can anyone tell me what package I have to install or whatever else I have to do to get it?

---

### Post by robotgeek on 2005-12-22
You can get the source using 
```

sudo apt-get install comedi-source

```

I think you are trying to install the comedi-driver (ni/labview?). Doing the above will get you the source, try the module-assistant part in /usr/src i think.

---

### Post by nalmeth on 2005-12-22
here are some google results, you'll have to put it together. never heard of it myself 

[http://keithdevens.com/weblog/archive/2005/May/12/Ubuntu-rules](http://keithdevens.com/weblog/archive/2005/May/12/Ubuntu-rules)
[http://ubuntuforums.org/archive/index.php/t-77931.html](http://ubuntuforums.org/archive/index.php/t-77931.html) (find debian/rules)

may / may not help

google is friend

---

### Post by Game_Ender on 2005-12-22
[QUOTE=robotgeek]You can get the source using 
```

sudo apt-get install comedi-source

```

I think you are trying to install the comedi-driver (ni/labview?). Doing the above will get you the source, try the module-assistant part in /usr/src i think.[/QUOTE]

I have the comedi-source package and the libcomedi package.  The comedi-source package had some documentation in /usr/share/doc/comedi-source and a README.Debian file that told me to do the module-assistant command.  After getting some extra packages (mostly kernel headers) to do the compile I finally got this error.

This is for the use of special hand controllers, not data acquisition.

I am beginning to think that debian/rules is package specific path, I will dig a little deeper, but this looks like something a package maintainer could tell me in about 2 minutes flat.

---

### Post by robotgeek on 2005-12-22
The debian/rules file will be in the src folder. Say the package is /usr/src/comedi-src, the rules file will be in /usr/src/comedi-src/debian/rules.

---

### Post by Game_Ender on 2005-12-23
So I have a little more info, when I first run the module-assistant auto-install, it finds the comedi-source.tar.gz package in the /usr/src directory and unpacks it.  It then spits out the error about not being able to find debian/rules.  Here is the exact and only error it gives:
```
/usr/share/modass/packages/generic.sh: line 58: debian/rules: No such file or directory

```

I have also looked at the structure of that tarball, and it is like this:
```

/modules
  /comedi
  /debian
  /Documentation
  /m4
  /incudes
  /scripts

```

There is also all the usual build files and such and there is a rules program under debian, so have no idea what the programs problem is.  Is there anyone with some module-assistant experience who could help?

---

### Post by wonko on 2007-01-13
Have anyone found a solution to this problem? 
Please share, because I'm having the same problem and getting really frustrated! 
](*,)

---

### Post by wonko on 2007-01-13
Installed debhelper and came a bit further... But modules-assistant still stops with an error. It now says:
>  dh_testdir                                                                 
 &#9474; #dh_testroot                                                              
 &#9474; rm -f build-arch-stamp build-indep-stamp                                  
 &#9474; # Add here commands to clean up after the build process.              
 &#9474; /usr/bin/make distclean                                                   
 &#9474; make[1]: Entering directory `/usr/src/modules/comedi'                  
 &#9474; make[1]: Leaving directory `/usr/src/modules/comedi'                     
 &#9474; dh_clean                                                                 
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules    
 &#9474; make[1]: Entering directory `/usr/src/modules/comedi'                    
 &#9474; dh_testdir                                                               
 &#9474; #dh_testroot                                                               
 &#9474; rm -f build-arch-stamp build-indep-stamp                             
 &#9474; # Add here commands to clean up after the build process.                  
 &#9474; /usr/bin/make distclean
 make[2]: Entering directory `/usr/src/modules/comedi'                    
 &#9474; make[2]: *** No rule to make target `distclean'.  Stop.                    
 &#9474; make[2]: Leaving directory `/usr/src/modules/comedi'                     
 &#9474; make[1]: [clean] Error 2 (ignored)                                      
 &#9474; dh_clean                                                                 
 &#9474; /usr/bin/gcc-4.1                                                           
 &#9474; for templ in ; do \                                                       
 &#9474;     cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.17-10-generic/g'` ; \  
 &#9474;   done                                                               
 &#9474; for templ in `ls debian/*.modules.in` ; do \                              
 &#9474;     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}        
 &#9474; ${templ%.modules.in}.backup 2>/dev/null || true; \                        
 &#9474;     sed -e 's/##KVERS##/2.6.17-10-generic/g                              
 &#9474; ;s/#KVERS#/2.6.17-10-generic/g ; s/_KVERS_/2.6.17-10-generic/g ;           
 &#9474; s/##KDREV##/2.6.17.1-10.34/g ; s/#KDREV#/2.6.17.1-10.34/g ;
 s/_KDREV_/2.6.17.1-10.34/g  ' < $templ > ${templ%.modules.in}; \         
 &#9474;   done                                                                   
 &#9474; dh_testdir                                                                 
 &#9474; # Add here commands to configure the package.                            
 &#9474; CFLAGS="-Wall -g -O2 -O2" ./configure --host=i486-linux-gnu             
 &#9474; --build=i486-linux-gnu --with-rtaidir=/usr/lib/realtime                  
 &#9474; checking build system type... i486-pc-linux-gnu                          
 <...checking blabla....>              
 &#9474; checking Linux config option CONFIG_SMP... yes                            
 &#9474; checking Linux config option CONFIG_HIGHMEM64G... no                      
 &#9474; configure: Putting kernel modules under /lib/modules/2.6.17-10-generic    
 &#9474; configure: Putting kernel module development files under     
 /lib/modules/2.6.17-10-generic/build                                     
 &#9474; checking Linux major/minor version... 2.6                                 
 &#9474; checking for Linux CFLAGS... ./configure: line 3829:                      
 &#9474; /usr/src/modules/comedi/./confstatAt8994/flags: No such file or directory  
 &#9474; make[1]: *** [config.status] Error 1                                       
 &#9474; make[1]: Leaving directory `/usr/src/modules/comedi'                      
 &#9474; make: *** [kdist_build] Error 2

[COLOR="Red"]Edit:[/COLOR] Tried downloading source from comedi.org and installing, but when this failed too, I installed dapper from scratch, and with the source from comedi.org I think I finally got it working :)

---

