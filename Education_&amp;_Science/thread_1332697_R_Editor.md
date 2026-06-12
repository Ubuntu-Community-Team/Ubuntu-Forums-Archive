---
title: "R Editor"
date: 2009-11-20
forum: Education &amp; Science
---

### Post by gunksta on 2009-11-20
Apology - This turned into a rather long post but I am happy to say that it is NOT a rant. In contrast,  it is actually rather constructive. While I have written this for K/Ubuntu, it is relevant to other Linux distros.

A couple of days ago, there was an interesting discussion on the [REvolution Computing blog]("http://blog.revolution-computing.com/2009/11/installing-ess-on-ubuntu.html"), where David discusses installing and using ESS as a front-end for R. His discussion of ESS got me to thinking about R's default user interface on Linux (and other operating systems) and how accessible they made R to new users. While the default R interface on Windows and OS X are light years from offering the kind of accessibility and ease-of-use offered by SPSS or other graphical tools, they do make it easier for new users to know where to start on their journey into the land of single-letter Googling.

On Windows and OS X, the default interface for R is a Graphical User Interface (GUI). The screen-shots I have seen of the [R interface on OS X]("http://image.versiontracker.com/scrnsht/7831/167953/456R_snap1.jpg") look very nice. I have used the [Windows interface]("http://www.softpedia.com/screenshots/R-for-Windows_1.png") and while it is not as sophisticated as the interface provided by OS X, it is adequate.

In contrast to both, the default Linux interface is straight-up command-line heaven (or hell, depending on your point of view). I rather like the spartan, CLI interface provided by R, but many others do not. The most important reason I think the current default option is a problem is that many new users have a hard time locating R in the menu, because it's not there. Imagine a new users' surprise. After downloading and installing R, which is a fairly hefty download, the user is unable to find an icon or link to start the program.

This isn't exactly newbie-friendly. In fact, I will admit that I spend several minutes looking for a menu entry before figuring out that there wasn't one. And I figured this out by looking at the contents of the core package and realizing that there was no R.desktop file installed but there was a program called R in /usr/bin.

David's post on the REvolution Computing blog discusses [ESS]("http://ess.r-project.org/") as a front-end for R. I have used ESS in the past and it is a very good way to interact with R. Unfortunately, I had some problems with ESS and EMACS in general which eventually led me to abandoning it, but for many experienced users this is an excellent choice. In fact, it is obvious that many of the users on the R-users mailing list use ESS exclusively or nearly exclusively.

Lately, I have been using the new [Vim-R-plugin2]("http://www.vim.org/scripts/script.php?script_id=2628") for . . . [Vim]("http://www.vim.org/"). It is similar to ESS in many ways but uses [screen]("http://www.gnu.org/software/screen/") to connect Vim to R. I have been using screen at work for other reasons and the integration between Vim, R, and screen makes my life much easier. As a nice added bonus for Ubuntu users, the plugin works just as well with byobu.

While editor extensions such as Vim-R-plugin2 and ESS are great options for experienced users, these tools do not provide an adequate interface for new users. There are many reasons for this. 

[LIST]
[*]Learning curve -- Don't pretend there isn't a learning curve.
[*]Not installed by default when you install R.
[*]Neither tool provides a menu entry to start R.
[/LIST]
 My point is not to critique either tool. They both rock just the way they are. But, they are not good tools for new users and any attempt to shoe-horn them into meeting the needs of new users will fail, miserably. Asking a new user to learn EMACS and R at the same time is enough to send many intrepid analysts running for the safe hills of SPSS syntax.

Inevitably, someone will point out that while Python is installed by default on Ubuntu, IDLE is not and therefore Python does not have, by default, a menu entry in the menu. Hopefully everyone will read this far before writing a response.  :-) To me the difference between Python and R is simple. The people looking for Python are going to have at least some technical skills, otherwise they will never hear about python and don't need to interact with it. In contrast, non-programmers do learn about R and want to try it out. In the past year, I have seen articles about R in the NY Times and other mainstream publications. While R is unlikely to ever achieve an installation base similar to Python, it is an increasingly popular tool. More importantly, many of the people expressing interest in it are not programmers or Linux users with lots of Command-Line-Fu.

