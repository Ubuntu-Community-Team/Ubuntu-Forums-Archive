---
title: "HOWTO: quickly improve X11 font rendering"
date: 2006-05-22
forum: Desktop Environments
---

### Post by Pausanias on 2006-05-22
[B]
This post is now outdated. For the latest improved font information, including a proper Edgy repository so you don't get conflicts, check here:

[http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)
[/B]


This is just a summary of [a previous thread](http://www.ubuntuforums.org/showthread.php?t=178737) on improving the way your fonts look in X11. Many people have noticed significant improvment in font rendering with these patches. You might wish to check out these [before](http://www.ubuntuforums.org/attachment.php?attachmentid=9666&d=1147972226) and [after](http://www.ubuntuforums.org/attachment.php?attachmentid=9667&d=1147972226) screenshots from that thread.  

Other people wrote the patches; I am just condensing the various instructions that were dispersed throughout the previous thread, with some more detailed instructions. The algorithms in these patches may or may not be covered by Microsoft's ClearType patents; check with [this guy](http://turnerdavid.neuf.fr/freetype/patches/font-patches.html) if this is a concern for you. Special thanks go to jcooper, hugmenot, mannheim, and of course David Turner who wrote the patches to begin with. 

EDIT: The instructions have been updated so as not to conflict with certain people's setups. Please report any problems on this thread.

```

sudo apt-get install libcairo2-dev libxft-dev libfontconfig1-dev
sudo apt-get remove libcairo2-dev libxft-dev
mkdir fontpatches
cd fontpatches
(download the three message attachments here)
unzip *.zip
gunzip *gz
sudo cp local.conf /etc/fonts
sudo dpkg -i *deb

```

Answer yes to all questions. Then reboot the computer. When Ubuntu comes back, go to System->Preferences->Font. Make sure that subpixel smoothing is on. Then click on details. Choose either Slight or Full Hinting, or another value if you prefer. I find that the rendering works very well with the Bitstream Vera Sans font. If you find a better font you can post it here.

To prevent future updates from overwriting the patches, load synaptic. On the left hand side, click on "Installed (local or obsolete)." Select all packages containing the words libcairo, libxft, and libfreetype. Under the package menu, select lock version. To undo the version lock, click on the word "Pinned" on the left hand side. Select all package containing the words libcairo, libxft, and libfreetype. Under the package menu, uncheck lock version. 

To uninstall the packages, go again to the "Installed (local or obsolete)" section in synaptic. Select each package one at a time. Under the package menu, select "force version." When the menu comes, select the version that has the text "(dapper)" at the end of it. When you're done doing this for all the packages, click on apply. Then "sudo rm /etc/fonts/local.conf." Reboot to get the vanilla font rendering back.

---

### Post by flargen on 2006-05-22
Hi, I was just about to try this when I realised that there are cairo packages. I use Xgl and quinn´s repo etc, which installed an updated cairo. Will it make any difference if I stick with my newer but not patched cairo packages?

Thanks for the guide + patches

---

### Post by grendelkhan on 2006-05-22
I haven't been able to get these patches to apply without rejects to the cairo cvs (which is where Quinnstorm's packages come from)

Quinn hasn't put together source packages to apt-get grabs the 1.04 release instead.

I am waiting for the patch author to redo these to work with the 1.1 branch of cairo in cvs and then I'll grab it and go.  I did apply these debs to my laptop (not running compiz) and the results are FABULOUS!

---

### Post by nalthien on 2006-05-22
I can confirm that cairo 1.0.4 patched here works with Xgl / Compiz.

---

### Post by Novox on 2006-05-22
The screenshots look promising. Looks like these patches finally provide some decent sub-pixel rendering with FreeType.

Some x86_64/AMD64 debs would be great, though... :D

---

### Post by lithorus on 2006-05-22
I'm using the quinstorm Xgl/cairo packages and everything looks good, nothing like the before picture. The trick is to set your DPI setting correctly in the Font configuration panel.

Here is my before picture :
[http://ubuntuforums.org/attachment.php?attachmentid=9875&stc=1&d=1148339542](http://ubuntuforums.org/attachment.php?attachmentid=9875&stc=1&d=1148339542)

---

### Post by mikalh on 2006-05-22
Here are some AMD64 packages. Had to do a manual merge of the Turner patch and an existing patch on Cairo, but it seems to work okay :)

---

### Post by panurge77 on 2006-05-23
I've just installed these amd64 debs on top of quinns packages (downgrading them) and it's beautiful. Sadly my X has already restarted once, so there I go upgrading... ](*,)
And I'll post on compiz forums for these changes do be considered

(some minutes later: I've posted on quinns package thred on compiz forums and it might take a while before there's an answer (looks like Quinn is away)... besides that, after the first restart X is running ok, at least for that couple minutes.... I'll leave it some more time before really doing the upgrade)

---

### Post by Novox on 2006-05-24
Thanks a lot for the AMD64 debs. They work flawlessly so far.

---

### Post by malte on 2006-05-24
:shock: impressing results!!!

---

### Post by Melvil on 2006-05-24
Absolutely AWESOME!

---

### Post by Fass on 2006-05-24
Is this supposed to have, like, ten dev-package dependencies?

---

### Post by dejitarob on 2006-05-24
Fonts look much better, like XP's 'cleartype'. 

[QUOTE=Fass]Is this supposed to have, like, ten dev-package dependencies?[/QUOTE]I installed without any extra dependencies.

---

### Post by denjin on 2006-05-24
[quote=Fass]Is this supposed to have, like, ten dev-package dependencies?[/quote]
Just delete ever .deb that has a -dev in it then do the dpkg-i.  I did that since I don't install dev debs usually.

---

### Post by jmacak on 2006-05-24
Hi 

This sounds interesting.  But...are the following messages normal?

sudo dpkg -i *.deb
Password:
(Reading database ... 137723 files and directories currently installed.)
Preparing to replace libcairo2 1.0.4-0ubuntu1 (using libcairo2_1.0.4-0ubuntu1patched_i386.deb) ...
Unpacking replacement libcairo2 ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from libcairo2-dev_1.0.4-0ubuntu1patched_i386.deb) ...
Preparing to replace libfreetype6 2.1.10-1ubuntu2 (using libfreetype6_2.1.10-1ubuntu2-turnerpatch0_i386.deb) ...
Unpacking replacement libfreetype6 ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from libfreetype6-dev_2.1.10-1ubuntu2-turnerpatch0_i386.deb) ...
Preparing to replace libxft2 2.1.8.2-0ubuntu2 (using libxft2_2.1.8.2-0ubuntu2patched_i386.deb) ...
Unpacking replacement libxft2 ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from libxft-dev_2.1.8.2-0ubuntu2patched_i386.deb) ...
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libfontconfig1-dev; however:
  Package libfontconfig1-dev is not installed.
 libcairo2-dev depends on libxrender-dev (>= 0.6.0); however:
  Package libxrender-dev is not installed.
 libcairo2-dev depends on libpng12-dev; however:
  Package libpng12-dev is not installed.
dpkg: error processing libcairo2-dev (--install):
 dependency problems - leaving unconfigured
Setting up libfreetype6 (2.1.10-1ubuntu2-turnerpatch0) ...

dpkg: dependency problems prevent configuration of libfreetype6-dev:
 libfreetype6-dev depends on zlib1g-dev | libz-dev; however:
  Package zlib1g-dev is not installed.
  Package libz-dev is not installed.
dpkg: error processing libfreetype6-dev (--install):
 dependency problems - leaving unconfigured
Setting up libxft2 (2.1.8.2-0ubuntu2patched) ...
dpkg: dependency problems prevent configuration of libxft-dev:
 libxft-dev depends on libfontconfig1-dev; however:
  Package libfontconfig1-dev is not installed.
 libxft-dev depends on libfreetype6-dev; however:
  Package libfreetype6-dev is not configured yet.
 libxft-dev depends on x-dev; however:
  Package x-dev is not installed.
 libxft-dev depends on libx11-dev; however:
  Package libx11-dev is not installed.
 libxft-dev depends on libxrender-dev; however:
  Package libxrender-dev is not installed.
 libxft-dev depends on zlib1g-dev | libz-dev; however:
  Package zlib1g-dev is not installed.
  Package libz-dev is not installed.
dpkg: error processing libxft-dev (--install):
 dependency problems - leaving unconfigured
Setting up libcairo2 (1.0.4-0ubuntu1patched) ...

Errors were encountered while processing:
 libcairo2-dev
 libfreetype6-dev
 libxft-dev

---

### Post by denjin on 2006-05-24
Do what I suggested the other person to do...

---

### Post by jmacak on 2006-05-24
Hi denjin

I'm really sorry, I missed that response.  That works for me.

cheers

---

### Post by flibble on 2006-05-28
This is the single greatest and most welcome improvement to my everyday experience of using ubuntu that I've had so far. Looking at second rate fonts all day has been a big detractor of my ubuntu experience. Thank you!

---

### Post by sittisal on 2006-05-29
Impressive quality! Not as perfect as for Mac OS X but better than windows or any other linux distribution.
A must-have for all people who love internet and works a lot with office productivity.
For developers, the terminal is still the best choice IMHO...

Turi

---

### Post by Novox on 2006-05-29
IMHO this is a must-have for all who want to use small font sizes (8 pt or smaller) to save screen space.

---

### Post by Sloth on 2006-05-31
[QUOTE=flibble]This is the single greatest and most welcome improvement to my everyday experience of using ubuntu that I've had so far.[/QUOTE]

:shock: 

I second that.  This patch is the single best patch I have ever applied.  The results are absolutely stunning.

:shock:

---

### Post by tsb on 2006-05-31
No difference here. I still have color fringing.

---

### Post by eidex on 2006-05-31
will there be a version for PPC too?

---

### Post by Abandon on 2006-05-31
What about this thread?:

[http://www.ubuntuforums.org/showthread.php?t=4456&highlight=howto+font](http://www.ubuntuforums.org/showthread.php?t=4456&highlight=howto+font)

I think I liked that one better. Hmm...

---

### Post by gorkhal on 2006-06-03
these patches r amazing...

my fonts have never looked better...beautiful...i doubt font rendering for linux will get better than this...and if it did...coool...:D

---

### Post by donar73 on 2006-06-03
With these patches my fonts look even better than on WinXP with Cleartype on... Amazing!!! :-D

---

### Post by kegie on 2006-06-03
Wow, this really makes the fonts look awesome indeed. Linux is getting closer to OSX-quality font rendering. Bold fonts still don't look all that good unfortunately.. but I am sure that will be worked out soon.

---

### Post by digital_k on 2006-06-03
**THANK** you very much for this tweak, it works perfectly! Its things like this that make me love Linux and the Linux community. :)

