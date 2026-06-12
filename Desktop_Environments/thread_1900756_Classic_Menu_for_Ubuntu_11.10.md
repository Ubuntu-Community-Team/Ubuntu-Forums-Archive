---
title: "Classic Menu for Ubuntu 11.10"
date: 2011-12-27
forum: Desktop Environments
---

### Post by aimwin on 2011-12-27
edit 29/12/2011
[SIZE="3"]**Option 1, Classic Menu (modified)**[/SIZE] as in old Ubuntu version. Easiest Method.

**[SIZE="3"][COLOR="Red"]You must use Edubuntu 11.10 DVD[/COLOR][/SIZE] for installation instead of [SIZE="2"]Ubuntu 11.10 CD[/SIZE]**
[COLOR="Red"]

This Edubuntu installation method, 
you can logout and login with choices to choose Unity or Classic Menu anytime, (not Gnome3, pls see below edit 6/1/2012)
But only one style of Desktop only, not both style in one Desktop as option 3.
[B][SIZE="2"][I]AND no need for Command Line nor hassled manual tweaks after installation
It is Classic Menu Ubuntu 11.10 out of the box.[/I][/SIZE][/B][/COLOR] 

There will be option to choose Gnome Classic menu during installation.
AT the end you will get exact the same menu as[B][SIZE="3"] [this tutorial]("http://www.psychocats.net/ubuntu/classicgnome") 

And it is look like [ weblive 11.04]("http://edubuntu.org/weblive")[/SIZE][/B] 
[COLOR="Red"]**[SIZE="3"]==> Have you try "Weblive" Edubuntu/UBUNTU Online without installing on your hard disk.[/SIZE]**[/COLOR]


[B][SIZE="2"][SIZE="3"][COLOR="Blue"]Edit 6/1/2012
From my own experience.
Do not install Gnome-shell, Gnome 3,
after above Edubuntu 11.10 Classic Menu option installation. 
I did it 3 times now from flesh installation.
Once you choose to boot into Gnome 3, Desktop freezed.
And you will have a "dead Gnome 3 Edubuntu 11.10",
mouse move but no drop down menu, nor shutdown or system menu. 
even my power button will not creat shutdown menu.
Only hold down 5 seconds to bios shutdown.
I have fleshly reinstall to test my tutorial and they all end up with "DEAD" Desktop. 
I will try it once again and if it is the same I will report as bugs to launchpad.
Anyone has opposite result please tell me, 
I am going to install on different computer soon to see,
if it was just my notebook or I can reproduce these bugs in others too.
-----------------------------
[/COLOR][/SIZE][/SIZE][/B]
===============================================
my comments ====>
After installing Edubuntu 11.10 DVD, today,
I found that Edubuntu provide the "Option" during Installation,
to choose Gnome Classic (fallback module).
That is what we just need during our main UBUNTU installation.
alongside the choice for 3rd party software and codec.

I cannot see any reason why Canonical Team,
WILL not do the same for UBUNTU 11.10 and +++ Unity. 

However for myself I still will go for "hybrid Unity and ClassicMenu Indicator",
after I hated Unity, and start to learn the Pro side of Unity,
after being forced to use it by Mark and Canonical (with pain).
NOW I start to use good function in UNITY and like it too.

I do believe in Unity benefit as well,
those who hated Unity, please stick on for a while,
you will see the convenient soon or later after you get used to it.

But I still believe my point below, the last section, still stand.

And I try to do my part as member of the community,
to help Mark and Canonical in filling the "gap",
 that they intentionally or not left it behind their great leap forward.
========================================

**[SIZE="3"]OPTION 2.[/SIZE]** More hassle to do.
**[SIZE="2"]Manually install Classic Menu fall back modules.[/SIZE]**
End up with Option 1 result but without any Education Programs for your kids in the family. 
And it will use almost 1GB less on harddisk

=>click on Ubuntu Software Center.
=>key in "gnome-session-fallback"
=>click install
=>at the end of installation, log out.
=>on right top corner of the "login box", left click on corner icon,
  and you select Gnome Classic 
  or Gnome Classic (No effects) use less resource-run a bit faster)

Pictures and command line option is at 
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)
=======================================================================

[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)

**_[SIZE="4"]Option 3, Most complicated option.(my own choice by now)[/SIZE]_**

[COLOR="Red"][B][U]Results: You have One Desktop, HYBRID,
with goodness of new Unity and Ease of Use Classic Menu[/U][/B][/COLOR]
see below attached image.

