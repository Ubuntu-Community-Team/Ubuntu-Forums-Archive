---
title: "Cedega CVS"
date: 2005-09-17
forum: Gaming &amp; Leisure
---

### Post by rj686 on 2005-09-17
I'm installing cedega cvs by following the instructions off this website :
[http://www.linux-gamers.net/modules...hp?articleid=45](http://www.linux-gamers.net/modules...hp?articleid=45)

newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/ryan/.WineCVS/sources/winex330/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/ryan/.WineCVS/sources/winex330/winex/tools'
make: *** [tools] Error 2

i get this error when trying to compile but the suggestion they give doesn't solve my problem

---

### Post by cutOff on 2005-09-17
Type the following before compiling

CC=gcc-3.4
export CC

Btw the link you provided is broken.

---

### Post by rj686 on 2005-09-17
[QUOTE=cutOff]Type the following before compiling

CC=gcc-3.4
export CC

Btw the link you provided is broken.[/QUOTE]
 [www.linux-gamers.net/modules/wfsection/article.php?articleid=45](www.linux-gamers.net/modules/wfsection/article.php?articleid=45)
i clicked on it on my computer and it works......hmmm......

thx for teh idea ill try it.

---

### Post by rj686 on 2005-09-17
ryan@ubuntu:~$ CC=gcc-3.4
ryan@ubuntu:~$ export CC
ryan@ubuntu:~$ sh WineCVS.sh













===============================================================================

Profile menu

Here you can download new profiles, upgrade existing
or run existing


  g) Get a profile from [http://winecvs.linux-gamers.net/WineCVS](http://winecvs.linux-gamers.net/WineCVS)
  c) Change command line action
  r) Run existing profile


=================WineCVS helpsystem (q will quit, b go back)=================

 Make your choice:

===============================================================================

List of profiles (b to go back):

0 ) cedega_head_userinstall
1 ) cvscedega_head_old
2 ) winex330
Enter choice:
0


Running Profile : cedega_head_userinstall
/home/ryan/.WineCVS/sources/cvscedega/wine



WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Compiling ...




--------- Error log - file /home/ryan/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: Entering directory `/home/ryan/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/unicode'make[1]: Entering directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools'
make[2]: Entering directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Entering directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Entering directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Entering directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make



Nope still a problem thx for the idea though.......

---

### Post by rj686 on 2005-09-18
sorry didn't mean to post....

---

### Post by Airpizza on 2005-09-18
try doing this:

sh WineCVS.sh refresh

---

### Post by rj686 on 2005-09-18
are u supposed to run this as root?


nope same error..........
NTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools/wr c'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/ryan/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2

---

### Post by xbaez on 2005-09-18
Do not follow that tutorial

Seach for "Frank's Corner" + Wine at GOogle

he will explain you how to install WineCVS from scratch

---

### Post by Struck on 2005-09-29
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)
it says >"for you to able to run cvscedega properly, you should first know where cvscedega is located on your system: try to locate cvscedega first, e.g. #locate cvscedega. then execute the command including the location of cvscedega, e.g. #/usr/local/cvscedega"
so I sreached for it >Computer>Search for file...
and found it in /home/andrea/bin so I typed /home/andrea/bin/cvscedega and this came out
root@pc12:/home/andrea # /home/andrea/bin/cvscedega
Enter Path for first Drive (C:) (Default: /root/.cvscedega/drive_c)
Newbies, press enter
Making fake C drive...
Edit the /root/.cvscedega/config file to fit your system
Installing registry...
Done
FuddFeatures:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:  cvscedega regapi <regfilename.reg>
Install .reg with regedit: cvscedega regedit [regfilename.reg]
Start winecfg:             cvscedega winecfg
Log to file:               cvscedega log <normal params>
eg:               cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console
Cedega CVS
Usage: /home/andrea/.WineCVS/installs/cvscedega/bin/wine [options] [--] program_name [arguments]
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

So ermm am I done? Have I succesfully Installed CVSCEdega?

I think not>.< caz this pc doesnt have Drive C/Drive D and my friend says he would have to partition thoseT___________________T meh, do I really need a drive c to completly install cvs cedega? He's as clueless bout ubuntu as I am>.<

---

