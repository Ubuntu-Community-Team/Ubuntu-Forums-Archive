---
title: "Checkout JGR,  a Java GUI for R"
date: 2007-04-27
forum: Education &amp; Science
---

### Post by ahmatti on 2007-04-27
I have read in the forums that people are having trouble in running JGR a GUI for R in Ubuntu. I just thought to post that I got working in Feisty without any problems. I am only studying R, but so far JGR is my favourite interface for it :)

The **JGR** home page [http://rosuda.org/JGR/index.shtml](http://rosuda.org/JGR/index.shtml).

It has many nice features like 

Integrated editor with
    * Syntax highlighting
    * Autocompletion
    * Direct command transfer

Integrated multi tabbed help system 
'Type-on' spreadsheet
 Console with autocompletion
Object browser featuring
    * Tabbed object view
    * Model comparison
    * Drag & Drop

Direct 'Open' dialog for simple dataset loading

Here is what I did to install in Feisty:

[B]First I installed sun-java5-jdk with synaptic, (java6-jdk didnt' work with JGR for some reason?).
[/B]
After installing java configured R:

```
$sudo R CMD javareconf
``` 

Then I started R (as sudo) and run:

```
install.packages("JGR",dep=TRUE)
library(JGR)
JGR()
```

---

### Post by raja on 2007-04-29
Thanks for that. 
An initial attempt to install JGR had failed and I had given up. Following your instructions, I was able to do it this time. I am still not sure if this is significantly better than running R from the terminal or from emacs, but it is good to be able to try it too.

---

### Post by raja on 2007-05-01
Does anyone have it working in edgy?

---

### Post by Lise on 2007-05-01
I tried it out with feisty and I got this
```

> install.packages("JGR",dep=TRUE)
Warning in install.packages("JGR", dep = TRUE) : 
         argument 'lib' is missing: using /usr/local/lib/R/site-library
--- Please select a CRAN mirror for use in this session ---
Loading Tcl/Tk interface ... done
Error: subscript out of bounds
In addition: There were 11 warnings (use warnings() to see them)
> library(JGR)
Error in library(JGR) : there is no package called 'JGR'
> JGR()
Error: could not find function "JGR"
> 


```

and this are the warnings I got
```

> warnings()
Warning messages:
1: Line starting '<html> ...' is malformed!
2: Line starting '<head> ...' is malformed!
3: Line starting '<meta content="text/ ...' is malformed!
4: Line starting '</head> ...' is malformed!
5: Line starting '<style> ...' is malformed!
6: Line starting 'body { ...' is malformed!
7: Line starting '} ...' is malformed!
8: Line starting '</style> ...' is malformed!
9: Line starting '<body> ...' is malformed!
10: Line starting '</body> ...' is malformed!
11: Line starting '</html> ...' is malformed!

```

---

### Post by raja on 2007-05-01
Looks like you could not connect to a mirror and download the package at all. I dont know why though. Did you run R as sudo?

---

### Post by ahmatti on 2007-05-02
> **raja said:**
> Does anyone have it working in edgy?

I had it also working in Edgy with the R packages from CRAN repos.

---

### Post by ahmatti on 2007-05-02
Hi Lise,
Do you see the Tcl/Tk interface prompting for a mirror? I am no expert in this, but I guess you could try running R with sudo R -gui tk and then running the code install to JGR and if doesn't work try installing JGR and its depencies using the packages menu.

---

### Post by Lise on 2007-05-02
> **ahmatti said:**
> Hi Lise,
Do you see the Tcl/Tk interface prompting for a mirror? I am no expert in this, but I guess you could try running R with sudo R -gui tk and then running the code install to JGR and if doesn't work try installing JGR and its depencies using the packages menu.

I did that  and I got this in tk-R

```

The downloaded packages are in
	/tmp/RtmpRCocTb/downloaded_packages
Warning messages:
1: installation of package 'rJava' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
2: installation of package 'JavaGD' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
3: installation of package 'iplots' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
> 

```

if I do install packages from cran, I got this in the terminal
```

ERROR: configuration failed for package 'rJava'
** Removing '/usr/local/lib/R/site-library/rJava'
* Installing *source* package 'iplots' ...
** R
** inst
** preparing package for lazy loading
Error: package 'rJava' required by 'iplots' could not be found
Execution halted
ERROR: lazy loading failed for package 'iplots'
** Removing '/usr/local/lib/R/site-library/iplots'
* Installing *source* package 'iplots' ...
** R
** inst
** preparing package for lazy loading
Error: package 'rJava' required by 'iplots' could not be found
Execution halted
ERROR: lazy loading failed for package 'iplots'
** Removing '/usr/local/lib/R/site-library/iplots'

```

---

### Post by raja on 2007-05-02
> **ahmatti said:**
> I had it also working in Edgy with the R packages from CRAN repos.

Was it with sun-java5-jdk or with java-6 ? I am having problems getting it to work in edgy.

---

### Post by ahmatti on 2007-05-02
> **raja said:**
> Was it with sun-java5-jdk or with java-6 ? I am having problems getting it to work in edgy.

If I recall correctly it was with JDK6? I am not sure though since I have already upgraded to feisty...

---

### Post by ahmatti on 2007-05-02
> **Lise said:**
> I did that  and I got this in tk-R

```

The downloaded packages are in
	/tmp/RtmpRCocTb/downloaded_packages
Warning messages:
1: installation of package 'rJava' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
2: installation of package 'JavaGD' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
3: installation of package 'iplots' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
> 

```


Did you run ```
$sudo R CMD javareconf
```? What's your output for that?

---

### Post by Lise on 2007-05-03
I installed JGR succesfully now.
Probably it was a bad internet connection, a few hours later I downloaded the packages whithout any problems
Thanks for the support

---

### Post by ahmatti on 2007-05-03
Happy to help! Glad that you got it working :)

---

### Post by David Valentine on 2007-05-08
I got JGR working for the first time ever (for me).  I'm on feisty, and the critical thing is that the Sun's JDK 6 must be installed in order for rJava to work, which in turn is needed by JGR.  The original poster may want to update the "howto" to ensure that folks following it don't fall into the same trap I did.

---

### Post by raja on 2007-05-08
> **David Valentine said:**
> I got JGR working for the first time ever (for me).  I'm on feisty, and the critical thing is that the Sun's JDK 6 must be installed in order for rJava to work, which in turn is needed by JGR.  The original poster may want to update the "howto" to ensure that folks following it don't fall into the same trap I did.

I am not so sure of that. I followed the advice and managed to get JGR working with JDK 5. In another machine with edgy, I am still unable to get JGR working with JDK 6 or JDK 5. I cant figure out what the problem is actually.

---

### Post by David Valentine on 2007-05-08
> I am not so sure of that. I followed the advice and managed to get JGR working with JDK 5.Right, I should have been clearer:  the important thing was the JDK part, which on my machine is 6.  I couldn't get  rJava (hence JGR) working at all with just the JRE; rJava apparently requires the JDK.  That's what I was suggesting should be in the original HowTo.

UPDATE:  I guess I missed the JDK reference in the original HowTo.  D'Oh! :P

---

### Post by ahmatti on 2007-05-09
> **David Valentine said:**
> 
UPDATE:  I guess I missed the JDK reference in the original HowTo.  D'Oh! :P

I just made it boldface so it's harder to miss :) Glad that people are getting JGR workin'!

---

### Post by eggroid on 2007-05-11
I've tried installing and running JGR with Java 5 and 6.  In both cases it starts with out error, but the java window labeled "console" is completely blank.

Any ideas?

---

### Post by raja on 2007-05-15
I am still trying to get JGR to work on my edgy machine. I installed sun-java6-jdk, ran update-alternatives and even tried setting JAVA_HOME. Still rJava and iPlots do not install without error. Any ideas anyone ? 
```
raja@~> echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.00/
raja@~> sudo R CMD javareconf
Java interpreter : /usr/lib/jvm/java-6-sun-1.6.0.00//jre/bin/java
Java version     : 1.6.0
Java home path   : /usr/lib/jvm/java-6-sun-1.6.0.00/
Java compiler    : /usr/lib/jvm/java-6-sun-1.6.0.00//bin/javac
Java headers gen.: /usr/lib/jvm/java-6-sun-1.6.0.00//bin/javah
Java archive tool: /usr/lib/jvm/java-6-sun-1.6.0.00//bin/jar
Java library path: $(JAVA_HOME)jre/lib/i386/client:$(JAVA_HOME)jre/lib/i386:$(JAVA_HOME)jre/../lib/i386::/usr/java/packages/lib/i386:/lib:/usr/lib
JNI linker flags : -L$(JAVA_HOME)jre/lib/i386/client -L$(JAVA_HOME)jre/lib/i386 -L$(JAVA_HOME)jre/../lib/i386 -L -L/usr/java/packages/lib/i386 -L/lib -L/usr/lib -ljvm
JNI cpp flags    : -I/usr/lib/jvm/java-6-sun-1.6.0.00//include -I/usr/lib/jvm/java-6-sun-1.6.0.00//include/linux

Updating Java configuration in /etc/R
Done.

```

Thats my JAVA_HOME and output for R CMD javareconf.

---

### Post by David Valentine on 2007-05-16
On another Kubuntu 7.04 machine, my attempts to install rJava (thence JGR) failed with the error > C compiler cannot create executablesI found the solution to this [here]("http://article.gmane.org/gmane.comp.lang.r.rosuda.devel/185"):  install libc6-dev ```
sudo apt-get install libc6-dev
```After that, rJava and JGR installed without a hitch.  Whew!

---

### Post by Tart on 2007-07-21
Greetings Everybody,

This is my first week with Ubuntu and I have no prior linux experience whatsoever, and I would appreciate any help. 

I've been using R for about two years (windows version), and I just installed it in Ubuntu,  I used Tinn-R as my editor, but now I tried to installed JRG, 
It had lots of issues with java, after many install/uninstall/reinstall I finally was able to installed JGR.

It is currently istalled with java-5,  6-refused to work with "sudo R CMD javareconf" maybe I got the wrong Java, people seemes to use 6, I got it through Add/Remove in my "Applications" menue.

However, when I run JGR in R I get splash screen win jaguar, and white console and R tells me that there is a following error

/usr/share/themes/Glossy/gtk-2.0/gtkrc:35: error: lexical error or unexpected token, expected valid token

and I have absolutely no idea what it means. 
if i run update with JGR(update=TRUE), JGR completely refused to work, saying it will need different version of Java, so I expect that I do need 6, but then I cannot install JGR at all if I use 6.

Can anyone help me with this? 
Thanks

I found solution, the R i installed was older version and rJava package requires 2.5,

---

### Post by chris_77 on 2007-08-01
I have the same problem: an empty java windows named 'console' after typing in R
```

library(JGR)
JGR()
```
no matter if I use java 1.6 or 1.5. In both cases I have installed the jdk package.

I change the versions of java with:
```
sudo update-alternatives --config java
```

Has anybody found a solution?

---

### Post by krcabrer on 2007-08-05
Hi R and ubuntu users:

I try all the ways you suggest to compile and try to run
JGR on ubuntu feisty 64.
I compile R 2.5.1 version with --enable-R-shlib in
the ./configure command.

I use both java 1.5 and 1.6 with java 1.5, it compiles fine,
but when I run the code
```

JGR()

```

I obtain the following message:

> Error en file(con, "r") : no fue posible abrir la conexión
Además: Warning message:
no fue posible abrir el archivo '/usr/local/lib64/R/library/JGR/cont/run.in', motivo 'No existe el fichero ó directorio' in: file(con, "r") 

What am I doing wrong?

Is it better to use emacs if I want a equivalent to Tinn-R in
ubuntu linux?

If I like to use RKWard must I use KDE (I am
using gnome inteface).

If I like to compile RKWard should I install all the KDE libraries?

Thank you for your time and help.

Kenneth

---

### Post by Tart on 2007-08-05
I gave up on JGR, in the end I just couldn't make it work, no matter what I tried. 
I get following when I try to start it

[FONT="Courier New"]
Starting JGR ...
(You can use /usr/local/lib/R/site-library/JGR/scripts/run to start JGR directly)
> Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.
ICE default IO error handler doing an exit(), pid = 7307, errno = 0
[/FONT]
Nothing happens after that. 

And then I found Rkward, I did manage to install it. I use it on default ubuntu i.e. GNOME. 
I downloaded source files and compiled them manualy, it didn't work straight away, but someone on rkward forums suggested to do the following 
# apt-get build-dep rkward
and after that I was able to compile and install rkward on my machine. I don't run KDE, but there might be some libraries missing, because rkward gives some errors in terminal, when I start it, 

[FONT="Courier New"]
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81fe6d0 ): KAccel object already contains an action name "window_close"[/FONT]