**[SIZE="3"]Open the terminal and run the following commands[/SIZE]**
[COLOR="Blue"](to open terminal %for newbies%
=> mouse left click on top left corner icon-called "Dash home"
=> key in the search box "[SIZE="3"] **T** [/SIZE]erminal"
=> left click "Terminal" icon that appear below.
=> copy the command sudo...... below [SIZE="3"]**_one line at the time_**[/SIZE].
   and paste into "Terminal" window.
(you have to use mouse to right click in terminal to get paste function,
if you try to paste using key board, don't use Control V from keyboard it won't work,
you have to do press Shift and Control then V to paste by keyboard.)
=> then press enter
=> follow the instructions on the "Terminal" screen.)[/COLOR]
[B][I][SIZE="2"], END

    sudo add-apt-repository ppa:diesch/testing
    sudo apt-get update
    sudo apt-get install classicmenu-indicator[/SIZE][/I][/B]

Then go to click **[SIZE="2"]"Dash Home"[/SIZE]** - 
key "**[SIZE="3"] C[/SIZE]** lassic" in the **[SIZE="3"]search box[/SIZE]**,
you will see **[SIZE="2"]ClassicMenu Indicator[/SIZE]** appeared below the search box,
left mouse click it.
You should have the Gray(or Black) **[SIZE="2"]ClassicMenu[/SIZE]** Icon appear on the top panel in 2-4 seconds, as in the below img.

