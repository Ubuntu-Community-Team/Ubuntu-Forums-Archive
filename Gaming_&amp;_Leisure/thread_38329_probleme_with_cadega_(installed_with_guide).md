---
title: "probleme with cadega (installed with guide)"
date: 2005-05-31
forum: Gaming &amp; Leisure
---

### Post by glasscleaner on 2005-05-31
i have follow the guide on linux-gamer.net to install cadega, after i successfuly run the  WineCVS.sh script to install. after i got this:

Installing launcher script ...
    Packing sourcetree...
All done ... CVS installed   **<---- successfully installed no?**

   Installed as: cvscedega  **<---- right?**
   Config path : <homedir>/.cvscedega

amphore@ubuntu:~$ cvscedega
bash: cvscedega: command not found

that was happend when i try to run it. (same as sudo)

cannot find any help on the forum about that. any idea?

thanks

---

### Post by foxy123 on 2005-05-31
I tried to install cvscedega several times both on SuSE and Ubuntu and never managed to make it work.

---

### Post by glasscleaner on 2005-05-31
im happy to know im not the only one...

since 2 day i shearch to find something to make working that crap :P

---

### Post by Protonz on 2005-07-25
I had this problem until I called the install script as root (via sudo). Then it creates the /usr/bin/cvscedega file that you can run as a regular user.

Still haven't been able to play any games though.

---

### Post by Tad030 on 2005-07-25
I was able to install cedega using point2play - however, I can't get any of my games to run either.  At this point, I'm very frustrated with cedega.  I'm hoping that I'm proven wrong however.   :-|

---

### Post by No6 on 2005-07-26
You will have problems with Cedega and the current Ubuntu. It is not Cedega's problem but the kernel 2.6.10 is not compatible with some parts of cedega, mainly copy protection, so most games won't install or run. This was only a problem in 2.6.9 and 2.6.10 and is fine in earlier and later kernels.

Currently I'm using Ubuntu on a machine I don't do gaming on and use Mandake / Mandriva for my gaming machine. Breezy is going to have 2.6.12 so this will be fine.

Not a fix, but an explanation.

You can of course try to upgrade your kernel... :-) !

---

### Post by mcmuffy on 2005-07-27
I just installed the new 4.4 version from .debs supplied on the site and it went in with no problems. I even managed to get world of warcraft running 1st try (although it does crash now and again).

---

### Post by IeU on 2005-09-06
yea . . .

i have followed that tutorial . . .
( [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45) )

and when i get to this part . . .
```


4. Configuration

We need a so called fake windows. The cvscedega-script will create it if we run it the first time:

$ cvscedega

cvscedega creates a configuration (~/.cvscedega) and a fake windows directory (~/.cvscedega/c_drive). It is possible to change the directory for the fake windows e.g.

```

it gives me a . . .

```

tuche@tuche:~$ cvscedega
bash: cvscedega: command not found
tuche@tuche:~$

```

what i found is that during the first step, cedega created a "bin" folder in my home/user
directory . . . and there, there is a cvscedega file . . .

going to the folder and typing ```
 sudo sh cvscedega 
```

will print me the following msg . . .

```

tuche@tuche:~/bin$ sudo sh cvscedega

FuddFeatures:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:  cvscedega regapi <regfilename.reg>
Install .reg with regedit: cvscedega regedit <regfilename.reg>
Log to file:               cvscedega log <normal params>
         eg:               cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console

Cedega CVS

Usage: /home/tuche/.WineCVS/installs/cvscedega/bin/wine [options] [--] program_name [arguments]
The -- has to be used if you specify arguments (of the program)

Options:
   --debugmsg name  Turn debugging-messages on or off
   --dll name       Enable or disable built-in DLLs
   --dosver x.xx    DOS version to imitate (e.g. 6.22)
                    Only valid with --winver win31
   --help,-h        Show this help message
   --managed        Allow the window manager to manage created windows
   --version,-v     Display the Wine version
   --winver         Version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
   --dt             Defer trace until Alt+F12
   --use-dos-cwd    Used to set the DOS current working directory for the process (needs a path)
   --cmdline        Specifies the application's command line
   --monitor-cdrom-eject        Activate monitoring of CD-ROM ejection requests
tuche@tuche:~/bin$

```

from now on . . . im a bit on how to follow/continue the tutorial . . .

---

### Post by Chrno on 2005-10-05
ok im trying the same guides as u guy but im stuck alredy :(
[PHP]
Now its time to come to the real stuff...

Change to the location where the WineCVS.sh is lying and start it with:
$ sh WineCVS.sh[/PHP]

this is where im stuck i don't know where my "WineCVS" is 

i have managed to build a "Wine cvs" but i heard Cedega is better so i wanna try it

---