but they don't seems to affect it. it still works and I really like it.
I hope this helps.

---

### Post by earlycj5 on 2007-08-06
> **krcabrer said:**
> Hi R and ubuntu users:

If I like to use RKWard must I use KDE (I am
using gnome inteface).

If I like to compile RKWard should I install all the KDE libraries?

Thank you for your time and help.

Kenneth

Yes, you'll need KDE libraries and some Fortran libraries to compile RKward, though as I recall it's in the repositories.

RKward is my preference.

---

### Post by dugh on 2007-08-12
For those new to R (like myself), I put up complete instructions of how to get R (the latest version) and JGR, etc. installed in Ubuntu Feisty:

[http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html](http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html)

It's a bit funny that none of the instructions out there even tell you the name of the R executable ("R").

---

### Post by abim on 2007-08-14
I try to install JGR packages on Ubuntu.  Some depedency librarys can't  be installed, i.e.: rJava, JavaGD, and iplots.  Error massages:

1: installation of package 'rJava' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
2: installation of package 'JavaGD' had non-zero exit status in: install.packages("JGR", dep = TRUE) 
3: installation of package 'iplots' had non-zero exit status in: install.packages("JGR", dep = TRUE) 

I check with command : library(), These libraries not listed.

Then, I download packages manually. But I can't install packages from local directory. I try this command line:
Install.Packages("rJava", lib="~/R/library/")
and
Install.Packages("rJava", lib.loc="~/R/library/")
I save download files in ~/R/library.
How to install these packages from local directory?
Thx.

