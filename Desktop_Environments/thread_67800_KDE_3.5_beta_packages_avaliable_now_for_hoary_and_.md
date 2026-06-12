---
title: "KDE 3.5 beta packages avaliable now for hoary and breezy"
date: 2005-09-21
forum: Desktop Environments
---

### Post by SGC on 2005-09-21
For information on how to upgrade:
[http://kubuntu.org/kde-35beta1.php](http://kubuntu.org/kde-35beta1.php)

* i386 packages only

---

### Post by kenpozeiro on 2005-09-21
Hi there, does anyone knows if these packages can be installed under debian unstable? 
I don't know if they are 100% compatible with it.

Thanks

---

### Post by pchachte on 2005-09-21
I tried to update kubuntu, but along the way I got this error:

...
[INDENT]Unpacking replacement kdeutils ...
Preparing to replace superkaramba 0.36-0ubuntu1~5.04ubp1 (using .../superkaramba_4%3a3.4.91-0ubuntu0hoary1_i386.deb) ...
Unpacking replacement superkaramba ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
charles@chook:/stuff/soft$ sudo apt-get remove superkaramba[/INDENT]

It could be because I have compiled a few kde apps on my own (e.g., kimdaba).  

I tried to remove superkaramba, but I got this:

[INDENT]charles@chook:/stuff/soft$ sudo apt-get remove superkaramba
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.91-0ubuntu0hoary1) but 4:3.4.2-0ubuntu0hoary2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/INDENT]

apt-get -f install gave me this:
[INDENT]Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
56 not fully installed or removed.
Need to get 0B/8300kB of archives.
After unpacking 496kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 219936 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.2-0ubuntu0hoary2 (using .../kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/crystalsvg/32x32/apps/kttsd.png', which is also in package kttsd
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

Now I'm stuck.  Any ideas?

Thanks.

---

### Post by kenpozeiro on 2005-09-21
[QUOTE=pchachte]I tried to update kubuntu, but along the way I got this error:

...
[INDENT]Unpacking replacement kdeutils ...
Preparing to replace superkaramba 0.36-0ubuntu1~5.04ubp1 (using .../superkaramba_4%3a3.4.91-0ubuntu0hoary1_i386.deb) ...
Unpacking replacement superkaramba ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
charles@chook:/stuff/soft$ sudo apt-get remove superkaramba[/INDENT]

It could be because I have compiled a few kde apps on my own (e.g., kimdaba).  

I tried to remove superkaramba, but I got this:

[INDENT]charles@chook:/stuff/soft$ sudo apt-get remove superkaramba
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.91-0ubuntu0hoary1) but 4:3.4.2-0ubuntu0hoary2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/INDENT]

