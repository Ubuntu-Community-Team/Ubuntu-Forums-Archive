---
title: "Klik and Kubuntu"
date: 2005-09-17
forum: Desktop Environments
---

### Post by ltmon on 2005-09-17
Hi all,

If you haven't already, please check out the article at [http://dot.kde.org/1126867980/](http://dot.kde.org/1126867980/)

Note a slight change to the instructions in the article.  Instead of:

> 
- install the klik client: press [Alt]+[F2] and paste:
wget klik.atekon.de/client/install -O - | sh


Open a  Konsole and type:

```

sudo wget klik.atekon.de/client/install -O - | sh

```

I was surprised that this worked so well on my Kubuntu Hoary box.  So far, every Klik package I have tried has worked without a hitch.

The only problems I see are:
- No application icons with the cmg image downloaded.  It just looks like a blank document.
- Bad English translations in some of the dialogs.

A few extensions I would like to see for Klik, and it could be the killer application distrubution method:
- An option to "Install for everyone" by entering the sudo password
- Integration with the kmenu system (i.e. kmenu looks for .Desktop files in each Klik package)
- Some central registration of Klik packages that is updated regularly (i.e. looks to see if the package has been moved or deleted).  This would allow for central updates to all applications.

Has anyone been using Klik regularly?  Does it work this well all the time?  What are your experiences?

L.

---

### Post by jbus on 2005-09-17
Yes, I have Klik installed on my Kubuntu PC and it works pretty well. I like the serverside-apt idea.

This is great because it is similar to the way Mac applications are installed and is makes things much easier, especially for casual users. I know anytime someone compares the Mac way to the linux way there is usually a lot of heated arguments but Mac users really do have it simple. With all the dependencies in one package there is never a problem of conflicting dependencies, you can have multiple versions of the same app peacefully co-exist on the same system and to install you drag the icon to the folder you want the app installed, to uninstall you delete the file. Packages and their settings are portable across computers, If your friends/family wants to try an app you have just email or IM it to them and they just have to click on it... Very simple. 

Currently, I think a few Klik contributers are working on making the package (compressed folder) have the icon of the specific package like Mac only via some scripts. Though from what I could tell it's going to take some extensive reworking of the packages if it is to be accomplished.

---

### Post by OBnascar on 2005-09-17
[COLOR=Blue]ltmon wrote:

Has anyone been using Klik regularly?  Does it work this well all the time?  What are your experiences?[/COLOR]

