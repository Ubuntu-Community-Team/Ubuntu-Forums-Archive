---
title: "matlab-installation using wine"
date: 2006-05-31
forum: Education &amp; Science
---

### Post by u04f061 on 2006-05-31
i tried to install matlab 7 in ubuntu 5.10 using wine.matlab is very heavy software comes in two cds. 
something about installer
    on the cover of installer it is written 
          install commands
               1-on unix install
                2-on pcs setup.exe
i have seen that all the files are in zip format and they contribute the almost entire part of installer.from this i think that this is for both windows and unix.but i can't find any rpm or bin file in installer.
can i use this installer to install matlab on my pc without wine or other software?

my wine simulation result is below


ejaz@msiddique:~$ winecfg
ejaz@msiddique:~$ sudo wine /cdrom/setup.exe
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
java.lang.UnsatisfiedLinkError: no fontmanager in java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.font.NativeFontWrapper.<clinit>(Unknown Source)
        at sun.java2d.SunGraphicsEnvironment$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(Unknown Source)
        at sun.awt.Win32GraphicsEnvironment.<init>(Unknown Source)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at java.lang.Class.newInstance0(Unknown Source)
        at java.lang.Class.newInstance(Unknown Source)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(Unknown Source)
        at java.awt.Font.initializeFont(Unknown Source)
        at java.awt.Font.<init>(Unknown Source)
        at sun.awt.windows.WComponentPeer.<clinit>(Unknown Source)
        at java.awt.Component.initIDs(Native Method)
        at java.awt.Component.<clinit>(Unknown Source)
        at com.mathworks.installer.Installer.<clinit>(Installer.java:54)

can anybody fix it.
previously i have been using windows xp for this installer and now i have made my pc single boot with ubuntu only

---

### Post by meng on 2006-05-31
Is there a file called install? Not necessarily with any extension.

---

### Post by u04f061 on 2006-05-31
no there is no file with install but a file with name installer ini

can i install matlab with wine?
it opens matlab startup window but then an error message appears that says installer error:
error finding installer class
an exception occured while looking up for a class

i think it is java problem because it is trying to load java classes.should i install java development kit?

my wine says that it is six month old.can i upgrade this using apt-get so that this error may be minimized?

---

### Post by meng on 2006-05-31
I suspect that you are mistaken in this being a combined windows/unix version of Matlab. I don't believe there is such a thing. There are separate versions for Mac or Unix. But you could contact Mathworks and find out if you have a combination product.

On the winehq site, someone reported last month being unable to install the Windows version of Matlab using wine.

EDIT: forgot to mention, there are alternative open-source packages, for example, R statistical package.

---

### Post by u04f061 on 2006-05-31
to which these packages are alternate
matlab or wine?

---

### Post by meng on 2006-05-31
matlab, hence the reference to statistics.
[http://www.ubuntuforums.org/showthread.php?t=184343&highlight=matlab](http://www.ubuntuforums.org/showthread.php?t=184343&highlight=matlab)

---

### Post by Charlatat on 2006-05-31
there is a native linux version of Matlab available, but I believe the student version of it costs more than the Windows version...

---

### Post by u04f061 on 2006-05-31
what upeople think about matlab?
what are the functinalities of matlab?

i have checked octave and statistic in apt-get command to see their size.
u say that these are matlab for linux.don't confuse with my style of writing in post.
i donot want to hurt linux builders and i appreciate octave and statistic builders that they are making such useful softwares without any costin this world of materialism.i am specifying some functions of matlab so that i may find any alternative to it.plz tell me if octave and statistics provide these facilities. 

 matlab isnot just a software to plot graph and solve equations.it is cad for almost all engineers.being an electrical engineer i am listing some functions which normally i'll use or i use
1-it is  a programming language for parallel port intefacing
2-it supports all j2sdk version of java and swing libraries.i mean a class written in java is directly imported as if it is  a program of matlab.i think same would be for other languages also but i am java user
3-it provides simulink to combine mechanical engineering tools with electrical engineering tools(a computer based home industry)
4-it provides resources for telecom with such an extent that it is now treated as part of our course. i mean teachers give us lectures and presentations on how to use matlab.
5-a famous software for elctronics design is orcad capture(by [www.cadence.com)is](www.cadence.com)is) now providing a facility to export its designed circuits into matlab simulink

are these facilities in octave and statistic also?

---

### Post by KLineD on 2006-05-31
Matlab is much more than what u04f061 stated and his list is a very impressive array of features.

I'm an electronics engineer and the defacto standar in my university was (I think it still is) matlab. That fact alone makes almost all engineering students want to run matlab in whatever OS they use. I remember trying octave but it fall very short to the functionallity that matlab provides, not that I'm complaining, I think it's great to have an alternative but I also think that Octave can't compete (at least for now) with some of the features of matlab.

Anyway, I tried to get matlab 7 working with Wine but it was impossible. It has something to do with matlab using Java for the gui. I remember trying to install with the -nojvm or -nojava (I dont remember the switch) but it wouldn't install. I ended up getting a unix version and it installed well. It has some quirks, but you can search for "install matlab" here in the forums I posted some instructions to get it working in hoary I think.