apt-get -f install gave me this:
[INDENT]Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
56 not fully installed or removed.
Need to get 0B/8300kB of archives.
After unpacking 496kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 219936 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.2-0ubuntu0hoary2 (using .../kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/crystalsvg/32x32/apps/kttsd.png', which is also in package kttsd
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu0hoary1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

Now I'm stuck.  Any ideas?

Thanks.[/QUOTE]

You can download the .deb with apt-get -d install package
It will just download and don't install the package, at /var/cache/apt/archives
(Maybe there are a lot of files there, run apt-get clean to clean up);
Run dpkg --force-all -i package.deb to try to install it even with the errors.
I hope it helps.

C ya.

---

### Post by JuanC on 2005-09-21
When the final version of KDE 3.5 would be released?

---

### Post by zAo on 2005-09-21
No problems here (Breezy)

---

### Post by SGC on 2005-09-21
[QUOTE=JuanC]When the final version of KDE 3.5 would be released?[/QUOTE]
According to [this page](http://developer.kde.org/development-versions/kde-3.5-release-plan.html) it could be at the end of October

---

### Post by mcmuffy on 2005-09-21
I just added :
deb [http://kubuntu.org/kde35beta1](http://kubuntu.org/kde35beta1) breezy main
to my sources list and did refresh/mark/apply and I was up and running in 3.5 in minutes. And very pretty it looks too :D

---

### Post by Drakx on 2005-09-21
Well i dont normally play with betas but i could not resist :) and installed and fired up great :)

---

### Post by mcmuffy on 2005-09-21
I'm probably tempting fate really running kde 3.5 beta on Breezy beta but what the hell!

---

### Post by rosslaird on 2005-09-21
All done, no hitches, very cool.

---

### Post by ghostintheshell on 2005-09-21
[QUOTE=SGC]For information on how to upgrade:
[http://kubuntu.org/kde-35beta1.php]("http://kubuntu.org/kde-35beta1.php")

* i386 packages only[/QUOTE]


thanks for the info.

well done on hoary \\:D/

---

### Post by bailout on 2005-09-22
I added the repo and updated but kcontrol says my kde is 3.49* beta, is this correct? Also now I have problems with the taskbar. I had it set to autohide and it won't reappear. I had to run kcontrol and set it back to on all the time. I followed the instructions for adding j.riddel's key but got a message saying no such package (I just copied the instruction line into the console).

---

### Post by Slackitude on 2005-09-22
I also got the message about no such package for the key, I finally just typed the first couple letters and than hit tab to auto complete it. That, for some reason, it liked even though I could see no difference.

---

### Post by ltmon on 2005-09-22
[QUOTE=bailout]I added the repo and updated but kcontrol says my kde is 3.49* beta, is this correct? Also now I have problems with the taskbar. I had it set to autohide and it won't reappear. I had to run kcontrol and set it back to on all the time. I followed the instructions for adding j.riddel's key but got a message saying no such package (I just copied the instruction line into the console).[/QUOTE]

It won't be marked as 3.5 until it actually is released.  A lot of apps use a similar convention with alphas/betas/rc's.

L.

---

### Post by Mishura on 2005-09-22
I'll wait a day or two before upgrading.. to see if anything serious pops up here. :)

Test!! Test, my guinea pigs!!   :grin:

---

### Post by SGC on 2005-09-22
[QUOTE=Mishura]I'll wait a day or two before upgrading.. to see if anything serious pops up here. :)[/QUOTE]

So far its very stable, it doesn't crash even once since yesterday.

---

### Post by drizek on 2005-09-22
[QUOTE=][/QUOTE]
 damn breezy is not working for me so nowim in suse downloading hoary just so i can use this. i think the ability to ship debs the day a kde is released is kubuntus #1 feature.

---

### Post by drizek on 2005-09-22
wow, this is really awesome. the transparency works better than before even, although its not perfect. the new taskbar is awesome and konqueror kicks ass. im very happy with it.

---

### Post by Hobbsee on 2005-09-22
[QUOTE=drizek]wow, this is really awesome. the transparency works better than before even, although its not perfect. the new taskbar is awesome and konqueror kicks ass. im very happy with it.[/QUOTE]
 so tempting to install it...but I know I should wait to see what others think of it, like the other poster above...

---

### Post by Knome_fan on 2005-09-22
[QUOTE=Mishura]
Test!! Test, my guinea pigs!!   :grin:[/QUOTE]

Just wanted to report that here is an other happy guinea pig. I've been using 3.5 since yesterday and as far as I can tell, everything works fine here.

---

### Post by z_pod on 2005-09-22
One more happy man here !

Many thanks to all people involved, you really make the difference.

YO

---

### Post by vassalle on 2005-09-22
[QUOTE=z_pod]One more happy man here !

Many thanks to all people involved, you really make the difference.

YO[/QUOTE]
 thanks to whoever that made this possible! xcompmgr is so MUCH LESS buggier compared 3.4.2 and im loving' it! Thanks

---

### Post by cubox on 2005-09-22
I Hate KDE


GNOME IS BETTER  :razz:

**Try to stay on Topic.......KB**

---

### Post by ghostintheshell on 2005-09-22
[QUOTE=cubox]I Hate KDE


GNOME IS BETTER  :razz:[/QUOTE]

I use Gnome too (as WM) and I prefer Gnome too.
But I really love K3b and some other stuff (Kate, Krusader, Krename, ...) that require KDE.

Oh, and I hate comment like this. So stupido.

---

### Post by DarkT on 2005-09-22
Works fine for me on breezy, only little problem was that I had to manually restart KDM from the console as kdm died on logging out but this was a one off. 
 
Also, if you're using panel hiding it seems it reset some of your settings (or is it that it adds a new one?) so that you have to move the mouse to the bottom right to show the panel (until you change it)... which is OK unless you have the panel top centre and have to spend a couple of minutes very confused :P Anyway a quick Alt+f2 & KControl and you can find the panel settings. 
Speaking of which, the new search features are a good time saver, I really like being able to type in the settings page I'm after in the search box in KControl and it giving me a quick selection.

---

### Post by Manny C on 2005-09-22
Only gripe with 3.5 b1 is the fact that gam_server is chewing large amounts of RAM. I have to kill is manually every so often.

Otherwise all good. See attached screenshot.

---

### Post by 8FootSativa on 2005-09-22
Removed....OT.

---

### Post by cubox on 2005-09-22
[QUOTE=ghostintheshell]I use Gnome too (as WM) and I prefer Gnome too.
But I really love K3b and some other stuff (Kate, Krusader, Krename, ...) that require KDE.

Oh, and I hate comment like this. So stupido.[/QUOTE]


That's is true  :wink:

---

### Post by Hobbsee on 2005-09-22
[QUOTE=cubox]That's is true  :wink:[/QUOTE]
 nice....

Seems pretty stable here - I finally broke down and installed it though.

You will need to fully reboot though - ctrl+shift+backspace leaves you at the very friendly terminal (and I dont remember most of the commands there!)

If anyone's looking for the original appearance of the taskbar, ie what was in 3.4, it's under configuring the task bar, and change the appearance to classic, instead of elegant.

---

### Post by ykpaiha on 2005-09-22
very very fast toward gnome!!!
I don't understand but it seems better finalized even in beta ???

---

### Post by Freddy on 2005-09-22
The "new" taskbar has been around for a long time. just not with the default install. For those that not is ready for a install of KDE 3.5 beta and still want's to use it, it's called Taskbar V2 and you can download a Kubuntu .deb file from [http://www.kde-look.org/content/show.php?content=25615](http://www.kde-look.org/content/show.php?content=25615) that one I didn't got to work under Breezy, so I compiled my own from source, it's a quickie. Locate the tarball at [http://www.kde-look.org/content/show.php?content=16261](http://www.kde-look.org/content/show.php?content=16261) /// Freddan

---

### Post by Mishura on 2005-09-22
OK, seems that the overall majority is that its rock solid.  I'm sold!  :) 

// apt-gettin' time

---

### Post by GeneralZod on 2005-09-22
I won't upgrade to this until Breezy hits (although I'm looking forward to it :)), but in the meantime, can anyone do a quick check and see if my "favourite" bug has been fixed? It will only take a minute! An earlier poster's statement to the effect that gam_server was overheating gives me some hope!

[http://bugs.kde.org/show_bug.cgi?id=106394](http://bugs.kde.org/show_bug.cgi?id=106394)

If it has, can anyone open up some removable medium (CD-ROM, USB-Pen, etc) in Konqueror and then unmount it as a test that monitoring for file access doesn't prevent unmounting?

Cheers!

---

### Post by Paulus on 2005-09-22
works cool here! loving kompmgr, you can select it so it just uses the windeco for transparencies, makes a great user experiance.

just having some superkarmba compilation problems (/w breezy):
 ```
Superkaramba can't be compiled
because of missing Python libraries/headers.


Your GCC supports symbol visibility, but the patch for Qt supporting visibility
was not included. Therefore, GCC symbol visibility support remains disabled.

For better performance, consider including the Qt visibility supporting patch
located at:

http://bugs.kde.org/show_bug.cgi?id=109386

and recompile all of Qt and KDE. Note, this is entirely optional and
everything will continue to work just fine without it
``` 
 

btw, this isn't the same as takbar 2, it doesn't show a screenshot of programs as a tooltip.

---

### Post by Mishura on 2005-09-22
Pretty smooth upgrade.  I like the fact that the new Konqueror has adblock.  (Firefox/Linux is bugging me, I'm already using the latest Opera mostly.)

I like the look of the new Plastik windeco.

The panel mouseover effects are cool.  I especially like it when I mouseover the clock, and it gives me times for other timezones.  Very handy.

I do have one question:  If by the "off chance" that KDE 3.5 messes up seriously,  could I comment out the 3.5 repo and reinstate the 3.4.2 repo in my sources.list and downgrade?  Probably won't, but just curious.

---

### Post by f1dave on 2005-09-22
AFAIK i don't think that's possible, since it will say something along the lines of "program asked for is version 1.2, but you already have version 2.0"

Someone please correct me if i'm wrong.

---

### Post by Freddy on 2005-09-22
> btw, this isn't the same as takbar 2, it doesn't show a screenshot of programs as a tooltip. 
Okey but that can be turned off in Taskbar V2, myself I won't upgrade before Breezy hits stable, don't wan't to confuse things more then I already do :).  /// Freddan

---

### Post by ghostintheshell on 2005-09-22
[QUOTE=f1dave]AFAIK i don't think that's possible, since it will say something along the lines of "program asked for is version 1.2, but you already have version 2.0"

Someone please correct me if i'm wrong.[/QUOTE]

you can apt-get remove kde 
remove the 3.5b1 repo.
then apt-get install kde (from the 3.4.2 repo).

I think :-P

---

### Post by drizek on 2005-09-22
ya, what ^ said.

also, taskbar v2 is NOT the same. the kde 3.5 one is better, although instead of a screenshot it has an icon and information about hte window. 

im having some trouble though because i (stupidly) used the same username in ubuntu as i had been using in suse. its using the suse kde settings and a lot of things are messed up for me. anyone know how to make a new account under kubuntu hoary?

Edit: and other than the suse settings thing(which is hardly KDE's fault), 3.5 is really stable and fast. a lot of the new features like the filter boxes and the add to panel thing give it a "cool" feeling rather than making it seem like a windows clone.

---

### Post by ltmon on 2005-09-22
[QUOTE=Paulus]

just having some superkarmba compilation problems (/w breezy):
 ```
Superkaramba can't be compiled
because of missing Python libraries/headers.


Your GCC supports symbol visibility, but the patch for Qt supporting visibility
was not included. Therefore, GCC symbol visibility support remains disabled.

For better performance, consider including the Qt visibility supporting patch
located at:

http://bugs.kde.org/show_bug.cgi?id=109386

and recompile all of Qt and KDE. Note, this is entirely optional and
everything will continue to work just fine without it
``` 
[/QUOTE]

As of KDE 3.5, Superkaramba is part of KDE proper.  You shouldn't have to compile it... it's in the KDE 3.5 repository.

L.

---

### Post by geearf on 2005-09-22
Hello,

I am tempted to try this one, lots of people here says it works like a charm, but they do not say if this is under breezy or hoary. I am under hoary, and I guess it should be less buggy but I still wonder ;)

Thanks

---

### Post by ltmon on 2005-09-22
[QUOTE=geearf]Hello,

I am tempted to try this one, lots of people here says it works like a charm, but they do not say if this is under breezy or hoary. I am under hoary, and I guess it should be less buggy but I still wonder ;)

Thanks[/QUOTE]

I am under Hoary, and only had the one problem where it froze on logout after the upgrade.

Restarting KDM fixed this (just reboot if you don't know how).

From then on it has been fine.

L.

---

### Post by geearf on 2005-09-22
Now that tempts me even more, I'll give it a try tomorrow I guess, hoping my two kde bugs have been solved.

Thanks :)

---

### Post by drizek on 2005-09-22
ya, works perfect here on hoary. ive been using it all today and yesterday and not a single crash/problem.

---

### Post by claydoh on 2005-09-22
[QUOTE=Paulus]
 ```
Superkaramba can't be compiled
because of missing Python libraries/headers.


Your GCC supports symbol visibility, but the patch for Qt supporting visibility
was not included. Therefore, GCC symbol visibility support remains disabled.

For better performance, consider including the Qt visibility supporting patch
located at:

http://bugs.kde.org/show_bug.cgi?id=109386

and recompile all of Qt and KDE. Note, this is entirely optional and
everything will continue to work just fine without it
``` 
 [/QUOTE]

The first line is the important bit, the rest is irrelevent :)
You  just need to install python2.4-dev

---

### Post by Paulus on 2005-09-23
Thanks ^, I have sucessfully compiled it now, but it still gives me the above warning, but nevermind

[QUOTE=ltmon]As of KDE 3.5, Superkaramba is part of KDE proper. You shouldn't have to compile it... it's in the KDE 3.5 repository.

L.[/QUOTE]

yeah,  I see it, but it's only version 0.36, I understand 0.37 is only in RC stage atm, but most new themes use the .skz file format now :)

hence i want the latest! (and greatest)

---

### Post by getaceres on 2005-09-23
Have you tried kaffeine with KDE 3.5? I read in kubuntuforums.net that someone is having problems with it.

---

### Post by sinbad782 on 2005-09-23
Have got this installed now on Breezy and am impressed. I have been playing around with the kdebluetooth package and a generic bluetooth adapter that I got from eBay and this even seems to work now with my Motorola v500 phone - excellent!

The only issues I have had so far have been Kicker segfaulting on shutdown/logout. The taskbar looks a bit weird with the default settings as I have it all transparent, but I am sure I can find a better configuration later on.

---

### Post by Drakx on 2005-09-23
One thing i have noticed is that skype has stopped working since the upgrade but other than that ive not had a problem so ill use Gnome till i work out how to get my skype working again

---

### Post by geearf on 2005-09-23
Ok I'm on it tooo now :) (on a hoary system).
Well one bug that could not let met start kplayer with a video file with strange name (aka with sutff like [blbla] and so on), now it works again (like in 3.4.1).

But the desktop still does not refresh if something happens in the konsole (like if I do touch toto in Desktop\, nothing will happen in kdesktop :(  ).

Else the taskbar is alittle different, but that's ok :l)

---

### Post by Mishura on 2005-09-23
Not sure if this is mentioned earlier, but I'll post it anyways...

When you upgrade KDE, and you do a "Log off", you will be dropped down to a command prompt.

Because KDM was also upgraded, you will have to restart it.  A minor inconvenience, so do this:

```
$ sudo killall -9 kdm
$ sudo kdm
```

This will kill the original KDM, and restart it.  Must be done as root/sudo.  After this, you should be all fine and stuff.  :)

---

### Post by Paulus on 2005-09-23
anyone knotice the terminal sessions button doesn't work on the kicker.

could just be me

also, is there a way to sort out the firefox buttons + fonts, the gtk applet doesn't seem to perminantly save the settings in 3.5, I can't stand firefox looking this way!

---

### Post by geearf on 2005-09-23
[QUOTE=Mishura]Not sure if this is mentioned earlier, but I'll post it anyways...

When you upgrade KDE, and you do a "Log off", you will be dropped down to a command prompt.

Because KDM was also upgraded, you will have to restart it.  A minor inconvenience, so do this:

```
$ sudo killall -9 kdm
$ sudo kdm
```

This will kill the original KDM, and restart it.  Must be done as root/sudo.  After this, you should be all fine and stuff.  :)[/QUOTE]
you should be able to do
sudo /etc/init.d/kdm restart

