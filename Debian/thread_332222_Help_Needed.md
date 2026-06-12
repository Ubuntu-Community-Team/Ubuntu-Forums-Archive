---
title: "** Help Needed **"
date: 2007-01-05
forum: Debian
---

### Post by tacubuntuforums on 2007-01-05
Hello:
I need help urgently.
Desperately, I'm writing here, though my problem is in a debian system installation.

I was updating packages (stable version) but my usual source is not working. I changed the sources list to a foreign one (in UK). Since my package firefox1.5 was not there I added a testing source so that the sources.list was like this:

deb [http://security.debian.org/](http://security.debian.org/) stable/updates main contrib
deb [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) stable main contrib
deb [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) testing main contrib

Using aptitude interactively, I choosed the desired package for upgrade. Everything seemed to be ok and it was a small upgrade. I pressed 'g' wchich means to accept the selected changes and I saw a large list of packages to be deleted. It seemed strange, but since I was tired and wanted to finish quickly I just pressed 'g' again which means to start making the downloads and deletions presented.
I could believe it when I saw that it was going to take 15 minutes (1Mb ADSL) and when I started to see the large list of packages being downloaded. At almost the end of the process, I'm asked if I want to remove the kernel ( a dangerous operation). Of course I answered no. The process stoped asking me to press ENTER to continue. Thats when I started to read all what was going on. A large list of packages deleted.. I can't believe it WHY??

Here is the ouput of the process. Maybe I can make also list of the new packages from the cache.

SO, MY QUESTION IS WHAT CAN I DO??
CAN I DO SOMETHING TO RECOVER THE SITUATION BEFORE PRESSING 'ENTER' OR BEFORE REBOOTING ??

[HTML]sudo aptitude
Preconfiguring packages ...
(Reading database ... 75404 files and directories currently installed.)
Removing kdemultimedia ...
Removing akode ...
Removing kdeutils ...
Removing ark ...
Removing kde-core ...
Removing arts ...
Removing noatun ...
Removing krec ...
Removing artsbuilder ...
Removing base-config ...
Removing gnome-desktop-environment ...
Removing gnome-core ...
Removing bug-buddy ...
Removing file-roller ...
Removing bzip2 ...
Removing nautilus-media ...
Removing gnome-applets ...
Removing gdm ...
Removing gnome-terminal ...
Removing nautilus ...
Removing nautilus-cd-burner ...
Removing cdrecord ...
Removing totem ...
Removing totem-xine ...
Removing gnome-volume-manager ...
Removing pmount ...
Removing libnautilus-burn0 ...
Removing hal ...
Removing libhal-storage0 ...
Removing libhal0 ...
Removing dbus-glib-1 ...
Removing dbus-1 ...
Stopping system message bus: dbus-1.
Removing kdenetwork ...
Removing dcoprss ...
Removing gnome-panel-data ...
Removing gnome-panel ...
Removing gnome-session ...
Removing gnome-control-center ...
Removing capplets ...
Removing capplets-data ...
Removing desktop-base ...
Selecting previously deselected package tzdata.
(Reading database ... 72269 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2006p-1_all.deb) ...
Replacing files in old package libc6 ...
(Reading database ... 72296 files and directories currently installed.)
Removing kernel-image-2.6.8-2-386 ...

  You are running a kernel (version 2.6.8-2-386) and attempting to remove
  the same version. This is a potentially disastrous action. Not only
  will /boot/vmlinuz-2.6.8-2-386 be removed, making it impossible to boot
  it, (you will have to take action to change your boot loader to boot
  a new kernel), it will also remove all modules under the directory
  /lib/modules/2.6.8-2-386. Just having a copy of the kernel image is not
  enough, you will have to replace the modules too.

    I repeat, this is very dangerous. If at all in doubt, answer
    no. If you know exactly what you are doing, and are prepared to
    hose your system, then answer Yes.
Remove the running kernel image (not recommended) [No]? no
dpkg: error processing kernel-image-2.6.8-2-386 (--remove):
 subprocess pre-removal script returned error exit status 1
dpkg: initrd-tools: dependency problems, but removing anyway as you request:
 kernel-image-2.6.8-2-386 depends on initrd-tools (>= 0.1.63).
Removing initrd-tools ...
Errors were encountered while processing:
 kernel-image-2.6.8-2-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Setting up tzdata (2006p-1) ...
Current default timezone: 'Europe/Madrid'.
Local time is now:      Fri Jan  5 23:32:12 CET 2007.
Universal Time is now:  Fri Jan  5 22:32:12 UTC 2007.
Run 'tzconfig' if you wish to change it.

Press return to continue.
[/HTML]

I am starting to see that a few items in the desktop menus are being changed.

I'll be here waiting for your help.

Thank you.

---

### Post by teaker1s on 2007-01-05
save the list. I don't know about debian but with ubuntu until you reboot  you could reinstall the system by example

apt-get install kde
apt-get install ubuntu-base
apt-get install ubuntu-desktop

so why not just reinstall the removed components

---

### Post by Sef on 2007-01-05
Moving this post to the Debian Forum.

---

### Post by tacubuntuforums on 2007-01-05
Hi:
Well, that was fast!

It's Debian Sarge 3.1 all had been stable upgrades for a year.

I'm affraid that the system does not work ok after pressing ENTER to continue... or after rebooting.
I could try to install those packages before, runing aptitude in another console, but I'm affraid to make a mess in the databases

---

### Post by tacubuntuforums on 2007-01-05
Oh! C'mon Sef!!. I was thinking about that, but it's an Emergency for me. I posted here because I'm a user of this forum and I thought any answer would be valuable also for Ubuntu users (like me). This situation could be happening in any Linux distro. It 's not a Distro especific thing. PLEASE. I'd like to solve it right NOW!

---

### Post by teaker1s on 2007-01-05
install before reboot,  or you could be buggered
you could install synaptic which you can set recommended packages as dependencies in preferences and you won't have dependency nightmare

---

### Post by HarrisonHopkins on 2007-01-05
Yes, I had this exact same problem with Kubuntu 6.06 LTS. I tried everything, but it uninstalled my network drivers. I had to do an entire reinstall.

---

### Post by tacubuntuforums on 2007-01-05
Are you shure??? This is no fun. What will happen, then?

Should I do it before or after pressing the last 'Enter' (or it doesn't matter)?

Have you read well all this:

Removing base-config ...
Removing gnome-desktop-environment ...

Stopping system message bus: dbus-1.
Removing gnome-panel-data ...
Removing gnome-panel ...
Removing gnome-session ...
Removing gnome-control-center ...
Removing capplets ...
Removing capplets-data ...
Removing desktop-base ...

Whta the hell have I got now, then.

---

### Post by tacubuntuforums on 2007-01-05
Well, but there must be many other things to take into consideration, no?

First try to backup personal data.
Second: is it possible to see if I could save configuration data
How can I know if the config files may be reused. I suppose they do, but probably I shouldn''t replace whole folders in case I need to reinstall.

---

### Post by teaker1s on 2007-01-05
can also burn deb packages to cd and
apt-cdrom add
apt-get upgrade

then install deb packages if networking is down

I'd just reinstall the removed packages,you may find they are just removed and not purged from cache

---

### Post by tacubuntuforums on 2007-01-05
I believe that trying to revert the situation would include replacing the installed packages too (because I don't know what's there and what incongruencies there might be)

Is there any way to know which packages have been installed today?

If I go to

/var/cache/apt/archives/

y can see the downloaded packages in the cache since the system's birth, because I haven't deleted anything. But can I list by creation time or show the creation time?

---

### Post by RAV TUX on 2007-01-05
Edited thread title to:
> 
** HELP NEEDED **

---

### Post by tacubuntuforums on 2007-01-05
To make things worse I am starving and slept little yesterday.... pff!

 I can think of many things but I can't know which are right or which steps  make the safest path.

What about just updating the whole system while I have network? or upgrading?

But I don't know how should I do it?

first update, then upgrade? using testing, or going back to just stable?

(Debian has, for each version: stable, testing and unstable subversions)
I had always used stable until now that I wantes a package from testing.

Thinking about what you said..The problem is that those are the packages I had installed, but maybe others have been removed and besides maybe some of the recently installed ones (I still don't know which are they)  will cause trouble (is this possible? in which cases?)

I'm thinking of two main ways of restoring this mess:
1) whith an intelligent, wise upgrade ...but how?
2) trying to have a list of all packages removed, all installed ones and trying to rebuild the puzzle. (when I'm able to think more clearly again)

---

### Post by teaker1s on 2007-01-05
still think your best way if synaptic is available to use it with recommended packages as dependencies. it allows you to see broken packages and either reinstall or remove. I think your panicing too much as apt-get/synaptic/aptitude etc all use the same info to tell whats installed.

---

### Post by tacubuntuforums on 2007-01-05
I know that all package managers work with the same database and sources. That's not what troubles me.
What I don't see clearly is exactly how to use it. Exactly what steps to do.

If I start downloading the removed packages in the list (I don't know if they were deleted because thre was an incompatibility...which I doubt), 

(a)Should I use the "testing" sources or just "stable". As I said I had always used stable, but now some packages have been downloaded now ( but I don't know which ones. How can I know? Is there any creation date?)

(b) Should I remove things first?
(c) What about configurations? what should I do about them? If I install a removed package which left the configuration files (has not been "purged") will it respect the configuration?

---

### Post by teaker1s on 2007-01-05
again as I said before if you can install synaptic it will tell you what packages it needs to remove when you install the list of the now removed packages. and if you select recommended as dependencies-what ever you reinstall will not break your system with incompatible packages or missing dependencies

---

### Post by tacubuntuforums on 2007-01-05
OK, I'll do that.

The first decision is how to work with synaptic. With what sources.list.

If I want to have as many packages as possible from the "stable" repository, but I have ,in this last disastrous operation, installed a number of packages (i still don't know which ones and how many, but i believe they were a lot)  from the "testing". Can I be at ease using synaptic with "stable".

apt-get **-f** install synaptic

right?

---

### Post by teaker1s on 2007-01-05
synaptic won't work while terminal has apt-get running in any form due to lock. - terminals will need closing first.

 I'd recommend you went for stable for sources. 
Synaptic preferences will allow you to select upgrade packages under distribution -I'd select stable or what ever you consider most suitable to what your system was before this issue.

---

### Post by tacubuntuforums on 2007-01-05
[COLOR="Red"]Sorry: the lock was: sudo missing. uuuuuh! I'm so terribly tired![/COLOR]

Yes, there's the trouble:

Also, should I use **-f** option or first download  the package **initrd-tools ** the kernel needs?


$sudo apt-get install synaptic
...
The following packages have unmet dependencies:
  kernel-image-2.6.8-2-386: Depends: initrd-tools (>= 0.1.63) but it is not going to be installed
  synaptic: Depends: libapt-inst-libc6.3-6-1.1
            Depends: libapt-pkg-libc6.3-6-3.11
            Depends: libatk1.0-0 (>= 1.12.1) but 1.8.0-4 is to be installed
            Depends: libc6 (>= 2.3.6-6) but 2.3.2.ds1-22sarge4 is to be installed
            Depends: libcairo2 (>= 1.2.0) but it is not going to be installed
            Depends: libgcc1 (>= 1:4.1.0) but 1:3.4.3-13sarge1 is to be installed
            Depends: libglade2-0 (>= 1:2.5.1) but 1:2.4.2-2 is to be installed
            Depends: libglib2.0-0 (>= 2.10.0) but 2.6.4-1 is to be installed
            Depends: libgtk2.0-0 (>= 2.8.0) but 2.6.4-3.1 is to be installed
            Depends: libncurses5 (>= 5.4-5) but 5.4-4 is to be installed
            Depends: libpango1.0-0 (>= 1.12.3) but 1.8.1-1 is to be installed
            Depends: libstdc++6 (>= 4.1.0) but it is not going to be installed
            Depends: libvte4 (>= 1:0.12.1) but 1:0.11.12-1 is to be installed
            Depends: libxfixes3 but it is not going to be installed
            Depends: libxinerama1 but it is not going to be installed
            Depends: libxml2 (>= 2.6.26) but 2.6.16-7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


[COLOR="Red"]Close terminals? 
I have just one graphic terminal. Thje other one is waiting "enter"
gnome-terminal package has been removed![/COLOR]

---

### Post by tacubuntuforums on 2007-01-05
As far as I see, in three removed packages, the config files are still there.
Do you know it they will they be overwritten if I reinstall the packages?

---

### Post by teaker1s on 2007-01-05
If this was my situation I'd resolve dependencies and use synaptic, I'm x windows user so I prefer graphical solutions- that said this webpage will [help]("http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106")
it explains apt-get and dependency problems Debian.
another way would be to download missing deb packages and possibly ctrl-alt-f1 and root terminal outside gnome and apt cdrom add and install required packages. 

If all else fails your best bet leave it on and sleep and fix it in the morning;)

---

### Post by tacubuntuforums on 2007-01-06
Thank you teaker1s for your support!

All looks 100%OK now. UUUuuuf!
Well I decided to continue instead of gpoing to sleep, So I slept very little.
I was afraid of problems that might arose and the possible complication of the situation.

First I made some backups in a separate partition from the one that had the kernel and took notes of everything. The system was crumbling.

I went restoring the packages in my list, little by little, but afterwards there were more packages (a lot!) marked for deletion, packages broken and a mess. I didn't want to keep many things that might be completely new and I didn't need.

[COLOR="Gray"]When I was finishing I found an inconsistency. One important package needed package-A; another package needed package-B, but A and B were incompatible. So I had to leave one proposed package for instal.lation, which didn't seemed necesary (but the sistem was marking for insta.lation), in order to keep the xserver.[/COLOR] [COLOR="Red"](*WRONG - corrected down*)[/COLOR]

It was very tiredsome but I wanted to monitor everything step by step.

I'll do what you say and now try synaptic in this system  too. The apt-get and aptitude thing are compatible deep inside but a bit chaotic egarding the information the user needs to manage as a whole.

Well, I got scared. The lesson is that any small thing, mistake (was there?) can make a disorder. But Linux behaved well, over its feet.

Thanks!

---

### Post by teaker1s on 2007-01-06
turned out good in the end\\:D/

---

### Post by tacubuntuforums on 2007-01-07
That was badly written. Now that my mind works better, I'l explain it better.

Xserver needed package-A while another package, marked for instal.lation, needed package B. Package A was going to be removed because B covers A (it must be newer) but xserver didn't accept having B and not having A (thing that looks like a bug to my inexpert eyes). I knew that because, in that case, aptitude marked the xserver as a broken package. Moreover A and B couldn't live at the same time (B got marked as broken). So I took out both: B and one package which needed B from a small group of related packages marked for instal.lation, which didn't seem necessary, just recommended and had to do with multimedia, cd+dvd recordings, etc.. I dont understand why they were going to be installed if they were not strictly necessary, just suggested or recommended (i don't know now and I find all that terminology confusing).

One thing I didn't know was if reinstaling a package would preserve the configuration. I knew some packages were not purged (left the config files there) but I didn't know if that was the case for the rest.

Anyway, it had a happy ending and everything looks exactly the same.

I installed synaptic. I knew it and had already used it a few times in Ubuntu. I like the visual aspect, besides you don't need to write so much, remember so much, and the presentation is better, but the truth is that for some things is slower. So I'll keep and ocassionally use the comand line.

---

### Post by teaker1s on 2007-01-08
only point to watch is when removing packages it doesn't take another you still need;)

---

