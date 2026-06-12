---
title: "Adobe Flash player won't install?"
date: 2008-12-13
forum: General Help
---

### Post by tylerlekang on 2008-12-13
I just installed ubuntu 8.0.4. I then installed firefox 3.0.4.


I went to youtube and it said I needed flash player, so I clicked the link and downloaded the .deb file. I opened that file and ubuntu installed the package.


But then I go back to youtube and it's as if I did nothing, what the heck?!



Please help!

Thanks

---

### Post by taurus on 2008-12-13
Did you remember to close down firefox and then restart it again?

---

### Post by tylerlekang on 2008-12-13
I actually just restarted the computer and it's still as if I did nothing.

I typed "about:plugins" into the URL bar and the plugin doesn't even show up!

---

### Post by taurus on 2008-12-13
Close down firefox.  Then, open a terminal and type

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```
Now, see if it shows up in firefox.

---

### Post by tylerlekang on 2008-12-13
I just tried that and here is the output:

```


tylerlekang@tylerlekang:~$ sudo apt-get update
[sudo] password for tylerlekang: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit http://mirrors.us.kernel.org hardy Release.gpg           
Ign http://mirrors.us.kernel.org hardy/main Translation-en_US
Ign http://mirrors.us.kernel.org hardy/restricted Translation-en_US
Ign http://mirrors.us.kernel.org hardy/universe Translation-en_US
Ign http://mirrors.us.kernel.org hardy/multiverse Translation-en_US
Hit http://mirrors.us.kernel.org hardy-backports Release.gpg
Ign http://mirrors.us.kernel.org hardy-backports/main Translation-en_US
Ign http://mirrors.us.kernel.org hardy-backports/restricted Translation-en_US
Ign http://mirrors.us.kernel.org hardy-backports/universe Translation-en_US
Ign http://mirrors.us.kernel.org hardy-backports/multiverse Translation-en_US
Hit http://mirrors.us.kernel.org hardy Release
Hit http://mirrors.us.kernel.org hardy-backports Release
Hit http://mirrors.us.kernel.org hardy/main Packages
Hit http://mirrors.us.kernel.org hardy/restricted Packages
Hit http://mirrors.us.kernel.org hardy/main Sources
Hit http://mirrors.us.kernel.org hardy/restricted Sources
Hit http://mirrors.us.kernel.org hardy/universe Packages
Hit http://mirrors.us.kernel.org hardy/universe Sources
Hit http://mirrors.us.kernel.org hardy/multiverse Packages
Hit http://mirrors.us.kernel.org hardy/multiverse Sources
Hit http://mirrors.us.kernel.org hardy-backports/main Packages
Hit http://mirrors.us.kernel.org hardy-backports/restricted Packages
Hit http://mirrors.us.kernel.org hardy-backports/universe Packages
Hit http://mirrors.us.kernel.org hardy-backports/multiverse Packages
Reading package lists... Done
tylerlekang@tylerlekang:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flashplugin
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 1 to remove and 13 not upgraded.
Need to get 0B/18.8kB of archives.
After this operation, 9933kB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 95923 files and directories currently installed.)
Removing adobe-flashplugin ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 95910 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--16:29:07--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.6.10.70
Connecting to fpdownload.macromedia.com|96.6.10.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:29:07 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


```



Any idea what's going on there?

---

### Post by taurus on 2008-12-13
Are you trying to compile a custome kernel or something?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by tylerlekang on 2008-12-13
Here it is:

```


tylerlekang@tylerlekang:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb http://mirrors.us.kernel.org/ubuntu/ hardy main restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirrors.us.kernel.org/ubuntu/ hardy universe
deb-src http://mirrors.us.kernel.org/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.us.kernel.org/ubuntu/ hardy multiverse
deb-src http://mirrors.us.kernel.org/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.us.kernel.org/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner


```


I'm only trying to get flash player so I can watch youtube videos.


Fairly new to ubuntu.

---

### Post by generic_idea_machine on 2008-12-13
are you using the 64 bit version of Ubuntu?

There are some known issues with the flash player for the 64 bit version.

---

### Post by tylerlekang on 2008-12-14
I don't think it is the 64bit version?

---

### Post by zvacet on 2008-12-14
```
gksudo gedit /etc/apt/sources.list
``` 

and remove # sign from ubuntu partner repo so the line will look 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

Go in synaptic and in search box type adobe-flashplugin and when you find the package just install it.This way worked for me.

To find out whitch version do you use type

```
uname -a
```

and you can post output here.

---

### Post by xarte on 2008-12-15
Thanks for this. I had the same problem. After reading your solution I remembered seeing those addresses in Software Sources,so  before I tried the command line, I checked 'Software Sources' in System/Admin and found that in the third party list, 

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

was listed but not checked. I checked the box, and reloaded. Then went to synaptics manager, searched for 'flash' and found the Adobe Flash plugin. Marked for installation, installed, started firefox and it's there.

I'd be feeling more pleased with myself if I HAD gone the CLI route but it worked, anyway. Thanks heaps!

---

### Post by Kilmarac on 2008-12-15
Im running into a similar problem, but it looks like its because its trying to download an old version thats not posted anymore.  I did all the steps above.

```

Downloading...
--16:42:39--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.17.194.70
Connecting to fpdownload.macromedia.com|96.17.194.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:42:40 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

kilmarac@Ryoko:~$ 
kilmarac@Ryoko:~$ uname -a
Linux Ryoko 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux
kilmarac@Ryoko:~$ 

```

---

### Post by zvacet on 2008-12-15
@** xarte**

I posted how to add repo from terminal.After that all you have to do is 

```
sudo apt-get install adobe-flashplugin
```   ):P


@ **Kilmarac**

From your output it is look like you tried to install flashplugin-nonfree from multiverse repo.I don´t know if this work with 64 bit but try add partner repo and then install** adobe-flashplugin**.

---

### Post by tylerlekang on 2008-12-15
Nope. Didn't work AGAIN. Unfrickin believable! It's as if Firefox is just ignoring me! 

Here is what I did:

```

tylerlekang@tylerlekang:~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 96093 files and directories currently installed.)
Removing flashplugin-nonfree ...
tylerlekang@tylerlekang:~$ 
tylerlekang@tylerlekang:~$ 
tylerlekang@tylerlekang:~$ gksudo gedit /etc/apt/sources.list
tylerlekang@tylerlekang:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Get:1 http://archive.canonical.com hardy Release.gpg [189B]                    
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Get:2 http://archive.canonical.com hardy Release [6998B]
Get:3 http://archive.canonical.com hardy/partner Packages [3763B]
Hit http://mirrors.us.kernel.org hardy Release.gpg   
Ign http://mirrors.us.kernel.org hardy/main Translation-en_US
Ign http://mirrors.us.kernel.org hardy/restricted Translation-en_US
Ign http://mirrors.us.kernel.org hardy/universe Translation-en_US
Ign http://mirrors.us.kernel.org hardy/multiverse Translation-en_US
Hit http://mirrors.us.kernel.org hardy-backports Release.gpg
Ign http://mirrors.us.kernel.org hardy-backports/main Translation-en_US
Ign http://mirrors.us.kernel.org hardy-backports/restricted Translation-en_US
Ign http://mirrors.us.kernel.org hardy-backports/universe Translation-en_US
Ign http://mirrors.us.kernel.org hardy-backports/multiverse Translation-en_US
Hit http://mirrors.us.kernel.org hardy Release
Hit http://mirrors.us.kernel.org hardy-backports Release
Hit http://mirrors.us.kernel.org hardy/main Packages
Hit http://mirrors.us.kernel.org hardy/restricted Packages
Hit http://mirrors.us.kernel.org hardy/main Sources
Hit http://mirrors.us.kernel.org hardy/restricted Sources
Hit http://mirrors.us.kernel.org hardy/universe Packages
Hit http://mirrors.us.kernel.org hardy/universe Sources
Hit http://mirrors.us.kernel.org hardy/multiverse Packages
Hit http://mirrors.us.kernel.org hardy/multiverse Sources
Hit http://mirrors.us.kernel.org hardy-backports/main Packages                 
Hit http://mirrors.us.kernel.org hardy-backports/restricted Packages           
Hit http://mirrors.us.kernel.org hardy-backports/universe Packages             
Hit http://mirrors.us.kernel.org hardy-backports/multiverse Packages           
Fetched 10.9kB in 6s (1639B/s)                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpurple0 pidgin pidgin-data
The following packages will be upgraded:
  apturl brasero gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0
  libtheora0 transmission-common transmission-gtk