---

### Post by abim on 2007-08-16
I try to install packages JGR in ubuntu.  I found an error massages:
> library(JGR)
Error: package 'rJava' 0.4-16 was found, but >= 0.5 is required by 'JGR'

Then I try to update package with command line :

> update.packages()
But rJava not updated.  

I download last version of rJava from [http://www.rforge.net/rJava/files/](http://www.rforge.net/rJava/files/).
How to update packages form local directory?

Thx.
[abim]

---

### Post by David Valentine on 2007-11-07
> **dugh said:**
> For those new to R (like myself), I put up complete instructions of how to get R (the latest version) and JGR, etc. installed in Ubuntu Feisty:

[http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html](http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html)

It's a bit funny that none of the instructions out there even tell you the name of the R executable ("R").Thank you for your work--that really helped!

---

### Post by sasquatch74 on 2007-11-18
HI all,
I was having trouble compiling JGR with the install.packages(:JGR", dep=TRUE) command until I installed gcc-4.2.  I had gcc-4.2-base, but apparently it was not enough.  Look for gcc-4.2 in Synaptic and install it and then try to install JGR again.  

Good luck!

Edit:  You might also try installing build-essential in Synaptic and retry installing JGR.  This was not included in a fresh Gutsy install.

---

### Post by laharrin on 2008-05-22
Does anyone have a launcher for JGR?

thanks

---

### Post by dugh on 2008-05-24
> **laharrin said:**
> Does anyone have a launcher for JGR?

thanks


No, but you can create one.  When you run JGR() from inside R, it will tell you where the JGR run script is.  It probably is at:
/usr/local/lib/R/site-library/JGR/scripts/run

Now you can add your own launcher.
Right click on the panel for example, and select "add to panel" then "custom application launcher" and paste the above path to run.

---

### Post by spamalot on 2008-06-02
Hi all,

I think have followed the guidelines (see below) but it did not work (bottom line : JavaJD could not be found)

Any suggestion, please?


$ sudo apt-get install sun-java6-jdk

$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-4.1
          3    /usr/bin/gij-4.2
          4    /usr/lib/jvm/java-gcj/jre/bin/java
 +        5    /usr/lib/jvm/java-7-icedtea/jre/bin/java

$sudo R CMD javareconf
Java interpreter : /usr/bin/java
Java version     : 1.6.0_03
Java home path   : /usr/lib/jvm/java-6-sun-1.6.0.03/jre
Java compiler    : /usr/bin/javac
Java headers gen.: /usr/bin/javah
Java archive tool: /usr/bin/jar
Java library path: $(JAVA_HOME)/lib/amd64/server:$(JAVA_HOME)/lib/amd64:$(JAVA_HOME)/../lib/amd64::/usr/java/packages/lib/amd64:/lib:/usr/lib
JNI linker flags : -L$(JAVA_HOME)/lib/amd64/server -L$(JAVA_HOME)/lib/amd64 -L$(JAVA_HOME)/../lib/amd64 -L -L/usr/java/packages/lib/amd64 -L/lib -L/usr/lib -ljvm
JNI cpp flags    : -I/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../include -I/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../include/linux

Updating Java configuration in /etc/R
Done.

$ sudo R

R version 2.5.1 (2007-06-27)
Copyright (C) 2007 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> install.packages('JGR', dep=TRUE)
Warning in install.packages("JGR", dep = TRUE) : 
         argument 'lib' is missing: using '/usr/local/lib/R/site-library'
--- Please select a CRAN mirror for use in this session ---
Loading Tcl/Tk interface ... done
also installing the dependency ‘JavaGD’

trying URL 'http://lib.stat.cmu.edu/R/CRAN/src/contrib/JavaGD_0.5-1.tar.gz'
Content type 'application/x-gzip' length 86505 bytes
opened URL
==================================================
downloaded 84Kb

trying URL 'http://lib.stat.cmu.edu/R/CRAN/src/contrib/JGR_1.5-18.tar.gz'
Content type 'application/x-gzip' length 426244 bytes
opened URL
==================================================
downloaded 416Kb

* Installing *source* package 'JavaGD' ...
checking for gcc... gcc-4.2 -std=gnu99
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc-4.2 -std=gnu99 accepts -g... yes
checking for gcc-4.2 -std=gnu99 option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc-4.2 -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for string.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking return type of signal handlers... void
checking for memset... yes
checking for mkdir... yes
checking for rmdir... yes
checking for select... yes
checking for socket... yes
checking Java support in R... present:
interpreter : '/usr/bin/java'
cpp flags   : '-I/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../include -I/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../include/linux'
java libs   : '-L/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64/server -L/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64 -L/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../lib/amd64 -L -L/usr/java/packages/lib/amd64 -L/lib -L/usr/lib -ljvm'
checking whether JNI programs can be compiled... yes
configure: creating ./config.status
config.status: creating src/Makevars
config.status: creating R/zzz.R
config.status: creating src/config.h
** libs
gcc-4.2 -std=gnu99 -I/usr/share/R/include -I/usr/share/R/include     -I/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../include -I/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../include/linux -Iinclude -fpic  -g -O2 -c javaGD.c -o javaGD.o
In file included from javaGD.h:12,
                 from javaGD.c:23:
/usr/share/R/include/R_ext/GraphicsEngine.h:150: error: expected specifier-qualifier-list before ‘NewDevDesc’
/usr/share/R/include/R_ext/GraphicsEngine.h:224: error: expected ‘)’ before ‘*’ token
/usr/share/R/include/R_ext/GraphicsEngine.h:231: error: expected declaration specifiers or ‘...’ before ‘NewDevDesc’
javaGD.c: In function ‘Rf_addJavaGDDevice’:
javaGD.c:215: warning: implicit declaration of function ‘GEcreateDevDesc’
javaGD.c:215: warning: assignment makes pointer from integer without a cast
javaGD.c: In function ‘reloadJavaGD’:
javaGD.c:233: error: ‘GEDevDesc’ has no member named ‘dev’
javaGD.c: In function ‘javaGDobjectCall’:
javaGD.c:252: error: ‘GEDevDesc’ has no member named ‘dev’
javaGD.c: In function ‘javaGDresize’:
javaGD.c:269: error: ‘GEDevDesc’ has no member named ‘dev’
javaGD.c: In function ‘javaGDgetSize’:
javaGD.c:307: error: ‘GEDevDesc’ has no member named ‘dev’
make: *** [javaGD.o] Error 1
chmod: cannot access `/usr/local/lib/R/site-library/JavaGD/libs/*': No such file or directory
ERROR: compilation failed for package 'JavaGD'
** Removing '/usr/local/lib/R/site-library/JavaGD'
* Installing *source* package 'JGR' ...
** R
** inst
** help
 >>> Building/Updating help pages for package 'JGR'
     Formats: text html latex example 
  jgr.addMenu                       text    html    latex   example
  jgr.addMenuItem                   text    html    latex   example
  jgr.addMenuSeperator              text    html    latex   example
  supplements                       text    html    latex
** building package indices ...
* DONE (JGR)

The downloaded packages are in
        /tmp/RtmpfnAtvi/downloaded_packages
Warning message:
installation of package 'JavaGD' had non-zero exit status in: install.packages("JGR", dep = TRUE) 

>library(JGR)
Loading required package: rJava
Error: package 'JavaGD' required by 'JGR' could not be found

---

### Post by bryncoles on 2008-06-06
cant help you with jgr im afraid, but i personally like R commander. its in the repos, which makes it nice and easy to install. just search for Rcmdr. then boot r ('R' in the terminal), and type ```
library(Rcmdr)
``` to start the program. its not pretty, but it gets the job done, and you can still type in / see R syntax, so you can still learn the programming language of R!

---

### Post by GreenLinux@R on 2008-06-06
# INSTALL R, JAVA6, JGR, 

####  in terminal 
### [http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html](http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html)

  gpg --keyserver subkeys.pgp.net --recv-key E2A11821
  gpg -a --export E2A11821 | sudo apt-key add -

## get the sources.list file, 
 sudo gedit /etc/apt/sources.list

## in the pop sources.list file, at the bottom add

deb [http://cran.cnr.berkeley.edu/bin/linux/ubuntu](http://cran.cnr.berkeley.edu/bin/linux/ubuntu) hardy/

## e.g., using [http://cran.cnr.berkeley.edu/](http://cran.cnr.berkeley.edu/)
#click Linux to access Index of /bin/linux  select  ubuntu  to see the file 
# structure.
# use the closest mirror site to you. I used berkeley's R-cran though.
 
## save and clos sources.list back to terminal to insall R 
## [http://rosuda.org/JGR/linux.shtml](http://rosuda.org/JGR/linux.shtml)

sudo apt-get update
sudo apt-get install r-base-dev r-recommended 

#  I run and installed the r-base after "the recommended" following 
#  [http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html](http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html) 

sudo apt-get install r-base r-base-dev

# in the terminal  run R  to see 
# you can run some old code to have fun but DONT INSTALL JGR!! install java # first

R 

# type 
quit()
# quit R without saving . now java

# in terminal type 

sudo apt-get update
sudo apt-get install sun-java6-jdk  # [http://rosuda.org/JGR/linux.shtml](http://rosuda.org/JGR/linux.shtml)

# RUN IF YOU HAVE ANOTHER JAVA INSTALLED  
sudo update-java-alternatives -s java-1.6.0-sun 

## RUN NOW, THIS 
sudo R CMD javareconf

# IF EVERYTHING FUN, NO ERROR MESSAGE 
# DO INSTALL JGR 

install.packages("JGR",dep=TRUE)

## type these commands in R:

library(JGR)
JGR()

# YOU WILL SEE A JAVA CONSOL POP WINDOW, ENJOY JGR-ING.

---

### Post by GreenLinux@R on 2008-06-06
ok, I might be able to help you. 

go to System/Adminstration/Synaptic Package Manager/ 
 
you might be told that you have broken package. , in Synaptic Package Manager/Settings/Filters     in the pop window of Filters
highligh Broken on the left, and click Select All button on the right, then ok  

back to the Synaptic Package Manager window, click title S  on the right upmini-window. (do you see, S, Package, Installed Version ...., Yes, click the S ), you will see the packages have been ordered. Roll-down to find the broken java6 package. Then right click and marked it for update. you will notice a up-arrow appeas on the green block. now click Reload (the blue arrow). roll down to find the highlighted java6 , push the Apply (green ) button, java6 will be updated. 

now  run sudo R CMD javareconf again to see.

---

### Post by spamalot on 2008-06-07
Thanks, 

Although my problem was fixed I'd like to understand what you wrote for future reference. I lost you at "right upmini-window". What do you mean?

PS:
Thanks extends to all other answers. To anyone interested I also have a thread started at [http://www.nabble.com/forum/ViewPost.jtp?post=17622071&framed=y](http://www.nabble.com/forum/ViewPost.jtp?post=17622071&framed=y)

---

### Post by GreenLinux@R on 2008-06-09
Here is a way to install JGR into a folder you want it to be. 

## download 4 packages' source codes (.tar.gz files ) from R-CRAN  to local_folder  (mine is [COLOR="Red"]Desktop[/COLOR] )

rjava*.tar.gz,JavaGD*.tar.gz,iplots*.tar.gz and JGR*.tar.gz 

#  copy packages to the targeted lib you want JGR to be installed (mine is [COLOR="Navy"]/usr/lib/R/site-library[/COLOR] )


greenlinux4r@greenlinux4r-desktop:$ cd ~/Desttop
greenlinux4r@greenlinux4r-desktop:~/Desktop$ sudo cp rJava* /usr/lib/R/sit*greenlinux4r@greenlinux4r-desktop:~/Desktop$ sudo cp JavaGD* /usr/lib/R/sit*
greenlinux4r@greenlinux4r-desktop:~/Desktop$ sudo cp iplot* /usr/lib/R/sit*
greenlinux4r@greenlinux4r-desktop:~/Desktop$ sudo cp JGR* /usr/lib/R/sit*

##go to the folder you want to install JGR in:

greenlinux4r@greenlinux4r-desktop:~/Desktop$ cd /usr/lib/R/sit*
###

greenlinux4r@greenlinux4r-desktop:/usr/lib/R/site-library$ sudo R CMD INSTALL -l /usr/lib/R/site-library rJava*.tar.gz
greenlinux4r@greenlinux4r-desktop:/usr/lib/R/site-library$ sudo R CMD INSTALL -l /usr/lib/R/site-library JavaG*.tar.gz
greenlinux4r@greenlinux4r-desktop:/usr/lib/R/site-library$ sudo R CMD INSTALL -l /usr/lib/R/site-library iplo*.tar.gz
greenlinux4r@greenlinux4r-desktop:/usr/lib/R/site-library$ sudo R CMD INSTALL -l /usr/lib/R/site-library JGR*.tar.gz

So here you go.

---

### Post by GreenLinux@R on 2008-06-09
here you need to change permission to run JGR in some folder in root.  

see [http://ubuntuforums.org/showthread.php?t=275183](http://ubuntuforums.org/showthread.php?t=275183)

#### I did:

greenlinux4r@greenlinux4r-desktop:~$ sudo su

# after input my pswds 

root@greenlinux4r-desktop:/home/greenlinux4r# 

# run JGR outside R 

root@greenlinux4r-desktop:/home/greenlinux4r# /usr/lib/R/site-library/JGR/scripts/run

---

### Post by GreenLinux@R on 2008-06-09
here you need to change permission to run JGR in some folder in root.  

see [http://ubuntuforums.org/showthread.php?t=275183](http://ubuntuforums.org/showthread.php?t=275183)

I did:

greenlinux4r@greenlinux4r-desktop:~$ sudo su

 after input my pswds 

root@greenlinux4r-desktop:/home/greenlinux4r#

---

### Post by Draug on 2008-08-09
Hi,

After some manipulations with Java for other purposes than JGR, JGR don't work anymore (yes, I'm not very gifted). So I reconfigure Java (R CMD javareconf) after some difficulties and try to reinstall JGR. But when I do library(JGR) in R,
I have this message :

Le chargement a nécessité le package : rJava
Le chargement a nécessité le package : JavaGD
Le chargement a nécessité le package : iplots
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:89)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.Toolkit$2.run(Toolkit.java:836)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:828)
        at org.rosuda.util.Platform.initPlatform(Platform.java:39)
        at org.rosuda.iplots.Framework.<init>(Framework.java:49)
Error in .jnew("org/rosuda/iplots/Framework") :
  Failed to create object of class `org/rosuda/iplots/Framework'
De plus : Warning message:
In .jnew("org/rosuda/iplots/Framework") :
  NewObject("org/rosuda/iplots/Framework","()V",...) failed
Erreur : le package 'iplots' ne peut être chargé

[CENTER]________[/CENTER]

Even after reinstall iplots, I have the same thing
Someone has an idea to help me ?

Thanks

---

### Post by spamalot on 2008-09-23
I think i might have started this post...JGR finally worked fine for me until I upgraded to Ubuntu 8.04. Rather than go through more tinkering I looked for another editor and found rkward, which after install from synaptic manager launches w/o problem fromfrom menu>education>rkward.

---

### Post by LEDB612 on 2008-11-23
I'm new in this forum, but not too new in R, JGR and Ubuntu. I want to share my experience with this Java GUI. I installed it on my Ubuntu Server 8.10:

1. $ sudo apt-get install sun-java6-jdk sun-java6-jre

2. Download R 2.8 (the last modified version) at
[http://cran.at.r-project.org/bin/linux/ubuntu/intrepid/r-base-core_2.8.0-1intrepid0_i386.deb]("http://cran.at.r-project.org/bin/linux/ubuntu/intrepid/r-base-core_2.8.0-1intrepid0_i386.deb") and install the package.

3. $ sudo R CMD javareconf # enable Java support for R

4. Set Java version:
   
   $ sudo update-java-alternatives -a     # automatically

5. I got empty spaces in the log obtained in step 4:

Java interpreter : /usr/bin/java
Java version     : 1.6.0_10
Java home path   : /usr/lib/jvm/java-6-sun-1.6.0.10/jre
Java compiler    : /usr/bin/javac
Java headers gen.: /usr/bin/javah
Java archive tool: /usr/bin/jar
Java library path: $(JAVA_HOME)/lib/i386/client:$(JAVA_HOME)/lib/i386:$(JAVA_HOME)/../lib/i386::/usr/java/packages/lib/i386:/lib:/usr/lib
JNI linker flags : -L$(JAVA_HOME)/lib/i386/client -L$(JAVA_HOME)/lib/i386 -L$(JAVA_HOME)/../lib/i386 -L -L/usr/java/packages/lib/i386 -L/lib -L/usr/lib -ljvm
JNI cpp flags    :

# The "JNI cpp flags" line had no log, so I wrote:
   
    $ update-alternatives --config java   # and I chose option 2, "java-6-sun (I also had "openjdk")

6. $ R CMD javareconf   # again, and now I had the log completed :)

7. $ R    # to enter R (sorry if too obvious)
   
8. > install.packages("JGR",dep=TRUE)

8. > library(JGR)

9. > JGR()

10. /usr/local/lib/R/site-library/JGR/scripts/run  # the path to add a quick launcher.


Sorry for my English, and I hope this help someone...

---

### Post by zika on 2009-03-09
I get```
 WARNING: org.rosuda.JRI.Mutex was unlocked by other thread than locked! This may soon lead to a crash...
```after, finally, successful installation and adaptation ... what does this warning mean?

---

### Post by Huss on 2009-03-16
JGR is up and running.

I haven't played around with it yet, but I'll share my process so far.

1) I added the third party software source:

[http://cran.ms.unimelb.edu.au/bin/linux/ubuntu](http://cran.ms.unimelb.edu.au/bin/linux/ubuntu) intrepid/
I tried to add a varification key

2) Updated, and installed R

3) Took a long time to find out that the executable is 'R', 

