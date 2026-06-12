---
title: "How do I install programs"
date: 2005-12-24
forum: General Help
---

### Post by gamer46290 on 2005-12-24
I don't know how to install programs, what is this package manager adept thing ???????? How do I install programs????????? Please HELP!!

---

### Post by ardchoille on 2005-12-24
The easiest way to install new apps is to open Synaptic and do it there.. or use "sudo apt-get install appname" if you know what the name of the app is.

---

### Post by Zio84 on 2005-12-24
You can find the graphical package manager in the Ubuntu memny under "add applications". Or simply by typing "sudo synaptic" in a terminal.

---

### Post by gamer46290 on 2005-12-24
Is that a command line or something, because when I put it there nothing works

---

### Post by chimera on 2005-12-24
If the program you need is in the ubuntu repositories, you can install it with synaptic (main menu->system->administration->synaptic package manager), if you have a .deb package you can install it with
sudo dpkg -i <filename>
if you have a .rpm package, you can install it with
alien -i <filename>              (please note you need alien installed for this, you can find it in synaptic)
if you have the source, you'll need to compile it yourself, I can't give you any details on this since I've never really had to it myself.

---

### Post by Jzor on 2005-12-24
... Nevermind

(Chimera beat me to it, and I can't figure out how to delete instead of just edit.)

---

### Post by Zio84 on 2005-12-24
The terminal is under Accessories in the meny.

---

### Post by gamer46290 on 2005-12-24
I tried the terminal code you told me and it asked me for a password.

---

### Post by Jzor on 2005-12-24
It wants the same password you use to login with.

---

### Post by ardchoille on 2005-12-24
[QUOTE=gamer46290]I tried the terminal code you told me and it asked me for a password.[/QUOTE]
Yes, that is asking for your user password.. it's for root user privileges.

---

### Post by sonicj on 2005-12-24
CAn you install windows programs on linux? like starcraft or wordpad etc?"\

---

### Post by The Warlock on 2005-12-24
[QUOTE=gamer46290]I tried the terminal code you told me and it asked me for a password.[/QUOTE]

Pretty much whenever something asks for a password in Ubuntu, it is asking for your logon password. This is a security measure.

Back to the original question: The easiest way to install software in Ubuntu is through Synaptic, which can be found in the System menu, under Administration. Look through the list or do a search, check the box next to the programs you want to install, and click the apply button. The programs will be downloaded, installed, and from then on Ubuntu will check them for updates automatically.

Pretty nice, huh?

---

### Post by gamer46290 on 2005-12-24
wouldn't let me type

---

### Post by The Warlock on 2005-12-24
[QUOTE=gamer46290]wouldn't let me type[/QUOTE]
Just type the password and hit enter. The terminal doesn't show the password as you type it, and doesn't show the usual line of asterixes, either.

---

### Post by gamer46290 on 2005-12-24
I typed it in and hit enter and it said command not found, and I can't find synaptic anywhere, did I get a faulty installation disk or something, the only thing I have on here is called Adept

---

### Post by chimera on 2005-12-24
[QUOTE=sonicj]CAn you install windows programs on linux? like starcraft or wordpad etc?"\[/QUOTE]


For office applications, you'll need crossover office/wine
For games, you'll need cedega (wine will work to in some cases)

---

### Post by Zio84 on 2005-12-24
[QUOTE=sonicj]CAn you install windows programs on linux? like starcraft or wordpad etc?"\[/QUOTE]

Yes you can, there's a thing called Wine that will let you runt windows apps. There is also two commercial variants of wine called Cedega (for running games) and Crossover Office (for running office apps)

---

### Post by The Warlock on 2005-12-24
[QUOTE=sonicj]CAn you install windows programs on linux? like starcraft or wordpad etc?"\[/QUOTE]

First of all, what do you need wordpad for? Click on the Applications menu. Click on Office. There, you've got a whole office suite that's (almost) as good as MS office, and free, and already installed on your computer.

As for starcraft and other games. Windows programs do not work natively under Linux the same way they don't work under MacOS X; it's a different operating system than Windows. Some games (but very few) have Linux versions. UT2004 and Quake 3 Arena are good examples. For games that do not have Linux versions, there is a program called wine that acts as a sort of emulator or compatability layer to try and get Windows programs working under Linux. I think it can run Starcraft without problems, but more advanced games will have issues. It's a little tricky to get working. Try starting a thread in the Ubuntu Gaming forum here.

---

### Post by The Warlock on 2005-12-24
[QUOTE=gamer46290]I typed it in and hit enter and it said command not found, and I can't find synaptic anywhere, did I get a faulty installation disk or something, the only thing I have on here is called Adept[/QUOTE]

Are you using Kubuntu? If so, you're on the wrong section of the forum. But try Adept, it's similar to Synaptic, just made for KDE (the desktop environment for Kubuntu) rather than Gnome (the desktop environment for regular Ubuntu).

---

### Post by sciurus on 2005-12-24
If you have Adept, I assume you're using Kubuntu, not Ubuntu. A package management system, as wikipedia says, is "a collection of tools to automate the process of installing, upgrading, configuring, and removing software packages from a computer." There are three layers of package management you can deal wiht in Ubuntu. The first is dpkg, which is the underlying set of tools for adding and removing packages. The second is apt, which makes it easy to install software from online repositories. The third is software such as Synaptic and and Adept, which provide a graphical interface for the functionality of apt.

For lists of popular software in Ubuntu's repositories, try the following threads
[http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)
[http://ubuntuforums.org/showthread.php?t=35208](http://ubuntuforums.org/showthread.php?t=35208)

Before some of that software shows up, you may have to edit your sources. See [https://wiki.ubuntu.com/SourcesList](https://wiki.ubuntu.com/SourcesList)

---

### Post by gamer46290 on 2005-12-24
No one at the kubuntu forum will help me, yes I have kubuntu, it says I can't upgrade or install unless I run as root, How do i do that??????

---

### Post by The Warlock on 2005-12-24
[QUOTE=gamer46290]No one at the kubuntu forum will help me, yes I have kubuntu, it says I can't upgrade or install unless I run as root, How do i do that??????[/QUOTE]
You are asking on the wrong forum. Few of us have experience with kubuntu. Start a new thread here: [http://www.ubuntuforums.org/forumdisplay.php?f=99](http://www.ubuntuforums.org/forumdisplay.php?f=99)

---

### Post by gamer46290 on 2005-12-24
:-( I deleted windows and I don't have a back up cd, I would get ubuntu itself but I don't know what good program would burn the ISO image for linux, and heck I can't even install anything. No on in kubuntu helps me, I really need help!!!

---

### Post by sciurus on 2005-12-24
Wine should work well for lots of games, arguably better than Cedega. They maintain a [repository]("http://www.winehq.com/site/download-deb") with the latest version that should work in Ubuntu, although I haven't tried it. There are also many [native games]("http://doc.gwos.org/index.php/Native_Games") for linux. Before you can play 3d games, you'll need to install the binary drivers for your graphics card ([nvidia]("http://ubuntuforums.org/showthread.php?t=75074") | [ati]("http://ubuntuforums.org/showthread.php?t=75378")).

---

### Post by sciurus on 2005-12-24
[QUOTE=gamer46290]it says I can't upgrade or install unless I run as root, How do i do that??????[/QUOTE]

You mean when you start Adept, it asks for the root password? Type in your password. (K)Ubuntu uses sudo, which allows a user* to run a command as root.

K3B is a good program for burning cd's, by the way. However, if you want to switch from Kubuntu to Ubuntu, you don't have to reinstall. Just use your package manager to install ubuntu-desktop; you'll then have all Ubuntu and Kubuntu programs installed and be able to choose whether to use the KDE or GNOME desktop at each login.

* in the admin group

---

### Post by The Warlock on 2005-12-24
[QUOTE=gamer46290]:-( I deleted windows and I don't have a back up cd, I would get ubuntu itself but I don't know what good program would burn the ISO image for linux, and heck I can't even install anything. No on in kubuntu helps me, I really need help!!![/QUOTE]
If you want ubuntu itself, open up a terminal window and type in
```
sudo apt-get install ubuntu-desktop
```
and enter your password when it asks, and that's it. Just wait for it to finish, log out, and log back in, making sure to pick GNOME from the session menu. 

You'll have both at once then, and can switch between either when you find out which you like best.

KDE (and with it, Kubuntu) are more designed for advanced users (although I like Gnome better for other reasons).

---

### Post by gamer46290 on 2005-12-24
When I type in my password it lets me looks at the list of programs and when I try to install one nothing at all happens.

---

### Post by gamer46290 on 2005-12-24
Oh I think I figured it out!! :-) So what about programs like limwire how do I install those???

---

### Post by sciurus on 2005-12-24
[QUOTE=gamer46290]Oh I think I figured it out!! :-) So what about programs like limwire how do I install those???[/QUOTE]

See the links I posted previously. Also, [http://kudos.berlios.de/kf/kf1.html](http://kudos.berlios.de/kf/kf1.html) may be helpful. To access the Guntella network like Limewire does, in Kubuntu I would use appollon. In Ubuntu I would use gtk-gnutella.

---

### Post by The Warlock on 2005-12-24
[QUOTE=sciurus]See the links I posted previously. Also, [http://kudos.berlios.de/kf/kf1.html](http://kudos.berlios.de/kf/kf1.html) may be helpful. To access the Guntella network like Limewire does, in Kubuntu I would use appollon. In Ubuntu I would use gtk-gnutella.[/QUOTE]
What he said. There is a Linux version of the actual Limewire program, but it's not particularly good (nor is it in the repositories, because it's not Free Software, so it's a pain in the ass to install)

---

### Post by gamer46290 on 2005-12-24
Why can't kubuntu use limewire?? On the website, I bought pro, and there is a linux, macintosh, and windows version, So once I download it how would I install?

---

### Post by The Warlock on 2005-12-25
[QUOTE=gamer46290]Why can't kubuntu use limewire?? On the website, I bought pro, and there is a linux, macintosh, and windows version, So once I download it how would I install?[/QUOTE]

Ack! You bought pro? Pro is bad. Don't buy pro. Hell, don't buy software, that's why we're here. I'm sorry to say this, but you got ripped off by Limewire.

Anyway, it might not be impossible to use it, but it will be a pain. It downloads an .rpm file, right? This is a software package for a Red Hat based Linux distribution. Ubuntu is a Debian-based Linux distribution, and therefore uses .deb packages. You can convert an RPM package to DEB with the alien command. Type in (using the real file name and not my example, of course!):

```
sudo alien TheFileNameGoesHere.rpm
```
(don't forget, Linux is case-sensitive!)

and it will create a .deb file and tell you what the name of it is. Then you install the .deb file (again, use the real filename and not my example filename).

```
sudo dpkg -i the-new-file-name-goes_here.deb
```

---

### Post by Curlydave on 2005-12-29
I'm trying the alien thing, but it says that the command is not found.

> david@computer1:~$ sudo alien /home/david/untitled folder/LimeWireLinux.rpm
sudo: alien: command not found


---

### Post by Lord Illidan on 2005-12-29
That's because you haven't installed it.

```
sudo apt-get install alien
```

---

### Post by iand675@gmail.com on 2006-01-01
there's also frostwire :)
same thing as limewire- only open source and free

---

### Post by briancurtin on 2006-01-01
i havent used limewire in forever (back on windows), but does frostwire access the same material that limewire useres see on their network? or is this just a limewire-type thing within linux users?

---

### Post by ykpaiha on 2006-01-01
[QUOTE=briancurtin]i havent used limewire in forever (back on windows), but does frostwire access the same material that limewire useres see on their network? or is this just a limewire-type thing within linux users?[/QUOTE]

This is not the right way to beguin a new year mate!!!
good resolutions may take place these days!!!

limewire or so called pro only use a protole in the web : gnutella
you can use, gtk, or frostwire, appolon or else will all do the same, in a different shape that's it.

happy discovery in a new world....

---

