---
title: "Can't compile a file in terminal"
date: 2009-01-24
forum: General Help
---

### Post by E-Cecilia on 2009-01-24
When trying to compile the newest Pidgin version, I got this back:

[I][B](...)-laptop:~/Desktop/pidgin-2.5.4$ ./configure
bash: ./configure: No such file or directory[/B][/I]

I'm lost, what am I doing wrong? :(

---

### Post by cariboo on 2009-01-24
Is there a compelling reason to compile pidgin, when it is installed by default? Is there a configure file in the directory that the pigin source is located in?

Jim

---

### Post by oldos2er on 2009-01-24
Pidgin 2.5.4 is available from getdeb.net, if you don't really want to compile it.

---

### Post by Wartender on 2009-01-24
you could always try making a ./configure folder in your home directory
wait never mind i read it wrong, i don't know

---

### Post by E-Cecilia on 2009-01-24
> **cariboo907 said:**
> Is there a compelling reason to compile pidgin, when it is installed by default? Is there a configure file in the directory that the pigin source is located in?

Jim

I use Gutsy since it's the one that works the best for me. Gutsy comes with Pidgin 2.2.1 (an older version) and lately I've been having issues with transferring files to my contacts. I thought that upgrading it would fix the bug/problem but I found that there's no deb package yet for the newest Pidgin version, so compiling is the only option... and that's how I ended up here.

---

### Post by mikjp on 2009-01-24
Is the package build-essential installed?

mikko

---

### Post by kevdog on 2009-01-25
Here:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by mb_webguy on 2009-01-25
Well, this seems like an obvious question, but is there a file called "configure" in the directory you're in?  If not... well, there's your problem.  Can you post a file listing of the ~/Desktop/pidgin-2.5.4 directory?

Also, if you're not experienced with compiling software, you should read [this page]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by E-Cecilia on 2009-01-25
> **mb_webguy said:**
> Well, this seems like an obvious question, but is there a file called "configure" in the directory you're in?  If not... well, there's your problem.  Can you post a file listing of the ~/Desktop/pidgin-2.5.4 directory?

Also, if you're not experienced with compiling software, you should read [this page]("https://help.ubuntu.com/community/CompilingEasyHowTo").

I know now that I was missing some basic packages. I will follow the instructions from the page you suggested, thanks. ;)
There's one thing I haven't figured out yet: is it normal that I can't send files on Pidgin? I can't send nor receive files and I don't know why.

---

### Post by adamlau on 2009-01-26
No issues with sending/receiving from 2.5.2 to 2.5.4. Be wary that 'checkinstall' has known upstream bugs that have not yet been fixed (workaround is --force-overwrite for most dpkg related issues). Pidgin is one of those applications in which 'checkinstall' has failed to install and build a .deb out of for me. Though kevdog recommends 'make install' over 'checkinstall', community docs push 'checkinstall' over 'make install'. My take? I prefer to use 'make install' unless make 'uninstall' is not available.

---

### Post by kevdog on 2009-01-26
I spoke with the pidgin developers on freednode #pidgin.  They laughed at checkinstall.  Although that was probably not very polite, they revealed real problems with the checkinstall method and preferred the simple make install method.  They read over my How-To and suggested various improvements in the process where-ever possible.  I can't say its Pidgin developer approved, but its pretty darn close!

---

