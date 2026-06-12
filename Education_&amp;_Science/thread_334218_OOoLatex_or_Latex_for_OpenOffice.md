---
title: "OOoLatex or Latex for OpenOffice"
date: 2007-01-08
forum: Education &amp; Science
---

### Post by Toufik on 2007-01-08
**[color=red]The preferred method of installation is no more a deb package but rather via the OpenOffice extension manager[/color]**

The preferred method of installation is no more a deb package but rather via the OpenOffice extension manager. This has the advantage to be platform independent (Win, Mac, Linux,...); to be cleaner than the deb package which has to modify some configuration files (subjected to change from one version to another); ... However, the disadvantage is that there is no more automatic update. But if it works for you, why update? If you experience some problems, then go back to the website to check!

**Install dependencies:**
```
sudo apt-get install texlive imagemagick epstool
```

**Install Mathematical Fonts:**
```
mkdir OOoLatexFonts
cd OOoLatexFonts
wget http://mesh.dl.sourceforge.net/sourceforge/ooolatex/OOoLatexFonts.zip
unzip OOoLatexFonts.zip
cd ..
sudo mv OOoLatexFonts /usr/share/fonts/truetype/.
sudo fc-cache -f /usr/share/fonts/truetype
```
The last step may take a while before finishing

**(Optionnal) Install binaries for EMF**
If you want to use emf format (i.e. scalable pictures of the equations ==> I recommend), you need one more dependency: the latex2emf program.The easiest way to install it is to grab the binaries directly from the OOoLatex website: [http://sourceforge.net/project/showfiles.php?group_id=150801](http://sourceforge.net/project/showfiles.php?group_id=150801)
If you have Ubuntu i386 or 64bits choose latex2emf_Linux_i386_binary.tar.gz
If you have Ubuntu PPC  choose latex2emf_Linux_PPC_binary.tar.gz
If you have something else, you'll need to compile from source (grab OOoLatexEmf_noarch_src.tar.gz)

Once downloaded, go to the directory where you've downloaded:
```
tar -xzvf latex2emf_Linux_i386_binary.tar.gz
cd latex2emf_Linux_i386_binary/
sudo ./install.sh

```

**Install OOoLatex**
And finally, you can now install the extension!! Remarks that if you're just upgrading the extension, you need only this final step! But first download the extension here:
[http://sourceforge.net/project/showfiles.php?group_id=150801](http://sourceforge.net/project/showfiles.php?group_id=150801)
At the time of writing this post, the latest one was 4.0.0-beta2  --> file OOoLatex-4.0.0-beta-2-linux.oxt

There are _two types of installation_. The administrator one is useful when installing for a lot of users but each user is not allowed to modify the configuration (most notably the shortcuts), only root can do that. Therefore I recommend, for normal user, to install the single-user type. For each type ther are two ways to make the install:
[LIST]
[*]Terminal : 
Single-user
```
/usr/lib/openoffice/program/unopkg.bin add OOoLatex-4.0.0-beta-2-linux.oxt
```
Administrator
```
sudo /usr/lib/openoffice/program/unopkg.bin add --shared OOoLatex-4.0.0-beta-2-linux.oxt
```
[*]Graphical :
Single-user:
Open OpenOffice (writer or impress). Tools > Package Manager > Add > Select the oxt file you've downloaded
Administrator:
Not recommended, see terminal method
[/LIST]

Note that you'll have to accept the licence.

**Usage**
After installation, try <Control>+M and <Control>+K (the default shortcuts). You can also add the OOoLatex Toolbar: View > Toolbars > OOoLatex

The module _Equation_ transform a LaTeX code into an image. Two formats are proposed: .png and .emf. You probably know PNG, this is a kind of "normal" image. If you rescale it, you'll see pixel. A way to circumvent this problem is to increase the resolution (dpi) but you'll get larger files! Or to use the EMF format which is a scalable image: the equation is vectorised and don't loose resolution when you rescale it! This is probably the better choice but you need then some binaries (see above). Selecting an equation and opening the equation dialog box allows editing of the equation.

The module _Expand_ was first called Inline in the first versions of OOoLatex. Basically, it transforms (expands) the LaTeX special characters into ones that are usable by OpenOffice. This is done (partly) via the STIX general fonts. The interests of Expand is to include LaTeX characters directly in a sentence without requiring the insertion of an image (as in Equation). Evidently, not all LaTeX code can be expanded (e.g. a fraction bar with something above and under is not a character!), that's why a list is offered in the dialog box.

In summary: use Equation for ... equations and Expand for some in-text characters

**Remove**
Remove the extension:
Single User mode:
```
/usr/lib/openoffice/program/unopkg.bin remove net.sourceforge.ooolatex
```
Admin mode:
```
sudo /usr/lib/openoffice/program/unopkg.bin remove --shared net.sourceforge.ooolatex 
```

---

### Post by neoflight on 2007-01-09
it should be interesting....i could try that sometime.... would you please provide some screenshots if possible? thanks
edit: i forgot that you had provided tha link to that page...there are screen shots in there...so its ok.

---

### Post by Vincosmo on 2007-01-09
cool :)

next step: write a  .deb package and a page on the  ubuntu wiki(s) ;)

---

### Post by rlgc79 on 2007-02-08
Without OOoLatex I would never use Openoffice :) Openoffice should give support to equations written in Latex by default...

Keep the good work :)

Best,

---

### Post by eliasekp on 2007-03-11
Hi, this is my first post in Ubuntu Forum
I'd like to thank you for the the instructions of installing OOoLatex. I want to answer if anybody using the OOoLatex in emf output noticed that some math symbol it is not viewable like  \leq or \kappa in other output you can see the symbol. Is there a solution?

---

### Post by Toufik on 2007-03-15
Hi,

I made a verification: character number 183 is missing in each bakoma fonts... You guess that kappa and leq are at the 183th position.  It seems that the original Bakoma fonts  on the OOoLatex website are corrupted.  I'm trying to correct this.  I'll let you know when it will be fixed (a couple of days).

---