10 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 17.8MB of archives.
After this operation, 4825kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://mirrors.us.kernel.org hardy-backports/main apturl 0.2.6ubuntu1~hardy1 [14.4kB]
Get:2 http://mirrors.us.kernel.org hardy-backports/main brasero 0.8.1-0ubuntu2~hardy1 [2185kB]
Get:3 http://mirrors.us.kernel.org hardy-backports/main gimp-python 2.4.6-1ubuntu1~hardy1 [195kB]
Get:4 http://mirrors.us.kernel.org hardy-backports/main gimp-gnomevfs 2.4.6-1ubuntu1~hardy1 [8412B]
Get:5 http://mirrors.us.kernel.org hardy-backports/main gimp 2.4.6-1ubuntu1~hardy1 [3930kB]
Get:6 http://mirrors.us.kernel.org hardy-backports/main libgimp2.0 2.4.6-1ubuntu1~hardy1 [981kB]
Get:7 http://mirrors.us.kernel.org hardy-backports/main gimp-data 2.4.6-1ubuntu1~hardy1 [9735kB]
Get:8 http://mirrors.us.kernel.org hardy-backports/main libtheora0 1.0~beta3-1~hardy1 [262kB]
Get:9 http://mirrors.us.kernel.org hardy-backports/main transmission-gtk 1.22-1ubuntu1~hardy1 [428kB]
Get:10 http://mirrors.us.kernel.org hardy-backports/main transmission-common 1.22-1ubuntu1~hardy1 [15.7kB]
Fetched 17.8MB in 4min19s (68.4kB/s)                                           
(Reading database ... 96078 files and directories currently installed.)
Preparing to replace apturl 0.2.2ubuntu1 (using .../apturl_0.2.6ubuntu1~hardy1_all.deb) ...
Unpacking replacement apturl ...
Preparing to replace brasero 0.7.1-3ubuntu1 (using .../brasero_0.8.1-0ubuntu2~hardy1_i386.deb) ...
Unpacking replacement brasero ...
Preparing to replace gimp-python 2.4.5-1ubuntu2 (using .../gimp-python_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp-python ...
Preparing to replace gimp-gnomevfs 2.4.5-1ubuntu2 (using .../gimp-gnomevfs_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp-gnomevfs ...
Preparing to replace gimp 2.4.5-1ubuntu2 (using .../gimp_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement gimp ...
Preparing to replace libgimp2.0 2.4.5-1ubuntu2 (using .../libgimp2.0_2.4.6-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement libgimp2.0 ...
Preparing to replace gimp-data 2.4.5-1ubuntu2 (using .../gimp-data_2.4.6-1ubuntu1~hardy1_all.deb) ...
Unpacking replacement gimp-data ...
Preparing to replace libtheora0 1.0~beta2-2 (using .../libtheora0_1.0~beta3-1~hardy1_i386.deb) ...
Unpacking replacement libtheora0 ...
Preparing to replace transmission-gtk 1.06-0ubuntu6 (using .../transmission-gtk_1.22-1ubuntu1~hardy1_i386.deb) ...
Unpacking replacement transmission-gtk ...
Preparing to replace transmission-common 1.06-0ubuntu6 (using .../transmission-common_1.22-1ubuntu1~hardy1_all.deb) ...
Unpacking replacement transmission-common ...
Setting up apturl (0.2.6ubuntu1~hardy1) ...

Setting up brasero (0.8.1-0ubuntu2~hardy1) ...

Setting up gimp-data (2.4.6-1ubuntu1~hardy1) ...

Setting up libgimp2.0 (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp-python (2.4.6-1ubuntu1~hardy1) ...

Setting up gimp-gnomevfs (2.4.6-1ubuntu1~hardy1) ...
Setting up libtheora0 (1.0~beta3-1~hardy1) ...

Setting up transmission-common (1.22-1ubuntu1~hardy1) ...
Setting up transmission-gtk (1.22-1ubuntu1~hardy1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
tylerlekang@tylerlekang:~$ 
tylerlekang@tylerlekang:~$ 
tylerlekang@tylerlekang:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  adobe-flashplugin
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 3927kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Get:1 http://archive.canonical.com hardy/partner adobe-flashplugin 10.0.12.36-1hardy2 [3927kB]
Fetched 3927kB in 44s (88.7kB/s)                                               
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 96539 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_10.0.12.36-1hardy2_i386.deb) ...
Setting up adobe-flashplugin (10.0.12.36-1hardy2) ...

tylerlekang@tylerlekang:~$ 
tylerlekang@tylerlekang:~$ 
tylerlekang@tylerlekang:~$ uname -a
Linux tylerlekang 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
tylerlekang@tylerlekang:~$


```


Maybe it's a sign that I'm not supposed to watch Youtube videos?

:*(

---

### Post by spcwingo on 2008-12-15
Download the tar.gz version from here:

[http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz]("http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz")

and extract it.  Then extract the file named: install_flash_player_9_linux.tar.gz.  Then open a terminal and cd to the extracted directory. Then type sudo ./flashplayer-installer.  It'll tell you to close all open browsers.  Then ask where the installation directory is. It's /usr/lib/firefox-3.0.4 (or whatever version you're running).  Then open up Firefox and make sure it recognizes it.  Let me know how it turns out for you.  BTW, if you're wondering why flash 9 and not 10...it's because 9 is the version that used to be available through the repos.

---

### Post by hamlet_42 on 2008-12-15
hello, 
> Maybe it's a sign that I'm not supposed to watch Youtube videos?
it took me more than 20 hours to find out how it works for hardy: 
just like spcwingo said. 

but for me on 8.04 one or all of the following was necessary:
< add multi- and universe in synaptic
< add the hardy updates in synaptic
< run all updates
< remove completely the repo-version of flashplugin.

good luck 
hamlet.

---

### Post by xarte on 2008-12-16
> **zvacet said:**
> @** xarte**

I posted how to add repo from terminal.After that all you have to do is 

```
sudo apt-get install adobe-flashplugin
```   ):P



Thanks Z, yeah I'd written that down and was all ready to try it out when I decided to see what software sources might do. 

I'd like to make a point that experienced Linux users are very helpful with CLI stuff - and for me personally that's great as that's something I want to get familiar with - but nowadays many linux users want to use it 'just like windows' and maybe it's worth looking to see what the desktop has to offer first, you know? They are more familiar, less threatening.

---

### Post by hamlet_42 on 2008-12-16
hello; 

1)you just need to open a gnome-terminal
(ALT + Space <gnome-terminal>for gnome  ALT+F3,<konsole> for kde)
and type it down.


2)Synaptic

3)if you download the flash from adobe for Ubuntu8_0.4 
you just need to do the usual window clicking: 
download 
go wherever it is
install it by clicking
done

greetings 
hamlet

PS:
i  never got used to the windows-thing, cause i started a year ago 
with linux, after a three-month tortour with microslot.
For me its more easy to type a command than to say: 
for kde:...; for:gnome;...; for xfce:...,for flushbox:...; for icewm:...
for:all_the_rest_of_them; if_then_, rightcklick_here and leftclick_there. 
And you often get helpful error messages and help by just adding -h, --help or by man <command> within CLI:
apt-get -h
apt-get --help
man apt-get

---

### Post by zvacet on 2008-12-16
> I'd like to make a point that experienced Linux users are very helpful with CLI stuff - and for me personally that's great as that's something I want to get familiar with

Only way to get familiar with CLI is to use it.That will give you a choice to do things in both ways (CLI or graphic).You will have two tools not just one to work with on your comp.Here is something you maybe want to read 

[http://linuxcommand.org/]("http://linuxcommand.org/")
[http://www.linuxcmd.org/]("http://www.linuxcmd.org/")
[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")

---

### Post by tylerlekang on 2008-12-17
> **spcwingo said:**
> Download the tar.gz version from here:

[http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz]("http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz")

and extract it.  Then extract the file named: install_flash_player_9_linux.tar.gz.  Then open a terminal and cd to the extracted directory. Then type sudo ./flashplayer-installer.  It'll tell you to close all open browsers.  Then ask where the installation directory is. It's /usr/lib/firefox-3.0.4 (or whatever version you're running).  Then open up Firefox and make sure it recognizes it.  Let me know how it turns out for you.  BTW, if you're wondering why flash 9 and not 10...it's because 9 is the version that used to be available through the repos.


Sweet, that worked. (except your link did not contain install_flash_player_9_linux.tar.gz, luckily I found a link to it in another thread)



Why wouldn't sudo apt-get flashplugin-nonfree work?

---

### Post by |{urse on 2008-12-17
to fix this.

go to the tar.gz you downloaded right click and copy libflashplayer.so

paste it here

/usr/lib/firefox/plugins/libflashplayer.so

):P

By the way this simple process is made uber-annoying with install scripts, It's just a plugin for fork's sake.

---

### Post by tylerlekang on 2008-12-21
Ok so it worked fine when I ran the install_flash_player_9_linux installer but now every time I restart my computer it won't work.

Any place there's a flash app on a web page it just shows a big blank white space.


It will work if I rerun the installer EVERY TIME I RESTART THE COMPUTER. Why won't it stick.



Better yet, why the heck is it so dang difficult? Why won't it just work?


I actually think it's trying to screw me in any way it can.

---

### Post by wolfen69 on 2008-12-21
completely remove any flash you have. then
```
sudo apt-get clean
``` then
```
sudo apt-get autoremove
```then go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu. click to install. restart firefox if open.

---

### Post by tylerlekang on 2008-12-21
No I will waste another 20 hours of my life trying to get flash player 10 to work when it clearly does not work for Ubuntu, just look around the internet and you'll see hundreds of other who have the same problem.


I think I will try a fresh reformat/install of Ubuntu and then install firefox 3.0.4 and then install flash player 9 and see if that will work.


If that doesn't work then I'm probably going to be done with Ubuntu. I tried it and it was cool but I am not going to waste any more of my life trying to get simply little crap to work that is supposed to just work the first time.

---

### Post by tylerlekang on 2008-12-24
Update: I did reinstall ubuntu 8.0.4, just left the version of Firefox that came with it (3.0) and installed flashplayer 9 and it seems like it works now, even after restarting.

So I don't have much need to update to any newer versions of Firefox or flash player.


But I did try installing flash player 10 using the same method as installing flash player 9 (download tar file, extract, and run sudo ./flashplayer-installer). It does the exact same thing for both versions (installs to /usr/lib/firefox-3.0). Except nothing happens with 10 whereas with 9 it works. 


Weird but I'm done wasting my life trying to figure it out, I will live with what I have.

---

### Post by darkbluedove on 2008-12-24
I'm running Hardy x64, and the "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner" does not work for me:

sudo apt-get install adobe-flashplugin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin

Maybe it has to do with x64 and not finding an i386 binary package; I'm not sure.  (Yes, I ran apt-get update.)  But anyway, the following works for me with the original flashplugin-nonfree package.  I wanted to keep Flash under APT control (hence not tar/install script solutions), and I'm okay with Flash 9 instead of 10.

My solution to get flashplugin-nonfree working:

It looks like the bug is with the hardy-backports package.  After confirming that "apt-get -t hardy-updates install flashplugin-nonfree" works, I looked up APT pinning so that "Update Manager" and "apt-get upgrade" would know not to recommend the higher version in hardy-backports.  (If the hardy-backports package is fixed someday, I can remove the pinning at that time.)  (For completeness, I should mention I ran "apt-get remove flashplugin-nonfree" before doing the following.)

1.) Create /etc/apt/preferences with this entry:

Explanation: Flash plugin from hardy-backports was broken on 12/24/2008;
Explanation: pinning to hardy-updates for now until it is fixed
Package: flashplugin-nonfree
Pin: release a=hardy-updates
Pin-Priority: 980

2.) sudo apt-get update

3.) sudo apt-get install flashplugin-nonfree

4.) Restart Firefox

I have not tested what happens if I reboot.  Hopefully, it will continue to work.

---