---

### Post by DarkT on 2005-09-23
[QUOTE=Paulus]anyone knotice the terminal sessions button doesn't work on the kicker.

could just be me
[/QUOTE]
Same here, it worked the first login if I remember correctly and then it stopped.

As for firefox, I've no idea. The gtk-qt theme engine works fine for me... You could try tracking down the config for the gtk-qt engine and deleting it. The when you run its setting page again it should generate a new config and might work.

---

### Post by Jeezis on 2005-09-23
i installed the 3.5 beta with no problem, but man, it seems unstable as heck! it freezes any time i try to edit the k menu and randomly other times as well. i suppose it's what i get for messing with a beta release, but i shall tough it out i suppose :| 

just wondering if anyone else has had similar problems with instability.

---

### Post by beefsprocket on 2005-09-23
[QUOTE=Jeezis]i installed the 3.5 beta with no problem, but man, it seems unstable as heck! it freezes any time i try to edit the k menu and randomly other times as well. i suppose it's what i get for messing with a beta release, but i shall tough it out i suppose :| 

just wondering if anyone else has had similar problems with instability.[/QUOTE]

My only problem is that I've lost the icon for Kmenu. Other than that, no instability whatsoever. Did you upgrade everything in kde or only parts?

---

### Post by Jeezis on 2005-09-23
[QUOTE=beefsprocket]My only problem is that I've lost the icon for Kmenu. Other than that, no instability whatsoever. Did you upgrade everything in kde or only parts?[/QUOTE]

