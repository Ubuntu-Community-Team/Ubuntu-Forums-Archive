---
title: "Thunar slow as molasses"
date: 2013-09-23
forum: Desktop Environments
---

### Post by Buntu Bunny on 2013-09-23
Within, I'd say, the past week, Thunar has gotten extremely slow at opening everything. So slow, in fact, that I become alarmed that something is broken. One time, I got the following

> Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I'm not sure what to do with that. By network connection I'm assuming home network (which consists of one modem and one desktop, so why would that slow opening files on that one computer??? We did change ISPs a week ago, but again, would that effect work I'm doing offline on my own computer?)

Earlier this summer someone [reported a similar problem with Nautilus]("http://ubuntuforums.org/showthread.php?t=2156298"), but there were no answers for it.

Any ideas?

---

### Post by Kirboosy on 2013-09-23
Have you tried reseting Thunar? Also maybe clearing out your thumnails will help.

```
mv ~/.config/Thunar ~/.config/Thunar.bak
rm -rf ~/.thumbnails/
```
 If that doesn't change anything you can always revert your old configs with.

```
 mv ~/.config/Thunar.bak ~/.config/Thunar
```

Hope that helps!
~Caboose

---

### Post by Buntu Bunny on 2013-09-23
> **Caboose885 said:**
> Have you tried reseting Thunar? Also maybe clearing out your thumnails will help.

```
mv ~/.config/Thunar ~/.config/Thunar.bak
rm -rf ~/.thumbnails/
```
 If that doesn't change anything you can always revert your old configs with.

Caboose, wow. I started with the first code you suggested to reset Thunar and that alone made a huge difference. Thanks!

---

### Post by Kirboosy on 2013-09-23
You may want to run the following command to remove your old backup (just so you don't have useless clutter on the hard drive)

```
rm -rf ~/.config/Thunar.bak
```

Anyways, glad I could help \\:D/

~Caboose

---

### Post by Buntu Bunny on 2013-09-23
> **Caboose885 said:**
> You may want to run the following command to remove your old backup (just so you don't have useless clutter on the hard drive)

```
rm -rf ~/.config/Thunar.bak
```

Anyways, glad I could help 

Will do. And yes, you've been a great help. Much appreciated! :D

---

### Post by vasa1 on 2013-09-23
> **Buntu Bunny said:**
> Caboose, wow. I started with the first code you suggested to reset Thunar and that alone made a huge difference. Thanks!
Just curious, but what did you have in ~/.config/Thunar?

I see two files: accels.scm and uca.xml. From the looks of it, the latter is meant for Thunar's custom actions and the former is automatically generated. Any thoughts on which was the culprit?

---

### Post by Buntu Bunny on 2013-09-24
Rats. The first file I opened this morning was, once again, very slow to respond. In fact I got another of these...

> Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


*sigh*

> **vasa1 said:**
> Just curious, but what did you have in ~/.config/Thunar? 

I see two files: accels.scm and uca.xml. From the looks of it, the latter is meant for Thunar's custom actions and the former is automatically generated. Any thoughts on which was the culprit?

Vasa1, the only file there is thunarrc.txt

Do I need to repeat Caboose's suggestion?

---

### Post by vasa1 on 2013-09-24
> **Buntu Bunny said:**
> Rats. The first file I opened this morning was, once again, very slow to respond. ...
Vasa1, the only file there is thunarrc.txt

Do I need to repeat Caboose's suggestion?

Oops, sorry to hear that. What is your version of Thunar? Mine is Thunar 1.6.2. My desktop is not conventional Xubuntu or Xfce but a mix of Lubuntu and Xfce **but** the contents of [FONT=Courier New]~/.config/Thunar[/FONT] should be similar, IMO. I wonder why they aren't.

[FONT=Courier New]thunarrc.txt[/FONT] doesn't sound like a "legit" file and by "legit" I mean something that comes with Thunar or is created by the system. Such files are usually [FONT=Courier New]something.rc[/FONT] or [FONT=Courier New]somethingrc[/FONT] but not [FONT=Courier New]somethingrc.txt[/FONT]. For example, I have [FONT=Courier New]~/.themes/MyGreybird/gtk-2.0/apps/thunar.rc[/FONT].

I'm not good at this but I think Thunar is looking for something it feels it has to contact or automount. Sometime ago, there were a lot of posts about why Thunar took a while to open on its first launch but I thought that problem no longer exists.

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)
[http://askubuntu.com/questions/106262/slow-folder-opening-due-to-folder-scan-in-xfce](http://askubuntu.com/questions/106262/slow-folder-opening-due-to-folder-scan-in-xfce)

---

### Post by Buntu Bunny on 2013-09-24
> **vasa1 said:**
> Oops, sorry to hear that. What is your version of Thunar? Mine is Thunar 1.6.2. My desktop is not conventional Xubuntu or Xfce but a mix of Lubuntu and Xfce **but** the contents of [FONT=Courier New]~/.config/Thunar[/FONT] should be similar, IMO. I wonder why they aren't.

Wow, mine's version 1.2.3. Seems like I'm rather out of date! I installed Xfce after I installed Ubuntu 12.04 and discovered I didn't care for Unity. Sounds like some upgrading is definitely in order. 

> [FONT=Courier New]thunarrc.txt[/FONT] doesn't sound like a "legit" file and by "legit" I mean something that comes with Thunar or is created by the system. Such files are usually [FONT=Courier New]something.rc[/FONT] or [FONT=Courier New]somethingrc[/FONT] but not [FONT=Courier New]somethingrc.txt[/FONT]. For example, I have [FONT=Courier New]~/.themes/MyGreybird/gtk-2.0/apps/thunar.rc[/FONT].

I'm not good at this but I think Thunar is looking for something it feels it has to contact or automount. Sometime ago, there were a lot of posts about why Thunar took a while to open on its first launch but I thought that problem no longer exists.

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)
[http://askubuntu.com/questions/106262/slow-folder-opening-due-to-folder-scan-in-xfce](http://askubuntu.com/questions/106262/slow-folder-opening-due-to-folder-scan-in-xfce)

I'm definitely no expert, but your explanation sounds very logical. And you've given me a starting point for more research. Thank you vasa1!

---

### Post by Kirboosy on 2013-09-24
I forgot to have you clear the cache of Thunar as well. Sorry, my bad!

```
rm -rf ~/.cache/sessions
```

Hope that fixes it once and for all!
~Caboose

---

### Post by Buntu Bunny on 2013-09-24
> **Caboose885 said:**
> I forgot to have you clear the cache of Thunar as well. Sorry, my bad!

```
rm -rf ~/.cache/sessions
```

Hope that fixes it once and for all!

Caboose, no problem. It's funny because yesterday, after resetting Thunar, it was back up to speed. The problem didn't reoccur until this morning when I booted my computer. Thunar was slow again. I'll let you know if clearing the cache helps!

---

### Post by slickymaster on 2013-09-24
> **vasa1 said:**
> Oops, sorry to hear that. What is your version of Thunar? Mine is Thunar 1.6.2. My desktop is not conventional Xubuntu or Xfce but a mix of Lubuntu and Xfce **but** the contents of [FONT=Courier New]~/.config/Thunar[/FONT] should be similar, IMO. I wonder why they aren't.

[FONT=Courier New]thunarrc.txt[/FONT] doesn't sound like a "legit" file and by "legit" I mean something that comes with Thunar or is created by the system. Such files are usually [FONT=Courier New]something.rc[/FONT] or [FONT=Courier New]somethingrc[/FONT] but not [FONT=Courier New]somethingrc.txt[/FONT]. For example, I have [FONT=Courier New]~/.themes/MyGreybird/gtk-2.0/apps/thunar.rc[/FONT].

+1
I think vasa1 is right. I have a conventional Xubuntu install on this computer with Thunar 1.6.3 on it, and the contents of my **~/.config/Thunar/** folder is ```
~$ ls -la ~/.config/Thunar/
total 20
drwx------  2 slickymaster slickymaster 4096 Ago 20 09:31 .
drwx------ 24 slickymaster slickymaster 4096 Set 16 12:13 ..
-rw-r--r--  1 slickymaster slickymaster 4714 Set 24 11:41 accels.scm
-rw-------  1 slickymaster slickymaster  613 Ago 20 09:31 uca.xml

```just like him's.

> **vasa1 said:**
> I'm not good at this but I think Thunar is looking for something it feels it has to contact or automount. Sometime ago, there were a lot of posts about why Thunar took a while to open on its first launch but I thought that problem no longer exists.

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)
[http://askubuntu.com/questions/106262/slow-folder-opening-due-to-folder-scan-in-xfce](http://askubuntu.com/questions/106262/slow-folder-opening-due-to-folder-scan-in-xfce)

Another possibility to approach is to prevent Thunar from using thumbnails. See this bug reports: [https://bugzilla.xfce.org/buglist.cgi?quicksearch=tumblerd](https://bugzilla.xfce.org/buglist.cgi?quicksearch=tumblerd)

---

### Post by vasa1 on 2013-09-24
My "vote" is for a clean Xubuntu 13.10 install in a month's time.

BTW, tumbler has a very nice /etc/xdg/tumbler/tumbler.rc with lots of options. But then again, I don't know if it's on systems with older versions of Xfce.

---

### Post by Buntu Bunny on 2013-09-24
> **slickymaster said:**
> +1
I think vasa1 is right. I have a conventional Xubuntu install on this computer with Thunar 1.6.3 on it, and the contents of my **~/.config/Thunar/** folder is ```
~$ ls -la ~/.config/Thunar/
total 20
drwx------  2 slickymaster slickymaster 4096 Ago 20 09:31 .
drwx------ 24 slickymaster slickymaster 4096 Set 16 12:13 ..
-rw-r--r--  1 slickymaster slickymaster 4714 Set 24 11:41 accels.scm
-rw-------  1 slickymaster slickymaster  613 Ago 20 09:31 uca.xml

```just like him's.

Would mine be as it is because I didn't initially install Xubuntu? I installed Xfce once I discovered I don't like Unity. Would that make a difference in the config file?

> **slickymaster said:**
> Another possibility to approach is to prevent Thunar from using thumbnails. See this bug reports: [https://bugzilla.xfce.org/buglist.cgi?quicksearch=tumblerd](https://bugzilla.xfce.org/buglist.cgi?quicksearch=tumblerd)

slickymaster, I will definitely look into that. Thanks.

> **vasa1 said:**
> My "vote" is for a clean Xubuntu 13.10 install in a month's time.

Sounds good except that my husband is also a user on this computer and he likes his Gnome Classic. :) I'd ask if I could just update Thunar, but wouldn't it be better to update Xfce from 4.8 to 4.10?

> **vasa1 said:**
> BTW, tumbler has a very nice /etc/xdg/tumbler/tumbler.rc with lots of options. But then again, I don't know if it's on systems with older versions of Xfce.

I don't have /xdg/tumbler in my /etc, so you are correct about the older Xfce. Sounds like I definitely need to update.

---

### Post by Bashing-om on 2013-09-24
Mine for reference; xfce4:
> 
sysop@1304mini:~$ ls -la ~/.config/Thunar/
total 12
drwx------  2 sysop sysop 4096 May 20 00:46 .
drwxrwxr-x 16 sysop sysop 4096 Jul 13 14:00 ..
-rw-r--r--  1 sysop sysop  103 Sep 23 23:24 accels.scm

sysop@1304mini:~$ apt-cache policy thunar
thunar:
  Installed: 1.6.2-0ubuntu1
  Candidate: 1.6.2-0ubuntu1
  Version table:
 *** 1.6.2-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/universe amd64 Packages
        100 /var/lib/dpkg/status

sysop@1304mini:~$ apt-cache policy xfce4
xfce4:
  Installed: 4.10.0
  Candidate: 4.10.0
  Version table:
 *** 4.10.0 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/universe amd64 Packages
        100 /var/lib/dpkg/status
sysop@1304mini:~$ 

[INDENT][INDENT]any little bit can help
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-24
Buntu Bunny; Hi !

For consideration only ;
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435)
Please help testing Ricardo F. Teixeira's patched builds from this PPA:
[https://launchpad.net/~ricardo.teixas/+archive/xfce4-session](https://launchpad.net/~ricardo.teixas/+archive/xfce4-session)
...and provide feedback here:
[https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735](https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735)
Please be sure to test thoroughly.

The process to get the updated package would be:
sudo apt-add-repository ppa:ricardo.teixas/xfce4-session
sudo apt-get update
sudo apt-get install xfce4-session=4.10.0-2ubuntu2~raring1 ppa-purge

To remove this PPA:
sudo ppa-purge ppa:ricardo.teixas/xfce4-session

note for "~raring1" research to see how to get the updated/patched application for your particular version of 'buntu.


Not only do you get the latest xfce4 -that I had expected to be in the archive by this time- but also the updated thunar (and all other packages).

[INDENT][INDENT]hey, it's a thought !
[/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2013-09-24
> **Bashing-om said:**
> Mine for reference; xfce4:

[INDENT][INDENT]any little bit can help
[/INDENT][/INDENT]

Bashing-om, thanks. It's curious that everyone else has at least the accels.scm and I don't. :confused:

> **Bashing-om said:**
> 

For consideration only ;
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435)
Please help testing Ricardo F. Teixeira's patched builds from this PPA:
[https://launchpad.net/~ricardo.teixas/+archive/xfce4-session](https://launchpad.net/~ricardo.teixas/+archive/xfce4-session)
...and provide feedback here:
[https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735](https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735)
Please be sure to test thoroughly.

The process to get the updated package would be:
sudo apt-add-repository ppa:ricardo.teixas/xfce4-session
sudo apt-get update
sudo apt-get install xfce4-session=4.10.0-2ubuntu2~raring1 ppa-purge

To remove this PPA:
sudo ppa-purge ppa:ricardo.teixas/xfce4-session

note for "~raring1" research to see how to get the updated/patched application for your particular version of 'buntu.

Not only do you get the latest xfce4 -that I had expected to be in the archive by this time- but also the updated thunar (and all other packages).


Those details are very much appreciated, and I hear you about thorough research. Xfce 4.8 came with Xubuntu 12.04, but whether or not I can run Xfce 4.10 on 12.04 is what I need to look into. I confess I prefer to stick with the LTS versions for the time being. I'll have to see how well the current fixes last before making a final decision. :)

---

### Post by Bashing-om on 2013-09-24
Buntu Bunny; Hey !

Looks like I may have been running headless way out in left field on my last. From my 12.04 install:
> 
sysop1@1204-a:~$ apt-cache policy xfce4
xfce4:
  Installed: (none)
  Candidate: 4.8.0.3
  Version table:
     4.8.0.3 0
        500 [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) precise/universe amd64 Packages
sysop1@1204-a:~$ 

xfce4 version 4.10 + may be a stretch for ya ... hang on a bit and let me see what Lubuntu relates:

edit: Lubuntu 12.04 same same for what is available in the repository for xfce4 version.

-----------------
As we are looking at what appears to be a config file not being generated .. recon what would result from:
```

sudo apt-get install -f thunar

```
or maybe reconfigure "thunar" ?
```

sudo dpkg-reconfigure thunar

```

Let the package manager do it's job ?

---

### Post by vasa1 on 2013-09-24
> **Buntu Bunny said:**
> .... Xfce 4.8 came with Xubuntu 12.04, but whether or not I can run Xfce 4.10 on 12.04 is what I need to look into. ...
When I was on Ubuntu (not Lubuntu or Xubuntu) 12.04, I added xfce 4.10 which was that time available as a ppa. No problems at all.

---

### Post by Buntu Bunny on 2013-09-25
Things have gotten really strange. I booted my computer this morning and firstly noticed that the backgrounds for my desktop icons are now transparent. As I tried to make these out, I realised that my home folder is no longer displayed as an icon on my desktop [Edit: I now realise that none of my default icons are displaying on my desktop].

I opened Settings Manager to make sure Home was checked under Default Icons, it is. [Edit: all are checked] I also discovered that I cannot change my desktop wallpaper. 

The only thing I knew to try was 

```
xfwm4 --replace
```

but that did nothing. 

Thunar is no longer sluggish in opening files, but what happened???? Help?

*[COLOR="#FF0000"]A CLUE?[/COLOR]* I just right-clicked on my desktop and out of curiosity clicked "change desktop background". The box that popped up was not Xfce's Desktop Settings, but System Settings for Unity. :confused: Has Unity hijacked my desktop???

P.S.  @Bashing-om, here's what I got

```
sudo apt-get install -f thunar
[sudo] password for buntu bunny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunar is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono-sqlite4.0-cil libmono-system-web-services4.0-cil libunistring0:i386
  libwnck2.20-cil libmono-web4.0-cil linux-headers-3.2.0-51
  libmono-system-transactions4.0-cil python-mutagen libgomp1:i386 python-mpd
  libmono-system-data4.0-cil libmono-system-web-applicationservices4.0-cil
  libgnome-desktop-2-17 libmono-system-enterpriseservices4.0-cil
  libgnomedesktop2.20-cil libcroco3:i386 libnotify0.4-cil librsvg2-2.18-cil
  libmono-system-web4.0-cil libgettextpo0:i386 dockmanager e17-data
  linux-headers-3.2.0-51-generic libgnome-keyring1.0-cil
  libmono-system-xml-linq4.0-cil libmono-data-tds4.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Also tried 

```

sudo dpkg-reconfigure thunar

```

No output, no change.

@vasa1, thank you for the feedback for Xfce 4.10 on Ubuntu 12.04. Since I installed Xfce for Ubuntu 12.04, it may work for me too.

---

### Post by slickymaster on 2013-09-25
> **Buntu Bunny said:**
> ... Xfce 4.8 came with Xubuntu 12.04, but whether or not I can run Xfce 4.10 on 12.04 is what I need to look into... 

Yes you can, Buntu Bunny. In a terminal run the following:```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Buntu Bunny on 2013-09-25
> **slickymaster said:**
> Yes you can, Buntu Bunny....

Slickymaster, thank you! Am I correct that this will simply update Xfce? IOW, I don't have to uninstall 4.8 to upgrade to 4.10?

---

### Post by slickymaster on 2013-09-25
> **Buntu Bunny said:**
> Slickymaster, thank you! Am I correct that this will simply update Xfce? IOW, I don't have to uninstall 4.8 to upgrade to 4.10?

Yes Buntu Bunny, your assumption is correct. In the meantime I'm trying to figure out the transparency issue with the icons in your desktop.

---

### Post by Buntu Bunny on 2013-09-25
> **slickymaster said:**
> Yes Buntu Bunny, your assumption is correct. In the meantime I'm trying to figure out the transparency issue with the icons in your desktop.

Slickymaster, thank you so much. I cannot tell you how relieved I am to have your help.

I have successfully upgraded to Xfce 4.10 and Thunar 1.6.3, and can report

```
$ ls -la ~/.config/Thunar/
total 20
drwx------  2 buntubunny buntubunny 4096 Sep 25 10:12 .
drwx------ 57 buntubunny buntubunny 4096 Sep 24 11:28 ..
-rw-r--r--  1 buntubunny buntubunny  103 Sep 25 10:09 accels.scm
-rw-rw-r--  1 buntubunny buntubunny 1262 Sep 24 21:52 thunarrc
-rw-------  1 buntubunny buntubunny  381 Sep 25 10:12 uca.xml
```

However, the other problems still exist:
[LIST]
[*]desktop icon text background transparent
[*]cannot change wallpaper
[*]Unity Settings pops up if I right click desktop and select "Change Desktop Background", (rather than Xfce's Settings Manager). 
[/LIST]

To quote Laura Ingalls Wilder, 

> If it isn't chickens, it's feathers.

---

### Post by Buntu Bunny on 2013-09-25
Another clue. Nautilus is opening my desktop folders, even though Thunar is selected in my preferred applications. Thunar opens folders from panels or menus. Is there a way to disable Nautilus and let Thunar handle the desktop?

---

### Post by slickymaster on 2013-09-25
> **Buntu Bunny said:**
> Another clue. Nautilus is opening my desktop folders, even though Thunar is selected in my preferred applications. Thunar opens folders from panels or menus. Is there a way to disable Nautilus and let Thunar handle the desktop?

Buntu Bunny, see if this article can provide you any help: [Securing XFCE's Control over the desktop Against Nautilus]("http://cmpstuff.blogspot.pt/2009/09/securing-xfces-control-over-desktop.html")

---

### Post by Buntu Bunny on 2013-09-25
Well, I appeared to have really messed up. I followed the steps in  [Securing XFCE's Control over the desktop Against Nautilus]("http://cmpstuff.blogspot.pt/2009/09/securing-xfces-control-over-desktop.html"). When I got to the part about gconfig-editor > apps > Nautilus > Preferences > uncheck 'Show Desktop', I didn't have a Show Desktop. Only 'start_with_sidebar' was checked. I unchecked it, rechecked it, and closed gconfig-editor. Now it would seem something happened to my desktop manager, I have only a blank grey screen for a desktop! My panels are still there but nothing else: no icons, no wallpaper, no screen saver, no right click. In the desktop file manager window, Thunar shows everything that is supposed to be there, but it's hidden by this grey wall!

---

### Post by vasa1 on 2013-09-25
I looked at that link last night. It was from 2009. I'm not sure but a lot of things may have been moved around: dconf is also there. Then, as the author cautions, although Linux may be "modular", mixing and matching can have unexpected results. That's partly why I don't like having more than one desktop environment. You have three, if I understand correctly: Unity, Xfce, and GNOME Classic. Then, and this is just my bias, Nautilus is one of those "take charge" things and sorting it out takes quite a bit of experience if not trial and error. Plus, Nautilus is evolving rapidly, so what was suggested in 2009 may not work now.

---

### Post by Buntu Bunny on 2013-09-25
> **vasa1 said:**
> I looked at that link last night. It was from 2009. I'm not sure but a lot of things may have been moved around: dconf is also there. Then, as the author cautions, although Linux may be "modular", mixing and matching can have unexpected results. That's partly why I don't like having more than one desktop environment. You have three, if I understand correctly: Unity, Xfce, and GNOME Classic. Then, and this is just my bias, Nautilus is one of those "take charge" things and sorting it out takes quite a bit of experience if not trial and error. Plus, Nautilus is evolving rapidly, so what was suggested in 2009 may not work now.

Yes, that was the risk. You're correct, vasa1, there are three desktops on this computer, which likely compounded the issue. There is a mix and match of applications and things that pop up (gedit for example when I open an existing text file. If I open a text editor from my panel, it's leafpad).

Seems if I could restore my desktop manager, that would be a step in the right direction. 

I've tried this

```
$ xfwm4 --sm-client-disable
xfwm4-Message: Another Window Manager (Xfwm4) is already running on screen :0.0
xfwm4-Message: To replace the current window manager, try "--replace"

(xfwm4:28840): xfwm4-WARNING **: Could not find a screen to manage, exiting
$ xfwm4 --replace
Waiting for current window manager (Xfwm4) on screen :0.0 to exit: Done
```

No change.

---

### Post by vasa1 on 2013-09-26
Coming back to the idea of using pure Xubuntu for both users, if the requirement for Nautilus as file manager isn't **absolute** and Thunar would suffice, I would guess that Xubuntu could be configured to be like GNOME Classic.

---

### Post by Buntu Bunny on 2013-09-26
> **vasa1 said:**
> Coming back to the idea of using pure Xubuntu for both users, if the requirement for Nautilus as file manager isn't **absolute** and Thunar would suffice, I would guess that Xubuntu could be configured to be like GNOME Classic.

Apparently so. In fact, I found [this article]("http://www.namakutux.id.or.id/2011/11/how-to-make-xfce-looks-like-gnome-2.html") awhile back, and bookmarked it for when the time came to upgrade from 12.04. If I can't sort this out satisfactorily, then that time may have come upon me sooner than I'd anticipated. :smile:

---

### Post by slickymaster on 2013-09-26
I'm really sorry to hear that following the steps in that article lead you to a worst situation than you previously were, and even though it's from 2009 I think that what might have cause the mess your stuck with now was probably the non-pacific coexistence of your three installed desktop environments.

In order to restore your desktop I was going to suggest you to run ```
xfwm4 --sm-client-disable
```but I see that you already done that to no avail and with ```
xfwm4 --replace
```nothing also happened.

Let's not give up on this for the time being.

---

### Post by Buntu Bunny on 2013-09-26
> **slickymaster said:**
> Let's not give up on this for the time being.

Slickymaster, thank you. Fortunately, it mostly amounts to an inconvenience and an aesthetic issue (grey is not my favorite color :) ) I can still find and do what I need to do. I have to say I've come to appreciate the convenience of a functioning desktop. As they say, absence makes the heart grow fonder.

---

### Post by Buntu Bunny on 2013-09-26
Here's an update on my research. Apparently my problem is that xfdesktop is no longer running. (See attached screenshot). I note that my process IDs are not the same as the example on [Xfce's Preferences page.]("http://docs.xfce.org/xfce/xfce4-session/preferences") In Settings Editor > xfce4-desktop, backdrop, screen monitor, desktop and file icons are (type) empty. 

On the Xfce forums, I found someone with a similar problem, [Xfce Launches Nautilus Instead of Thunar]("https://forum.xfce.org/viewtopic.php?id=6886"), but I don't know how to apply his solution at this time. 

More tomorrow.

---

### Post by vasa1 on 2013-09-26
Maybe start a new thread with an appropriate title because Thunar running slow is no longer the main issue?

As for the PIDs being different, that's okay. Even your PIDs on the same machine with absolutely nothing changed will differ from session to session. What's important is what is under "Program" and "Restart Style".

---

### Post by Buntu Bunny on 2013-09-27
> **vasa1 said:**
> Maybe start a new thread with an appropriate title because Thunar running slow is no longer the main issue?

I thought this a good suggestion, so I decided to start a new thread. As always, I clicked "Check If Already Posted." There were a few leads, so I took a look and found a few old threads from 2009, addressing xfdesktop recovery. They all pointed to this thread, [http://ubuntuforums.org/showthread.php?t=1138641&highlight=xubuntu+reboot]("http://ubuntuforums.org/showthread.php?t=1138641&highlight=xubuntu+reboot")

> When the cursor appears press alt+f2 and run xfce4-panel to recover the panel and xfdesktop to recover the desktop. 

Alt+F2 no longer brings up run dialogue, rather, I get Application Finder. So I tried this in terminal:

```
~$ xfdesktop

(xfdesktop:4300): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed
```

I was thinking, oh darn, but realized that my desktop was indeed back: wallpaper, icons, and icon text. Right click brings up the xfdesktop menu. I will save session for future logins. 

Not sure what happened or why, but am thankful all is right in my world once again.

Thank you to everyone who responded, your help is deeply appreciated. This forum has enabled me to escape Windows, something for which I am eternally grateful.

---

### Post by slickymaster on 2013-09-27
> **Buntu Bunny said:**
> Here's an update on my research. Apparently my problem is that xfdesktop is no longer running. (See attached screenshot). I note that my process IDs are not the same as the example on [Xfce's Preferences page.]("http://docs.xfce.org/xfce/xfce4-session/preferences") In Settings Editor > xfce4-desktop, backdrop, screen monitor, desktop and file icons are (type) empty. 

On the Xfce forums, I found someone with a similar problem, [Xfce Launches Nautilus Instead of Thunar]("https://forum.xfce.org/viewtopic.php?id=6886"), but I don't know how to apply his solution at this time. 

More tomorrow.

Yes, your screenshot confirms it. You don't have **xfdesktop** running. I'm attaching a screenshot of mine. [ATTACH=CONFIG]246530[/ATTACH]

As for the fact that in your Settings Editor you don't have the items backdrop, screen monitor, desktop and file icons ticked under the xfce4-desktop category, that's expected. The same also in mine.

Following the thread on Xfce forum, did you tried to clean your ```
~/.cache
```

> **vasa1 said:**
> ...
As for the PIDs being different, that's okay. Even your PIDs on the same machine with absolutely nothing changed will differ from session to session. What's important is what is under "Program" and "Restart Style".

Yes, vasa1 is completely right. A session contains a number of process groups, and a process group contains a number of processes, and a process contains a number of threads. Each process has a unique nonnegative integer identifier that is assigned when the process is created in a process group of a session.

---

### Post by Buntu Bunny on 2013-09-27
@ slickymaster, by now you've probably caught up with the last posts in the thread. I can't say I understand the hows of these problems any more than the whys. I'm just relieved it worked out, plus I've upgraded to Xfce 4.10! As always, I'm grateful for your help. Many thanks for encouraging me not to give up.

---