---

### Post by Czak on 2006-06-03
I tried these patches, and they definitely improve the overall clarity of fonts. However, there are some fonts which still look bad.
For example, I really like the Luxi family of fonts (ttf-xfree86-nonfree package in multiverse), and they just still look bad. Or maybe I'm doing something wrong?
Can somebody please check these fonts and describe/screenshot the results? I remember using them on entire system in FC5, with greyscale antialiasing and they looked awesome in all sizes/styles.

---

### Post by lazyd2 on 2006-06-03
Thanks! My kubuntu looks better than ever...

---

### Post by m3pz on 2006-06-04
Wow! The results look even better than on Windows XP with Cleartype! Thanks!!

---

### Post by zikki on 2006-06-04
Guys, thanks for some great patches, my fonts look superb with them.
I've got one small problem: after applying the patch synaptic says that there are 2 broken packages (libcairo2-dev, libxft-dev), do you know how to tell synaptic "to forget" about these packages?

Any help is appreciated, thank in advance.

---

### Post by coxis on 2006-06-04
Hey, great i was looking for this :)
Finally fonts looks great.

But what to do with that bad packs now, ubuntu say i got 3 of them:
libcairo2-dev
libfreetype6-dev
libxft-dev

And with this my update manager, now it is broke with that :(

---

### Post by Mancman on 2006-06-04
Yes, I have the same problem. Synaptic says I have 3 broken packages, so when I try to install anything it says I have to remove the them first !
Any ideas anybody?

ps. Fonts look great, though:D

---

### Post by Pausanias on 2006-06-04
Those of you who are getting errors about broken packages: did you get any error messages the first time you installed the patched packages? Or did go cleanly without any error messages?

---

### Post by nocloud on 2006-06-05
i have the same problem with the broken packages....

and yes, i got errors during the install

---

### Post by Alienist on 2006-06-05
I think you had to add those packages **before** you installed the patches. i think... (At least that's what I did, and I haven't had any problems.)

---

### Post by nocloud on 2006-06-05
is there anything i can do to fix it now that i HAVE installed the packages/patches already?

---

### Post by hugmenot on 2006-06-05
You will get broken packages if versions don&#8217;t match between the normal libs and the libs&#8217; devel packages.
If you don&#8217;t usually compile stuff forget the *-dev packages.
If you already have the dev packages installed you need to overwrite them too, so they match.
All this posting debs on the forums is a very messy method of software distribution. Someone should setup a repo fro this.

---

### Post by coxis on 2006-06-05
So. What to do to make this work ?
I still don't get the idea, sorry.
Could someone post a howto to fix that.

---

### Post by defuseme2k on 2006-06-05
I'm running amd64, sorry to be really noob, but should I also extract the fontpatched.zip along with the two amd64 packages?  I just happened to notice that the fontpatched.zip has 32bit deb's, and I didn't know if those were necessary?

I did it without, and I couldn't tell a difference =X.  Especially in firefox, when rendering hardocp.com for instance it looks like shite.

---

### Post by rhy7s on 2006-06-05
Is the OP's method still applicable and the current method for the best obtainable font rendering? It seems there should be an easily maintainable way to have readable fonts in Ubuntu. I've done a fresh install of dapper to keep things clean and I don't really want to go on another wild goose chase to get decent font rendering as I did with breezy and hoary. It's my main reason for being unable to use Ubuntu for my main rig, I just get a massive headache and eystrain. OS X is fuzzy for sure but more readable (sort of like sub-pixel smoothing with no hinting in Ubuntu) but XP's cleartype is still "clearly" the most comfortable environment, much as I would prefer it not to be.

edit: installed the patches and font rendering is the best I've seen it on linux, diagonals are almost normal :) lost my touchpad's tap function though (gsynaptics has dependencies on the patched packages) so there's a bit of housework to do but at least it will be easy on the eyes while I'm finding out how to fix that.

another edit: as the above poster notes, [H]ard|OCP is still pretty rough (hugely better than it was before though).

---

### Post by cerebral on 2006-06-05
The patch worked great on my laptop.  I have a second monitor attached and setup in xorg.conf with 96dpi with the laptop resolution of 1920x1200.  The font patch made everything look so much better.  I can actually code without hurting my eyes now.  Thanks a lot everyone.

---

### Post by just2cool on 2006-06-05
I had the problem with the 3 broken packages as well.

I did what it told me. The command (I think) was sudo apt-get install -f
and I said yes to everything. I then reinstalled the font patches right after that and then rebooted. Now, I have the new font and I no longer have the 3 broken packages.

---

### Post by Pausanias on 2006-06-05
I have just updated the instructions at the top post. If you are having problems with broken packages, you should redownload the attachments from the top post, and follow the instructions from scratch. **If** you have the broken packages, you will get an error after issuing the first command; you can safely ignore it. The remaining commands should produce no errors and all the broken packages should be fixed at the end of the procedure (reboot just to be sure to get the font rendering back).

---

### Post by Pausanias on 2006-06-05
[QUOTE=hugmenot]
All this posting debs on the forums is a very messy method of software distribution. Someone should setup a repo fro this.[/QUOTE]

OK, well who should we contact about this? The backports people?

---

### Post by Ramses de Norre on 2006-06-05
Man this patches look bad here.. I uninstalled them right away. I don't know why it's so different but they made my fonts a lot more fuzzy compared to the normal vanilla rendering packages.

---

### Post by bjtuna on 2006-06-05
Ok I don't know what I'm doing wrong here, but I followed these instructions to a T and there has been no effect on my font rendering.  This is a machine running Dapper, having been upgraded from Breezy. I had a ~/.fonts.conf going in Breezy that improves the font rendering quite a bit, and it still works pretty well, but not as well as in Breezy. I renamed that file, hoping these patches would do the same (or better) but my fonts just look thin and definitely not subpixel-smoothed.

Let me know what sort of diagnostic output I need to show here...

Thanks!

---

### Post by Pausanias on 2006-06-05
Ramses and bjtuna, are you using LCDs or CRTs? The patches should not really affect font rendering on a CRT.

---

### Post by bjtuna on 2006-06-05
[QUOTE=Pausanias]Ramses and bjtuna, are you using LCDs or CRTs? The patches should not really affect font rendering on a CRT.[/QUOTE]


LCD.

---

### Post by Pausanias on 2006-06-05
After removing .fonts.local, did you restart GDM (or reboot)?

Did you go into the Fonts preferences menu (under System->Preferences) and activate subpixel rendering and autohinting?

If you go into synaptic, and click on the section "Installed (local or obselete)", do the patched libxft, libcairo2, and libfreetype6 show up?

If the answer to all three questions is, "yes," then I'm not sure what the answer is, bjtuna.

---

### Post by bjtuna on 2006-06-05
[QUOTE=Pausanias]After removing .fonts.local, did you restart GDM (or reboot)?

Did you go into the Fonts preferences menu (under System->Preferences) and activate subpixel rendering and autohinting?

If you go into synaptic, and click on the section "Installed (local or obselete)", do the patched libxft, libcairo2, and libfreetype6 show up?

If the answer to all three questions is, "yes," then I'm not sure what the answer is, bjtuna.[/QUOTE]

Yes, yes and yes :(

---

### Post by ruffneck on 2006-06-06
The results are absolutely stunning! Thank you so much!

---

### Post by coxis on 2006-06-06
I see there is a new instruction to install it, nice. Ok i uninstall the dev packs.

The solusion for me was to uninstall the dev (the broken one) and now it is workin good :)

---

### Post by piotrs on 2006-06-06
Unbelievable - this is what I was looking for since my very beginings with Linux. The only issue, to be mentioned, is some kerning problems (sometimes) - I hope it is to be fixed...

---

### Post by Ramses de Norre on 2006-06-06
[QUOTE=Pausanias]Ramses and bjtuna, are you using LCDs or CRTs? The patches should not really affect font rendering on a CRT.[/QUOTE]
LCD too, and I checked all settings in gnome-font-properties.
I also did restart X and it looked the same when I booted up again the next day.
All the patches were aplied.
So I just deleted the packages again and got my reasonable font rendering back.

---

### Post by calande on 2006-06-08
Is it just me or other also see no difference between the "B4" and "After" screenshots of the original message? :rolleyes:

---

### Post by toaste on 2006-06-08
calande,

If you have a CRT, you won't see any difference between sub-pixel rendering (cleartype in MS) and regular anti-aliasing.  This is because sub-pixel rendering depends on the order of red/green/blue segments within a pixel, which is well defined on LCDs and just kind of a blob on a CRT.

---

### Post by rickg on 2006-06-08
Holy crap!  Fonts were OK before, but everything is so much clearer now, esp small sizes!!

Thanks very much for this.

---

### Post by donar73 on 2006-06-09
A security-update to libfreetype6 2.1.10 has been released ([klick](http://www.ubuntuforums.org/showthread.php?t=192091)). Maybe someone could make new patched deb's?

---

### Post by chanders on 2006-06-09
This stops caro-clock from working, it doesnt update anymore....  :-(  Such a hard tradeoff... Someone please supply the patch to the cairo development team....

I am running XGL and Compiz BTW...

---

### Post by jinacio on 2006-06-10
I followed the simple instructions, copied some fonts from a windows box, and used a custom ~/.fonts.conf to tune at wich sizes fonts would be antialiased.

They now look *almost perfect* on my 17" CRT monitor (some characters still have bugs: verdana bold uppercase W and N are examples).

Feel free to browse some of my screenshots:

[http://jcinacio.com/fonts-firefox-screenshots/]("http://jcinacio.com/fonts-firefox-screenshots/")

BTW: I also use other (non-MS) fonts with antialising and they look pretty decent.

Cheers!
Joao Inacio

---

### Post by Pausanias on 2006-06-11
[QUOTE=donar73]A security-update to libfreetype6 2.1.10 has been released ([klick](http://www.ubuntuforums.org/showthread.php?t=192091)). Maybe someone could make new patched deb's?[/QUOTE]

When I get the chance, I plan to do so, together with actual working patches so that non-i386 architectures can make their own debs.

---

### Post by hugmenot on 2006-06-11
jinacio, are you being serious? There&#8217;s subpixel rendering nowhere in any of your screenshots. Even more, most of your fonts are monochrome.
Nothing of which this topic is about can be seen in your screenshots.

---

### Post by nocloud on 2006-06-11
jinacio, ur fonts look hideous

---

### Post by jinacio on 2006-06-11
Well, i just wanted to show how they look for CRT users like me, in case someone's interested.

I don't use a LCD at home, but if i grab 1 at work i'll take a couple more.

---

### Post by leimus on 2006-06-15
The first two lines of the instructions are:

sudo apt-get install libcairo2-dev libxft-dev libfontconfig1-dev
sudo apt-get remove libcairo2-dev libxft-dev

isn't this installing and then removing libcairo2 and libxft? Or is there something I'm not quite getting...

---

### Post by hugmenot on 2006-06-15
> isn't this installing and then removing libcairo2 and libxft? Or is there something I'm not quite getting...
No, this is installing and then removing the headers for those packages, which noone, who actually needs instructions to accomplish this, would need anyway. They&#8217;re only needed when you plan to compile something that depends on one of these libs.
Why the hokuspokus? Superstition comes in many ways.

---

### Post by giuliastro on 2006-06-15
Is this going to be included in Ubuntu ufficially? What I don't like is having my update icon constantly flashing telling me there are 6 updates waiting.. :)

---

### Post by jgbiggs on 2006-06-15
Will these patches solve the funny issue I am having?  My screen fonts seem to quiver or shake on my lcd.  especially in the terminal.

I have the refresh set to exactally what it is when an XP machine is using the display and the dpi is set to 96 (17 inch lcd)

I have futzed around with all the font hinting and sub-pixel foo and even tried a bunch of TrueType front from a windows install.

This problem only came about after doing a clean install of 6.06

Thanks.

---

### Post by georgevn on 2006-06-15
hi, can you help with the newer version of the packages?

---

### Post by crash9877 on 2006-06-16
absolutly amazing. never looked so good on my TFT. The best patch i´ve ever applied.

---

### Post by dimaash on 2006-06-16
Is it possible to apply those patches on a Debian system?
 I've tried but it complains about some dependancy conflicts and says my libc6 is old. (2.3.2 something something, sarge).

I would appriciate if someone could tell me how to get those patches working on a debian box.

---

### Post by hugmenot on 2006-06-16
I noticed that the folks that provide the XGL packages did their homework and provide source packages for libcairo2 1.1.8.
I looked at patching it and saw that significant changes went into cairo font stuff between 1.0.4 and 1.1.8
This patch needs a thorough porting effort for 1.1.8.

---

### Post by neo_reloaded on 2006-06-18
This patch is all what gnome font rendering needed??? :)
works great - thanks all!

---

### Post by donar73 on 2006-06-19
[QUOTE=Pausanias]When I get the chance, I plan to do so, together with actual working patches so that non-i386 architectures can make their own debs.[/QUOTE]

Any progression on this?

---

### Post by rniella on 2006-06-21
Hi, have a i386 AMD with Ubunto 6.06 freshly installed, Nvidia FX5200 installed OK, etc...   I just wanted to improve the font renedring a little bit so I´ve tried this howto and the end result was ok but not all that different from what I already had.. in fact, the rendering was a liiittle bit worse with some coloring around the edges of small fonts.. the thing is that when I tried the uninstall procedure: "To uninstall the packages, go again to the "Installed (local or obsolete)" section in synaptic. Select each package one at a time. Under the package menu, select "force version." When the menu comes, select the version that has the text "(dapper)" at the end of it........." etc.  my system went CRAZY !!  first I lost almost all the icons (while the uninstall was working) then the X session closed and could never startit again !! If I reboot Ubuntu, it goes directly to the terminal and the command line.. is there a way to get the X system back ??  what commands could I run to reinstall the basics without having to reinstall from scratch ???  Thank you very much in advance !!

Reinaldo

---

### Post by Pausanias on 2006-06-21
Sounds like you've inadvertantly uninstalled some of the core system stuff when you reverted. 

Try this. When you go to the terminal command line, log in as usual and then type

```

sudo apt-get install ubuntu-desktop ubuntu-minimal ubuntu-standard

```

Answer yes to all the questions. See what happens then.

---

### Post by elephas on 2006-06-21
Followed the instructions on the top and got this:

```
Setting up libxft2 (2.1.8.2-0ubuntu2patched) ...
dpkg: dependency problems prevent configuration of libxft-dev:
 libxft-dev depends on x-dev; however:
  Package x-dev is not installed.
 libxft-dev depends on libx11-dev; however:
  Package libx11-dev is not installed.
 libxft-dev depends on libxrender-dev; however:
  Package libxrender-dev is not installed.
dpkg: error processing libxft-dev (--install):
 dependency problems - leaving unconfigured
Setting up libcairo2 (1.0.4-0ubuntu1patched) ...

Errors were encountered while processing:
 libcairo2-dev
 libxft-dev
``` 
so I ran ```
aptitude install x-dev
``` then reran last step, then it worked

---

### Post by rniella on 2006-06-21
=D>   Thank you very much !!!  it worked !!!  I have almost everything back to what I had before, thanks again for your great help !!!

Reinaldo

[QUOTE=Pausanias]Sounds like you've inadvertantly uninstalled some of the core system stuff when you reverted. 

Try this. When you go to the terminal command line, log in as usual and then type

```

sudo apt-get install ubuntu-desktop ubuntu-minimal ubuntu-standard

```

Answer yes to all the questions. See what happens then.[/QUOTE]

---

### Post by wjarek on 2006-06-23
I tried these and comparing with the clarity of Windows fonts Ubuntu is nowhere near. FC5 can be easily configured to match Windows, not sure why this is so hard on Ubuntu.

---

### Post by hugmenot on 2006-06-23
I see. Do you have a screenshot of that FC5 quality you speak of?

---

### Post by malte on 2006-06-24
I pinned (Lock version) the installed packages in Synaptic but the update-manager still wants to upgrade them (and they have the same version number too...).
Anyone noticed the same strange behaviour?

---

### Post by QwUo173Hy on 2006-07-03
"When Ubuntu comes back, go to System->Preferences->Font. Make sure that subpixel smo
othing is on. Then click on details. Choose either Slight or Full Hinting, or another value if you prefer."

How do I do this in Kubuntu?

---

### Post by bladus on 2006-07-09
I just tried this patches, and they are awesome! Thank you

---

### Post by desperado666 on 2006-07-10
Possible to build newer version of libcairo2 and the others?
I use Quinns XGl so i use newer versions but they are not patched...

---

### Post by Treviño on 2006-07-12
.> **desperado666 said:**
> Possible to build newer version of libcairo2 and the others?
I use Quinns XGl so i use newer versions but they are not patched...I'm asking the same too... The problem is that I can't find the patch used in libcairo... In the pach author site, there's no trace of this.


@jarlath: in kubuntu do it from kcontrol -> Font selector. Btw use gnome-font-properties to set that values for gtk apps:
[[IMG]http://img100.imageshack.us/img100/2467/smothfontssettingsscreenshot8o.th.png[/IMG]](http://img100.imageshack.us/my.php?image=smothfontssettingsscreenshot8o.png)

---

### Post by jackpipe on 2006-07-16
Well, I too have tried this patch, with mixed results.
Congratulations for getting this far - This is one of the things I've been waiting for (for about 10 years!!) before making linux my permanent everyday desktop, rather than just for my server / useful tookit under VMware.

Firstly, on a VMware install under XP, the patches seemed to make quite an improvement, although the libfreetype patche seemed to make the text 'smudgy' - I personally very much like the MS 'anemic' style and find that on a 14.1" XGA laptop screen text needs to be as crisp as possible.

I then installed ubuntu 'for real'.  After a complete installation failure (another story) I got things working, but noticed that the default screen depth was 16 bits.  I've now changed that to 24.
This time, applying the patches results in relatively smudgy, color-banded text.  Relative to the bog-standard ubuntu install, that is.  So I've now de-applied the patches.  Is there a chance that these show most improvement on 16bit screens ?

I'd agree with the post above that says even with the patch, it still doesn't match windows - promising though it looks, though I can't see why another distro would be any better.

A final question about the filter being used (0x10, 0x70, etc) - even MS provide a 'cleartype tuner' since presumably different screens and different users have different tolerances/preferences.  Ideally I guess the filter should be configurable - but in the meantime, any suggestions for values to try, and why were the current values chosen?

---

### Post by hugmenot on 2006-07-16
> **jackpipe said:**
> A final question about the filter being used (0x10, 0x70, etc) - even MS provide a 'cleartype tuner' since presumably different screens and different users have different tolerances/preferences.  Ideally I guess the filter should be configurable - but in the meantime, any suggestions for values to try, and why were the current values chosen?

They were chosen by David Turner based on what looked good on the two LCD screens he had available. All that these patches show is that there is potential for improvement in the area of font rendering on X11. They are, however, not very user-friendly because many combinations of settings are possible; many lead to suboptimal results. On Windows it&#8217;s a toggle with a simple tableau to select the optimal FIR parameter for a given screen and taste. If the improved FIR filtering makes it into the affected libraries something like that needs to go into the GUI dialogs.

---

### Post by jackpipe on 2006-07-17
Are the values free-form ?  They are currently 0x10, 0x40, 0x70, 0x40, 0x10 - which looks suspiciously like a bitmask of some kind to me.
Can I just pick 0x12, 0x53, 0x7a, for example?
I'm asking rather than trying, since I haven't got all the dev stuff installed yet, so can't just compile it up and try...

---

### Post by s_spiff on 2006-07-21
what to do for smd64 arch type?

---

### Post by oobuntoo on 2006-07-28
I was skeptical about this patch at first, but it really works. However, if you're using nvidia driver and turned on XGL, you might get really fuzzy fonts when FSAA is enabled by having "export __GL_FSAA_MODE" in a config file somewhere. I turned off FSAA and now my fonts stay focus all the time.

---

### Post by Footissimo on 2006-07-29
Thankyou for these patched debs, they work lovely :)

Is there anyway to have a nobytecode version of the libfreetype deb, as outlined in [this howto](http://ubuntuforums.org/showthread.php?t=84359) (to improve fonts in OOo)?  Its not a big change, but at the moment, if I apply one patch, I can't have the other :(

---

### Post by giuliastro on 2006-07-30
> **oobuntoo said:**
> I was skeptical about this patch at first, but it really works. However, if you're using nvidia driver and turned on XGL, you might get really fuzzy fonts when FSAA is enabled by having "export __GL_FSAA_MODE" in a config file somewhere. I turned off FSAA and now my fonts stay focus all the time.

I don't understand. What do you mean for "fuzzy fonts"? And what is the config file that should have the line you mention? Thanks in advance.

---

### Post by oobuntoo on 2006-07-30
> **giuliastro said:**
> I don't understand. What do you mean for "fuzzy fonts"? And what is the config file that should have the line you mention? Thanks in advance.

I meant my fonts, especially in Firefox, will stay sharp or focus for few seconds then get blurry/fuzzy (like an object in a photo that's out of focus). If I refresh my desktop or reload a web page, fonts became sharp (like cleartype) again, but only for few seconds. In Firefox, if I moved the mouse cursor over a link, that link text instantly became sharper and then got blurry again. So I had to refresh my desktop and webpage constantly.

How do I know this is caused by full scene antialiasing, FSAA? I had this line "export __GL_FSAA_MODE=4" in my /etc/init.d/kdm config file. After I removed this line, the only thing I did, the font problem I mentioned above, went away.

---

### Post by zerwas on 2006-07-31
Thanks for this howto and the files. Better than Microsofts Cleartype!
works perfectly.

---

### Post by digivation on 2006-08-01
**WOW**

The difference is amazing ... no more annoying fringe... looks as good as or better than XP. I've been using Windows with Cleartype enabled for years now, and after switching my laptop back to Ubuntu (I used it a little last summer), this has made things look WONDERFUL.

Thanks!

---

### Post by Rollmops on 2006-08-03
There are already updates for libfreetype6. The current package is 2.1.10-1ubuntu2.2. The patched package is 2.2.10-1ubuntu2. Does someone has a more recent patched package?

---

### Post by donar73 on 2006-08-03
> **Rollmops said:**
> There are already updates for libfreetype6. The current package is 2.1.10-1ubuntu2.2. The patched package is 2.2.10-1ubuntu2. Does someone has a more recent patched package?

I'd like to see updated versions too, there were two security-updates to libfreetype6 since this patched version came out.

---

### Post by hugmenot on 2006-08-03
I provided the quantization-disabled libfreetype6 originally, but I moved to edgy in the meantime and completely lost the improvements.
I really hope the patches will not get lost in history.

But the patch was really simple for this one and should be easy to update.

---

### Post by donar73 on 2006-08-04
> **hugmenot said:**
> I provided the quantization-disabled libfreetype6 originally, but I moved to edgy in the meantime and completely lost the improvements.
I really hope the patches will not get lost in history.

But the patch was really simple for this one and should be easy to update.

Can you give us a little HowTo? I'd like to know how to apply the patches by myself.

---

### Post by hugmenot on 2006-08-04
> **donar73 said:**
> Can you give us a little HowTo? I'd like to know how to apply the patches by myself.

apt-get source libfreetype6
apt-get build-dep libfreetype6
Check [this posting]("http://lists.nongnu.org/archive/html/freetype/2006-04/msg00012.html") 
Observe the small change in the patch
cd into freetype_2.*/
Untar the source tarball
Navigate to the right place in the source file
remove the "|| mode == FT_RENDER_MODE_LCD" conditional
Retar the tarball (with c**j**f)
dpkg-buildpackage -rfakeroot -b
Either set the package to "hold" in whatever package manager you use or increment the version of the package in debian/changelog before you build the packages (append something like -patched0).

Is that detailed enough?

---

### Post by Footissimo on 2006-08-04
When you say :

> **hugmenot said:**
> apt-get source libfreetype6
Navigate to the right place in the source file
remove the "|| mode == FT_RENDER_MODE_LCD" conditional
Is that detailed enough?

I presume you mean .../freetype-2.1.10/freetype-2.1.10/src/autofit/aflatin.c?  Then removing both instances of the conditional?

---

### Post by hugmenot on 2006-08-04
Yes sure, I assumed that you are able to handle finding the right place by reading the patch. Otherwise you really shouldn&#8217;t fool around with system-critical libraries.

---

### Post by donar73 on 2006-08-05
> **hugmenot said:**
> apt-get source libfreetype6
apt-get build-dep libfreetype6
Check [this posting]("http://lists.nongnu.org/archive/html/freetype/2006-04/msg00012.html") 
Observe the small change in the patch
cd into freetype_2.*/
Untar the source tarball
Navigate to the right place in the source file
remove the "|| mode == FT_RENDER_MODE_LCD" conditional
Retar the tarball (with c**j**f)
dpkg-buildpackage -rfakeroot -b
Either set the package to "hold" in whatever package manager you use or increment the version of the package in debian/changelog before you build the packages (append something like -patched0).

Is that detailed enough?

Thanks, it worked for me! :)

---

### Post by kinghajj on 2006-08-06
I'm having a problem with the instructions at the start of this thread.
[IMG]http://kinghajj.ath.cx/images/problem.png[/IMG]
As you can see, I have subpixel rendering enabled, and the example looks as it should, but the way the fonts are actually being rendered looks like it's still using the grayscale method. I've taken screenshots of fonts being rendered on white backgrounds, and it still appears to be using grayscale.

---

### Post by hugmenot on 2006-08-06
Run "sudo dpkg-reconfigure fontconfig" in a terminal and see whether subpixel rendering is selected system-wide.

EDIT: And check that there isn&#8217;t a hidden ".fonts.conf" in you home dir that overrides your Gnome settings.

---

### Post by xelios on 2006-08-07
Thank's a lot **Pausanias**!

I just followed your *howto*, and now my fonts are so smooth :-D

---

### Post by kurup on 2006-08-07
sorry to ask a naiive question at this stage of the thread..is there a possibility of acheiving any results on a CRT monitor?

---

### Post by snowpalmer on 2006-08-07
I just installed this on my system and it looks great! 

> What about this thread?:

[http://www.ubuntuforums.org/showthre...ght=howto+font](http://www.ubuntuforums.org/showthre...ght=howto+font)

I think I liked that one better. Hmm...

I disagree. I just removed my .fonts.conf from that forum and installed these packages. This is much better. That .fonts.conf made some fonts look good and others look really bad.

Thanks,

Snowpalmer

---

### Post by bandoba on 2006-08-08
Great info! Ubuntu looks really great with these changes.

BTW, I locked the packages as suggested in first post. Later I issued apt-get update and upgrade command and looks like it upgraded some of the packages required for these fonts. With this, I lost the great the looking fonts. Can you please help me get back the fonts?

Here are my  versions:
libxft2 and libxft-dev - 2.1.8.2-0ubuntu2patched
libfreetype6 & libfreetype6-dev - 2.1.1.0-1ubuntu2-turnerpatch0

TIA.

---

### Post by chaosgeisterchen on 2006-08-08
I suggest reinstalling the patched libcairo2 and libcairo2-dev?

Helped with me as far as I remember. Well.. Synaptic/apt in general is arguing with these debs as there are 'better' Versions in the repos, you should really lock them by setting them to be _hold_

@thread:

I am using it some time now and the results are fabolous! Great improvement, KDE is not even more a charm for my eyes and for working on it :)

---

### Post by bandoba on 2006-08-08
Thanks chaosgeisterchen. I tried installing libcairo2 and libcairo20-dev. But it updated only libcairo2-dev and it says libcairo2 is already the newest version. Then I read the thread again and just followed the steps once again from scartch. Now the fonts look great again!

BTW, how can I make lock the packages by setting them on _hold_?

---

### Post by chaosgeisterchen on 2006-08-09
Oh.. it works like that:

```
sudo dpkg --set-selections << EOF
<package name 1> hold
<package name 2> hold
<package name 3> hold
<package name 4> hold
EOF
```

And: you better work it out the way it's explained in the initial posting, first uninstalling all the packages and then reinstalling the patched ones. Setting them on **hold** and you should be happy again...

---

### Post by prymitive on 2006-08-10
Is there a patch against cairo 1.2.2?

---

### Post by tannq on 2006-08-11
This is great, thank you very much.

---

### Post by Mystique on 2006-08-11
i try this patches on my "do what ever you want" PC

seems to me as a dirty hack, packages have to be pinned etc..

i do it my way:

first add load "xtt" to xorg.conf (loadsection)

add dpi=96x96 to xorg.conf (card-device section)

then debconf fontconfig, say autohinter & always

then debconf x-ttcidfont-conf, say use xtt as backend & quality over speed
(i realy dont know the exact differents between the 2 backends, but xtt seems to look better on my monitor)

installing the ms-font
choose in gnome-font the right fonts, do lcd-subpixel

and finaly
firefox: about:config, choose font.FreeType2.autohinted=true & font.FreeType2.enable


for me it look ok.
i dont have to attention when dist-upgrade etc...

---

### Post by hugmenot on 2006-08-13
For Edgy packages see this thread: [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)

---

### Post by hanzomon4 on 2006-08-17
I had to update my libvte4 and broke it my fonts can. Someone update this patch.

---

### Post by latebeat on 2006-08-17
> **hanzomon4 said:**
> I had to update my libvte4 and broke it my fonts can. Someone update this patch.
Same problem here! Need the new versions of the patched libraries asap! :(

---

### Post by lazyd2 on 2006-08-17
> **latebeat said:**
> Same problem here! Need the new versions of the patched libraries asap! :(
+1

---

### Post by misha680 on 2006-08-17
Ok, I made a HOWTO including the patched debs and instructions for patching yourself. It can be found here:

[http://www.ubuntuforums.org/showthread.php?p=1398114#post1398114](http://www.ubuntuforums.org/showthread.php?p=1398114#post1398114)

Misha

---

### Post by Robin Mulder on 2006-08-18
I tried those debs, they don't seem to be working for me.

---

### Post by misha680 on 2006-08-18
Deleted

---

### Post by hanzomon4 on 2006-08-18
Same here font's still look blurry. But I appreciate the effort

---

### Post by misha680 on 2006-08-18
Ok, I figured it out. The edgy libxft didn't work, but if I just get the source for the dapper one and then patch it it works great :) I updated the tar.bz2 files in my post several above. Enjoy :)

Misha

---

### Post by hanzomon4 on 2006-08-18
Good job! I can read in peace again. 

Hey would you mine doing howto on how to patch these files?

---

### Post by neo_reloaded on 2006-08-18
> **misha680 said:**
> Ok, I figured it out. The edgy libxft didn't work, but if I just get the source for the dapper one and then patch it it works great :) I updated the tar.bz2 files in my post several above. Enjoy :)

Misha

Hey, thanks a lot for the patch.
Would you mind sharing the secret of patching ..?
thanks

---

### Post by aiiee on 2006-08-19
Outstanding work!  Fonts look thousand times better.  And as a bonus, Firefox now listens to me when I tell it to use system font sizes instead of page defined font sizes. Thanks!

---

### Post by oobuntoo on 2006-08-19
Thanks for these newly patched packages. However, the result is not the same as the original patched packages from the first page of this thread. The normal texts look very good, but the bold texts look blurry with bad spacing between letters. I have gone back to the original patched packages even though Synaptic complains about two broken packages.

---

### Post by ariel on 2006-08-19
Hi there, I followed the howto at the beginning of this thread and this gave nice looking fonts but synaptic complains about the package index being broken, and suggests to run this:

          sudo apt-get install -f

This changes back libfreetype; after that, synaptic runs and offers to downgrade libcairo2; after a reboot I am back where I started, with the Bold fonts in firefox totally unreadable.

I have xgl/compiz and use quinns' repo. I'd like to remove that but I have so many dependencies on them now that I prefer to wait for edgy.

Has someone out there been able to fix this without removing compiz' new features (transparent terminal and such)? Can someone post a procedure?

Thanks!

---

### Post by misha680 on 2006-08-19
I think for the bold fonts problem all you need to do is take the patchedfonts.zip from the original post in this thread, unzip it, and do a 

```
sudo cp local.conf /etc/fonts
```

As for the broken packages, see my post a page back.

Hope that helps.

Misha

---

### Post by oobuntoo on 2006-08-19
> **misha680 said:**
> I think for the bold fonts problem all you need to do is take the patchedfonts.zip from the original post in this thread, unzip it, and do a 

```
sudo cp local.conf /etc/fonts
```

As for the broken packages, see my post a page back.

Hope that helps.

Misha

I have tried copy local.conf file you mentioned along with installing your new patched packages, but bold fonts still look crappy.

Also, does anyone know what happened to this David Turner guy's site [here]("http://turnerdavid.neuf.fr/freetype/patches/font-patches.html")? I was hoping to find his original patch.

---

### Post by misha680 on 2006-08-19
If you can make it work better, that will be great. I made a HOWTO that descrbes what I did to patch the files and also moved the debs there:

[http://www.ubuntuforums.org/showthread.php?p=1398114#post1398114](http://www.ubuntuforums.org/showthread.php?p=1398114#post1398114)

Misha

---

### Post by ariel on 2006-08-19
I tried the new packages and the local.conf replacement, rebooted, and got back the bold font problem. What I finally did to fix it is getting this two new libfreetype6 debs from here:

[http://www.compiz.net/viewtopic.php?pid=26964#p26964](http://www.compiz.net/viewtopic.php?pid=26964#p26964)

after installing, synaptic complained again of a broken index, then i run 

apt-get install -f 

which removed the -dev packages for cairo, libfreetype and a few more  -devs , but left the font rendering system untouched. After a restart everything looks fine (better than before all this odisea). Hopefully the compiz will be a bit more carefull after this. Although i know this is what it takes to use development software.... which I enjoy anyways :-)

---

### Post by misha680 on 2006-08-19
Ariel, could you try my new debs here:

[http://www.ubuntuforums.org/showthread.php?p=1398114#post1398114](http://www.ubuntuforums.org/showthread.php?p=1398114#post1398114)

I turned on the bytecode interpreter in the libfreetype debs (that is what  it seems to me was also done on the compiz packages from the posts I saw). Does this fix the bold thing for you?

Thanks
Misha

> **ariel said:**
> I tried the new packages and the local.conf replacement, rebooted, and got back the bold font problem. What I finally did to fix it is getting this two new libfreetype6 debs from here:

[http://www.compiz.net/viewtopic.php?pid=26964#p26964](http://www.compiz.net/viewtopic.php?pid=26964#p26964)

after installing, synaptic complained again of a broken index, then i run 

apt-get install -f 

which removed the -dev packages for cairo, libfreetype and a few more  -devs , but left the font rendering system untouched. After a restart everything looks fine (better than before all this odisea). Hopefully the compiz will be a bit more carefull after this. Although i know this is what it takes to use development software.... which I enjoy anyways :-)

---

### Post by xtknight on 2006-08-19
Here are some amd64 debs for the latest libcairo2(1.2.2) and libxft2(2.1.8.2) with the ClearType patches applied.

[libcairo2_1.2.2-0firfilt1_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/libcairo2_1.2.2-0firfilt1_amd64.deb")
[libcairo2-dev_1.2.2-0firfilt1_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/libcairo2-dev_1.2.2-0firfilt1_amd64.deb")
[libxft2_2.1.8.21-0cleartype1_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/libxft2_2.1.8.21-0cleartype1_amd64.deb")
[libxft2-dbg_2.1.8.21-0cleartype1_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/libxft2-dbg_2.1.8.21-0cleartype1_amd64.deb")
[libxft-dev_2.1.8.21-0cleartype1_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/libxft-dev_2.1.8.21-0cleartype1_amd64.deb")

These should have no package conflicts.  Install:

sudo dpkg -i --force-all libcairo2_1.2.2-0firfilt1_amd64.deb
sudo dpkg -i --force-all libcairo2-dev_1.2.2-0firfilt1_amd64.deb

sudo dpkg -i --force-all libxft2_2.1.8.21-0cleartype1_amd64.deb
sudo dpkg -i libxft2-dbg_2.1.8.21-0cleartype1_amd64.deb
sudo dpkg -i libxft-dev_2.1.8.21-0cleartype1_amd64.deb

I'll see if I can get some i386 ones later.

Edit: It looks like I need to patch freetype too.  Does anyone have the patch files for that?  His site is down.

---

### Post by mlind on 2006-08-19
Here's repository for i386 binaries and source
```

deb http://www.elisanet.fi/mlind/ubuntu dapper fonts
deb-src http://www.elisanet.fi/mlind/ubuntu dapper fonts

```

---

### Post by danil on 2006-08-22
After installation this packages for amd64 my xorg was crashed! How can I remove this packages?

2 Misha680: ty govorish po russki?

---

### Post by Johan! on 2006-08-22
You probably installed a xorg-related update today.
The update broke many Ubuntu machines, search the forums and find the topics... :(

---

### Post by iamsobored0056 on 2006-08-22
um, i have the same problem where there are 3 broken packages.  when i try to fix the broken packages in synaptic almost all of my programs are removed. is that normal?

---

### Post by misha680 on 2006-08-22
> **danil said:**
> After installation this packages for amd64 my xorg was crashed! How can I remove this packages?

2 Misha680: ty govorish po russki?

Da govorui. See Johan!'s post. Also, if for some reason it is the packages that you want to remove and you can't use X you can use aptitude, just type:

```
sudo aptitude
```

Then you can use the forward slash character (/) to find libcairo and libcairo-dev, same for libxft and libfreetype. For each package you find, you click enter on it to go into the details, scroll to the bottom with the arrow keys, find a list of previously installed version there, select the latest one that is not installed (doesn't have the little i on the left hand side), press the + plus key to select that it be installed.

To apply all your selected changed press the "g" button.

Misha

---

### Post by danil on 2006-08-25
Misha, 10ks for your help!

---

### Post by Mandoscottie on 2006-08-25
spot on this worked flawlessly :) thanks

---

### Post by bmor4590 on 2006-08-28
Love it - thanks.

---

### Post by mindtrick on 2006-08-29
> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libfreetype6-dev (>= 2.1.7) but it is not going to be installed
  libfontconfig1-dev: Depends: libfreetype6-dev (>= 2.1.7) but it is not going to be installed
  libxft-dev: Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages


I couldn't.

---

### Post by misha680 on 2006-08-29
Did you download _all_ the packages including the two .deb.bz2 files I've attached in addition to hte fontdebs.tar.bz2 files? And unpack the .deb.bz2 files using the Debian command? Sorry... just got to check the simple things before I go delving further.

Misha

> **mindtrick said:**
> I couldn't.

---

### Post by Footissimo on 2006-08-31
> **hugmenot said:**
> Yes sure, I assumed that you are able to handle finding the right place by reading the patch. Otherwise you really shouldn’t fool around with system-critical libraries.

It's called learning ;)  Thanks for the info :)

---

### Post by blackbirdXXX on 2006-09-05
Will there be packages for ubuntu edgy too? Because the current edgy font rendering (especially firefox) looks very bad...

---

### Post by misha680 on 2006-09-05
[http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)

> **blackbirdXXX said:**
> Will there be packages for ubuntu edgy too? Because the current edgy font rendering (especially firefox) looks very bad...

---

### Post by starNIX on 2006-09-06
I have 3 broken packages on my system as well and running this:  

[code]
sudo apt-get install -f     Causes this:      
[code/]

[code]
Reading package lists... Done Building dependency tree... Done Correcting dependencies...Done The following packages will be REMOVED   acidrip alacarte alltray at-spi automatix avidemux azureus baobab beagle beagle-backend-evolution bluez-cups bluez-pin   brltty-x11 bug-buddy bum cgwd cgwd-themes compiz compiz-core compiz-gnome compiz-plugins contact-lookup-applet cowbell   csm cupsys cupsys-driver-gutenprint dasher dbus-1-utils deskbar-applet dia-common dia-gnome eog etherape evince evolution   evolution-exchange evolution-plugins evolution-webcal exaile f-spot file-roller firefox firefox-gnome-support   firefox-themes-ubuntu fontconfig freeloader freespeak freevo freevo-media gaim gaim-encryption gaim-extendedprefs   gaim-guifications gaim-otr gcalctool gchangepass gconf-editor gdebi gdm gedit gimp gimp-print gimp-python gkrellm gksu   gnome-about gnome-accessibility-themes gnome-alsamixer gnome-app-install gnome-applets gnome-art gnome-bling-manager   gnome-btdownload gnome-compiz-manager gnome-control-center gnome-cups-manager gnome-games gnome-gpg gnome-icon-theme   gnome-keyring gnome-keyring-manager gnome-launch-box gnome-mag gnome-main-menu gnome-media gnome-netstatus-applet   gnome-nettool gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-schedule gnome-screensaver   gnome-session gnome-spell gnome-splashscreen-manager gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes   gnome-utils gnome-volume-manager gnopernicus gok gparted gpass greent gstreamer0.10-plugins-bad   gstreamer0.10-plugins-good gstreamer0.10-x gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-gtk   gstreamer0.8-lame gstreamer0.8-misc gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-swfdec   gstreamer0.8-vorbis gstreamer0.8-xvid gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast   gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95   gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap hal-device-manager hardinfo   hot-babe hplip hwdb-client inkscape k3b kcontrol kdebase-bin kdelibs-bin kdelibs4c2a kicker language-selector leafpad   libarts1c2a libatspi1.0-0 libavahi-qt3-1 libbonoboui2-0 libcairo-java libcairo-ruby libcairo2 libcairo2-dev   libdbus-qt-1-1c2 libedataserverui1.2-6 libeel2-2 libevolution-cil libexchange-storage1.2-1 libfontconfig1   libfontconfig1-dev libgail-common libgail-gnome-module libgail17 libgcj7-awt libgdk-pixbuf2-ruby libgdl-1-0   libgdl-1-common libgecko2.0-cil libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglade2-ruby libglade2.0-cil   libglademm-2.4-1c2a libgnome-desktop-2 libgnome-keyring-dev libgnome-keyring0 libgnome2-canvas-perl libgnome2-perl   libgnome2-wnck-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprintui2.2-0   libgnomeui-0 libgpod0 libgtk-java libgtk-jni libgtk2-gladexml-perl libgtk2-perl libgtk2-ruby libgtk2-trayicon-perl   libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtkmm-2.4-1c2a   libgtksourceview1.0-0 libgtksourceview2.0-cil libgtkspell0 libgucharmap4 libgutenprintui2-1 libk3b2 libkonq4   liblaunchpad-integration0 liblpint-bonobo0 libmetacity0 libmultisync-plugin-backup libmultisync-plugin-evolution   libnautilus-burn3 libnautilus-extension1 libnotify-bin libnotify1 libpanel-applet2-0 libpango1-ruby libpango1.0-0   libpango1.0-common libpoppler1 libpoppler1-glib libqt3-mt librsvg2-2 librsvg2-common libsexy1 libsexy2 libsvg-cairo   libswfdec0.3 libswt3.1-gtk-java libswt3.1-gtk-jni libtotem-plparser1 libvte2.0-cil libvte4 libwnck18 libxft-dev libxft2   listen mail-notification mencoder mencoder-386 metacity metacity-themes mozilla-browser mozilla-mplayer   mozilla-thunderbird mplayer-fonts mplayer-nogui multisync nautilus nautilus-cd-burner nautilus-sendto netapplet   notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core   openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress   openoffice.org-java-common openoffice.org-math openoffice.org-writer poppler-utils python-glade2 python-gnome2   python-gnome2-desktop python-gnome2-dev python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration   python-uno python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras   python2.4-gtk2 qt3-dev-tools quick-lounge-applet realplay rhythmbox sbackup scim scim-gtk2-immodule   screensaver-default-images seahorse serpentine sound-juicer ssh-askpass-gnome streamtuner sun-java5-plugin synaptic   synce-multisync-plugin sysinfo t1-xfree86-nonfree tangerine-icon-theme tango-icon-theme-common thoggen timer-applet   tomboy totem-xine tsclient ttf-xfree86-nonfree ubuntu-artwork update-manager update-notifier vino x-window-system-core   xbase-clients xclock xfd xlogo xnetcardconfig xscreensaver-data xscreensaver-gl xterm yelp zenity 0 upgraded, 0 newly installed, 330 to remove and 5 not upgraded. Need to get 0B of archives. After unpacking 911MB disk space will be freed.
[code/]

That can't be right....

---

### Post by mlind on 2006-09-06
Try editing your post to use [code] tags instead..

---

### Post by misha680 on 2006-09-06
Which packages did you install? compiz? non-compiz? 386? amd?

Misha

> **starNIX said:**
> I have 3 broken packages on my system as well and running this:  

```

sudo apt-get install -f     Causes this:      

```

```

Reading package lists... Done Building dependency tree... Done Correcting dependencies...Done The following packages will be REMOVED   acidrip alacarte alltray at-spi automatix avidemux azureus baobab beagle beagle-backend-evolution bluez-cups bluez-pin   brltty-x11 bug-buddy bum cgwd cgwd-themes compiz compiz-core compiz-gnome compiz-plugins contact-lookup-applet cowbell   csm cupsys cupsys-driver-gutenprint dasher dbus-1-utils deskbar-applet dia-common dia-gnome eog etherape evince evolution   evolution-exchange evolution-plugins evolution-webcal exaile f-spot file-roller firefox firefox-gnome-support   firefox-themes-ubuntu fontconfig freeloader freespeak freevo freevo-media gaim gaim-encryption gaim-extendedprefs   gaim-guifications gaim-otr gcalctool gchangepass gconf-editor gdebi gdm gedit gimp gimp-print gimp-python gkrellm gksu   gnome-about gnome-accessibility-themes gnome-alsamixer gnome-app-install gnome-applets gnome-art gnome-bling-manager   gnome-btdownload gnome-compiz-manager gnome-control-center gnome-cups-manager gnome-games gnome-gpg gnome-icon-theme   gnome-keyring gnome-keyring-manager gnome-launch-box gnome-mag gnome-main-menu gnome-media gnome-netstatus-applet   gnome-nettool gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-schedule gnome-screensaver   gnome-session gnome-spell gnome-splashscreen-manager gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes   gnome-utils gnome-volume-manager gnopernicus gok gparted gpass greent gstreamer0.10-plugins-bad   gstreamer0.10-plugins-good gstreamer0.10-x gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-gtk   gstreamer0.8-lame gstreamer0.8-misc gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-swfdec   gstreamer0.8-vorbis gstreamer0.8-xvid gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast   gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95   gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap hal-device-manager hardinfo   hot-babe hplip hwdb-client inkscape k3b kcontrol kdebase-bin kdelibs-bin kdelibs4c2a kicker language-selector leafpad   libarts1c2a libatspi1.0-0 libavahi-qt3-1 libbonoboui2-0 libcairo-java libcairo-ruby libcairo2 libcairo2-dev   libdbus-qt-1-1c2 libedataserverui1.2-6 libeel2-2 libevolution-cil libexchange-storage1.2-1 libfontconfig1   libfontconfig1-dev libgail-common libgail-gnome-module libgail17 libgcj7-awt libgdk-pixbuf2-ruby libgdl-1-0   libgdl-1-common libgecko2.0-cil libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglade2-ruby libglade2.0-cil   libglademm-2.4-1c2a libgnome-desktop-2 libgnome-keyring-dev libgnome-keyring0 libgnome2-canvas-perl libgnome2-perl   libgnome2-wnck-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprintui2.2-0   libgnomeui-0 libgpod0 libgtk-java libgtk-jni libgtk2-gladexml-perl libgtk2-perl libgtk2-ruby libgtk2-trayicon-perl   libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtkmm-2.4-1c2a   libgtksourceview1.0-0 libgtksourceview2.0-cil libgtkspell0 libgucharmap4 libgutenprintui2-1 libk3b2 libkonq4   liblaunchpad-integration0 liblpint-bonobo0 libmetacity0 libmultisync-plugin-backup libmultisync-plugin-evolution   libnautilus-burn3 libnautilus-extension1 libnotify-bin libnotify1 libpanel-applet2-0 libpango1-ruby libpango1.0-0   libpango1.0-common libpoppler1 libpoppler1-glib libqt3-mt librsvg2-2 librsvg2-common libsexy1 libsexy2 libsvg-cairo   libswfdec0.3 libswt3.1-gtk-java libswt3.1-gtk-jni libtotem-plparser1 libvte2.0-cil libvte4 libwnck18 libxft-dev libxft2   listen mail-notification mencoder mencoder-386 metacity metacity-themes mozilla-browser mozilla-mplayer   mozilla-thunderbird mplayer-fonts mplayer-nogui multisync nautilus nautilus-cd-burner nautilus-sendto netapplet   notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core   openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress   openoffice.org-java-common openoffice.org-math openoffice.org-writer poppler-utils python-glade2 python-gnome2   python-gnome2-desktop python-gnome2-dev python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration   python-uno python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras   python2.4-gtk2 qt3-dev-tools quick-lounge-applet realplay rhythmbox sbackup scim scim-gtk2-immodule   screensaver-default-images seahorse serpentine sound-juicer ssh-askpass-gnome streamtuner sun-java5-plugin synaptic   synce-multisync-plugin sysinfo t1-xfree86-nonfree tangerine-icon-theme tango-icon-theme-common thoggen timer-applet   tomboy totem-xine tsclient ttf-xfree86-nonfree ubuntu-artwork update-manager update-notifier vino x-window-system-core   xbase-clients xclock xfd xlogo xnetcardconfig xscreensaver-data xscreensaver-gl xterm yelp zenity 0 upgraded, 0 newly installed, 330 to remove and 5 not upgraded. Need to get 0B of archives. After unpacking 911MB disk space will be freed.

```

That can't be right....

---

### Post by starNIX on 2006-09-06
What do you mean?  I do have compiz installed but these patches are what caused the broken packages on my system and now it won't let me revert back by forcing the dapper versions.

Any ideas?

---

### Post by jsully1 on 2006-09-07
AWESOME difference - just like to say thanks!

---

### Post by misha680 on 2006-09-14
Which font packages exactly did you install? As in where did you get them?

Also, try:

```
sudo aptitude -f install
```

it seems to work better fixing dependencies.

Misha

> **starNIX said:**
> What do you mean?  I do have compiz installed but these patches are what caused the broken packages on my system and now it won't let me revert back by forcing the dapper versions.

Any ideas?

---

### Post by Dralt on 2006-09-19
Is this still a good plan or is it now part of the standard distribution?

I would like to try it, but I don't like to branch my installation out of official updates.

---

### Post by chaosgeisterchen on 2006-09-20
Hy there. 

I always liked this type of font improval.

But there is one question yet to be solved:

How can I strictly force those packages not to be updated? I use aptitude via command line for all install and upgrading issues. But it overrides settings done by synaptics as the font improval vanishes after the next start of X. 

Thanks in advance for letting me know. I do only know **dpkg --set-selections >> EOF** afaik to give it the **hold**-attribute.

Greetings

chaosgeisterchen

---

### Post by hugmenot on 2006-09-20
Use aptitude hold <list whatever packages>
and aptitude unhold <list ...>

---

### Post by minkoo.seo@gmail.com on 2006-09-22
Thanks for the awesome patches. But, unfortunately, I got dependency problems. 

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  fglrx-control: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 is installed
  libfontconfig1: Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2-turnerpatch0 is installed
  libvte4: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 is installed
  python-vte: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

Does anybody know how to handle this problem?

---

### Post by chaosgeisterchen on 2006-09-22
> **hugmenot said:**
> Use aptitude hold <list whatever packages>
and aptitude unhold <list ...>

hey - thanks. But how do I manage to let it hold all packages containing 'libcairo' back? There must be any option :)

I am not yet a professional bash user :)

//edit

Well, all you have to do is try. I hope this is the right method

```
sudo aptitude hold `apt-cache pkgnames | grep libcairo` && sudo aptitude hold `apt-cache pkgnames | grep libxft` && sudo aptitude hold `apt-cache pkgnames | grep libfreetype`
```

---

### Post by hugmenot on 2006-09-22
> **chaosgeisterchen said:**
> 
Well, all you have to do is try. I hope this is the right method

```
sudo aptitude hold `apt-cache pkgnames | grep libcairo` && sudo aptitude hold `apt-cache pkgnames | grep libxft` && sudo aptitude hold `apt-cache pkgnames | grep libfreetype`
```

A bit overkill, but yeah, why not :)

What I use is aptitude search libcairo | grep "^i"

---

### Post by chaosgeisterchen on 2006-09-24
Hmh.. but your command provides unusable text output it seems..

---

### Post by smartov on 2006-09-25
Followed instructions of first post but did not uninstalled any packages. Result is very good. Thank you.

---

### Post by chaosgeisterchen on 2006-09-25
Is this improvement already suggested to be default in egdy I wonder...

It should be.. it leaves Windows ages behind.

---

### Post by Neo40 on 2006-09-25
Is it possible to apply this HOWTO to another distro like Zenwalk? If yes, how can I do that?
Thanks

---

### Post by cvacubo on 2006-09-28
After that HOWTO my fonts became ideal, that always did not suffice me.

But there is a question how to achieve such fonts in Edgy?

Thanks a lot.

---

### Post by hugmenot on 2006-09-28
> **cvacubo said:**
> But there is a question how to achieve such fonts in Edgy?

There is a repo for Edgy packages. Instructions in this thread: [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)

I see some differences in rendering between Dapper and Edgy. It would be interesting to know what others think about it.

---

### Post by Entheogen on 2006-10-02
Guys, is there patch like this for Debian Sarge?

---

### Post by mlind on 2006-10-02
> **Entheogen said:**
> Guys, is there patch like this for Debian Sarge?

What versions of libcairo2, libxft2 (and libfreetype6) does Sarge use if any?

---

### Post by brucevangeorge on 2006-10-02
What's the difference between full and slight hinting?

---

### Post by dagnabit dang doohickey on 2006-10-02
A few months ago I was looking for a solution to the ugly fonts problem. I tried a bunch of things; the first was installing the TrueType core fonts package, and after that, an assortment of tweaks that didn't solve the problem. I undid all the tweaks, kept the core fonts and patiently searched for a solution in my free time.

If I would have stumbled upon this thread's solution it would have surely been tried, but I didn't, I stumbled upon [this]("http://www.michael-and-mary.net/?q=node/440") [michael-and-mary.net] and haven't searched for a solution since.

I don't know how the results compare to the solution in this thread, but I'm satisfied enough to not even find out.

---

### Post by hugmenot on 2006-10-02
> **brucevangeorge said:**
> What's the difference between full and slight hinting?

Full tries more aggressively to force letters onto the pixel grid. Slight will leave more gray pixels that represent partly filled pixels (only in antilaias mode of course). For monochrome rendering only strong hinting will produce intelligible characters.

---

### Post by hugmenot on 2006-10-02
> **dagnabit dang doohickey said:**
>  [this]("http://www.michael-and-mary.net/?q=node/440") [michael-and-mary.net] and haven't searched for a solution since.

I don't know how the results compare to the solution in this thread, but I'm satisfied enough to not even find out.

I&#8217;d love to see this but the site doesn&#8217;t load.

---

### Post by hugmenot on 2006-10-02
> **chaosgeisterchen said:**
> Hmh.. but your command provides unusable text output it seems..

No. I use aptitude search ... "aha" ... aptitude hold result. I was unclear, scuse.

---

### Post by dagnabit dang doohickey on 2006-10-02
> **hugmenot said:**
> I’d love to see this but the site doesn’t load.
It's loading for me...strange. In any case, here's the short and sweet of the [post]("http://www.michael-and-mary.net/?q=node/440") at michael-and-mary.net:

> **A solution to bad fonts on Linux/BSD**

For all those who have bad fonts on Linux/BSD, the following might be the solution...(Works on LCD monitors and it worked for me)

Save the following[*see attached file below*] as .fonts.conf in your home directory (e.g. /home/michael). Logout of your desktop environement and log back in. You should notice much better fonts.

I found it when I searched for how to make my fonts look better on my LCD monitor. I post it, since I feel it might help many of you who want to make fonts on Linux/BSD look better.

- Site Admin

---

### Post by Tares on 2006-10-02
I've tried to do this HowTo, but didn't work for me. Something was wrong with the packages I should install.

Anyway, I've wanted to ask if there is a way to make the fonts look like in XP ? like there -> [linux-xp]("http://www.linux-xp.com/gallery/"). 

I've tried few howtos, but didn't worked. I have all the MS fonts I need (Tahoma+Verdana also).

---

### Post by hugmenot on 2006-10-02
> **dagnabit dang doohickey said:**
> It's loading for me...strange. In any case, here's the short and sweet of the [post]("http://www.michael-and-mary.net/?q=node/440") at michael-and-mary.net:

That doesn&#8217;t look especially remarkable to me. He activates the autohinter, full hinting and remaps Helvetica. What does it look like? Screenshots?

At any rate you might try out what is presented here and compare. It&#8217;s not that intrusive/difficult.

---

### Post by hugmenot on 2006-10-02
> **Tares said:**
> I've tried to do this HowTo, but didn't work for me. Something was wrong with the packages I should install.

Anyway, I've wanted to ask if there is a way to make the fonts look like in XP ? like there -> [linux-xp]("http://www.linux-xp.com/gallery/"). 

I've tried few howtos, but didn't worked. I have all the MS fonts I need (Tahoma+Verdana also).

Uh..., switch to monochrome, full hinting, bytecode interpretation and see what happens. Nothing for my eyes.

Reminds me of the olde W95 days.

---

### Post by Entheogen on 2006-10-02
> **mlind said:**
> What versions of libcairo2, libxft2 (and libfreetype6) does Sarge use if any?

there is no debian package for libcairo. Debian sarge uses libxft2 2.1.7-2 and libfreetype6 2.1.7-2.4.
Can I somewhere download source packages for these libs and compile it (if they are too old)? Is there any solution for me :)

---

### Post by Tares on 2006-10-02
> **hugmenot said:**
> Uh..., switch to monochrome, full hinting, bytecode interpretation and see what happens. Nothing for my eyes.

Reminds me of the olde W95 days.

Done that, effect is terrible -_-

---

### Post by dagnabit dang doohickey on 2006-10-02
> **hugmenot said:**
> That doesn’t look especially remarkable to me. He activates the autohinter, full hinting and remaps Helvetica. What does it look like? Screenshots?

At any rate you might try out what is presented here and compare. It’s not that intrusive/difficult.

Here are a couple of screenshots.

---

### Post by hugmenot on 2006-10-03
This is how that looks on my screen. I couldn&#8217;t really match you font settings. The Serif is smaller.

---

### Post by jrjazzman on 2006-10-05
First, thanks to the linux community in general, and specifically the people who developed this patch.  I'm a new linux user.  I followed the instrcutions by the OP and, finally, I can run linux without getting a headache after a hour.  Given how critically important good font rendering is for me, and presumably many others, there are some things I just don't understand about linux.  

Why has it taken so long to get font rendering that is on par with other operating systems?  Technology, patent issues?

Why don't Dapper and Edgy come with decent font rendering?  Many linux users who want good fonts don't have much business hacking around with system libraries.  I'm not sure I do.. yet.

Now that I've got these packages locked down, preventing updates to them, it seems that sooner or later something's going to stop working.. new packages will require new versions of the locked packages.  Am I signing up for having to patch source code for the foreseeable future?

---

### Post by ferd on 2006-10-05
This does not work because the files are not found after downloading.](*,)

---

### Post by hugmenot on 2006-10-05
> **jrjazzman said:**
> Why has it taken so long to get font rendering that is on par with other operating systems?  Technology, patent issues?

The latter. Microsoft ownz &#8217;em.
> **jrjazzman said:**
> 
Why don't Dapper and Edgy come with decent font rendering?  Many linux users who want good fonts don't have much business hacking around with system libraries.  I'm not sure I do.. yet.
The improvement patches have only recently been developed and around the same time the developer made clear that patents will prevent inclusion.

---

### Post by chiklit on 2006-10-16
> **hugmenot said:**
> The latter. Microsoft ownz ’em.

Does that mean Apple is paying protection money to Microsoft? I haven't heard of them getting sued for nice looking fonts.

---

### Post by jrjazzman on 2006-10-16
I wondered this as well.  Since Microsoft uses apple's truetype, they probably have some cross-licensing agreements.  

I just think it is insane that Microsoft has essentially prevented everyone from rendering fonts well, excluding those whom they authorize (apple?).

> **chiklit said:**
> Does that mean Apple is paying protection money to Microsoft? I haven't heard of them getting sued for nice looking fonts.

---

### Post by dagnabit dang doohickey on 2006-10-16
> **jrjazzman said:**
> Since Microsoft uses apple's truetype, they probably have some cross-licensing agreements.

Yes, Apple and MS made a cross-licensing agreement on the TrueType specification. This was done to get past Adobe's grip on the font market with it's PostScript License.

The TrueType fonts created by each company are, however, owned by their respective creator.

---

### Post by ssarkarhyd on 2006-10-17
WORKS LIKE A CHARM.

> **Pausanias said:**
> This is just a summary of [a previous thread](http://www.ubuntuforums.org/showthread.php?t=178737) on improving the way your fonts look in X11. Many people have noticed significant improvment in font rendering with these patches. You might wish to check out these [before](http://www.ubuntuforums.org/attachment.php?attachmentid=9666&d=1147972226) and [after](http://www.ubuntuforums.org/attachment.php?attachmentid=9667&d=1147972226) screenshots from that thread.  

Other people wrote the patches; I am just condensing the various instructions that were dispersed throughout the previous thread, with some more detailed instructions. The algorithms in these patches may or may not be covered by Microsoft's ClearType patents; check with [this guy](http://turnerdavid.neuf.fr/freetype/patches/font-patches.html) if this is a concern for you. Special thanks go to jcooper, hugmenot, mannheim, and of course David Turner who wrote the patches to begin with. 

EDIT: The instructions have been updated so as not to conflict with certain people's setups. Please report any problems on this thread.

```

sudo apt-get install libcairo2-dev libxft-dev libfontconfig1-dev
sudo apt-get remove libcairo2-dev libxft-dev
mkdir fontpatches
cd fontpatches
(download the three message attachments here)
unzip *.zip
gunzip *gz
sudo cp local.conf /etc/fonts
sudo dpkg -i *deb

```

Answer yes to all questions. Then reboot the computer. When Ubuntu comes back, go to System->Preferences->Font. Make sure that subpixel smoothing is on. Then click on details. Choose either Slight or Full Hinting, or another value if you prefer. I find that the rendering works very well with the Bitstream Vera Sans font. If you find a better font you can post it here.

To prevent future updates from overwriting the patches, load synaptic. On the left hand side, click on "Installed (local or obsolete)." Select all packages containing the words libcairo, libxft, and libfreetype. Under the package menu, select lock version. To undo the version lock, click on the word "Pinned" on the left hand side. Select all package containing the words libcairo, libxft, and libfreetype. Under the package menu, uncheck lock version. 

To uninstall the packages, go again to the "Installed (local or obsolete)" section in synaptic. Select each package one at a time. Under the package menu, select "force version." When the menu comes, select the version that has the text "(dapper)" at the end of it. When you're done doing this for all the packages, click on apply. Then "sudo rm /etc/fonts/local.conf." Reboot to get the vanilla font rendering back.

---

### Post by dasnk on 2006-10-23
For my CRT monitor I just 'sudo gedit /etc/fonts/local.conf' and I added the following to the file and saved it:

```
    <match target="font">
        <test compare="more" name="size" qual="any" >
            <double>0</double>
        </test>
        <test compare="less" name="size" qual="any" >
            <double>72</double>
        </test>
        <edit mode="assign" name="antialias" >
            <bool>false</bool>
        </edit>
    </match>

```

I have font rendering set to "monochrome" and smoothing set to "none", hinting set to "full".

Used with the apprpriate windows fonts it looks pretty good.
[Source](http://www.convexhull.com/mandrake_fonts.html)

Edit: In light of hugemont's following post I removed a reference to installing the patches.

---

### Post by hugmenot on 2006-10-23
The packages do absolutely nothing to monochrome rendering.

---

### Post by ZeeG on 2006-10-26
I'm trying this on ubuntu 6.10 (Edgy Eft) and having an error message when I install the deb packages.

sudo dpkg -i *deb

after doing this command, I'm getting following message. 

```

(Reading database ... 90737 files and directories currently installed.)
Preparing to replace libcairo2 1.0.4-0ubuntu1patched (using libcairo2_1.0.4-0ubuntu1patched_i386.deb) ...
Unpacking replacement libcairo2 ...
Preparing to replace libcairo2-dev 1.0.4-0ubuntu1patched (using libcairo2-dev_1.0.4-0ubuntu1patched_i386.deb) ...
Unpacking replacement libcairo2-dev ...
Preparing to replace libfreetype6 2.1.10-1ubuntu2-turnerpatch0 (using libfreetype6_2.1.10-1ubuntu2-turnerpatch0_i386.deb) ...
Unpacking replacement libfreetype6 ...
Preparing to replace libfreetype6-dev 2.1.10-1ubuntu2-turnerpatch0 (using libfreetype6-dev_2.1.10-1ubuntu2-turnerpatch0_i386.deb) ...
Unpacking replacement libfreetype6-dev ...
Preparing to replace libxft2 2.1.8.2-0ubuntu2patched (using libxft2_2.1.8.2-0ubuntu2patched_i386.deb) ...
Unpacking replacement libxft2 ...
dpkg: regarding libxft-dev_2.1.8.2-0ubuntu2patched_i386.deb containing libxft-dev:
 x11-common conflicts with libxft-dev (<= 2.1.8.2-5)
  libxft-dev (version 2.1.8.2-0ubuntu2patched) is to be installed.
dpkg: error processing libxft-dev_2.1.8.2-0ubuntu2patched_i386.deb (--install):
 conflicting packages - not installing libxft-dev
Setting up libfreetype6 (2.1.10-1ubuntu2-turnerpatch0) ...

Setting up libfreetype6-dev (2.1.10-1ubuntu2-turnerpatch0) ...

Setting up libxft2 (2.1.8.2-0ubuntu2patched) ...
Setting up libcairo2 (1.0.4-0ubuntu1patched) ...

Setting up libcairo2-dev (1.0.4-0ubuntu1patched) ...
Errors were encountered while processing:
 libxft-dev_2.1.8.2-0ubuntu2patched_i386.deb

```

Could anybody tell me what I was doing wrong :(

---

### Post by hugmenot on 2006-10-26
Use those ones: [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)

---

### Post by wilberfan64 on 2006-10-27
> **defuseme2k said:**
> I'm running amd64, sorry to be really noob, but should I also extract the fontpatched.zip along with the two amd64 packages?  I just happened to notice that the fontpatched.zip has 32bit deb's, and I didn't know if those were necessary?

I did it without, and I couldn't tell a difference =X.  Especially in firefox, when rendering hardocp.com for instance it looks like shite.

I can't see that anyone has responded to this yet?   I have the same question.   

I skipped the 32bit deb's, only installed the 64bit ones...  I never got prompted for any "y" or "n" questions...  

However, I AM being told by the update manager that there are updates available for some libcairo and libxft stuff--so maybe it worked?

[edit] Things DO seem to look better (I think)?   Is there a way to tell for sure that the install(s) went properly and I'm getting the benefits?

---

### Post by ZeeG on 2006-10-27
> **hugmenot said:**
> Use those ones: [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)

Thanks for your reply.
Ok. maybe it is a stupid question, but I'm not good at linux especially this debian packages, so I cannot figure out how to install the packages in the mllnd's repository.

I added following two lines in /etc/apt/sources.list

```
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts
```

and then what am I supposed to do? should I run following commands?

sudo apt-get install libcairo2-dev libxft-dev libfontconfig1-dev

If I do so, isn't it supposed to get the binaries from the ubuntu official repository not mllnd's one?

Please help me more :D Thanks.

---

### Post by hugmenot on 2006-10-27
> **ZeeG said:**
> Thanks for your reply.
Ok. maybe it is a stupid question, but I'm not good at linux especially this debian packages, so I cannot figure out how to install the packages in the mllnd's repository.

I added following two lines in /etc/apt/sources.list

```
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts
```


good

> 
and then what am I supposed to do? should I run following commands?

sudo apt-get install libcairo2-dev libxft-dev libfontconfig1-dev

If I do so, isn't it supposed to get the binaries from the ubuntu official repository not mllnd's one?

Well, dist-upgrading should be enough, because the packages have a higher version number than the packages in the official edgy repos. So the &#8220;newer&#8221; packages will override them.

---

### Post by Ruth Lazkoz on 2006-12-18
Hi,

I get the following error

ruth@ruth-desktop:/usr/local/src/fontpatches$ sudo dpkg -i *deb
(Leyendo la base de datos ...  
190073 ficheros y directorios instalados actualmente.)
Preparando para reemplazar libcairo2 1.0.4-0turnerpatch0 (usando libcairo2_1.0.4-0turnerpatch0_amd64.deb) ...
Desempaquetando el reemplazo de libcairo2 ...
Preparando para reemplazar libcairo2-dev 1.0.4-0turnerpatch0 (usando libcairo2-dev_1.0.4-0turnerpatch0_amd64.deb) ...
Desempaquetando el reemplazo de libcairo2-dev ...
Preparando para reemplazar libcairo2-doc 1.0.4-0turnerpatch0 (usando libcairo2-doc_1.0.4-0turnerpatch0_all.deb) ...
Desempaquetando el reemplazo de libcairo2-doc ...
Preparando para reemplazar libxft2 2.1.8.2-0turnerpatch0 (usando libxft2_2.1.8.2-0turnerpatch0_amd64.deb) ...
Desempaquetando el reemplazo de libxft2 ...
Preparando para reemplazar libxft2-dbg 2.1.8.2-0turnerpatch0 (usando libxft2-dbg_2.1.8.2-0turnerpatch0_amd64.deb) ...
Desempaquetando el reemplazo de libxft2-dbg ...
dpkg: acerca de libxft-dev_2.1.8.2-0turnerpatch0_amd64.deb que contiene libxft-dev:
 x11-common conflicts with libxft-dev (<= 2.1.8.2-5)
  libxft-dev (versión 2.1.8.2-0turnerpatch0) va a ser instalado.
dpkg: error al procesar libxft-dev_2.1.8.2-0turnerpatch0_amd64.deb (--install):
 paquetes en conflicto - no se instalará libxft-dev
Configurando libcairo2 (1.0.4-0turnerpatch0) ...

Configurando libcairo2-dev (1.0.4-0turnerpatch0) ...
Configurando libcairo2-doc (1.0.4-0turnerpatch0) ...

Configurando libxft2 (2.1.8.2-0turnerpatch0) ...
Configurando libxft2-dbg (2.1.8.2-0turnerpatch0) ...
Se encontraron errores al procesar:
 libxft-dev_2.1.8.2-0turnerpatch0_amd64.deb

Hope you can guess what is going on despite the spanish. Can you help me?

Regards,

Ruth

---

### Post by hugmenot on 2006-12-18
EDIT: if you run 6.10 Edgy Eft (and it seems you do) then use those instructions instead:
[http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)

The results will be a lot better



> **Ruth Lazkoz said:**
> Hi,
dpkg: acerca de libxft-dev_2.1.8.2-0turnerpatch0_amd64.deb que contiene libxft-dev:
 x11-common conflicts with libxft-dev (<= 2.1.8.2-5)
  libxft-dev (versión 2.1.8.2-0turnerpatch0) va a ser instalado.
dpkg: error al procesar libxft-dev_2.1.8.2-0turnerpatch0_amd64.deb (--install):


If you never build/compile stuff yourself you can get rid of the -dev packages and have no conflicts anymore. I.e., delete the -dev packages (rm *-dev_*.deb) and remove the ones that were already installed (apt-get remove libxft-dev). You shouldn&#8217;t need those under the above condition.

---

### Post by Ruth Lazkoz on 2006-12-18
Hi,

I did what you say and also removed the packages for the i386 architechture, because they gave me trouble.

Everything seemed to work, but I never got prompted any questions as it says it must happen in the firts message of this thread, so I wonder if I have really done anything. I feel no improvement.

The alternative of using the instructions is 
[http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)
is not valid because there are no amd64 binaries.

Regards.

Ruth

---

### Post by lukejduncan on 2007-11-13
I'm new to ubuntu and am learning a lot through trial and error, and I've definitely made an error.  When I went to install the deb files there was an error (not sure what it said and don't know if there are log files somewhere) and now ubuntu won't load.  Does anyone know a quick way to restore the font rendering software to it's former state from recovery mode?

Thanks

---

### Post by hugmenot on 2007-11-14
Which is your Ubuntu version? If you are really new to Ubuntu and have the most recent version 7.10, then intalling the old packages herein would give you no gain whatsoever.

Could you run these commands on the command line to see what&#8217;s going on?

```
apt-cache policy libfreetype6 libcairo2 libxft2
ls -l /etc/fonts/* ~/.fonts.conf
```

---

