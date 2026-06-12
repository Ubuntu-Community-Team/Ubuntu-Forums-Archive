---
title: "Statistics - PSPP 0.6.0"
date: 2008-08-21
forum: Education &amp; Science
---

### Post by gunksta on 2008-08-21
The Hardy repos have pspp 0.4.x in them, but 0.6.0 is out and it's really really incredible. If you have experience using SPSS, you will feel very much at home. It's not done yet (0.6 < 1.0) but it is much more capable and useful than the version in the hardy repos. The GUI (psppire) does have some limitations, but it's much better than any R-CRAN front-end I've ever seen. In time this program will become _the_ tool to point new Linux users to when they need a statistics tool that comes with a GUI. 

As an added bonus some of you will be pleased to learn that the FSF have worked very hard to reproduce the delightful fortranesque world that is SPSS syntax. :KS If you have to work with SPSS syntax or .sav files, this program is worth checking out. If you are already a wizard with R-CRAN, and don't need to share files / code with SPSS users, you are better off ignoring this post. Because of the brilliant structure R adopted for letting people write custom code/modules, R-CRAN has more functions and features than either PSPP or SPSS base. But, PSPP has a lot to offer people who need compatibility with SPSS or want a GUI. I'm sure that PSPP will (slowly) close the gap with R in the future.

[http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)

The installation directions directions are pretty good but I had to install the ruby packages for most of the dependencies in order to get it to compile. So, if you just go through the dependencies and make sure you have the -dev and -ruby stuff, it works as advertised.

Conversely, I could send you the .deb file that I have but I feel obligated to tell you that it was created via checkinstall and it does not do dependency checking for you. I just wrote it to make it easier to remove / upgrade with Intrepid comes out. If you want it, PM me, and I'll send it to you.

For all you emacs fans out there (I am slowly becoming one myself) the program comes with a very useful mode called pspp-mode that will make a very nice addition to your collection of modes. If someone who actually knows LISP could look at this and tell me how hard it would be to fold this mode into ESS, I would love to learn more about that.

---

### Post by UbuWu on 2008-08-21
0.6 is in intrepid :) It looks so much better than the previous version!

---

### Post by gunksta on 2008-08-22
Yeah, it's definitely in Intrepid, but I wanted to play with it today, and it only takes a few minutes to compile (once you get done figuring out how to make it compile).

You can actually do useful stuff with PSPP now . . . but I don't much care for the name.

---

### Post by alienseer23 on 2008-09-12
Right, so I am confused here :) I need to get this installed. It's for a class. I checked (via synaptic) and I have all of the dependencies installed (or their replacements?) and I try to `./configure' and I get some error 

> configure: WARNING: The following optional prerequisites are not installed.
You may wish to install them to obtain additional functionality:
	libxml2
	libreadline (which may itself require libncurses or libtermcap)
configure: error: The following required prerequisites are not installed.
You must install them before PSPP can be built:
	libplot (or use --without-libplot)
	gtk+ 2.0 v2.12 or later (or use --without-gui)
	libglade 2.0 v2.6.0 or later (or use --without-gui)

so, I do not understand how to get beyond this point. How did you get it to recognize that you had these packages installed?
I am running hardy, all updates.

---

### Post by ad_267 on 2008-09-12
If you do want to compile it then you need the packages that have a "-dev" on the end too.

---

