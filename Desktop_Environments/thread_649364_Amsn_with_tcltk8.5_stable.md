---
title: "Amsn with tcl/tk8.5 stable"
date: 2007-12-24
forum: Desktop Environments
---

### Post by patrickfromspain on 2007-12-24
Hi there!

**EDIT:** this isn't necessary anymore. To install the latest stable amsn (0.97), just enable the gutsy backports repo, sudo apt-get update and sudo apt-get install amsn. This will get you the latest 0.97 amsn with antialiased fotns.

It's been a couple of day since the stable version of tcl/tk8.5. This version is already in the debian sid repos, and I've backported it to ubuntu. It shouldn't harm anything and it shouldn't conflict with any previous tcl/tk version, as the packages should be compliant with the debian packaging rules. 

I've also done a package from the latest amsn version. The package isn't a standard amsn one, but it has some extra skins and plugins and some configuration tweaks. It supports drag and drop: drag a file into the conversation and it will be sent to you contact! 

UPDATE: new package is tcltls1.50. Repackaged from the package from the repos, against tcl8.5, so that it doesn't require tcl8.3 anymore.

INSTALL ORDER: tcl8.5, tk8.5, tcltls, amsn. If you install amsn before tcltls, you will also install tcl8.3, which isn't necessary with my tcltls package.

For all stuff to work correctly, you **MUST INSTALL ALL OF MY THREE PACKAGES **(install them using gdebi). If you install my tcl/tk8.5 and the amsn from the repos chances are that it won't work or, at best, you will have the ugly and "old" aMsn.

**WARNING, please read:** The packages are made for gutsy. If you have amsn installed from the ubuntu oficial repos this will replace that one. For other installations you could have done, better ask if you don't know what to do. The same aplies to tcl/tk8.5: it won't conflict with tcl/tk 8.4 or 8.3, but if you already have a 8.5 version installed, you should uninstall that one first. If you don't know anything about how you installed amsn and/or tcl/tk, better don't do anything.

**IF YOU HAVE PROBLEMS:** open synaptic and there remove tcl8.5, tk8.5 and amsn. Then install again my three packages. First tcl8.5, then tk8.5 and at last amsn.