### Post by Toufik on 2007-03-15
After some searches, I discover that the ttf fonts coming from CTAN are buggy !?  The character number 183 is missing in all the fonts (these are : "[", \kappa, \leq, and other various AMS symbol).  I correct this by using the fontforge program.  Now, the fonts included in OOoLatex4Ubuntu are corrected (the ones on the OOoLaTeX website are still buggy but they should be changed soon).  The easiest way the do the update is simply to repeat steps 1 to 3 hereabove.

Enjoy

---

### Post by Belathor on 2007-03-16
I did steps 1-3 again but I still don't have \kappa and \leq.

---

### Post by etotehpii on 2007-03-18
```
4) This is a bit boring, so we will create a new shortcut

  Tools > Customize
  Choose the tab Keyboard
  Select Openoffice.org (instead of Writer in order to have it in all openoffice applications)
  Choose the category : OpenOffice.org > user > OOoLatex > OOoLatexEquation
  Choose the function : Main
  Select your shortcut key (for instance Control+M which is free)
  Click on Modify
  Click on OK

  Try it!!

```

I get that in the console.  Then I go to Tools and Customize and select openoffice.org instead of writer.  Once I do this Office crashes on me.  (I followed the instructions as stated in the OP)

---

### Post by Toufik on 2007-03-18
I also experienced a lot of bug/crash with OpenOffice.  The Ubuntu version is _really_ buggy!  Personnally, I use the offcial OpenOffice from their website: much more stable (but need a bit of work to install because there is no Ubuntu package)!!  For your problem, I cannot advice you anything else than "retry until it doesn't crash on that step" (or install the official Openoffice).  I'm not sure if this is an issue but have you check in Tools > Options > OpenOffice.org > Java if you have a proper JRE. Maybe it is better to use Sun one : ```
$ sudo apt-get install sun-java5-jre sun-java5-bin
$ sudo update-alternatives --config java
``` and select sun java.  Tell me if it helps so I can add it in the first post.

For the \kappa, I'll check what happens.  For the moment, I've made a .deb package (my first :) ) and I'm testing it on sevral computers.  It installs the binaries AND the macros :D  Must be release very soon.

---

### Post by etotehpii on 2007-03-18
I have current Java.  I've slightly narrowed it down. 

Office bombs after I select Openoffice.org.(In the part where I select that or writer)

It is stil responsive, but once I click on Openoffice.org in the category selection then it dies.

How much easier is it to use the LaTeX/Tex commands in Openoffice as opposed to an editor like Kile?  I'm only using Kile to write mathematical proofs at the moment.

Thanks

---

### Post by Toufik on 2007-03-21
I've also experienced problem at same place but it was a random crash for me, so I managed to install it.  The problem is in OpenOffice, I can't do anything for that.

The purpose of OOoLaTeX is to easily insert LaTeX equation within an openoffce document.  Personally, I use Kile for articles, reports,... where I need a lot of equations.  But I really don't like to write presentations in LaTeX (with \usepackage{prosper}), therefore I make them with OpenOffice and when I need an equation, I just copy/paste the LaTeX equations from Kile to OOoLaTeX, i.e. no need to use the equation editor of OOo to rewrite an equation (and the typesetting is also better!).  For screenshots, see here: [http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/)

---

### Post by Toufik on 2007-03-27
Hi,

I managed to create a debian package. See my first post for instructions.  If you've installed the macro manually, I advice you to install the .deb because it works better :)  For instance, every new user will now have OOoLaTeX automatically installed, and it is easier to managed in case of new version.

Bye

---

### Post by etotehpii on 2007-03-28
I tried the new instructions.

It bombed at Tools>Macros>Run Macro...

Didn't get as far as I did the last time.:) 

Its not a big deal though, Kile is more than sufficient presently.

---

### Post by Toufik on 2007-03-29
Let's try some debugging of OpenOffice... (It should be better with Feisty)

Which version if OOo do you have?

Do you have any error message while installing the deb?

If not, the macro is correctly installed but OOo bump when trying to access it.  Let's try it with a shortcut instead of clicking:
Find this file ~/.openoffice.org2/user/config/soffice.cfg/modules/simpress/accelerator/YOUR_LOCALE/current.xml
where YOUR_LOCALE is your language code (if you have several, choose the one you used, or do it for all if you don't know :) )
Then, add this line
```
<accel:item accel:code="KEY_M" xlink:href="vnd.sun.star.script:OOoLatex.OOoLatexEquation.main?language=Basic&amp;location=application" accel:mod1="true"/>
```

Now open Impress and press "CTRL M", the macro should open.

Give me all the informations you get (you'll get more if you launch openoffice from a terminal: type openoffice)

---

### Post by etotehpii on 2007-03-29
Here is what I get when I run through the terminal.

```
*** glibc detected *** free(): invalid pointer: 0xb6177678 ***
/usr/lib/openoffice/program/soffice: line 233:  3299 Killed                  "$sd_prog/$sd_binary" "$@"



```

I'll try your new suggestion later.

Thanks

---

### Post by Toufik on 2007-03-30
We have made a repository for the deb => you can now install via apt-get which deals better with dependencies.

Changelog: a default shortcut is created: CRTL+M

See my first post for the address of the repo

---

### Post by aikishugyo on 2007-05-21
Is there any chance of getting a package for AMD64? When I enter the repository into my sources.list then I still don't get the ooolatex in any searches, so I assume it is for i386 architecture. Since OO did install in some clever way, is there a chance for ooolatex to do so too?

---

### Post by luca.de.alfaro on 2007-05-26
Dear All, 

I had in February or so contacted the original developer, Geoffroy Piroux.  As I very much needed this package for my work (and for my students), I adapted Geoffroy's code, and I improved (in my opinion) the fonts used in the in-line mode.  The version I have works reliably with OpenOffice 2.2, and with Ubuntu 6.10, 7.04, on Windows under Cygwyn, and on the Mac (except that under fink, the version of latex is a bit old, and the display mode doesn't work as well). The version I made uses really somewhat different fonts from the one by Geoffroy; I am quite satisfied by this version. 

I am contacting Geoffroy again, to see if he would like to adopt any of the changes I made. 
You are also free to try my version, available at [http://www.dealfaro.com/home/ooolatex.html]("http://www.dealfaro.com/home/ooolatex.html")
I am curious to know whether it works well also for you. 

My students and I very much need this plug-in, so I decided to start distributing it even before Geoffroy decides (if he ever will) to adopt the changes I made.

---

### Post by Toufik on 2007-05-27
> **aikishugyo said:**
> Is there any chance of getting a package for AMD64? When I enter the repository into my sources.list then I still don't get the ooolatex in any searches, so I assume it is for i386 architecture. Since OO did install in some clever way, is there a chance for ooolatex to do so too?

The original OOoLaTeX is available as sources so it works on every system. The package I wrote contains the binaries I've compiled on my computer. I don't know how to compile for AMD64 from a i386 :) So you can try to compile on your own and then send me the binaries in order that I create a new package.

From [http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/) download OOoLatexEmf_noarch_src.tar.gz

```
tar -xzvf  OOoLatexEmf_noarch_src.tar.gz
cd OOoLatexEmf_noarch_src
tar -xzvf libEMF-1.0.2.tar.gz
cd libEMF-1.0.2
./configure
make
sudo make install
cd ../Linux
```
There (/download/place/OOoLatexEmf_noarch_src/Linux/) edit the Makefile to have this:

```
# Makefile for latex2emf 
ROOT=/usr/local