What is needed is a sane front-end for new users that will help ease them into R. I am ***not*** saying that R needs an interface like SPSS or [PSPP]("http://www.gnu.org/software/pspp/"). I would be more than satisfied by something similar to what is provided for Windows or OS X users *(perferably more like the OS X interface)*. At the very least a new user should be able to install R and find it/run it from their menu! Fortunately, there are several front-ends to R.

[LIST]
[*][tkStartGUI]("http://archpub20.cs.ccu.edu.tw/cgi-bin/dwww?type=file&location=/usr/share/doc/r-base-dev/library/tcltk/help/tkStartGUI")
[*][RCmdr]("http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/")
[*][Rkward]("http://rkward.sourceforge.net/index.php?content=overview")
[*][JGR]("http://rkward.sourceforge.net/index.php?content=overview")
[*][Cantor]("http://edu.kde.org/cantor/")
[*][Rattle]("http://rattle.togaware.com/")
[*]Kate/Gedit (The default text editors on K/Ubuntu)
[*][Others]("http://wiki.r-project.org/rwiki/doku.php?id=guis:projects") - There are several others.
[/LIST]
 Many of these options present problems as the "default" GUI interface for R. For starters, Cantor hasn't actually been released yet and like Rkward, is designed for the KDE desktop. While both apps will work wonderfully under Gnome, XFCE, or any other desktop environment, both tools have a large dependencies list. Installing either of these tools, plus R on a non-KDE based environment will require a large download that many new users may not like. Besides, R is not part of the KDE project and requiring a new user to install KDE when installing R is absolutely silly (and I use Kubuntu and think Cantor is an interesting project). 

Tools such as JGR or Rattle are not currently in the Ubuntu repositories, which makes using them as the default interface difficult to say the least. They can be installed via CRAN, but that's not the first thing that a new user is going to want to do. 

Kate and Gedit include syntax highlighting for R and can embed a terminal in the editor but, new users will not find this easily and it does not address the need for a menu entry.

We have narrowed the list to tkStartGUI and RCMDR. tkStartGUI is actually installed by default, although it's rarely used. If you are already running R, it's easy to get it running, if you want to. Simply enter these two commands into an existing R session:

    library(tcltk)
    tkStartGUI()

This should start the simplest graphical interface you have ever seen. While it's not pretty (tcl/tk), it is functional AND odds are good that if you are reading this long-*** post, you already have it installed! You will quickly notice that this interface is actually less useful than the basic interface provided on Windows. 

While Rcmdr is not installed by default, it is easy to install:

sudo apt-get install r-cran-rcmdr

On my machine, installation of Rcmdr required me to install 22 megabytes of additional R extensions. Most users can spare 22 megabytes, or more and this is a much smaller download/installation than RKward on a Ubuntu system. But, much like tkStartGUI, Rcmdr does not come with a .desktop file and can not be located from within the K/Ubuntu menu. Starting Rcmdr, from within R is easy:
```

library(Rcmdr)
Rcmdr()
```

This should present you with a nice easily used GUI for R. While it's not as nice as the OS X interface, it is an ugly (tcl/tk) but capable interface for R.

<< I apologize to any tcl/tk developers who read this. I don't know why I have something against the toolkit. >>

It is possible to set up a default Ubuntu installation to include a menu entry for either tkStartGUI or Rcmdr. Given that tkStartGUI is already installed by default this seems like a good place to start. And, logically, Rcmdr should have a .desktop file when installed, although I don't think it should be installed by default, although setting it to recommended might be a good idea (it may be already, I have to look). 

These two proposals would help new users find R and get started and bring a certain degree of parity to the different platforms served by R. As an added bonus, setting things up this way would have practically no affect on users who are already satisfied with the command-line approach. Most would never even notice the additional entry in their menus and it wouldn't hurt them if they did.

Comments?

When I get something banged out I'll stick it up here for others to look at before I try submitting it to Canonical.

---

### Post by ahmatti on 2009-11-22
Its good that you brought this up and thanks for the long post. Having a menu entry for R would definetly be a good idea for newbies.

Given that the tkGUI is really limited I would rather add a shortcut for starting R in the default terminal and maybe display a infoscreen about the GUI options at startup. 