4) Then ran:

Code:
sudo R CMD javareconf

(I didn't need to change my Java version from 6 to 5)

5) Ran R as super user (sudo)

4) Then ...
Code:

install.packages("JGR",dep=TRUE)
library(JGR)
JGR()

I found that I had to quit and reopen R to get 'library(JGR) to run smoothly.
To add a new launcher in the menu, add another item with this command: 
Code:
/usr/local/lib/R/site-library/JGR/scripts/run



Thanks for the excellent tute


Huss

---

### Post by mousecat on 2009-03-24
> **zika said:**
> I get```
 WARNING: org.rosuda.JRI.Mutex was unlocked by other thread than locked! This may soon lead to a crash...
```after, finally, successful installation and adaptation ... what does this warning mean?

I have got same warning as well...
anyone knows?

---

### Post by hugo_koopmans on 2011-05-17
This is an excellent post > thank you!

I only get this to work when sudo R ...

When opening with regular user i get:
> library(JGR)
Loading required package: rJava
Error : .onLoad failed in loadNamespace() for 'rJava', details:
  call: dyn.load(file, DLLpath = DLLpath, ...)
  error: unable to load shared object '/home/hugo/R/x86_64-pc-linux-gnu-library/2.13/rJava/libs/rJava.so':
  libjvm.so: kan gedeeld objectbestand niet openen: Bestand of map bestaat niet

giving up  if JGR guys want to be taken seriously they need to support linux better ...

tx

hugo

---

