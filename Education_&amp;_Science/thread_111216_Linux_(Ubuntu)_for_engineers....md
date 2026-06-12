---
title: "Linux (Ubuntu) for engineers..."
date: 2006-01-01
forum: Education &amp; Science
---

### Post by neoflight on 2006-01-01
Hello people,

I was wondering whether its a good idea to have a good thread on using ubuntu for engineering applications. I learn that there are some discussions on using packages and all, but scattered. 

I am in grad school and from a horrible experience while writing thesis on xp, I've decided to make a shift. 
-Esp the word processor. I am slowly getting comfi with latex. 
-I've had trouble installing the student matlab version but managed to make it after reading some how-to's. 
- other applications i would love to try are
-- python, maxima (for maple?).

my school has redhat installed in the labs. but iam not comfortable with that.

what are y'all using for your engineering studies/work? such as 3d modelling? 
Any FEM (finite element analysis) software??

Do you think its a good idea to have a section for engineering applications here in this forum?

If that has already been taken care of then please redirect me and repost this appropriately..

thank you...

Neo

---

### Post by bernardfrancois on 2006-01-12
Im studying informatics engineer, so we're not using a lot of programs that have to do anything with other sciences than informatics.

But I **latex** is great for making a thesis. You can use **lyx** as a front-end.
You can use **dia** to make various diagrams (like electrical cuircuits).
The **[graphviz]("http://www.graphviz.org")** tools are great to make schemes fastly (you don't need to waste time on drawing or moving nodes since it calculates all node positions).

There are various other tools in the repositories under different categories: electronics, mathematics, science (make sure you have access to the 'universe' repositories).
For example, **chemtool** allows you to draw chemical structures.

---

### Post by Hairy_Palms on 2006-01-12
i know you can use blender for 3d modelling it works very well, im a studying electronic engineer but i use livewire inside wine for my circuit drawing.

---

### Post by leech on 2006-01-12
I just ran 'apt-cache search engineer' and it came up with quite a nice list.

```
atlc - Arbitrary Transmission Line Calculator
drawtiming - tool for documenting hardware designs through timing diagrams
ecos - Deeply embedded operating system
elfsh - The ELF shell
gipsc - IP Subnet Calculator for X
gpib-modules-source - kernel modules for various GPIB boards
htag - A tagline/.signature adder for email, news and FidoNet messages.
ipsc - IP Subnet Calculator for console
libalzabo-perl - Data modelling tool and RDBMS-OO mapper
libcoin20 - high-level 3D graphics kit - runtime
libcoin20-dev - high-level 3D graphics kit - development
libcoin20-doc - high-level 3D graphics kit - documentation
libcoin20-runtime - high-level 3D graphics kit - external data files
libelfsh0 - The ELF shell library
libelfsh0-dev - The ELF shell library
libgpib-bin - libgpib support applications and configuration
libgpib-perl - libgpib perl bindings
libgpib0 - C bindings for GPIB (IEEE 488) kernel driver -- headers
libgpib0-dev - C bindings for GPIB (IEEE 488) kernel driver -- headers
linsmith - a tool to generate Smith Charts
maria - reachability analyzer for Algebraic System Nets
php4-gpib - libgpib php bindings
proguard - java class file shrinker, optimizer, and obfuscator
python-gpib - libgpib python bindings (default package)
python-scipy - scientific tools for Python
python-scipy-core - low level utilities for scipy (default python version)
python2.3-gpib - libgpib Python 2.3 bindings
python2.3-scipy - scientific tools for Python 2.3
python2.3-scipy-core - low level utilities for scipy (for python 2.3)
python2.4-gpib - libgpib Python 2.4 bindings
python2.4-scipy - scientific tools for Python 2.4
python2.4-scipy-core - low level utilities for scipy (for python 2.4)
r-cran-fbasics - GNU R package for financial engineering -- fBasics
r-cran-fcalendar - GNU R package for financial engineering -- fCalendar
r-cran-fextremes - GNU R package for financial engineering -- fExtremes
r-cran-fmultivar - GNU R package for financial engineering -- fMultivar
r-cran-foptions - GNU R package for financial engineering -- fOptions
r-cran-fportfolio - GNU R package for financial engineering -- fPortfolio
r-cran-fseries - GNU R package for financial engineering -- fSeries
splat - analyze point-to-point terrestrial RF communication links
tcpreen - Simple TCP re-engineering tool
varkon - A CAD-system with parametric modelling
varkon-programmer-manual - Programmer manual for VARKONs mbs language
varkon-user-manual - User manual for VARKON
graphviz - rich set of graph drawing tools
libbcel-java - Analyze, create, and manipulate (binary) Java class files
libbcel-java-doc - Documentation for Byte Code Engineering Library (BCEL)
esix - PDP-8 Engineering and Scientific Interpreter eXtended
```

I'm ot an engineer nor going to school for it, but love looking at what sort of stuff is already in the repositories for all sorts of applications :D

Leech

---

### Post by Mr_Grieves on 2006-01-12
A friend of mine studies engineering at the University, and thier school runs matlab on Linux.. it's Java.. but, it seems that it's not working exactly as good as in Windows.

---

### Post by Spie on 2006-01-12
- I use texmaker for LaTeX. It's the somewhat same as Kile but without the qt-libraries.
- I use Matlab. It runs very well on Linux. An open-source effort is Scilab.
- Dia is nice, but it is nothing compared to AutoCad.
- Fluent on Linux is used by the University for CFD.

Overall, Linux makes my life (Almost MSc) a lot easier.

EDIT[line 3] - I mean: QCad is nice, but doesn't have the level of AutoCad, yet.

---

### Post by bernardfrancois on 2006-01-12
[QUOTE=Spie]- I use texmaker for LaTeX. It's the somewhat same as Kile but without the qt-libraries.
- I use Matlab. It runs very well on Linux. An open-source effort is Scilab.
- Dia is nice, but it is nothing compared to AutoCad.
- Fluent on Linux is used by the University for CFD.
[/QUOTE]

I'll try texmaker.

Dia is not really a program in the same category as Autocad. You won't use autocad to draw diagrams, and you won't use Dia to draw (for example) a 2d view of some object.

I just checked out the site of fluent, it seems to be an interesting program.

---

### Post by neoflight on 2006-01-12
[QUOTE=bernardfrancois]I'll try texmaker.

Dia is not really a program in the same category as Autocad. You won't use autocad to draw diagrams, and you won't use Dia to draw (for example) a 2d view of some object.

I just checked out the site of fluent, it seems to be an interesting program.[/QUOTE]

i tried texmaker.. but i have had problems linking the same to my latex installation. so i tried gedit and it works ok but i need to compile using latex command and view dvi using xdvi ... no fancy help tho... i liked kile and it had so many problems from linking, and so many errors i cant even finish reading...

i still use matlab...i run that with gui interface at the cluster using ssh.thats much faster and so i wasted my matlab student version so to speak.

i use ansys too...but no opensource to match that....i run it at the clusted too...gui... with ssh -X... 

its good to know what kind of applications and solutions engineers/science/other students use as a part of their studies?

any idea what free program available for 3d drawing...

thanks:smile:

---

### Post by gunksta on 2006-01-12
I don't do engineering, but I do work with math a lot in terms of research.  If you don't have it install qalculate.  It is the greatest "basic" calculator I have ever seen.  I use this thing all the time for quick views of data sets, since it can insert .csv files into graphviz for me, and give me a graph is less than time than I can open up gnome-terminal.  Seriously, this is a powerful tool.  It's hardly matlab, but it doesn't take as long to learn either! You also don't feel silly using it for multiplication.  :D 

I agree, comparing DIA to Autocad doesn't seem like a fiar comparison.  They aren't even the same category of tool.  I enojoy looking at the page [www.gnomefiles.org](www.gnomefiles.org).  They have some stuff on math and engineering.

I think latex is great, and lyx is certainly a wonderful application.  But, it sucks if you are going to  have to give you paper to someone who doesn't use latex too.  It's just not a very portable file format.  True, latex does work on every OS on earth, but how many people have the software to do so.  I'm sorry, but it seems to me to be just as easy to let OOo handle my bibliography information.  And, I use the paragraph styles, so I can get most of the benefits of latex, and email it to my professor easily.

---

### Post by Hitchhiker427 on 2006-01-12
My university uses a program called Mentor Graphics in our Unix labs.  Does anyone have any experience running this in Ubuntu?  It's circuit design/simulation software.  I've tried out a few, and the only one I could get to work right is Oregano, however, this doesn't seem to be very feature-filled, but it'll do for now.

Can anyone recommend any other quality engineering software?  I mean, I can always search the repositories, but that doesn't guarantee that the software's any good.

---

### Post by htoerrin on 2006-01-13
Just a couple of programs not mentioned yet:

octave: A matlab clone. I have never used Matlab, so I can't compare, but octave seemes quite useful.

qcad: Seemes to be a quite reasonable 2d cad program. 

eagle: ([www.cadsoftusa.com](www.cadsoftusa.com)) Electronic schematics and layout. Limited free version.

---

### Post by Peter76 on 2006-01-13
Have a look at wings3d for ( duh :-) 3d modelling. It's in the repo's

---

### Post by cb951303 on 2006-01-13
I reccomend [www.octave.org](www.octave.org) which is a matlab like dev environment by GNU. It's a very complete package.

---

### Post by cotcot on 2006-01-13
If you look for an CAD program "QCAD" will do. I have checked its compatibilty with Autocad and that is quite good.
I am currently learning Blender3D. Nice tool for 3D. 
I do not really feel the need for a separate engineers section (although I am a chemical engineer).

---

### Post by scpike on 2006-01-13
Maple runs natively under linux, its pretty cool

---

### Post by cb951303 on 2006-01-13
blender3d or wings3d are not good for engineering. A 3d CAD would be more efficient ( maybe at least with some basic physics simulations )
Unfortunatly QCAD is 2d only

---

### Post by Hitchhiker427 on 2006-01-13
yeah, that is one thing missing.  I haven't been able to find a decent Autodesk Inventor or Solidworks clone yet.  Until then, I'll just dual-boot and use the real things in Windows.

---

### Post by apolyak on 2006-01-13
look at:
- bc - An arbitrary precision calculator language. Uses C-like language. Search Google for bc, there are a lot functions written for bc. There is a bug in if - else statement: ad ' \ ' after if closing '}'
if (x < i){
 do something;
}\   /* add \ after } */
else{
do something;
}

- gnuplot
- SwitcherCad III -> is a high performance Spice III simulator, schematic capture and waveform viewer with enhancements and models for easing the simulation. [http://www.linear.com/company/software.jsp](http://www.linear.com/company/software.jsp). Runs under wine very well.

---

### Post by ReverseEngineered on 2006-01-14
I'm a fourth-year studying Electrical Engineer, and there are several programs I use.

Latex is quite common, even among our entire university.  Rather than distribute the actual source itself, many people convert the dvi's to pdf's, either directly (pdflatex) or using a simple script (dvips and ps2pdf).  Our University has made this standard practice for the entire faculty (including giving workshops on how to do it) and the result has been clear, standardize, universally-accessible tests and assignments; definitely a nice touch.

I use Unix versions of both the commercial Matlab and Maple.  Aside from their horrible interfaces (as far as I know both use Motif), they function almost identically to their Windows counterparts.  There are also open source equivalents of both (Octave and Maxima).  I have yet to try Maxima.  Octave is nice, but doesn't quite have the same functionality as Matlab (several of the more basic toolboxes either have parts missing or with limited functionality, uses gnuplot for output so can't perform many of the same system-design methods like root locus very well).

Dia works very well for diagrams (such as UML in computer science).  Only problems I've ever had is intermixing .dia files between Linux and Cygwin versions (font sizes exploded sporadically).  I have yet to see a good Linux equivalent of AutoCAD, though my searches have been limited.  Anybody comment on this?

My biggest stumbling block as been in the actual electronics arena.  EDA (schematic capture, simulation, PCB layouts, etc) is severely limited.  gEDA is in the works, but it's no where near Multisim or CircuitMaker.  From what I know CircuitMaker will work under WINE, but last I checked both old (Electronics Workbench) and new (Multisim) versions of the Multisim products don't work properly (load, but the UI has fatal bugs).  Eagle is a great program (though REALLY weird to learn at first), but the limited free version is almost useless for anything but the most simple projects, and don't even bother trying to pirate it.

All in all, most anything you need for Engineering can be found under Linux (after all, many scientists write their in-house tools in Unix), though it may not be as refined and as powerful as the commercial Windows offerings.  I suppose the old adage is still true--you get what you pay for.

---

### Post by bernardfrancois on 2006-01-14
[QUOTE=ReverseEngineered]Dia works very well for diagrams (such as UML in computer science).[/QUOTE]

For UML diagrams, you can also use **umbrello**.
I used it to draw an ERD for a database modelling project (though I had to add symbols for primary keys using the gimp).

[QUOTE=apolyak]- SwitcherCad III -> is a high performance Spice III simulator, schematic capture and waveform viewer with enhancements and models for easing the simulation. [http://www.linear.com/company/software.jsp](http://www.linear.com/company/software.jsp). Runs under wine very well.[/QUOTE]

There are other spice simulators as well. Spice started as a free unix program, later several GUI's were made (there are commercial ones an non-commercial ones, for both unix and windows). I didn't search very far for a good one, since I have only seen the basics of electronics.

---

### Post by Showan on 2006-01-21
hi

is there any chance to run Inventor/autocad/MDT with a Windows Emulator?
Not regarding the fact that some functions need Excell :???: 

thanks

---

### Post by bernardfrancois on 2006-01-22
If you really need to run a windows application, I would advice you to run it under windows, if you already have a windows license.

Otherwise, you can check the site of wine. There's a database with information about many windows programs (and how they run emulated using wine).

But this is out of the scope of this thread, maybe there's a thread specific about autocad on these forums, or you could open one (also, more people will give you usefull replies there since the title of the thread will be more to the point).

---

### Post by adamkat on 2006-01-26
I backported the latest taxmaker but am not able to set the paths of each indevidual program.
I am a linux beginner so please explain in detail.
Thanks

---

### Post by neoflight on 2006-01-26
[QUOTE=adamkat]I backported the latest taxmaker but am not able to set the paths of each indevidual program.
I am a linux beginner so please explain in detail.
Thanks[/QUOTE]


aaaaaahhh ! .... i had the same problem again...

just locate where the latex is installed... and thats the path u need to set in there. everything else seems ok. 

which latex are u planning to use? tetex2, tetex3 or texlive2005?

---

### Post by neoflight on 2006-01-26
[QUOTE=adamkat]I backported the latest taxmaker but am not able to set the paths of each indevidual program.
I am a linux beginner so please explain in detail.
Thanks[/QUOTE]


aaaaaahhh ! .... i had the same problem....

just locate where the latex is installed... and thats the path u need to set in there. everything else seems ok. 

which latex are u planning to use? tetex2, tetex3 or texlive2005?

---

### Post by bernardfrancois on 2006-01-27
[QUOTE=adamkat]I backported the latest taxmaker but am not able to set the paths of each indevidual program.
I am a linux beginner so please explain in detail.
Thanks[/QUOTE]
Please don't do double posting. You already posted the same question at [http://www.ubuntuforums.org/showthread.php?t=121368](http://www.ubuntuforums.org/showthread.php?t=121368) .

But you mentioned a program here that I'm going to try out :)

But please continue the discussion about your specific problem in the other thread.

---

### Post by phen on 2006-02-02
hello y'all!

Please add all scientific/engineering programs you know/like to
[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)
we try to get a comprehensive list of available software! it is really helpful, but QCad wasn't there. I found the tip in this thread...

cheers,

kai

---

### Post by bernardfrancois on 2006-02-03
nice job!

---

### Post by lyly on 2006-02-03
For myself I use:
- **LateX** with **emacs/auctex** not very wisiwig but evince (document viewer of ubuntu) still crash a lot...
- **gnuplot** for data rendering. I used it in commande line but I have see **plotdrop** (not in repo) which seems to be a promising front-end. Unfortunatenly the last version doesnt have an ubuntu package.
- **regexxer** to manage the text result of experiment.
- **octave** can fit to replace mathlab, but I dont know any good front end to it, and command line is not very friendly for everydays work...
- **wxmaxima** a gnome front end to maxima for litteral calculation
- **inkscape** to make the schemas and figures
- **dia** for flowchart etc...
- I dont use it but statical calculation the **R** programm is good (I learned it during my studies) 

I miss:
- a **CAD** program with 3D design and plan making of mechanical parts
- a **PCB/Mask** designer
- an small and easy **3D drawing** program. Everybody say Blender is great, but I feel it is too complicated. I dont need any raytracing feature or big texture rendenring..., but sometime I like too have a little 3D fig just to explain something
- a **video editing** program. Kino is in ubuntu, but I cannot open my experiment film with it... and I am not sure the conversion to another format dont do any loss of data...
- a program to **draw molecules**

---

### Post by jefferbean on 2006-03-05
Octave works great, it is virtually the same as Matlab.  Make sure to get the octave-forge package as well.  It contains 500 additional functions not in the main distro.  The one I found most useful was print(), which allows you to save your plots and graphs as variable graphics files including .png.

---

### Post by htoerrin on 2006-03-06
For video editing you might concider cinelerra, [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

---

### Post by neoflight on 2006-03-15
there is a discussion on this forum on making a specific group for university related stuff...

[http://ubuntuforums.org/showthread.php?t=142557](http://ubuntuforums.org/showthread.php?t=142557)

raise your voice and a group like that should help searching stuff and getting replies really easy....

---

### Post by cg_linux on 2006-08-31
--------------------------------------------------------------------------------

Hello...
I need instructions to install and to run Fluent 6.2 in Ubuntu 6.06 for 64-bit(AMD Athlon).

---

### Post by tower_ on 2007-07-13
How to install ANSYS V10 (or ANSYS V9) on a Linux 32-bit box with Ubuntu Feisty or Debian Sid:

rtfm then install and follow the instructions from Ansys. At the end of the install process there are some modifications needed:

create an empty file license.log (because it is missing) in 

/.../ansys/ansys_inc/shared_files/licensing                  
(replace "/.../" with your real install path)

then
sudo chmod 755 /.../ansys/ansys_inc/shared_files/licensing/license.log

then copy your license.dat (if there is no license.dat already)
cp license.dat /.../ansys/ansys_inc/shared_files/licensing

and
sudo chmod 755 /.../ansys/ansys_inc/shared_files/licensing/license.dat

now start your licensemanager: /.../shared_files/licensing/lic_admin/anslic_admin.sh

try to start ansys now:
/.../ansys/ansys_inc/v100/ansys/bin/launcher100

when ansys starts it will fail because a link to your relevant libgcc_s.so.1 is needed:

cd /.../ansys_inc/v100/ansys/syslib/linia32 
mv libgcc_s.so.1 libgcc_s.so.1.old 
ln -s /lib/libgcc_s.so.1 . 

now your are ready to go :-)


*additional ansys "nice to have" modifications and tuning*

make a desktop entry:
create and edit the file "ANSYS.desktop"

sudo gedit /usr/share/applications/ANSYS.desktop

then insert the following text into the file "ANSYS.desktop"

[Desktop Entry]
Name=ANSYS
Comment=ANSYS lancher
Exec=/.../ansys_inc/v100/ansys/bin/launcher100
Icon=/.../ansys_inc/v100/ansys/bin/ansysLogo16x16.gif
Terminal=false
Type=Application
Categories=Application;Office; 

save and exit gedit

to start the ansys flexlm license server when you boot your box:

cd /.../ansys_inc/shared_files/licensing/linia32
sudo cat boot_ansflex >>/etc/init.d/rc.local 

to change the ansys fonts:
start ansys then go to

 MenuCtrls --> Font selection --> item   

go through and change all items as you needed
watch also your entrys in the file /home/user/.ansys/ansys10.0/ansys10.0.reg

and/or:
start ansys by 
/.../ansys/ansys_inc/v100/ansys/bin/launcher100 -fontsize 11

if you have dual processors:
sudo gedit /../ansys_inc/v100/ansys/apdl/start100.ans
and insert the following line at the end of the file "start100.ans":

/config,nproc,2

---

### Post by tower_ on 2007-07-13
:guitar:

---

### Post by tower_ on 2007-07-21
> **cg_linux said:**
> --------------------------------------------------------------------------------

Hello...
I need instructions to install and to run Fluent 6.2 in Ubuntu 6.06 for 64-bit(AMD Athlon).

what you need exactly?
what problem you noticed?
i installed fluent on debian 32-bit without any problems.

---

### Post by ricardo.slacker on 2007-07-24
I've done a lot of scientific/mathematical programming, and i've found scilab to be a nice clone of matlab, but a very popular alternative to those kind of programs is python. It's used by [nasa]("http://www.python.org/Quotes.html"), and actually used in some high [performance]("http://www.cs.utk.edu/~luszczek/pubs/plw-200605.pdf") physics applications.
Python is a great choice because it has a natural syntax for engineers, for example the following statement
works with pylab
```
x=arange(begin,end,increment)
y=sin(x)
plot(x,y)
```
and will produce an nice looking interactive graph (much prettier than gnuplot).
its that simple to do math in the interactive interpretor, and it scales well. Have you ever tried to connect to a databse in matlab? I'm told it's not easy. In python, the code only takes a few lines.
In matlab's defense, open source doesn't really have anything that can compete with simulink.

I've expiremented with octave and found it somewhat confusing. I would say that for symbolic calculations I would still fall back to maple or even a ti-89 calculator.

---

### Post by ioakost on 2007-07-25
Hello everyboby!

could somebody show me how to install ANSYS_11 on UBUNTU/KUBUNTU 64bit linux?

I appreciate and waiting for your answer!

---

### Post by monoj on 2007-07-26
Hello
I'm trying to make to work Ansys V10 on Feisty (Kubuntu), I followed your explain (Tower_ ) but when I start it by /ansys/ansys_inc/v100/ansys/bin/launcher100 and choice some possibility to run I have this error :

```
Segmentation fault (core dumped)
Press enter to exit
```

I tried all to resolve this problem.
Can somebody help me, please?


Thanks a lot.

Bye

---

### Post by Thingymebob on 2007-07-30
Medusa4 Personal from [http://www.cad-schroer.com/]("http://www.cad-schroer.com/") looks pretty good, Ihaven't yet got it to run under my ubuntu install, but have in slack and gentoo. Although the interface is a little weird it certainly is full featured cad.

---

### Post by neoflight on 2007-07-31
that link is not working for me !!!:confused:

---

### Post by dmontalvao on 2007-10-03
Hi! I have the same problem with Ansys 11. Also, with Labview 7.1. I heard with later versions of Labview, 8+, it might work, although Ubuntu is not a supported version. We will hv Labview 8.5, so as soon as I get it, I'll try it with Ubuntu 7.04 or 7.10 (if already released).

Anyway, atm, I would like to install Ansys 11... If someone has found a solution to the "Segmentation Fault (Core Dumped)" problem, please help! Maybe Ubuntu is not a supported distribution? OMG!

Thanks!

Oh..., Tower, I am no able to find libcc_s.so.1 in /.../ansys_inc/v110/ansys/syslib/linia32. Since I don't know anything about this, with Ansys11, should I make a link to other library? Which one would it be? You can call me a noob if you like, but please help. hehe. :)

Quoting Tower:

"when ansys starts it will fail because a link to your relevant libgcc_s.so.1 is needed:

cd /.../ansys_inc/v100/ansys/syslib/linia32
mv libgcc_s.so.1 libgcc_s.so.1.old
ln -s /lib/libgcc_s.so.1 ."

---

### Post by dmontalvao on 2007-10-04
OMG!!! I feel so stupid!!!!

After all, everything is ok... The problem is I was choosing as "Simulation Environment" on the launcher "Ansys Workbench" instead of "Ansys". Now I can run Ansys Mechanical on Ubuntu Feisty! Woo hoo!

Well, I just posted this here because I think others might be stuck with this aswell.

(I still don't understand why I can't run Ansys Workbench, but, what the heck!)

Cheers!

---

### Post by Steph_fr_37 on 2007-10-21
Hello,
do you finally find something  to run workbench, i have the same problem, i can run ansys but i obtain a nice core dumped with WB. I use a french feisty.
thank you

---

### Post by drmatty on 2007-10-21
What are people using for creating/testing circuit diagrams?

When people say that Matlab doesn't run as well on Linux, vs Win, what are the limitations? I'm ony about 75% Ubuntu, and want to complete the switch, but I'm afraid to lose my Matlab. Are people using real-time workshop?

---

### Post by doogan18 on 2007-10-23
I'd also love to know what people are using for circuit design and analysis because I am a computer systems engineer student atm.  My labs involve using an FPGA, and it looks like we're supposed to use Quartis which is similar to LogicWorks, but I haven't been able to use either of these.  I've been searching for some time, and I'd like to see if Ubuntu users have some tools similar to either of those editors.

~Joe

---

### Post by arkara on 2007-10-30
i am on my 3 rd year studing mechanical engineering here in greece.
we have used matlab and fortran so far and  there is a linux version for matlab and i am doing just great. because my university is very fond on open source. i was given the matlab linux version and i am doing my job great.
i also used koctave and was very very good.

---

### Post by dmontalvao on 2007-10-31
Scilab is also an excelent clone of Matlab.

---

### Post by drmatty on 2007-11-01
Any open source programs available for circuit diagrams?

---

### Post by Whiffle on 2007-11-01
I use gEDA for circuit diagrams (the actual program that comes with that suite is called gschem), works pretty well.

I can't believe nobody has mentioned Kile.  Its a frontend for LaTeX and works extremely well.

---

### Post by drmatty on 2007-11-03
Thanks, I'll check geda.

---

### Post by mocha on 2007-11-03
For circuit diagrams, SPICE, etc, you can use Qucs, Oregano, LTspice (in Wine), geda, or KiCad.  All work very well.  LTspice is probably the easiest SPICE program I have found.  It's closed source but freeware and runs perfect in Wine.

---

### Post by macro182 on 2007-11-14
Hello!

I've installed Ansys 10, but I have some problem with license file, because I don't managed to understand what's correct hostname and hostid that I would insert in license.dat

For hostname I write "hostname" in shell, but for hostid?

Thanks a lot!

---

### Post by Slingshot on 2007-11-15
3D Parametric solid modeling. Alas, this is one area Windows has it all over any other OS. Linux options seem to be high end costly packages like Pro/Engineer or cheap programs with a poorly designed interface.

Some to keep your eye on are Medusa4, GraphiteOne and VariCAD. Still all rough compared to the likes of Solidworks or Inventor.

---

### Post by sr_eivel on 2008-01-24
A good tool for studying Finite Elements is FreeFEM++. It's a linear 2D FEM application that is just great if you're learning the FEM basics. Fast and nice. Very intuitive coding language in which you, basicly, give the processo the weak form of the PDE and the domain and it solves ti. (Magic!) There is a 3d version currently in development... haven't used it.
Wouldn't recomend it for serious studies. Nonlinear stuff can be done but requires more serious programming. Anyway it's sufficiently modular for one to experiment different things.
Give it a try.

---

### Post by sfabel on 2008-01-25
Maybe not the right thread, but there is a Engineering Linxu Distribution out there, called [CAELinux]("http://www.caelinux.com"). I haven't tried it myself, but there seems to a couple of applications supporting 3D CAD as well.

I personally use Kile or OOo for word processing, MATLAB2007a for numerical stuff and Maxima for symbolic math.

There also was a question further up whether MATLAB is feature complete on Linux. So far, I haven't been able to find one feature that would not work under Linux (unless it is a bug). I have used real-time workshop under Linux before.

Cheers,
Stephan

---

### Post by woody_green on 2008-02-05
> **drmatty said:**
> When people say that Matlab doesn't run as well on Linux, vs Win, what are the limitations? I'm ony about 75% Ubuntu, and want to complete the switch, but I'm afraid to lose my Matlab. Are people using real-time workshop?


At school, we use Linux, that is why we use Kicad and Hades (a Java-based editor) for circuit diagrams and logic gate-related design respectively. We also use Octave as a substitute for MatLab.I don't know the Linux equivfalent for AutoCAD but I think there's one out there.

---

### Post by pawn on 2008-02-05
Hye there,its nice to be here.
I study mechanical engineering,degree level.
1 question I will always love to ask:
Will there be CAD,CAM or CAE softwares such as Dassault System Catia,Ansys,Matlab, or AutoCAD on ubuntu? I found it is really hard to find the software as good as those in linux(they can run smoothly on Windows).using Wine seems to not be very helpful.
Just asking,coz i need to boot from ubuntu to windows when i'm doing my assignments and projects...really messy...

Another question,will ubuntu(or may be other distros) come out with these type of softwares,and becoming open source?

Just asking,coz i really believe in the power of open source,huhu

---

### Post by AlexVader on 2008-02-18
Hi Tower, 
I am experiencing the same problem, when i start the fluent script in Ubuntu Gutsy 7.10, it states something about an incomplete string, the gui doesn't even show up...

It happens with Fluent 6.2.16...

can you give me any hint pls...?

Thanks in advance

Alex

---

### Post by amd-64 on 2008-02-19
> **pawn said:**
> Hye there,its nice to be here.
I study mechanical engineering,degree level.
1 question I will always love to ask:
Will there be CAD,CAM or CAE softwares such as Dassault System Catia,Ansys,Matlab, or AutoCAD on ubuntu? I found it is really hard to find the software as good as those in linux(they can run smoothly on Windows).using Wine seems to not be very helpful.
Just asking,coz i need to boot from ubuntu to windows when i'm doing my assignments and projects...really messy...

Another question,will ubuntu(or may be other distros) come out with these type of softwares,and becoming open source?

Just asking,coz i really believe in the power of open source,huhu

I stopped dual booting completely. The softwares you mention will run on Virtualbox. It is virtually transparent, provided you are not low on RAM.

---

### Post by jjgomera on 2008-02-19
anybody knows some free alternatives to Chemcad, hysys or Aspen Plus, chemical engineering process simulation?

I can use chemcad with wine without problems, but i'd like to find free alternative

---

### Post by Mark Bolton on 2008-03-27
What I a looking for is a **process control program** to interface a PC via IO devices such as paralell port buffers and sound cards to run simple process machinery. 

The sort of thing I want to do is monitor and record temperatures and switch on pumps and heaters in response to Logical flowcharts I want to implement. 

My background is in electronics but I have been out of the field since machine programming on language 8086 uP. I am fairly new to linux and need to figure out where to start. 

I dont really want to tinker with things and am more interested in getting the machines going and testing. 

THX in anticipation

Mark

---

### Post by sfabel on 2008-03-28
Hi folks,

MATLAB was developed for UNIX before it was developed for Windows so it should run fine (and it does). I used to use Kile for LaTeX editing, now I use XEmacs - I like the features of their preview within the editor - it is almost WYSIWYM.

I also use Eclipse for all the programming efforts I undertake. Sometimes I use Octave or wxMaxima.

There apparently is a full-fledged Linux distribution aimed at Engineering Applications: [CAELinux]("http://www.caelinux.com/CMS/")

I haven't tried that one out, though.

Cheers,
Stephan

---

### Post by rajendra on 2008-03-30
Hi!

I'm a mechanical engineer. In my office, I use SolidWorks on Windows XP Professional. At home, I tried installing GraphiteOne on Ubuntu 7.10, but ran into problems. (I'm a newbie at Linux).

I think linux needs a good 3D solid modelling software, and I miss it sorely.

---

### Post by Battalion on 2008-03-31
> **sfabel said:**
> Hi folks,

MATLAB was developed for UNIX before it was developed for Windows so it should run fine (and it does). I used to use Kile for LaTeX editing, now I use XEmacs - I like the features of their preview within the editor - it is almost WYSIWYM.

I also use Eclipse for all the programming efforts I undertake. Sometimes I use Octave or wxMaxima.

There apparently is a full-fledged Linux distribution aimed at Engineering Applications: [CAELinux]("http://www.caelinux.com/CMS/")

I haven't tried that one out, though.

Cheers,
Stephan

Hi, i'm a mechanical engineer and the two things i can't live without is MATLAB and solidworks (or solidedge).  I haven't been able to find out how to install matlab on ubuntu and i'm sure there's no 3d modelling software that can do what i need.  These limitations keep me from making a full conversion into linux.

Also an FEA (FEM) modelling and analysis program would be nice.  In windows XP i use MSC.patran and other parts of it.  

Someone shed some light on me please

---

### Post by ad_267 on 2008-04-01
For installing MATLAB have a look here:
[https://wiki.ubuntu.com/MATLAB](https://wiki.ubuntu.com/MATLAB)

There's also the open source Octave available as an alternative.

For 3D modelling, PTC Pro/Engineer is available for Linux.

ANSYS can be used for finite element analysis. Their website says they require SuSE or Redhat so they might not support Ubuntu officially but there shouldn't be any problem getting the software to work. [http://www.ansys.com/services/ansys-requirements110.htm](http://www.ansys.com/services/ansys-requirements110.htm)

If you want something open source and free for FEM have a look at Code_Aster [http://www.code-aster.org/](http://www.code-aster.org/), [http://en.wikipedia.org/wiki/Code_Aster](http://en.wikipedia.org/wiki/Code_Aster)
The brochure looks good: [http://www.code-aster.org/V2/spip.php?rubrique18](http://www.code-aster.org/V2/spip.php?rubrique18)

Code_Aster can be used in conjunction with SALOME: [http://www.salome-platform.org/home/presentation/overview/](http://www.salome-platform.org/home/presentation/overview/)

---

### Post by qgfreire on 2008-05-10
Hello,
I'm doing chemical engineering modelling and simulation. I'm trying to be M$ independent but I've a difficulty;
- Excell Solver add-in. 
None of the spreadsheets (OO.. Gnu.. Gno.. )I know have something like it.
What a pity.


Good NEWS!
OOffice spreadsheet have now a solver. It works now with non-linear problems. It's not so good as M$ but it's working ;-)
My thanks to developers!!

---

### Post by jjgomera on 2008-05-10
> **qgfreire said:**
> Hello,
I'm doing chemical engineering modelling and simulation. I'm trying to be M$ independent but I've a difficulty;
- Excell Solver add-in. 
None of the spreadsheets (OO.. Gnu.. Gno.. )I know have something like it.
What a pity.
How much have you looked for?

In OO. is in Tools/Solver oh, oh, oh, what a surprise:lolflag:, and work exactly than excel's solver
Although in 7.10 there are a [bug]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/135776"), so in 7.10 solver can't be used at all

---

### Post by lrx on 2008-05-18
I have used scilab for my studies and can recommend it as an alternative to matlab. Many of the commands is the same.
Still want to try python.

Tnx

---

### Post by hardyn on 2008-05-18
> **rajendra said:**
> Hi!

I'm a mechanical engineer. In my office, I use SolidWorks on Windows XP Professional. At home, I tried installing GraphiteOne on Ubuntu 7.10, but ran into problems. (I'm a newbie at Linux).

I think linux needs a good 3D solid modelling software, and I miss it sorely.

There are a few good attempts for linux, but right now, IMO there are no usable linux based 3d (or even 2d) cad applications of the open source verity.  i *think* pro-e still has a linux verison, catia has a unix version, but of course is pay-fer software.

alebre, i really think has a shot with linux, but has chosen to ignore it.

there are lots of graphic engines out there, even open source ones, but putting together a good OSS parametric cad solution would be a such an enormous task im not sure anybody would want to take it on.  It would be an interesting project, but i don't think i have the mathematics background to contribute even a little. 

I am currently dual booting, and i think that it is going to stay like that for some time.

---

### Post by neoflight on 2008-05-22
> **hardyn said:**
> There are a few good attempts for linux, but right now, IMO there are no usable linux based 3d (or even 2d) cad applications of the open source verity.  i *think* pro-e still has a linux verison, catia has a unix version, but of course is pay-fer software.

alebre, i really think has a shot with linux, but has chosen to ignore it.

there are lots of graphic engines out there, even open source ones, but putting together a good OSS parametric cad solution would be a such an enormous task im not sure anybody would want to take it on.  It would be an interesting project, but i don't think i have the mathematics background to contribute even a little. 

I am currently dual booting, and i think that it is going to stay like that for some time.

i agree...i have to switch back and forth to access my other OS to get the 3D application. There were several projects a couple of years ago...they all seem stagnant now...

---

### Post by qgfreire on 2008-06-20
> **jjgomera said:**
> How much have you looked for?

In OO. is in Tools/Solver oh, oh, oh, what a surprise:lolflag:, and work exactly than excel's solver
Although in 7.10 there are a [bug]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/135776"), so in 7.10 solver can't be used at all

Hello, thank you. I noticed that in my last actualization of OO. So I even have made a new comment to my last post.
Thank you again.

---

### Post by parhyang on 2008-06-30
You're looking for FEM just like me, may i litle share something i have succesfully installed [FTOOL]("http://www.tecgraf.puc-rio.br/ftool/ftooleng.html") in HH8.04  it's great for 2d frame structural analysis. I make a bit of try too with 3d FEM [CalculiX]("www.calculix.de"), just moving the executable file to /usr/local/bin/ and it' will be working properly.

---

### Post by Michael Sams on 2008-08-31
Hi,

i am using Ubuntu 8.04 and I want to use ANSYS v11 - but it do not wanna work! :confused:

After the installation and correct set-up of the license manager the launcher starts normally, but if I try to run any application of ANSYS Classic I get this error message: 

> 
 *** FATAL ***
  Invalid language value= English             
  (specified language directory does not exist)

 *** NOTE ***
  USAGE: ansys.e110  [-d device name] [-j job name] [-m scratch memory(mb)]
                     [-f [off|nogrow]] [-b list|nolist]
                     [-s read|noread] [-g] [-db database(mb)]
                     [-p product] [-l language]
                     [-dtm] [-np #] [-cci cciopt]
                     [-vta] [-dvt] [-dxs]
                     [-ser port] [-mpi native|mpich|mpich_sh|hpmpi|msmpi|sgimpt|alt]
                     [-dir working_directory] [-cli IP address]


-if I want to start Workbench, the whole system freezes!

I appreciate every suggestion!!! :KS

Best Regards
Michael

---

### Post by Frenske on 2008-09-08
You better contact Ansys or look in their forums about that! I have used it (long time ago) on Linux without any problems.

---

### Post by korri on 2009-06-01
Hello all.
I try install Ansys11 on ubuntu 9.
But have some error

```
~/Ansys$ ./INSTALL
copying necessary files to /tmp/ans_install_tmp2079/
cd: 307: can't cd to /tmp/ans_install_tmp2079/tcl
gzip: /tmp/ans_install_tmp2079/tcl/linem64t.tar.gz: No such file or directory
./INSTALL: 371: /tmp/ans_install_tmp2079/common/startTcl.sh: not found
```

Can anyone help me?

---

### Post by sumedhmumbai on 2009-06-12
I am looking to convert few engg. Labs to linux

i am looking at linux alternates for following software to run on Ubuntu 9.04

pl guide with some installation tutorial /notes u have

Rational Rose
Flash dev IDE
HTML DEV ide
Matlab
MASAM/TASAM
TINA PRO
P-spice
MICROWIND
XYlink
modelsim
Prolog

Any guides to install rational rose , Oracle 10g ,Matlab on ubuntu 9.04

---

### Post by mechanicaldesign on 2009-08-02
Hello to everibody,

Can somebody help me with some steps necessary to install ANSYS 11 ?

Thank you in advance.

Bye

---

### Post by mechanicaldesign on 2009-08-21
Hello to everibody,

I install the ANSYS sofware on my computer, and I have a problem when I want to launch the program. Here I will put the error:

[B][I][COLOR=Red]/usr/ansys_inc/v110/ansys/bin/linia32/ansys.e110: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory.

Press <Enter> to close this window.[/COLOR][/I][/B]

What representin this mising file?

Thank you in advance for your answer, support and sugestion.

Best regards.

---

### Post by jjgomera on 2009-08-21
try to install openmotif support, the package libmotif3

---

### Post by mechanicaldesign on 2009-08-22
Hello [jjgomera]("http://ubuntuforums.org/member.php?u=346679"),

Be more explicit please, because I'm new in user in Linux , and I dont now what representing that folder or files.

Thank you in advance for your support and your advice.

Best regards.:confused:

---

### Post by mechanicaldesign on 2009-08-22
Hello to everibody,

I installing on my computer ANSYS 11, to Linux Ubuntu 9.04. All install it was ok, but when I want to launch the ANSYS from ANSYS launcher apear the problem:

[B][I][COLOR=Red]/usr/ansys_inc/v110/ansys/bin/linia32/ansys.e110: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory.

Press <Enter> to close this window.[/COLOR][/I][/B]

I try to find file which missing ***[COLOR=Red]libXm.so.3 [/COLOR]***[COLOR=Red][COLOR=Black]but I dont find him. What must be done ?

Where is the problem?

Thank you in advance for your support.

Best regards.

P.S. I waiting your answer much early is possible.
[/COLOR][/COLOR]

---

### Post by mechanicaldesign on 2009-08-22
Hello to everibody,

I installing on my computer ANSYS 11, to Linux Ubuntu 9.04. All install it was ok, but when I want to launch the ANSYS from ANSYS launcher apear the problem:

[B][I][COLOR=Red]/usr/ansys_inc/v110/ansys/bin/linia32/ansys.e110: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory.

Press <Enter> to close this window.[/COLOR][/I][/B]

I try to find file which missing ***[COLOR=Red]libXm.so.3 [/COLOR]***[COLOR=Red][COLOR=Black]but I dont find him. What must be done ?

Where is the problem?

Thank you in advance for your support.

Best regards.

P.S. I waiting your answer much early is possible.
[/COLOR][/COLOR]
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7828519") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7828519")

---

### Post by Whiffle on 2009-08-22
I believe you need the package "libmotif3", which provides libXm.so.3

---

### Post by jjgomera on 2009-08-22
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

use synaptic to install packages, in your case you need libmotif3, i think

---

### Post by mechanicaldesign on 2009-08-23
Hello to everibody,

Your advice it was very useful for me, because I installing ANSYS 11 on Ubuntu 9.04.

From launch panel of Ansys I started Ansys Classic. But I encountered a new problem:
when I want to launch from launcher panel or terminal comand the Workbench module, appear the next  proposition : [COLOR=Red][B]

Segmentation fault
Press <Enter> to close this window

[/B][COLOR=Black]What means that, what connection, link, or file missing?[/COLOR][/COLOR]

Thank in advance for your advice.

Best regards.

---

### Post by mechanicaldesign on 2009-08-27
Hello to everibody,

Finaly, I install on my computer ANSYS 11 on Ubuntu 9.04.
 From ANSYS Launch panel I can launch all aplication, exception ANSYS Worckbench.
Both with this, I can launch from terminal ANSYS CFX. :popcorn:
I can't run yet ICEM CFD and ANSYS Autodyn, but this softwares in this moment not representing an priority for me.

If somebody think that my version of ANSYS is much good (without error), please tell me to put here a link from where I download my version.

Thank you very much for your support and I waiting your sugestion refering to launch ANSYS Worckbench.

Best regards.=D>

---

### Post by mechanicaldesign on 2009-10-14
Hi to everibody,

First of all I want to thanks to all for your advice. It was very precisely and exactly advice, in a manner in which I installed at my home on both computer the Ubuntu9.04

In this moment I need your advice inthe next problem: on virtual machine (vmware) from Ubuntu, I installed CentOS5.3. Here I encountered the next problem:

1. I cannot see the DVD-rom DVD-writer ? You can help me to see the DVD's from intermedium of CentOS (installed on virtual machine) ?

2. I cannot see all partitions from my hard disk? You can help me to see all partitions  from intermedium of CentOS (installed on virtual machine) ?

I'm sorry becuase I specify here other version of linux (CentOS5.3), but the users from forum of CentOS told me that the problem can be apear because of virtual machine.:confused:

I waiting your's advice and ideea.

Thank's in advance for support and understanding.

Best regards.

---

### Post by mechanicaldesign on 2009-10-29
Hello to everybody,

Can somebody to recommended me some software which can be installed on Ubuntu, and on which I can create ".gif" animation ?

I waiting your advice. This are help me to put some animation from ANSYS to INTERNET.

Than you in advance for your support and recommendation.

Best regards.:popcorn:

---

### Post by samden on 2009-10-29
Mechanicaldesign, you are far more likely to get an answer to such questions if you start a new thread with a relevant title in a relevant part of the forum, rather than just hoping someone will see your post at the end of this long thread and happen to know the answer. The people reading this thread aren't necessarily the best people to answer your somewhat off-topic questions.

Hopefully that helps you to get answers to your questions.

---

### Post by mechanicaldesign on 2009-10-30
Hi [samden]("http://ubuntuforums.org/member.php?u=194974"),

Unfortunatly for me, you have write. This is not corect topic when I put my question. After I posted my question, I searched and look much better on topics, and I observed that my topic must be added to other topic like multimedia, software, etc.

Thank you for your observations.

Best regards.:-$

---

### Post by pakki on 2010-04-16
My favourite applications\


For maple 12 users it is very important to get this file 
[http://www.mediafire.com/file/tryjzw4yhzm/AEM](http://www.mediafire.com/file/tryjzw4yhzm/AEM) Maple 12 +Solution Manual.rar

google name to find abt this valuable thing
unpaack this in maple installation directory or anywhere else!!
run Table of contents *.mws file from within maple
one folder consists of book & the other the solution manual

---

### Post by Gemnoc on 2010-04-26
@ pakki

Dude, have you ever heard about **thumbnails**?!? Your screen captures are **huge**. I don't have a problem with it (I'm on a 7.5MBit cable modem connection), but I'm pretty sure there's a forum rule about not posting images that big!

Anyway, back to the topic, which is "the sorry state of engineer apps on Linux". :P

I've been using AutoCAD/Solidworks/Solid Edge in my field of work, and have hoped for Linux alternatives for years. I'm keeping pretty much up to date about this. Here's what I know about MCAD apps on Linux:

Commercial (high-end) parametric MCAD packages:
[LIST]
[*]Pro|Engineer Wildfire 3 from 2007 was the last Linux release from PTC, which claimed there was not enough demand to continue offering it. It was certified for Red Hat 32-bit.

[*]Siemens PLM Software (formerly UGS) NX is currently the only available parametric CAD app on Linux. It is the result of combining Unigraphics, which was first developed on UNIX 30 years ago, with SDRC I-DEAS. NX is used in the automotive and aeronautics industries. NX4 to NX6 (the latter published in 2008 ) are available on Linux, certified for SuSE 64-bit (and on OS X and Solaris too I believe). The latest NX7 release from 2009 is currently only available on Windows, I don't know if a Linux release will be available.

[*]Catia V5 is **not** available on Linux, but many people claim they can run it through Wine. (see WineHQ's [AppDB entry]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6153"))

[*]No other Windows parametric MCAD app will run with Wine: that's Solidworks, Solid Edge, Inventor or Pro|Engineer. They just use too much of Microsoft's .NET framework and APIs for that to happen anytime soon.

[*]Solidworks may actually run on Linux, when it turns to the cloud in the next few years. Then the main app would run on a Windows server, and there would be a client app on (possibly) any platform. At SolidWorks World 2010, a demo showed such a client running on a Mac.
[/LIST]

AutoCAD alternatives
[LIST]
[*]Bricscad by Bricsys, an Autocad clone that has been available on Windows for 10 years, is being ported to Linux. Currently at alpha stage, final version to be available during 2010; a standard (2D) and Pro version (ACIS modeling) should be offered.
[*]ARES and ARES Commander Edition are new Autocad LT/Autocad clones developed by Graebert, the Linux versions also to be made available during 2010.
[/LIST]

Other lesser known commercial packages:
[LIST]
[*]GraphiteOne is at v3.1 and based on the Parasolid kernel. Its interface is now close to Solidworks (without all the features or the same ease of use). There was a free personal version (part design only) available in Ubuntu package. As of now, [the website]("http://www.graphiteone-cad.com/") has been down ("under construction" it says) for some time. No idea what's going on.

[*]VariCAD has already been mentioned: it works in 2D/3D. Its UI is not easy to grasp.

[*]MEDUSA4 from CAD-Schroer has a free version: it's an odd 2D/3D hybrid modeling app. You draw on ortho views, the software generates a 3D model from it. The drafting module's UI is one of the best I've seen on Linux. Problems with the free version: you need a license locked to your PC's MAC address, it has to be renewed every 6 months. And you can't save in any other format than their proprietary one. Their website offers a service to export to DWG or PDF, for a fee.
[/LIST]

The odd one
[LIST]
[*]Google Sketchup 7.1 for Windows now runs surprisingly well on Linux with Wine, even on some Intel graphics. (tested on PCs with nVidia GF6200GT, GF8600GTS and GF9800GT; and on a mini-notebook with Intel GMA 4500MHD)
[/LIST]
Open Source Projects of note:
[LIST]
[*]QCad Community Edition for 2D drafting, frustrating to use for any AutoCAD user (the snaps you need to set manually, only one active at a time, is the main source of frustration)
[*][PythonCAD]("http://sourceforge.net/projects/pythoncad/"), after being left for dead for a couple years, was picked up by a new maintainer last year. This 2D CAD app has a simplistic but straightforward UI, automatic snap tools (a plus against QCad), but it lacks features, is slow and ATM can't open or save DXF. There's a release planned for next August that may address that.
[*][FreeCAD]("http://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Main_Page") is a promising 3D parametric package aiming to offer a tool set similar to commercial parametric apps, but it may take years for that to happen; still, it's a fun app to play with, and is already available in Lucid Lynx's repositories.
[*][HeeksCAD]("http://code.google.com/p/heekscad/") is a comparable project to FreeCAD, I haven't had the chance to try it yet but it too is very interesting. Both are based on OpenCascade.
[*][gCAD3D]("http://www.gcad3d.org/") is another project which is currently active.
[/LIST]

By the way, don't expect any open source CAD software to be "compatible" to Solidworks, Inventor and the like. All they can import are open, non-proprietary and fully spec'd formats like STEP and IGES, and possibly DXF.

That's it for now. :)

---

### Post by ad_267 on 2010-04-26
To the OpenSource CAD apps you could add avoCADo ([http://avocado-cad.sourceforge.net/](http://avocado-cad.sourceforge.net/)). It looks very well planned and organised, but there was only ever one main developer and it looks like they've burnt out a bit. The last commit to the source code was 17 months ago.

The feature set is very basic at the moment but the potential is definitely there.

FreeCAD and HeeksCAD both use the OpenCASCADE library, where as avoCADo is starting from scratch and writing it's own backend.

AvoCADo is written in Java which I thought was a bit of a weird choice for a CAD app, but if there are any Java developers out there looking for something to contribute to this might be a really good option.

---

### Post by Gemnoc on 2010-04-26
> **ad_267 said:**
> To the OpenSource CAD apps you could add avoCADo ([http://avocado-cad.sourceforge.net/](http://avocado-cad.sourceforge.net/)). It looks very well planned and organised, but there was only ever one main developer and it looks like they've burnt out a bit. The last commit to the source code was 17 months ago.
You're right, and I didn't mention it because it's been inactive for so long. One other 2D app I forgot is [CADEMIA]("http://www.cademia.org/frontend/index.php?folder_id=258"), which is also programmed in Java. A new v2 release should be out soon.

Maybe I could add those two to my list.

[QUOTE=ad_267]FreeCAD and HeeksCAD both use the OpenCASCADE library, where as avoCADo is starting from scratch and writing it's own backend.[/QUOTE]
That's because 3D apps need a geometric kernel. OpenCASCADE offers this kernel as well as a development platform. Well known comercial kernels are ACIS, Parasolid, Granite (Pro|E), Catia's. To my knowledge, OpenCASCADE's is the only open source geometric kernel. But FreeCAD and HeeksCAD still needed to develop their 2D drafting modules, as I understand it.

I just remembered another app: [OpenSCAD]("http://openscad.org/"): it's labeled "the programmer's solid 3D CAD modeler". 3D models are generated by scripting.

---

### Post by ad_267 on 2010-04-26
Yeah FreeCAD and HeeksCAD look to be better options than avoCADo, I just hadn't seen avoCADo before and it looked like it had some potential if someone wanted to take it over.

It seems like there's some licensing issues with Open CASCADE. Debian used to include it in the non-free repository but recently moved it into main, however Fedora still considers it to be non-free and won't include it in their repos. Hopefully that gets sorted out but from what I've read the Open CASCADE people haven't been at all helpful in trying to resolve this: [https://bugzilla.redhat.com/show_bug.cgi?id=458974](https://bugzilla.redhat.com/show_bug.cgi?id=458974).

---

### Post by Gemnoc on 2010-04-27
Hey ad_267,

Thanks for bringing this to my attention. I didn't know about that OCC licensing problem. I wonder what was done for FreeCAD to be finally included in Debian and Ubuntu repositories (the HeeksCAD project hasn't had such luck).

I found a thread in [the OpenCascade forums]("http://www.opencascade.org/org/forum/thread_15859/") discussing it further. I know licensing issues are very important, but reading the whole thread and trying to understand all the specifics almost gave me a headache!

As for avoCADo, I wouldn't go as far as say it's not as good an option as FreeCAD and HeeksCAD. It just doesn't have the same goal. I think a good 2D CAD app will always be useful.

Regards

---