I also think that the default interfaces for Windows and Mac give you a good start and it would be nice to have something similar on Linux. Although, they are not really efficient once you get to know R and a lot of people rather use ESS or Vim etc.

---

### Post by memilanuk on 2009-11-22
Just a thought... I think it might be worth sticking with something that is cross-platform, so that the new user at least has a chance of being able to compare notes with their counterparts who may be running other operating systems.  

If they have problems, and they are running something that *only* runs on *nix platforms (and lets face it, all propaganda aside - M$ still has the lion's share of the desktop market) then they are going to have fewer resources for getting their problems fixed and be on their way actually *using* the computer to do useful work (with R).

Conversely... if they happen to want to lure their friends and associates over to Linux/Ubuntu, it might be helpful for those folks to be able to install said program on their M$ machines, and see how *useful* FLOSS can be - both R as a language and whatever GUI front-end - to get them interested in coming more fully into the fold (installing Ubuntu on their machine...).

I've only used RCmdr myself... mainly because its there, it's mature (been around going on what, five years now), and it works fine on both my Windows machines (Win XP before, Win Vista currently) and my Macbook (OS X 10.4).  tkStartGUI() does not run under Windows, and so far I've not had a chance to run JGR from either Windows or Mac.  The caveat being... Tck/Tk is, speaking frankly, a bit on the fugly side - especially when viewed from the perspective of a Mac user ;)  It may not be the best choice asthetically to 'impress' a new user.  I have heard that Tcl/Tk doesn't *have* to be quite so bland; that it could be almost as attractive as some of the Java GUIs depending on something or other.  Not much help on that regard... though I wonder if the person maintaining Rcmdr could be talked into taking a look at that part?

HTH,

Monte

---

### Post by gunksta on 2009-11-22
> **ahmatti said:**
> 
Given that the tkGUI is really limited I would rather add a shortcut for starting R in the default terminal and maybe display a infoscreen about the GUI options at startup. 

It would also be possible to do both. Given the fact that most Linux users of R use the CLI interface is proof enough that it is good enough to get work done. On the other hand, it is a little frightening to the uninitiated, but starting R in the default terminal does have the huge advantage of providing an icon in the menu that does something, the lack of which I think is the biggest problem.

> **ahmatti said:**
> 
I also think that the default interfaces for Windows and Mac give you a good start and it would be nice to have something similar on Linux. Although, they are not really efficient once you get to know R and a lot of people rather use ESS or Vim etc.

I would love to package the OS X interface but it looks like it is based on Cocoa? or whatever they call their their toolkit. I'm not sure that's very feasible (rats!). And I read some of the documentation and it looks like th Windows GUI is using the win32 API, so it's not going to work on Linux either, unless we want to start installing the Windows version of R, which seems kinda pointless.

---

### Post by ahmatti on 2009-11-22
> **gunksta said:**
> 
I would love to package the OS X interface but it looks like it is based on Cocoa? or whatever they call their their toolkit. I'm not sure that's very feasible (rats!). And I read some of the documentation and it looks like th Windows GUI is using the win32 API, so it's not going to work on Linux either, unless we want to start installing the Windows version of R, which seems kinda pointless.

I don't think it is not possible to port the win or mac version to Linux, so achieving a similar GUI would require writing a native Linux app using either Qt or GTK. And ideally get it included in the R base. That would be a project that I'd be happy to contribute to, but I'm afraid I don't have enough knowledge/time to write it myself.

---

### Post by samden on 2009-11-22
I agree with your analysis gunksta, we do need a menu entry for R. Much as I feel RKward is excellent too, I agree with your criticism that it requires KDE libraries so should not be the default.

The bare minimum requirement for a useful R GUI for a newbie is:
- A script window
- A terminal window (at least for output)
- A data view window (newbies are generally used to spreadsheets)

Tcltk does not provide an obvious script window, just a terminal. It is therefore too limited to be a useful option for most users in my opinion.

Rcmdr on the other hand has pretty much everything you need - a script window, an output terminal window, and a good data viewer. It does not include the ability to type directly in the terminal but this is unnecessary for a newbie.

And when I booted it I realised I'd seen it on Windows somewhere before also...

So I'd put in my vote for Rcmdr as the default. I wouldn't use it myself (I'm the text editor + terminal type, even on Windows I use Notepad++ with an R plugin), but it fills the requirement fairly well, is already available in the repositories, and doesn't have very high system requirements.

---

### Post by gunksta on 2009-11-22
I have discovered that it is possible to start the default tcltk GUI directly from the command line. In bash, type:

```
R -g "tcltk"
```

The end result should be the uber-simplistic default GUI. But, there's a problem. If you close via the menu, everything is fine. But, if you exit the GUI via the window manager (close button in the top right corner) the GUI closes but R does not, since it hasn't been told to save the workspace or not. It's stuck. This is clearly a problem. This, combined with the relative lack of functionality that you have all pointed out clearly makes the included GUI a bad option.

I'm going to look at the packages included in r-recommended and see how these differ from the requirements for Rcmdr, which I agree is quite possibly the best option for a "default" R GUI.

For KDE users, I wish there was a way to recommend Rkward or Cantor (when it is ready) as the GUI instead, but that's quite a bit more complicated.

---

### Post by gunksta on 2009-11-22
I am beginning to understand why there is not default graphical tool under Linux.

```
Rscript -e "library(Rcmdr)"
```

Results:
[INDENT]Loading required package: tcltk
Loading Tcl/Tk interface ... done
The Commander GUI is launched only in interactive sessions

Attaching package: 'Rcmdr'


        The following object(s) are masked from package:tcltk :

         tclvalue[/INDENT]

It may be that the best option IS to just open the CLI interface in the default editor. Dangit.

---

### Post by gunksta on 2009-11-22
On my home computer, I installed Rcmdr to look at this a little more carefully. Turns out, when you do this, you also install a .desktop file. Rcmdr is now in the menu (Education -> Mathematics -> Rcmdr ) on Kubuntu 9.10

There is an included shell script.

Perhaps the best approach is to add r-cran-rcmdr to r-recommended.

---

### Post by earlycj5 on 2009-11-23
Ok I'll bite.

I've never understood the whole "It's KDE it's Gnome, it's another toolkit" etc.

I use the right tool for the job.  I mean good heavens, have you looked at the installation size of SAS on Windows lately?  It's HUGE.  It makes RKWard with some KDE library dependencies and R and it's packages look silly small.

Not saying that RKWard is the be-all, end-all (though it's open currently on the monitor opposite the one on which I'm typing currently).  Cantor looks very interesting as well.

Unless the R community actually puts together a front-end like Windows or Mac, I wish they would, then what's wrong with suggesting one of these more full-featured IDEs.  Hard drive space is cheap these days and if I'm a new user I'm more likely to be put off by the look/interaction of TCL/TK (heck I'm an experienced user and I still am) than by something that's QT or GTK based and integrates with the desktop theme I'm using.

I've only used the Mac interface once, and the windows interface several times.  The Mac interface left me impressed, I'm not so much with the Windows version.

With KDE4 working with Windows now and RKWard offering a Windows port it's an ideal place for people new to R to start IMO if they want to move to Linux whether or not they use Kubuntu.

I'd be happy to see something written in strictly QT or GTK so that we don't have this "KDE vs. Gnome" argument anymore when it comes to R editors/IDEs but you can still get desktop integration as far as looks and feel.

I've tried ESS, just couldn't get the hang of it.  Not saying it's not a good tool, but I'm a pretty experienced Linux user and I just never got the hang of it.  I can't imagine being a new R user and being confronted with that.  R is hard enough to learn by itself, then you throw in that learning curve of EMACS and well, you know.

Having said all that I just installed Rcmdr and took a look at it.  If it's an issue of libraries, then I'd say rcmdr should be a default interface for R in Ubuntu as they're already there and you just need a few more packages for R to make it run.

I do remember installing R and going through all this some years ago.  Wondering how I accessed it.  Not understanding that I had to type "R" at the CLI.  So I think you're onto something here gunksta.

---

### Post by samden on 2009-11-23
Gunksta:> Perhaps the best approach is to add r-cran-rcmdr to r-recommended. Sounds about right to me.

Earlycj5:> I've never understood the whole "It's KDE it's Gnome, it's another toolkit" etc.

I use the right tool for the job. I mean good heavens, have you looked at the installation size of SAS on Windows lately? It's HUGE. It makes RKWard with some KDE library dependencies and R and it's packages look silly small.
I agree, I use Gnome or Fluxbox but have no problem using the odd KDE program, and I used to use Rkward extensively. However r-recommended has to cater both for newbies and for experienced users. 

Certainly Rkward might give a nice interface for a newbie. But if I am installing a package called "r-recommended", I expect to just get bare-bones R with the most essential packages, not a whole stack of KDE libraries as well. Sure hard drive space is cheap these days, but bandwidth is still limiting for many users in many countries (I have a 2GB cap at home, and only have broadband because I invested a thousand dollars in wireless equipment, most internet users in my area are still stuck with dialup). This might sound like the dark ages to some users in Europe, America, or the richer areas in Asia, but is the reality for most of the world. So it is vital that we do not make what users expect to be a basic package containing the absolute essentials into a big bloated installation containing packages that many users may never use.

Rcmdr is small enough to not bloat it too badly. But any larger than that and you could cause difficulties for some users.

The best way to show new users that better interfaces exist may be to have a link from the "Add / Remove Software" application entry for R to a webpage outlining all the different available software for running R, and how to install it. A new user will probably see this. A user that is proficient enough to install with the command line will have less need to see it.

---

### Post by gunksta on 2009-11-23
> **earlycj5 said:**
> 
I use the right tool for the job.  I mean good heavens, have you looked at the installation size of SAS on Windows lately?  It's HUGE.  It makes RKWard with some KDE library dependencies and R and it's packages look silly small.

I've never used SAS in my life, but I do think your comparison is interesting. Out of curiosity, just how big is it? Is there a good breakdown on the SAS site showing what features are included in the base installation of SAS? I looked at their website for a second and drowned in the meaningless jargo, catchphrases, and scores of text.

Although it is a little plain and dated, comparing the [SAS]("http://www.sas.com/") website to the [R ]("http://www.r-project.org/")website really does make one appreciate the beautiful spartan simplicity/uasability of the R Project's site.

While I always done my flame-proof pants before logging into any forum, I do **NOT** want to start a Gnome v. KDE fight. I think most Linux users respect and appreciate both desktop environments. In the case of R, it is most important to select a tool that is being actively maintained and will be available in future versions of Ubuntu. That should be the number 1 criteria. While Rkward is a nice tool, there was a time during the transition to KDE4 when it was (or appeared to be) quite dormant. But, after playing around with it a little today, it is a nice tool, although I really really like some of the shortcuts in the new vim-rplugin2 (for example, run current paragraph/function shortcuts).

> **earlycj5 said:**
> 
Not saying that RKWard is the be-all, end-all (though it's open currently on the monitor opposite the one on which I'm typing currently).  Cantor looks very interesting as well.

Unless the R community actually puts together a front-end like Windows or Mac, I wish they would, then what's wrong with suggesting one of these more full-featured IDEs.  Hard drive space is cheap these days and if I'm a new user I'm more likely to be put off by the look/interaction of TCL/TK (heck I'm an experienced user and I still am) than by something that's QT or GTK based and integrates with the desktop theme I'm using.