all: latex2emf

latex2emf: ../latex2emf.cpp
        c++  -L$(ROOT)/lib/ \
             -I$(ROOT)/include/ -I$(ROOT)/include/libEMF/ \
             -o latex2emf ../latex2emf.cpp -lEMF
clean:
        rm latex2emf
install:
        cp latex2emf $(ROOT)/bin/

```

Then
```
make
sudo make install
```

Now you have all the binaries, download the macro and follow the instructions (see README)

---

### Post by INormann on 2007-06-23
Installation failed on my Edgy Ubuntu following the corresponding instructions from Toufik:

"aptitude install ooolatex" stops with this error:

Updating the font cache.  This may take a while...
"/usr/share/fonts/truetype/": error scanning

So what should be changed here?

---

### Post by Toufik on 2007-06-24
Strange... This is one of the last step of the installation: adding the new fonts (BakomaFonts) to the cache. Maybe OOoLaTeX is still working, could you try?

Could you post also
$ ls /usr/share/fonts/truetype/

The command who causes the error is this one, could you retry it:
$ sudo fc-cache -f /usr/share/fonts/truetype/

Thanks for bug reporting

Toufik

---

### Post by franjesus on 2007-06-26
> **Toufik said:**
> The original OOoLaTeX is available as sources so it works on every system. The package I wrote contains the binaries I've compiled on my computer. I don't know how to compile for AMD64 from a i386 :) So you can try to compile on your own and then send me the binaries in order that I create a new package.


If you provide the source package, or at least the debian subdirectory, it would  be much easiser.

---

### Post by Toufik on 2007-06-27
> **franjesus said:**
> If you provide the source package, or at least the debian subdirectory, it would  be much easiser.

What do you mean exactly? I'm not sure to understand.

If you want the sources, go to [http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/)
If you want the debian tree, uncompress the .deb (the binaries you get during the compilation (latex2emf and OOoLatex) are in /usr/local/bin, the rest is for the macro and the fonts)

Toufik, ready to help

---

### Post by fulch on 2007-07-04
When I type 
sudo apt-get install ooolatex
I am told that the package ooolatex does not exist. Neither does the synaptic package manager find the package. And also on the website [http://packages.ubuntu.com/](http://packages.ubuntu.com/) I cannot find the package ooolatex. :( What am I doing wrong? Does have to do with the fact that I am running an AMD 64?

So I tried to use Method 2 from the original post. There I get stuck at step 4, when running ./test.sh. It tells me that a LaTeX error occured. Also running 
OOolatex test.tex   fails. What is going on here?

---

### Post by Toufik on 2007-07-05
You're right! The problem is that you have a AMD 64. The package exists only for 386 (I have no clue on how to compile something for 64 from a 386).  Sorry but you have to use methos number 3 :) Compile from sources:

[http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/) 

A new release is schedule for soon... I hope to be able to build a package for AMD64 also

---

### Post by dhris on 2007-07-08
I'm currently running Dapper (don't want to upgrade at the moment) and I get the following error upon pressing ctrl+m in Impress:

BasicProviderImpl:: getScript: no script!

Evidently OpenOffice can't find the script. I know it's installed because I can run it from the command line and ctrl+m was correctly mapped to look for the script. But if I look in the macro menu of Impress, the script does not seem to be listed.

To install, I followed the directions posted here and installed from the specified repository with apt-get. I have tried restarting OpenOffice, and even rebooting my machine. That means I'm fresh out of ideas.

---

### Post by kknd on 2007-07-08
Very nice!!!

---

### Post by abalter on 2007-07-08
Public access to [http://www.fyma.ucl.ac.be](http://www.fyma.ucl.ac.be) seems to have been removed.  Can the deb files be posted elsewhere?
Thanks, Ariel

---

### Post by Toufik on 2007-07-10
> **abalter said:**
> Public access to [http://www.fyma.ucl.ac.be](http://www.fyma.ucl.ac.be) seems to have been removed.  Can the deb files be posted elsewhere?
Thanks, Ariel

Sysadmin paranoîa :D

I've asked to make it public again !

Toufik

---

### Post by Toufik on 2007-07-10
> **dhris said:**
> I'm currently running Dapper (don't want to upgrade at the moment) and I get the following error upon pressing ctrl+m in Impress:

BasicProviderImpl:: getScript: no script!

Evidently OpenOffice can't find the script. I know it's installed because I can run it from the command line and ctrl+m was correctly mapped to look for the script. But if I look in the macro menu of Impress, the script does not seem to be listed.

To install, I followed the directions posted here and installed from the specified repository with apt-get. I have tried restarting OpenOffice, and even rebooting my machine. That means I'm fresh out of ideas.

The deb has been tested with breezy dapper edy and feisty, so it should work!

If that command works (with some tex file)
$ OOoLatex -e emf test.tex
then the program is correctly installed

The problem is the installation of the macro. The deb file does it automatically, but if you encounter a problem, could you check these:
Open impress
Tools > Macro > Run macro
Select "My Macros" > OOoLatex > OOoLatexEquation (if I understand, you don't have that)

What is your openoffice version? Is it the ubuntu one or the official one (from OO.org website)?

In last resort, you can try method 2 (without the steps 3 and 4)

---

### Post by Schoappied on 2007-07-10
Hi guys!

I'm a newbie at the Latexworld...
I've tried to install of ooolatex on Feisty. I added the source to my sourcelist en installed ooolatex. Everything went fine... so far.

But I couldn't make the macro work. When I do Ctrl M I get:
'There is a scripting Frameworkfault when Basic script is running 
 vnd.sun.star.script:OOolatex.OOolatexEquation.main?language=Basic&location=application. 
  
 Basicproviderimpl::getscript: no script! '

Are there some steps which I've missed?

I hope You can help me out.

Thanks! schoappied

---

### Post by dhris on 2007-07-10
> **Toufik said:**
> The deb has been tested with breezy dapper edy and feisty, so it should work!

If that command works (with some tex file)
$ OOoLatex -e emf test.tex
then the program is correctly installed

The problem is the installation of the macro. The deb file does it automatically, but if you encounter a problem, could you check these:
Open impress
Tools > Macro > Run macro
Select "My Macros" > OOoLatex > OOoLatexEquation (if I understand, you don't have that)

What is your openoffice version? Is it the ubuntu one or the official one (from OO.org website)?

In last resort, you can try method 2 (without the steps 3 and 4)

I have OpenOffice 2.0 from Ubuntu. Anyway, I see Schoappied is having the same problem and he's using Feisty. But anyway, the download with apt-get evidently did not configure the macro properly on my system or his.

I was able to easily fix the problem though. I downloaded the script from here:
[http://sourceforge.net/project/showfiles.php?group_id=150801](http://sourceforge.net/project/showfiles.php?group_id=150801)
get OOoLatexMacro-test5.tar.gz   

Unzip it and follow the directions in the "Macro Installation" from the OOoLatex site:
> To install the OOoLatex macros, launch OpenOffice, open the "marco organizer" from the menu Tools>Macro, button Organizer and select the tab "Libraries". There is a button "Append" which allows you to select the file script.xlb from the directory OOoLatexMacro-[xxx]/macro1.1.x/ for OpenOffice-1.1.x and from OOoLatexMacro-[xxx]/macro2.0/ for OpenOffice-2.x.

use the script.xlb file from your unzipped macro directory. Not the prettiest solution but it worked for me.

Amazing script by the way. Thanks for your work on it.

---

### Post by Toufik on 2007-07-11
Thanks for bug reporting, I will try to fix it soon

---

### Post by Schoappied on 2007-07-11
> **dhris said:**
> I have OpenOffice 2.0 from Ubuntu. Anyway, I see Schoappied is having the same problem and he's using Feisty. But anyway, the download with apt-get evidently did not configure the macro properly on my system or his.

I was able to easily fix the problem though. I downloaded the script from here:
[http://sourceforge.net/project/showfiles.php?group_id=150801](http://sourceforge.net/project/showfiles.php?group_id=150801)
get OOoLatexMacro-test5.tar.gz   

Unzip it and follow the directions in the "Macro Installation" from the OOoLatex site:

use the script.xlb file from your unzipped macro directory. Not the prettiest solution but it worked for me.

Amazing script by the way. Thanks for your work on it.

Thanks!!! :) It also works on my system ;)
Also thanks to Toufik!

Ps. Is there a way to 'convert'/ 'export' a OOwriter tekst to LaTEx? And what are the possibilities with OOcalc?

---

### Post by Toufik on 2007-07-11
Some news:

- Installation of a new repository, powered by falcon 2.0-beta2
have a look at [http://www.fyma.ucl.ac.be/ubuntu/](http://www.fyma.ucl.ac.be/ubuntu/)
- The deb have been splitted in two 
   --> ooolatex with the binaries and macros
   --> bakomafonts for the fonts
- the macros are the new ones (v3 aka test5)
- the binaries are also provided for AMD 64 (needs to be tested!!!)

Thanks for reporting
 * if you still have problems with the installation
 * if you have a 64 bits processors: does it works or not?

Toufik

---

### Post by lattice_cat on 2007-07-12
Thanks Toufik. But I couldn't down load bakomafonts deb ?

---

### Post by Toufik on 2007-07-12
> **lattice_cat said:**
> Thanks Toufik. But I couldn't down load bakomafonts deb ?
Sh*** it seems there is a bug in falcon (which is beta). I've made a quick fix. It works now

---

### Post by lattice_cat on 2007-07-12
> **Toufik said:**
> Sh*** it seems there is a bug in falcon (which is beta). I've made a quick fix. It works now

Thanks.


When I tried to edit existing equation by typing C-m on the equation,
the dialog pops up.  I typed some modification and  push
Latex button,  a runtime error called ElementExitsException is thrown.
This happends about the  probability of  1/3 of all editing existing
equation.

Does anyone experience this ?

---

### Post by vonkad on 2007-07-22
I'm running Feisty with OO 2.2.0-1ubuntu4. I've just installed OOoLatex from the feisty repository, i.e. adding
"deb [http://www.fyma.ucl.ac.be/ubuntu](http://www.fyma.ucl.ac.be/ubuntu) feisty contrib" to sources.

Everything instals fine, but when I press ctrl-m, I get message boz saying:
blablabla BasicProviderImpl::getScript: no script !

This error has already appeared here and I'll be able to find some trick. Just reporting that it doesn't work out of the box yet.

Regards, 
David Vonka

---

### Post by Toufik on 2007-07-23
Thanks for reporting, we are working on a new way to install the macro that should solve all the problems. See post 33 for a manual installation of the macro (the binaries are correctly installed).

---

### Post by chca on 2007-10-30
> **vonkad said:**
> I'm running Feisty with OO 2.2.0-1ubuntu4. I've just installed OOoLatex from the feisty repository, i.e. adding
"deb [http://www.fyma.ucl.ac.be/ubuntu](http://www.fyma.ucl.ac.be/ubuntu) feisty contrib" to sources.

Everything instals fine, but when I press ctrl-m, I get message boz saying:
blablabla BasicProviderImpl::getScript: no script !

This error has already appeared here and I'll be able to find some trick. Just reporting that it doesn't work out of the box yet.

Regards, 
David Vonka

with feisty, everything was fine for me, but after upgrading to gutsy, I get the same error, but only after a few times using ooolatex (Ctrl+M, editing something, creating new fomula)

Any idea?

EDIT:
A manual install of the latest version (test5) does not work either. When I launch the macro using the macro manager (after the first error), ooo says
com.sun.star.uno.RuntimeException

by the way the exact error message when using ctrl+M is
com.sun.star.uno.RuntimeExceptionScriptProtocolHandler::createScriptProvider() 

maybe its not the same ...

---

### Post by chca on 2007-11-02
Now, I have made a completely new installation of Ubuntu 7.10 and installed ooolatex from 

deb [http://www.fyma.ucl.ac.be/ubuntu](http://www.fyma.ucl.ac.be/ubuntu) gutsy all

When I start OpenOffice Writer, ooolatex works fine until I save the document. Then I always get this error when I use Ctrl+M

> 
com.sun.star.uno.RuntimeExceptionScriptProtocolHandler::createScriptProvider() 


and this error when I start the script (ooolatex/ooolatexEquatation/main) manually:

> 
com.sun.star.uno.RuntimeException 


until I restart OpenOffice.

Very strange. Can anybody reproduce this issue who is using gutsy?

---

### Post by phetre on 2007-11-02
I don't have OOoLatex installed, but I get that error using the OpenOffice Lilypond extension (derived from OOoLatex) in Gutsy. Closing and reopening the document seems to help without having to restart OpenOffice entirely.

---

### Post by Toufik on 2007-11-08
A new version of OOoLatex is being tested. It was first expected for September but we had to wait for the Stix fonts that were being delayed every month to the next one...

This version should have a better installation and a better module for InlineEquation.

More news soon...

---

### Post by clconway on 2007-11-09
The debian package depends on tetex rather than tetex OR texlive. Trying to install gives:
```

