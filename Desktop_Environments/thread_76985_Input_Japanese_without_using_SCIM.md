---
title: "Input Japanese without using SCIM"
date: 2005-10-16
forum: Desktop Environments
---

### Post by dauvm on 2005-10-16
*Edit:* Turns out that ["gnomerc file can't contain input method-related information anymore"]("https://wiki.ubuntu.com/JapaneseInputHowto"). I *did* search, I swear, before writing my own way, but it turns out someone has already done a fine job on the Ubuntu Wiki page. Although my way worked fine for me, the Wiki page follows the same steps, but gives you more options in the long run. I suggest you use [JapaneseInputHowToInBreezy]("https://wiki.ubuntu.com/JapaneseInputHowToInBreezy").

For a lot of people, upgrading to Breezy and trying to install SCIM doesn't work so well. For me, SCIM on a fresh install of Breezy was terrible. All programs hung before loading, scim-setup segfaulted, and even after all that, no Japanese input.

So, in the meantime, until the devs or upstream gets SCIM working again, here's a workaround to easily get Japanese input for people that need it.

With universe repository enabled, do:
```
sudo apt-get install uim uim-anthy uim-applet-gnome
```

Then right click on the gnome-panel and click "Add to Panel..." and scroll all the way to the bottom, under utilities you should find "uim Applet". Add that to the panel, then click on the setup icon and change **Default input method** to **Anthy**.

Open up any program and hit **shift + space** and start typing Japanese... worked for me in firefox and openoffice too.

&#32066;&#12431;&#12426;&#12391;&#12377;&#65281;&#65342;&#65343;&#65342;
-Doug

---

### Post by hpn on 2005-10-16
> For a lot of people, upgrading to Breezy and trying to install SCIM doesn't work so well. For me, SCIM on a fresh install of Breezy was terrible.


Same here.

For those who've been using SCIM, upgrading to breezy is nothing short of nightmare. Not only Japanese, but SCIM is used to input many other Asian languages.

Here's a list of applications that have been segfaulting for me:
*  Mousepad
*  Leafpad
*  Synaptic
*  theme-manager
*  Scim-setup

and maybe lot more. Since SCIM daemon seems to start with most GNOME based apps, the whole installation with SCIM is appearing rather unstable at the moment. :-|

---

### Post by hanzj on 2005-10-16
Yes, programs from menu such as synaptic or add_applications hang for about 10 seconds and then do not load at all. 
un-installing scim solved this problem.
Just one problem with uim. I can get to type japanese in gedit and openoffice programs, but i can't type japanese into opera. why not?

---

### Post by hpn on 2005-10-16
[QUOTE=hanzj] I can get to type japanese in gedit and openoffice programs, but i can't type japanese into opera. why not?[/QUOTE]

Although I ain't sure, my quick guess is that Opera uses QT library. But SCIM doesn't yet work on KDE stuff. I think they're working on it. Correct me if I'm wrong.

---

### Post by hanzj on 2005-10-16
Hpn said:
> my quick guess is that Opera uses QT library. But SCIM doesn't yet work on KDE stuff as of now. I think they're working on it.


Just to clarify:
 I uninstalled scim packages and installed uim instead. 
I use Ubuntu Gnome. i don't use kubuntu.

Does your comment still apply?

---

### Post by Liet on 2005-10-16
How to install Scim and anthy in Breezy:

-Uninstall all scim and uim related things.

-sudo apt-get apt-build

-Add 'deb-src [ftp://ftp.ie.debian.org/debian/](ftp://ftp.ie.debian.org/debian/) unstable main non-free contrib' to your apt sources list.

-sudo apt-get update

-sudo apt-build build-source scim'.

-sudo apt-build build-source scim-anthy'.

-sudo apt-get anthy

-cd /var/cache/apt-build/repository

-sudo dpkg -i *.deb

-sudo gedit /etc/X11/Xsession.d/75custom-scim_init

Paste this:

export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=xim
glgo &
export XIM_PROGRAM="scim -d

-mkdir ~/.scim

