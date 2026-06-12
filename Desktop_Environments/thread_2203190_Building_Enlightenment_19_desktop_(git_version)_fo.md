---
title: "Building Enlightenment 19 desktop (git version) for fun"
date: 2014-02-02
forum: Desktop Environments
---

### Post by batden on 2014-02-02
[I][COLOR=#ff0000]ARCHIVES...

[/COLOR]New thread here:[COLOR=#ff0000][/COLOR]
[http://ubuntuforums.org/showthread.php?t=2274982](http://ubuntuforums.org/showthread.php?t=2274982)[/I]

Install script:
dazibao.perso.sfr.fr/Scripts/build-e19.sh

Uninstall script:
dazibao.perso.sfr.fr/Scripts/cleaner.sh

Enjoy!

**EDIT: SEE BELOW**

---

### Post by batden on 2014-02-10
All-in-one (install/update or uninstall) script for compiling E19 on Ubuntu 14.04 LTS:

[http://dazibao.perso.sfr.fr/Scripts/nineteen.sh](http://dazibao.perso.sfr.fr/Scripts/nineteen.sh)

**Latest version** of the script:** April 22**, 2014.

---

### Post by mr-stevenperez on 2014-04-25
I am using ubuntu 14.04 LTS and this script fails to install.  Tried this twice already. Error message is as follows:

In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from /usr/local/include/emotion-1/Emotion.h:94,
                 from elc_player.c:5:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from ./Elementary.h:72,
                 from elc_fileselector.c:12:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from ./Elementary.h:72,
                 from elc_ctxpopup.c:5:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from ./Elementary.h:72,
                 from elc_hoversel.c:5:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from ./Elementary.h:72,
                 from elc_fileselector_button.c:5:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from ./Elementary.h:72,
                 from elc_fileselector_entry.c:6:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from ./Elementary.h:72,
                 from elc_multibuttonentry.c:5:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
In file included from /usr/local/include/evas-1/Evas.h:293:0,
                 from ./Elementary.h:72,
                 from elc_naviframe.c:5:
/usr/local/include/evas-1/Evas_Eo.h:213:38: fatal error: canvas/evas_3d_camera.eo.h: No such file or directory
 #include "canvas/evas_3d_camera.eo.h"
                                      ^
compilation terminated.
make[4]: *** [libelementary_la-elc_player.lo] Error 1
make[4]: *** Waiting for unfinished jobs....
make[4]: *** [libelementary_la-elc_naviframe.lo] Error 1
make[4]: *** [libelementary_la-elc_hoversel.lo] Error 1
make[4]: *** [libelementary_la-elc_multibuttonentry.lo] Error 1
make[4]: *** [libelementary_la-elc_ctxpopup.lo] Error 1
make[4]: *** [libelementary_la-elc_fileselector.lo] Error 1
make[4]: *** [libelementary_la-elc_fileselector_button.lo] Error 1
make[4]: *** [libelementary_la-elc_fileselector_entry.lo] Error 1
make[4]: Leaving directory `/home/steven/Enlightenment19/elementary/src/lib'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/steven/Enlightenment19/elementary/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steven/Enlightenment19/elementary/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steven/Enlightenment19/elementary'
make: *** [all] Error 2



Any ideas how to fix this?

---

### Post by batden on 2014-04-26
Thanks for reporting.

This issue is now fixed in git:
[https://git.enlightenment.org/core/efl.git/commit/](https://git.enlightenment.org/core/efl.git/commit/)
("Evas_3d: fix some typo in .eo")

Please run the script again and select option #2 (update).

If you still have trouble, uninstall E19 programs first (choice #3) then reinstall Enlightenment (choice #1).

(Just updated my E19 installation and everything builds fine.)

_EDIT_
Screenshot of my desktop:
[https://www.enlightenment.org/ss/e-535d29397bc8c7.63688520.jpg](https://www.enlightenment.org/ss/e-535d29397bc8c7.63688520.jpg)

---

### Post by bryanhundven on 2014-04-30
batden,

I have created a gist that has updates to let it work on Debian as well.

[https://gist.github.com/bhundven/11439386](https://gist.github.com/bhundven/11439386)

You can git clone it here: [https://gist.github.com/11439386.git](https://gist.github.com/11439386.git)

I created the gist with your original script from: [http://dazibao.perso.sfr.fr/Scripts/nineteen.sh](http://dazibao.perso.sfr.fr/Scripts/nineteen.sh) - 22-Apr-2014 09:01     16K

I plan on doing a few more updates, but I'll add commit messages from now on. the original few commits just add some more comments to the top, get CODE to parse for 'LANG=' instead of LANGUAGE (not commonly used on Debian), and allow Debian Sid and Wheezy.

Cheers!

Debian Sid, E19 screenshot:
[ATTACH=CONFIG]252683[/ATTACH][ATTACH=CONFIG]252691[/ATTACH]

---

### Post by batden on 2014-05-03
_Bash script_

*Download*...

[FONT=Verdana][SIZE=2][COLOR=black][FONT=Verdana][SIZE=2][COLOR=black]GnuPG-signed[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] script for **Ubuntu 14.04.2 LTS** (save file):
[http://dazibao.perso.sfr.fr/Scripts/nineteen.sh.gpg](http://dazibao.perso.sfr.fr/Scripts/nineteen.sh.gpg)
[COLOR=#008000][Latest version: April 22, 2015][/COLOR]

*Access...*

Open Terminal, change (cd) to the download folder,
copy and paste the following command to access the file:
gpg --output nineteen.sh --decrypt nineteen.sh.gpg

*Use...*

1. In Terminal (Edit > Profile Preferences > Scrolling > set Scrollback to Unlimited)
2. Make the script executable with  chmod +x ./nineteen.sh
3. Run it with   ./nineteen.sh

_Screenshots_

[http://dazibao.perso.sfr.fr/Pictures/lightdm-e19-icon.png](http://dazibao.perso.sfr.fr/Pictures/lightdm-e19-icon.png)
[https://www.enlightenment.org/ss/e-55337d21b6bab5.08762407.jpg](https://www.enlightenment.org/ss/e-55337d21b6bab5.08762407.jpg)
[http://dazibao.perso.sfr.fr/Pictures/xephyr-debug.png](http://dazibao.perso.sfr.fr/Pictures/xephyr-debug.png)
[http://dazibao.perso.sfr.fr/Pictures/batden-pubkey.png](http://dazibao.perso.sfr.fr/Pictures/batden-pubkey.png)

---

### Post by notjimcarrey on 2014-05-21
Getting this on the latest script:
```

  CCLD     elm_prefs_cc
test_weather.c:7:29: fatal error: EWeather_Smart.h: No such file or directory
 # include "EWeather_Smart.h"
                             ^
compilation terminated.
/usr/bin/ld: cannot find -leweather
collect2: error: ld returned 1 exit status
Makefile:826: recipe for target 'elementary_codegen' failed
make[3]: *** [elementary_codegen] Error 1
make[3]: *** Waiting for unfinished jobs....
/usr/bin/ld: cannot find -leweather
collect2: error: ld returned 1 exit status
Makefile:830: recipe for target 'elementary_config' failed
make[3]: *** [elementary_config] Error 1
/usr/bin/ld: cannot find -leweather
collect2: error: ld returned 1 exit status
Makefile:834: recipe for target 'elementary_quicklaunch' failed
make[3]: *** [elementary_quicklaunch] Error 1
Makefile:2289: recipe for target 'elementary_test-test_weather.o' failed
make[3]: *** [elementary_test-test_weather.o] Error 1
make[3]: Leaving directory '/home/notjimcarrey/Enlightenment19/elementary/src/bin'
Makefile:442: recipe for target 'all-recursive' failed
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/notjimcarrey/Enlightenment19/elementary/src'
Makefile:617: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/notjimcarrey/Enlightenment19/elementary'
Makefile:498: recipe for target 'all' failed
make: *** [all] Error 2


 BUILD ERROR&#8212;TRY AGAIN LATER. 

```

---

### Post by batden on 2014-05-22
Libeweather it's not actively developed and typically not needed.
If you do want to enable this&#8212;unsupported&#8212;option then you need to build libeweather before elementary.

Get it here:
[https://git.enlightenment.org/libs/libeweather.git/](https://git.enlightenment.org/libs/libeweather.git/)

You're on your own.

---

### Post by notjimcarrey on 2014-05-22
How do I tell the script not to use it?

Edit: It was very trivial to get libeweather built, but still curious how to make the build ignore it.

---

### Post by batden on 2014-05-22
List of all available options:

0pen Terminal
cd /path/to/enlightened/program/folder
Then enter
./configure --help | less

> still curious how to make the build ignore it...

You would add "--disable-eweather" to every configure line ("$GEN" in the script) concerning elementary.

**EDIT:**

The presence of optional libraries is generally auto-detected during the configuration phase.
If you need to explicitly disable eweather support then it means that another version of this lib is already installed on your system...
Where does it come from?

---

### Post by notjimcarrey on 2014-05-23
It may be leftover from a prior build; thought I got it all.

---

### Post by batden on 2014-06-01
Hi enlightened ubunteros,

Check out this neat theme for E19:
[http://e17-stuff.org/content/show.php/Radiance...+with+a+Lot+of+Colors?content=165101](http://e17-stuff.org/content/show.php/Radiance...+with+a+Lot+of+Colors?content=165101)

Screenshot:
[https://www.enlightenment.org/ss/e-538b291f082ad2.16050296.jpg](https://www.enlightenment.org/ss/e-538b291f082ad2.16050296.jpg)

---

### Post by headen2 on 2014-06-01
Hello batden,

Thank you for this script !
But it cannot continue to compile after the dowloaded programs, because the problem appears during the build and the command 'make' return 2. 
See the following message :  
/* All programs have been downloaded successfully. 
Build internationalization support in Enlightenment? [Y/n] y
DIRECTORY : /home/voxit/Enlightenment19/efl
/home/voxit/Enlightenment19/efl
Building efl... 
./autogen.sh: 6: ./autogen.sh: autoreconf: not found
./autogen.sh: 31: exec: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
*/
Thank you in advance for your support.

---

### Post by batden on 2014-06-01
Corrupted download?

Make sure you have the latest version of the script (dated 2014-06-02 in changelog).
Execute the script and select option #3 (uninstall E19 programs). Then reinstall Enlightenment 19 (option #1).

EDIT:

If you still have trouble please post the complete output, like this:
[http://paste.ubuntu.com/7570878/](http://paste.ubuntu.com/7570878/)

---

### Post by headen2 on 2014-06-02
The problem is solved !
uninstall (#3)
reinstall (#1)
That's all folks !

---

### Post by theller on 2014-06-25
I saw "That's all folks." Restarted, chose enlightenment and get a black screen? I am using Ubuntu 14.04 and gnome3. When I log into a unity session laptop slowly goes crazy with the graphics. Gnome works fine.

I did try changing the greeter from gdm to lightdm. I don't think it worked because I got the same Gnome looking login screen. 

Any ideas?

---

### Post by batden on 2014-06-26
This sounds like a graphics driver issue. What is your graphics card?

And there is no need to switch to lightdm, gdm should work fine with E19.

---

### Post by theller on 2014-06-26
Radeon HD 8210

I do remember having trouble loading Ubuntu. I got a black screen with blinking cursor. Solved that problem with Niki Pixels help: [https://www.youtube.com/watch?v=OTmZYzaxR_k](https://www.youtube.com/watch?v=OTmZYzaxR_k)

---

### Post by batden on 2014-06-26
Sorry, but the Ati Radeon cards are not well supported in Enlightenment...

[http://sourceforge.net/p/enlightenment/mailman/message/31739017/](http://sourceforge.net/p/enlightenment/mailman/message/31739017/)

---

### Post by theller on 2014-06-26
Bummer. Gnome is lighter then Unity but I wanted something even lighter. The processor in this netbook is an AMD dual core, A4-1250 (1.0 GHz) so it's not to speedy.  

Thanks!

---

### Post by breakolami2 on 2014-08-31
Hello/salut **pourunmondesansgourou**

Je suis sous / I am under **Kubuntu 14.04**

I try to install E19 with your script but I get an error - J'essaye d'installer E19 avec ton script mais j'obtiens une erreur

I install GIT and WMCTRL - lors de mes prédédents essais j'ai vu qu'il fallait installer GIT et WMCTRL
I launch the nineteen script - je lance le script
Everything is downloaded - les téléchargements se passent bien

and I get this error - j'obtiens cette erreur

> All programs have been downloaded successfully. 


Build internationalization support in Enlightenment? [Y/n] n

Building efl... 

./autogen.sh: 6: ./autogen.sh: autoreconf: not found
cmp: config.cache-env: Aucun fichier ou dossier de ce type
Cleaning configure cache...
./autogen.sh: 31: exec: ./configure: not found

make: *** Pas de cible spécifiée et aucun makefile n'a été trouvé. Arrêt.

 BUILD ERROR—TRY AGAIN LATER. 


J'ai essayé 3 fois sans succès - I try 3 times without success

Thanks

---

### Post by batden on 2014-08-31
Hi breakolami2,

See post #15 (uninstall then reinstall).

---

### Post by breakolami2 on 2014-08-31
> **batden said:**
> See post #15 (uninstall then reinstall).
Yes I already tried but same error

---

### Post by batden on 2014-09-01
Make sure there are no leftovers from previous installations: cruft from Enlightenment deb packages or tarballs, unwanted hidden files in your home directory...

Run the script again and choose option #3.

If you still get the same error, please go to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and post the link to the entire output.

---

### Post by batden on 2014-09-12
OT...

Sad news for Enlightenment users:

[http://jeffhoogland.blogspot.fr/2014/09/stepping-down-from-bodhi-linux-lead.html](http://jeffhoogland.blogspot.fr/2014/09/stepping-down-from-bodhi-linux-lead.html)

---

### Post by phanhan on 2014-09-15
That is the problem that I'm interested.
I saw "That's all folks." Restarted, chose enlightenment and get a black screen? I am using Ubuntu 14.04 and gnome3. When I log into a unity session laptop slowly goes crazy with the graphics. Gnome works fine.


I did try changing the greeter from gdm to lightdm. I don't think it worked because I got the same Gnome looking login screen. 


Any ideas?

Ads: Technewonline is a website that specializes in introducing the latest technologies such as [Best Tablet Android Have Price Under $200](http://www.technewonline.com/2014/06/best-tablet-android-have-price-under-200-usd.html) and [Best tablet of Apple in 2014](http://www.technewonline.com/2014/04/best-tablet-of-apple-in-2014.html) and [Best phone In The World](http://www.technewonline.com/2014/03/best-phone-in-the-world.html) and [Best cell phone on the market](http://www.technewonline.com/2014/03/best-cell-phone-on-the-market.html) and [The Best Phones 4G Valued At Under 300 USD](http://www.technewonline.com/2014/07/list-of-best-4g-phones-valued-at-under-300-usd.html) is also a website for sharing your tips about computers, mobile phones and tablets, products are available from leading supermarkets will surely satisfy you.

---

### Post by batden on 2014-09-16
Another Ati driver problem?

Try this workaround:

&#8211; delete your ~/.e folder then logout and select "Enlightenment" in gdm or lightdm
&#8211; in Setup wizard, disable OpenGL when you reach the compositing page

---

### Post by Thiago Camargo on 2014-09-25
Hey guys!


This nineteen.sh script is very cool!    :-)


I did a fork of it, just for fun, to install E19 from stable tarballs, to try to use it in the months ahead, in a daily basis on my PC (i.e., not so frequent updates / "more stable")... Check it out!


nineteen-2.sh:
[https://gist.github.com/tmartinx/86adc8f33b12f163028b](https://gist.github.com/tmartinx/86adc8f33b12f163028b)


BTW, I'm also using the following E19 PPA: [https://launchpad.net/~niko2040/+archive/ubuntu/e19?field.series_filter=trusty](https://launchpad.net/~niko2040/+archive/ubuntu/e19?field.series_filter=trusty) - Also made up from the same tarball sources above!


Lets revive `apt-get install elbuntu-desktop` ?!   :-D


Cheers!

---

### Post by batden on 2014-10-08
Japan theme update:
[http://forums.bodhilinux.com/index.php?/topic/11188-e19-themes/page__pid__86176#entry86176](http://forums.bodhilinux.com/index.php?/topic/11188-e19-themes/page__pid__86176#entry86176)

Direct download:
[https://drive.google.com/file/d/0B_VgEo2Znv0_SXMycEVxd0Zwb1E/view?pli=1](https://drive.google.com/file/d/0B_VgEo2Znv0_SXMycEVxd0Zwb1E/view?pli=1)

---

### Post by batden on 2014-12-21
My script is now distributed as a digitally signed file.

Get it here (save file):
[http://dazibao.perso.sfr.fr/Scripts/nineteen.sh.gpg](http://dazibao.perso.sfr.fr/Scripts/nineteen.sh.gpg)

Then,
open Terminal
cd to the Downloads folder, copy and paste the following command:

gpg --output nineteen.sh --decrypt nineteen.sh.gpg

[Optional] My Public Key info:
[http://dazibao.perso.sfr.fr/Pictures/batden-pubkey.png](http://dazibao.perso.sfr.fr/Pictures/batden-pubkey.png)

---

### Post by titiou on 2015-04-02
Can you update your script for utopic? and add eflete, erigo, and enventor? 
Thank you for your script it's work very good on ubuntu 14.04.
best regard

---

### Post by batden on 2015-04-03
Sorry titiou but I don't plan to upgrade my main system to utopic unicorn, or add support for non-core applications.

[B]I've installed the upcoming Ubuntu release on a test machine though and you'll find a new version of my script for vivid vervet (with systemd support) on this page:
[http://dazibao.perso.sfr.fr/HTML/scriptings.html](http://dazibao.perso.sfr.fr/HTML/scriptings.html)
[/B](download nineteenviv.sh.gpg)

Eflete, erigo and enventor are developer tools with uncommon build requirements and infrequent updates. if you do need them, you'll have to install these programs manually.
More details here:
[https://git.enlightenment.org/](https://git.enlightenment.org/)

---

### Post by kelt65 on 2015-04-05
ah, memories. Has anyone dug up that theme that made the desktop switchers like like old televisions? The screen shots here look like gnome. I thought the whole point of enlightenment was wasting your time making your desktop look insane.

---

### Post by titiou on 2015-04-07
All good batden, thank you for your script.

---

### Post by batden on 2015-04-23
Please refer to new thread:
[http://ubuntuforums.org/showthread.php?t=2274982](http://ubuntuforums.org/showthread.php?t=2274982)

Thanks.

---