I've only used the Mac interface once, and the windows interface several times.  The Mac interface left me impressed, I'm not so much with the Windows version.

Agreed. tcl/tk is one of the ugliest things running on a modern Linux desktop. I take one look at those widgets and I get flashbacks from 1995.

You're right - in most cases, hdd space is cheap. But there are some fringe situations (netbooks for example) where hard drive space is NOT cheap (SSD anyone). (I really want one of these to replace my aging laptop for when I'm on the road.)

This weekend I noted that Rcmdr does now install a menu entry. This was not the case in past releases (although I'm not sure when this changed).

The more I look at this, and a few other issues in Linux, the more I think that the problem is one of familiarity / organization and not the applications themselves. Tools like Synaptic make finding Rkward hard, because they drown in the long alphabetical list of choices unless you search for the package itself. 

Adding r-cran-rcmdr and it's remaining dependencies to r-recommended is a nearly painless way to make R easier to find after installation but this assumes that people are able to locate r-recommended which isn't a given in the current structure. 

I am becoming increasingly convinced that Mark S. is, once again, way ahead of us all here. I want to learn more about the immediate plans for the Ubuntu App Center. There are some good tools out there for R, and it's entirely possible that the community will struggle agreeing to use one or the other, but that doesn't change the underlying fact they are hard to find.


> **earlycj5 said:**
> 
I'd be happy to see something written in strictly QT or GTK so that we don't have this "KDE vs. Gnome" argument anymore when it comes to R editors/IDEs but you can still get desktop integration as far as looks and feel.

There are several other good user interfaces to R. Rattle and JGR are the most obvious and are currently only installable via CRAN. Maybe the goal should be to help get these packages into Lucid and then work on making it easier to find the interfaces when R is installed. For example, apt-get will give you a list of packages that "recommended" when you install a new application. This makes it easier to install all of the relevant dependencies, but it doesn't help you find and install similar software that also might be of interest to you. I would really like to know if the goals of the App Center include making it easier to find relevant software, even if these suggestions have nothing to do with apt-get and are instead human-based suggestions based on installation base and Ubuntu developer reviews. Wouldn't it be neat if you used the App Center to install R and then had it suggest that you install a GUI and gave you a list of choices?

---

### Post by earlycj5 on 2009-11-23
> **gunksta said:**
> I've never used SAS in my life, but I do think your comparison is interesting. Out of curiosity, just how big is it?


I'll have to check, right now my U installs over a SAMBA server it's so large now.  The Linux version was five CDs IIRC, this is the Windows version that I'd be able to compare.  Still, I guess five CDs gives you an idea...

> **gunksta said:**
> You're right - in most cases, hdd space is cheap. But there are some fringe situations (netbooks for example) where hard drive space is NOT cheap (SSD anyone). (I really want one of these to replace my aging laptop for when I'm on the road.)

