---
title: "Compile Reveal"
date: 2006-09-29
forum: Desktop Environments
---

### Post by villindesign on 2006-09-29
Hello-

I'm trying to install [Reveal]("http://albumshaper.sourceforge.net/download.shtml") from source. The qmake command did not find all of the libraries it needs to compile the program, but they are installed. So I changed some settings to make it use manual paths that I give it in a file named libraries.pri. I put in /usr/lib for most of those, but I guess this wasn't right. I am putting the output of qmake below:
```
britt@britt-laptop:~/Desktop/clay_2006_04_17/projects$ qmake Reveal.pro sh: exiv2-config: command not found
sh: exiv2-config: command not found
Project MESSAGE: Configuring library dependencies for Reveal:
Project MESSAGE: ->Automatically configuring
Project MESSAGE: ->Build will require libjpeg
Project MESSAGE: ->Build will require libexiv2

```

Also, here is the libraries.pri file which needs changed to reflect the library locations. To compile, I need the Qt, libjpeg, libxslt, libxml2, and Exiv2 libraries; these libraries are installed. The top part of the file contains the paths. So if anyone knows what absolute paths I should use, please tell me! thanks
 -britt
```
#=====================================================================
#
# In order to build Album Shaper or one of the spinoff projects
# (Reveal, Presenter, etc) you may need one of the following libraries.
#
# Can't find the libraries you need?
#
# libjpeg:  http://www.ijg.org/files/
# libiconv: http://ftp.gnu.org/gnu/libiconv/
# libxslt:  http://xmlsoft.org/sources/
# libxml2:  http://xmlsoft.org/sources/
# libexiv2: http://www.exiv2.org/
#
#=====================================================================
#------------ Linux / BSD ------------
!mac:unix { 
  contains( CONFIG, manualPaths ) {

    contains(CONFIG, libjpeg) {
      INCLUDEPATH += ../../libs/libjpeg
      LIBS += ../../libs/libjpeg.a
    }

    contains(CONFIG, libxslt) {
      INCLUDEPATH += ../../libs/libxslt
      LIBS += ../../libs/libxslt.a    
    }
    
    contains(CONFIG, libxml2) {
      INCLUDEPATH += ../../libs/libxml2/include
      LIBS += ../../libs/libxml2.a        
    }

    contains(CONFIG, libiconv) {
      INCLUDEPATH += ../../libs/libiconv/include
      LIBS += ../../libs/libiconv.a        
    }
    
    contains(CONFIG, libexiv2) {
      INCLUDEPATH += ../../libs/libexiv2/src
      LIBS += ../../libs/libexiv2.a
    }
  } else {
        
    contains(CONFIG, libjpeg) LIBS += -ljpeg

    contains(CONFIG, libxslt) {
      LIBXSLT_INCLUDE  = $$system(xslt-config --cflags)
      QMAKE_CFLAGS_DEBUG     += $$LIBXSLT_INCLUDE
      QMAKE_CXXFLAGS_DEBUG   += $$LIBXSLT_INCLUDE
      QMAKE_CFLAGS_RELEASE   += $$LIBXSLT_INCLUDE
      QMAKE_CXXFLAGS_RELEASE += $$LIBXSLT_INCLUDE
      LIBS += $$system(xslt-config --libs)  
    }
  
    contains(CONFIG, libxml2) {
      LIBXML2_INCLUDE  = $$system(xml2-config --cflags)
      QMAKE_CFLAGS_DEBUG     += $$LIBXML2_INCLUDE
      QMAKE_CXXFLAGS_DEBUG   += $$LIBXML2_INCLUDE
      QMAKE_CFLAGS_RELEASE   += $$LIBXML2_INCLUDE
      QMAKE_CXXFLAGS_RELEASE += $$LIBXML2_INCLUDE
      LIBS += $$system(xml2-config --libs)
    }
    
    contains(CONFIG, libexiv2) {
      LIBEXIV2_INCLUDE = $$system(exiv2-config --cflags)
      QMAKE_CFLAGS_DEBUG     += $$LIBEXIV2_INCLUDE
      QMAKE_CXXFLAGS_DEBUG   += $$LIBEXIV2_INCLUDE
      QMAKE_CFLAGS_RELEASE   += $$LIBEXIV2_INCLUDE
      QMAKE_CXXFLAGS_RELEASE += $$LIBEXIV2_INCLUDE
      LIBS += $$system(exiv2-config --libs)         
    }

  } 
}
#-------------- Mac OSX --------------
mac {

  contains(CONFIG, libjpeg) {
    INCLUDEPATH += ../../libs/libjpeg
    LIBS += ../../libs/libjpeg.a 
  }
  
  contains(CONFIG, libxslt) {
    INCLUDEPATH += ../../libs/libxslt
    LIBS += ../../libs/libxslt.a    
  }
    
  contains(CONFIG, libxml2) {
    INCLUDEPATH += ../../libs/libxml2/include
    LIBS += ../../libs/libxml2.a        
  }
    
  contains(CONFIG, libiconv) {
    INCLUDEPATH += ../../libs/libxml2/include
    LIBS += ../../libs/libiconv.a        
  }

  contains(CONFIG, libexiv2) {
    INCLUDEPATH += ../../libs/libexiv2/src
    LIBS += ../../libs/libexiv2.a
  }
  
  LIBS += -L../../libs -F../../libs
}
#-------------- Windows --------------
windows {  
   
  contains(CONFIG, libjpeg) {
    INCLUDEPATH += ../../libs/libjpeg/include
    LIBS += ../../libs/libjpeg/lib/libjpeg.a
  }

  contains(CONFIG, libxslt) {
    INCLUDEPATH += e:/programming/libs/libxslt/include
    LIBS += ../../libs/libxslt/lib/libxslt_a.lib
  }

  contains(CONFIG, libxml2) {
    INCLUDEPATH += ../../libs/libxml2/include
    LIBS += ../../libs/libxml2/lib/libxml2_a.lib
  }

  contains(CONFIG, libiconv) {
    INCLUDEPATH += e:/programming/libs/iconv/include
    LIBS += ../../libs/iconv/lib/iconv_a.lib
  }

  contains(CONFIG, libexiv2) {
    INCLUDEPATH += ../../libs/libexiv2/src
    LIBS += ../../libs/libexiv2/src/.libs/libexiv2.a
  }

  contains(CONFIG, zlib) {
    INCLUDEPATH += ../../libs/zlib123
  }
  
  LIBS += -lws2_32

}
#-------------------------------------
#Announce library configuration

message('Configuring library dependencies for $$TARGET:')
contains( CONFIG, manualPaths ) {
  message('->Using manual paths')
} else {
  message('->Automatically configuring')
}

contains(CONFIG, libjpeg) message('->Build will require libjpeg')
contains(CONFIG, libxslt) message('->Build will require libxslt')
contains(CONFIG, libxml2) message('->Build will require libxml2')
contains(CONFIG, libiconv) message('->Build will require libiconv')
contains(CONFIG, libexiv2) message('->Build will require libexiv2')
#-------------------------------------


```

---

### Post by croak77 on 2006-09-29
Do you have all the *xxx*-dev packages installed. Like libexiv2-dev not just libexiv2.

---

### Post by villindesign on 2006-09-29
Yes, I have all of the devs for the libs. I installed of the libs with synaptic, so they should be in their default location...

Thanks for the suggestion!

---

### Post by villindesign on 2006-10-01
Anyone else have any ideas about this?

---