$ sudo apt-get install ooolatex
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bakomafonts epstool tetex-base tetex-bin
Suggested packages:
  tetex-extra dvipng chktex lacheck rubber sam2p
Recommended packages:
  tetex-doc
The following packages will be REMOVED:
  latex-beamer texlive-base texlive-base-bin texlive-latex-base
  texlive-math-extra texlive-pdfetex
The following NEW packages will be installed:
  bakomafonts epstool ooolatex tetex-base tetex-bin
0 upgraded, 5 newly installed, 6 to remove and 0 not upgraded.
Need to get 27.0MB of archives.
After unpacking 14.6MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```
I would assume that texlive is sufficient...

---

### Post by Okuryo on 2007-12-01
> **chca said:**
> Now, I have made a completely new installation of Ubuntu 7.10 and installed ooolatex from 

deb [http://www.fyma.ucl.ac.be/ubuntu](http://www.fyma.ucl.ac.be/ubuntu) gutsy all

When I start OpenOffice Writer, ooolatex works fine until I save the document. Then I always get this error when I use Ctrl+M



and this error when I start the script (ooolatex/ooolatexEquatation/main) manually:



until I restart OpenOffice.

Very strange. Can anybody reproduce this issue who is using gutsy?

I got the exact same issue with Gutsy, OpenOffice.org 2.3.0 and OOoLatex 4.0.0-beta-2.

---

### Post by Dragon45 on 2008-02-07
I have that same issue, but I don't think it's related entirely to saving in my case. Occasionally I can save and still continue to use the macro normally. I will admit that saving greatly increases the chances of that createScriptProvider error.

---

### Post by anando on 2008-04-09
Is there any plan to package a deb for the newer OOoLatex 4.0.0-beta1 ? I wonder what is different ?

Thanks,
Anando

---

### Post by MarkieB on 2008-05-20
no longer participating in ubuntuforums.org

---

### Post by mikewhatever on 2008-05-20
> **MarkieB said:**
> Is there a bug with OOo2.4 [Hardy]? I'm seeing a little non-resizeable window for equation editing [Installation Method 2]

The last post from the author is dated Nov 8 2007. It looks like this thread has been abandoned.

---

### Post by Toufik on 2008-05-21
Yes it has been abandonned as the official website contains information for an easy installation ([http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/)).

Maybe, if I've time, I'll do a .deb ... maybe...

---

### Post by MarkieB on 2008-05-23
no longer participating in ubuntuforums.org

---

### Post by gorgor_bay on 2008-05-23
Just switch compiz fusion off, and OOoLatex will behave correctly. This is a bug related to compiz as the same behaviour happends with DicOOo

---

### Post by leopar31 on 2008-05-29
Do not know if this thread is alive ... Just came up in the search when I started  

I was having problems with ooolatex Installation on Kubuntu 8.04 (it is most likely generic to all *ubuntu). I have posted the problem and the way I solved it on OOOLatex forums on SourceForge. Just repost it here as it is obviously relevant...

FIRST POST - PROBLEM 
------------------------------------------------------------
Hi OOoLatex! 
 
I am having problems with Ubuntu Installation. 
 
Installation fails with : 
... 
sed: can't read /usr/lib/openoffice/share/config/soffice.cfg/modules/simpress/accelerator/default.xml/default.xml: Not a directory 
... 
 
I found that this is coming from installation bash script /var/lib/dpkg/info/ooolatex.postint which has lines:  
... 
if [ -d $INST/share/config/soffice.cfg/modules/simpress/accelerator ] 
then 
for ii in $( ls $INST/share/config/soffice.cfg/modules/simpress/accelerator/); do 
# REMOVE OLD CONFIG 
sed '/OOoLatex/d' -i $INST/share/config/soffice.cfg/modules/simpress/accelerator/$ii/default.xml 
# ADD THE NEW LINE JUST BEFORE END 
sed 's|</accel:acceleratorlist>| <accel:item accel:code="KEY_M" xlink:href="vnd.sun.star.script:OOoLatex.OOoLatexEquation.main?language=Basic\&amp;location=application" accel:mod1="true"/>\n&|' -i $INST/share/config/soffice.cfg/modules/simpress/accelerator/$ii/default.xml 
done 
fi 
... 
 
but in the $INST/share/config/soffice.cfg/modules/simpress/accelerator/ there are 3 folders "de", "es" and "fr" + the default.xml file which does not fit into ".../accelerator/$ii/default.xml" line obviously 
 
Any ideas how to fix it? 
 
Leo 
--------------------------------------

SECOND POST - SOLUTION    
-----------------------------------------------------------
Right 
 
Since nobody responded... 
 
It might be a problem of this particular package version build for ubuntu users in "http://www.fyma.ucl.ac.be/ubuntu feisty contrib" repository... but  
 
The problem was that this particular error stopped any updates on my machine because each time it tied to update it encountered this error and stop any updates installation!  
 
I thought about uninstalling ooolatex to get all other updates going, but apparently I was able to resolve the problem.  
 
What I did - I created "en-US" directory in "$INST/share/config/soffice.cfg/modules/simpress/accelerator/" and moved "default.xml" in there just like it was in "$INST/share/config/soffice.cfg/modules/swriter/accelerator/" 
 
Was it a known OOoLatex/Linux problem?  
 
I will post this on Ubuntu forums as well  
 

--------------------------------

;^) ... LEo

---

### Post by Toufik on 2008-05-30
You sould better remove OOoLatex and install directly from the website [http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/)  where you'll find a installation script for **any** openoffice (Windowd, Mac and of course Linux).

I'll change the first post

---

### Post by leopar31 on 2008-05-31
YES! Now I can remove it, but previously it was not possible because of this error. the entire "ADEPT machinery" was jammed.

AS for me it is OK the way it is organized in your repositories ... BUT!!! Please make "hardy" repository. It is LTS after all. Much more people will be using it. 

LEo

---

### Post by leopar31 on 2008-06-04
Toufik

Thanks for new installation instructions 

Regards
Leo

---

### Post by anando on 2008-07-09
Hi Toufik

Thanks for the new instructions for installation. Could you please add a small section on how to delete the ooolatex stuff once we install it using the new instructions ? Also, why did you decide to discontinue with the debs ? IMHO, they are far more easily installed and removed. If you need a hand - please let me know.

Thanks,
Anando.

---

### Post by Toufik on 2008-07-10
Single User mode:
> /usr/lib/openoffice/program/unopkg.bin remove net.sourceforge.ooolatex
Admin mode:
> sudo /usr/lib/openoffice/program/unopkg.bin remove --shared net.sourceforge.ooolatex

Concerning the deb, the biggest issues are 
  *  the acceptation of the license which is now bundle with OOoLaTex (that could be circumvent by modifying the .oxt)
  *  the fact that any .deb will use the Admin mode install. Therefore not allowing anyone to change the shortcuts and other configrations...
If you have any idea on how to deal with this, for sure, I'll make a .deb! That's far more useful!

---

### Post by jarondl on 2008-08-14
First of all Thanks Toufik!!
The guide is really helpful.
Anyway, EMF didn't work for me. PNG worked fine. 
I Solved it by installing libstdc++5
```
sudo apt-get install libstdc++5
```
Now EMF works excellent.

---

### Post by nbubis on 2008-10-12
Hmmm..
"emf" still doesn't work for me. I've installed latex2emf in (/usr/bin) and libstc++ as well. any ideas?

running oowrite from a shell I get (after trying to create an emf):

[FONT="Courier New"]GPL Ghostscript 8.63: Unrecoverable error, exit code 1[/FONT]

---

### Post by raycosm on 2009-02-01
Whenever I try to make a Latex equation, I get "BASIC runtime error. Object variable not set." I have the plugin configured fine, and Latex works because the Kopetex plugin works, so what gives?

EDIT: OOoLatex seems to work fine on my Kubuntu Intrepid laptop, so maybe it has something to do with Openoffice in Opensuse?

Picture of error:
[http://i41.tinypic.com/xds378.jpg]("http://i41.tinypic.com/xds378.jpg")

---

### Post by amylase on 2009-03-10
Hi every one, here is a very basic question about location of my LaTeX and Ghostscript. I have just installed OOoLaTeX following this thread. I am at the final step in OpenOffice's OOoLaTeX System Confirguation window which asks me this: 
> The macro OOoLatex uses external programs to generate the image of the equations. Enter below, the location of your LaTeX and Ghostscript binary distributions.

Question 1: I installed everything as outlined in this thread. What location do I now specify for LaTeX and for Ghostscript please?
Question 2: Ctrl+M totally ignored me. How could I get Ctrl+M to work?

Thanks very much.

[B]ADDENDUM
Problem solved!
For both path (for LaTeX and ghostscript) I just put down /usr/bin
OOoLaTeX was smart enough to seek in there for .latex and .gs
Ctrl+M macro problem also solved by applying test5[/B]

---

### Post by Toufik on 2009-03-15
Great you fixed it by yourself. For your information when looking for the location of an exectuable, try "which" in the terminal. For instance:
```
which latex
```
should answer
```
/usr/bin/latex
```

---

### Post by Rahul Biswas on 2009-04-10
I was totally frustrated to figure out Ghostscript and Latex. I tried using which but still it would cause problem. But the reply above saved my life..

---

### Post by FrenchyFungus on 2009-04-12
> **raycosm said:**
> Whenever I try to make a Latex equation, I get "BASIC runtime error. Object variable not set." I have the plugin configured fine, and Latex works because the Kopetex plugin works, so what gives?

EDIT: OOoLatex seems to work fine on my Kubuntu Intrepid laptop, so maybe it has something to do with Openoffice in Opensuse?

Picture of error:
[http://i41.tinypic.com/xds378.jpg]("http://i41.tinypic.com/xds378.jpg")
I'm getting this problem in Xubuntu as well.

Any ideas?

---

### Post by Mothinator on 2009-04-30
[QUOTE=raycosm] Whenever I try to make a Latex equation, I get "BASIC runtime error. Object variable not set." I have the plugin configured fine, and Latex works because the Kopetex plugin works, so what gives?[/QUOTE]

I suppose this is happening in Impress? 

I found on the answer in: [http://ubuntuforums.org/showthread.php?t=514585](http://ubuntuforums.org/showthread.php?t=514585)

Basically, everything in slide must be deselected.

---

### Post by Meson on 2009-05-02
> **Mothinator said:**
> I suppose this is happening in Impress? 

I found on the answer in: [http://ubuntuforums.org/showthread.php?t=514585](http://ubuntuforums.org/showthread.php?t=514585)

Basically, everything in slide must be deselected.

I'm having the problem in Writer and I've only once been able to get it to work. It seems SOMETHING is selected even when I think it's not.

---

### Post by FrenchyFungus on 2009-05-03
> **Meson said:**
> I'm having the problem in Writer and I've only once been able to get it to work. It seems SOMETHING is selected even when I think it's not.

Are there cells or tables in your document? Right click them and look for an option to unprotect them.

---

### Post by Meson on 2009-05-03
> **FrenchyFungus said:**
> Are there cells or tables in your document? Right click them and look for an option to unprotect them.

No, I've been trying to generate my equations in a blank document. I've found that certain symbols generate the error. For example:

```

