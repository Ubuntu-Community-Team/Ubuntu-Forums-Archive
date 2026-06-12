---
title: "Tweaking Gnome3"
date: 2011-05-06
forum: Desktop Environments
---

### Post by maverick280857 on 2011-05-06
Hi,

I'm running Ubuntu 11.04 64-bit with Gnome3. Is it possible to make the following changes to Gnome3:

1. Change the Date and Time appearance to reflect "Friday May 06 13:32" rather than "Fri 13:32"?

2. Include Date and Time of other cities (other time zones)?

3. Have Cairo-Dock start automatically? As Gnome3 doesn't have a "taskbar" and also no maximize-minimize buttons its hard to keep track of windows. So I decided to use Cairo Dock, but I can't figure out how to start it by default -- there is no "startup programs" application anymore it seems.

4. Change the theme in gnome 3? I followed the instructions on [http://danodymake.deviantart.com/#/d3fkpe9](http://danodymake.deviantart.com/#/d3fkpe9), but the newly placed theme does not show up in gnome-tweak-tool.

I'll use this thread to ask more questions about Gnome3 in future. Thanks in advance for your help!

---

### Post by -unseen- on 2011-05-06
Hi,

1. use gnome-tweak-tool, there goto shell -> show date in clock

2. sorry don't know, is it even possible?

3. type gnome-session-properties in a terminal to see the startup applications. You can also bring back the minimize/maximize buttons with the gnome-tweak-tool if you like.

---

### Post by maverick280857 on 2011-05-06
> **-unseen- said:**
> Hi,

1. use gnome-tweak-tool, there goto shell -> show date in clock

2. sorry don't know, is it even possible?

3. type gnome-session-properties in a terminal to see the startup applications. You can also bring back the minimize/maximize buttons with the gnome-tweak-tool if you like.

Thanks for 1 & 3! What do you think about 4?

As for 2, I guess its not possible anymore.

---

### Post by -unseen- on 2011-05-06
I'm not sure on the theme. I guess you need the gnome-shell-extensions-user-theme.deb, which can be found here [http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux](http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux) . It's not in the ppa so far. Once it is installed, in gnome-tweak-tool there is a new option for a user theme. I got it to select the new theme, but it didn't get applied for some reason ...

---

### Post by 23dornot23d on 2011-05-06
I am just going through a clean install of Gnome3 / Gnome Shell here with all the latest updates included**. **[**LINK**]("http://ubuntuforums.org/showthread.php?t=1750450")
go to page 2 for the Themes ..... all the work here is on a 64 bit system too.

1 ......Themes I have set up and show which files you need and where to put them.
2 ......Cairo-dock I have already set up and show how,  

To get cairo-dock running
**alt+f2 cairo-dock** 
once cairo-dock is running goto 
**Applications menu (on the left side of cairo-dock) >>> Preferences  >>> Startup Applications.**
add a launcher with the command [B] cairo-dock

[/B] 3 ......Times and Dates Month can be shown using conky .... plus other useful info too.

Hope this helps in some way ....

---

### Post by maverick280857 on 2011-05-06
Thanks guys. I'll check out the link in a bit.

Conky doesn't load on my system.

And I don't see "Startup Applications" on the Preferences menu in Cairo-Dock. But "gnome-session-properties" did the trick.

When I try to install unseen's deb file, I get the following error message:

"The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath."

"Lintian check results for /tmp/gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb:
E: gnome-shell-extensions-user-theme: maintainer-address-malformed Charles Bowman <chuck@Gnome-3>
"

---

### Post by maverick280857 on 2011-05-06
> **23dornot23d said:**
> [/B][**LINK**]("http://ubuntuforums.org/showthread.php?t=1750450")
go to page 2 for the Themes ..... all the work here is on a 64 bit system too.

1 ......Themes I have set up and show which files you need and where to put them.

When I unzip the contents of themeselector into $HOME/.local/share/gnome-shell and reboot the system, I am unable to boot into GNOME 3. I get an error message saying that something bad has happened and I have to log out. The situation is remedied only by deleting the themeselector files from the abovementioned directory.

---

### Post by jjcv on 2011-05-06
> **maverick280857 said:**
> When I unzip the contents of themeselector into $HOME/.local/share/gnome-shell and reboot the system, I am unable to boot into GNOME 3. I get an error message saying that something bad has happened and I have to log out. The situation is remedied only by deleting the themeselector files from the abovementioned directory.

I have the same problems.

---

### Post by 23dornot23d on 2011-05-06
Interesting :- 

I have them running   ........ and have not seen an error message ....... :confused:

and the THEMES are working ..... on both my 32 bit and 64 bit systems ...... 

[LAUNCHPAD BUG]("https://bugs.launchpad.net/ugr-meta/+bug/772221") ( Themeselector not working )

I know in the UGR team they were going to include them as standard as it solved the problem ..... this has maybe been done now ..... and they are maybe doing checks to make sure their own versions are
being loaded now.


[B]Ok If they are causing problems now I will add a warning to check for them - as they may already be installed.

__________________________

[/B][@ maverick280857]("http://ubuntuforums.org/member.php?u=251653")

> 
Conky doesn't load on my system.
What errors do you get back when you run the command 

**conky **

from a terminal window

**ALSO**

> 
And I don't see "Startup Applications" on the Preferences menu in Cairo-Dock. But "gnome-session-properties" did the trick.

Startup applications is in mine - but I have a lot of things loaded maybe it does not come as standard

[IMG]http://img854.imageshack.us/img854/1823/startupb.jpg[/IMG]

_____________________________

@ [jjcv]("http://ubuntuforums.org/member.php?u=59981")

Do you have the option for themes in the window .... as shown below ... 

( after moving the cursor into the top left corner of the screen in Gnome-shell )

[IMG]http://img508.imageshack.us/img508/5945/themes.jpg[/IMG]

The THEMES and the instructions for getting them working if not can be found here [MUSINGS THEME SELECTOR]("http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html")

Check above just in-case it is already loaded up now after the updates ..... as the only thing you need are the Themes then ...... which are shown and included in the link above .....

---

### Post by maverick280857 on 2011-05-07
Thanks, I will check out your links in a bit. But right now, I am having difficulty with NetworkManager. It seems to have disappeared altogether, and I have no network in Ubuntu. Any ideas on how to fix it?

It seems the network manager service is running, but the icon isn't in the identification area, and the wireless network is also inactive.

EDIT: SOLVED
Reference: [http://ubuntuforums.org/showthread.php?t=1751436](http://ubuntuforums.org/showthread.php?t=1751436)

---

### Post by maverick280857 on 2011-05-07
> **23dornot23d said:**
> Interesting :- 

I have them running   ........ and have not seen an error message ....... :confused:

and the THEMES are working ..... on both my 32 bit and 64 bit systems ...... 


Can you please post **detailed** step-by-step instructions? There seems to be some confusion about where the themes should reside. I would appreciate if you could pick up any one theme and post all the commands you used to get it to work. I do not see the themes button in GNOME3, unlike you.

---

### Post by 23dornot23d on 2011-05-07
Gnome-Shell is still in development ..... at some point the updates and upgrades will fix your problems properly.

One thing that you definitely need is the themes in the correct place
and I can help you find out if they are there to start with.

Here is the Link to the Themes to start with ..... 
 [http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html](http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html)

So we will first look in the directory and see what is there .....

I will first show whats in mine .......

keith@keith-Aspire-7730ZG:~$ cd .local/share/gnome-shell
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.local"]keith@keith-Aspire-7730ZG:~/.local[/EMAIL]/share/gnome-shell$ ls

[COLOR=Red][B]application_state  extensions  themes
[/B] [/COLOR]
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.local"]keith@keith-Aspire-7730ZG:~/.local[/EMAIL]/share/gnome-shell$ cd themes
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.local"]keith@keith-Aspire-7730ZG:~/.local[/EMAIL]/share/gnome-shell/themes$ ls

[COLOR=Red][B]Adwaita  ANewHope  Atolm  DarkGlass  DeviantArt  Elementary  SmoothInsert

[/B] [/COLOR] 

What does yours show .... after doing these commands LS (lower case) for list by the way ......

**cd ~**

[B]cd .local/share/gnome-shell
ls[/B]

[B]cd themes
ls[/B]

---

### Post by walt.smith1960 on 2011-05-07
Sorry if this is simplistic but what happens if you open a terminal and enter"nm-applet"?  I sometimes don't have network manager showing up and the above fixes it but I have to leave the terminal open.  I do have the network without the icon though so my problem is probably different than yours.

---

### Post by jjcv on 2011-05-07
> **23dornot23d said:**
> Interesting :- 

@ [jjcv]("http://ubuntuforums.org/member.php?u=59981")

Do you have the option for themes in the window .... as shown below ... 

 .....

Thanks for your response.  I have it working now.   

What I did was go into synaptic and noticed there were a few gnome 3 packages that were not installed.   Also an apt upgrade of some packages at the same time seems to have done the trick.

---

### Post by 23dornot23d on 2011-05-07
> **jjcv said:**
> Thanks for your response.  I have it working now.   

What I did was go into synaptic and noticed there were a few gnome 3 packages that were not installed.   Also an apt upgrade of some packages at the same time seems to have done the trick.


Good .... glad you got it sorted ..... ;)

---

### Post by maverick280857 on 2011-05-08
> **23dornot23d said:**
> 
Here is the Link to the Themes to start with ..... 
 [http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html](http://blog.fpmurphy.com/2011/04/gnome-shell-theme-selector-preview.html)


Maybe I need to read it more carefully then..I didn't find any instructions there. I'm assuming there's a themeselector tarball somewhere on that page.

[QUOTE=23dornot23d]
So we will first look in the directory and see what is there .....

I will first show whats in mine .......

keith@keith-Aspire-7730ZG:~$ cd .local/share/gnome-shell
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.local"]keith@keith-Aspire-7730ZG:~/.local[/EMAIL]/share/gnome-shell$ ls

[COLOR=Red][B]application_state  extensions  themes
[/B] [/COLOR]
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.local"]keith@keith-Aspire-7730ZG:~/.local[/EMAIL]/share/gnome-shell$ cd themes
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.local"]keith@keith-Aspire-7730ZG:~/.local[/EMAIL]/share/gnome-shell/themes$ ls

[COLOR=Red][B]Adwaita  ANewHope  Atolm  DarkGlass  DeviantArt  Elementary  SmoothInsert

[/B] [/COLOR] 

What does yours show .... after doing these commands LS (lower case) for list by the way ......

**cd ~**

[B]cd .local/share/gnome-shell
ls[/B]

[B]cd themes
ls[/B][/QUOTE]

Here's my output

```

vivek@krypton:~/.local/share/gnome-shell$ ls -l
total 12
-rw-r--r-- 1 vivek vivek 4709 2011-05-08 10:14 application_state
drwxr-xr-x 2 vivek vivek 4096 2011-05-07 00:49 extensions
vivek@krypton:~/.local/share/gnome-shell$ 

```

I haven't untarred the tarball yet. But I should at least see a themes folder with the standard gnome themes here? Adwaita is the one I'm using (by default).

---

### Post by 23dornot23d on 2011-05-08
Well even the Adwaita one I had to put in there manually .... following a link I found to it but that was a long time back
was before the Natty release came out as the thread to the file with the Adwaita theme was zipped in the development area.

But just a guess ..... if they are not in there maybe you will not be able to get them
working ......

If it was me I would put them in there ...... but if you are getting an error and its not
good for your system ...... 

> 
When I try to install unseen's deb file, I get the following error message:

"The installation of a package which violates the quality standards  isn't allowed. This could cause serious problems on your computer.  Please contact the person or organisation who provided this package file  and include the details beneath."

"Lintian check results for /tmp/gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb:
E: gnome-shell-extensions-user-theme: maintainer-address-malformed Charles Bowman <chuck@Gnome-3>
then wait until the upgrades come out to solve it.

Because if that is not working for you ....... you cannot follow any instructions that I made as they related to that
package plus the other one that Charles Bowman kindly made available to us .......

The other option is to install the Gnome-Shell [DVD ....]("http://ubuntuforums.org/showthread.php?t=1750450")

That he created with the Themes and extensions already working on it.

---

### Post by maverick280857 on 2011-05-08
Yes, I think I will wait for the updates before I take another plunge into themeselector.

Meanwhile, how do you change the screensaver?

---

### Post by peter.senna on 2011-05-08
I'm missing the system-monitor applet that I was used to have on the top bar. Is there a way to install it in gnome-3?

Thanks!

---

### Post by maverick280857 on 2011-05-09
> **peter.senna said:**
> I'm missing the system-monitor applet that I was used to have on the top bar. Is there a way to install it in gnome-3?

Thanks!

I don't think so...they revamped the whole thing. You could use conky or something to show all that you want to see up there.

---

### Post by maverick280857 on 2011-05-09
Okay I tried to install gnome-shell-extensions by following the advice given on

[http://piecesoflint.wordpress.com/2011/04/06/how-to-tweak-gnome-3-to-your-needs/](http://piecesoflint.wordpress.com/2011/04/06/how-to-tweak-gnome-3-to-your-needs/)

I get an error

```

vivek@krypton:~/Downloads/gnome-shell-extensions$ sudo ./autogen.sh --prefix=$HOME/.local --enable-extensions="enter the extensions you want to enable here, space separated"
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.67
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.1
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running intltoolize...
Running aclocal-1.11...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell&component=extensions
Running autoconf...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell&component=extensions
Running automake-1.11...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell&component=extensions
Running ./configure --prefix=/home/vivek/.local --enable-extensions=enter the extensions you want to enable here, space separated ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.26... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.22... yes
[B]./configure: line 4201: GLIB_GSETTINGS: command not found
./configure: line 4217: test: too many arguments
configure: error: invalid extension enter[/B]
vivek@krypton:~/Downloads/gnome-shell-extensions$ 

```

Any ideas on what's going wrong here?

---

### Post by bulldog on 2011-05-09
People who have trouble to install the theme-selector should take a look at this web-page.

[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

I have done it like discribed here and it works very well on natty.

I think the theme-selector which will be used by gnome-tweak-tool isn't the same as the one with the extra tab in activities.

Here is discribed how to get it from git.
After you did that you have to download the themes AND the theme-selector.

Just read it carefully and take the steps wich are required for your gnome-shell and it will work beautifully.

Also there are much more themes,Gnome-shell and GTK3.

It's certainly worth to take a read at this web-pages.

---

### Post by maverick280857 on 2011-05-09
Ok I accidentally deleted the contents of $HOME/.themes/...now I have nothing in it and while I am running Adwaita, my icons and menu colors are all messed up compared to what they were when I had some stuff by default in $HOME/.themes/

Can someone send me the bare minimum default stuff in $HOME/.themes/?? The icon and menu themes seem to be messed up (please see attached **screenshot** -- everything is dark and gray suddenly)

EDIT: Please ignore this. Problem solved after deleting $HOME/.themes and rebooting.

---

### Post by maverick280857 on 2011-05-09
> **bulldog said:**
> People who have trouble to install the theme-selector should take a look at this web-page.

[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

I have done it like discribed here and it works very well on natty.

Okay I tried this too but I get errors:

```

vivek@krypton:~/Downloads/gnome-shell-extensions$ ./autogen.sh --prefix=/usr --enable-extensions=user-theme
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.67
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.1
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running intltoolize...
Running aclocal-1.11...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell&component=extensions
Running autoconf...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell&component=extensions
Running automake-1.11...
configure.ac:2: warning: AC_INIT: not a literal: https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-shell&component=extensions
Running ./configure --prefix=/usr --enable-extensions=user-theme ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.26... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.22... yes
./configure: line 4201: GLIB_GSETTINGS: command not found
configure: creating ./config.status
config.status: creating extensions/alternate-tab/Makefile
config.status: creating extensions/alternative-status-menu/Makefile
config.status: creating extensions/auto-move-windows/Makefile
config.status: creating extensions/dock/Makefile
config.status: creating extensions/drive-menu/Makefile
config.status: creating extensions/example/Makefile
config.status: creating extensions/windowsNavigator/Makefile
config.status: creating extensions/gajim/Makefile
config.status: creating extensions/places-menu/Makefile
config.status: creating extensions/xrandr-indicator/Makefile
config.status: creating extensions/user-theme/Makefile
config.status: creating extensions/Makefile
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing po/stamp-it commands
Now type `make' to compile gnome-shell-extensions
vivek@krypton:~/Downloads/gnome-shell-extensions$ make && sudo make install
[B]Making all in extensions
make[1]: Entering directory `/home/vivek/Downloads/gnome-shell-extensions/extensions'
Making all in user-theme
make[2]: Entering directory `/home/vivek/Downloads/gnome-shell-extensions/extensions/user-theme'
Makefile:432: *** missing separator.  Stop.
make[2]: Leaving directory `/home/vivek/Downloads/gnome-shell-extensions/extensions/user-theme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vivek/Downloads/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1[/B]
vivek@krypton:~/Downloads/gnome-shell-extensions$ 

```

---

### Post by maverick280857 on 2011-05-09
Fresh problems:

(1) Alt + Tab no longer works
(2) I see a "favorites" bar on the right hand side of my screen which prevents me from maximizing windows. I don't know how it got activated by itself (please refer to attached screenshot). **How do I disable it?**

---

### Post by bulldog on 2011-05-09
I think you used the one with ALL the extensions,you should have used this one 
 cd
git clone [http://git.gnome.org/browse/gnome-shell-extensions](http://git.gnome.org/browse/gnome-shell-extensions)
cd gnome-shell-extensions
./autogen.sh --prefix=/usr --enable-extensions=user-theme
make && sudo make install

This would only give you the theme exetension you need.
Then you should do this,

The ThemeSelector extension already comes with 5 great GNOME Shell themes by half-left: Atolm, Smooth Inset, Elementaty, Dark Glass and Deviant Art GNOME Shell themes. Here's how to install it.


Download the Themeselector Gnome Shell extension, extract it and place "extension.js" and metadata.json under the ~/.local/share/gnome-shell/extensions/themeselector@fpmurphy.com/ folder (if it doesn't exist, create it). Then copy all the folders you've extracted to the ~/.themes/ folder (it's a hidden folder in your home directory; if some of those folders exists, merge the data).

Now restart GNOME Shell and you should have a new Themes tab in the Activities overview.

And you should be done with it.

---

### Post by bulldog on 2011-05-09
> **maverick280857 said:**
> Fresh problems:

(1) Alt + Tab no longer works
(2) I see a "favorites" bar on the right hand side of my screen which prevents me from maximizing windows. I don't know how it got activated by itself (please refer to attached screenshot). **How do I disable it?**

A question though,do you run Gnome-Shell native in Natty or did you compiled it in a "sandbox" in your HOME ?

---

### Post by maverick280857 on 2011-05-09
> **bulldog said:**
> I think you used the one with ALL the extensions,you should have used this one 
 cd
git clone [http://git.gnome.org/browse/gnome-shell-extensions](http://git.gnome.org/browse/gnome-shell-extensions)
cd gnome-shell-extensions
./autogen.sh --prefix=/usr --enable-extensions=user-theme
make && sudo make install

This would only give you the theme exetension you need.

Thanks for your reply. But I get the same errors:

```

vivek@krypton:~/Downloads/gnome-shell-extensions$ make && sudo make install
Making all in extensions
make[1]: Entering directory `/home/vivek/Downloads/gnome-shell-extensions/extensions'
Making all in user-theme
make[2]: Entering directory `/home/vivek/Downloads/gnome-shell-extensions/extensions/user-theme'
Makefile:432: *** missing separator.  Stop.
make[2]: Leaving directory `/home/vivek/Downloads/gnome-shell-extensions/extensions/user-theme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vivek/Downloads/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1
vivek@krypton:~/Downloads/gnome-shell-extensions$ 

```

Also, what are your thoughts about the other issue (Alt + Tab and Favorites menu)

---

### Post by maverick280857 on 2011-05-09
> **bulldog said:**
> A question though,do you run Gnome-Shell native in Natty or did you compiled it in a "sandbox" in your HOME ?

I installed it on Natty using the instructions given here: [http://ubuntuforums.org/showpost.php?p=10734567&postcount=1](http://ubuntuforums.org/showpost.php?p=10734567&postcount=1)

---

### Post by bulldog on 2011-05-09
> **maverick280857 said:**
> I installed it on Natty using the instructions given here: [http://ubuntuforums.org/showpost.php?p=10734567&postcount=1](http://ubuntuforums.org/showpost.php?p=10734567&postcount=1)

Should work properly,I did not have any error whatsoever with my gnome-shell install,but that could be just luck.

About the theme-extension error I have no idea,I did the git install and down-loaded the theme selector and it worked.

I did take a look at the makefile, but didn't see anything what could be of use.

It gives an error on line 432 as I remember correct,but I'm not an expert on these things either.

I have the ricotz testing ppa enabled next to the gnome3 ppa.
Shouldn't make a difference though.

---

### Post by bulldog on 2011-05-09
QUOTE[Also, what are your thoughts about the other issue (Alt + Tab and Favorites menu)]/QUOTE

Well if you can install them,you can usual un-install them:D

There should be a README of some kind in the extension folder I presume,did not look for one though.

Will have a look and if I find something I come back at it.
```

GNOME Shell Extensions is a collection of extensions providing additional
and optional functionality to GNOME Shell.
Since GNOME Shell is not API stable, extensions work only against a very
specific version of the shell, usually the same as this package (see
"configure --version"). Also, since extensions are built from many
individual contributors, we cannot guarantee stability or quality for any
specific extension.
For these reasons, distributions are advised to avoid installing or packaging
this module by defaul.

For more information about GNOME Shell Extensions
 [http://live.gnome.org/GnomeShell/Extensions](http://live.gnome.org/GnomeShell/Extensions)

For general information about GNOME Shell
 [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

Bugs should be reported at [http://bugzilla.gnome.org](http://bugzilla.gnome.org) against the 'gnome-shell'
product, with the 'extensions' component.

Extensions
==========

alternate-tab

  Lets you use classic Alt+Tab (window-based instead of app-based) in GNOME Shell.

alternative-status-menu

  For those who want a power off item visible at all the time, replaces GNOME Shell
status menu with one featuring separate Suspend and Power Off. Adds the ability to
hibernate as well.

auto-move-windows

  Lets you manage your workspaces more easily, assigning a specific workspace to
each application as soon as it creates a window, in a manner configurable with a
GSettings key.

dock

  Shows a dock-style task switcher on the right side of the screen.

example

  A minimal example illustrating how to write extensions.

gajim

  Integration with Gajim, a Jabber/XMPP instant messaging client.

user-theme

  Loads a shell theme from ~/.themes/<name>/gnome-shell.

windowsNavigator

  Allow keyboard selection of windows and workspaces in overlay mode.

xrandr-indicator

  Replace the GTK+ based indicator from gnome-settings-daemon with
a native one. Lets the user rotate the laptop monitor and open
display preferences quickly.

License
=======
GNOME Shell Extensions are distributed under the terms of the GNU General Public License,
version 2 or later. See the COPYING file for details.
Individual extensions may be licensed under different terms, see each source
file for details.
```

---

### Post by bulldog on 2011-05-09
Disabling extensions

Per-user and systemwide extensions can be disabled with the GSettings key org.gnome.shell.disabled-extensions

Found this here,

[http://live.gnome.org/GnomeShell/Extensions](http://live.gnome.org/GnomeShell/Extensions)

There's something called LookingGlass [ALT-F2  lg] to start,which will let you see the installed extensions.

---

### Post by SebFZ1 on 2011-05-09
Hi all.
I've got the same issue while trying to build user-theme extension (on line 432).

[FONT=Courier New]Making all in user-theme
make[2]: Entering directory `/home/sebastien/gnome-shell/source/gnome-shell-extensions/extensions/user-theme'
Makefile:432: *** missing separator.  Stop.
make[2]: Leaving directory `/home/sebastien/gnome-shell/source/gnome-shell-extensions/extensions/user-theme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sebastien/gnome-shell/source/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1
[/FONT]
Here is the Makefile extract:
[FONT=Courier New]431:        $(am__relativize); \
432:        new_top_distdir=$$reldir; \
433:        echo " (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) top_distdir="$$new_top_distdir" distdir="$$new_distdir" \\"; \
434:        echo "     am__remove_distdir=: am__skip_length_check=: am__skip_mode_fix=: distdir)"; \[/FONT]

A quick googlization seems to confirm the syntax is ok. So... I do not any idea...
Thanks in advance :)

---

### Post by bulldog on 2011-05-09
> **SebFZ1 said:**
> Hi all.
I've got the same issue while trying to build user-theme extension (on line 432).

[FONT=Courier New]Making all in user-theme
make[2]: Entering directory `/home/sebastien/gnome-shell/source/gnome-shell-extensions/extensions/user-theme'
Makefile:432: *** missing separator.  Stop.
make[2]: Leaving directory `/home/sebastien/gnome-shell/source/gnome-shell-extensions/extensions/user-theme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sebastien/gnome-shell/source/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1
[/FONT]
Here is the Makefile extract:
[FONT=Courier New]431:        $(am__relativize); \
432:        new_top_distdir=$$reldir; \
433:        echo " (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) top_distdir="$$new_top_distdir" distdir="$$new_distdir" \\"; \
434:        echo "     am__remove_distdir=: am__skip_length_check=: am__skip_mode_fix=: distdir)"; \[/FONT]

A quick googlization seems to confirm the syntax is ok. So... I do not any idea...
Thanks in advance :)

The problem is that I have no idea either.
I can only confirm that I did this some time ago,and it worked fine.

Maybe you should take a look at them here,
[http://live.gnome.org/GnomeShell/Extensions](http://live.gnome.org/GnomeShell/Extensions)

And maybe you can find something useful over there.

---

### Post by jjcv on 2011-05-09
> **bulldog said:**
> I think you used the one with ALL the extensions,you should have used this one 
 cd
git clone [http://git.gnome.org/browse/gnome-shell-extensions](http://git.gnome.org/browse/gnome-shell-extensions)
cd gnome-shell-extensions
./autogen.sh --prefix=/usr --enable-extensions=user-theme
make && sudo make install



This worked for me:

```

git clone [http://git.gnome.org/browse/gnome-shell-extensions](http://git.gnome.org/browse/gnome-shell-extensions)
cd gnome-shell-extensions
./autogen.sh --prefix=/usr 
make && sudo make install

```

i.e.  remove the --enable-extensions=user-theme

---

### Post by maverick280857 on 2011-05-10
I don't really know how the favorites bar got enabled and the Alt+Tab feature got disabled. I want to get rid of the favorites bar because I don't need it and it doesn't let me maximize my windows. And of course, I also want Alt+Tab to start working again. I am guessing some messing around with the extensions yesterday may have caused this. 

But I am new to all of this, so I hope you guys will be able to pinpoint the cause.

EDIT: These two problems have been solved...see my post below.

---

### Post by maverick280857 on 2011-05-10
> **bulldog said:**
> Well if you can install them,you can usual un-install them:D

**This is what made the favorites bar disappear**:

```

vivek@krypton:~/.local/share$ cd /usr/share/gnome-shell/
vivek@krypton:/usr/share/gnome-shell$ ls
extensions  js  search_providers  shaders  theme
vivek@krypton:/usr/share/gnome-shell$ cd extensions/
vivek@krypton:/usr/share/gnome-shell/extensions$ ls
alternate-tab@gnome-shell-extensions.gnome.org
alternative-status-menu@gnome-shell-extensions.gnome.org
dock@gnome-shell-extensions.gnome.org
drive-menu@gnome-shell-extensions.gnome.org
places-menu@gnome-shell-extensions.gnome.org
windowsNavigator@gnome-shell-extensions.gnome.org
vivek@krypton:/usr/share/gnome-shell/extensions$ **sudo mv dock@gnome-shell-extensions.gnome.org/ dock@gnome-shell-extensions.gnome.org.old**
vivek@krypton:/usr/share/gnome-shell/extensions$ 

```

or

```
mv /usr/share/gnome-shell/dock@gnome-shell-extensions.gnome.org/ /usr/share/gnome-shell/dock@gnome-shell-extensions.gnome.org.old/
```

followed by a reload of the shell (Alt+F2, and then type 'r' and press Enter).

**And this is what made Alt+Tab work again**:

```
sudo mv /usr/share/gnome-shell/alternate-tab@gnome-shell-extensions.gnome.org/ /usr/share/gnome-shell/alternate-tab@gnome-shell-extensions.gnome.org.old
```

**Some of you may also have to do the same thing in $HOME/.local/share/gnome-shell/extensions**

Thanks for your help guys.

---

### Post by maverick280857 on 2011-05-10
So in summary, when you run autogen.sh, the only it works (for me) is when I remove the --enable-extensions flag. Then,

(a) Alt + Tab stops working
(b) I see a favorites dock
(c) I **_don't_** see themes alongside Windows and Applications in the Gnome Shell.

Problems (a) and (b) have been solved in my previous post.

(c) is the original reason for trying to install the gnome-shell-extensions, and remains unsolved. Any ideas on how to fix (c)?

This is probably because user-theme isn't even in $HOME/.local/share/gnome-shell/extensions:

```

vivek@krypton:~/.local/share/gnome-shell/extensions$ pwd
/home/vivek/.local/share/gnome-shell/extensions
vivek@krypton:~/.local/share/gnome-shell/extensions$ ls -l
total 24
drwxr-xr-x 2 root root 4096 2011-05-10 11:49 alternate-tab@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root root 4096 2011-05-10 11:49 alternative-status-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root root 4096 2011-05-10 11:49 dock@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root root 4096 2011-05-10 11:49 drive-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root root 4096 2011-05-10 11:49 places-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root root 4096 2011-05-10 11:49 windowsNavigator@gnome-shell-extensions.gnome.org
vivek@krypton:~/.local/share/gnome-shell/extensions$ 

```

---

### Post by jjcv on 2011-05-10
> **maverick280857 said:**
> **This is what made the favorites bar disappear**:



Hey, thanks, worked a treat.  All back to normally and working again.

---

### Post by scpxi on 2011-05-10
(c) I **_don't_** see themes alongside Windows and Applications in the Gnome Shell.

if your looking for a quick fix to that you should get **[this]("http://fpmurphy.com/public/themeselector-0.9.tar.gz")**
its an extension to add themes just read the readme for instructions

and thanks for the fixes

---

### Post by maverick280857 on 2011-05-10
> **scpxi said:**
> (c) I **_don't_** see themes alongside Windows and Applications in the Gnome Shell.

if your looking for a quick fix to that you should get **[this]("http://fpmurphy.com/public/themeselector-0.9.tar.gz")**
its an extension to add themes just read the readme for instructions

I have this, but I couldn't get it to work. It looks similar to gnome-shell-extensions..

> and thanks for the fixes

You're welcome.

---

### Post by bulldog on 2011-05-10
> **maverick280857 said:**
> I have this, but I couldn't get it to work. It looks similar to gnome-shell-extensions..



You're welcome.

Read the original post again on [http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

You will see what is written about the theme-selector,

```
Download the Themeselector Gnome Shell extension, extract it and place "extension.js" and metadata.json under the ~/.local/share/gnome-shell/extensions/themeselector@fpmurphy.com/ folder (if it doesn't exist, create it). Then copy all the folders you've extracted to the ~/.themes/ folder (it's a hidden folder in your home directory; if some of those folders exists, merge the data).

Now restart GNOME Shell and you should have a new Themes tab in the Activities overview.
```

---

### Post by scpxi on 2011-05-10
ok I'm just going to place the readme on how to install the theme-selector extension manually here this is how I got it to work
>            README
                         ------

This is v0.9 of the themeselector iextensioni, dated April 30th 2011.

To use this extension the following schema must exist in 
/usr/share/glib-2.0/schemas.

   <?xml version="1.0" encoding="UTF-8"?>
   <schemalist gettext-domain="gnome-shell-extensions">
     <schema path="/org/gnome/shell/extensions/user-theme/" id="org.gnome.shell.extensions.user-theme">
       <key type="s" name="name">
         <default>""</default>
         <summary>Theme name</summary>
         <description>The name of the current shell theme</description>
       </key>
     </schema>
   </schemalist>

The schema must be named org.gnome.shell.extensions.user-theme.gschema.xml
and compiled using glib-compile-schemas.

Place all theme directories in $HOME/.themes/

Places extension.js and metadata.json in:

   $HOME/.local/share/gnome-shell/extensions/themeselector@fpmurphy.com

Create the [email]themeselector@fpmurphy.com[/email] if necessary.

Restart your GNOME shell to load the extension.

This extension has been tested on Fedora 15 Beta.

Send any bug reports to fpm[AT]fpmurphy[DOT]com.

Enjoy!

---

### Post by maverick280857 on 2011-05-13
I have followed the instructions exactly, but it does not work for me. In fact I am not even able to log into the Gnome-Shell. I get an error saying "something went wrong" and that I have to log out.

So maybe this doesn't work for everyone?

---

### Post by bmbaker on 2011-05-13
you might want to-try this :-)

```

cd
git clone http://git.gnome.org/browse/gnome-shell-extensions
cd gnome-shell-extensions
./[autogen.sh]("http://autogen.sh/") --prefix=/usr
make && sudo make install      

```

then do this.

```

cd gnome-shell-extensions 
./autogen.sh --prefix=/usr --enable-extensions=user-theme 
make && sudo make install

```[B]

Download the [Themeselector Gnome Shell extension]("http://fpmurphy.com/public/themeselector-0.9.tar.gz")[/B], [http://fpmurphy.com/public/themeselector-0.9.tar.gz](http://fpmurphy.com/public/themeselector-0.9.tar.gz)
extract it and **place "extension.js" and metadata.json under the ~/.local/share/gnome-shell/extensions/themeselector@fpmurphy.com/** folder (if it doesn't exist, create it). Then **copy all the folders you've extracted to the ~/.themes/ folder** (it's a hidden folder in your home directory;  if some of those folders exists, merge the data).

then Alt-F2 and enter r press enter and it should be wking fine :-)

these instructions are from various places on [http://www.webupd8.org](http://www.webupd8.org)

---

### Post by kelvin spratt on 2011-05-13
Well well well what a lot of palaver to change the shell theme in Arch its already enabled in "gnome tweak tool" came in as a update a few days ago just place shells in ~home/#####/themes all this in a so called hard to use distro.

---

### Post by bmbaker on 2011-05-13
> **kelvin spratt said:**
> Well well well what a lot of palaver to change the shell theme in Arch its already enabled in "gnome tweak tool" came in as a update a few days ago just place shells in ~home/#####/themes all this in a so called hard to use distro.

yes the gnome-tweak wks great :-)
some people also like the the extension from Finnbarr P. Murphy 
its really not difficult to run gnome-shell on ubuntu, a few quirks here and there but generally it runs really well.

I have tried unity for over a week and i must say gnome-shell will definitly my choice :-)

---

### Post by maverick280857 on 2011-05-14
> **kelvin spratt said:**
> Well well well what a lot of palaver to change the shell theme in Arch its already enabled in "gnome tweak tool" came in as a update a few days ago just place shells in ~home/#####/themes all this in a so called hard to use distro.

It's Ubuntu we're talking about. And it's actually good that it's so tough, because its a learning experience ;-)

> **bmbaker said:**
> you might want to-try this :-)

```

cd
git clone http://git.gnome.org/browse/gnome-shell-extensions
cd gnome-shell-extensions
./[autogen.sh]("http://autogen.sh/") --prefix=/usr
make && sudo make install      

```

then do this.

```

cd gnome-shell-extensions 
./autogen.sh --prefix=/usr --enable-extensions=user-theme 
make && sudo make install

```[B]

Download the [Themeselector Gnome Shell extension]("http://fpmurphy.com/public/themeselector-0.9.tar.gz")[/B], [http://fpmurphy.com/public/themeselector-0.9.tar.gz](http://fpmurphy.com/public/themeselector-0.9.tar.gz)
extract it and **place "extension.js" and metadata.json under the ~/.local/share/gnome-shell/extensions/themeselector@fpmurphy.com/** folder (if it doesn't exist, create it). Then **copy all the folders you've extracted to the ~/.themes/ folder** (it's a hidden folder in your home directory;  if some of those folders exists, merge the data).

then Alt-F2 and enter r press enter and it should be wking fine :-)

these instructions are from various places on [http://www.webupd8.org](http://www.webupd8.org)

I've done exactly this, several times now...

I can't use "enable-extensions". I get error messages (listed in previous posts). And when I get rid of the flag, the installation completes successfully but I am unable to log into gnome-shell.

---

### Post by maverick280857 on 2011-05-21
Fresh symptoms:

1. Cairo Dock 'freezes' (hangs)
2. Garbled characters show up in the taskbar on top (where you're supposed to see the date and time, and your user name).

---

### Post by LarsKongo on 2011-05-21
> **maverick280857 said:**
> 2. Garbled characters show up in the taskbar on top (where you're supposed to see the date and time, and your user name).
May have something to do with the text-shadow CSS property used in some themes.

Open gedit and open gnome-shell.css from the theme you're using. CTRL+F text-shadow and remove those lines.

---

### Post by maverick280857 on 2011-05-21
Thanks, I'll try this.

By the way, is it possible to refresh (animate) wallpapers? I have a whole bunch of wallpapers in my Pictures directory. I want an app which picks one of them at random and sets it as my wallpaper, and updates the wallpaper after a preset time period. Note that I am using Gnome 3. [http://ubuntuforums.org/showthread.php?p=10847992#post10847992](http://ubuntuforums.org/showthread.php?p=10847992#post10847992)

---

### Post by maverick280857 on 2011-05-22
So it seems Gnome-Tweak-Tool now lets you enable/disable shell extensions.

But even though my 'UserTheme' extension is installed, I still see the message 'User Theme Extension not enabled', and I also don't see User Theme Extension being listed in the Shell Extensions section...

---

### Post by 23dornot23d on 2011-05-22
Just to see if the extensions are in there ..... to start with .... Charles is the man for these
he also has the links ...... to the files you need.

From [home] have a look in ....... your home directory hidden files ....
[B]/.local/share/gnome-shell/extensions/
[/B]
Gnatty pack ( I would start by downloading this ) ..... [**LINK**]("http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz")

( There are a few steps to getting them working ..... and I start just by getting the themes 
working first ..... on any new system. )

---

### Post by maverick280857 on 2011-05-23
> **23dornot23d said:**
> From [home] have a look in ....... your home directory hidden files ....
[B]/.local/share/gnome-shell/extensions/
[/B]


```
vivek@krypton:~/.local/share/gnome-shell$ pwd
/home/vivek/.local/share/gnome-shell
vivek@krypton:~/.local/share/gnome-shell$ ls -l
total 12
-rw-r--r-- 1 vivek vivek 3589 2011-05-23 03:06 application_state
drwxr-xr-x 9 vivek vivek 4096 2011-05-10 12:15 extensions
drwxr-xr-x 2 vivek vivek 4096 2011-05-10 00:47 themeselector@fpmurphy.com.old
vivek@krypton:~/.local/share/gnome-shell$ cd extensions

```

```

vivek@krypton:~/.local/share/gnome-shell/extensions$ ls -l
total 28
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 alternate-tab@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 alternative-status-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 dock@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 drive-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 places-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 vivek vivek 4096 2011-05-10 12:15 user-theme@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 windowsNavigator@gnome-shell-extensions.gnome.org
vivek@krypton:~/.local/share/gnome-shell/extensions$ 

```

The directories labelled .old represent the extensions I disabled 'by hand'.

---

### Post by maverick280857 on 2011-05-23
> **23dornot23d said:**
> 
Gnatty pack ( I would start by downloading this ) ..... [**LINK**]("http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz")

I get an error when I try to unzip the file using

```

gunzip -d gnatty%20Pack.tar.gz
tar -xvf gnatty%20Pack.tar

```

```

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors

```

EDIT: (SOLVED) See below.

EDIT: This is where one can get it from: [http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz](http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz)

---

### Post by maverick280857 on 2011-05-23
Thanks guys! Using gnatty pack I was able to get the themes to work! Now I see the themes when I click on the 'windows' key on my keyboard. 

1. By the way, gnome-tweak-tool still says that user theme extensions are disabled. Is that something that requires fixing?

2. **Themes show up ONLY if 'GNOME Shell Theme Selector Extension' is switched 'OFF' (please see screenshots).**

3. To select one of the themes installed in $HOME/.themes, does one have to copy the files to /usr/share/gnome-shell/theme? I don't see most of the themes on screen which are already in $HOME/.themes.

------------

Okay so for the record, my folders now look as follows..

**$HOME/.themes/**

```

vivek@krypton:~/.themes$ ls -l
total 60
drwxrwxr-x 3 vivek vivek 4096 2011-05-01 00:32 Adwaita_old
drwx------ 3 vivek vivek 4096 2011-03-26 16:01 Ambiance Alt
drwxr-xr-x 3 vivek vivek 4096 2011-05-01 00:30 ANewHope
drwx------ 3 vivek vivek 4096 2011-05-01 00:26 Atolm
drwxr-xr-x 3 vivek vivek 4096 2008-06-14 08:18 Dark
drwxrwxr-x 3 vivek vivek 4096 2011-05-01 00:27 DarkGlass
drwxrwxr-x 3 vivek vivek 4096 2011-05-01 00:28 DeviantArt
drwxr-xr-x 3 vivek vivek 4096 2011-04-26 15:45 Elegant
drwxrwxr-x 3 vivek vivek 4096 2011-05-01 00:29 Elementary
drwxr-xr-x 3 vivek vivek 4096 2011-05-02 15:46 gs-orta
drwxr-xr-x 3 vivek vivek 4096 2011-05-02 15:46 gs-orta-dark
drwx------ 3 vivek vivek 4096 2010-09-12 21:51 iNDENTURE
drwx------ 3 vivek vivek 4096 2010-09-12 21:51 iNDENTURE-outlined
drwxr-xr-x 3 vivek vivek 4096 2011-04-29 08:58 Lexinya
drwxrwxr-x 3 vivek vivek 4096 2011-05-01 00:30 SmoothInsert
vivek@krypton:~/.themes$ 

```

**$HOME/.local/share/gnome-shell**

```

vivek@krypton:~/.local/share/gnome-shell$ ls -l
total 16
-rw-r--r--  1 vivek vivek 3484 2011-05-23 12:07 application_state
drwxr-xr-x 10 vivek vivek 4096 2011-05-23 12:18 extensions
drwxrwxr-x  2 vivek vivek 4096 2011-05-13 18:23 themeselector@fpmurphy.com
drwxr-xr-x  2 vivek vivek 4096 2011-05-10 00:47 themeselector@fpmurphy.com.old
vivek@krypton:~/.local/share/gnome-shell$ 

```

**$HOME/.local/share/gnome-shell/extensions**

```

vivek@krypton:~/.local/share/gnome-shell/extensions$ ls -l
total 32
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 alternate-tab@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 alternative-status-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 dock@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 drive-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 places-menu@gnome-shell-extensions.gnome.org
drwxrwxr-x 2 vivek vivek 4096 2011-05-13 18:23 themeselector@fpmurphy.com
drwxr-xr-x 2 vivek vivek 4096 2011-05-13 18:23 user-theme@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 windowsNavigator@gnome-shell-extensions.gnome.org
vivek@krypton:~/.local/share/gnome-shell/extensions$ 

```

**/usr/share/themes**

```

vivek@krypton:/usr/share/themes$ ls -l
total 136
drwxr-xr-x 6 root  root  4096 2011-05-08 10:12 Adwaita
drwxr-xr-x 3 root  root  4096 2011-04-26 04:24 AgingGorilla
drwxr-xr-x 4 root  root  4096 2011-04-26 04:29 Ambiance
drwxr-xr-x 3 root  root  4096 2011-04-26 04:24 Atlanta
drwxr-xr-x 2 vivek vivek 4096 2011-05-04 23:45 background
drwxr-xr-x 3 root  root  4096 2011-04-26 04:24 Bright
drwxr-xr-x 5 root  root  4096 2011-05-05 15:21 Clearlooks
drwxr-xr-x 4 root  root  4096 2011-05-05 15:21 ClearlooksClassic
drwxr-xr-x 5 root  root  4096 2011-05-07 00:58 Crux
drwxr-xr-x 4 root  root  4096 2011-05-05 15:18 Default
drwxr-xr-x 4 root  root  4096 2011-04-26 04:28 Dust
drwxr-xr-x 4 root  root  4096 2011-04-26 04:28 Dust Sand
drwxr-xr-x 4 root  root  4096 2011-05-05 15:18 Emacs
drwxr-xr-x 3 root  root  4096 2011-04-26 04:24 Esco
drwxr-xr-x 4 root  root  4096 2011-05-07 00:58 Glider
drwxr-xr-x 4 root  root  4096 2011-05-07 00:58 Glossy
drwxr-xr-x 3 root  root  4096 2011-05-05 15:21 GNOME3
drwxr-xr-x 4 root  root  4096 2011-05-08 10:12 HighContrast
drwxr-xr-x 4 root  root  4096 2011-05-08 10:12 HighContrastInverse
drwxr-xr-x 4 root  root  4096 2011-05-05 15:21 Industrial
drwxr-xr-x 4 root  root  4096 2011-05-05 15:21 Inverted
drwxr-xr-x 4 root  root  4096 2011-05-08 10:12 LowContrast
drwxr-xr-x 3 root  root  4096 2011-04-26 04:24 Metabox
drwxr-xr-x 4 root  root  4096 2011-05-06 01:06 MintLiner
drwxr-xr-x 5 root  root  4096 2011-05-07 00:58 Mist
-rwxr-xr-x 1 vivek vivek 6153 2011-05-01 20:38 nautilus.css
drwxr-xr-x 4 root  root  4096 2011-04-26 04:28 New Wave
drwxr-xr-x 3 root  root  4096 2011-04-26 04:28 New Wave Dark Menus
drwxr-xr-x 4 root  root  4096 2011-04-26 04:29 Radiance
drwxr-xr-x 4 root  root  4096 2011-05-05 15:18 Raleigh
drwxr-xr-x 4 root  root  4096 2011-05-05 15:21 Redmond
drwxr-xr-x 4 root  root  4096 2011-05-05 15:21 Simple
drwxr-xr-x 4 root  root  4096 2011-05-05 15:21 ThinIce
vivek@krypton:/usr/share/themes$ 

```

All I've done is follow the README from Charles Bowman in his gnatty pack.

---

### Post by 23dornot23d on 2011-05-23
Yep good one .....

Now all you need to do is install the two .deb files ....... that were alien packed ....

[B]gnome-shell-extensions-common_3.0.1-2_all.deb
[/B]
**gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb**

and then the Yellow marker in the tweak tool will go away .......

You need to do these as root though as they need to be answered with a y reply 
to say its ok to add them.

---

### Post by maverick280857 on 2011-05-23
> **23dornot23d said:**
> Yep good one .....

Now all you need to do is install the two .deb files ....... that were alien packed ....

[B]gnome-shell-extensions-common_3.0.1-2_all.deb
[/B]
**gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb**

and then the Yellow marker in the tweak tool will go away .......

You need to do these as root though as they need to be answered with a y reply 
to say its ok to add them.

Where can I get these? I have installed 'gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb' -- it was part of the gnatty pack tarball. Where did you get the first .deb file?

EDIT: Found them

[http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gnome-shell-extensions-common%5E_3.0.1-2%5E_all.deb](http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gnome-shell-extensions-common%5E_3.0.1-2%5E_all.deb)

[http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux?wa=wsignin1.0&sa=168264950](http://cid-32ec6e89f4aa803b.office.live.com/browse.aspx/Linux?wa=wsignin1.0&sa=168264950)

[https://bugs.launchpad.net/ugr-meta/+bug/772221](https://bugs.launchpad.net/ugr-meta/+bug/772221)

**I've installed them gnome-shell-extensions-common and gnome-shell-extensions-user-theme...no change in gnome-tweak-tool.**

---

### Post by 23dornot23d on 2011-05-23
Have a look see what list you get back from this command .....

> 
(only needed if aptitude is not already installed)
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
[B]sudo aptitude safe-upgrade
[/B]
A screen shot here of the packages it wants to update may be useful  .......

  To see what it produces ..... ( answer no ) ....... when it asks .... if you want to upgrade
or yes if you feel the programs will cause you no problems.

  [B]Would like to see where your system stands for updates and upgrades at the moment though .
[/B] 
We have had to do a cold reboot too in the past  .... and then it seems to work ...... 

( Just restarting gnome-shell does not seem to pick up the changes )

if you would please.

---

### Post by maverick280857 on 2011-05-23
> **23dornot23d said:**
> Have a look see what list you get back from this command .....

[B]sudo aptitude safe-upgrade
[/B]
A screen shot here of the packages it wants to update may be useful  .......

```

vivek@krypton:~$ sudo aptitude safe-upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  gir1.2-totem-1.0{a} gir1.2-totem-plparser-1.0{a} libtotem0{a} 
The following packages will be upgraded:
  baobab gnome-screenshot gnome-search-tool gnome-system-log 
  gnome-utils-common totem totem-common totem-mozilla totem-plugins 
9 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5 MB of archives. After unpacking 565 kB will be used.
Do you want to continue? [Y/n/?] 

```

I'll post the output after a reboot in a bit. Am I supposed to say Y to the aptitude safe-upgrade?

Also, what's the difference between 'sudo aptitude safe-upgrade' and 'sudo apt-get upgrade'?

**EDIT: I did the upgrade, and rebooted the system. But I still see only 6 themes on the themes tab (when I hit the windows key). And I still see 'User Theme Extensions not enabled' in gnome-tweak-tool.**

---

### Post by 23dornot23d on 2011-05-23
> **maverick280857 said:**
> ```

vivek@krypton:~$ sudo aptitude safe-upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  gir1.2-totem-1.0{a} gir1.2-totem-plparser-1.0{a} libtotem0{a} 
The following packages will be upgraded:
  baobab gnome-screenshot gnome-search-tool gnome-system-log 
  gnome-utils-common totem totem-common totem-mozilla totem-plugins 
9 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5 MB of archives. After unpacking 565 kB will be used.
Do you want to continue? [Y/n/?] 

```I'll post the output after a reboot in a bit. Am I supposed to say Y to the aptitude safe-upgrade?

Also, what's the difference between 'sudo aptitude safe-upgrade' and 'sudo apt-get upgrade'?

[COLOR=Red][B]The difference for me is using aptitude safe-upgrade
[/B][COLOR=Black][I]seems to do more dependency checks and touch wood ..... upto just from my days
of using linux it has never left me in a position where I need to repair my system.[/I][/COLOR][B]

[COLOR=Black]The other option[/COLOR][/B][/COLOR][COLOR=Red][B][COLOR=Black] ...... [/COLOR]
apt-get works very well ......[I][COLOR=Black] but I have ended up in all sorts
of problems using it .... [/COLOR][/I]
[/B][COLOR=Black]_*( so to answer its just from my bad experiences with apt-get )*_[/COLOR][/COLOR][COLOR=Black]
[/COLOR]
> 
**EDIT: I did the upgrade, and rebooted the system. But I still see only 6 themes on the themes tab (when I hit the windows key). And I still see 'User Theme Extensions not enabled' in gnome-tweak-tool.**

You may not have the same PPA's as me ...... but if you have the Themes to choose now
it is working.

Here is a link to some more information ...... take it in and then you can decide whether
or not you want to use it or not ............ [LINK ]("http://ubuntu-tweak.com/source/gnome-shell-testing/")

But at the moment - if you are having no other problems with it ..... in time some of the new additions may become available.

[IMG]http://img714.imageshack.us/img714/8652/tweak3.jpg[/IMG]

I use ricotz / team-gnome and ugr at the moment ..... and everything is going well
but I always use aptitude safe-upgrade ....... and I carefully look at what is going to be replaced .......

[IMG]http://img8.imageshack.us/img8/2376/tweak2.jpg[/IMG]

 and then make my decisions ...... we can always say no .....


[URL="http://ubuntu-tweak.com/source/gnome-shell-testing/"]
[/URL]

---

### Post by maverick280857 on 2011-05-24
> **23dornot23d said:**
> You may not have the same PPA's as me ...... but if you have the Themes to choose now
it is working.

I am not sure what you mean by working because there are two ways I can now select themes:

1. Through gnome-tweak-tool.
2. By pressing the 'windows' key on my keyboard and selecting the Themes tab.

But these two do not refer to the same thing. The selections in gnome-tweak-tool correspond to /usr/share/themes, whereas the ones in the 'themes tab' (option 2) correspond to **some** of the stuff in $HOME/.themes.

I have attached screenshots for both..

What are the differences between

1. Gtk+ Theme
2. Shell Theme
3. Window Theme

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> 
When I try to install unseen's deb file, I get the following error message:

"The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath."

"Lintian check results for /tmp/gnome-shell-extensions-user-theme_3.0.0-6.6_all.deb:
E: gnome-shell-extensions-user-theme: maintainer-address-malformed Charles Bowman <chuck@Gnome-3>
"

This is two weeks old, but just stumbled across the thread.  That deb was created from the Fedora rpm using alien.  It complains, less so using gdebi, but it works.

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> When I unzip the contents of themeselector into $HOME/.local/share/gnome-shell and reboot the system, I am unable to boot into GNOME 3. I get an error message saying that something bad has happened and I have to log out. The situation is remedied only by deleting the themeselector files from the abovementioned directory.

As long as there is a ~/.local/share/gnome-shell/extensions directory and [email]themeselector@fpmurphy.com[/email] directory resides within it, it should work, providing user theme support is installed.

** (might not need user theme support extension)

---

### Post by cbowman57 on 2011-05-24
> **peter.senna said:**
> I'm missing the system-monitor applet that I was used to have on the top bar. Is there a way to install it in gnome-3?

Thanks!

There is an extension for that now, look it up on webupd8.

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> ```
vivek@krypton:~/.local/share/gnome-shell$ pwd
/home/vivek/.local/share/gnome-shell
vivek@krypton:~/.local/share/gnome-shell$ ls -l
total 12
-rw-r--r-- 1 vivek vivek 3589 2011-05-23 03:06 application_state
drwxr-xr-x 9 vivek vivek 4096 2011-05-10 12:15 extensions
drwxr-xr-x 2 vivek vivek 4096 2011-05-10 00:47 themeselector@fpmurphy.com.old
vivek@krypton:~/.local/share/gnome-shell$ cd extensions

```

```

vivek@krypton:~/.local/share/gnome-shell/extensions$ ls -l
total 28
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 alternate-tab@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 alternative-status-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 dock@gnome-shell-extensions.gnome.org.old
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 drive-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 places-menu@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 vivek vivek 4096 2011-05-10 12:15 user-theme@gnome-shell-extensions.gnome.org
drwxr-xr-x 2 root  root  4096 2011-05-10 11:49 windowsNavigator@gnome-shell-extensions.gnome.org
vivek@krypton:~/.local/share/gnome-shell/extensions$ 

```

The directories labelled .old represent the extensions I disabled 'by hand'.

That's a simple fix, the themeselector directory needs to be moved from gnome-shell to gnome-shell/extensions

---

### Post by maverick280857 on 2011-05-24
> **cbowman57 said:**
> As long as there is a ~/.local/share/gnome-shell/extensions directory and [email]themeselector@fpmurphy.com[/email] directory resides within it, it should work, providing user theme support is installed.

Hi Charles, thanks for the info. My current status is described in post #62: [http://ubuntuforums.org/showpost.php?p=10855208&postcount=62](http://ubuntuforums.org/showpost.php?p=10855208&postcount=62). I am able to do *something*, which is better than nothing now thanks to you and 23dornot23d :-)

[QUOTE=cbowman57]That's a simple fix, the themeselector directory needs to be moved from gnome-shell to gnome-shell/extensions[/QUOTE]

Yeah, I moved it. My current directory structure is now listed in post #56: [http://ubuntuforums.org/showpost.php?p=10851495&postcount=56](http://ubuntuforums.org/showpost.php?p=10851495&postcount=56)

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> I am not sure what you mean by working because there are two ways I can now select themes:

1. Through gnome-tweak-tool.
2. By pressing the 'windows' key on my keyboard and selecting the Themes tab.

But these two do not refer to the same thing. The selections in gnome-tweak-tool correspond to /usr/share/themes, whereas the ones in the 'themes tab' (option 2) correspond to **some** of the stuff in $HOME/.themes.

I have attached screenshots for both..

What are the differences between

1. Gtk+ Theme
2. Shell Theme
3. Window Theme

Shell theme, the top panel, overall desktop.
Gtk3 Theme, what's inside the windows borders.
Window theme, uses mutter or metacity. Window borders & title bar.

Looking at my desktop.  I use Atolm for my shell theme, the dark verion of Adwaita for GTK3, & iNDENTURED for the window (metacity) theme, Aw0ken for the icon theme.

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> Hi Charles, thanks for the info. My current status is described in post #62: [http://ubuntuforums.org/showpost.php?p=10855208&postcount=62](http://ubuntuforums.org/showpost.php?p=10855208&postcount=62). I am able to do *something*, which is better than nothing now thanks to you and 23dornot23d :-)



Yeah, I moved it. My current directory structure is now listed in post #56: [http://ubuntuforums.org/showpost.php?p=10851495&postcount=56](http://ubuntuforums.org/showpost.php?p=10851495&postcount=56)

No problem, I realized they were old posts but responded in the interests of those that might stumble upon this thread looking for answers.  The detailed information you posted is most likely the kind of problems that a lot of people are having, or will have. :)

---

### Post by maverick280857 on 2011-05-24
> **cbowman57 said:**
> No problem, I realized they were old posts but responded in the interests of those that might stumble upon this thread looking for answers.  The detailed information you posted is most likely the kind of problems that a lot of people are having, or will have. :)

Okay, I rebooted and something must've happened automatically because gnome-tweak-tool no longer says that user-theme-extensions are disabled, and I can in fact pick a shell theme. Do the screenshots look okay?

[QUOTE=cbowman57]Looking at my desktop. I use Atolm for my shell theme, the dark verion of Adwaita for GTK3, & iNDENTURED for the window (metacity) theme, Aw0ken for the icon theme.[/QUOTE]

How have you been able to make things transparent, and black? :-P

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> Okay, I rebooted and something must've happened automatically because gnome-tweak-tool no longer says that user-theme-extensions are disabled, and I can in fact pick a shell theme. Do the screenshots look okay?

How have you been able to make things transparent, and black? :-P

Yes, they look fine.

In the terminal it's just a matter of tweaking profile preferences and selecting/adjusting transparency for the background.

The shell theme is Atolm, Gtk3 theme is Adwaita dark (go to /usr/share/themes/Adwaita/gtk3 and rename gtk-dark.css to gtk.css), the window theme is metacity iNDENTURED-outlined.

---

### Post by maverick280857 on 2011-05-24
> **cbowman57 said:**
> Yes, they look fine.

In the terminal it's just a matter of tweaking profile preferences and selecting/adjusting transparency for the background.

Yeah, I tried this. I am able to set up a solid color or a background image as the background, but I can't get the transparent background setting to work somehow. It used to work fine in 10.10.

[QUOTE=cbowman57]The shell theme is Atolm, Gtk3 theme is Adwaita dark (go to /usr/share/themes/Adwaita/gtk3 and rename gtk-dark.css to gtk.css), the window theme is metacity iNDENTURED-outlined.[/QUOTE]

Thanks, I'll try this. Is 'iNDENTURED-outlined' the same as 'metacity iNDENTURED-outlined'?

It seems now all we have left on the wish list are a dynamic wallpaper and a screensaver :-)

PS -- Some excellent wallpapers and images are available from [www.jootix.com](www.jootix.com).

---

### Post by maverick280857 on 2011-05-24
How have you customized the taskbar on top (if that's what it's called), to show weather, and the drop down menu on the left which is reminiscent of Gnome2? I only see 'Activities'.

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> Yeah, I tried this. I am able to set up a solid color or a background image as the background, but I can't get the transparent background setting to work somehow. It used to work fine in 10.10.

Odd?


> Thanks, I'll try this. Is 'iNDENTURED-outlined' the same as 'metacity iNDENTURED-outlined'?

Yes.

> It seems now all we have left on the wish list are a dynamic wallpaper and a screensaver :-)

True, it will take some time but I don't think they intended for G3 shell to have a screensaver.  The rotating wallpaper would be nice to have again.

> PS -- Some excellent wallpapers and images are available from [www.jootix.com](www.jootix.com).

I may check that out.  Thanks. :)

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> How have you customized the taskbar on top (if that's what it's called), to show weather, and the drop down menu on the left which is reminiscent of Gnome2? I only see 'Activities'.


Yes, all extensions.  Most should be in the gNatty Pack, the weather extension I just got working tonight.  They have an article on it over at webupd8.  With the help of David Walker I edited mine a little bit.  In it's original form it crashed my desktop when used in conjunction with a couple of the other extensions.

---

### Post by maverick280857 on 2011-05-24
> **cbowman57 said:**
> Yes, all extensions.  Most should be in the gNatty Pack, the weather extension I just got working tonight.  They have an article on it over at webupd8.  With the help of David Walker I edited mine a little bit.  In it's original form it crashed my desktop when used in conjunction with a couple of the other extensions.

Okay, where will the latest version of gnatty pack be hosted (so that I update my tarball every few days/weeks)?

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> Okay, where will the latest version of gnatty pack be hosted (so that I update my tarball every few days/weeks)?

Link to thread is in my signature.  Links are in post #1.

---

### Post by maverick280857 on 2011-05-24
Just installed the weather extension...I'm not able to log into Gnome-Shell now. It gives me the old error message 'something went wrong' and makes me log out. I am able to log into 'Ubuntu' though which looks like Unity. And thanks to wicd, I am able to access this website.

EDIT: Just read "Note: this extension is incompatible with the following Gnome Shell extensions: Applications, Panel Favorites & App Indicator (thanks to Charles Bowman for the info)." :-)

---

### Post by cbowman57 on 2011-05-24
> **maverick280857 said:**
> Just installed the weather extension...I'm not able to log into Gnome-Shell now. It gives me the old error message 'something went wrong' and makes me log out. I am able to log into 'Ubuntu' though which looks like Unity. And thanks to wicd, I am able to access this website.

In a post in this thread, within the past hour I posted this: "Yes, all extensions. Most should be in the gNatty Pack, the weather extension I just got working tonight. They have an article on it over at webupd8. **With the help of David Walker I edited mine a little bit. In it's original form it crashed my desktop when used in conjunction with a couple of the other extensions.**"

The information you need is once again in the thread that is linked in my signature.

Use whatever desktop or recovery console you can use & move or delete the weather extension until you get it sorted out.

:)  If you look at the comments on Webupd8 you will find a comment of mine in reply to David Walker, the solution is there.  I'm tired, 4am here, off to bed for me in a couple minutes.

---

### Post by maverick280857 on 2011-05-24
Haha it seems you didn't read my original post, where I acknowledged the comment on webup8...my bad (I used 'EDIT' instead of writing a new post). I got rid of the weather applet. I have a screenlet showing the weather, so I didn't really need it. Anyway, good night ;-)

The only annoying thing about gnome3 is that it seems to forget the screen brightness setting every now and then. This seems to be a bug with the gnome-power-manager on my laptop.

---

### Post by maverick280857 on 2011-05-24
Is there some way one can change the background and themes for the Gnome3 login-screen?

---

### Post by maverick280857 on 2011-05-26
All of a sudden, the 'gnatty' menu button has disappeared. I made no changes, and my extensions folder is the same old one:

```

vivek@krypton:~/.local/share/gnome-shell/extensions$ ls
alternate-tab@gnome-shell-extensions.gnome.org.old
alternative-status-menu@gnome-shell-extensions.gnome.org
Applications_Menu@rmy.pobox.com
dock@gnome-shell-extensions.gnome.org.old
drive-menu@gnome-shell-extensions.gnome.org
kovtray@kov.eti.br
Move_Clock@rmy.pobox.com
noa11y@example.com
paradoxxxzero-gnome-shell-system-monitor-applet-2616174
pidgin-integration
places-menu
places-menu@gnome-shell-extensions.gnome.org
themeselector@fpmurphy.com.old
user-theme@gnome-shell-extensions.gnome.org
weather@venemo.net.old
windowsNavigator@gnome-shell-extensions.gnome.org
vivek@krypton:~/.local/share/gnome-shell/extensions$ 

```

But most of these extensions do not appear in gnome-tweak-tool anymore (please refer to the attached screenshot).

Anyone know what could've happened?

---

### Post by 23dornot23d on 2011-05-26
What folders do you have in this directory ......

[home]/.local/share/gnome-shell/extensions/

ok just seen your listing ..... are the privileges any different on these compared to the others.



pidgin-integration 
[EMAIL="user-theme@gnome-shell-extensions.gnome.org"]user-theme@gnome-shell-extensions.gnome.org[/EMAIL]

[EMAIL="Move_Clock@rmy.pobox.com"]Move_Clock@rmy.pobox.com[/EMAIL]

[EMAIL="kovtray@kov.eti.br"]kovtray@kov.eti.br[/EMAIL]


Ok guess the answer is in the version ...... cheers ..... C Bowman ..... ( we posted at similar times )

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> All of a sudden, the 'gnatty' menu button has disappeared. I made no changes, and my extensions folder is the same old one:

```

vivek@krypton:~/.local/share/gnome-shell/extensions$ ls
alternate-tab@gnome-shell-extensions.gnome.org.old
alternative-status-menu@gnome-shell-extensions.gnome.org
Applications_Menu@rmy.pobox.com
dock@gnome-shell-extensions.gnome.org.old
drive-menu@gnome-shell-extensions.gnome.org
kovtray@kov.eti.br
Move_Clock@rmy.pobox.com
noa11y@example.com
paradoxxxzero-gnome-shell-system-monitor-applet-2616174
pidgin-integration
places-menu
places-menu@gnome-shell-extensions.gnome.org
themeselector@fpmurphy.com.old
user-theme@gnome-shell-extensions.gnome.org
weather@venemo.net.old
windowsNavigator@gnome-shell-extensions.gnome.org
vivek@krypton:~/.local/share/gnome-shell/extensions$ 

```

But most of these extensions do not appear in gnome-tweak-tool anymore (please refer to the attached screenshot).

Anyone know what could've happened?

```
metadata.json
{"shell-version": ["3.0"],
"uuid": "App@Indicator",
"name": "Application Indicators",
"description": "Add application indicators to the panel",
"url": "http://ubuntuforums.org/showthread.php?t=1754198"
}
```

Gnome-shell jumped to 3.0.2 this morning (or last night, whatever)  If you look at the metadata.json, "shell-version", you may have to change it to 3.0.2, or simply drop the minor version, i.e. "3.0"

Just a guess, but that's the most likely explanation.

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> Is there some way one can change the background and themes for the Gnome3 login-screen?

Haven't found a method that worked for the background screen, if I could discover the name it would just be a simple matter of replacing image & keeping the same name.  I think waspbloke found a method on the Arch forums but it didn't work for me.

The login-window adopts the system's gtk3 theme.

---

### Post by maverick280857 on 2011-05-26
> **cbowman57 said:**
> ```
metadata.json
{"shell-version": ["3.0"],
"uuid": "App@Indicator",
"name": "Application Indicators",
"description": "Add application indicators to the panel",
"url": "http://ubuntuforums.org/showthread.php?t=1754198"
}
```

Gnome-shell jumped to 3.0.2 this morning (or last night, whatever)  If you look at the metadata.json, "shell-version", you may have to change it to 3.0.2, or simply drop the minor version, i.e. "3.0"

Just a guess, but that's the most likely explanation.

Ah great, using the minor version restored everything back to 'normal'. Thank you!

---

### Post by maverick280857 on 2011-05-26
Is changing it to use the minor version "3.0" a permanent fix for all "3.0.x" where x > 0?

I noticed that I didn't have to change it for $HOME/.local/share/gnome-shell/themeselector@fpmurphy.com/metadata.json. I did change it eventually, but it did not seem to be necessary. Why is that so?

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> Ah great, using the minor version restored everything back to 'normal'. Thank you!


Yeah, I've tried to maintain the ones I use so they ignore those shell changes, but I occasionally miss a few.

BTW, simple edit to change gNatty to whatever you want. I just did that to kind of brand the extensions in the gNatty Pack.

Glad that fixed it up for you, undoubtedly it affected the other 2 people using the pack too. :lol:

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> Is changing it to use the minor version "3.0" a permanent fix for all "3.0.x" where x > 0?

I noticed that I didn't have to change it for $HOME/.local/share/gnome-shell/themeselector@fpmurphy.com/metadata.json. I did change it eventually, but it did not seem to be necessary. Why is that so?

I believe it works universally at this time but don't take that as gospel.  As soon as I say it will, somebody will surely say that it doesn't. 

Gotta love forums. :)

---

### Post by maverick280857 on 2011-05-26
I don't have Themes anymore! I mean I don't see them when I press the windows key -- I used to see them along with "Windows" and "Applications".

---

### Post by maverick280857 on 2011-05-26
> **23dornot23d said:**
> What folders do you have in this directory ......

[home]/.local/share/gnome-shell/extensions/

ok just seen your listing ..... are the privileges any different on these compared to the others.



pidgin-integration 
[EMAIL="user-theme@gnome-shell-extensions.gnome.org"]user-theme@gnome-shell-extensions.gnome.org[/EMAIL]

[EMAIL="Move_Clock@rmy.pobox.com"]Move_Clock@rmy.pobox.com[/EMAIL]

[EMAIL="kovtray@kov.eti.br"]kovtray@kov.eti.br[/EMAIL]

As a matter of fact they were.

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> I don't have Themes anymore! I mean I don't see them when I press the windows key -- I used to see them along with "Windows" and "Applications".

Ok, you can check the status & errors of your extensions with Looking Glass.

Can't remember if theme@selector is dependent on gnome-shell-user-themes-extension or not, but if it does go into /usr/share/gnome-shell/extensions and double check the version number in that extension, it might require a quick edit.

With gnome-tweak-tool you can disable the User themes extension & still have theme support.  Apparently there is something about the .css in that extension that affect the appearance of some other extensions, i.e. weather extension.  Thanks to Andrew over at Webupd8 for that tip.

---

### Post by 23dornot23d on 2011-05-26
The only two I have in there for themes to work are these ,,,, 

I noticed earlier if you do not have them - themes mysteriously start swapping ...

[IMG]http://img845.imageshack.us/img845/9661/extm.jpg[/IMG]

---

### Post by cbowman57 on 2011-05-26
> **23dornot23d said:**
> What folders do you have in this directory ......

[home]/.local/share/gnome-shell/extensions/

ok just seen your listing ..... are the privileges any different on these compared to the others.



pidgin-integration 
[email]user-theme@gnome-shell-extensions.gnome.org"]user-theme@gnome-shell-extensions.gnome.org[/email]

[email]Move_Clock@rmy.pobox.com"]Move_Clock@rmy.pobox.com[/email]

[email]kovtray@kov.eti.br"]kovtray@kov.eti.br[/email]


Ok guess the answer is in the version ...... cheers ..... C Bowman ..... ( we posted at similar times )

Hey, I didn't consider permissions, good idea too.

We help where we can. :)

---

### Post by cbowman57 on 2011-05-26
> **23dornot23d said:**
> The only two I have in there for themes to work are these ,,,, 

I noticed earlier if you do not have them - themes mysteriously start swapping ...

[IMG]http://img845.imageshack.us/img845/9661/extm.jpg[/IMG]

Pretty sure the .deb installed that user theme extension to the /usr/share/gnome-shell/extensions location.  I think it works from either location but if you check with looking glass it will issue a warning if they are in both locations, but will still work.

---

### Post by maverick280857 on 2011-05-26
What I mean is: before the updates today, I was able to see Themes as a separate tab (not in gnome-tweak-tool, but in Gnome Shell).

Also, why is Alternative Status Menu extension perpetually disabled in gnome-tweak-tool? Is that the case for you too?

---

### Post by maverick280857 on 2011-05-26
> **23dornot23d said:**
> The only two I have in there for themes to work are these ,,,, 

I noticed earlier if you do not have them - themes mysteriously start swapping ...

[IMG]http://img845.imageshack.us/img845/9661/extm.jpg[/IMG]

Yes, you're right. Thanks for pointing it out. In the afternoon, I had renamed [email]themeselector@fpmurphy.com[/email] to [email]themeselector@fpmurphy.com.old[/email] to fix something, and I forgot to name it back. Doing so seems to have solved the problem for now.

So now, I have two [email]themeselector@fpmurphy.com[/email] directories. One is in

```
$HOME/.local/share/gnome-shell/
```

and the other is in

```
$HOME/.local/share/gnome-shell/extensions/
```

[B]
The latter is required if you want to be able to switch to themes using the tabs (using the 'windows' key on your keyboard, not gnome-tweak-tool).[/B]

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> What I mean is: before the updates today, I was able to see Themes as a separate tab (not in gnome-tweak-tool, but in Gnome Shell). Please see the attached screenshot.

Also, why is Alternative Status Menu extension perpetually disabled in gnome-tweak-tool? Is that the case for you too?

No, all of my extensions are functional, with the exception of alt-tab, which I cannot get to work for some reason, no big deal, the default behavior is great anyway.

Just noticed that new shell wiped out my user name removal in the status menu, that happens with every shell change.  Time to visit the link & bust out gedit. :)

---

### Post by maverick280857 on 2011-05-26
> **cbowman57 said:**
> No, all of my extensions are functional, with the exception of alt-tab, which I cannot get to work for some reason, no big deal, the default behavior is great anyway.

Well, I just "re-installed" the alt-menu extension by overwriting the contents of /usr/share/gnome-shell/extensions/ as well as $HOME/.local/share/gnome-shell/extensions/ and restarting the shell. But it is still disabled in the gnome-tweak-tool.

This is what it's modified metadata.json looks like now

```

{
 "uuid": "alternative-status-menu@gnome-shell-extensions.gnome.org",
 "name": "Alternative Status Menu",
 "description": "Replaces GNOME Shell Status Menu with one showing Suspend/Hiber
nate and Power Off as separate items",
 "shell-version": [ "3.0.2" ],
 "localedir": "/usr/share/locale",
 "url": "http://git.gnome.org/gnome-shell-extensions"
}

```

I tried to change the shell-version to 3.0 too, but it does not help. Any ideas?

---

### Post by cbowman57 on 2011-05-26
Yes, verify that the uuid matches the name of the directory it is in exactly & you might also want to remove it from /usr/share/gnome-shell/extensions, it's redundant and it might be crashing due to it being loaded twice. ~/.local/share/gnome-shell/extensions is the only place it's needed for the user.

I suppose if it's a multi-user system you'd want it to be universally accessible, in which case, do the reverse of what I wrote above. :)

---

### Post by maverick280857 on 2011-05-26
> **cbowman57 said:**
> Yes, verify that the uuid matches the name of the directory it is in exactly & you might also want to remove it from /usr/share/gnome-shell/extensions, it's redundant and it might be crashing due to it being loaded twice. ~/.local/share/gnome-shell/extensions is the only place it's needed for the user.

Done, no improvement..it's still disabled.

---

### Post by cbowman57 on 2011-05-26
> **maverick280857 said:**
> Done, no improvement..it's still disabled.

What is Looking Glass telling you, if anything?

---

### Post by maverick280857 on 2011-05-26
> **cbowman57 said:**
> What is Looking Glass telling you, if anything?

I assume you're not referring to the desktop environment, right? How do I install and execute it? Couldn't find useful links for natty on google...

---

### Post by cbowman57 on 2011-05-26
alt+f2, lg, enter

---

### Post by bmbaker on 2011-05-26
> **maverick280857 said:**
> I assume you're not referring to the desktop environment, right? How do I install and execute it? Couldn't find useful links for natty on google...

do alt f2 and enter lg
press Esc to exit

---

### Post by bmbaker on 2011-05-26
snap! :-)

---

### Post by cbowman57 on 2011-05-26
> **bmbaker said:**
> snap! :-)

:)

---

### Post by maverick280857 on 2011-05-27
Ok, and what am I supposed to see in lg?

---

### Post by maverick280857 on 2011-05-27
> **cbowman57 said:**
> BTW, simple edit to change gNatty to whatever you want. I just did that to kind of brand the extensions in the gNatty Pack.

Change what?

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> Ok, and what am I supposed to see in lg?

The 3d tab will show if there are errors in an extension.

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> Change what?

The text for the Application menu extension.

---

### Post by maverick280857 on 2011-05-27
Okay I have attached screenshots of 'Errors' and 'Extensions' from lg.

---

### Post by maverick280857 on 2011-05-27
A lot of my themes don't have themes.json, which is weird. The system monitor extension doesn't have metadata.json.

It seems the error tab isn't scrollable.

---

### Post by maverick280857 on 2011-05-27
Okay I cleaned up a little bit, and got rid of the extensions I had disabled by hand. Now, the errors tab looks like this (attached).

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> A lot of my themes don't have themes.json, which is weird. The system monitor extension doesn't have metadata.json.

It seems the error tab isn't scrollable.

The metacity themes don't have metadata.json, no big deal.

Looks like the theme selector is loading without error, something on your system might be broken.

To display the ones giving you a problem you might have to disable the ones that work just so they will all display in the looking glass.

---

### Post by maverick280857 on 2011-05-27
> **cbowman57 said:**
> Looks like the theme selector is loading without error, something on your system might be broken.

Can you elaborate?

[QUOTE=cbowman57]To display the ones giving you a problem you might have to disable the ones that work just so they will all display in the looking glass.[/QUOTE]

Yeah, I did that. I've posted an updated screenshot here: [http://ubuntuforums.org/showpost.php?p=10868079&postcount=114](http://ubuntuforums.org/showpost.php?p=10868079&postcount=114)

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> Can you elaborate?

Just mysterious problems, I have no idea what it might be.  I've run into a few today that just won't work & give an error message similar to the one the alt-status menu is giving you.



> Yeah, I did that. I've posted an updated screenshot here: [http://ubuntuforums.org/showpost.php?p=10868079&postcount=114](http://ubuntuforums.org/showpost.php?p=10868079&postcount=114)

Yeah, saw that after I posted.

All I can suggest is that you locate a fresh alt-status extension & see if that works for you.  Make sure you're using theme selector .09, not the old .08 version.  You also have a couple loading from both extension directories, but they aren't causing a real problem, just reporting an error and loading the first ones.

Sorry that's the best I can offer tonight.

---

### Post by maverick280857 on 2011-05-27
Thanks Charles. 

For now, I've found a fix: use the poweroptions extension which is available here: [http://ubuntuforums.org/showthread.php?t=1748167](http://ubuntuforums.org/showthread.php?t=1748167).

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> Thanks Charles. 

For now, I've found a fix: use the poweroptions extension which is available here: [http://ubuntuforums.org/showthread.php?t=1748167](http://ubuntuforums.org/showthread.php?t=1748167).

Now that is odd, that one won't work for me. :)

I spent quite some time trying to get it working and it fails every time, and I know it's good because fpmurphy coded it.  I guess there are still some mysteries to solve.

Hmm, I tried 2.0, I'll give 1.0 a shot.

---

### Post by maverick280857 on 2011-05-27
> **cbowman57 said:**
> Hmm, I tried 2.0, I'll give 1.0 a shot.

What's the difference between the two?

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> What's the difference between the two?

I have no idea, but neither one worked.

Do me a favor & download his eureka 2.1 extension & see if it runs for you.  For me everything works in it but the applications menu, and his stand alone applications menu doesn't work here either.

I was trying to help a guy get some extensions running on his Debian system, he tried everything in the gNatty Pack & all but two worked.  I'm just wondering if it's due to slight variations in the builds.

[Here's the link directly to his downloads]("http://www.fpmurphy.com/gnome-shell-extensions/")

---

### Post by maverick280857 on 2011-05-27
Eureka 2.1 works for me.

Check out [http://blog.fpmurphy.com/2011/05/more-gnome-shell-customization.html](http://blog.fpmurphy.com/2011/05/more-gnome-shell-customization.html). I haven't tried it myself, but it seems interesting.

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> Eureka 2.1 works for me.

Thanks, this is puzzling the hell out of me here. :(

I like that one, nice all-in-one solution, would eliminate at least 4 extensions that I'm using now.

If you edit it & replace the fedora-icon reference with file-manager it looks really nice too.

---

### Post by maverick280857 on 2011-05-27
> **cbowman57 said:**
> The login-window adopts the system's gtk3 theme.

I am not so sure of this. For me, it is the plain old gnome-shell login-screen which I got the first time I booted into gnome3, w/out any themes or extensions.

Are you seeing a different theme? Could that be due to the stuff in /usr/share/themes?

---

### Post by 23dornot23d on 2011-05-27
I just installed the Eureka 2.1  to see if it works ..... and it appears to do so  .....

[**Link to Screenshot**]("http://img41.imageshack.us/img41/2082/screenshot3tk.jpg") ..... the icons seem to have dropped too which is actually good for me
as I can now see them on my screen ..... 
( as the top 1/2 inch of my TV screen is always hidden from view )

Looking good now ..... at least I can use the panel if I need to now ...... ;)

keep up the great work  .....

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> I am not so sure of this. For me, it is the plain old gnome-shell login-screen which I got the first time I booted into gnome3, w/out any themes or extensions.

Well it uses the Adwaita gtk3 theme then.  I forgot I switched mine to the dark version. :)

---

### Post by maverick280857 on 2011-05-27
> **cbowman57 said:**
> If you edit it & replace the fedora-icon reference with file-manager it looks really nice too.

Can you post the details for this?

---

### Post by cbowman57 on 2011-05-27
> **23dornot23d said:**
> I just installed the Eureka 2.1  to see if it works ..... and it appears to do so  .....

[**Link to Screenshot**]("http://img41.imageshack.us/img41/2082/screenshot3tk.jpg") ..... the icons seem to have dropped too which is actually good for me
as I can now see them on my screen ..... 
( as the top 1/2 inch of my TV screen is always hidden from view )

Looking good now ..... at least I can use the panel if I need to now ...... ;)

keep up the great work  .....

Now I'm beginning to wonder what's broken on my system?

BTW, edit that extension.js & get rid of that big red X. :)

---

### Post by 23dornot23d on 2011-05-27
Which extension would it be .....

I never see the big red X as its usually hidden from view on my screen ....

But now I can see it will get rid ...... if only I knew which line to change ..... ?

The menu actually works though .... ;)

[IMG]http://img860.imageshack.us/img860/5901/screenshot5ff.jpg[/IMG]

---

### Post by cbowman57 on 2011-05-27
> **23dornot23d said:**
> Which extension would it be .....

I never see the big red X as its usually hidden from view on my screen ....

But now I can see it will get rid ...... if only I knew which line to change ..... ?

The menu actually works though .... ;)

[IMG]http://img860.imageshack.us/img860/5901/screenshot5ff.jpg[/IMG]

I believe it should also contain an applications menu, does that work also, or do you just get the Activities button.

Ok, for the both of you, in the extension.js there is a line right above start-here that references fedora-icon something or another.  Change that to simply file-manager , it should pick up the nautilus icon from your icon theme.  No .icon, nothing else, just file-manager (you can also browse your icons and select something else)

---

### Post by cbowman57 on 2011-05-27
> **maverick280857 said:**
> Eureka 2.1 works for me.

Check out [http://blog.fpmurphy.com/2011/05/more-gnome-shell-customization.html](http://blog.fpmurphy.com/2011/05/more-gnome-shell-customization.html). I haven't tried it myself, but it seems interesting.

Yes, he's a wizard, I've been reading his blog & trying to apply his examples for a month or so.

I gave Webupd8 the tip abut his theme@selector extension that actually kicked this journey into Gnome 3.0 for me. :)

---

### Post by 23dornot23d on 2011-05-27
Ok did it but its still a no Entry sign on mine ...... 
( although it did appear to change for a split second - will re-boot see if it changes ..... )

[IMG]http://img820.imageshack.us/img820/9594/screenshot9ox.jpg[/IMG]


I quite like the way the menu selections open up though ,,,, 

but no Applications menu !!

Do I need another extension installing for the Applications to appear ..... ?

Interesting ..... there must be tow pointers to this ..... as I have seen it change twice now and then
revert back to the red circle with the line across it .....

After re-booting and coming back in it took ages to bring the desktop up too ....... 
something is wrong with the way they load up ...... 

I found this out before when creating the  Dvd for the 64 bit version ..... it would fail to load Gnome-shell 
due to a problem in the panel extensions .....

But  .......   using the menu from cairo-dock is much quicker and everything is set up as standard too .....

[IMG]http://img857.imageshack.us/img857/4895/gnome4.jpg[/IMG]



If I just have the extensions relating to the themes in there as I showed earlier in a screenshot here it all works fine though though .....

Is there two places where these are being picked up from ..... and if so ..... 

Which is the correct one to use ?

[**Screenshot of active and Zipped extensions at the time**]("http://img689.imageshack.us/img689/9561/screenshot10bk.jpg") .... just to make sure all information is available
if anybody wants to work out why its slowing down on desktop entry .....

Will zip them up again and see if it changes the speed I get into my desktop as there is obviously something wrong.

It works very fast using only cairo-dock .......

No red Marker top left [**SCREENSHOT**]("http://img571.imageshack.us/img571/286/screenshot11kh.jpg")

---

### Post by cbowman57 on 2011-05-27
Just realized that the menu is all inclusive, Places, Bookmarks, then all the applications in their respective categories.

I just did an installation from scratch to see if it made a difference. :)  The process has changed a bit since gNatty was first released due to updates.

---

### Post by 23dornot23d on 2011-05-27
It all works and the applications are there .... but there is something still not quite right
with it ..... 

Maybe its just java that is slow .... but it does make quite some difference when going into the desktop with the panel extensions activated ..... 

I put everything I need onto Cairo-dock .... [COLOR=Red]**one click and I am running my application**[/COLOR] ...... [B][SCREENSHOT]("http://img96.imageshack.us/img96/876/screenshotro.jpg")

I have not found anything else as quick to use as Gnome-shell with Cairo-dock added ......
its set to autohide too .... so most of the time you do not even know its there .......

[COLOR=Blue]_*( This is my main system by the way .... and it swaps back and forth between Unity and Gnome-shell )*_[/COLOR]
[/B]
Will keep watching the development though .......

---

### Post by cbowman57 on 2011-05-27
> **23dornot23d said:**
> It all works and the applications are there .... but there is something still not quite right
with it ..... 

Maybe its just java that is slow .... but it does make quite some difference when going into the desktop with the panel extensions activated ..... 

I put everything I need onto Cairo-dock .... [COLOR=Red]**one click and I am running my application**[/COLOR] ...... [B][SCREENSHOT]("http://img96.imageshack.us/img96/876/screenshotro.jpg")

I have not found anything else as quick to use as Gnome-shell with Cairo-dock added ......
its set to autohide too .... so most of the time you do not even know its there .......
[/B]
Will keep watching the development though .......

You need to remove the wokspace & activities extensions, those are included with eureka.

This is what mine looks like now.

That's just with the app indicator, weather & eureka extensions

---

### Post by 23dornot23d on 2011-05-27
> **cbowman57 said:**
> You need to remove the wokspace & activities extensions, those are included with eureka.

This is what mine looks like now.

That's just with the app indicator, weather & eureka extensions

That's neat .... looks good .....

Here's mine when[ ***I swap into UNITY** *]("http://img713.imageshack.us/img713/5827/screenshotbd.jpg")..... same layout and it gives me the best use of both
desktops now ..... Conky works in both and remains active ..... also doing record my desktop
works between both .... and continues to do the recording while switching .....

But horses for courses ..... video and graphics manipulation are better in UNITY ....
where organisation and a cleaner look exist within Gnome-shell .......

I like them both and its good to see progress in both of them too .....

( Gnome-shell to me has very few problems other than additions made to it
and are now causing some problems ..... mainly to do with the version numbers 
but that really should not be happening ...... as version changes are bound to keep altering )

How we stop this is another matter though and its still in development - so it will be
good to see the finished working items ........

---

### Post by maverick280857 on 2011-05-27
> **cbowman57 said:**
> Well it uses the Adwaita gtk3 theme then.  I forgot I switched mine to the dark version. :)

How did you change the login-screen theme, even if it was to the dark version? I see the standard Adwaita log-in screen.

---

### Post by maverick280857 on 2011-05-29
Is there a fix for the weather extension now?

By the way, I am using wicd instead of network-manager for two reasons: (1) network-manager doesn't remember my static DNS IPs, and (2) the wireless doesn't work in console mode if I can't boot into the graphical mode for some reason, with network-manager.

Is there any extension for wicd, which would promote its status icons to appear on the top bar instead of the notifications area? I am not sure if some of my [other problems]("http://ubuntuforums.org/showthread.php?p=10875483#post10875483") are due to wicd.

---

### Post by artoonie on 2011-05-29
Is there any way to tweak away these problems?

Attachment 1: The weirdest error, fixable by alt+f2, r. But after that command, I get:
Attachment 2: Weird default icons, which fix on rollover. These fix if I use gnome-tweak-tool and switch away and back to the old icon theme. But:
Attachment 3: Happens all the time in certain places, like when there is only one suggestion in google.

---

### Post by Dobbie03 on 2011-05-29
For some reason adding the icon extension for the activities crashes my GS.

---

### Post by maverick280857 on 2011-05-29
> **artoonie said:**
> Is there any way to tweak away these problems?

Attachment 1: The weirdest error, fixable by alt+f2, r. But after that command, I get:
Attachment 2: Weird default icons, which fix on rollover. These fix if I use gnome-tweak-tool and switch away and back to the old icon theme. But:
Attachment 3: Happens all the time in certain places, like when there is only one suggestion in google.

Looks like a badly broken theme at first sight. Your display configuration could be messed up. Just reinstall everything if you can, and use the default configuration for some time.

EDIT: Can we restrict ourselves to 'tweaking' Gnome3 on this thread please :-)

---

### Post by artoonie on 2011-05-29
> **maverick280857 said:**
> EDIT: Can we restrict ourselves to 'tweaking' Gnome3 on this thread please :-)
Right; wasn't sure if I should start a new thread.

Tweaking related:
Is there any way to invert colors like Compiz did previously? Or perhaps a keyboard shortcut to switch back and forth from High Contrast Inverted theme?

---

### Post by cbowman57 on 2011-05-29
> **maverick280857 said:**
> Is there a fix for the weather extension now?

By the way, I am using wicd instead of network-manager for two reasons: (1) network-manager doesn't remember my static DNS IPs, and (2) the wireless doesn't work in console mode if I can't boot into the graphical mode for some reason, with network-manager.

Is there any extension for wicd, which would promote its status icons to appear on the top bar instead of the notifications area? I am not sure if some of my [other problems]("http://ubuntuforums.org/showthread.php?p=10875483#post10875483") are due to wicd.

Use the application indicator extension, at least that's what I call it here, just edit it and add wicd, should show up in your top panel.  Haven't tried it with wicd but seems like it should work.

---

### Post by cbowman57 on 2011-05-29
> **artoonie said:**
> Is there any way to tweak away these problems?

Attachment 1: The weirdest error, fixable by alt+f2, r. But after that command, I get:
Attachment 2: Weird default icons, which fix on rollover. These fix if I use gnome-tweak-tool and switch away and back to the old icon theme. But:
Attachment 3: Happens all the time in certain places, like when there is only one suggestion in google.

Have you tried changing video drivers?  Looks like there may be some kind of conflict.  What video card do you use?

---

### Post by cbowman57 on 2011-05-29
> **Dobbie03 said:**
> For some reason adding the icon extension for the activities crashes my GS.

What extensions are you running Dobbie?  My guess is that you have another one trying to grab the same location.  You may be better off using eureka 2.1

---

### Post by cbowman57 on 2011-05-29
> **artoonie said:**
> Right; wasn't sure if I should start a new thread.

Tweaking related:
Is there any way to invert colors like Compiz did previously? Or perhaps a keyboard shortcut to switch back and forth from High Contrast Inverted theme?

I would think you could do that from the accessabilty menu via the icon in the top panel.  If we could figure out what the command is you could create a launcher & add it to your favorites.  Then use the panel favorites extension to put it up on the top panel also.

---

### Post by maverick280857 on 2011-05-29
> **artoonie said:**
> Tweaking related:
Is there any way to invert colors like Compiz did previously? Or perhaps a keyboard shortcut to switch back and forth from High Contrast Inverted theme?

Good question. I couldn't find one, but the following links are worth checking:

[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)
[http://www.multimediaboom.com/gnome-3-keyboard-and-mouse-shortcuts/](http://www.multimediaboom.com/gnome-3-keyboard-and-mouse-shortcuts/)

Thinking out of the box, if we could isolate the event that is initiated when you click on the acceesibility->toggle high contrast theme button, we could probably write a script, or assign a keyboard shortcut to it.

---

### Post by maverick280857 on 2011-05-29
> **cbowman57 said:**
> Use the application indicator extension, at least that's what I call it here, just edit it and add wicd, should show up in your top panel.  Haven't tried it with wicd but seems like it should work.

What's the application indicator extension? How do I 'edit it and add wicd'?

Are you referring to [email]Applications_Menu@rmy.pobox.com[/email]? That's the one which adds a 'gNatty' menu. (Btw, is it possible to replace the text 'gNatty' with an icon, or add a Ubuntu icon next to it?).

---

### Post by cbowman57 on 2011-05-29
> **maverick280857 said:**
> What's the application indicator extension? How do I 'edit it and add wicd'?

Are you referring to [email]Applications_Menu@rmy.pobox.com[/email]? That's the one which adds a 'gNatty' menu. (Btw, is it possible to replace the text 'gNatty' with an icon, or add a Ubuntu icon next to it?).

Look for App@Indicator, came in gNatty Pack, or at least it's in the latest one.  For the application menu, open extension.js with a text editor and replace gNatty with whatever text you want.

Fpmurphy has a new extension now called eureka, it would replace that menu, and replaces both the activities icon & a menu icon.

---

### Post by maverick280857 on 2011-05-29
You remember how Network Manager used to have an indicator applet running on the top right of the screen? I'd like that for wicd. That is what I was referring to, when I asked you how I can add it.

> **cbowman57 said:**
> Look for App@Indicator, came in gNatty Pack, or at least it's in the latest one.

Is this the latest one?

[http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz?wa=wsignin1.0&sa=92561471](http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz?wa=wsignin1.0&sa=92561471)

I'm guessing not, because its dated May 10. Where do you host the latest version, as a general rule?

---

### Post by cbowman57 on 2011-05-29
> **maverick280857 said:**
> You remember how Network Manager used to have an indicator applet running on the top right of the screen? I'd like that for wicd. That is what I was referring to, when I asked you how I can add it.

Does it show up in the message tray at the bottom of the screen?  If it does it can be added to the app-indicator.  Been awhile since I used wicd, the applet display might be an option.  You'll have to test it out and see if it works for you.



> Is this the latest one?

[http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz?wa=wsignin1.0&sa=92561471](http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz?wa=wsignin1.0&sa=92561471)

I'm guessing not, because its dated May 10. Where do you host the latest version, as a general rule?

Yep, look at the modification date, lower right on the page.

I've decided that barring any significant changes I'm probably going to freeze the pack where it's at now.  People are better off getting their extensions from their respective sources.  I expect to see a website catering to extensions, sort of like the theme sites before too long.

---

### Post by maverick280857 on 2011-05-29
Thanks for your reply Charles..the App extension is pretty cool!

> **cbowman57 said:**
> Does it show up in the message tray at the bottom of the screen?  If it does it can be added to the app-indicator. Been awhile since I used wicd, the applet display might be an option.  You'll have to test it out and see if it works for you.

Okay this is my extension.js for App@Indicator now:

```

const Panel = imports.ui.panel;
const StatusIconDispatcher = imports.ui.statusIconDispatcher;

function main() {

    // add the notification(s) you want display on the top bar
    // - one per line. Use the english text string displayed when
    // hovering your mouse over the bottom right notification area

    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['gm-notify'] = 'gm-notify';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['transmission-gtk'] = 'transmission-gtk';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['empathy'] = 'empathy';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['gmusicbrowser'] = 'gmusicbrowser';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['pidgin'] = 'pidgin';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['dropbox'] = 'dropbox';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['indicator-weather'] = 'indicator-weather';
**    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['wicd-gtk'] = 'wicd-gtk';**
}
```

I have to figure out what is supposed to go into the last line. I figured it out for dropbox and the weather indicator applet by chance, but wicd is actually running through python. I see 'Connected to ...' as the string when I hover over wicd in the notifications tray.

---

### Post by cbowman57 on 2011-05-29
Look in system monitor, you may have to set it to view all processes, and see what wicd is running.

Check **wicd --help** from the command line too, you might have to run something as a startup application to get a display. (just a thought)

If it's showing up in the notifications tray then I'm 99.999% sure you can get it to display using that extension.

BTW, if you find that you'd like to take some of that panel space back there is a way to edit one of the shell files to remove your user name from being displayed.

---

### Post by maverick280857 on 2011-05-29
> **cbowman57 said:**
> Look in system monitor, you may have to set it to view all processes, and see what wicd is running.

Check **wicd --help** from the command line too, you might have to run something as a startup application to get a display. (just a thought)

If it's showing up in the notifications tray then I'm 99.999% sure you can get it to display using that extension.



wicd --help returns this

```

wicd 1.7.0 (bzr-r552) 
wireless (and wired) connection daemon.

Arguments:
	-a	--no-autoconnect	Don't auto-scan/auto-connect.
	-f	--no-daemon	Don't daemonize (run in foreground).
	-e	--no-stderr	Don't redirect stderr.
	-n	--no-poll	Don't monitor network status.
	-o	--no-stdout	Don't redirect stdout.
	-h	--help		Print this help.

```

gnome-system-monitor has 'wicd-client' running, and I tried to use this

```
StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['wicd-client'] = 'wicd-client';
```

but it does not work. Guess I have to keep trying. I have been able to get everything else (dropbox, skype, ktorrent, weather indicator, empathy) to show up.

---

### Post by cbowman57 on 2011-05-29
> **maverick280857 said:**
> but it does not work. Guess I have to keep trying. I have been able to get everything else (dropbox, skype, ktorrent, weather indicator, empathy) to show up.

Seems there are some limitations, I can't get it to display gm-notify either.  Guess we'll just have to keep exploring.

Wonder if it can be 'python wicd'?

---

### Post by artoonie on 2011-05-29
> **cbowman57 said:**
> Have you tried changing video drivers?  Looks  like there may be some kind of conflict.  What video card do you  use?
  ATI Radeon HD 6xxx, with ATI Catalyst Control Center..but i believe this is the wrong thread to discuss it.
 

 > **cbowman57 said:**
> I would think you could do that from the  accessabilty menu via the icon in the top panel.  If we could figure out  what the command is you could create a launcher & add it to your  favorites.  Then use the panel favorites extension to put it up on the  top panel also.
> **maverick280857 said:**
> Good question. I couldn't find one, but the following links are worth checking:

[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)
[http://www.multimediaboom.com/gnome-3-keyboard-and-mouse-shortcuts/](http://www.multimediaboom.com/gnome-3-keyboard-and-mouse-shortcuts/)

Thinking out of the box, if we could isolate the event that is initiated when you click on the acceesibility->toggle high contrast theme button, we could probably write a script, or assign a keyboard shortcut to it.
After following a few links on that first URL, I found:
[https://bugzilla.gnome.org/show_bug.cgi?id=639851](https://bugzilla.gnome.org/show_bug.cgi?id=639851)
So it looks like a work in progress. The High Contrast Inverse isn't perfect (Firefox white backgrounds are still white, etc) so I'll keep an eye out there for progress.
Thanks!

---

### Post by maverick280857 on 2011-05-29
Aah! Got it. It is 'wicd-client.py'. Wonderful!

For the record, my extension.js looks like this now

```

const Panel = imports.ui.panel;
const StatusIconDispatcher = imports.ui.statusIconDispatcher;

function main() {

    // add the notification(s) you want display on the top bar
    // - one per line. Use the english text string displayed when
    // hovering your mouse over the bottom right notification area

    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['gm-notify'] = 'gm-notify';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['transmission-gtk'] = 'transmission-gtk';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['empathy'] = 'empathy';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['gmusicbrowser'] = 'gmusicbrowser';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['pidgin'] = 'pidgin';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['dropbox'] = 'dropbox';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['indicator-weather'] = 'indicator-weather';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['skype'] = 'skype';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['ktorrent'] = 'ktorrent';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['vlc'] = 'vlc';
**    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['wicd-client.py'] = 'wicd-client.py';**
}

```

Thanks for your help Charles!

---

### Post by maverick280857 on 2011-05-29
> **artoonie said:**
> ATI Radeon HD 6xxx, with ATI Catalyst Control Center..but i believe this is the wrong thread to discuss it.

If it's a hardware issue you want to discuss, then perhaps yes.

But I really didn't mean to bump you off. Sorry if it seemed that way. Please feel free to use this thread to discuss any Gnome3 related tweaks or issues. And if you create a new thread which is related to the problems you outlined above (the hardware ones), do leave a link here so that the other posters on this thread can try to help you.

Unfortunately I have no experience with the Radeon, I have always used NVIDIA cards.

---

### Post by maverick280857 on 2011-05-29
There is a caveat to this App@Indicator thing which is worth mentioning. It seems that once Dropbox has been promoted to the top bar using this extension, the 'mouse hover' text does not appear anymore. So when I update my dropbox account, I do see an animation in the dropbox notification icon, but if I hover my mouse cursor over it, I don't see "Uploading files.." or anything for that matter, which I used to earlier.

But wicd does not suffer from this problem.

---

### Post by cbowman57 on 2011-05-29
@artoonie; link to thread in my signature, somebody there may be able to help.

---

### Post by cbowman57 on 2011-05-29
> **maverick280857 said:**
> Aah! Got it. It is 'wicd-client.py'. Wonderful!

Thanks for your help Charles!

Cool! You're more than welcome. :)

Just looked to see if gm-notify used the same or similar, no such luck.

I'm not sure if app@indicator is actually even in the wild.  I think I cut & pasted it from a fpmurphy's blog.

---

### Post by maverick280857 on 2011-05-29
> **cbowman57 said:**
> Cool! You're more than welcome. :)

Just looked to see if gm-notify used the same or similar, no such luck.

I'm not sure if app@indicator is actually even in the wild.  I think I cut & pasted it from a fpmurphy's blog.

What does gm-notify do?

By the way, here's a nicer weather-indicator

[http://www.webupd8.org/2011/02/my-weather-indicator-020-released-new.html](http://www.webupd8.org/2011/02/my-weather-indicator-020-released-new.html)

and the corresponding entry in extension.js would be 'my-weather-indicator'. I had to create a symbolic link to the py file in /usr/share. Not sure if it is required though.

---

### Post by cbowman57 on 2011-05-29
> **maverick280857 said:**
> What does gm-notify do?

By the way, here's a nicer weather-indicator

[http://www.webupd8.org/2011/02/my-weather-indicator-020-released-new.html](http://www.webupd8.org/2011/02/my-weather-indicator-020-released-new.html)

and the corresponding entry in extension.js would be 'my-weather-indicator'. I had to create a symbolic link to the py file in /usr/share. Not sure if it is required though.

gm-notify monitors gmail periodically and if there's mail it notifies you.

Never mind, thought that was the link to the weather extension. :)

---

### Post by maverick280857 on 2011-05-29
But I'm still not able to add thunderbird ('thunderbird-bin') :-(

---

### Post by maverick280857 on 2011-05-29
Okay I found a fix for the thunderbird issue.

1. Do the modifications in extension.js as mentioned above.

2. Install firetray, from [http://code.google.com/p/firetray/downloads/list](http://code.google.com/p/firetray/downloads/list). I installed firetray_0.2.8.xpi (Tools-->Addons-->Install... in Thunderbird).

---

### Post by maverick280857 on 2011-05-29
Have a look at the top bar (attached image) carefully though. In the background, do you see the word 'Loading' next to what looks like a window frame? I wonder why this is showing up. There is no window. Seems to be something broken with the theme. What do you think?

---

### Post by Dobbie03 on 2011-05-30
> **cbowman57 said:**
> What extensions are you running Dobbie?  My guess is that you have another one trying to grab the same location.  You may be better off using eureka 2.1

I tried eureka2.1, but it still crashed for me.  
The extensions I am running:
User Theme Extensions
Places Status Indicator 
Media Extension
Pidgin Integration
Removable Drive Menu
Applications Menu
Move Clock
Weather

Do you think some of these could be conflicting?

---

### Post by maverick280857 on 2011-05-30
> **maverick280857 said:**
> 
1. Change the Date and Time appearance to reflect "Friday May 06 13:32" rather than "Fri 13:32"?

Using

```
gsettings set org.gnome.shell.clock show-seconds true
```

(not as root!) one can get the clock to display seconds.

---

### Post by maverick280857 on 2011-05-30
> **Dobbie03 said:**
> I tried eureka2.1, but it still crashed for me.  
The extensions I am running:
User Theme Extensions
Places Status Indicator 
Media Extension
Pidgin Integration
Removable Drive Menu
Applications Menu
Move Clock
Weather

Do you think some of these could be conflicting?

Instead of using a weather extension, you can just use App@Indicator from the new gnatty pack, and configure it's extension.js file to include a line for indiciator-weather or my-weather-indicator. That way, you won't have an extension for each indicator, and the conflicts can get resolved.

---

### Post by cbowman57 on 2011-05-30
> **Dobbie03 said:**
> I tried eureka2.1, but it still crashed for me.  
The extensions I am running:
User Theme Extensions
Places Status Indicator 
Media Extension
Pidgin Integration
Removable Drive Menu
Applications Menu
Move Clock
Weather

Do you think some of these could be conflicting?

We were talking about the activities icon extension correct?  If so it's conflicting with the applications menu extension I think.

Eureka conflicts with the applications menu & possibly places extensions.  when you try new extensions the best advice I can give when there is a crash is to disable them and add them in one at a time to determine the conflict.  Then you can do something similar to what I did with the weather extension and relocate it to another "child" process.  I don't fully understand it, nor can I explain it.  Takes some research & trial and error at this point.  It's a little like trying to set up conky. :)

---

### Post by maverick280857 on 2011-05-31
Charles, there's a way people are customizing the GDM login screen in Arch and Fedora 15. Its documented here:

[http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/](http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/)

I believe it should be possible to adapt this to Natty, but it requires access to the 'gdm' user (**which I can't figure out in Natty**), and also to 'dconf-service', which in Natty is

```
/usr/lib/d-conf/dconf-service
```

Your thoughts on this?

---

### Post by cbowman57 on 2011-05-31
> **maverick280857 said:**
> Charles, there's a way people are customizing the GDM login screen in Arch and Fedora 15. Its documented here:

[http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/](http://ranjith.zfs.in/change-the-background-of-gnome-3-gdm-login-screen/)

I believe it should be possible to adapt this to Natty, but it requires access to the 'gdm' user (**which I can't figure out in Natty**), and also to 'dconf-service', which in Natty is

```
/usr/lib/d-conf/dconf-service
```

Your thoughts on this?

I believe I tried that & it wouldn't take.  I've forced a downgrade to gdm 2.32 and got my auto login back so I don't care so much about how the login looks anymore.

I'm guessing you already tried it?

---

### Post by maverick280857 on 2011-05-31
> **cbowman57 said:**
> I believe I tried that & it wouldn't take.  I've forced a downgrade to gdm 2.32 and got my auto login back so I don't care so much about how the login looks anymore.

I'm guessing you already tried it?

Does downgrading to gdm 2.32 affect gnome-shell/gnome3 at all?

How exactly do you downgrade?

Yes, I tried the stuff on that page. It seems to have been taken from an ArchLinux wiki. But the first step 'su -c gdm /bin/bash' didn't work for me, as I do not know the password for the user 'gdm'.

---

### Post by cbowman57 on 2011-05-31
> **maverick280857 said:**
> Does downgrading to gdm 2.32 affect gnome-shell/gnome3 at all?

How exactly do you downgrade?

Yes, I tried the stuff on that page. It seems to have been taken from an ArchLinux wiki. But the first step 'su -c gdm /bin/bash' didn't work for me, as I do not know the password for the user 'gdm'.

Nope, gnome-shell does just fine with the older gdm.  Select gdm in synaptic, then package, force version, select the previous version.  After that you can "lock" it to make sure it doesn't get overwritten by synaptic.

If you update with aptitude it's a simple matter of using sudo aptitude hold gdm.  Probably a way to do it with apt-get also but I haven't tried that yet.

---

### Post by maverick280857 on 2011-05-31
I'll check this out. Thanks for the screenshots and advice Charles!

---

### Post by cbowman57 on 2011-05-31
> **maverick280857 said:**
> I'll check this out. Thanks for the screenshots and advice Charles!

No problem, you should always do a quick backup first but if for some reason it locks you out of the desktop (though it shouldn't).

---

### Post by valnar on 2011-05-31
Here is an attack on Gnome 3 via Fedora 15.  I love it.  My same concerns are about Unity.  Different yes, but not better.

[http://www.zdnet.com/blog/open-source/fedora-15s-five-best-features/8968]("http://www.zdnet.com/blog/open-source/fedora-15s-five-best-features/8968")

---

### Post by maverick280857 on 2011-06-01
> **cbowman57 said:**
> No problem, you should always do a quick backup first but if for some reason it locks you out of the desktop (though it shouldn't).

Sorry for the dumb question (again), but a quick backup of what?

---

### Post by cbowman57 on 2011-06-01
> **valnar said:**
> Here is an attack on Gnome 3 via Fedora 15.  I love it.  My same concerns are about Unity.  Different yes, but not better.

[http://www.zdnet.com/blog/open-source/fedora-15s-five-best-features/8968]("http://www.zdnet.com/blog/open-source/fedora-15s-five-best-features/8968")

My favorite quote from that article, "Finally, GNOME makes it very hard indeed to tweak your desktop."  LOL!  

It's obvious that most people that are trying review or critique Gnome 3.0 haven't spent more than an hour or two using it, cursing the entire time and haven't even begun to see what is available for customization through the use of extensions.

fpmurphy just created an extension adding a hotspot to the upper right corner, among all the others he's created & he's just one java script coder.  The customization potential for gnome shell is almost limitless.

---

### Post by cbowman57 on 2011-06-01
> **maverick280857 said:**
> Sorry for the dumb question (again), but a quick backup of what?

I was always taught that the only dumb question is the one that isn't asked. :)

I backup my whole system, how you want to do it is up to you but I like clonezilla for backing up & restoring partitions.  Excluding your Downloads &/or other large folders a typical Ubuntu installation on my system takes up less than 4Gb.  A backup takes me about 5 minutes.

My Downloads, Music & Maintenance folders are actually mounted from their own dedicated partitions.  But that's a whole 'nother post. :)

---

### Post by maverick280857 on 2011-06-01
Okay this is interesting. Does Clonezilla create an exact clone of my drive, and restore it exactly as it was before the system crashed? This would include the MBR, Grub and Windows partitions?

If GDM does crash due to a downgrade, I suppose it should be possible to upgrade it 'back' to the original gnome3 version from the command line too right? So its probably better to downgrade it from the command line itself?

By the way, did you downgrade GDM just so you could customize it, or were there other technical reasons too?

---

### Post by maverick280857 on 2011-06-01
Okay I noticed there are a whole bunch of dependencies involved.

```

Package: gdm
Versions: 
3.0.2-0ubuntu1~build1 (/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_u
buntu_dists_natty_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_u
buntu_dists_natty_main_binary-amd64_Packages
                  MD5: 6c08dfbdac506777ff44a81cd07a6e34

2.32.1-0ubuntu3 (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_mai
n_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_nat
ty_main_binary-amd64_Packages
                  MD5: 6c08dfbdac506777ff44a81cd07a6e34


Reverse Depends: 
  plymouth,gdm 2.29.1-0ubuntu4
  gnome-session,gdm 2.29.92
  xubuntu-gdm-theme,gdm
  xubuntu-desktop,gdm
  xfswitch-plugin,gdm
  ubuntustudio-desktop,gdm
  ubuntu-sugar-remix,gdm
  ubuntu-mobile-default-settings,gdm
  ubuntu-chinese-desktop,gdm
  mythbuntu-default-settings,gdm
  gnome-desktop-environment,gdm 2.20.10
  gnome,gdm
  brdesktop-gnome,gdm
  mythbuntu-desktop,gdm
  ubuntu-desktop,gdm
  sabayon,gdm
  plymouth,gdm 2.29.1-0ubuntu4
  numlockx,gdm
  indicator-session,gdm 2.27.4-0ubuntu9
  indicator-session,gdm
  indicator-applet-session,gdm 2.27.90-0ubuntu1
  indicator-applet-session,gdm 2.27.90-0ubuntu1
  gnome-session,gdm 2.29.92
  gdm-guest-session,gdm 2.30.0-0ubuntu5
Dependencies: 
3.0.2-0ubuntu1~build1 - libaccountsservice0 (2 0.6.8) libatk1.0-0 (2 1.12.4) lib
attr1 (2 2.4.41-1) libc6 (2 2.4) libcairo-gobject2 (2 1.10.0) libcairo2 (2 1.10.
0) libcanberra-gtk3-0 (2 0.25) libcanberra0 (2 0.2) libdbus-1-3 (2 1.0.2) libdbu
s-glib-1-2 (2 0.88) libfontconfig1 (2 2.8.0) libfreetype6 (2 2.2.1) libgconf2-4 
(2 2.31.1) libgdk-pixbuf2.0-0 (2 2.22.0) libglib2.0-0 (2 2.27.4) libgtk-3-0 (2 3
.0.0) libpam0g (2 0.99.7.1) libpango1.0-0 (2 1.14.0) libpolkit-gobject-1-0 (2 0.
94) libselinux1 (2 1.32) libupower-glib1 (2 0.9.0) libx11-6 (0 (null)) libxau6 (
0 (null)) libxdmcp6 (0 (null)) libxklavier16 (2 5.1) libxrandr2 (2 2:1.2.99.3) d
ebconf (18 0.5) debconf-2.0 (0 (null)) gconf2 (2 2.28.1-2) upstart-job (0 (null)
) adduser (0 (null)) libpam-modules (2 0.72-1) libpam-runtime (2 0.76-13.1) gnom
e-session-bin (0 (null)) kbd (16 (null)) console-tools (0 (null)) udev (2 166-0u
buntu4) locales (0 (null)) uswsusp (0 (null)) libpam-gnome-keyring (0 (null)) gn
ome-power-manager (0 (null)) gnome-orca (0 (null)) gok (0 (null)) gnome-mag (0 (
null)) xserver-xorg (0 (null)) metacity (16 (null)) x-window-manager (0 (null)) 
gnome-settings-daemon (16 (null)) xfconf (0 (null)) fast-user-switch-applet (0 (
null)) gdm-snapshot (0 (null)) libxklavier15 (3 4.0-0ubuntu2) xsplash (3 0.8) us
plash (0 (null)) fast-user-switch-applet (0 (null)) gdm-snapshot (0 (null)) 
2.32.1-0ubuntu3 - libatk1.0-0 (2 1.12.4) libattr1 (2 2.4.41-1) libc6 (2 2.4) lib
cairo2 (2 1.2.4) libcanberra-gtk0 (2 0.4) libcanberra0 (2 0.2) libdbus-1-3 (2 1.
0.2) libdbus-glib-1-2 (2 0.88) libfontconfig1 (2 2.8.0) libfreetype6 (2 2.2.1) l
ibgconf2-4 (2 2.31.1) libgdk-pixbuf2.0-0 (2 2.22.0) libglib2.0-0 (2 2.24.0) libg
tk2.0-0 (2 2.23.90-0ubuntu4) libpam0g (2 0.99.7.1) libpango1.0-0 (2 1.14.0) libp
olkit-gobject-1-0 (2 0.94) libselinux1 (2 1.32) libupower-glib1 (2 0.9.0) libwra
p0 (2 7.6-4~) libx11-6 (0 (null)) libxau6 (0 (null)) libxdmcp6 (0 (null)) libxkl
avier16 (2 5.0) debconf (18 0.5) debconf-2.0 (0 (null)) gconf2 (2 2.28.1-2) upst
art-job (0 (null)) adduser (0 (null)) libpam-modules (2 0.72-1) libpam-runtime (
2 0.76-13.1) gnome-session-bin (0 (null)) kbd (16 (null)) console-tools (0 (null
)) udev (2 166-0ubuntu4) locales (0 (null)) uswsusp (0 (null)) libpam-gnome-keyr
ing (0 (null)) gnome-power-manager (0 (null)) gnome-orca (0 (null)) gok (0 (null
)) gnome-mag (0 (null)) xserver-xorg (0 (null)) metacity (16 (null)) x-window-ma
nager (0 (null)) gnome-settings-daemon (16 (null)) xfconf (0 (null)) fast-user-s
witch-applet (0 (null)) gdm-snapshot (0 (null)) libxklavier15 (3 4.0-0ubuntu2) x
splash (3 0.8) usplash (0 (null)) fast-user-switch-applet (0 (null)) gdm-snapsho
t (0 (null)) 
Provides: 
3.0.2-0ubuntu1~build1 - x-display-manager 
2.32.1-0ubuntu3 - x-display-manager 
Reverse Provides:

```

I guess I will just wait till I figure out a way to customize GDM3, rather than downgrading it.

---

### Post by cbowman57 on 2011-06-01
> **maverick280857 said:**
> Okay this is interesting. Does Clonezilla create an exact clone of my drive, and restore it exactly as it was before the system crashed? This would include the MBR, Grub and Windows partitions?

Yes it will but I prefer backing up by partition, you only need 1 HDD to do that & it's a lot quicker to backup & restore.

> If GDM does crash due to a downgrade, I suppose it should be possible to upgrade it 'back' to the original gnome3 version from the command line too right? So its probably better to downgrade it from the command line itself?

I'd recommend downgrading with synaptic, if it crashes then all you need to do is sudo apt-get upgrade and 3.0 will be reinstalled.

> By the way, did you downgrade GDM just so you could customize it, or were there other technical reasons too?

No, though I may customize it at some point I wanted auto login, don't really care what it looks like if I don't see it on login. 

For technical reasons I think it's less prone to failure for my custom live iso.  It works correctly, gdm 3.0 doesn't.

---

### Post by bmbaker on 2011-06-01
> **cbowman57 said:**
> I believe I tried that & it wouldn't take.  I've forced a downgrade to gdm 2.32 and got my auto login back so I don't care so much about how the login looks anymore.

I'm guessing you already tried it?
Doesn't the auto-login stop you from choosing unity or gnome-shell ?

---

### Post by cbowman57 on 2011-06-01
> **bmbaker said:**
> Doesn't the auto-login stop you from choosing unity or gnome-shell ?

I removed unity, don't use it, don't like, don't miss it. :)

You get logged into your last used session, so yes, it requires me to logout, then select something else (I still have gnome fallback).  The older gdm is what the system settings in ubuntu can manipulate.

I decided a few days ago that keeping unity on my system was just a waste of space, sudo apt-get purge unity*

The only DE I use is gnome shell, wouldn't go back to anything else.

---

### Post by maverick280857 on 2011-06-01
Charles, I have a fresh problem. Every time I reboot my computer and log into the GNOME Shell, I get an error saying 'Something bad happened', forcing me to log out (the only option left). When I log back in, Gnome Shell works just fine. I haven't installed any new extensions, or updated anything. 

Do you know what the source of this problem could be?

---

### Post by cbowman57 on 2011-06-01
> **maverick280857 said:**
> Charles, I have a fresh problem. Every time I reboot my computer and log into the GNOME Shell, I get an error saying 'Something bad happened', forcing me to log out (the only option left). When I log back in, Gnome Shell works just fine. I haven't installed any new extensions, or updated anything. 

Do you know what the source of this problem could be?

I'd disable all the extensions with gnome-tweak-tool, then turn them back on one at a time to isolate the problem.  It's likely related to an extension but it's hard telling.

---

### Post by bmbaker on 2011-06-01
> **cbowman57 said:**
> I removed unity, don't use it, don't like, don't miss it. :)

You get logged into your last used session, so yes, it requires me to logout, then select something else (I still have gnome fallback).  The older gdm is what the system settings in ubuntu can manipulate.

I decided a few days ago that keeping unity on my system was just a waste of space, sudo apt-get purge unity*

The only DE I use is gnome shell, wouldn't go back to anything else.
ya i don't like or use unity but i kept this time around for  updating purposes.
though i did remove the ubuntu desktop, maybe i remove unity too!

---

### Post by bmbaker on 2011-06-01
> **cbowman57 said:**
> I'd disable all the extensions with gnome-tweak-tool, then turn them back on one at a time to isolate the problem.  It's likely related to an extension but it's hard telling.
I was having the same problem so i checked in lookinglass and it was showing it was the xrandir extension. i removed it rebooted 3 times plus a few times logging out and it seems to have fixed it :-)

---

### Post by cbowman57 on 2011-06-01
> **bmbaker said:**
> I was having the same problem so i checked in lookinglass and it was showing it was the xrandir extension. i removed it rebooted 3 times plus a few times logging out and it seems to have fixed it :-)

Good catch, I don't use that extension. Was it the one from git, fpmurphy, or the one from the ppa?

---

### Post by maverick280857 on 2011-06-02
> **cbowman57 said:**
> I'd disable all the extensions with gnome-tweak-tool, then turn them back on one at a time to isolate the problem.  It's likely related to an extension but it's hard telling.

I tried that. Looking glass shows no errors now, and yet every time I log in for the first time after rebooting my system, I get that error, forcing me to log out. But when I log back in again, it works fine.

---

### Post by maverick280857 on 2011-06-02
Okay, this is what happens.

I reboot my computer, and try to log in. I get an error message saying something has gone wrong and Gnome Shell cannot load. The dialog box has a log out button (the only thing I can click). When I log out and log back in, everything seems to work just fine.

I have tried disabling ALL extensions, and even with no extensions, I get the same error.

---

### Post by 23dornot23d on 2011-06-02
Tweaking the login screen - by creating your own image/jpg
at the correct size - replace the stipes .jpg

usr/share/themes/Adwaita/backgrounds/stripes.jpg

with your own 

I found the best way to do this was to start Gimp 

gksudo gimp

pull a picture into it .... and then write it out to the directory above with stripes.jpg
as a filename ..... its not the best way of solving this problem - but it does work.


_*[COLOR=Red]**[LINK]("http://img821.imageshack.us/img821/9061/screenshot6rs.png") ....**[/COLOR]*_ is this the one to change .... ? Yes ......

Change this picture and it changes the login screen ..... background.

usr/share/themes/Adwaita/backgrounds/stripes.jpg 
( make sure you get the size correct mine was 1920 x1200  yours may be different )


>   Next can this be animated ..... or use a GIF file ?
and where does it [COLOR=Red]**[get called up from]("http://www.google.com/search?client=ubuntu&channel=fs&q=usr%2Fshare%2Fthemes%2FAdwaita%2Fbackgrounds%2Fstripes.jpg&ie=utf-8&oe=utf-8") ?**[/COLOR]

---

### Post by maverick280857 on 2011-06-02
> **23dornot23d said:**
> Tweaking the login screen - by creating your own image/jpg
at the correct size - replace the stipes .jpg


I went a step further, and tweaked the theme. As discussed in a previous thread and on the Arch wiki, gdm is apparently a 'user' and if you can figure out how to log into it's own account, you can configure themes much the same way as we do for ourselves.

Meanwhile, since Adwaita is the default theme, you can do the following to replace it.

```
sudo mv /usr/share/themes/Adwaita /usr/share/themes/Adwaita.old
```

Now, you can copy one of the existing themes, say MintLiner, into a new folder which we will call Adwaita

```
sudo mkdir /usr/share/themes/Adwaita
sudo cp -r /usr/share/themes/MintLiner/* /usr/share/themes/Adwaita/
```

But if you look closely, the background file 'stripes.jpg' is contained in Adwaita/backgrounds, whereas MintLiner doesn't have a 'backgrounds' folder. So let's create it

```
sudo mkdir /usr/share/themes/Adwaita/backgrounds
```

Now, copy an image of appropriate resolution into /usr/share/themes/Adwaita/backgrounds/ and remember to name it 'stripes.jpg' (the only filename that seems to work). Next, reboot the system, or log out, to see the new GDM.

Attached is a screenshot of how it looks on my system. I had to tone down the quality to upload the image.

---

### Post by maverick280857 on 2011-06-02
> **maverick280857 said:**
> Okay, this is what happens.

I reboot my computer, and try to log in. I get an error message saying something has gone wrong and Gnome Shell cannot load. The dialog box has a log out button (the only thing I can click). When I log out and log back in, everything seems to work just fine.

I have tried disabling ALL extensions, and even with no extensions, I get the same error.

Here is the screenshot.

I still haven't been able to fix this problem. It is clearly **not** due to any extensions.

---

### Post by 23dornot23d on 2011-06-02
I am also getting this too ..... its the most uninformative error message I have ever seen.

and the thing is when you look behind it the rest of the process's are running normally

I would like to know exactly what triggers this and what it relates to ......

For the past few days now I have been seeing more and more of it .... and it was never appearing before.
as I do not need the extensions they are rarely activated on my set up ...... so something else may be 
causing it to keep appearing - not sure which log files it will be in though ?.

My solution was to remove all the extensions ..... including the ones that are now in the 
ricotz ppa .....

Will check the log files later to see if I can pinpoint why it happens .... in the past its been 
a bad extension ...... but now its very difficult to tell what is causing it to happen. :confused:

---

### Post by bmbaker on 2011-06-02
> **cbowman57 said:**
> Good catch, I don't use that extension. Was it the one from git, fpmurphy, or the one from the ppa?
that one was from the ppa :-)
i just did a reboot as normally i put my laptop into sleep mode, but when i rebooted this morning the error message was back !

unrelated perhaps but has anyone been getting any kernel panics?
i was doing a backup of my music to another hard drive and it crashed after about 30gigs !!!
not once but 3x !!!

---

### Post by 23dornot23d on 2011-06-02
Looked through all my log files nothing stands out as a big problem .....

I have not tried to copy 30 Gig of Data yet but may try it later .....

But normally things like Distros 2 Gig in size have been moved around ok .....

This version I am in now is fully up to date as of today using aptitude Safe-upgrade

The only apparent problems are the odd program does not run ......

But I put that down to me removing Mono and also removing Ubuntuone ..... as
something was causing a real lag when exiting the desktop .....

After I removed these that lag i no longer there anymore ..... no sad face either ....

---

### Post by maverick280857 on 2011-06-03
I'm still getting that error message on logging on. I'm wondering why there's no message when I log in the second time. Where are the X session logs, and don't they store information about the most recent successful login? Technically, to view them, we'd have to log out on that error message, and switch to console mode and save them elsewhere before we log back in (and they're overwritten).

Which log files would contain information about Gnome login errors?

---

### Post by maverick280857 on 2011-06-03
Here is my .xsession-errors

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-FvNjGt
GNOME_KEYRING_CONTROL=/tmp/keyring-FvNjGt
SSH_AUTH_SOCK=/tmp/keyring-FvNjGt/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-FvNjGt
SSH_AUTH_SOCK=/tmp/keyring-FvNjGt/ssh
GPG_AGENT_INFO=/tmp/keyring-FvNjGt/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-FvNjGt
SSH_AUTH_SOCK=/tmp/keyring-FvNjGt/ssh
GPG_AGENT_INFO=/tmp/keyring-FvNjGt/gpg:0:1

** (gnome-settings-daemon:3227): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:3227): common-plugin-WARNING **: Key 0xff6a (keycodes:  146)  with state 0x0 (resolved to 0x0)  has no usable modifiers (usable modifiers are 0x140000ed)

(canberra-gtk-play:3276): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(canberra-gtk-play:3276): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(canberra-gtk-play:3276): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(canberra-gtk-play:3276): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(canberra-gtk-play:3276): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(xdg-user-dirs-gtk-update:3280): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(xdg-user-dirs-gtk-update:3280): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(xdg-user-dirs-gtk-update:3280): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(xdg-user-dirs-gtk-update:3280): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(xdg-user-dirs-gtk-update:3280): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(vino-server:3278): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
gnome-session[3170]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/share/my-weather-indicator/my-weather-indicator.py" (No such file or directory)
To link this computer to a dropbox account, visit the following url:
https://www.dropbox.com/cli_link?host_id=e56f1aa930c0c6230315a3b8f2055d60&cl=en_US

(ClearWeatherScreenlet.py:3275): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ClearWeatherScreenlet.py:3275): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ClearWeatherScreenlet.py:3275): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ClearWeatherScreenlet.py:3275): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ClearWeatherScreenlet.py:3275): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(wicd-client.py:3281): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(wicd-client.py:3281): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(wicd-client.py:3281): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(wicd-client.py:3281): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(wicd-client.py:3281): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(screenlets-daemon.py:3295): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(screenlets-daemon.py:3295): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(screenlets-daemon.py:3295): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(screenlets-daemon.py:3295): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(screenlets-daemon.py:3295): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(cairo-dock:3303): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(cairo-dock:3303): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(cairo-dock:3303): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(cairo-dock:3303): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(cairo-dock:3303): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",
`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)


 ============================================================================ 
	Cairo-Dock version: 2.3.0~1
	Compiled date:  Apr 20 2011 20:54:28
	Running with OpenGL: 1
 ============================================================================

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

CachingBackend: Loading instances from cache
CachingBackend: Loading <ClearWeather1>
scale='1.5'
theme_name='default'
ZIP='INXX0067'
is_sticky='True'
is_widget='True'
keep_above='False'
lock_position='True'
is_dragged='False'
keep_below='False'
y='28'
x='1705'
skip_taskbar='True'
Initializing nautilus-gdu extension
daemon already started
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167) [0m 
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
03/06/2011 12:42:38 PM Autoprobing TCP port in (all) network interface
03/06/2011 12:42:38 PM Listening IPv6://[::]:5900
03/06/2011 12:42:38 PM Listening IPv4://0.0.0.0:5900
03/06/2011 12:42:38 PM Autoprobing selected port 5900
03/06/2011 12:42:38 PM Advertising security type: 'TLS' (18)
03/06/2011 12:42:38 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
03/06/2011 12:42:38 PM Listening IPv6://[::]:5900
03/06/2011 12:42:38 PM Listening IPv4://0.0.0.0:5900
03/06/2011 12:42:38 PM Clearing securityTypes
03/06/2011 12:42:38 PM Advertising security type: 'TLS' (18)
03/06/2011 12:42:38 PM Clearing securityTypes
03/06/2011 12:42:38 PM Advertising security type: 'TLS' (18)
03/06/2011 12:42:38 PM Advertising authentication type: 'No Authentication' (1)
03/06/2011 12:42:38 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
03/06/2011 12:42:38 PM Listening IPv6://[::]:5900
03/06/2011 12:42:38 PM Listening IPv4://0.0.0.0:5900
03/06/2011 12:42:38 PM Clearing securityTypes
03/06/2011 12:42:38 PM Clearing authTypes
03/06/2011 12:42:38 PM Advertising security type: 'TLS' (18)
03/06/2011 12:42:38 PM Advertising authentication type: 'No Authentication' (1)
03/06/2011 12:42:38 PM Advertising security type: 'No Authentication' (1)
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~1/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:699) [0m 
  while listing user packages in '/home/vivek/.config/cairo-dock/third-party' : Error opening directory '/home/vivek/.config/cairo-dock/third-party': No such file or directory
Found a running session of ClearWeather, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.ClearWeather was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.vivek.running
Loading instances in: /home/vivek/.config/Screenlets/ClearWeather/default/
Loaded config from: ClearWeather1.ini
Theme set to: 'default'
theme.conf found! Loading option-overrides.
Loaded theme config from: /usr/share/screenlets/ClearWeather/themes/default/theme.conf
	Name: Stardock weather icons
	Author: Stardock Corporation
	Version: 1.0
	Info: These weather images are (c) 2003 by Stardock Corporation.  All rights reserved.
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Set options in ClearWeatherScreenlet
Theme set to: 'default'
theme.conf found! Loading option-overrides.
Loaded theme config from: /usr/share/screenlets/ClearWeather/themes/default/theme.conf
	Name: Stardock weather icons
	Author: Stardock Corporation
	Version: 1.0
	Info: These weather images are (c) 2003 by Stardock Corporation.  All rights reserved.
Screenlet has been initialized.
Restored instances from session 'default' ...
    JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old

** (ClearWeatherScreenlet.py:2944): WARNING **: Failed to send buffer

** (ClearWeatherScreenlet.py:2944): WARNING **: Failed to send buffer
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
    JS ERROR: !!!   WARNING: 'assignment to undeclared variable file'
    JS ERROR: !!!   WARNING: file '/home/vivek/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gnome.org/extension.js' line 29 exception 0 number 156
      JS LOG: GNOME Shell started at Fri Jun 03 2011 12:42:42 GMT+0530 (IST)

** (gnome-screensaver:3408): WARNING **: screensaver already running in this session

** (nautilus:3294): WARNING **: Can not determine workarea, guessing at layout
`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3294): Gtk-WARNING **: Failed to load type module: (null)

Window manager warning: Got a request to focus 0x2400029 (switcher) with a timestamp of 0.  This shouldn't happen!
`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-terminal: undefined symbol: menu_proxy_module_load

(gnome-terminal:3425): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~1/src/gldit/cairo-dock-packages.c:cairo_dock_get_url_data_with_post:327) [0m 
  an error occured while downloading 'http://download.tuxfamily.org/glxdock/themes/third-party/2.3.0/list.conf' : Timeout was reached
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~1/src/gldit/cairo-dock-packages.c:cairo_dock_list_net_packages:646) [0m 
  empty packages list on http://download.tuxfamily.org/glxdock/themes (check that your connection is alive, or retry later)
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~1/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:710) [0m 
  while listing distant packages in 'http://download.tuxfamily.org/glxdock/themes/third-party/2.3.0' : empty packages list on http://download.tuxfamily.org/glxdock/themes
ClearWeatherScreenlet.py: Fatal IO error 0 (Success) on X server :0.

(applet.py:3503): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(applet.py:3503): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(applet.py:3503): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(applet.py:3503): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(applet.py:3503): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ubuntuone-launch:3505): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ubuntuone-launch:3505): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ubuntuone-launch:3505): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ubuntuone-launch:3505): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(ubuntuone-launch:3505): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(firefox-trunk-bin:3538): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(firefox-trunk-bin:3538): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(firefox-trunk-bin:3538): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(firefox-trunk-bin:3538): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(firefox-trunk-bin:3538): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",
error: An exception occurred.
Traceback (most recent call last):
  File "/home/vivek/.mozilla/firefox-trunk/ks6qfd6z.default/extensions/jid0-GXjLLfbCoAx0LcltEdFrEkQdQPI@jetpack/resources/jid0-gxjllfbcoax0lcltedfrekqdqpi-as-ff-data/js/content.js", line 1, in 
TypeError: document.getElementById("exit") is null
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(update-notifier:3613): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(update-notifier:3613): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(update-notifier:3613): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(update-notifier:3613): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(update-notifier:3613): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(gnome-shell:3268): Clutter-CRITICAL **: clutter_actor_queue_relayout: assertion `CLUTTER_IS_ACTOR (self)' failed

(gnome-shell:3268): Clutter-CRITICAL **: clutter_actor_queue_relayout: assertion `CLUTTER_IS_ACTOR (self)' failed

(gnome-shell:3268): Clutter-CRITICAL **: clutter_actor_queue_relayout: assertion `CLUTTER_IS_ACTOR (self)' failed
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x38000c4 (Ubuntu Sta)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:3279): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:3279): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events
`menu_proxy_module_load': gnome-power-manager: undefined symbol: menu_proxy_module_load

(gnome-power-manager:3218): Gtk-WARNING **: Failed to load type module: (null)


(gnome-power-manager:3218): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:3279): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
```

All I can gather from this is that the clearweather screenlet I use requires nm-applet (network-manager) which I don't have, since I use wicd. But this is a minor error, and I don't think it should cause the shell to crash?

---

### Post by maverick280857 on 2011-06-03
I don't know if this fixes it, but I found a file named nm-applet.desktop in ~/.config/autostart/, which I removed. I did not get an error on the next login attempt, but since it is so random, I don't know if this is a permanent fix.

I have cairo-dock running on startup, and it loads up as a black bar. The actual dock shows up when I hover my mouse over it. This is something that has recently happened. I wonder if the cairo dock errors in .xsession-errors are related to this?

---

### Post by maverick280857 on 2011-06-03
I am still getting the error. Here is the latest .xsession-errors. I can't get hold of /var/lib/gdm. Any other log files which could shed light into the problem?

EDIT: Also, it takes a LONG time (about a minute) to load GNOME3, with or without extensions. How do I speed it up? My guess is that the error I get on first time bootup is due to some application which fails to load, and the reason I am able to log in a second time is that the error condition from the previous session prevents that application from loading.

---

### Post by ontwowheels on 2011-06-03
> **maverick280857 said:**
> I tried that. Looking glass shows no errors now, and yet every time I log in for the first time after rebooting my system, I get that error, forcing me to log out. But when I log back in again, it works fine.

off topic, but what is looking glass?

---

### Post by maverick280857 on 2011-06-04
> **ontwowheels said:**
> off topic, but what is looking glass?

[INDENT]"Looking Glass is GNOME Shell's integrated debugger and inspector tool."[/INDENT]

[https://live.gnome.org/GnomeShell/LookingGlass](https://live.gnome.org/GnomeShell/LookingGlass)

---

### Post by ontwowheels on 2011-06-04
> **maverick280857 said:**
> [INDENT]"Looking Glass is GNOME Shell's integrated debugger and inspector tool."[/INDENT]

[https://live.gnome.org/GnomeShell/LookingGlass](https://live.gnome.org/GnomeShell/LookingGlass)

Awesome, THANKS

---

### Post by bmbaker on 2011-06-04
> **maverick280857 said:**
> I am still getting the error. Here is the latest .xsession-errors. I can't get hold of /var/lib/gdm. Any other log files which could shed light into the problem?

EDIT: Also, it takes a LONG time (about a minute) to load GNOME3, with or without extensions. How do I speed it up? My guess is that the error I get on first time bootup is due to some application which fails to load, and the reason I am able to log in a second time is that the error condition from the previous session prevents that application from loading.
i too have noticed that gnome-shell is taking longer to load now, i timed it and it took 46 seconds, I just installed Oneiric on my old samsung (which is 7 years old) then i installed gnome-shell etc had to do this from [http://ubuntuforums.org/showthread.php?t=1775049](http://ubuntuforums.org/showthread.php?t=1775049) to get it to work it kept crahing. then i added ricotz testing ppa i also manually installed the latest GDM and gnome-tweak from the gnome3 ppa and did a full upgrade and believe it or not it booted faster than my IBM dual cpu laptop! i was a bit surprised.
it might be the new kernel as well as the work being done to intergrate the shell with ubuntu, but i am looking forward the next full release :-)

---

### Post by maverick280857 on 2011-06-04
That is surprising..I don't think the choice of the ppa is responsible for the slow bootup. Btw, I use the gnome3 team ppa -- [http://ubuntuforums.org/showpost.php?p=10734567&postcount=1](http://ubuntuforums.org/showpost.php?p=10734567&postcount=1).

What could be the reasons for the slow loading of the gnome shell? Interestingly, if I log out and log back in, it loads faster.

---

### Post by bmbaker on 2011-06-04
> **maverick280857 said:**
> That is surprising..I don't think the choice of the ppa is responsible for the slow bootup. Btw, I use the gnome3 team ppa -- [http://ubuntuforums.org/showpost.php?p=10734567&postcount=1](http://ubuntuforums.org/showpost.php?p=10734567&postcount=1).

What could be the reasons for the slow loading of the gnome shell? Interestingly, if I log out and log back in, it loads faster.
i persnally think that its the extensions, i do a test with them all disabled and let you know :-)
i also see its faster when logging out and then back in.
but from a cold boot its slow!!

---

### Post by cbowman57 on 2011-06-04
You guys might want to try installing preload & see if that helps speed up the loading.

When you logout & log back in gnome-shell is already in memory so it's faster.

---

### Post by bmbaker on 2011-06-04
> **cbowman57 said:**
> You guys might want to try installing preload & see if that helps speed up the loading.

When you logout & log back in gnome-shell is already in memory so it's faster.
hmmm what is preload?
sounds interesting ;-)
i just disabled all my extensions and i did a cold reboot 3 times and it was between 20 to 25 seconds faster!!

---

### Post by cbowman57 on 2011-06-04
> **bmbaker said:**
> hmmm what is preload?
sounds interesting ;-)
i just disabled all my extensions and i did a cold reboot 3 times and it was between 20 to 25 seconds faster!!

preload is a Free Linux program written by Behdad Esfahbod which runs as a daemon and records statistics about usage of programs using Markov chains; files of more frequently-used programs are, during a computer's spare time, loaded into memory.[1] This results in faster application startup times as less data needs to be fetched from disk. preload is often paired with prelink.

[Wikipedia link]("http://en.wikipedia.org/wiki/Preload_(software)")

Also look at you extensions with Looking Glass and eliminate any errors, if there are any.

---

### Post by bmbaker on 2011-06-04
ok so i installed preload and will see how it works :-)
thanks for the tip :-)

---

### Post by maverick280857 on 2011-06-04
> **cbowman57 said:**
> Also look at you extensions with Looking Glass and eliminate any errors, if there are any.

I have a whole bunch of 'missing theme.json' messages for all my shell themes.

---

### Post by bmbaker on 2011-06-04
> **maverick280857 said:**
> I have a whole bunch of 'missing theme.json' messages for all my shell themes.
you could check the version and make sure its just 3.0
and check the permissions see screenshot :-)

---

### Post by bmbaker on 2011-06-04
> **cbowman57 said:**
> preload is a Free Linux program written by Behdad Esfahbod which runs as a daemon and records statistics about usage of programs using Markov chains; files of more frequently-used programs are, during a computer's spare time, loaded into memory.[1] This results in faster application startup times as less data needs to be fetched from disk. preload is often paired with prelink.

[Wikipedia link]("http://en.wikipedia.org/wiki/Preload_%28software%29")

Also look at you extensions with Looking Glass and eliminate any errors, if there are any.
ya i had and still have no errors via LG.
but there is a measurable diff in boot time with the extension disabled, which is normal i guess.
i always try to have a delay for programs loading at boot, i will try and figure out if there is a way to put a delay on the start times for different extension.
the weather extension is a good example it is still trying to load so i always have to restart the shell !!

---

### Post by cbowman57 on 2011-06-05
> **maverick280857 said:**
> I have a whole bunch of 'missing theme.json' messages for all my shell themes.

Those shouldn't be anything to be concerned about, those are probably just metacity themes.

---

### Post by cbowman57 on 2011-06-05
> **bmbaker said:**
> ya i had and still have no errors via LG.
but there is a measurable diff in boot time with the extension disabled, which is normal i guess.
i always try to have a delay for programs loading at boot, i will try and figure out if there is a way to put a delay on the start times for different extension.
the weather extension is a good example it is still trying to load so i always have to restart the shell !!

Over on the Gentoo forums somebody suggested this be added to your /etc/environment file, claims it speeds up gnome shell.  I'm trying it know, not sure if it sped up but it doesn't seem to hurt anything.

```
export CLUTTER_VBLANK=none
```

---

### Post by maverick280857 on 2011-06-05
> **cbowman57 said:**
> Over on the Gentoo forums somebody suggested this be added to your /etc/environment file, claims it speeds up gnome shell.  I'm trying it know, not sure if it sped up but it doesn't seem to hurt anything.

```
export CLUTTER_VBLANK=none
```

I think you're referring to [http://forums.gentoo.org/viewtopic-t-871887-start-0.html](http://forums.gentoo.org/viewtopic-t-871887-start-0.html). I will try this in a bit, and post the outcome. But is this for a generally slow shell (which I don't have), or just the slow bootup (which we seem to)?

---

### Post by maverick280857 on 2011-06-05
The addition of 

```
'export CLUTTER_VBLANK=none'
```

to /etc/environment (followed by a reboot) did not speed up the loading of the gnome shell. I am not sure if it has sped up anything else though (if it is supposed to).

Preload may have had a very minor difference, but I am not too sure.

By the way, does your Plymouth splash screen work with proprietary NVIDIA drivers?

---

### Post by cbowman57 on 2011-06-05
> **maverick280857 said:**
> The addition of 

```
'export CLUTTER_VBLANK=none'
```

to /etc/environment (followed by a reboot) did not speed up the loading of the gnome shell. I am not sure if it has sped up anything else though (if it is supposed to).

Preload may have had a very minor difference, but I am not too sure.

By the way, does your Plymouth splash screen work with proprietary NVIDIA drivers?

Plymouth only display on shutdown, not on boot, if that's what you mean.  Preload is subtle, but if you had a very slow login it should have sped it up, if not you can always remove it.

---

### Post by maverick280857 on 2011-06-05
> **cbowman57 said:**
> Plymouth only display on shutdown, not on boot, if that's what you mean.

Are you sure? [http://www.freedesktop.org/wiki/Software/Plymouth](http://www.freedesktop.org/wiki/Software/Plymouth) 

I am referring to the splash screen that used to show up during bootup, before the NVIDIA splash screen.

---

### Post by cbowman57 on 2011-06-05
> **maverick280857 said:**
> Are you sure? [http://www.freedesktop.org/wiki/Software/Plymouth](http://www.freedesktop.org/wiki/Software/Plymouth) 

I am referring to the splash screen that used to show up during bootup, before the NVIDIA splash screen.

Clarify your question.  Are you asking how mine works or how it is supposed to work?

---

### Post by maverick280857 on 2011-06-05
As far as I know, Plymouth runs primarily at bootup. It may also run as the splash screen during shutdown or reboot, though this never worked for me (I always see the verbose text mode on my laptop). [http://en.wikipedia.org/wiki/Plymouth_%28software%29](http://en.wikipedia.org/wiki/Plymouth_%28software%29)

After one full day of no GNOME shell login errors, I am getting them again. 

By the way, I figured out a way to prevent multiple instances of the rotating wallpaper script from starting. I've edited the original post: [http://ubuntuforums.org/showpost.php?p=10858322&postcount=8](http://ubuntuforums.org/showpost.php?p=10858322&postcount=8).

---

### Post by bmbaker on 2011-06-05
has anyone tried without the weather extension?
i find that for some reason it doesn't start properly and so i reload the shell again!

---

### Post by maverick280857 on 2011-06-05
> **bmbaker said:**
> has anyone tried without the weather extension?
i find that for some reason it doesn't start properly and so i reload the shell again!

I don't use the weather extension.

---

### Post by Mad-Halfling on 2011-06-08
Hi folks, any found that having (or reinstalling) gnome-shell-extensions-alternative-status-menu no longer seems to make the "Power Off" menu option appear in the system menu?

---

### Post by ontwowheels on 2011-06-08
> **Mad-Halfling said:**
> Hi folks, any found that having (or reinstalling) gnome-shell-extensions-alternative-status-menu no longer seems to make the "Power Off" menu option appear in the system menu?

Running gnome3 gnome-shell on Ubuntu 11.04, are we able to load the extensions?  Like the theme selector extension?  I had looked before and couldn't find it.

---

### Post by bmbaker on 2011-06-08
> **ontwowheels said:**
> Running gnome3 gnome-shell on Ubuntu 11.04, are we able to load the extensions?  Like the theme selector extension?  I had looked before and couldn't find it.
these two links are great :-)
[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)
[http://www.webupd8.org/search/label/gnome%20shell?max-results=10](http://www.webupd8.org/search/label/gnome%20shell?max-results=10)

---

### Post by maverick280857 on 2011-06-08
> **Mad-Halfling said:**
> Hi folks, any found that having (or reinstalling) gnome-shell-extensions-alternative-status-menu no longer seems to make the "Power Off" menu option appear in the system menu?

alternative-status-menu does not work for me.

Get the poweroptions extension from [http://fpmurphy.com/gnome-shell-extensions](http://fpmurphy.com/gnome-shell-extensions), and extract it in ~/.local/share/gnome-shell/extensions.

---

### Post by ontwowheels on 2011-06-08
> **bmbaker said:**
> these two links are great :-)
[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)
[http://www.webupd8.org/search/label/gnome%20shell?max-results=10](http://www.webupd8.org/search/label/gnome%20shell?max-results=10)

Thanks, I'll check them out!!  :)

---

### Post by Mad-Halfling on 2011-06-08
> **maverick280857 said:**
> alternative-status-menu does not work for me.

Get the poweroptions extension from [http://fpmurphy.com/gnome-shell-extensions](http://fpmurphy.com/gnome-shell-extensions), and extract it in ~/.local/share/gnome-shell/extensions.

It certainly used to work for me (on 11.04) - I'm 95% sure that was what I used, and it was installed on my system.  However since the patch about 2 or 3 days ago it doesn't seem to.  It's bloody annoying as I can't shut down using just the mouse, now.

---

### Post by bmbaker on 2011-06-08
> **Mad-Halfling said:**
> It certainly used to work for me (on 11.04) - I'm 95% sure that was what I used, and it was installed on my system.  However since the patch about 2 or 3 days ago it doesn't seem to.  It's bloody annoying as I can't shut down using just the mouse, now.
can you post a screen shot with looking glass open and can you check the permissions on the alt status and that the version number is 3.0 and lastly check that its active in gnome-tweak :-)

---

### Post by maverick280857 on 2011-06-09
Is anyone else still getting errors in Gnome3 when logging in the first time? The error goes away when you click on log out and log back in. It's a first time error only, and I don't think its because of the extensions.

Somehow I don't think ~/.xsession-errors will point us to the clue. Which are the other relevant logs?

---

### Post by maverick280857 on 2011-06-10
Attached are two versions of .xsession-errors, corresponding to the failed and successful login sessions.

I may have found a few errors:

```

JS ERROR: !!!   Exception was: Error: Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = '("Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/status/network.js:8
'
    JS ERROR: !!!     message = 'Requiring NetworkManager, version none: Typelib file for namespace 'NetworkManager' (any version) not found'
      JS LOG: NMApplet is not supported. It is possible that your NetworkManager version is too old

```

I don't use Network Manager, and use wicd instead. Could this be one problem? This error doesn't show up in the .xsession-errors for the successful login session.

---

### Post by maverick280857 on 2011-06-10
Not facing the issue since a Sun Java update a few hours ago...

---

### Post by maverick280857 on 2011-06-12
And the error is back :-(

Keith, are you getting it too?

---

### Post by h313 on 2011-06-13
I installed gnome3 on my natty a couple of hours before.
Going through some tutorials, it became clear that it would replace unity.
After a successful installation of gnome3 using the following commands :

> 
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell


On reboot, however i was unable to log in to ubuntu with gnome 3.
It displayed an error message **"Something went wrong"** and forced log out.
I have the following options in my GDM login screed :
[LIST]
[*]gnome
[*]gnome classic  
[*]gnome classic(no effects)
[*]ubuntu
[/LIST]
The Gnome session displays the error as explained above.
The Ubuntu has a gnome UI with fewer applications than before
And a gnome2.3 in ubuntu classic.

I cant find out the reason why i am not able get gnome 3 working.
I think it may be a graphics issue, but i am not sure.
My configuration is :
Core i3
4GB Ram
1GB ati mobility HD 5470

---

### Post by maverick280857 on 2011-06-13
> **h313 said:**
> On reboot, however i was unable to log in to ubuntu with gnome 3.
It displayed an error message **"Something went wrong"** and forced log out.


You need to install gnome-session. Please follow the steps given in the first post of this thread: [http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343) (which is also a better place to discuss Gnome3 install issues).

---

### Post by h313 on 2011-06-13
Sailed through!!
thanks a lot for your help.
Got it working by removing my graphics fglrx drivers for ati

---

### Post by maverick280857 on 2011-06-16
This might help for the 'something has gone wrong' error:

[http://ubuntuforums.org/showpost.php?p=10767963&postcount=2](http://ubuntuforums.org/showpost.php?p=10767963&postcount=2)

---

### Post by maverick280857 on 2011-06-17
Is anyone experiencing frequent flicker in the Gnome Shell these days?

---

### Post by bmbaker on 2011-06-17
> **maverick280857 said:**
> Is anyone experiencing frequent flicker in the Gnome Shell these days?
ya i was but the latest updates from testing seems to have cleared it up !

---

### Post by 23dornot23d on 2011-06-17
I found that there was a flicker on the theme that looks like the old windows theme.

But on the other ones its not there .... ( no idea why though ..... )

---

### Post by h313 on 2011-06-17
so far, my experience with gnome 3 is very good.
Although a problem which i face is, when i open any new application when i have some other windows open, the new application doesn't show up on the top.
i mean, when i start VLC for instance,the video starts playing in the background. Thus, i have to manually bring the window to front. how can i get over this.
Every new window which starts, is not automatically brought to the front.

---

### Post by maverick280857 on 2011-06-17
> **bmbaker said:**
> ya i was but the latest updates from testing seems to have cleared it up !

Do you have an NVIDIA graphics card?

Also, which updates from testing did you apply?

Btw, using the App@Indicator extension, I get notifications of wicd, dropbox, etc on the top bar. Of late, I've noticed that all icons are wicd icons. Have you also seen similar symptoms?

---

### Post by ontwowheels on 2011-06-19
> **23dornot23d said:**
> Tweaking the login screen - by creating your own image/jpg
at the correct size - replace the stipes .jpg

usr/share/themes/Adwaita/backgrounds/stripes.jpg

with your own 

I found the best way to do this was to start Gimp 

gksudo gimp

pull a picture into it .... and then write it out to the directory above with stripes.jpg
as a filename ..... its not the best way of solving this problem - but it does work.


_*[COLOR=Red]**[LINK]("http://img821.imageshack.us/img821/9061/screenshot6rs.png") ....**[/COLOR]*_ is this the one to change .... ? Yes ......

Change this picture and it changes the login screen ..... background.

usr/share/themes/Adwaita/backgrounds/stripes.jpg 
( make sure you get the size correct mine was 1920 x1200  yours may be different )

I had done this and it worked, switching the stripes.jpg, but after a recent update it does not work.  I noticed that after the update stripes.jpg was replaced, so I replaced it again with my custom stripes.jpg.  But, I still get the blue stripes....anyone know why?

Thanks

---

### Post by maverick280857 on 2011-06-19
I have a peculiar problem with the laptop volume control keys.

When I increase the volume using the increase volume key, the indicator shows maximum volume. When I reduce, it displays the mute icon. The keys work to increase and decrease the volume, but the on-screen indications in Gnome 3 are messed up.

Any ideas what could be wrong here?

Also, I see wicd icons for all the programs in the notification area on top (I am using the App@Indicator extension).

---

### Post by maverick280857 on 2011-06-19
This is what my notification bar looks like.

Strange, isn't it? They're all wicd icons. Any ideas how I can fix this?

---

### Post by maverick280857 on 2011-06-21
> **maverick280857 said:**
> This is what my notification bar looks like.

Strange, isn't it? They're all wicd icons. Any ideas how I can fix this?

I still have the flicker, and the messed up icons. I am contemplating backing up my data, and reinstalling Natty and Gnome3. Any ideas on what could be wrong, so I could fix it before resorting to the brute force solution?

---

### Post by bmbaker on 2011-06-23
> **maverick280857 said:**
> I still have the flicker, and the messed up icons. I am contemplating backing up my data, and reinstalling Natty and Gnome3. Any ideas on what could be wrong, so I could fix it before resorting to the brute force solution?
have you tried changing the icon theme using gnome-tweak?
or check the permissions of the icon theme.

---

### Post by maverick280857 on 2011-06-23
> **bmbaker said:**
> have you tried changing the icon theme using gnome-tweak?
or check the permissions of the icon theme.

I have tried changing the icon theme. It is now ubuntu-mono-dark (the default icon theme). But the wicd icon is used for wicd, dropbox and anything I start manually (vlc, ktorrent, whatever).

I am also experiencing a lot of screen flicker. I am using the latest NVIDIA drivers.

---

### Post by maverick280857 on 2011-06-27
Now I have a fresh problem. I just turned on my laptop, and it seems neither the taskbar (the top bar in the Gnome Shell), nor the title bar of any window show up.

Any ideas what could be wrong here? It seems some updates have damaged the gnome shell. I wanted to take a backup of my system before reinstalling Ubuntu, but now I don't know if I can.

---

### Post by LarsKongo on 2011-06-28
Same problem here. Updated today and can't login properly. I only see my wallpaper and mouse-cursor. :/ (Running it in VirtualBox.) Install openbox or any other minimal WM to access your files in a GUI.

---

### Post by maverick280857 on 2011-07-01
Have reinstalled Natty. 

Btw, I am not going to use wicd from now on, unless I have a strong reason. My main problem with Network Manager was that it reset my static DNS settings. I found a fix for that:

1. Edit your /etc/resolv.conf (as superuser) and make necessary modifications.

2. Type

```
sudo chattr +i /etc/resolv.conf
```

This will prevent resolv.conf from being modified by networkmanager. To test this, just click on the network manager icon and reconnect. Then check if resolv.conf has been overwritten.

---

### Post by vitorsouza on 2011-07-02
> **maverick280857 said:**
> This might help for the 'something has gone wrong' error:

[http://ubuntuforums.org/showpost.php?p=10767963&postcount=2](http://ubuntuforums.org/showpost.php?p=10767963&postcount=2)

It seems to have solved it for me! Thanks!

---

### Post by bmbaker on 2011-07-02
> **maverick280857 said:**
> Now I have a fresh problem. I just turned on my laptop, and it seems neither the taskbar (the top bar in the Gnome Shell), nor the title bar of any window show up.

Any ideas what could be wrong here? It seems some updates have damaged the gnome shell. I wanted to take a backup of my system before reinstalling Ubuntu, but now I don't know if I can.

it seems to be a problem if you have the  **xorg-edgers ppa** enabled

[http://ubuntuforums.org/showthread.php?t=1793998&page=2](http://ubuntuforums.org/showthread.php?t=1793998&page=2)

---

### Post by maverick280857 on 2011-07-04
I don't have that ppa, bmbaker. 

I reinstalled Natty 64-bit on my laptop a few days ago, and I have the latest NVIDIA drivers. A few hours into it, I started encountering frequent screen flicker. I 'fixed' it by installing Flash 64 using this link

[http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/](http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/)

and unchecking 'dim screen' in the power settings (apparently updates to gnome-power-manager will restore default settings).

Now, I have Gnome Shell, but I have not yet installed gnatty pack or ANY extensions. So I am using the pristine Gnome Shell with Network Manager instead of wicd. 

And guess what, the notification bar (which appears on the bottom right of your screen when you hover your mouse there) displays the Network Manager (wireless) icon for all applications like VLC, Skype, etc.

So, the problem I was facing with regard to icons not showing up correctly in the taskbar on the top right (when using the App@Indicator extension) still persists, in spite of a clean reinstallation. Only now, it is 'demoted' to the notification bar, which is less bothersome. So, you have to use Alt+Tab to switch applications, and cannot rely on the icons which look the same for all programs.

It looks like a Gnome Shell/Gnome 3 bug.

---