-echo '/SupportedUnicodeLocales = en_US.UTF-8,put_your_locale_here' > ~/.scim/global

-sudo su

-gtk-query-immodules-2.0 > /etc/gtk-2.0/gtk.immodules


It works fine ;)

---

### Post by hanzj on 2005-10-16
[QUOTE=Liet]sudo apt-get apt-build[/QUOTE]

I did the above, but got:
> E: Invalid operation apt-build


[QUOTE=Liet]echo '/SupportedUnicodeLocales = en_US.UTF-8,put_your_locale_here' > ~/.scim/global[/QUOTE]
how do i find out my locale?

---

### Post by hpn on 2005-10-16
[QUOTE=Liet]
It works fine ;)[/QUOTE]

followed the same set of steps. Its stopping halfway:

```
Skipping unpack of already unpacked source in scim-1.4.1
-----> Building scim <-----
Can't chdir(scim-1.0.2): No such file or directory at (eval 1) line 3
        main::__ANON__('scim-1.0.2') called at /usr/bin/apt-build line 286
        main::build('scim', 1.0.2, -3) called at /usr/bin/apt-build line 603
        main::build_source called at /usr/bin/apt-build line 82

```

---

### Post by hpn on 2005-10-16
>  E: Invalid operation apt-build

you need to install ap-build first:
> sudo apt-get install apt-build

---

### Post by hanzj on 2005-10-16
Since you're getting problems, maybe I'll wait until I know it works.

Besides, I don't know whether SCIM is any better than UIM. Do you?

---