---

### Post by meng on 2006-05-31
Thanks for providing details. I suspect that the opensource offerings will not suit you as well as matlab, but for more details look here.

[http://www.gnu.org/software/octave/doc/interpreter/](http://www.gnu.org/software/octave/doc/interpreter/)
[http://cran.r-project.org/](http://cran.r-project.org/)

In the end, if you need Matlab, ring up the Mathworks people and ask them for help. If you pay for a product you're entitled to support.

---

### Post by u04f061 on 2006-05-31
[QUOTE=meng]Thanks for providing details. I suspect that the opensource offerings will not suit you as well as matlab, but for more details look here.

[http://www.gnu.org/software/octave/doc/interpreter/](http://www.gnu.org/software/octave/doc/interpreter/)
[http://cran.r-project.org/](http://cran.r-project.org/)

In the end, if you need Matlab, ring up the Mathworks people and ask them for help. If you pay for a product you're entitled to support.[/QUOTE]

  sorry if u got hurt of mine.i've not said any word against octave , its developer or its
users.i have installed r-base but i typed command r-base in terminal it says no command exist.it is given below

ejaz@msiddique:~$  r-base
bash: r-base: command not found
ejaz@msiddique:~$ man r-base
No manual entry for r-base
ejaz@msiddique:~$ man r_base
No manual entry for r_base
ejaz@msiddique:~$ r_base
bash: r_base: command not found

i also have downloadedorcave 2.9 from orcave home but there is a problem with its
./configure

so now i am installing it from apt
plz post how to start r-base if u can ,also for stating command for orcave
 
thnx

---

### Post by meng on 2006-05-31
Command to start octave: octave
Command to start R: R
note it has to be upper case.

---

### Post by u04f061 on 2006-05-31
[QUOTE=KLineD]Matlab is much more than what u04f061 stated and his list is a very impressive array of features.

I'm an electronics engineer and the defacto standar in my university was (I think it still is) matlab. That fact alone makes almost all engineering students want to run matlab in whatever OS they use. I remember trying octave but it fall very short to the functionallity that matlab provides, not that I'm complaining, I think it's great to have an alternative but I also think that Octave can't compete (at least for now) with some of the features of matlab.

Anyway, I tried to get matlab 7 working with Wine but it was impossible. It has something to do with matlab using Java for the gui. I remember trying to install with the -nojvm or -nojava (I dont remember the switch) but it wouldn't install. I ended up getting a unix version and it installed well. It has some quirks, but you can search for "install matlab" here in the forums I posted some instructions to get it working in hoary I think.[/QUOTE]

can u give me the ls command for cdrom/matlab-cd in drive

i mean by inserting cd in cd rom and list of its files.my ls is below

ejaz@msiddique:/cdrom$ ls
archives     CD Covers      install_guide.pdf  KeyGen       readme.txt  utils
autorun.inf  help           java               license.txt  setup.exe
bin          installer.ini  jhelp              matinfo.enc  uninstall
ejaz@msiddique:/cdrom$
u hav'nt given the link to that forum.

plz tell me you got unix version with licence of windows version or purchased a new one?

---

### Post by u04f061 on 2006-05-31
[QUOTE=meng]Command to start octave: octave
Command to start R: R
note it has to be upper case.[/QUOTE]

i can't exit R.how to exit it

---

### Post by meng on 2006-05-31
The command is
q()
The manual is a must.

---

### Post by KLineD on 2006-05-31
[QUOTE=u04f061]can u give me the ls command for cdrom/matlab-cd in drive

i mean by inserting cd in cd rom and list of its files.my ls is below

ejaz@msiddique:/cdrom$ ls
archives     CD Covers      install_guide.pdf  KeyGen       readme.txt  utils
autorun.inf  help           java               license.txt  setup.exe
bin          installer.ini  jhelp              matinfo.enc  uninstall
ejaz@msiddique:/cdrom$
u hav'nt given the link to that forum.

plz tell me you got unix version with licence of windows version or purchased a new one?[/QUOTE]

The version I got is a unix version but I don't know if it's licence is a windows or unix licence. If by that you mean if I bought a Windows licence and then used with a unix matlab, then no. I got unix matlab from my university computer laboratory (since I needed it for some of my courses) and I'm sorry I can't give you a listing of the files, I don't know where's the CD ](*,) 

you can find detailed (but dated) instructions to installing matlab [here]("http://www.ubuntuforums.org/showthread.php?t=40997&highlight=matlab+installation+KLineD")

---

### Post by GDR! on 2007-03-01
Have you tried this solution, available on MathWorks forum?

[http://www.mathworks.com/support/solutions/data/1-11VD0Z.html?solution=1-11VD0Z](http://www.mathworks.com/support/solutions/data/1-11VD0Z.html?solution=1-11VD0Z)

---

### Post by FredrikN on 2007-03-03
I found this in the wiki: [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) I think I read it when I installed Matlab R14 student-something on my brothers laptop running Ubuntu 6.06.

Personally, I stick with C, Octave and Python at home and use Matlab over SSH or at the university when necessary.

---