i added the kde 3.5 sources and did a dist-upgrade, so i assumed that i got everything.

---

### Post by jbinc1 on 2005-09-23
Hi,
I'm trying to import the key for KDE 3.5 and I get this.

user1@workstation100:~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
gpg: can't open `kubuntu-packages-jriddell-key.gpg': No such file or directory

I'm a noob to this, so some help would be greatly appreciated.](*,)

---

### Post by Jeezis on 2005-09-23
i am wondering if my instability problems are because of my kernel, i installed 2.6.11-1-686 at the same time i upgraded kde, i'm going to try it with 2.6.10-5-686 and see if that helps.

could it be because i'm using a 686 kernel? i saw the packages were i386 only, so could this be causing the system lockups?

---

### Post by drizek on 2005-09-23
[QUOTE=jbinc1]Hi,
I'm trying to import the key for KDE 3.5 and I get this.

user1@workstation100:~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
gpg: can't open `kubuntu-packages-jriddell-key.gpg': No such file or directory

I'm a noob to this, so some help would be greatly appreciated.](*,)[/QUOTE]

you have to actually download the key to your home directory before you do that command.

---

### Post by BetaguyGZT on 2005-09-23
It's working pretty good for me. Little hang with trying to get Synaptic to download it for me, so I had to do it twice to get everything, but it's working and aside from some functionality & convienince changes (that I hope they make before it goes final), I think it's pretty good. It feels a lot more solid to me.

