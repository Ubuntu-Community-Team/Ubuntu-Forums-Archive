---
title: "AWN Installation"
date: 2009-01-18
forum: General Help
---

### Post by DJ24966 on 2009-01-18
I'm trying to install AWN using the following guide.

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

All goes well until I get to the 

sudo apt-get install avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk

When I try to do this in terminal I get the following

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-trunk: Depends: libawn0-trunk (>= 0.3.0) but it is not going to be installed
                                Depends: python-awn-trunk (>= 0.3.1~bzr496-hardy1-1) but it is not going to be installed
  awn-extras-applets-trunk: Depends: libawn0-trunk (>= 0.3.0) but it is not going to be installed
                            Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
                            Depends: libwebkit-1.0-1 (>= 0~svn31841) but it is not going to be installed
  awn-manager-trunk: Depends: python-awn-trunk but it is not going to be installed
E: Broken packages

```

I have checked for updates and can't seem to figure this out for the life of me, that and the fact that I'm still new to linux.

Any help is appreciated.

Thanks

---

### Post by gettinoriginal on 2009-01-18
That is because not all necessary dependencies have been installed.  May I suggest this installation guide instead :P
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by DJ24966 on 2009-01-18
I missed a step before I guess.

Got it going now

Thanks alot!

---