### Post by hpn on 2005-10-16
Just as I filed a bug here:
[https://launchpad.net/distros/ubuntu/+sources/scim/+bug/3237](https://launchpad.net/distros/ubuntu/+sources/scim/+bug/3237)

I found a discussion on about the same thing on launchpad:
[https://launchpad.net/distros/ubuntu/+sources/scim/+bug/2565](https://launchpad.net/distros/ubuntu/+sources/scim/+bug/2565)

Looks like updated debs are available from here:
[http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/](http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/)

let me know if anyone tries this out.

---

### Post by Liet on 2005-10-17
[QUOTE=hanzj]I did the above, but got:

>  E: Invalid operation apt-build

> Originally Posted by Liet
echo '/SupportedUnicodeLocales = en_US.UTF-8,put_your_locale_here' > ~/.scim/global
how do i find out my locale?[/QUOTE]

Sorry, I installed apt-build via synaptic, so I put the wrong command for apt-get :oops:  Try installing with synaptic

To find you locale:

**sudo gedit /etc/environmen**t

and see what is your default locale. To change the default locale:

**sudo dpkg-reconfigure locales**

[QUOTE=hpn]followed the same set of steps. Its stopping halfway:

```
Skipping unpack of already unpacked source in scim-1.4.1
-----> Building scim <-----
Can't chdir(scim-1.0.2): No such file or directory at (eval 1) line 3
        main::__ANON__('scim-1.0.2') called at /usr/bin/apt-build line 286
        main::build('scim', 1.0.2, -3) called at /usr/bin/apt-build line 603
        main::build_source called at /usr/bin/apt-build line 82

```[/QUOTE]

I don' t know, I read on a post of Breezy development a how to for installing scim, I followed and worked for me. Them I put it here to help other people, I'm not a scim expert, sorry.

But in the other hand the Debs that are in [http://svn.ubuntu.org.cn/ubuntu-cn/d...ary-i386/scim/](http://svn.ubuntu.org.cn/ubuntu-cn/d...ary-i386/scim/) are the same wich generates apt-build, so download and install all of them, I supose that it will work.

---

### Post by kairu0 on 2005-10-18
If all you need is Japanese support, you can easily follow the first post in this thread to get UIM running.

If, however, you need other languages or use QT applications with Japanese, SCIM is probably better.

---

### Post by hanzj on 2005-10-19
[QUOTE=Liet]To find your locale:

**sudo gedit /etc/environment**

and see what is your default locale. 
[/QUOTE]


Mine says:
> LANGUAGE="en_JP:en"

LANG=en_US.UTF-8


I'm not even sure if this info is correct. Here's the thing. I bought a computer in Japan. The keyboard is meant for Japanese people. I use Dvorak layout for both inputting english (roman letters) and Japanese. Because my first language is English, and because I do most of my computer work in English, I'd like the default to be in English (Dvorak) but be able to switch to dvorak Japanese when need be. With this info in mind, what should my locale be?

---

### Post by Liet on 2005-10-19
I supose your locale should be:

> LANGUAGE="en_JP:en"

LANG=en_US.UTF-8

Because your key board is Japanese, and for ensure yo have Japanese suport do:

**sudo dpkg-reconfigure locales**

And check if you have the two Japanese fonts checked.

---

### Post by Psimon on 2005-10-19
QUOTE:  I don't know whether SCIM is any better than UIM. Do you?


I've used both depending on which installs easiest. They're both great when they work but everytime I upgrade (previously I was on Mandriva and it was the same there) one of them breaks and I have to switch. If anything UIM seems simpler and is usually the more reliable. At the end of the day I'd just like anyone of them to work consistently.

---

### Post by Kushou on 2005-10-22
[QUOTE=hpn]Just as I filed a bug here:
Looks like updated debs are available from here:
[http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/](http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/)

let me know if anyone tries this out.[/QUOTE]

Hi, I tried install all the pkgs there and scim is still not working.

---

### Post by Kushou on 2005-10-22
Hi Guys, I got SCIM up running after finding the following info from a chinese website:

```

sudo apt-get install scim scim-gtk2-immodule scim-modules-socket scim-modules-table scim-pinyin scim-tables-zh scim-input-pad 
sudo sh -c " echo 'export XMODIFIERS=@im=SCIM ; export GTK_IM_MODULE="scim" ; scim -d ' > /etc/X11/Xsession.d/95xinput "
sudo chmod +755 /etc/X11/Xsession.d/95xinput

```

Actually I installed scim from synaptic, but thought the last two **[COLOR="DarkRed"]sudo [/COLOR]**commands must be there.

---

### Post by ichigo on 2005-10-24
[QUOTE=hpn]followed the same set of steps. Its stopping halfway:

```
Skipping unpack of already unpacked source in scim-1.4.1
-----> Building scim <-----
Can't chdir(scim-1.0.2): No such file or directory at (eval 1) line 3
        main::__ANON__('scim-1.0.2') called at /usr/bin/apt-build line 286
        main::build('scim', 1.0.2, -3) called at /usr/bin/apt-build line 603
        main::build_source called at /usr/bin/apt-build line 82

```[/QUOTE]

I had the same problem. So I took the debs from [http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/]("http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/") and installed them.
Then Scim worked, but except for the little keyboard-icon it didn't do much. The icon didn't react. (I think this was, because of the anthy-plugin missing)
I got back to the
"sudo apt-build build-source scim-anthy"-line and followed the other steps...

This is what actually helped me. Scim is working now. Maybe somebody finds this helpful:)

---

### Post by kairu0 on 2005-10-26
[QUOTE=ichigo]I had the same problem. So I took the debs from [http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/]("http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/scim/") and installed them.
Then Scim worked, but except for the little keyboard-icon it didn't do much. The icon didn't react. (I think this was, because of the anthy-plugin missing)
I got back to the
"sudo apt-build build-source scim-anthy"-line and followed the other steps...
[/QUOTE]

YES! This is helpful! Now, scim works for me with Kubuntu.

First, I installed the new debs from this link and then I compiled my own scim-anthy deb file from source like ichigo did.

Finally, I put a new file in /etc/X11/Xsession.d to export variables for Japanese (mrbass' HOWTO for Japanese input tells you how to do this), and finally I removed the xinput file in /etc/X11/Xsession.d.

Thanks, ichigo!

---

### Post by ichigo on 2005-10-27
[QUOTE=kairu0]
Thanks, ichigo![/QUOTE]
You're welcome!

---

### Post by Rounin on 2005-10-28
SCIM has a better menu and better support for Chinese. For inputting Japanese, scim-anthy is roughly equvalent to uim-anthy, and I guess the same might be the case for prime.

---

### Post by t3g on 2005-10-31
Just in came someone reading this thread doesn't know (like me who didn't realise it right away :)
New debian packages for scim-pinyin and scim-tables (and even scim-anthy, for those that thought they had to compile it themselves ;)) are accessible using the same link. Just remove the /scim/ at the end of the adress and pick up the folder you need.
Or click
[http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/](http://svn.ubuntu.org.cn/ubuntu-cn/dists/breezy/main/binary-i386/)

Don't know what you think, but in the case of a package as broken as scim, the developper could rethink their "only updates are for security issues" policy. 
Since the scim provided by breezy is not just malfunctionning but ***really*** cause big trouble issues with other (sometime criticall for **security**) packages, they might consider it as a security matter.

Not to say that most people using breezy with scim installed will not be able to guess their problems comes from scim and will just judge breezy unstabe and bugged, filling bug reports, complaints, shouts and thus distracting them from better issues...

**If you know who could listen to this explanation amid ubuntu devs, please forward this post or let me know. **
I had to install breezy again on another partition thinking ubuntu was as bad as windows NoUpdatesFormatB4(tm) before realising it all came from scim.

Thanks. Hope it will help somebody.

---

### Post by JesterMania on 2005-11-02
Hi, I followed everything in this thread and now I have SCIM set up in Ubuntu and can enter Japanese perfectly in GNOME.  However, I cannot enter Japanese in KDE/QT applications.  I did a search and found this webpage:  [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/) .  I followed the instructions

```

So if you want to also input in KDE apps while using GNOME do the following:
sudo touch ~/.gnome2/session-manual
echo "[Default]" >> ~/.gnome2/session-manual
echo "num_clients=1" >> ~/.gnome2/session-manual
echo "0,RestartStyleHint=3" >> ~/.gnome2/session-manual
echo "0,Priority=50" >> ~/.gnome2/session-manual
echo "0,RestartCommand=scim -d" >> ~/.gnome2/session-manual
echo "0,Program=scim" >> ~/.gnome2/session-manual 

```

The first sudo command worked, but the echo commands all said Permission denied, even if I place sudo in front of them.  So, I used gedit to manually input the contents into the ~/.gnome2/session-manual file:

```

[Default]
num_clients=1
0,RestartStyleHint=3
0,Priority=50
0,RestartCommand=scim -d
0,Program=scim

```

I restarted and I still cannot enter Japanese in any KDE/QT applications.  If someone can help me on this I'd appreciate it.

---

### Post by ikuya on 2005-11-08
Hi,
Here is another solution:

1. add following apt-line to /etc/apt/sources.list
 deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) breezy/
2. run apt-get update
3. install SCIM 1.4.2 and scim-anthy 0.7.1
 # apt-get install scim-anthy scim-gtk2-immodule

regards,

---

### Post by James Keating on 2005-11-14
[QUOTE=ikuya]
1. add following apt-line to /etc/apt/sources.list
 deb http://archive.ubuntulinux.jp/ubuntu-ja breezy
2. run apt-get update
3. install SCIM 1.4.2 and scim-anthy 0.7.1
 # apt-get install scim-anthy scim-gtk2-immodule
[/QUOTE]

Thank you, thank you. I have SCIM again, much sooner than I had hoped. 

For others who try this, be warned that it can be somewhat scary and confusing.

I advise a simple approach:
1. add this line to /etc/apt/sources.list
    deb http://archive.ubuntulinux.jp/ubuntu-ja  breezy
2. run synaptic, upgrade everything

I usually use apt-get from the command line, but in a complicated situation like this Synaptic is better because you can see what you have and what might be missing.

I added the ubuntu-ja site to sources.list. Then I ran "apt-get update" and "apt-get upgrade." Upgrade told me that several packages would be added, several would be held back, and several would be removed -- all of them formerly essential to SCIM. Eek. I said yes anyway. (Held back apparently means those packages have newer versions, but require libraries I don't have and apt-get can't find.)

I didn't run "apt-get install scim-anthy scim-gtk2-immodule." Instead I started Synaptic to see if I had damaged anything. Several packages were listed as upgradable, including scim-anthy and scim-gtk2-immodule. I upgraded them, plus their dependencies and several other programs listed (Firefox, gnome-utils, klogd, sysklogd, xpdf-japanese). I ignored warnings that the packages couldn't be verified and might contain malware. 

All the new packages are now listed in Synaptic as Installed (local or obsolete).

I now have removed the ubuntu-ja line from sources.list, to avoid possible trouble. "apt-get upgrade" runs like usual. If I have another Japanese-related problem, I will restore the line.

My SCIM-related packages now are:
anthy        
im-switch  
scim         
scim-anthy
scim-gtk2-immodule     
scim-modules-socket 
scim-uim

---

### Post by t3g on 2005-11-14
[QUOTE=James Keating]
I advise a simple approach:
1. add this line to /etc/apt/sources.list
    deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja)  breezy
