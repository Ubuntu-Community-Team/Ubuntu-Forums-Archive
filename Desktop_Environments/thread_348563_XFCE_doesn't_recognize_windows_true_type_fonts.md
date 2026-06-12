---
title: "XFCE doesn't recognize windows true type fonts"
date: 2007-01-28
forum: Desktop Environments
---

### Post by sewpafly on 2007-01-28
Using xfce 4.4 rc1 (I think -- it's from the edgy xubuntu release).  I tried adding my windows fonts to both the .fonts subdirectory of my user directory and /usr/share/fonts/myfonts and updated my font cache and the system sees all the fonts, but when I try to set one of them with xubuntu (in the window-manager or the user-interface panel) all I see is a series of blocks where the words/characters should be.  Does anyone know what the problem could be?

---

### Post by kerry_s on 2007-01-29
Have you tried rebooting? Also did you add the font path to xorg.conf?

---

### Post by sewpafly on 2007-01-29
Tried adding the path to xorg.conf and then rebooting.  Didn't work.

---

### Post by kerry_s on 2007-01-29
When you say your windows fonts, does that mean like a personal collection or are you just trying to use windows fonts?

---

### Post by sewpafly on 2007-01-29
Copied the .ttf fonts from a WINDOWS/Fonts directory

---

### Post by kerry_s on 2007-01-29
Okay, the easy way i found to do it is to install msttcorefonts, then just copy the windows fonts and paste them into that folder.

in terminal:
sudo apt-get update
sudo apt-get install msttcorefonts

this will create a folder in truetype named msttcorefonts just add your fonts in there. That should setup your system to use windows fonts.

---

### Post by kanha on 2007-01-29
> **kerry_s said:**
> Okay, the easy way i found to do it is to install msttcorefonts, then just copy the windows fonts and paste them into that folder.

in terminal:
sudo apt-get update
sudo apt-get install msttcorefonts

this will create a folder in truetype named msttcorefonts just add your fonts in there. That should setup your system to use windows fonts.

I am getting this response ... don't know what to do now :confused: 
kanha@vachaspati:~$ sudo apt-get install msttcorefonts
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
kanha@vachaspati:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
kanha@vachaspati:~$ sudo dpkg --configure -a
Setting up msttcorefonts (1.2ubuntu3) ...
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 6.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 6.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 6.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 9.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 13.
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--14:12:08--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--14:12:08--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
--14:12:13--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
--14:12:14--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Temporary failure in name resolution.
--14:12:19--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--14:12:24--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

somebody enlighten me,
one more thing - this is in ubuntu-gnome not in xfce

---

### Post by kerry_s on 2007-01-29
Looks like your apt-get system is a mess. Try running this->
sudo apt-get -f install

---

### Post by sewpafly on 2007-01-29
Happy Ending!

Unfortunately, the advice above didn't work exactly...  It did get me pointed in the right direction though.  (I already had the msttcorefonts package installed).  I hadn't noticed that when I mounted the windows drive it wasnt giving world readable permissions to the files for some reason...  A quick ```
chmod 644 *
``` did the trick though.  

Thanks for your help.

---

