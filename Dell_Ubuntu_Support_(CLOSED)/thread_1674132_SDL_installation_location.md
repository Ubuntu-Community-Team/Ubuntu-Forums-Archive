---
title: "SDL installation location?"
date: 2011-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SitarHER0 on 2011-01-23
I'm trying to install SDL_Perl-v2.2.6. I've followed instructions I've been given, and this error message appears: 

daniel@ubuntu:~/Programming/SDL/SDL_Perl-v2.2.6$ perl ./Build.PL
********************************* !!!ERROR!!! ********************************* 
SDL library not found.
1) If you do not have SDL, you can download it from see [http://www.libsdl.org/](http://www.libsdl.org/)
2) If you have already installed SDL, you can specify the location of your SDL
   installation by setting the enviroment variable SDL_INST_DIR.  
*******************************************************************************
SDL not installed at ./Build.PL line 26

I'm pretty sure I already have SDL from [www.libsdl.org]("http://www.libsdl.org"), and that is in this folder: /home/[user]/Documents/Module_folders/SDL-1.2.14

I've tried specifying SDL_INST_DIR in the "environment" file in "/etc", but I still get the the same error message. Could someone give me some pointers into what I'm doing wrong?

Thanks in advance.

---