Yeah, I've got one w/ a 16GB SSD.  I love it.  I installed Crunchbang and then installed RKWard.  LOL!  Still, you have a good point.  I'm guessing that my R programming is more important to me than your average Linux user so space is of importance there.

> **gunksta said:**
> This weekend I noted that Rcmdr does now install a menu entry. This was not the case in past releases (although I'm not sure when this changed).

The more I look at this, and a few other issues in Linux, the more I think that the problem is one of familiarity / organization and not the applications themselves. Tools like Synaptic make finding Rkward hard, because they drown in the long alphabetical list of choices unless you search for the package itself. 


Agreed, unless you know to look for it, you'll not find it.


> **gunksta said:**
> Wouldn't it be neat if you used the App Center to install R and then had it suggest that you install a GUI and gave you a list of choices?

I was thinking that as I was typing my first reply.

---

### Post by ahmatti on 2009-11-24
Interesting discussion everyone!
 
As I see r-recommended contains the recommended packages that come with R-source and are installed in all platforms. If we wan't to add Rcmdr to r-recommended then I think we should try to get in as recommended package for the whole R project, not just Ubuntu. That way we could get a consistent installation also for other distros and the same content of r-recommended in Ubuntu and CRAN repos. 

Getting the GUI packages recommended in app center when installing R would be great! That would probably be more helpful, because I don't think anybody is going to stay with Rcmdr for long, no offense.

@gunksta LOL about the flame-proof pants :D

@earlycj5 R is very important for me too, but I still consider Rkward a waste of space since I use ESS or plain terminal ;)