GTK apps' font rendering is a LOT better than before. That's a plus in my book. :)

---

### Post by jbinc1 on 2005-09-24
[QUOTE=drizek]you have to actually download the key to your home directory before you do that command.[/QUOTE]

Does it have to go anywhere in particular? Also, do I click on the link and copy & paste it? When I click on it now it takes me to the page that shows the code. I don't get an option to download or save it. Sorry to be so ignorant of the process.:)

---

### Post by MadPriest on 2005-09-24
I've added KDE3.5 repos together with the Breezy repos, and made dist-upgrade. 
Everything worked fine.
And it's very stable. 
For all those who have no sound in xmms and amarok - check whether oss plugin is set by default and change it (this worked for me)
**Jeezis**, as for Kmenu - you should add this applet  O:) . I was shocked also  ;-) 
It's very stable (running for 3 days already) on Breezy upgraded from Hoary.
The only thing i cant get to show up on the task bar is the Battery monitor.

---

### Post by Luzbel on 2005-09-24
Konqueror+Flash7 under hoary is not working here. Grey squares instead of swf movies. Konqueror does recognise the plugins.

---

### Post by MadPriest on 2005-09-24
[QUOTE=MadPriest]The only thing i cant get to show up on the task bar is the Battery monitor[/QUOTE] 
I'm an idiot!!!!  ](*,) 
I just had to add "system tray" applet to the kicker.
 \\:D/  \\:D/  \\:D/

---

### Post by Jonathan2007 on 2005-09-24
[QUOTE=jbinc1]Does it have to go anywhere in particular? Also, do I click on the link and copy & paste it? When I click on it now it takes me to the page that shows the code. I don't get an option to download or save it. Sorry to be so ignorant of the process.:)[/QUOTE]
Right click on the link (this is for Firefox but should be similar on Konqueror or another browser) and say save this link as and then save it under /home/yourusername. Then go to konsole and type in sudo apt-key add kubuntu-packages-jriddell-key.gpg. You can then go into Synaptic and try again.

I upgraded last night. I am running Hoary. It is running good for me so far.

---

### Post by jbinc1 on 2005-09-24
[QUOTE=Jonathan2007]I upgraded last night. I am running Hoary. It is running good for me so far.[/QUOTE]

Thanks for the help. Are any of the issues fixed? For instance administrator mode in control center not working?

---

### Post by beefsprocket on 2005-09-24
[QUOTE=Jeezis]i am wondering if my instability problems are because of my kernel, i installed 2.6.11-1-686 at the same time i upgraded kde, i'm going to try it with 2.6.10-5-686 and see if that helps.

could it be because i'm using a 686 kernel? i saw the packages were i386 only, so could this be causing the system lockups?[/QUOTE]

I wonder if that is it. It could well be but then, I'm running 2.6.12-8-k7with Breezy and KDE3.5. Have you thought about a newer kernel? I suppose upgrading one thing at a time would be the only way to really tell which broke what. 

Any progress?

---

### Post by beefsprocket on 2005-09-24
[QUOTE=jbinc1]Thanks for the help. Are any of the issues fixed? For instance administrator mode in control center not working?[/QUOTE]

I still have that problem. It's something I've learned to deal with by running kcmshell from the command line with sudo i.e. "sudo kcmshell kde-clock"

Not ideal but it works for now.

---

### Post by Paperjam on 2005-09-24
[QUOTE=beefsprocket]I still have that problem. It's something I've learned to deal with by running kcmshell from the command line with sudo i.e. "sudo kcmshell kde-clock"

Not ideal but it works for now.[/QUOTE]

I had that problem too. I fixed it by doing
```
cd /home/*username*
sudo chown -R *username* .kde
sudo chgrp -R *username* .kde

```

Apparently, some files in the .kde-directory were owned by root. I guess that's because when using sudo, the home-directory doesn't change, so if configuration-files are created, they are created in your very own home-directory, but owned by root.

Paperjam

---

### Post by jbinc1 on 2005-09-24
Thanks. I'll give that a try. I know there's work-arounds, but it will be much more convenient if I can get it to work correctly.

---

### Post by JPatrick on 2005-09-24
[QUOTE=jbinc1]Thanks for the help. Are any of the issues fixed? For instance administrator mode in control center not working?[/QUOTE]
That's an upstream (?) bug and no I don't think it's fixed :(

---

### Post by samwyse on 2005-09-24
[QUOTE=JPatrick]That's an upstream (?) bug and no I don't think it's fixed :([/QUOTE]
 works ok, but kweather is held back for some reason and konqueror sorts files using weird spaces in icon mode.

---

### Post by jbinc1 on 2005-09-24
I finally got it installed. I had a problem with Firefox. I had to remove & reinstall and now it's ok. Did anyone else lose Control Center. The app was still there, but not in the K menu. I removed & reinstalled but it didn't show back up. Any clues??? BTW, the administrator mode button seems to be working on all but file sharing. Kinda weird.

---

### Post by claydoh on 2005-09-24
[QUOTE=jbinc1]I finally got it installed. I had a problem with Firefox. I had to remove & reinstall and now it's ok. Did anyone else lose Control Center. The app was still there, but not in the K menu. I removed & reinstalled but it didn't show back up. Any clues??? BTW, the administrator mode button seems to be working on all but file sharing. Kinda weird.[/QUOTE]

It is now called "system Settings" on the Main Menu, with a new layout style, you can still access the old one by typing "kcontrol' in a konsole.