### Post by ad_267 on 2008-09-12
The .deb package from [http://packages.debian.org/lenny/pspp](http://packages.debian.org/lenny/pspp) can be installed in Ubuntu 8.04 so just use that instead.

---

### Post by alienseer23 on 2008-09-12
thank you!

---

### Post by ad_267 on 2008-09-12
Hmm it seems everything works fine but I get this appearing in the terminal:
** (psppire:9910): CRITICAL **: Gtk+ version too old (micro mismatch)

The debian page says libgtk2.0-0  (>= 2.12.0), and Ubuntu has  2.12.9-3ubuntu2, so I don't think there should be any problems.

---

### Post by gunksta on 2008-09-12
I have had problems using compiled binaries from Debian in Ubuntu. The basic system is the same, but you do get into version problems and other hang ups. I agree with the above post, if you are going to compile you will need the -dev packages that accompany EACH dependency for pspp. Without the -dev packages (not installed unless you do it manually) the compile will fail.

If I can get an email address, I can send you the binary that I compiled.

--andy

---

### Post by alienseer23 on 2008-09-12
I get the same error about gtk, I sent a message to you, gunksta, with my email for the deb, but I am going to try to compile it one more time (with all of the -dev file versions of the dependencies) before I use your failsafe. I dislike brick walls, and prefer to go over them, but I will slam thru with your .deb if required. :D

---

### Post by gunksta on 2008-09-12
Sorry folks. I can't upload the binary because it's too big. Contact me privately with an email and I'll send it to you.

---

### Post by suxenexus on 2008-09-13
I would want to try that. Here's my email- suxenexus06[at]gmail[dot]com

---

### Post by gunksta on 2008-09-13
I sent it to you.

---

### Post by Dirty D on 2008-10-10
Hi,

I'm having a bit of trouble getting started in PSPP. I'm coming from using SPSS 16 in Windows.  My procedure there was to write the bulk of my code in a text editor and then call it from a syntax window. After that, if I needed to do small, ad hoc commands, I'd run them from the syntax window.

The problem that I have is that I don't know how to get PSPP to go straight into GUI mode. Is anyone available to help me out with this?

Thanks,

DD

---

### Post by ad_267 on 2008-10-10
> **Dirty D said:**
> 
The problem that I have is that I don't know how to get PSPP to go straight into GUI mode. Is anyone available to help me out with this?


The command is "psppire"

---

### Post by UbuWu on 2008-10-11
> **Dirty D said:**
> 
I'm having a bit of trouble getting started in PSPP. I'm coming from using SPSS 16 in Windows.  My procedure there was to write the bulk of my code in a text editor and then call it from a syntax window. After that, if I needed to do small, ad hoc commands, I'd run them from the syntax window.

If you work that way, you might also like rkward.

---

### Post by Dirty D on 2008-10-12
> **ad_267 said:**
> The command is "psppire"

Thanks for the tip. Unfortunately, I don't seem to have psppire. 

dirtyd@dirtyd-laptop:~$ psppire
bash: psppire: command not found
dirtyd@dirtyd-laptop:~$ locate psppire
dirtyd@dirtyd-laptop:~$ sudo apt-get install psppire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package psppire
dirtyd@dirtyd-laptop:~$ apt-get install pspp
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dirtyd@dirtyd-laptop:~$ sudo apt-get install pspp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pspp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dirtyd@dirtyd-laptop:~$ psppire
bash: psppire: command not found
dirtyd@dirtyd-laptop:~$ 

Advice?

Dirty D

---

### Post by UbuWu on 2008-10-12
You need to have at least version 0.6.0 for psppire.

---

### Post by Dirty D on 2008-10-12
Didn't work.

dirtyd@dirtyd-laptop:~$ sudo apt-get remove pspp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libplot2c2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  pspp
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3621kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128749 files and directories currently installed.)
Removing pspp ...
dirtyd@dirtyd-laptop:~$ sudo apt-get install pspp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pspp
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1208kB of archives.
After this operation, 3621kB of additional disk space will be used.
Selecting previously deselected package pspp.
(Reading database ... 128510 files and directories currently installed.)
Unpacking pspp (from .../pspp_0.4.0-7ubuntu3_i386.deb) ...
Setting up pspp (0.4.0-7ubuntu3) ...

dirtyd@dirtyd-laptop:~$ psppire
bash: psppire: command not found
dirtyd@dirtyd-laptop:~$

---

### Post by ad_267 on 2008-10-12
Why would you expect that to work? You just uninstalled and then reinstalled the same version of pspp (0.4).

The command "apt-cache show pspp" will give you the version available in the repository. I don't know much about pspp sorry, I didn't realise that psppire is only in recent versions. As mentioned in this thread I was able to use the debian package of pspp. If you upgrade to 8.10 you will also get the most recent version.

---

### Post by Dirty D on 2008-10-13
Brilliant, thanks. I'm off to code code code away on my ridiculously large .SAV files. THANKS!


Dirty D

---

### Post by jdackle on 2008-11-19
Thanks for starting this thread, gunksta! :cool:
Somehow, that first post of yours does not seem to offer a "Thank you" icon right now... :confused:
I'll just thank you in some other of your posts in the thread. ;)

