---
title: "Kdevelop - code completion"
date: 2009-04-02
forum: General Help
---

### Post by marco1989 on 2009-04-02
Hello..
Sorry for my english but I'm italian and I've pass english exam with 66/100.

I started to use Kdevelop but I would use code completion..
Someone can help me...

---

### Post by 3Miro on 2009-04-02
Try this.

[http://www.kdevelop.org/mediawiki/index.php/FAQ#Code_Completion_FAQs](http://www.kdevelop.org/mediawiki/index.php/FAQ#Code_Completion_FAQs)

I have been thinking about enabling it for some time now and never got to it. I will try later today and see if it works. Let me know if it does for you.

---

### Post by marco1989 on 2009-04-02
Thank's for the answer.
I tried but doesn't work... :(

---

### Post by Vorian on 2009-04-02
you need build-essential and ...
```
steve@liger:~/motu/kde/422-mine/ubuntu$ apt-cache depends kdevelop
kdevelop                                                          
  Depends: kdelibs4c2a                                            
  Depends: libacl1                                                
  Depends: libapr1                                                
  Depends: libaprutil1                                            
  Depends: libart-2.0-2                                           
  Depends: libattr1                                               
  Depends: libaudio2                                              
  Depends: libc6                                                  
  Depends: libdb4.6                                               
  Depends: libfontconfig1                                         
  Depends: libfreetype6                                           
  Depends: libgcc1                                                
  Depends: libice6                                                
  Depends: libidn11                                               
  Depends: libjpeg62                                              
  Depends: libpcre3                                               
  Depends: libpng12-0                                             
  Depends: libqt3-mt                                              
  Depends: libsm6                                                 
  Depends: libstdc++6                                             
  Depends: libsvn1                                                
  Depends: libuuid1                                               
  Depends: libx11-6                                               
  Depends: libxcursor1                                            
  Depends: libxext6                                               
  Depends: libxft2                                                
  Depends: libxi6                                                 
  Depends: libxinerama1                                           
  Depends: libxrandr2                                             
  Depends: libxrender1                                            
  Depends: libxt6                                                 
  Depends: zlib1g                                                 
  Depends: kdevelop-data                                          
  Depends: kdebase-bin                                            
  Suggests: libqt3-mt-dev                                         
  Suggests: kdelibs4-dev                                          
  Suggests: sgmltools-lite
  Suggests: gettext
  Suggests: qt3-dev-tools
  Suggests: ark
  Suggests: <kbabel>
  Suggests: kiconedit
  Suggests: kdesdk-scripts
  Suggests: graphviz
  Suggests: exuberant-ctags
  Suggests: khelpcenter4
  Suggests: qt3-doc
  Suggests: konsole
  Suggests: cmake
  Suggests: ruby
  Suggests: python
  Recommends: kdevelop-doc
  Recommends: make
  Recommends: libtool
  Recommends: autoconf
  Recommends: automake
  Recommends: gdb

```

or $sudo apt-get build-dep kdevelp

---

### Post by 3Miro on 2009-04-02
> **Vorian said:**
> or $sudo apt-get build-dep kdevelp

Thanks a lot!

---

### Post by marco1989 on 2009-04-05
Thank's!!
 Now it work..

---