% These work
a
adfadf
\pi r^2
1.9891 ~ 10^{30} ~ \mathrm{kg}

% These do not work
a = b
a \gg b
\pi r^2 = 0
1.9891 \times 10^{30} ~ \mathrm{kg}

```

The first error I get is "Incorrect format. \ Incorrect file format." Followed by "BASIC runtime error. \ Object variable not set."

And it points to this line in the macro.```
oDrawDocCtrl = oDrawDoc.getCurrentController()
```

---

### Post by Meson on 2009-05-03
I think the errors in my previous post might have to do with the fonts... ?

---

### Post by fari81 on 2009-10-19
Just a quick note: The font pack from mesh.dl.sourceforge.net is not complete. For example it is missing cmbx10.ttf that is basically the default bold font in equation modes (i.e., \mathbf). 

This font and other possibly missing fonts are available directly on the CTAN website:

[http://www.ctan.org/tex-archive/fonts/cm/ps-type1/bakoma/ttf/](http://www.ctan.org/tex-archive/fonts/cm/ps-type1/bakoma/ttf/)

You just need to copy them over to the fontfolder (see the first post for the location) and run fc-cashe (as shown in the first post). Restart OO and you're good to go!

---

### Post by LitusMayol on 2009-10-27
Hiya!

First of all, thank you for it!

Second, my problem. I've installed, run OOO and...

Appeared a window with two parts: "*Short Cuts*" (no worries with it) and "*System Directories*"

I've to fill two things "*LaTex*" and "*Ghostscript*". Whitout this lines it doesn't work.


Any idea of what I've to do?

Thanks!

---

### Post by Toufik on 2009-10-31
For Latex:
/usr/bin/latex

For Ghostscript:
/usr/bin/gs

or whatever the location of these progs on your system.

---

### Post by hendrikwout on 2009-11-04
I'm on Ubuntu Jaunty, I've followed the installation instructions. However I get the following error when I configure the plugin in openoffice:
BASIC-runtime-error.
An exception occured.
Type: com.sun.star.ucb.InteractiveAugmentedIOException
Message: an error occured during file opening.


After this the 'Expand'-buttton in openoffice works fine, the 'Equation'-button doesn't work (it says I have to configure it first).

Anyone has the same, or any ideas to resolve it?

---

### Post by Sjenitzer on 2009-11-09
Hi,

I 'm trying to install OOoLatex on Ubuntu 9.10 64, I followed the cook book from the first post and it works fine except that the latex2emf doesn't work. 

I get this error:

```
latex2emf: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```This package is installed, but it looks like latex2emf cannot find it. 
Any ideas?

---

### Post by fari81 on 2009-12-11
> **Sjenitzer said:**
> Hi,

I 'm trying to install OOoLatex on Ubuntu 9.10 64, I followed the cook book from the first post and it works fine except that the latex2emf doesn't work. 

I get this error:

```
latex2emf: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```This package is installed, but it looks like latex2emf cannot find it. 
Any ideas?

I get the same error on my 64 bit machine. It says libstdc++.so.5 not found, though I have it installed. 

```