---

### Post by earlycj5 on 2009-11-24
> **ahmatti said:**
> @earlycj5 R is very important for me too, but I still consider Rkward a waste of space since I use ESS or plain terminal ;)

Yeah, like I said, I tried ESS, just never got the hang of it.  Just not my thing, I know RKward isn't everyone's best app either. Just saying, my priorities mean that I don't mind giving up a bit of space to install it.

I've built my workflow around it as I'm sure you have ESS or the command line.  I still use the command line quite a bit, in fact I'm using it right now rather than RKward.  Just depends on the user and the situation.

I don't think there is an "ideal" package for every user *per se* but there should be a way to highlight the interfaces available to new users unfamiliar with R.  I think we all agree on that.  :)

---

### Post by slowtrain on 2009-12-13
The R situation in Ubuntu is a crying shame.  Ubuntu has great appeal for the scientific / academic communities, but one of the most important programs for these communities, statistics software, is difficult for many users to install and use in Ubuntu because it installs without appearing in the Applications menu and without a GUI.  

I'll have to try some of the GUIs mentioned here (thanks folks)--new to me.  My impression, though, is that JGR has quite a following, and it is something I've used on Windows as well as Linux.  It's lightweight--only about 1MB, slicker than any tcl interface I can imagine, and installs fairly easily via a few commands, except in Ubuntu.  