2. run synaptic, upgrade everything

I wouldn't advise adding anything to /etc/apt/sources.list, especially since it lead you to updating applications that had nothing to do with scim.

IMHO, downloading the packages and installing everything with dpkg -i name_of_the_packages doesn't take much time, isn't complicated and is far more secure.
If Ubuntu is your working environment, I think it's preferable to do it that way. If you don't mind risking to uselessly mess up your system, go ahead.

Btw, packages installed with dpkg will appear in synaptic, as if you had installed them using your method. So I don't see the reason to go as far as changing /etc/apt/sources.list

Feel free to comment. There might be a good reason behind your method, and I would be happy to learn something that would be usefull later.

---

### Post by James Keating on 2005-11-15
Good reason? Reason? Apt-get didn't finish the job, so I went to Synaptic, where I could see what was happening more easily. There may be a better way, but this one worked for me and is simple enough for anyone. I still recommend it for this one particular risky problem. 

This is a one-time-only emergency procedure, to get a working SCIM. I don't say I like it. I just report that it works in this case. I never added an outside archive to sources.list before, and don't intend to again. 

I amend the suggested procedure to:
1. add this line to /etc/apt/sources.list
    deb http://archive.ubuntulinux.jp/ubuntu-ja  breezy
2. run synaptic, upgrade everything
3. remove the above line from sources.list, and forget you ever did this