---

### Post by nrwilk on 2005-09-24
Would KDE 3.5 beta run on a PPC breezy Kubuntu install?  Emphasis on PPC.

Does it matter?  If not, I'm installing it tonight.  Can't wait!

---

### Post by Freddy on 2005-09-24
Couldn't hold myself any longer even though i know I should, I installed KDE 3.5-beta and this is not for my Breezy. I'm going back.

I just have to use my baghira style and it doesn't work that well yet, kicker gets all messed up and the icons gets a black background after been pointed on with the mouse, not even a recompile for 3.5 made it work proper. After every restart of Kde, all my applets thats runs on my mainkicker dies and has to be readded, while doing that my maclike upper panel grows big and has to be restarted.

I will try to make it work for a couple of days but if it stays like this, I'm back on 3.4.2 till realese date.   /// Freddan

---

### Post by Jonathan2007 on 2005-09-24
[QUOTE=jbinc1]I finally got it installed. I had a problem with Firefox. I had to remove & reinstall and now it's ok. Did anyone else lose Control Center. The app was still there, but not in the K menu. I removed & reinstalled but it didn't show back up. Any clues??? BTW, the administrator mode button seems to be working on all but file sharing. Kinda weird.[/QUOTE]
Firefox has nothing to do with the KDE 3.5 upgrade. It is a bug with the update to Firefox 1.0.7 which probably got upgraded if you did an apt-get dist upgrade. It seems everyone had to uninstall it and reinstall it to make it work again. If you want more info search for Firefox upgrade problem.