Turns out that the version of R in the standard Synaptic repository is not generally up to date.  If you then try to use install.packages("JGR") in R to install JGR, the CRAN repository may tell you there is no JGR package--if there is no current JGR package in the repository that is consistent with your out of date version of R (or you could get errors).  More generally, if users want to try newer R packages, the old version of R in Synaptic will be a problem.  

Someone wanting to use JGR or up to date R packages needs to install an up to date R repository and gpg key for the repository as described in [http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/).

I think a partial solution for the problem raised here is for Ubuntu to include an up-to-date version of R.  Including a READ.ME file that explains the 4-5 commands needed to download and set-up JGR would help.  Better would be having Synaptic take care of this (can it?) or perhaps offering some GUI alternatives and then installing the one chosen.

---

### Post by euler_fan on 2009-12-15
All choices of front end aside, how many people who read the manual (where is specifically says to drop into your favorite shell, type ``R'' and hit enter) have had trouble finding and getting into R?

Before we get all bent out of shape about the need for a link to the shell (honestly, not that big of a deal either way), we need to ask if this is a problem and if the people with the problem need to go read the manual first (and let's face it, the intro to R is one of the best primers out there for something which is better compared to a programming language than an app).

Full disclosure: I think ESS or any similar system (the vim thing mentioned earlier is fascinating but ultimately a matter of taste) is where any serious statistician is going to end up in order to (1) document their search for patterns and (2) replicate them over time.

---

### Post by earlycj5 on 2009-12-15
> **euler_fan said:**
> All choices of front end aside, how many people who read the manual (where is specifically says to drop into your favorite shell, type ``R'' and hit enter) have had trouble finding and getting into R?

Before we get all bent out of shape about the need for a link to the shell (honestly, not that big of a deal either way), we need to ask if this is a problem and if the people with the problem need to go read the manual first (and let's face it, the intro to R is one of the best primers out there for something which is better compared to a programming language than an app).


While it's certainly *ideal* to think that people read the manual before starting, in reality it doesn't happen.

---

### Post by gunksta on 2009-12-15
Of course people *should* read the manual first, but many don't. 

The KDE Software Compilation apparently agrees that mathematical programs like R, Octave, etc. need better front-ends on Linux. The 4.4 release will include a program called Cantor that is specifically designed to be a front-end for R and other math packages.

Regarding JGR, I think it would be much better to ship Ubuntu with a JGR binary that works with the version of R that ships with Ubuntu. I do not think users should be instructed in how to access the non-Ubuntu R repository. Obviously this repo has to be disabled before upgrading the computer and while Debian is really really good at juggling lots of repositories, it seems silly to ask every R user on the Linux platform to use a non-distro repository.

Because R and Ubuntu will (probably) never sync their development time-lines, there is an on-going problem when users try to download anything from CRAN. This is a silly limitation that affects every Linux distro. The R-Project should maintain a set of mirrors that include downloads for older versions of R. Mirrors for distros and other projects (CPAN) aren't as restrictive as CRAN. Honestly, this limitation is not Ubuntu's fault. It's the R-Project's. Hard-drive space is cheap. It is affordable to maintain binaries from past versions (up to a point).

---

### Post by samden on 2009-12-15
euler_fan, R users come in all types. Sure there are the programming people who are familiar with computers. But there are also many who have just come from Windows, and expect to install an application and have a nice wee button to click to make it come up. That doesn't seem too much to ask, especially if we want to expand the user base.

---

### Post by slowtrain on 2009-12-16
gunksta, granted that a good solution would be for Ubuntu to include in its repositories both a version of R and JGR that work together.  The difficulty, as you mention, is that CRAN doesn't retain much by way of older versions of its software.  While that might be CRAN's fault, this doesn't make things any easier for many R users in Ubuntu.  I'm not a high-level Ubuntu programmer, but I wonder whether there is some software that could insure that Synaptic's versions of R and JGR stayed synchronized with that of CRAN?

---