or you can follow this tutorial if above tutorial is not clear enough
it has pictures every **steps**.
[http://www.liberiangeek.net/2011/11/classic-menu-indicator-now-works-with-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/classic-menu-indicator-now-works-with-ubuntu-11-10-oneiric-ocelot/)
-----------------------------

[SIZE="3"]And if you want **Classic Task Bar** at the bottom.[/SIZE]
(Task Bar that list all opening programs,
new unity launcher panel is a Task Bar in itself, 
except most of the space are occupied by program icons,
and all the listing opening programs got uselessly squash at the bottom,
except those programs which is position in the unity launcher panel.
**if you remove some icons by right click them** and choose the "Remove from Luncher" you would have good Task Bar without installing "tint2"

You can just drag any program icons on to the "launcher panel"
when you want to add back the icons to the launcher panel.

=> GO TO "**[SIZE="2"]Ubuntu Software Center[/SIZE]**",
[COLOR="Blue"]**[SIZE="2"]on the left new unity panel about 7 icons from the top[/SIZE]**[/COLOR].
Key in the right top Search Box for **[SIZE="3"][COLOR="Black"]_Tint2_[/COLOR][/SIZE]**,
Click install.

**[COLOR="Black"][SIZE="2"]To start Tint2 immediately[/SIZE][/COLOR]**
[COLOR="Blue"][SIZE="2"]=>open Terminal
=>at the command prompt key in "[SIZE="3"]**tint2**[/SIZE]"
and not "Tint2"=>error, and not "sudo tint2" =>error
if you close "Terminal" your tint2 task bar will close too.[/SIZE][/COLOR]

[SIZE="2"]And ***add to Startup Application if you want to start it when Ubuntu start***[/SIZE]. 
***and it will be at the bottom of the screen all the time,***
it will not depend on "Terminal" to start or stop the "tint2" task bar.
[COLOR="Blue"](add to Startup Application:
=> left click on right-most top "Shutdown Icon"
=> 3rd down in new pop up menu, left click "Startup Applications"
=> Click **[SIZE="2"]ADD[/SIZE]** icon.
=> key in "tint2" in both **[SIZE="2"]Name[/SIZE]** and [SIZE="2"]**Command box**[/SIZE].
=> Click ADD and then Close
=> Log out and log in again to start "tint2" automatically,
END[/COLOR]

or follow this tutorial if above tutorial is not clear enough.
it has details of picture and more details.
[http://www.liberiangeek.net/2011/10/add-taskbar-in-ubuntu-11-0411-10-with-panel-tint2/](http://www.liberiangeek.net/2011/10/add-taskbar-in-ubuntu-11-0411-10-with-panel-tint2/)
=====================================

The following comment I post at [http://design.canonical.com/2011/11/ubuntu-phone-tablet-and-tv-discussion-opened/](http://design.canonical.com/2011/11/ubuntu-phone-tablet-and-tv-discussion-opened/)
-------------------------
The point that Ubuntu is for Human Being, and for Canonical (and Canonical must survive). You can make a move on new Technology, but you don&#8217;t have to leave the majority of &#8220;old age&#8221; loyal communities in cold.

Just have an easy option during the installation or the first login for them to choose.

1. Unity (Fully support by Canonical)

2. Genome Classic (Canonical does not provide updates for Gnome Desktop. Some updates may be provided by the Ubuntu community).

and the third and fourth if they are available.

3. TV &#8211; Unity (Support by Canonical)
4. Netbook & Tablet (Support by Canonical)

Human Being is for freedom and not forcing them to choose one Theme of Freedom.

Ubuntu can provide options which is from community support, since Mark said it is too costly to provide options. Which I accept his position, since he has to make sure Canonical survival and he has the &#8220;duty to leap forward&#8221;.

Canonical said
In Ubuntu 11.10 (Oneiric), GNOME 2 has been replaced by GNOME 3. The default desktop is Unity, with Unity 2D as a fallback. The &#8220;classic&#8221; GNOME desktop option is not shown by default. However, a &#8220;Classic&#8221; desktop built upon GNOME 3 is still available.

And those &#8220;old age&#8221; communities have to hunt painfully how to install that old love or legacy Classic Menu.

Ubuntu &#8220;NetBook Remix&#8221; have that option in the old day, though unreliable.
(edit= as in Edubuntu 11.10 DVD has the option for user to choose Gnome Classic)

If Mark and Canonical show the &#8220;backward&#8221; community some respect that you have tried to provide comfortable switch to the old classic.

No one will express dissatisfaction and you will not lost as many supporters as you had, more important degrading the hard to build &#8220;Good Will&#8221; of Mark & Canonical.

(edit=I am now, understood and accepted (after days of reading pro and con),
on Mark and his team move to UNITY, 
but still critical of the way they did not provide the missing ClassicMenu Option) 

Why can&#8217;t you make a button or an option so you can switch easy between the old and the new Unity?
=================================================
Canonical was born from those customers&#8217; loyalties.
And Canonical don&#8217;t need to betray them to leap forward.
Canonical can leap forward with care to those &#8220;old age&#8221; community. 
And the Good Will and Respect will keep growing and not diminishing.
=================================================

I agree that Ubuntu should move to Mobile, Tablet and TV and make them easy integration with Desktop, but we don&#8217;t need to force everyone to go unity on Desktop.

So I beg to Mark and Canonical team, please have an easy option for Classic Menu, or include Classic Menu Indicator as in
[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)
as one of the program option on desktop, or in the shutdown menu or in any other prominent spot, where people can see it easy.

Google and Yahoo, even Microsoft(in the old day) when they provide new look or desktop environment, they will provide the easy option for old loyal customers to choose.

You have to treat your loyal communities as loyal customers and make them grow in quantities as well as qualities. And Canonical will grow as Google does.

Best Wishes to Mark and his teams.

---

### Post by grahammechanical on 2011-12-27
This is useful information for those who like that "old" look but I think you have missed a couple of things on the way.

1) the priority for Canonical from October 2010 until October 2012 is to complete their chosen path and that is Ubuntu (unity 3D) and Ubuntu 2D (Unity 2D).

2) Ubuntu community involvement. Canonical cannot do everything and does not intend to do everything. There is an open invitation for anyone to get involved. This Classic Menu Indicator is just the type of community involvement that is needed. Another such area is themes and background wallpapers as well as app indicators.

It seems to me that Canonical needs outside involvement and it is making it easier for outsiders to participate.

Check out this link

[http://developer.ubuntu.com/]("http://developer.ubuntu.com/")

Regards.

---

### Post by aimwin on 2011-12-28
> **grahammechanical said:**
> This is useful information.........
.........it is making it easier for outsiders to participate......

YYes grahammechanical, you are right,

the community must join in and help,
but Canonical can make it easier for "loyal" customers by providing,
ClassicMenu Option as they did in Edubuntu 11.10, which is release at the same time.

I belive they may have that "limited space" on the CD,
WHICH can be resolve by,

1. have a "condition" with that choice of "ClassicMenu fallback"
==> the user must connect to the internet,<==
since it will download "Classic fallback module"
and install on hardisk,
which is the same as option "download and update" during installation.

2. Provide info that anyone want that "ClassicMenu",
has to install from Ubuntu 11.10 DVD. 
and there will be the choice of the auto installing of ClassicMenu.
Which is Especially Important for the Nebies,
(like me 4 years ago, who hate Command Line,
and would not know how to do all those above tutorial steps).

3. Give direction that they can go to Software Center,
and donwload "Gnome ClassicMenu fallback" and install manually.
(It took me days with frustration to finally found that info and do it,
but if it was explain during installation it would be acceptable)

That would give a "goodwill" warm service to those ClassicMenu Fan.

============================================
Unless they decided to force people to use UNITY, 
since if they provide the ClassicMenu then majority will not try UNITY.

If this is so,

Then Option 4. (which I am useing)
I suggest the 12.04 should have the above "ClassicMenu Indicator" by default.
installed next to the Shutdown Indicator.
Since if you don't like it you can quit that icon any time.
And it will give convinient and benefit to both world of desktop.

This is not Mr.Mark's expensive option, but a built in function,
which will give UBUNTU as "ease" to use as before.
And it is nothing to do with "politics".

Best Wishes

---

### Post by drdos2006 on 2011-12-28
The fact that I was able to install and use the Classic Menu software from [http://www.florian-diesch.de/software/](http://www.florian-diesch.de/software/) has stopped me from converting over to Debian or another distro of Linux. I shall now persist with version 11.10 ( even though I do not particularly like the sidebar ). I do not have 7" or 10" tablets but only desktops and a laptop.

I had installed Debian on my test machine but came back to Ubuntu after the above software was available.

Personally I think that giving consumers an option to have the Classic Menu would be beneficial for loyal Ubuntu users and allow new users to transition away from Windows. Windows 7 still allows CMD to be able to be run, but trying to find a way to run a terminal from Ubuntu 11 is not a simple matter. New users would have to hunt for it.

My 2cents worth.

regards

---

### Post by stinkeye on 2011-12-28
> trying to find a way to run a terminal from Ubuntu 11 is not a simple matter. New users would have to hunt for it.
Only if they don't know how to spell terminal.
:rolleyes:

---

### Post by helmarfernandes on 2011-12-29
After 4 days using Unity I have to say that I´ve changed my mind.
Unity sucks!
It´s lazy, slow, buggy and annoying...

The worse: I would like to make any "unofficial" installation like GnomeFAllback or other.... I´m going to downgrade to 11.04 this night

---

### Post by stinkeye on 2011-12-29
> **helmarfernandes said:**
> After 4 days using Unity I have to say that I´ve changed my mind.
Unity sucks!
It´s lazy, slow, buggy and annoying...

The worse: I would like to make any "unofficial" installation like GnomeFAllback or other.... I´m going to downgrade to 11.04 this night

Then this 10 mins later where you must have jumped in your time machine 
and have now been using unity for 6 days.
> **helmarfernandes said:**
> After six days of Unity I´m giving up from it...

It´s sad, but if I want to be up to date with a Linux distro my only option is to look for another distro than Ubuntu... 
Sad... very sad
Sad for you. Although compiz has a couple of bugs I quite like 11.10 and runs fine here.

---

### Post by aimwin on 2012-01-06
> **helmarfernandes said:**
> After 4 days using Unity I have to say that I´ve changed my mind.
Unity sucks!
It´s lazy, slow, buggy and annoying...

The worse: I would like to make any "unofficial" installation like GnomeFAllback or other.... I´m going to downgrade to 11.04 this night

Have you try to install ClassicMenu Indicator, and try the hybrid Unity&ClassicMenu as I have done.
Need to stick to it for a while to get a hang of it though.

For myself if I am going to do a lot of programs manupilation..
I boot into 11.04 too.

But for Newbies, who "never know" Ubuntu, I have tested their favors,
most of them choose Unity. So I have to agree to Mark S. that his decision is the right direction.

But for "us", you and including me, and possibly majority of the oldies would vote for Classic Menu.

So it look like we, as community got to work on the old systems, and try to keep promoting them so the alternative classic Menu will live on.

---

### Post by sundial on 2012-03-22
As a Ubuntu user for the last four years, I find Unity destop nothing short of awful. I finally dumped ubuntu and switched to MINT 12

Echoing others, WHY CAN WE NOT HAVE A CHOICE between Classic Genome and Unity fro the desktop?

MINT is OK but I wpuld rather use Ubuntu.

---

### Post by kurt18947 on 2012-03-22
For those pining for Gnome 2, once extensions work again in Precise gnome-shell (they don't right now), you can come quite close to the look & feel of gnome 2 in gnome 3.  You can also add desktop launchers in Unity & Gnome-shell.  I've tried  Unity, Mint Cinnamon, Mint's shell and Mate but find gnome-shell fits best.  Shell does not work as well for me without about 6 extensions to add a bottom task bar, favorites menu, places,application menu etc.

---

### Post by esagherardo on 2012-03-28
> **sundial said:**
> As a Ubuntu user for the last four years, I find Unity destop nothing short of awful. I finally dumped ubuntu and switched to MINT 12

Echoing others, WHY CAN WE NOT HAVE A CHOICE between Classic Genome and Unity fro the desktop?

MINT is OK but I wpuld rather use Ubuntu.

Me too. I found this thread with the keywords "unity sucks".

The operating system for me is a tool for working, not for playing! I need to do things fast as I was used to. I do not need fancy graphics, I need CONFIGURABILITY!

I cannot customize anything, also the fallback gnome session is a fake... 
Just a few examples: A) I am used since ever (I started linuxing on 1989) to drag by highlighting and dropping by third button, I HATE the microsoft combination Ctrl-C/Ctrl-V  and now I am forced to use it! Apparently there's no way to change that, not even in the fall-back B) I want the highly configurable gtk/bonobo applets back (in particular giplet), or any sound replacement.

Damn if this does not change ASAP I'll be forced t change distro!

---

### Post by aimwin on 2012-06-28
New Ubuntu 12.04 is out and you can easily install Gnome Classic Menu with no issue now, quite stable, but still not many plugin as the old version.

After Flesh Install, 
goto Ubuntu Software Center
search for Gnome Shell
click install it.

then LOG OUT
and before login, on the right hand top conner of the login window,
mouse left click and choose Gnome Classic for your old classic menu.

you can choose Gnome for new Gnome 3 desktop,
 which is in many ways similar to Unity.



> **aimwin said:**
> edit 29/12/2011
[SIZE="3"]**Option 1, Classic Menu (modified)**[/SIZE] as in old Ubuntu version. Easiest Method.

**[SIZE="3"][COLOR="Red"]You must use Edubuntu 11.10 DVD[/COLOR][/SIZE] for installation instead of [SIZE="2"]Ubuntu 11.10 CD[/SIZE]**
[COLOR="Red"]

This Edubuntu installation method, 
you can logout and login with choices to choose Unity or Classic Menu anytime, (not Gnome3, pls see below edit 6/1/2012)
But only one style of Desktop only, not both style in one Desktop as option 3.
[B][SIZE="2"][I]AND no need for Command Line nor hassled manual tweaks after installation
It is Classic Menu Ubuntu 11.10 out of the box.[/I][/SIZE][/B][/COLOR] 

There will be option to choose Gnome Classic menu during installation.
AT the end you will get exact the same menu as[B][SIZE="3"] [this tutorial]("http://www.psychocats.net/ubuntu/classicgnome") 

And it is look like [ weblive 11.04]("http://edubuntu.org/weblive")[/SIZE][/B] 
[COLOR="Red"]**[SIZE="3"]==> Have you try "Weblive" Edubuntu/UBUNTU Online without installing on your hard disk.[/SIZE]**[/COLOR]


[B][SIZE="2"][SIZE="3"][COLOR="Blue"]Edit 6/1/2012
From my own experience.
Do not install Gnome-shell, Gnome 3,
after above Edubuntu 11.10 Classic Menu option installation. 
I did it 3 times now from flesh installation.
Once you choose to boot into Gnome 3, Desktop freezed.
And you will have a "dead Gnome 3 Edubuntu 11.10",
mouse move but no drop down menu, nor shutdown or system menu. 
even my power button will not creat shutdown menu.
Only hold down 5 seconds to bios shutdown.
I have fleshly reinstall to test my tutorial and they all end up with "DEAD" Desktop. 
I will try it once again and if it is the same I will report as bugs to launchpad.
Anyone has opposite result please tell me, 
I am going to install on different computer soon to see,
if it was just my notebook or I can reproduce these bugs in others too.
-----------------------------
[/COLOR][/SIZE][/SIZE][/B]
===============================================
my comments ====>
After installing Edubuntu 11.10 DVD, today,
I found that Edubuntu provide the "Option" during Installation,
to choose Gnome Classic (fallback module).
That is what we just need during our main UBUNTU installation.
alongside the choice for 3rd party software and codec.

I cannot see any reason why Canonical Team,
WILL not do the same for UBUNTU 11.10 and +++ Unity. 

However for myself I still will go for "hybrid Unity and ClassicMenu Indicator",
after I hated Unity, and start to learn the Pro side of Unity,
after being forced to use it by Mark and Canonical (with pain).
NOW I start to use good function in UNITY and like it too.

I do believe in Unity benefit as well,
those who hated Unity, please stick on for a while,
you will see the convenient soon or later after you get used to it.

But I still believe my point below, the last section, still stand.

And I try to do my part as member of the community,
to help Mark and Canonical in filling the "gap",
 that they intentionally or not left it behind their great leap forward.
========================================

**[SIZE="3"]OPTION 2.[/SIZE]** More hassle to do.
**[SIZE="2"]Manually install Classic Menu fall back modules.[/SIZE]**
End up with Option 1 result but without any Education Programs for your kids in the family. 
And it will use almost 1GB less on harddisk

=>click on Ubuntu Software Center.
=>key in "gnome-session-fallback"
=>click install
=>at the end of installation, log out.
=>on right top corner of the "login box", left click on corner icon,
  and you select Gnome Classic 
  or Gnome Classic (No effects) use less resource-run a bit faster)

Pictures and command line option is at 
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)
=======================================================================

[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)

**_[SIZE="4"]Option 3, Most complicated option.(my own choice by now)[/SIZE]_**

[COLOR="Red"][B][U]Results: You have One Desktop, HYBRID,
with goodness of new Unity and Ease of Use Classic Menu[/U][/B][/COLOR]
see below attached image.

**[SIZE="3"]Open the terminal and run the following commands[/SIZE]**
[COLOR="Blue"](to open terminal %for newbies%
=> mouse left click on top left corner icon-called "Dash home"
=> key in the search box "[SIZE="3"] **T** [/SIZE]erminal"
=> left click "Terminal" icon that appear below.
=> copy the command sudo...... below [SIZE="3"]**_one line at the time_**[/SIZE].
   and paste into "Terminal" window.
(you have to use mouse to right click in terminal to get paste function,
if you try to paste using key board, don't use Control V from keyboard it won't work,
you have to do press Shift and Control then V to paste by keyboard.)
=> then press enter
=> follow the instructions on the "Terminal" screen.)[/COLOR]
[B][I][SIZE="2"], END

    sudo add-apt-repository ppa:diesch/testing
    sudo apt-get update
    sudo apt-get install classicmenu-indicator[/SIZE][/I][/B]

Then go to click **[SIZE="2"]"Dash Home"[/SIZE]** - 
key "**[SIZE="3"] C[/SIZE]** lassic" in the **[SIZE="3"]search box[/SIZE]**,
you will see **[SIZE="2"]ClassicMenu Indicator[/SIZE]** appeared below the search box,
left mouse click it.
You should have the Gray(or Black) **[SIZE="2"]ClassicMenu[/SIZE]** Icon appear on the top panel in 2-4 seconds, as in the below img.

or you can follow this tutorial if above tutorial is not clear enough
it has pictures every **steps**.
[http://www.liberiangeek.net/2011/11/classic-menu-indicator-now-works-with-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/classic-menu-indicator-now-works-with-ubuntu-11-10-oneiric-ocelot/)
-----------------------------

[SIZE="3"]And if you want **Classic Task Bar** at the bottom.[/SIZE]
(Task Bar that list all opening programs,
new unity launcher panel is a Task Bar in itself, 
except most of the space are occupied by program icons,
and all the listing opening programs got uselessly squash at the bottom,
except those programs which is position in the unity launcher panel.
**if you remove some icons by right click them** and choose the "Remove from Luncher" you would have good Task Bar without installing "tint2"

You can just drag any program icons on to the "launcher panel"
when you want to add back the icons to the launcher panel.

=> GO TO "**[SIZE="2"]Ubuntu Software Center[/SIZE]**",
[COLOR="Blue"]**[SIZE="2"]on the left new unity panel about 7 icons from the top[/SIZE]**[/COLOR].
Key in the right top Search Box for **[SIZE="3"][COLOR="Black"]_Tint2_[/COLOR][/SIZE]**,
Click install.

**[COLOR="Black"][SIZE="2"]To start Tint2 immediately[/SIZE][/COLOR]**
[COLOR="Blue"][SIZE="2"]=>open Terminal
=>at the command prompt key in "[SIZE="3"]**tint2**[/SIZE]"
and not "Tint2"=>error, and not "sudo tint2" =>error
if you close "Terminal" your tint2 task bar will close too.[/SIZE][/COLOR]

[SIZE="2"]And ***add to Startup Application if you want to start it when Ubuntu start***[/SIZE]. 
***and it will be at the bottom of the screen all the time,***
it will not depend on "Terminal" to start or stop the "tint2" task bar.
[COLOR="Blue"](add to Startup Application:
=> left click on right-most top "Shutdown Icon"
=> 3rd down in new pop up menu, left click "Startup Applications"
=> Click **[SIZE="2"]ADD[/SIZE]** icon.
=> key in "tint2" in both **[SIZE="2"]Name[/SIZE]** and [SIZE="2"]**Command box**[/SIZE].
=> Click ADD and then Close
=> Log out and log in again to start "tint2" automatically,
END[/COLOR]

or follow this tutorial if above tutorial is not clear enough.
it has details of picture and more details.
[http://www.liberiangeek.net/2011/10/add-taskbar-in-ubuntu-11-0411-10-with-panel-tint2/](http://www.liberiangeek.net/2011/10/add-taskbar-in-ubuntu-11-0411-10-with-panel-tint2/)
=====================================

The following comment I post at [http://design.canonical.com/2011/11/ubuntu-phone-tablet-and-tv-discussion-opened/](http://design.canonical.com/2011/11/ubuntu-phone-tablet-and-tv-discussion-opened/)
-------------------------
The point that Ubuntu is for Human Being, and for Canonical (and Canonical must survive). You can make a move on new Technology, but you don’t have to leave the majority of “old age” loyal communities in cold.

Just have an easy option during the installation or the first login for them to choose.

1. Unity (Fully support by Canonical)

2. Genome Classic (Canonical does not provide updates for Gnome Desktop. Some updates may be provided by the Ubuntu community).

and the third and fourth if they are available.

3. TV – Unity (Support by Canonical)
4. Netbook & Tablet (Support by Canonical)

Human Being is for freedom and not forcing them to choose one Theme of Freedom.

Ubuntu can provide options which is from community support, since Mark said it is too costly to provide options. Which I accept his position, since he has to make sure Canonical survival and he has the “duty to leap forward”.

Canonical said
In Ubuntu 11.10 (Oneiric), GNOME 2 has been replaced by GNOME 3. The default desktop is Unity, with Unity 2D as a fallback. The “classic” GNOME desktop option is not shown by default. However, a “Classic” desktop built upon GNOME 3 is still available.

And those “old age” communities have to hunt painfully how to install that old love or legacy Classic Menu.

Ubuntu “NetBook Remix” have that option in the old day, though unreliable.
(edit= as in Edubuntu 11.10 DVD has the option for user to choose Gnome Classic)

If Mark and Canonical show the “backward” community some respect that you have tried to provide comfortable switch to the old classic.

No one will express dissatisfaction and you will not lost as many supporters as you had, more important degrading the hard to build “Good Will” of Mark & Canonical.

(edit=I am now, understood and accepted (after days of reading pro and con),
on Mark and his team move to UNITY, 
but still critical of the way they did not provide the missing ClassicMenu Option) 

Why can’t you make a button or an option so you can switch easy between the old and the new Unity?
=================================================
Canonical was born from those customers’ loyalties.
And Canonical don’t need to betray them to leap forward.
Canonical can leap forward with care to those “old age” community. 
And the Good Will and Respect will keep growing and not diminishing.
=================================================

I agree that Ubuntu should move to Mobile, Tablet and TV and make them easy integration with Desktop, but we don’t need to force everyone to go unity on Desktop.

So I beg to Mark and Canonical team, please have an easy option for Classic Menu, or include Classic Menu Indicator as in
[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)
as one of the program option on desktop, or in the shutdown menu or in any other prominent spot, where people can see it easy.

Google and Yahoo, even Microsoft(in the old day) when they provide new look or desktop environment, they will provide the easy option for old loyal customers to choose.

You have to treat your loyal communities as loyal customers and make them grow in quantities as well as qualities. And Canonical will grow as Google does.

Best Wishes to Mark and his teams.

---

