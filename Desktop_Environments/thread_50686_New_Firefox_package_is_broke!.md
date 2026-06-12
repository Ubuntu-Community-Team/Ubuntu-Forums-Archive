---
title: "New Firefox package is broke!"
date: 2005-07-21
forum: Desktop Environments
---

### Post by martijntje on 2005-07-21
I've just installed the new Firefox and Firefox GNOME Support packages.

Now, i can't close tabs with <Ctrl>+<W> anymore, since this closes the entire window.

What can i do about that?

Edit: You can't close single tabs anymore. The 'close this tab' x at the right now closes the entire window too, instead of the single tab.

---

### Post by martijntje on 2005-07-21
It seems you can't download from Newzbin with this new package too. It just stops after a while of loading.

The normal mozilla does this wonderfully.

---

### Post by Ethan on 2005-07-21
[QUOTE=martijntje]It seems you can't download from Newzbin with this new package too. It just stops after a while of loading.

The normal mozilla does this wonderfully.[/QUOTE]
 I am just experiencing the exact same problems... :(

---

### Post by trinux on 2005-07-21
[QUOTE=martijntje]It seems you can't download from Newzbin with this new package too. It just stops after a while of loading.

The normal mozilla does this wonderfully.[/QUOTE]

I also! :(

---

### Post by bugmenot on 2005-07-21
Extention and theme are also broken.
Firefox crash (Segmentation Fault) ...

---

### Post by XenoCyber on 2005-07-21
Not only did i notice the above bugs but after firefox closes twice It wont open untill I goto the synaptic package manager and have it re-install the firefox packages.

does any one know how to downgrade the packages untill this is fixed ?

XenoCyber

---

### Post by martijntje on 2005-07-21
[QUOTE=XenoCyber]Not only did i notice the above bugs but after firefox closes twice It wont open untill I goto the synaptic package manager and have it re-install the firefox packages.

does any one know how to downgrade the packages untill this is fixed ?

XenoCyber[/QUOTE]
 Really? I haven't had that problem. Must've closed it like 50 times today trying to close the current tab.

I would be interested in downgrading as well BTW.

---

### Post by lupo on 2005-07-21
I've exactly the same problem!
Switching from one tab to an other causes firefox to crash with a Segmentation fault...
Is there an easy way to downgrade?
Greets
  Lupo

---

### Post by Luggy on 2005-07-21
```
paul@ubuntu:~$ firefox
*** loading the extensions datasource
Segmentation fault
``` 
:(

---

### Post by lothrids on 2005-07-21
I am not having any trouble loading firefox and I can switch from tab to tab with no problem but my extensions are pretty much busted. Any idea how soon we can expect a fix for this?

---

### Post by wolfpakz on 2005-07-21
I've also had problems with the most recent upgrade. After the upgrade firefox periodically exits with a segfault. I downgraded firefox back to the version I had installed before. In case any one is interested, the following shell command will downgrade firefox:

sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

-WolfpakZ

---

### Post by veritas366 on 2005-07-21
I can't even click on a tab without Firefox closing on me.  How on earth did such grievous errors make it into an update.  Please if anyone knows how to "unupdate" let us know!

---

### Post by zalun on 2005-07-21
[QUOTE=XenoCyber]does any one know how to downgrade the packages untill this is fixed ?
XenoCyber[/QUOTE]
I've the polish version of it, so the menu may be other than you have.

Select the package (mozilla firefox) choose Packet from the menu and after that Choose version.

---

### Post by DancingSun on 2005-07-21
Well, I can't even launch Firefox!  No error messege box.  When lauching via the terminal it just says "Segmentation fault".

---

### Post by XenoCyber on 2005-07-21
Thanks I was able to downgrade successfully
and now all is fine untill they fix the package

XenoCyber

---

### Post by XenoCyber on 2005-07-21
[QUOTE=DancingSun]Well, I can't even launch Firefox!  No error messege box.  When lauching via the terminal it just says "Segmentation fault".[/QUOTE]

1. Reinstall the Packages VIA synaptic fixes it for a bit. Or you could downgrade as i did and not get upset every time it crashes

---

### Post by jdong on 2005-07-21
What version?

---

### Post by Luggy on 2005-07-21
[QUOTE=jdong]What version?[/QUOTE]

My segmentation error was in version 1.0.2 (well version 1.0.2 with the version number not changed to 1.0.4)

---

### Post by jdong on 2005-07-21
ok, because I've heard this a bit in the Backports forum too, but it was traced to problems in a k ernel update.

---

### Post by XenoCyber on 2005-07-21
[QUOTE=jdong]What version?[/QUOTE]

The Affected Packages Are:
mozila-firefox Version 1.0.2-0ubuntu5.4
and the dependency
mozila-firefox-gnome-support Version 1.0.2-0ubuntu5.4

both were software updates aailable this morning when i got in and i installed both.

---

### Post by jdong on 2005-07-21
I would file a bug report with bugzilla.ubuntu.com about this.

---

### Post by atilasendil on 2005-07-21
[QUOTE=wolfpakz]I've also had problems with the most recent upgrade. After the upgrade firefox periodically exits with a segfault. I downgraded firefox back to the version I had installed before. In case any one is interested, the following shell command will downgrade firefox:

sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

-WolfpakZ[/QUOTE]
 thanks a lot :-)

---

### Post by AndyAWS on 2005-07-21
If the new package was built from Firefox 1.05 (and I assume that's what 1.02-ubuntu***5*** means, then wait for the next version. 1.05 has serious problems and 1.06 is now out.
[http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151](http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151)

---

### Post by AndyAWS on 2005-07-21
Actually I think I'm wrong on the version, I can't figure out exactly what Ubuntu's official versioning system means.

I'm using the latest Backport of firefox 1.04 from ubp and everything works fine.

---

### Post by brian g on 2005-07-21
[QUOTE=AndyAWS]If the new package was built from Firefox 1.05 (and I assume that's what 1.02-ubuntu***5*** means, then wait for the next version. 1.05 has serious problems and 1.06 is now out.
[http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151](http://www.informationweek.com/story/showArticle.jhtml?articleID=166401151)[/QUOTE]i've read that Mozilla Firefox 1.0.5 is really broken and that 1.0.6 will be out soon.

as far as ubuntu versions i'm using Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.8) Gecko/20050608 Firefox/1.0 (Ubuntu package 1.0.4) with no problems

---

### Post by spd106 on 2005-07-21
I have updated to the latest version of firefox in the official repos through synaptic ie ubuntu5.4 and have had no problems yet.

Except for the mozilla website won't let me access the extensions page. It says it recognises that I have the ubuntu version, but that it can't tell whether it's patched or not. It then directs you to the bug filed with ubuntu 10681.

I don't have any extensions in firefox yet, so that might be why I'm relatively unaffected by the version upgrade.

---

### Post by martijntje on 2005-07-21
[QUOTE=spd106]I have updated to the latest version of firefox in the official repos through synaptic ie ubuntu5.4 and have had no problems yet.

Except for the mozilla website won't let me access the extensions page. It says it recognises that I have the ubuntu version, but that it can't tell whether it's patched or not. It then directs you to the bug filed with ubuntu 10681.

I don't have any extensions in firefox yet, so that might be why I'm relatively unaffected by the version upgrade.[/QUOTE]
 No, this has nothing to do with the latest release.

I've had that problem for ages. The bug-report has a way around the problem, which works just fine. :)

---

### Post by astoltz on 2005-07-21
I upgraded this morning also and have had no problems.  Tabs work as expected, Firefox opens and closes on command, no crashes.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050720 Firefox/1.0.4 (Ubuntu package 1.0.2 MFSA2005-56)

---

### Post by bob k on 2005-07-21
I am also having problems, If I open a second web page from history or bookmarks, firefox crashes with no error message, and shuts down.

---

### Post by skylark on 2005-07-21
Just upgraded 5 minutes ago on an AMD64 box (and also upgraded firefox running in 32bit chroot mode on the same box) - both crash sometimes when switching/closing tabs, especially if some of the tabs are still loading content.

Will try to downgrade...

Edit: thanks to wolfpakz the downgrade worked and the problem is now gone.

PS: would be nice to have a way to roll back packages more easily... something like "sudo aptitude rollback firefox" or something.

---

### Post by Luggy on 2005-07-22
[QUOTE=skylark]Just upgraded 5 minutes ago on an AMD64 box (and also upgraded firefox running in 32bit chroot mode on the same box) - both crash sometimes when switching/closing tabs, especially if some of the tabs are still loading content.

Will try to downgrade...

Edit: thanks to wolfpakz the downgrade worked and the problem is now gone.

PS: would be nice to have a way to roll back packages more easily... something like "sudo aptitude rollback firefox" or something.[/QUOTE]

yeah that's a really good Idea, especially for newer updates.

---

### Post by the_it on 2005-07-22
[QUOTE=lupo]I've exactly the same problem!
Switching from one tab to an other causes firefox to crash with a Segmentation fault...
Is there an easy way to downgrade?
Greets
  Lupo[/QUOTE]
Yup! Same prob for me.  I thought it might have had something to do with me installing backports, but when I looked at it again, my firefox was from ubuntu.

The extensions I have installed include: session-saver, mouse gestures, download manager, flashgot, etc etc.

I've tried uninstalling the firefox package, then installing, no help.  I've tried uninstalling completely then reinstalling, same prob.  I think it's the package.  I'm using konqueror right now, and I might even get the gecko renderer for it.

---

### Post by mhael on 2005-07-22
I had the same problem - firefiox became extremely unstable after last update.
Crashes randomly on tab switching, hostory using, etc..

Uninstalling extentions (i used "MediaPlayerConnectivity") fixed the problem.
So far I haven't experienced a single crash.

It seems that last firefox update broke extention handling. Besides that, it's pretty stable (If you can live without extentions).

---

### Post by jamyskis on 2005-07-22
Probably sick of hearing this, but I'm having this problem too - both on my work and home computers. The Google toolbar no longer works either. Closing a tab or entering something into the toolbar bombs out Firefox with a "Segmentation fault"

---

### Post by mongolito404 on 2005-07-22
Me too...

(In my case) It seems related to extensions. I manually removed the "extensions" and all extensions related folder in my profile folder and now firefox seems to works fine (without any extensions).

---

### Post by peter07 on 2005-07-22
I've got bigger problem. New firefox version ( I think this couses my problems - but it could be also other security updates form ubuntu.com ) sometimes freezes Gnome. For few minutes I can't do anything - only firefox ( or other application which is running ) window is working then. I'm using standard ubuntu updates and I have no idea how to repair this bug.

---

### Post by Ghaleon on 2005-07-22
I upgraded about 20 minutes ago, and I've had no problems at all. Though, that could be because I don't use any extensions. >.>

---

### Post by peter07 on 2005-07-22
[QUOTE=Ghaleon]I upgraded about 20 minutes ago, and I've had no problems at all. Though, that could be because I don't use any extensions. >.>[/QUOTE]
 Firefox without flashgot and adblock - no thanks. Extensions couses problems ??
When the correct version will be release ??

---

### Post by atf487 on 2005-07-22
i havent even had the option of upgrading, im still using 1.0.4. probably something to do with the backports.

---

### Post by bpilgrim1979 on 2005-07-22
[QUOTE=wolfpakz]In case any one is interested, the following shell command will downgrade firefox:

sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

-WolfpakZ[/QUOTE]

Thanks!  That's what I was looking for.  I'll try it.

---

### Post by peter07 on 2005-07-23
[QUOTE=atf487]i havent even had the option of upgrading, im still using 1.0.4. probably something to do with the backports.[/QUOTE]
 I wasn't using backports - only security updates.
> 
Originally Posted by wolfpakz
In case any one is interested, the following shell command will downgrade firefox:

sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

-WolfpakZ


Thanks! That's what I was looking for. I'll try it.


What was the effect ??

---

### Post by AgenT on 2005-07-23
The security update uses the "broken" code from a newer Firefox because it was the only version available that fixed security issues.

To developers:

**REQUEST OF ANOTHER FIREFOX UPDATE (based on the new 1.0.6)**:
(taken from firefox.org)

 >  What's New 1.0.6
Firefox 1.0.6 is a stability update.  We recommend that users upgrade to this latest version.

           Here's what's new in Firefox 1.0.6:

         



[list]
[*]Restore API compatibility for extensions and web applications that did not work in Firefox 1.0.5.
[/list] 
The "**Restore API compatibility for extensions and web applications**" should fix the current major breakage in Firefox.

---

### Post by lothrids on 2005-07-23
[QUOTE=wolfpakz]I've also had problems with the most recent upgrade. After the upgrade firefox periodically exits with a segfault. I downgraded firefox back to the version I had installed before. In case any one is interested, the following shell command will downgrade firefox:

sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

-WolfpakZ[/QUOTE]

Dude that worked great. Thatnks!!!!

---

### Post by obvious_ron on 2005-07-23
[QUOTE=wolfpakz]I've also had problems with the most recent upgrade. After the upgrade firefox periodically exits with a segfault. I downgraded firefox back to the version I had installed before. In case any one is interested, the following shell command will downgrade firefox:

sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

-WolfpakZ[/QUOTE]

[FONT=Georgia]Thanks very much for this.[/FONT]   \\:D/

[FONT=Georgia]I'm a Linux newbie and just installed Ubuntu this morning as a dual boot with Windows XP Professional.  It's my first ever Linux installation.  I automatically installed the updates right after installation.[/FONT]

---

### Post by jdong on 2005-07-23
[QUOTE=AgenT]The security update uses the "broken" code from a newer Firefox because it was the only version available that fixed security issues.

To developers:

**REQUEST OF ANOTHER FIREFOX UPDATE (based on the new 1.0.6)**:
(taken from firefox.org)

  
The "**Restore API compatibility for extensions and web applications**" should fix the current major breakage in Firefox.[/QUOTE]

Unfortunately, that's no good. We've already packaged 1.0.6 from Breezy here @ backports, and it's no good, either.

```

------------------------------------------------------------------------
r492 | Mez | 2005-07-23 16:28:42 -0400 (Sat, 23 Jul 2005) | 2 lines
Changed paths:
   D /dists/hoary-backports-staging/main/binary-i386/firefox-dev_1.0.6-1ubuntu1~5.04ubp1_i386.deb
   D /dists/hoary-backports-staging/main/binary-i386/firefox-dom-inspector_1.0.6-1ubuntu1~5.04ubp1_i386.deb
   D /dists/hoary-backports-staging/main/binary-i386/firefox-gnome-support_1.0.6-1ubuntu1~5.04ubp1_i386.deb

Pulled Firefox, see http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html for more details

------------------------------------------------------------------------
r491 | jdong | 2005-07-21 18:28:21 -0400 (Thu, 21 Jul 2005) | 2 lines
Changed paths:
   A /dists/hoary-backports-staging/main/binary-i386/firefox-dev_1.0.6-1ubuntu1~5.04ubp1_i386.deb
   A /dists/hoary-backports-staging/main/binary-i386/firefox-dom-inspector_1.0.6-1ubuntu1~5.04ubp1_i386.deb
   A /dists/hoary-backports-staging/main/binary-i386/firefox-gnome-support_1.0.6-1ubuntu1~5.04ubp1_i386.deb
   A /dists/hoary-backports-staging/main/binary-i386/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb
   A /dists/hoary-backports-staging/main/binary-i386/mozilla-firefox-dev_1.0.6-1ubuntu1~5.04ubp1_all.deb
   A /dists/hoary-backports-staging/main/binary-i386/mozilla-firefox-dom-inspector_1.0.6-1ubuntu1~5.04ubp1_all.deb
   A /dists/hoary-backports-staging/main/binary-i386/mozilla-firefox-gnome-support_1.0.6-1ubuntu1~5.04ubp1_all.deb
   A /dists/hoary-backports-staging/main/binary-i386/mozilla-firefox_1.0.6-1ubuntu1~5.04ubp1_all.deb

Autopackaged by ubp-build.py
 Command was: /usr/local/bin/ubp-build.py firefox 
------------------------------------------------------------------------
```

---

### Post by AgenT on 2005-07-23
[QUOTE=jdong]Unfortunately, that's no good. We've already packaged 1.0.6 from Breezy here @ backports, and it's no good, either.
[/QUOTE]

So I guess there is nothing you guys can do, eh? Except maybe revert back to the old version that has security problems. Although that in itself is not a good idea.

Bad move by the Firefox team. Either that, or those that coded the extensions did not follow standards and had their applications break when the Firefox team updated their browser. The extension coders could have used shortcuts for example. Sort of like those annoying web coders that code for specific browsers.


 Glad to see the Ubuntu team jump on this problem and not trying to hide it. Good job guys, we know its not your fault! ;)

---

### Post by Oceola on 2005-07-23
I'm running the 1.06 Firefox from the Mozilla site I downloaded yesterday afternoon.
Although the install did not remove the 1.02 version which came with the Ubuntu discs, it seems to be fairly stable. I've downloaded several packages with it and have found no visible issues other than the install and it's missing the "make Sure Firefox is your default browser." toggle.

I have had the "System Monitor" crash several times as it seems someone is trying to access through the games servers. One of the reasons I'm looking for the files which takes the "AT" string to shut down the games side of the modem.

I also don't see some of the files like /etc/modules/ and I had a hard time working out the dial up setup.

 :-#

---

### Post by jdong on 2005-07-23
[QUOTE=AgenT]So I guess there is nothing you guys can do, eh? Except maybe revert back to the old version that has security problems. Although that in itself is not a good idea.

Bad move by the Firefox team. Either that, or those that coded the extensions did not follow standards and had their applications break when the Firefox team updated their browser. The extension coders could have used shortcuts for example. Sort of like those annoying web coders that code for specific browsers.


 Glad to see the Ubuntu team jump on this problem and not trying to hide it. Good job guys, we know its not your fault! ;)[/QUOTE]
No, I'm powerless now... I provide Firefox 1.0.4 still in the repos, which is more secure than the Ubuntu team's workaround (includes 1.0.3+1.0.4 patches) but still isn't 100% secure.

---

### Post by mortoray on 2005-07-24
I'm experiencing the same random firefox crashing on an AMD64 install.

As a new user this is a real turn-off for Ubuntu.  Firefox+Adblock is the first thing I install on any machine, and if that doesn't work the machine is rather limited in its use.

---

### Post by martijntje on 2005-07-24
[QUOTE=mortoray]I'm experiencing the same random firefox crashing on an AMD64 install.

As a new user this is a real turn-off for Ubuntu.  Firefox+Adblock is the first thing I install on any machine, and if that doesn't work the machine is rather limited in its use.[/QUOTE]
 It's not ubuntu's fault.

If you wish, you can downgrade to an earlier version, but it leaves you vulnerable to a whole lot of exploits.

It's your choice.

---

### Post by jdong on 2005-07-24
[QUOTE=mortoray]I'm experiencing the same random firefox crashing on an AMD64 install.

As a new user this is a real turn-off for Ubuntu.  Firefox+Adblock is the first thing I install on any machine, and if that doesn't work the machine is rather limited in its use.[/QUOTE]

As others have said, the same problem exists on Windows Firefox 1.0.6, and Firefox 1.0.5 and 1.0.6 on every other distro.

At the Backports project, we're experimenting with FF 1.0.6. So far, it seems to be good and stable with plugins.




BTW, if you enable Backports repositories, you'll get a stable Firefox 1.0.4 which doesn't crash. :)

---

### Post by craigevil on 2005-07-24
I installed Firefox 1.0.6 from Backports-staging and it has not crashed one time.
I do not have alot of extensions.
Tabbrowser extension
Copyurl+
Infolister
Mouse gestures
NoScript
Toolbar enhancements
No problems.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.10) Gecko/20050721 Firefox/1.0.6 (Ubuntu package 1.0.6)

---

### Post by redboar on 2005-07-29
I get this every time I try to upgrade to Firefox 1.0.6 with apt-get or synaptic:

```
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This happens even if I uninstall the 1.0.4 version first.

Any suggestions?

---

### Post by bpilgrim1979 on 2005-07-29
This is how I finally fixed firefox after all the recent apt-get issues.  I now have firefox 1.0.6 and everything works.  :)

**[COLOR=Red]*WARNING*[/COLOR]: You must backup your bookmarks.html file or any other personal data BEFORE you do this.**  However, my profile was causing one of the problems so I had to delete it.  You can reinstall extensions and themes directly from mozilla addons later into a fresh, new profile.

```
sudo rm -R /var/lib/mozilla-firefox
sudo rm -R ~/.mozilla
```

That will completely wipe your firefox extension information, profile, etc.

**Now go into Synaptic and REINSTALL mozilla-firefox and mozilla-firefox-gnome-support **.  Ubuntu thinks that firefox is already installed but you manually wiped out /var/lib/mozilla-firefox so you need to reinstall.

This will reinstall your /var/lib/mozilla-firefox files.

Now don't click on any launcher icon yet.  You don't have a profile.

Go to console and type

```
firefox -profilemanager
```

If you have any profiles, delete everything (assuming you have backed up your bookmarks.html file or anything else).

Now create a new default profile.

Start firefox and you should be okay!  :)

Then install any extensions, themes, etc. into your fresh, new profile.

---

### Post by jdong on 2005-07-29
Usually, running **apt-get dist-upgrade** and **apt-get -f install** in alternation will fix this.

---

### Post by jdong on 2005-07-29
[QUOTE=redboar]I get this every time I try to upgrade to Firefox 1.0.6 with apt-get or synaptic:

```
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This happens even if I uninstall the 1.0.4 version first.

Any suggestions?[/QUOTE]

Whoa, what Backports mirror are you using? Make sure you reload / update your package lists (apt-get update), because 1.0.6-1ubuntu~5.04ubp1 should be trying  to install.

---

### Post by dkitty on 2005-07-30
Nothin is 100% secure anyway. I'm with Peter07. I'd rather have some a stable version with some of the extensions I've come to depend upon. Thank you for the shell commands wolfpakz.

---

### Post by redboar on 2005-07-30
[QUOTE=jdong]Whoa, what Backports mirror are you using? Make sure you reload / update your package lists (apt-get update), because 1.0.6-1ubuntu~5.04ubp1 should be trying  to install.[/QUOTE]

Oddly enough, I restarted the OS and Firefox works.  Here is the backports section of my sources.list file:

```
## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by robins_web on 2005-07-31
I just upgraded this morning and Firefox wouldn' even run. I did this twice before noticing that in kynaptic, thre are *two* entries for firefox: one says "forefox" and the other says "mozilla-firefox." The first 2 times, I picked "firefox;" the third time I clicked "mozilla-firefox" and everything installed perfectly. I've had no problems similar to those that have been posted here.

Robin

---

### Post by atilasendil on 2005-08-10
Hello again everybody;
the Software Updates show : 1.0.6-0ubuntu0.1 for mozilla-firefox and mozilla-firefox-gnome-support ...
I just do not remember if this was the faulty package;
is it safe to install now ? ? ?
sorry for beeing a noob . . .

---

### Post by atilasendil on 2005-08-13
better learn more about following the forums . . .
the packages are already fixed :

[http://www.ubuntuforums.org/showthread.php?t=51926](http://www.ubuntuforums.org/showthread.php?t=51926)

---