SCREENSHOT:
[[IMG]http://img504.imageshack.us/img504/4348/amsncx8.th.png[/IMG]](http://img504.imageshack.us/my.php?image=amsncx8.png)

LINKS:

TCL8.5: [http://in.solit.us/archives/download/114664](http://in.solit.us/archives/download/114664)

TK8.5: [http://chronos.solit.us/archives/download/113979](http://chronos.solit.us/archives/download/113979)

AMSN 0.97 stable: [http://in.solit.us/archives/download/114530](http://in.solit.us/archives/download/114530)

TCLTLS1.50 [http://in.solit.us/archives/download/115681](http://in.solit.us/archives/download/115681)

CHEEERS!

---

### Post by rainwalker on 2007-12-26
Would this fix my webcam troubles, since I keep getting some message saying it was fixed in the latest version of amsn (or something along those lines)?
Also, will it actually look good (anti-aliased text, for example)?

---

### Post by patrickfromspain on 2007-12-26
It will look good (it is antialiased), but I don't know if it would fix your webcam problems.

---

### Post by Steve Fisher on 2007-12-27
Thanks for this. I've been becoming increasingly unhappy with Pidgin and was looking for an alternative. I'd tried aMSN before but was put off by the ugly interface.  This is much better!   Plus, it seems like almost everyone uses MSN these days!

---

### Post by Dropknee on 2007-12-27
Strange, this aMSN show 0.98b (25/12/07) well at last for me, anyone else?

---

### Post by patrickfromspain on 2007-12-28
that's completely normal, since it is a development version, and since it was very near to the 0.97 release, they changed it into 0.98.. 

Anyway, I've uploaded 0.97 stable, which is already out! enjoy :)

[http://in.solit.us/archives/download/114436](http://in.solit.us/archives/download/114436)

---

### Post by Reeva on 2007-12-28
Thanks ;)

worked very well!

---

### Post by picpak on 2007-12-28
Hi,

is there any reason your packages need kde packages installed?

if there isn't, could you please provide a version that doesn't require it?

Thanks!

---

### Post by mabovo on 2007-12-28
Is there a version for amd64 ?

---

### Post by patrickfromspain on 2007-12-28
I've uploaded a new version. It know doesn't depend on klash, cabextract and libsnack2 anymore, but it rather suggests them and, because of that, the winks plugin isn't active by default and isn't configured to use klash, as it was before. It now supports drag and drop to send file: drag a file into the conversation window and it will be sent to the contact!

There aren't any 64bits packages for that, sorry.

[http://in.solit.us/archives/download/114530](http://in.solit.us/archives/download/114530)

Hope you like it!

EDIT: by the way, the reason for using klash was because it was able to play received winks inside the chat window, while gnash couldn't (strange..), but I didn't realise that would require to install kde packages. sorry

---

### Post by picpak on 2007-12-28
> **patrickfromspain said:**
> I've uploaded a new version. It know doesn't depend on klash, cabextract and libsnack2 anymore, but it rather suggests them and, because of that, the winks plugin isn't active by default and isn't configured to use klash, as it was before. It now supports drag and drop to send file: drag a file into the conversation window and it will be sent to the contact!

There aren't any 64bits packages for that, sorry.

[http://in.solit.us/archives/download/114530](http://in.solit.us/archives/download/114530)

Hope you like it!

EDIT: by the way, the reason for using klash was because it was able to play received winks inside the chat window, while gnash couldn't (strange..), but I didn't realise that would require to install kde packages. sorry

Thank you! That's very strange indeed. I don't even know what Winks are, so I sure won't be missing them, lol.

---

### Post by Juan_VCS on 2007-12-28
Thanks a lot!

---

### Post by mac-duff on 2007-12-29
Hi,
by executing the AMSN has a problem to find TK location. How can I change it, I just have 8.5

amsn
Application initialization failed: Can't find a usable init.tcl in the following directories: 
    /usr/lib/tcl8.4 /usr/lib/tcl8.4 /lib/tcl8.4 /usr/library /library /tcl8.4.15/library /usr/lib/tcl8.4



This probably means that Tcl wasn't installed properly.

Error in startup script: can't find package Tk
    while executing
"package require Tk"
    (file "/usr/local/bin/amsn" line 48)
stephan@m-d-l:~$

---

### Post by Starlight on 2007-12-29
Hi! I got this error when I tried to run it...

wish8.5: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

But Adept says I have libxss installed...

---

### Post by patrickfromspain on 2007-12-29
[QUOTE=mac-duff]Hi,
by executing the AMSN has a problem to find TK location. How can I change it, I just have 8.5

amsn
Application initialization failed: Can't find a usable init.tcl in the following directories:
/usr/lib/tcl8.4 /usr/lib/tcl8.4 /lib/tcl8.4 /usr/library /library /tcl8.4.15/library /usr/lib/tcl8.4



This probably means that Tcl wasn't installed properly.

Error in startup script: can't find package Tk
while executing
"package require Tk"
(file "/usr/local/bin/amsn" line 4
stephan@m-d-l:~$[/QUOTE]

have you install all MY three packages? You must install tcl8.5 first, tk8.5 then and at last amsn. It seems like you have installed amsn from the ubuntu repos, not the package I have uploaded. If you have, download them again, make sure you haven't installed and previous tcl/tk8.5 and reinstall them.

EDIT: I have just seen you have another amsn version, installed in /usr/local. Try this: sudo mv /usr/local/bin/amsn /usr/local/bin/old-amsn

---

### Post by patrickfromspain on 2007-12-29
> **Starlight said:**
> Hi! I got this error when I tried to run it...

wish8.5: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

But Adept says I have libxss installed...
could you reinstall libxss1 please?

sudo apt-get install --reinstall libxss1

You could also try to reinstall all my three packages: tcl8.5, tk8.5 and amsn

---

### Post by rainwalker on 2007-12-29
How will I get updates if I install this aMSN? Will I have to check back to this thread or what?

Also, do I need to uninstall the aMSN I have right now (which I installed from the repos)?

---

### Post by patrickfromspain on 2007-12-30
As for amsn, there won't be any updates in some time... they release a new version every year or so. For tcl/tk 8.5, I don't know how things will move.. I've already done an update to tcl, and I'm quite sure I'll do more updates as they update on Debian SID or the final  tcl/tk8.5 makes it into hardy or debian lenny (right now, they are at beta3).

As for amsn.. my package will overwrite the one from the ubuntu repos. If you don't like it, you just have to uninstall amsn and reinstall it from the repos and remove tcl/tk8.5 packages, no problem.

EDIT: case the final amsn makes it into the gutsy oficial repos, if it was compiled against tcl/tk8.4 I would do an update so my packages would have a higher version and thus wouldn't be upgraded.

---

### Post by Starlight on 2007-12-30
> **patrickfromspain said:**
> could you reinstall libxss1 please?

sudo apt-get install --reinstall libxss1

You could also try to reinstall all my three packages: tcl8.5, tk8.5 and amsn
I'll try. :) But first I have a question... could this problem be caused by installing all these three packages with the --force-architecture option? I had to use it, because I have amd64. But I thought that 32bit programs can work on a 64bit system...hmm...

---

### Post by patrickfromspain on 2007-12-30
oh.. then it sure is because of that. A 32bit program won't work with a 64bit library, sorry. What you could do is install this stuff using Vuen's script ([http://ubuntuforums.org/showthread.php?t=297676&highlight=amsn](http://ubuntuforums.org/showthread.php?t=297676&highlight=amsn)) or build all stuff from source by yourself and install it on /usr/local.

---

### Post by Starlight on 2007-12-30
Thanks...maybe I'll try this script. :) But the script was made before the final version of aMSN 0.97 was released... will it install it correctly?

Or maybe I should just wait for them to make official Ubuntu packages...

---

### Post by patrickfromspain on 2007-12-30
I believe it should install the latest version. Check that page, the answer should be there.

---

### Post by picpak on 2007-12-30
A little help...this is what it tells me...

"Loading TkCximage failed. This module is needed to run aMSN. Please compile aMSN first, instructions on how to compile are located in the file INSTALL".

---

### Post by mac-duff on 2007-12-30
Hi patrickfromspain,
thanks! I uninstalled your packages and reinstalled the old 8.4 versions. reinstalled your versions and now it works.
Thx

---

### Post by rainwalker on 2007-12-30
Sweet! aMSN actually looks nice now! And my webcam works!
You rock

---

### Post by patrickfromspain on 2007-12-30
> **picpak said:**
> A little help...this is what it tells me...

"Loading TkCximage failed. This module is needed to run aMSN. Please compile aMSN first, instructions on how to compile are located in the file INSTALL".
Are you sure you installed all of my three packages? Could you please do:

sudo updatedb
locate tclsh8.5
locate wish8.5
locate amsn

and post the outputs?

thanx

---

### Post by picpak on 2007-12-30
I removed all other tcl's and tk's and reinstalled yours. It worked, thanks!

---

### Post by p0g0 on 2007-12-31
It works!!! thanks man :guitar:

---

### Post by Dyn-o-mite on 2008-01-03
Hi.

I've tried to install your 3 packages but in the end when i try to run aMSN it loads for a few seconds and then just disappear from the bar without any message. What could be the cause of that?

Sorry for my english :X

Thanks in advance

---

### Post by patrickfromspain on 2008-01-03
open a terminal and there, type amsn and post the error message you get.

---

### Post by Dyn-o-mite on 2008-01-03
hey.

This is what console shows:
```

jeremias@ubuntu:~$ amsn
Error in startup script: extra characters after close-brace
    while executing
"set command [list  $self  {expand}$Snit_optionInfo(configure-$option)  $option]
            "
    invoked from within
"if {$Snit_optionInfo(configure-$option) eq ""} {
                set command [list set ${selfns}::options($option)]
            } else {
             ..."
    (procedure "snit::RT.CacheConfigureCommand" line 32)
    invoked from within
"snit::RT.CacheConfigureCommand  $type $selfns $win $self $option"
    (procedure "::snit::RT.method.configurelist" line 7)
    invoked from within
"::snit::RT.method.configurelist $type $selfns $win $self $args"
    (procedure "::snit::RT.method.configure" line 4)
    invoked from within
"$self configure -width $arrow1width"
    (procedure "::pixmapscrollbar::Snit_constructor" line 52)
    invoked from within
"::pixmapscrollbar::Snit_constructor ::pixmapscrollbar ::pixmapscrollbar::Snit_inst1 .plugins_log.ys .plugins_log.ys -command {.plugins_log.info yview}"
    ("eval" body line 1)
    invoked from within
"eval [linsert $arglist 0  ${type}::Snit_constructor $type $selfns $instance $instance]"
    (procedure "RT.ConstructInstance" line 9)
    invoked from within
"RT.ConstructInstance $type $selfns $name $args"
    (procedure "::snit::RT.widget.typemethod.create" line 54)
    invoked from within
"scrollbar $window.ys -command "$window.info yview""
    (procedure "::pluginslog::draw" line 12)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 210)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 27)
    invoked from within
"uplevel \#0 {

        # amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
        source amsncore.tcl
        source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 257)
 
```

---

### Post by patrickfromspain on 2008-01-03
no idea what's happening there, could you please do the following:

sudo apt-get remove --purge tcl8.5 tk8.5 amsn and then reinstall all of my three packages? You should install first tcl8.5, then tk8.5 and at last amsn.

---

### Post by Dyn-o-mite on 2008-01-03
before i do that i have one question. it is right your aMSN package to install tcl8.3? i have installed tcl/tk 8.5 (yours) and tcl/tk 8.3. Could that be the problem?

thanks

---

### Post by patrickfromspain on 2008-01-03
yes, that's right, since tcl8.3 is needed for tcltls. The problem isn't coming from there, since I've changed /usr/bin/amsn to point to wish8.5.

---

### Post by Dyn-o-mite on 2008-01-03
Ok.

Another thing.  [This]("http://tostamista.planetaclix.pt/Screenshot45436.png") shows when open de aMSN .deb (after install the other two).

I wrote the following commands on the console and the output is this:
sudo updatedb
locate amsn

```

/home/jeremias/.amsn
/home/jeremias/.amsn/config.xml
/home/jeremias/.amsn/gconfig.xml
/home/jeremias/.amsn/langlist.xml
/home/jeremias/.amsn/logs
/home/jeremias/.amsn/plugins
/home/jeremias/.amsn/profiles
/home/jeremias/amsn_received
/home/jeremias/amsn_received/aaaa.mp3.incomplete
...
/home/jeremias/amsn_received/zcxz.mp3
/home/jeremias/.amsn/skins
/home/jeremias/.amsn/smileys
/home/jeremias/.amsn/states.xml
/home/jeremias/.amsn/webcam
/home/jeremias/Desktop/amsn-0.97-1.tcl85.x86.package
/home/jeremias/Desktop/amsn_0.97+dfsg-1.deb
/home/jeremias/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fgarlou%2F.amsn%2Fskins.xml
/home/jeremias/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fgarlou%2Famsn_received.xml
/usr/share/app-install/desktop/amsn.desktop
/usr/share/doc/amsn-skins
/usr/share/doc/amsn-skins/copyright
/usr/share/icons/amsn.png
/usr/share/sgml/entities/sgml-iso-entities-8879.1986/ISOamsn.ent
/usr/share/sgml/entities/sgml-iso-entities-9573-13.1991/ISOamsn.ent
/usr/share/xml/entities/xml-iso-entities-8879.1986/ISOamsn.ent
/var/cache/apt/archives/amsn_0.97RC1+dfsg-0ubuntu1_i386.deb
/var/lib/dpkg/info/amsn-skins.list
/var/lib/dpkg/info/amsn-skins.md5sums
/var/packages/amsn
/var/packages/amsn-0.97
/var/packages/@amsn-project.net
/var/packages/@amsn-project.net/amsn:0.97
/var/packages/@amsn-project.net/amsn:0.97/baseline
/var/packages/@amsn-project.net/amsn:0.97/environment.en
/var/packages/@amsn-project.net/amsn:0.97/files
/var/packages/@amsn-project.net/amsn:0.97/log
/var/packages/@amsn-project.net/amsn:0.97/uninstall
/var/packages/@amsn-project.net/amsn:0.97/verification

```

---

### Post by patrickfromspain on 2008-01-03
Strange... I suppose the list you have posted is incomplete. If you have installed my amsn packages, there should be files under /usr/bin/amsn and /usr/share/amsn.

About the screenshot.. that's normal and fine. My package is a newer version than the one in the ubuntu repos, so that's fine.

You could also try mv ~/.amsn ~/.amsn-copy

---

### Post by Free Penguin on 2008-01-04
If you want here there is a simple (and tested) guide to install aMSN SVN with tcl/tk 8.5 with antialiasing on Ubuntu: [http://www.freepenguin.it/tip8-en.html](http://www.freepenguin.it/tip8-en.html)


Free Penguin

---

### Post by patrickfromspain on 2008-01-04
That guide uses Treviños repo's, which have a very old tcl/tk8.5 version (alpha 5). It also installs tile (used for chameleon, which isn't developed anymore) and you have to compile amsn, which means you will have to install some build-depedencies and will be harder to uninstall.

Honestly, I don't see that any better than my packages.

---

### Post by patrickfromspain on 2008-01-04
Added tcltls package so that installing this won't require tcl8.3 or tcl8.4 anymore.

---

### Post by rainwalker on 2008-01-04
> **patrickfromspain said:**
> Added tcltls package so that installing this won't require tcl8.3 or tcl8.4 anymore.

So what do we do if we already installed it?

---

### Post by patrickfromspain on 2008-01-04
if it works.. don't fix it ;)

---

### Post by rainwalker on 2008-01-04
Ah, very good point.

---

### Post by maistr on 2008-01-05
thank you very much..

it works fine

---

### Post by fepa on 2008-01-08
YES, aMSN FINALLY works! Thank you very much!! :D :KS

---

### Post by terrax on 2008-01-15
Thx for the packages :-) Im am packaging amsn-98b for myself, but can you get me the dev packages for tcl, tk and tlscls ? :-) Would be nice. Thx in advance.

---

### Post by patrickfromspain on 2008-01-15
Sure, here they are:

tk8.5-dev: [http://in.solit.us/archives/download/118166](http://in.solit.us/archives/download/118166)

tcl8.5-dev: [http://in.solit.us/archives/download/118167](http://in.solit.us/archives/download/118167)

---

### Post by terrax on 2008-01-17
Thank you very much :-)

---

### Post by icarlos on 2008-01-19
Finally, it works very fine.

Thanks=D>

---

### Post by VoXoM on 2008-01-19
Cheers, it's great.

---

### Post by gsiliceo on 2008-01-19
The profiles feature is broken in this version dont use it if you share your amsn with another  person.

---

### Post by Norrbagge on 2008-01-25
This worked like a charm... Thanks alot for providing it for us... =D>

---

### Post by Speedboy on 2008-03-23
Thanks for the packages, amsn looks and works great now!

---