I agree that downloading and installing with dpkg generally is better. That's what I have done before in the few cases where I needed a program Ubuntu didn't have. But in a case like this, where I needed a whole suite of packages, Synaptic was easier, and easier to check what I had and what I might be missing.

Did you actually update SCIM by downloading the packages and installing them with dpkg? If you did, how did you know which packages you needed? The new set is considerably different from those in Breezy -- many packages are dropped, and others are new. Did you just keep downloading those that were missing, then run dpkg again? And didn't it say that you also needed packages for Firefox, Xpdf-japanese and the like? 

I wasn't happy that non-SCIM programs were updated, but I think it was only to give them Japanese capability. I didn't ask for this improvement, but it's still an improvement.

---

### Post by t3g on 2005-11-15
Hi,
For editing sources.list, everybody has their own preferences. To me, the folders and package names were explicit enough, but it might not be the case for everybody.
Using dpkg seems simpler to me. Look at the packages you need to update in synaptic, dl them and dpkg -i "put here everything at the same time"

For the other programs (not scim-related) I still wouldn't advise installing them. If you only need scim, just keep with scim. Every repo has their own packages, and once added to sources.list, they will of course be suggested. Synaptic will suggest to install them *since* you added the repository, but it doesn't mean you need them.

For those that prefer using synaptic and editing sources.list, it might be good to look at all the packages you are suggested to install and deselect the ones that are not scim related.
It doesn't mean they're bad packages that will mess up your system. Most often they won't.
But once in a while you'll be installing a package that works on sbdy's system but won't on yours cause yours hasn't been ultra-customised as theirs (or vice-versa).
You could, for example, be installing a new kernel that won't boot X cause your proprietary graphic card drivers are not compiled against it.
Don't laugh, it happens :)
And for some people here, Ubuntu is their system for work. Sometimes the only OS they have.

