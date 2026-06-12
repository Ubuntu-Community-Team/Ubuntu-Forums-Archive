---
title: "&quot;command not found&quot; error with new program"
date: 2006-03-23
forum: Desktop Environments
---

### Post by greatgoo on 2006-03-23
I have downloaded the iSeries Access for Linux from IBM.  This is an rpm package and I used alien to convert it and dpkg -i to install it.  There were some dependencies and I have installed those.

When I try to launch the emulator I get a command not found error.  I have tried to launch it from both the file viewer and the command line of the terminal window.  In fact, none of the executables in the bin folder will launch.  I was able to cat the file and got the basic bunch of machine code gibberish one would expect, so I assume the file is there.  The file viewer shows it to be an exacutable file.

I used Synaptic and removed it from the system and reinstalled it with dpkg on the odd chance that installing the depedencies after the fact would break it.  That didn't work.

One of the dependencies listed by IBM is glibc 2.2.  I see libc6 installed.  Could it be that there is that much difference between the libraries?

I have provided the link to the IBM documentation below.

[http://publib.boulder.ibm.com/infocenter/iseries/v5r4/index.jsp?topic=/rzatv/rzatvkickoff.htm](http://publib.boulder.ibm.com/infocenter/iseries/v5r4/index.jsp?topic=/rzatv/rzatvkickoff.htm)

David Davis     ](*,)

---

### Post by taurus on 2006-03-23
If that program is a binary, then you can check to see all the dependencies that it needs by
```

ldd <exact path to program>
-or-
ldd /usr/bash

```

---

### Post by greatgoo on 2006-03-23
> If that program is a binary, then you can check to see all the dependencies that it needs by
Code:

ldd <exact path to program> -or- ldd /usr/bash


My thanks for the tip.  I ran it and found three listed that it could not find.  I found all three in their various folders, so I assume there is a bug in the load.

All that I found were named correctly, except one that was updated.  However in that folder was a link to the new library, correctly named.

I will continue working on it but will gladly accept any suggestions.

David Davis

BTW:  I can use telnet to accomplish the same task,  but it is the principle of the thing.

D

---

### Post by taurus on 2006-03-23
If you run "ldd <program name>" and see a missing library, you need to hunt down and install that library or your program will never run!  If you can post the complete output of that command, "ldd <program name>", perhaps I can help you to look for it!!!

---

### Post by dcstar on 2006-03-24
[QUOTE=greatgoo]I have downloaded the iSeries Access for Linux from IBM.  This is an rpm package and I used alien to convert it and dpkg -i to install it.  There were some dependencies and I have installed those.

When I try to launch the emulator I get a command not found error.  I have tried to launch it from both the file viewer and the command line of the terminal window.
......[/QUOTE]
**Exactly** how did you try to launch it in the command line?

---

### Post by greatgoo on 2006-03-24
I will start with dcstar's question ..

I attempted to launch the 5250 emulator using the information from the IBM site.  Per their faq, at the command line, either with a path statement or from the directory where the executable resides, type the command followed by the target server.  Here then, from the home directory, is the attempt and the result ..

greatgoo@lnnw081:~$ /opt/ibm/iSeriesAccess/bin/ibm5250 lnn400
/opt/ibm/iSeriesAccess/bin/ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

AND  from the bin directory ..

greatgoo@lnnw081:/opt/ibm/iSeriesAccess/bin$ ibm5250  lnn400
bash: ibm5250: command not found

The first result giving much more detail than the last.  When I first posted the problem I was running from the bin directory to avoid typing in the path.

This brings me to taurus's question, the ldd printout ..

greatgoo@lnnw081:/opt/ibm/iSeriesAccess/bin$ ldd ibm5250
        linux-gate.so.1 =>  (0xffffe000)
        libXm.so.3 => not found
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7f9c000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7f4e000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7f47000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7f2e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7e6e000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb7e67000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7e59000)
        libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7e44000)
        libcwbcore.so => not found
        libstdc++.so.5 => not found
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e22000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7e16000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ce8000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ce5000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7ce2000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7cde000)
        /lib/ld-linux.so.2 (0xb7fbe000)

Here I see that the libxm.so.3 is not found.  This basically confirms what I saw in the above launch failure.  Using Synaptic I looked to see where the various files for openmotif had been installed.  The path is /usr/X11R6/lib and there an ls shows ..