Well, unfortunately my experiences are all negative. Here is my terminal error:
[COLOR=Red]
root@ubuntu:~#  wget klik.atekon.de/client/install -O - | sh
--05:02:00--  [http://klik.atekon.de/client/install](http://klik.atekon.de/client/install)
           => `-'
Resolving klik.atekon.de... 134.169.172.48
Connecting to klik.atekon.de[134.169.172.48]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,361 [text/plain]

 0% [                                     ] 0             --.--K/s             sh: line 19: /sbin/pidof: No such file or directory
sh: line 21: /sbin/pidof: No such file or directory
38% [=============>                       ] 5,459          5.81K/s             find: /home/jerryo/.mozilla/: No such file or directory
48% [================>                    ] 6,907          5.57K/s             sh: line 45: Xdialog: command not found
100%[====================================>] 14,361         5.07K/s

05:02:04 (5.06 KB/s) - `-' saved [14,361/14,361]

Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
sh: line 45: Xdialog: command not found[/COLOR]

Funny thing is though when i go to the Kubuntu menu, it does show install software from Klik. So then when I go to the program I want to install from Konqueror it does nothing.

I was going to post a separate post on how buggy my Kubuntu 5.04 is. Not much works at all, get so many errors on so many task they are to numberous to post. I installed ubuntu 5.04 on the same hard drive in a new partition and it runs perfect. I don't really want to give up on Kubuntu.

---

### Post by ltmon on 2005-09-18
[QUOTE=OBnascar]
[COLOR=Red]
root@ubuntu:~#  wget klik.atekon.de/client/install -O - | sh
--05:02:00--  [http://klik.atekon.de/client/install](http://klik.atekon.de/client/install)
           => `-'
Resolving klik.atekon.de... 134.169.172.48
Connecting to klik.atekon.de[134.169.172.48]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,361 [text/plain]
 0% [                                     ] 0             --.--K/s             sh: line 19: /sbin/pidof: No such file or directory
sh: line 21: /sbin/pidof: No such file or directory
38% [=============>                       ] 5,459          5.81K/s             find: /home/jerryo/.mozilla/: No such file or directory
48% [================>                    ] 6,907          5.57K/s             sh: line 45: Xdialog: command not found
100%[====================================>] 14,361         5.07K/s

05:02:04 (5.06 KB/s) - `-' saved [14,361/14,361]

Link points to "/var/tmp/kdecache-root"
Link points to "/tmp/kde-root"
sh: line 45: Xdialog: command not found[/COLOR]
[/QUOTE]

Well, easy fixed:

sudo apt-get install xdialog

then try again.

But it's strange that you don't have that in the first place... I thought it was a standard part of Kubuntu.

L.

---

### Post by OBnascar on 2005-09-18
[COLOR=Blue]ltmon wrote: Well, easy fixed:

sudo apt-get install xdialog

then try again.

But it's strange that you don't have that in the first place... I thought it was a standard part of Kubuntu[/COLOR]

Hi ltmon, ok here is my lastest terminal info:
[COLOR=Red]
xxxxx@ubuntu:~$ sudo apt-get install xdialog
Reading package lists... Done
Building dependency tree... Done
Package xdialog is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xdialog has no installation candidate[/COLOR]

Then when I go to the Konqueror browser, click the download link, it does nothing. What do you think ?

---

### Post by ltmon on 2005-09-18
[QUOTE=OBnascar]
Hi ltmon, ok here is my lastest terminal info:
[COLOR=Red]
xxxxx@ubuntu:~$ sudo apt-get install xdialog
Reading package lists... Done
Building dependency tree... Done
Package xdialog is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xdialog has no installation candidate[/COLOR]
[/QUOTE]

Try enabling the extra repositories (look at [http://ubuntuguide.org](http://ubuntuguide.org), near the top), and then install xdialog again.  

I'm not really sure when and from where I installed xdialog, but I'm really surprised that it isn't part of the base installation.

This time for sure!

L.

---

### Post by Mishura on 2005-09-18
I've tried klik, but I keep getting an error message like "cannot mount /tmp/app/1" or something.

---

### Post by drizek on 2005-09-18
this is awesome. the best part is that it works on just about any distro(assuming they choose to support it, so far its the debians and opensuse). it is not meant to be an apt replacement though. apt is still much more efficient than this in terms of hard drive space and this does not have an auto-update feature. this is just mean to be used to test out software or to use something htat hasnt been packaged yet. probably the coolest thing abou it is that you can run software with it with different libraries than the ones installed on your system. so you can run beta apps without having to have all the beta libraries they require, which is ussually a pain in the ass when you are trying to compile something from cvs. 

also, you can even run a full e17 desktop using klik inside of kde in a window. my system is very very messed up right now though(all windows vistas fault i might add) and i cant boot into anything. i really want to try klik out, but im not really sure how i can get my linux box back up without loosing a lot of my data. i really really want to try this out :(.

Hopefully in the future package management will be done by a synaptic-like frontend for autopackage complimented by klik. It will be the end of dependency hell and will make linux #1 in every way when it comes to package management.

---

### Post by ltmon on 2005-09-18
[QUOTE=Mishura]I've tried klik, but I keep getting an error message like "cannot mount /tmp/app/1" or something.[/QUOTE]

I got this error when I installed Klik as a normal user and not as sudo.  Make sure you've done that.

CHeers,

L.

---

### Post by ltmon on 2005-09-18
[QUOTE=drizek]this is awesome. the best part is that it works on just about any distro(assuming they choose to support it, so far its the debians and opensuse). it is not meant to be an apt replacement though. apt is still much more efficient than this in terms of hard drive space and this does not have an auto-update feature. this is just mean to be used to test out software or to use something htat hasnt been packaged yet. probably the coolest thing abou it is that you can run software with it with different libraries than the ones installed on your system. so you can run beta apps without having to have all the beta libraries they require, which is ussually a pain in the ass when you are trying to compile something from cvs. 

also, you can even run a full e17 desktop using klik inside of kde in a window. my system is very very messed up right now though(all windows vistas fault i might add) and i cant boot into anything. i really want to try klik out, but im not really sure how i can get my linux box back up without loosing a lot of my data. i really really want to try this out :(.

Hopefully in the future package management will be done by a synaptic-like frontend for autopackage complimented by klik. It will be the end of dependency hell and will make linux #1 in every way when it comes to package management.[/QUOTE]

I would like to see an apt-get managed "base" system.  THis would be (for example) the DCC base, or the LSB system (plus some upgrades).

All that needs to be done then is to upload a file to the Klik server saying "Kubuntu version X has these packages installed by default..... ", and Klik does the rest.

The redundancy would not be very much if the base system was carefully selected.

From then on we would need:
- A central 'Klik' repository for easy upgrading
- AppFolders supported in KDE to allow cmg's to have proper icons.  The code has been done, but it has not been integrated because there is a security issue to resolve.  Vote for the bug at: [http://bugs.kde.org/show_bug.cgi?id=81772](http://bugs.kde.org/show_bug.cgi?id=81772)
- Full integration in the K-menu (for example, drag to to kmenu to install, drag from the k-menu to trash to uninstall).
- Uber-testing of the popular Klik programs.  Some still fail now because the automatic generation process is not perfect.

and probably a few other things I'm not smart enough to think of (else someone would have done this by now) :)

L.

---

### Post by Mishura on 2005-09-19
I "fixed" klik by adding this to my fstab:

> 
/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

I tried a few packages and they worked.  However, there aren't enough packages that I'm really interested in... most are already in Ubuntu's repos.  I'd like klik to instead of mirroring Debian's repos, to concentrate on programs that aren't packaged.. and to concentrate on programs that don't require half a desktop enviroment to install.

Maybe it's just me, but the idea of installing Gnome with this seems **extremely** unclean.  But something like Inkscape, amaroK, or whatever, yeah.

I'm curious to try this on a Knoppix session, since it seems to be targeted at the "Live CD" people.

---

### Post by ltmon on 2005-09-19
[QUOTE=Mishura]I "fixed" klik by adding this to my fstab:



I tried a few packages and they worked.  However, there aren't enough packages that I'm really interested in... most are already in Ubuntu's repos.  I'd like klik to instead of mirroring Debian's repos, to concentrate on programs that aren't packaged.. and to concentrate on programs that don't require half a desktop enviroment to install.

Maybe it's just me, but the idea of installing Gnome with this seems **extremely** unclean.  But something like Inkscape, amaroK, or whatever, yeah.

I'm curious to try this on a Knoppix session, since it seems to be targeted at the "Live CD" people.[/QUOTE]

It confuses me that there are a lot of libraries and things like "grub" packaged for klik.  I'm not sure how these are useful.

Where an entire DE is useful is for testing.  You can (as a previous poster reported) download an entire E17 desktop in one Klik, test it in an Xnest window (by clicking on the package) and then remove it again by deleting the cmg file.  So testing e.g. an early alpha of KDE could become much cleaner and easier than it is right now.

In general I agree though - the DE should be part of the base system and not an addon.

L.

---

### Post by OBnascar on 2005-09-19
[COLOR=Blue]ltmon wrote: Try enabling the extra repositories (look at [http://ubuntuguide.org](http://ubuntuguide.org), near the top), and then install xdialog again.[/COLOR]

Ok, I'll give that a try......  

[COLOR=Blue]I'm really surprised that it isn't part of the base installation.[/COLOR]

In an earlier post I commented my Kubuntu seems real [COLOR=Red]**"buggy"**[/COLOR]. I have reinstalled it a couple of different times now. I have dial-up so I purchased the install CD, in fact I have two of them, one from Edmunds and one from Budget. 

Let me ask this then, when you burned your 5.04 ISO, did Firefox come with it ? The reason I ask is these CD's do not have Firefox and this is what I am trying to install. My ubuntu 5.04 did come with Firefox on the install CD. I thought Kububtu and ubuntu were supposed to be the same except for KDE ?

---

### Post by drizek on 2005-09-19
[QUOTE=OBnascar][COLOR=Blue]ltmon wrote: Try enabling the extra repositories (look at [http://ubuntuguide.org](http://ubuntuguide.org), near the top), and then install xdialog again.[/COLOR]

Ok, I'll give that a try......  

[COLOR=Blue]I'm really surprised that it isn't part of the base installation.[/COLOR]

In an earlier post I commented my Kubuntu seems real [COLOR=Red]**"buggy"**[/COLOR]. I have reinstalled it a couple of different times now. I have dial-up so I purchased the install CD, in fact I have two of them, one from Edmunds and one from Budget. 

Let me ask this then, when you burned your 5.04 ISO, did Firefox come with it ? The reason I ask is these CD's do not have Firefox and this is what I am trying to install. My ubuntu 5.04 did come with Firefox on the install CD. I thought Kububtu and ubuntu were supposed to be the same except for KDE ?[/QUOTE]
 no, kubuntu uses kde apps and ubuntu uses gnome apps. its because they look and integrate better that way. firefox in linux overall is a mess, and its especially bad in kde. its better to just stick with konqueror IMO.

---

### Post by OBnascar on 2005-09-19
[COLOR=Blue]drizek wrote:

Firefox in linux overall is a mess, and its especially bad in kde.[/COLOR]

Ok, one less thing to try to fix...............lol

---

### Post by drizek on 2005-09-19
is the klik site down? i cant access it here.

---