---

### Post by James Keating on 2005-11-15
Thanks. I'll be more selective next time. I posted mainly to let other people know that using the suggested repository, while risky, worked for me, and to say thanks for helping me get SCIM back again.

---

### Post by Onos on 2006-01-06
Hello! I am trying to get either uim or scim set up on a (X)ubuntu system that uses only X11/xfce4 as the graphical front-end.  

It looks like the only workable way involves using gnome or KDE, but if possible... I would prefer to avoid installing those.

My system is a bit "over the hill" and really chugged with gnome on a previous install of gentoo I tried to work with.

Is there anything specific to xfce that I should do differently?

Kind regards...

---

### Post by kairu0 on 2006-01-06
I've run UIM under XFCE just fine in the past without having Gnome or KDE installed.

After installing the UIM packages, I did the following:

1. Created a file called ~/Desktop/Autostart/uim

2. Made it executable ("chmod +x ~/Desktop/Autostart/uim")

3. Added the following to it:
```
#!/bin/sh
uim-toolbar-gtk-systray
```

Assuming you don't have SCIM installed, uim-xim should already be running by the time you login to XFCE.

---

### Post by Onos on 2006-01-07
I will try it out now, I just downloaded all the uim/uim-anthy files I could find in Synaptic, and made sure scim was uninstalled.

---

### Post by Onos on 2006-01-07
Yay! it works.  I do need to be in full on Japanese-language mode for it to work, but that is not a problem, only a minor nuisance of switching profile mode to JP from EN.

Thanks much!

---

### Post by phidippus on 2006-01-12
[QUOTE=dauvm]
Then right click on the gnome-panel and click "Add to Panel..." and scroll all the way to the bottom, under utilities you should find "uim Applet". Add that to the panel, then click on the setup icon and change **Default input method** to **Anthy**.

Open up any program and hit **shift + space** and start typing Japanese... worked for me in firefox and openoffice too.

&#32066;&#12431;&#12426;&#12391;&#12377;&#65281;&#65342;&#65343;&#65342;
-Doug[/QUOTE]

How can I use the gnome applet from KDE?

---

### Post by kairu0 on 2006-01-13
[QUOTE=phidippus]How can I use the gnome applet from KDE?[/QUOTE]

You can run the panel with the same command (uim-toolbar-gtk-systray.) There is also the work-in-progress kubuntu-ja, which offers Japanese UIM packages for KDE. For the record, I never got it to work.

---

### Post by phidippus on 2006-01-13
[QUOTE=kairu0]You can run the panel with the same command (uim-toolbar-gtk-systray.) [/QUOTE]


This command (uim-toolbar-gtk-systray) doesn't exist for me. Do I have to install something? In gnome, the toolbar was there from the beginning, so I didn't have to do anything.

---

### Post by rlgc79 on 2006-01-28
I've posted a HOW-TO 

[http://ubuntuforums.org/showthread.php?p=687776#post687776](http://ubuntuforums.org/showthread.php?p=687776#post687776)

(no need to install strange repositories)

Hope someone finds it useful

Cheers

---

### Post by James Keating on 2006-06-08
Dapper trouble:

If anyone else, like me, installed the SCIM packages from 
[http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) breezy
because the Breezy packages were broken, remove them before upgrading to Dapper. I thought the packages would simply be replaced by Ubuntu's now-newer ones, but I ended up with a tangle of five broken packages (scim-anthy, scim-modules-socket, libfontenc1, libxdmcp6, libxfont1) that couldn't be removed, installed or configured. In the end, I used Synaptic to remove the broken packages, but it also insisted on removing a couple of hundred other packages, one of which was Synaptic itself -- I had to reinstall it from the command line to restore everything. 

So in this situation or others, install non-Ubuntu packages if you must, but remove them before upgrading, then re-install by hand.

It may also help to keep a list of all your installed packages so you have something to refer to if an upgrade goes wrong for any reason. You can create a file called, say, installed-packages with the command
dpkg -l > installed-packages

---