And the administrator mode seemed to be working for me **so far**. But I think you are off on the file sharing tab. It is probably grayed out which means that you don't have samba or the nfs servers installed. It tells you that at the top but it is a little hard to read. I have the same problem but I can't get samba installed. See [this](http://ubuntuforums.org/showthread.php?p=369116)  thread for me info about problems getting samba installed. I am still looking for a solution.

[QUOTE=claydoh]It is now called "system Settings" on the Main Menu, with a new layout style, you can still access the old one by typing "kcontrol' in a konsole.[/QUOTE]
That must be for Breezy?? Because I still see Control Center on my Hoary machine.

---

### Post by claydoh on 2005-09-24
Probably, I didn't notice it till I upgraded breezy to kde 3.5 as the System Menu on the taskbar no longer contained a "settings" option. I probably did not notice it gone till I went looking for it :)

---

### Post by eMuNiX on 2005-09-25
Installed yesterday, along with Limewire, all was running fine but now the machine had slowed to a crawl after 5-10 minutes after boot and now the machine won't get passed the login screen for either KDE or Gnome.  Any thoughts on how I might fix this, at the moment I am a little stuck.  All in Hoary.

edit/ I can get into WindowMaker so maybe a reinstall of KDE and GNOME is required  (I half fried GNOME the other week so perhaps the 2 combined is thr problem)

---

### Post by Freddy on 2005-09-25
Has anyone figured out a satisfactory way of downgrading to kde 3.4.2 again, deleting the beta mirror and reinstall kdesktop and kdebase doesn't cut it. I can't stand how my kicker is all messed up with this new beta version and it was a little to early for me to upgrade to the beta, which is ofcourse why it's just still a beta :).  /// Freddan

---

### Post by eMuNiX on 2005-09-25
[QUOTE=eMuNiX]Installed yesterday, along with Limewire, all was running fine but now the machine had slowed to a crawl after 5-10 minutes after boot and now the machine won't get passed the login screen for either KDE or Gnome.  Any thoughts on how I might fix this, at the moment I am a little stuck.  All in Hoary.

edit/ I can get into WindowMaker so maybe a reinstall of KDE and GNOME is required  (I half fried GNOME the other week so perhaps the 2 combined is thr problem)[/QUOTE]
Now I can't get anything to start, hohum I was looking for an excuse to try out SuSE 10 so off to install that at least for the interim.

---

### Post by Redindian on 2005-09-25
Hello,
I'm getting the following error when I try to upgrade to KDE 3.5 beta in Hoary,
E: /var/cache/apt/archives/kdelibs-data_40x1.8810000000067p-8863.4.91-0ubuntu0hoary1_all.deb:  trying to overwrite `/usr/share/icons/crystalsvg/32x32/apps/kttsd.png', which is also in package kttsd

thanks.

---

### Post by Knome_fan on 2005-09-25
[QUOTE=Freddy]Has anyone figured out a satisfactory way of downgrading to kde 3.4.2 again, deleting the beta mirror and reinstall kdesktop and kdebase doesn't cut it. I can't stand how my kicker is all messed up with this new beta version and it was a little to early for me to upgrade to the beta, which is ofcourse why it's just still a beta :).  /// Freddan[/QUOTE]

One method that is perhaps quite radical but always worked for me is to uninstall kdelibs-bin. This will get rid of KDE for good (there might be some packages left, for example kdelibs-data doesn't get uninstalled).
Now you could change to the old repository and reinstall kubuntu-desktop.

Keep in mind that you have to do this from the command line, not from within KDE, or at least from some other desktop than KDE.


[QUOTE=Redindian]Hello,
I'm getting the following error when I try to upgrade to KDE 3.5 beta in Hoary,
E: /var/cache/apt/archives/kdelibs-data_40x1.8810000000067p-8863.4.91-0ubuntu0hoary1_all.deb: trying to overwrite `/usr/share/icons/crystalsvg/32x32/apps/kttsd.png', which is also in package kttsd[/QUOTE] 

Not a very clean solution but it should work:
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdelibs-data_40x1.8810000000067p-8863.4.91-0ubuntu0hoary1_all.deb

It's probably a good idea to run sudo apt-get -f install after this.

---

### Post by Redindian on 2005-09-25
Not a very clean solution but it should work:
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdelibs-data_40x1.8810000000067p-8863.4.91-0ubuntu0hoary1_all.deb

It's probably a good idea to run sudo apt-get -f install after this.[/QUOTE]


gnome_fan, I did run the above but still I'm getting the same error. 

Anyone please help me with the following error.
E: /var/cache/apt/archives/kdelibs-data_40x1.8810000000067p-8863.4.91-0ubuntu0hoary1_all.deb: trying to overwrite `/usr/share/icons/crystalsvg/32x32/apps/kttsd.png', which is also in package kttsd

Thanks.

---

### Post by Freddy on 2005-09-25
> One method that is perhaps quite radical but always worked for me is to uninstall kdelibs-bin. This will get rid of KDE for good (there might be some packages left, for example kdelibs-data doesn't get uninstalled). 
I will try this but in a few days cause I wanna backup some stuff before doing anything this radical and if that doesn't work I need to reinstall cause 3.5 is just now like a plague for me, thanks for the reply Knome_Fan.   /// Freddan

---

### Post by Knome_fan on 2005-09-25
> 
gnome_fan, I did run the above but still I'm getting the same error. 

Anyone please help me with the following error.
E: /var/cache/apt/archives/kdelibs-data_40x1.8810000000067p-8863.4.91-0ubuntu0hoary1_all.deb: trying to overwrite `/usr/share/icons/crystalsvg/32x32/apps/kttsd.png', which is also in package kttsd

Thanks.
Hm, that's strange.

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdelibs-data_40x1.8810000000067p-8863.4.91-0ubuntu0hoary1_all.deb
```
What does it say if you issue this command?

An other thing you could try is to uninstall kttsd, though I don't really know if this is a good idea, as I don't know what this packages does.

---

### Post by Jonathan2007 on 2005-09-25
Has anyone noticed that the system menu on kicker when going into Home using that it brings you to system:/home instead of /home/yourusername. I find this very annoying as I like to browse through various music videos and concerts and when I click on one to play in Kaffeine it has to copy it to a temp space because of the system:/home thing. If anyone knows how I could adjust this on the system menu I would appreciate it.

---

### Post by Paperjam on 2005-09-26
[QUOTE=Freddy]Has anyone figured out a satisfactory way of downgrading to kde 3.4.2 again (...)[/QUOTE]
Maybe uninstall everything related to kde with
```
apt-get remove "kde*"
```
Then clean the cache
```
apt-get clean
```
And reinstall kubuntu-desktop...

---

### Post by zsoltika on 2005-09-29
Hi for everyone, this is my first post here.
Got installed Kubuntu and kde3.5b.
Then switched my shell via [FONT="Courier New"]chsh[/FONT] to [FONT="Courier New"]/bin/zsh[/FONT].
Fired up kde and recognised that if I run konsole, it doesn't run zsh, but bash. More weird: it doesn't look like a bash shell: my [FONT="Courier New"]$HOME/.bashrc[/FONT] wasn't sourced. 
I hate this behaviour, and got no clue wwhat to do against :cry:
Any idea?

---

### Post by Jonathan2007 on 2005-09-29
[QUOTE=Jonathan2007]Has anyone noticed that the system menu on kicker when going into Home using that it brings you to system:/home instead of /home/yourusername. I find this very annoying as I like to browse through various music videos and concerts and when I click on one to play in Kaffeine it has to copy it to a temp space because of the system:/home thing. If anyone knows how I could adjust this on the system menu I would appreciate it.[/QUOTE]
I am still having this "problem" and would like to find a solution soon. Does anyone know how to solve it?

---

### Post by Knome_fan on 2005-09-30
[QUOTE=Jonathan2007]I am still having this "problem" and would like to find a solution soon. Does anyone know how to solve it?[/QUOTE]

Well, it's not really a solution, but a workaround, but what you could do is put the home directory on your kicker.

To do this, fire up konqueror as file browser and select your home folder on the navigation bar (the bar on the left).
You should now see the file hierachy of your home directory, with your home directory at the top.

Now you can simply grab this folder and drag it to your kicker and now should have a launcher that opens konqueror with /home/youruser.

---

### Post by jbinc1 on 2005-09-30
Hello,

Has anyone been having problems with the repositories? When I reload in synaptic or apt-get update, It tells me that some of the repositories (backports) are unavailable. Has there been a change or something I've missed?
Thanks

---

### Post by Knome_fan on 2005-09-30
The unofficial backports mirrors aren't availabe anymore, you'll have to change to the official ones now.
[http://ubuntuforums.org/showthread.php?t=69681](http://ubuntuforums.org/showthread.php?t=69681)

---

### Post by jbinc1 on 2005-09-30
[quote=Knome_fan]The unofficial backports mirrors aren't availabe anymore, you'll have to change to the official ones now.
[http://ubuntuforums.org/showthread.php?t=69681]("http://ubuntuforums.org/showthread.php?t=69681")[/quote]

Thanks. I totally missed the other thread.:oops:

---

### Post by suziequzie on 2005-10-01
Hey, I couldn't get the key for it... 
Here's what I got :

[I]suzie@kubuntu:~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
gpg: can't open `kubuntu-packages-jriddell-key.gpg': No such file or directory[/I]

Therefore, I couldn't get 3.5... any help would be greatly appreciated.

---

### Post by MadPriest on 2005-10-01
**suziequzie**, did you save the key somewhere on the computer?

---

### Post by jbinc1 on 2005-10-01
Right click on the link for the key (this is for Firefox but should be similar on Konqueror or another browser) and say save this link as and then save it under /home/yourusername. Then go to konsole and type in sudo apt-key add kubuntu-packages-jriddell-key.gpg. You can then go into Synaptic and try again.


This worked for me. Good Luck. Also make sure that you have the lastest repositories.

---

### Post by suziequzie on 2005-10-01
[QUOTE=MadPriest]**suziequzie**, did you save the key somewhere on the computer?[/QUOTE]

Uhm, yeah, I feel real stupid... I should have read through more posts before I tried it...  I found it after I posted my question, did it, and... well sorry about that... 

But:

I have 3.5 now! WooohOOO!  Thank you for your help.

:)