fari@mani:~$ locate libstdc++.so.5
/usr/lib/libstdc++.so.5
/usr/lib/libstdc++.so.5.0.7

```

I guess since the binaries are compiled on 32 bit machines, they don't run on 64 bit machines. I tried compiling libEMF and latex2emf on my 64 bit machine, but no luck yet.

---

### Post by smelloscope on 2010-01-24
Has anyone else had problems with ooolatex after updating to 9.10?  I updated about a month ago, and now the emf mode doesn't work.  No matter what equation I enter, it outputs the last equation that I entered before the update.  I tried reinstalling the plugin, but no luck.  png mode works fine, though.

Has anyone else been having similar problems?  Or, any ideas about why it seems to be stuck rendering the same equation?

---

### Post by gazer22 on 2010-02-18
> **smelloscope said:**
> Has anyone else had problems with ooolatex after updating to 9.10?  I updated about a month ago, and now the emf mode doesn't work.  ...  png mode works fine, though.


Apparently, you need to install libstdc++5, which was removed from Karmic.

I found a nice set of instructions from this site: [http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/]("http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/")

For **Ubuntu 9.10 i386**
[LIST=1]
[*]Download the i386 Jaunty libstdc++5 package here: [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb")
[*]Install it: ```
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_i386.deb 
```
[/LIST]

For **Ubuntu 9.10 amd64** (I haven't tried this, I'm just copying from the above site...let me know that it works!)
[LIST=1]
[*]Download **both** the i386 and the amd64 packages:
  [LIST]
  [*][http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb")
  [*][http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb")
  [/LIST]
  [*]Install the amd64 package:
```
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_amd64.deb
```
  [*]Extract the libstdc++5 library from the i386 file:
```
sudo dpkg-deb -x libstdc++5_3.3.6-17ubuntu1_i386.deb ./tmp
sudo cp ./tmp/usr/lib/* /usr/lib32/ 
```
[/LIST]

---

### Post by chaanakya_chiraag on 2010-02-24
> **hendrikwout said:**
> I'm on Ubuntu Jaunty, I've followed the installation instructions. However I get the following error when I configure the plugin in openoffice:
BASIC-runtime-error.
An exception occured.
Type: com.sun.star.ucb.InteractiveAugmentedIOException
Message: an error occured during file opening.


After this the 'Expand'-buttton in openoffice works fine, the 'Equation'-button doesn't work (it says I have to configure it first).

Anyone has the same, or any ideas to resolve it?
I did not get the first error, but I did get the second.  Hit the Config button on the toolbar.  That should do it :)

---

### Post by smelloscope on 2010-02-28
> Apparently, you need to install libstdc++5, which was removed from Karmic.

I found a nice set of instructions from this site: [http://hsmak.wordpress.com/2009/12/0...n-ubuntu-9-10/](http://hsmak.wordpress.com/2009/12/0...n-ubuntu-9-10/)

Thanks, this fixed the problem! emf looks so much nicer than png :-)

---

### Post by Sjenitzer on 2010-04-26
Thanks it works for me now as well!

---

### Post by atentik on 2010-05-09
edit

---

### Post by tiresias54000 on 2010-06-08
hello all,

i have the same problem with the configuration:

> I'm on Ubuntu Jaunty, I've followed the installation instructions.  However I get the following error when I configure the plugin in  openoffice:
BASIC-runtime-error.
An exception occured.
Type: com.sun.star.ucb.InteractiveAugmentedIOException
Message: an error occured during file opening.


another thing: i can type something like \alpha symbol in my documents, but if i try \LaTeX, it doesn't work, do you know why?

regards

---

### Post by ovis23 on 2010-09-23
I've run into a bit of a problem. I'm on 10.04 64-bit.
I've added OOoLatex from the extension manager. For Latex and Ghostscript locations, I've used:
/usr/bin/latex
/usr/bin/gs

A pop-up dialog then informs me that
"The program 'gs' is not located at [\n] /usr/bin/gs"

However,
$ which gs
/usr/bin/gs

What am I missing?

Thanks,
ovis23

---

### Post by Sjenitzer on 2010-09-23
You only need the path to the directory:
```
Latex:
/usr/bin/ 
Ghostscript:
/usr/bin/
```

---

### Post by ovis23 on 2010-09-23
> **Sjenitzer said:**
> You only need the path to the directory:
```
Latex:
/usr/bin/ 
Ghostscript:
/usr/bin/
```

Ha! Wonderful, thank you kindly. I was about to begin the unfriendly task of reading the source (having skipped the instructions entirely).

---

### Post by zandreas on 2010-09-25
Hello all,

I installed OOoLatex a couple of days ago and it works quite fine, apart 
from a couple of things:

1) I can produce equations as .png, but not as .emf. Once I try to produce a .emf, I get the error message:
Script error: the postscript file was not converted to emf...

I have followed all steps described in the forum (obviously I did sth wrong however), installed libstdc++5 and all, but I still get this message

2) Once I close the Impress file and reopen it, I can no longer edit my equations. Am I supposed not to be able or is there sth wrong with my installation?

I'm running on Ubuntu 10.04

Thanks, 
Andreas

---

### Post by chaanakya_chiraag on 2010-09-25
I've gone over to complete LaTeX.  Trust me, it's worth the time and effort of learning, especially if you are looking at this extension.  That's because no matter how much you try, right now, documents using OOLaTeX are not really portable.  Yes, you can save it as a MS Office document, but then (I'm pretty sure) you lose the ability to edit the equations.  If you just use LaTeX, you can edit it on any computer (notice I said **edit**, not compile) because it's just a text file.  If you need to compile, well...that's the only disadvantage ;)  I got around it by installing it on my account at school, but I'm pretty sure other schools have a better security system :D

---

### Post by ravi84m on 2010-10-20
basic runtime errorkept lingering so i uninstalled. hope to find something that works.

---

### Post by chaanakya_chiraag on 2010-10-20
Again...just use LaTeX and save as a PDF.  Then, you can convert the PDF to JPG or similar and import into your OpenOffice document.

---

### Post by vwishndaetr on 2011-02-20
Hello. Quick question for the crowd. I am a linux newb, so bear with me.

I followed the procedure and everything worked great, but I am a bit unsure as to what I am "linking" for the "Latex" and "Ghostscript" in configuration. This whole feature is not working for me, obviously, because these are not linked to anything.

Can someone shed some light for a newcommer?

Thanks.

---

### Post by vwishndaetr on 2011-02-20
Found the answer on pg 7.

\usr\bin

Thanks.

---

### Post by samhau on 2011-02-28
FYI if ur using ubuntu 10.4, u may also need **libstdc++.so.5 ** in order to convert latex to emf

```

wget http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb

sudo dpkg -i libstdc++5_3.3.6-18_i386.deb

```

---

### Post by amater on 2011-07-25
Check ooolatex ([http://extensions.services.openoffice.org/en/project/ooolatex](http://extensions.services.openoffice.org/en/project/ooolatex)) in your extension and then check if you have installed latex and Ghostscript (they are usualy placed in /usr/bin). 

Set path in ooolatex config for latex (usualy is /usr/bin) and for ghostscript (usualy is /usr/bin)...

If they are not there, you can find them with terminal 
(type *which latex* 

and you get the path - something like this:

*/file/file2/file3/latex* 

and you !!must!! take path: */file/file2/file3* ](*,)

whitout program!!!
)

If you want **emf** in ooolatex you type 

sudo apt-get install libstdc++5 

in terminal...

If you take al this correct it must work. If doesn't you may not do it all correct. :)

(I mean that all this work on ubuntu, Kubuntu, Xubuntu, ...)

---

### Post by KeithSloan on 2011-08-16
Okay I installed the OOoLatex-4.0.0-beta2-linux.oxt on OpenOffice 3.2 as supplied with Ubuntu 10.04 LTS but when I try Equation type in some Tea and then press Latex I get error :(

Basic runtime error
Property or Method not found: Graphcrop

Seems like I am missing some prereq.

And Ideas?

---