In the meantime, I NEED THAT BLOODY FILE! Sorry for the shouting... :oops: 
*(I'll be sending you my e-mail address through PM in a minute. Thanks for the offer. :) )*
I've practically lost tthe last two days trying to compile the darned thing (first time I ever used checkinstall) and to no success!

Worse still, I installs BEAUTIFULLY! But it the resulting .deb package includes nothing but documentation. The [checkinstall FAQ]("http://www.asic-linux.com.mx/~izto/checkinstall/faq.php"), regarding this issue, on Q#2, says:> **I ran CheckInstall and everything seems to run fine, but when I check my new package I only find the documentation files!**

CheckInstall can't trace (yet) the actions of three kind of binaries:

    * SUID programs
    * SGID programs
    * Statically linked binaries


You may now go to check the binaries you're using in the installation process   ;-). 
Now, I wouldn't know how to do that check and if I did, chances are I wouldn't know what to do about it.
This is an almost completely-fresh install of Hardy (except for the some 300 updates!), meaning I haven't messed with any system files (yet!) and very little with my personal ones, so... :confused:

I'm actually trying to build PSPP-0.6.1, if that matters...

I can't install Intrepid due to my current machine being apparently incopatible with it and that's why I installed Hardy instead and will keep it for a good while.

I also do hate to keep source-directories, for package/program maintenance, so the .deb file would be great!

Also, as I probably will keep using Hardy for a long time, I need to have a way to keep updating my PSPP install as it is updated upstream...

Can anyone help me out with this?

TIA

---

### Post by ahmatti on 2008-11-20
Have you tried the debs in this site: [http://www.getdeb.net/app/PSPP](http://www.getdeb.net/app/PSPP) ?

---

### Post by jdackle on 2008-11-20
> **ahmatti said:**
> Have you tried the debs in this site: [http://www.getdeb.net/app/PSPP](http://www.getdeb.net/app/PSPP) ?

Darn! There were none for Hardy just a couple days ago! :lolflag:

Thanks a lot! :)

---

### Post by gunksta on 2008-11-20
I guess I should update the name of this thread. Oh well.

Compiling PSPP isn't hard (compared to monsters like OpenOffice.org) but there are still several "gotchas".

The text below can also be found in the INSTALL file from the source download.

The following packages are required to install PSPP:

    * An ANSI C compiler and tool chain.  On Unix-like systems, we
      recommend GCC, but any modern compilation environment should
      work.  On Microsoft Windows, Cygwin ([http://www.cygwin.com/](http://www.cygwin.com/)) and
      MinGW ([http://www.mingw.org/](http://www.mingw.org/)) are known to work.

    * The GNU Scientific Library ([http://www.gnu.org/software/gsl/](http://www.gnu.org/software/gsl/)),
      version 1.6 or later, including libgslcblas included with GSL.

    * Perl ([http://www.perl.org/](http://www.perl.org/)), version 5.005_03 or later.  Perl is
      required during build but not after installation.

    * iconv, which should be installed as part of a Unix-like system.
      If you don't have a version already, you can install GNU
      libiconv ([http://www.gnu.org/software/libiconv/](http://www.gnu.org/software/libiconv/)).

The following package is required to enable PSPP's graphing features.
If you cannot arrange to install it, you must run `configure' with
--without-libplot.

    * libplot, from GNU plotutils
      ([http://www.gnu.org/software/plotutils/](http://www.gnu.org/software/plotutils/)).

The following packages are required to enable PSPPIRE, the graphical
user interface for PSPP.  If you cannot install them or do not wish to
use the GUI, you must run `configure' with --without-gui.

    * pkg-config ([http://pkg-config.freedesktop.org/wiki/](http://pkg-config.freedesktop.org/wiki/)).  Versions
      0.18 and 0.19 have a bug that will prevent library detection,
      but other versions should be fine.

    * GTK+ ([http://www.gtk.org/](http://www.gtk.org/)), version 2.12.0 or later.

    * libglade ([http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/)), version
      2.6 or later.

Installing the following packages will allow your PSPP binary to read
Gnumeric files.

    * pkg-config ([http://pkg-config.freedesktop.org/wiki/](http://pkg-config.freedesktop.org/wiki/)).  Versions
      0.18 and 0.19 have a bug that will prevent library detection,
      but other versions should be fine.

      To cross-compile PSPP, you will likely need to set the
      PKG_CONFIG_LIBDIR environment variable to point to an
      appropriate pkg-config for the cross-compilation environment.

    * zlib ([http://www.zlib.net/](http://www.zlib.net/)).

    * libxml2 ([http://xmlsoft.org/](http://xmlsoft.org/)).  

The following packages are optional.

    * libncurses ([http://www.gnu.org/software/ncurses/](http://www.gnu.org/software/ncurses/)).  Without it,
      PSPP will assume it is running in an 80x25 terminal.

    * libreadline and libhistory
      ([http://tiswww.case.edu/php/chet/readline/rltop.html](http://tiswww.case.edu/php/chet/readline/rltop.html)).  Without
      them, interactive command editing and history features in the
      text-based user interface will be disabled.

    * Texinfo ([http://www.gnu.org/software/texinfo/](http://www.gnu.org/software/texinfo/)), version 4.7 or
      later.  Installing Texinfo will allow you to build PSPP
      documentation in PostScript or PDF format.

    * libpq, from Postgresql ([http://postgresql.org](http://postgresql.org)). This enables PSPP 
      to read Postgresql databases.


You MUST install BOTH the libraries referenced here AND the -dev libraries. If you don't, it won't work. As I recall, I also installed all of the perl packages related to the above packages. Perl isn't a run-time requirement, but it is used in the config process, and it seemed to get rid of an error during the 0.6.0 era. It may or may not be absolutely necessary now. I know I have the stuff installed and I don't get errors on my compiles.

Before using this tool, PLEASE read the PSPP manual found at:
[http://www.gnu.org/software/pspp/documentation.html](http://www.gnu.org/software/pspp/documentation.html)

PSPP is not a finished product and it does have a few bugs. If you are turning things in for a grade, or the results matter, you need to be aware of the tool's limitations. All stats tools have limitations. It is our job, as users to be aware of these limitations.

Enjoy.

If you try to compile, and it doesn't work please post what you were doing AND the error you received. I also find it easier to do a ./config, then a make, and then a sudo make install. AFTER this all finishes without any errors, then I run checkinstall and I install the resulting .deb file. By removing the .deb file I get all of the advantages of using checkinstall and it makes it easier to know if the error I am getting is because of checkinstall or if it is because of my compilation.

---

### Post by jashk on 2010-04-17
Brilliant!
Thank you so much mates!
Following all your posts I'm finally able to use pspp!!!
Spss was one of the last software that made me a "slave" of windows, but not anymore!!!
It was very useful for me finding the .deb package and finding that "psppire" was the command to run with gui...
Again: Thank you so much!
Muchas gracias!!

---

### Post by gunksta on 2010-04-18
jashk -- What version of Ubuntu are you using? Your profile claims Hardy, which may or may not be true today (I forget to update that too). 

The last few versions, including Lucid, include PSPP in the repos and the psppire icon is cleanly integrated in the menu. If you are still on Hardy, I would consider updating.

You can install pspp/psppire via Synaptic/Add & Remove OR with the command:
```
 sudo apt-get install pspp 
```

Glad you are enjoying PSPP.

---

### Post by shuttleworthwannabe on 2010-11-02
Thanks I just downloaded from repo's (added the ppa first), and it looks great. I tested it on one of my very large datasets (10,000+ columns and 30,000 rows (records), and it computed basic descriptives without a glitch!

Any idea when more features like logistic regression will be added to the GUI menus? Can these be done using syntax in the mean time?

---

### Post by gunksta on 2010-11-02
I don't know what the developer's plans are, but you can ask them on the [PSPP mailing list]("http://lists.gnu.org/mailman/listinfo/pspp-users"). Glancing at the current [PSPP Manual]("http://www.gnu.org/software/pspp/manual/html_node/Concept-Index.html"), it doesn't look like logit models are possible yet. But, according to the [developer's site]("http://savannah.gnu.org/projects/pspp"), Factor Analysis is now in trunk. I realize this is not very useful if you want to do logistic regression, but it is progress.

---

### Post by shuttleworthwannabe on 2010-11-02
Cool thanks--at least the development on this app has started getting momentum.

---

### Post by gunksta on 2010-11-02
I have never used it, but I think Gretl has support for logit regression and probably has a GUI front-end for it.

---

### Post by ceciliasp on 2012-09-28
Hi. Do you know if this software is able to do mixed logit models?
I'm looking for a linux alternative to SAS... thanks!

---

### Post by overdrank on 2012-09-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

