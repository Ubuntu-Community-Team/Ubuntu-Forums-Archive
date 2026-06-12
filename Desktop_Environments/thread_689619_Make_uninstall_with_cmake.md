---
title: "Make uninstall with cmake?"
date: 2008-02-06
forum: Desktop Environments
---

### Post by JackieBrown on 2008-02-06
I have complied kde4 from svn and have been keeping it up to date.

There are some modules (programs) that I do not use.  Is there anyway of unistalling these modules.

---

### Post by firephoto on 2008-02-06
You should be able to 'make uninstall' from your build directory.

What I have is the ~/.bashrc part from techbase so I have 'cs' 'cb' 'cmakekde' 'cmakekdeall' functions and everything is built and installed in the user directory. If you're doing the same you should be able to 'cb' to the proper build directory or sub-directory and make uninstall from there.

If you're using the kde-svn build setup I'm not sure where the pieces end up but I would guess you could modify the script to not build everything and also go in and remove what you've already built in a similar way.

---

### Post by JackieBrown on 2008-02-06
I never noticed the kde-svn tool.  Looks nice.

I have just been using cmake then make and finally make install.

This installs everything to /usr/local/

make unistall does not work

david@debian:/media/sda8/multi/dragonplayer$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.

I looked at [http://techbase.kde.org/index.php?title=Getting_Started/Increased_Productivity_in_KDE4_with_Scripts/.bashrc](http://techbase.kde.org/index.php?title=Getting_Started/Increased_Productivity_in_KDE4_with_Scripts/.bashrc) and did not see anything that would let make unistall work.

Maybe you have something else in your bashrc or I am looking in the wrong place?

---

### Post by firephoto on 2008-02-06
That's the same bashrc I'm using.

I just noticed I can 'make uninstall' just fine but 'make install' rebuilds it.

I suspect you're just in the src directory and not the build directory when you're trying to uninstall.

If you use the bashrc linked you just need to 'cs' to the src you want to build and 'cmakekde' and it configures, builds, and installs locally.

---