greatgoo@lnnw081:/usr/X11R6/lib$ ls
libMrm.so.3      libUil.so.3      libXm.so.3      modules
libMrm.so.3.0.1  libUil.so.3.0.1  libXm.so.3.0.1  X11

so I was confused as to why the file was not found.  When I looked at the libxm.so.3 file in the file viewer I discovered it is a link, not a file, and points to libXm.so.3.0.1 which I assume is an update.

This openmotif is Rev 2.2.2-5 and I am wondering if I would be better served but putting on 2.2.2.  BUT!  IBM says openmotif  2.* per this clip from their web site ..

# iSeries Access: The 5250 Emulator is designed to be Linux distribution independent. The dependencies on the Linux distribution are glibc 2.2 and openmotif 2.*. The distribution must also support installing an rpm created with rpm 3.0.

Of course the rpm issue is resolved with alien.

David Davis

---

### Post by ispmarin on 2006-03-24
I don't know if this is related, but I am trying to run the opera brownser, and I am getting the same error... command not found, even if the command IS there. running with the entire path, from the symbolic link, from a script, or even ./opera, nothing works. Same with open office2, I've just discovered. What is happening? Very, very strange!!

---

### Post by dcstar on 2006-03-24
[QUOTE=greatgoo]I will start with dcstar's question ..

I attempted to launch the 5250 emulator using the information from the IBM site.  Per their faq, at the command line, either with a path statement or from the directory where the executable resides, type the command followed by the target server.  Here then, from the home directory, is the attempt and the result ..

greatgoo@lnnw081:~$ /opt/ibm/iSeriesAccess/bin/ibm5250 lnn400
/opt/ibm/iSeriesAccess/bin/ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

AND  from the bin directory ..

greatgoo@lnnw081:/opt/ibm/iSeriesAccess/bin$ ibm5250  lnn400
bash: ibm5250: command not found
.......[/QUOTE]
Of course it will say that, you have to launch any Unix/Linux executable not in an existing path with "./" in front of it, for example:
```
greatgoo@lnnw081:/opt/ibm/iSeriesAccess/bin$ ./ibm5250  lnn400
```
will probably give you the same result as using the full path.

To fix the libXm.so.3 problem, try installing the libxp6 package:

[http://www.ubuntuforums.org/showthread.php?t=65879&highlight=libXm.so.3](http://www.ubuntuforums.org/showthread.php?t=65879&highlight=libXm.so.3)

---

### Post by greatgoo on 2006-03-27
> Of course it will say that, you have to launch any Unix/Linux executable not in an existing path with "./" in front of it, for example:
Code:

greatgoo@lnnw081:/opt/ibm/iSeriesAccess/bin$ ./ibm5250 lnn400

will probably give you the same result as using the full path.

Thanks for that.  I am new to linux and still coming up to speed.  You are correct in that the result was the same.

I find I have libxp6  6.8.2-1ubuntul already installed.  Is the other a more current version?  I googled for libxm.so.3 and found a patch for that file group.  Expanding that patch I see the same files that I already have installed.

David Davis

---

### Post by dcstar on 2006-03-28
[QUOTE=greatgoo]Thanks for that.  I am new to linux and still coming up to speed.  You are correct in that the result was the same.

I find I have libxp6  6.8.2-1ubuntul already installed.  Is the other a more current version?  I googled for libxm.so.3 and found a patch for that file group.  Expanding that patch I see the same files that I already have installed.

David Davis[/QUOTE]
You should probably do a search for that lib file, and it is possible you will have to make a link to it in the particular directory your application expects it to be in.

You have to be aware that programs compiled for non-Ubuntu (or Debian) environments may not work straight away because of issues like different default directories etc.

---

### Post by kanna1620 on 2007-01-30
> **dcstar said:**
> You should probably do a search for that lib file, and it is possible you will have to make a link to it in the particular directory your application expects it to be in.

You have to be aware that programs compiled for non-Ubuntu (or Debian) environments may not work straight away because of issues like different default directories etc.
I downloaded the mplayer and i run it from the terminal but it says that failed to fine WIN 32 codecs directory ...
And in my system there is no "make" command where can i get it?
I am using Ubuntu 6.06.
Thanks for help.

---

### Post by taurus on 2007-01-30
Media:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

GCC/make:
```
sudo aptitude update
sudo aptitude install build-essential
```

---