---

### Post by MadPriest on 2005-10-01
**suziequzie**, just enjoy ;)

---

### Post by Bolverk on 2005-10-01
I like the 3.5 beta more than I like 3.4.2. I have noticed something odd though: my icons keep migrating down on my screen. Every time I log in, they move farther down and eventually begin to overlap. This is happening on both my laptop and desktop. I think it's because KDE is trying to reserve a spot for the CD drive and keeps making space every time it loads, "forgetting" that it had already made space last session.

---

### Post by haaglin on 2005-10-02
After upgrading to 3.5 i cant logout/shutdown anymore. after i press the "End current session" or "shutdown" button, it just stops and displays the background of gnome root?? to shut down i have to go into terminal and do it manually. Anyone else have this problem?

---

### Post by suziequzie on 2005-10-03
[QUOTE=MadPriest]**suziequzie**, just enjoy ;)[/QUOTE]


Oh, thank you very much, I am enjoying it. AND, I also installed the K7 kernel thru kynaptic (and it loaded it into GRUB for me) and that seems to be working very well too. (Running XP2200 processor).

Man, installing this system was fun.  Learning it is sometimes frustrating but also a blast! It's made my computer feel all shiny and new again, know what I mean?

My boyfriend, however, is probably sick of my geeking out everytime I try something new and it works... Well, fortunately I have this forum to indulge my geekish tendencies. 

Thanks for all the insights you guys have given me while reading your posts.

:D

---

### Post by zsoltika on 2005-10-03
[QUOTE=zsoltika]Then switched my shell via [FONT="Courier New"]chsh[/FONT] to [FONT="Courier New"]/bin/zsh[/FONT].
Fired up kde and recognised that if I run konsole, it doesn't run zsh, but bash. More weird: it doesn't look like a bash shell: my [FONT="Courier New"]$HOME/.bashrc[/FONT] wasn't sourced. 
I hate this behaviour, and got no clue wwhat to do against :cry:
Any idea?[/QUOTE]
To answer my own question: it was my default shell.session settings which had 'bash -ls' as the program to run. After clearing that zsh fired up ...

---

### Post by daller on 2005-10-03
[QUOTE=haaglin]After upgrading to 3.5 i cant logout/shutdown anymore. after i press the "End current session" or "shutdown" button, it just stops and displays the background of gnome root?? to shut down i have to go into terminal and do it manually. Anyone else have this problem?[/QUOTE]


An update will fix that - Did the trick here...

---

### Post by daller on 2005-10-03
Well, I love KDE3.5 - No doubt about that...

But something's really frustrating!

What is going on with "system:/home" instead of "/home/<USER>" ??? - It fsck's up the whole system!

Nothing works properly that way! (Kaffeine, OpenOffice, etc...)

Is there an easy workaround for this? (Or an explaination?)

Cheers

---

### Post by GameManK on 2005-10-03
[QUOTE=daller]Well, I love KDE3.5 - No doubt about that...
But something's really frustrating!
What is going on with "system:/home" instead of "/home/<USER>" ??? - It fsck's up the whole system!
Nothing works properly that way! (Kaffeine, OpenOffice, etc...)
Is there an easy workaround for this? (Or an explaination?)
Cheers[/QUOTE]

I don't feel like it really messes up the system, but I noticed that the home shortcut takes you there instead of /home/<user> and i find it really stupid and pointless.

I like the whole camera:/ and settings:/ thing (which were in earlier versions) but system:/home is a really unintuitive feature

---

### Post by daller on 2005-10-04
Well, it messes with most applications, which aren't modified to fit this change...

I like the idear, and I understand that it takes time to implement... But it's not that hard, is it?

And what about the new automount-thing? - Will it be able to identify different media from each other? - I have a lot of external harddrives, and only want some (partitions) of them to be automounted.

Of course, there should be some rules implemented:

Blanc cd/dvd - "Do nothing" or "Start K3b cd/dvd project"
Video DVD - "Do nothing" or "Play with Kaffeine"
Audio CD - "Do nothing" or "Play with KsCD"
USB Storage media - "Do nothing" or "Open in a new window"
Camera - "Do nothing" or "Open with Digikam" (another app maybe - digikam is not in the repos...)


etc...

By the way... how do I get access to the i18n files for KDE apps? - I'm from Denmark, and I would really like to translate some more of KDE3.5 before it's released...

---

### Post by sal on 2005-10-09
im running kernel 2.6.12-9-686 will the i386 packages still work for me or would i have to wait untill they make i686 packages?
thanks

---

### Post by geearf on 2005-10-09
the i386 is for the architecture x86, which 686 is too, so it will work without problem.

---

### Post by sal on 2005-10-09
[QUOTE=geearf]the i386 is for the architecture x86, which 686 is too, so it will work without problem.[/QUOTE]

thanks.

---

