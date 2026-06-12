---
title: "How do I put NOTES on files and folders in 12.04?"
date: 2012-06-07
forum: Desktop Environments
---

### Post by Thinkintuit on 2012-06-07
In 10.04 I was used to putting notes on files (and sometimes folders)--I would right-click, select "notes" and then type anything from a few words to pages of info, quotes from the file etc. It was like putting a post-it note on a file. 

This option has been discontinued in 12.04, but is central to the way I do my work (which involves sorting through thousands of files & coming back later to read the notes I've made).

How can I achieve a similar result on 12.04--any ideas? 

It kind of blows my mind that such an incredibly useful feature was discontinued! :confused:

---

### Post by Morbius1 on 2012-06-07
The first thing I found was this: [http://askubuntu.com/questions/90853/file-notes-tab-gone-in-nautilus-3-2-1](http://askubuntu.com/questions/90853/file-notes-tab-gone-in-nautilus-3-2-1)

> It kind of blows my mind that such an incredibly useful feature was discontinued! :confused: 	
Remember this is Gnome. If it's a feature it will eventually go away.

---

### Post by traditionalist on 2012-06-07
> **Thinkintuit said:**
> In 10.04 I was used to putting notes on files (and sometimes folders)--I would right-click, select "notes" and then type anything from a few words to pages of info, quotes from the file etc. It was like putting a post-it note on a file. 

This option has been discontinued in 12.04, but is central to the way I do my work (which involves sorting through thousands of files & coming back later to read the notes I've made).

How can I achieve a similar result on 12.04--any ideas? 

It kind of blows my mind that such an incredibly useful feature was discontinued! :confused:

There is a way to do it, but it is somewhat complex.  You can add any command/ function you like to the context menu of nautilus using this;

[http://www.grumz.net/index.php?q=taxonomy/term/2/9](http://www.grumz.net/index.php?q=taxonomy/term/2/9)

more info;

[http://www.makeuseof.com/tag/add-custom-functionality-to-nautilus-linux/](http://www.makeuseof.com/tag/add-custom-functionality-to-nautilus-linux/)

[http://tuxtweaks.com/2010/03/expand-the-gnome-file-manager-with-nautilus-actions/](http://tuxtweaks.com/2010/03/expand-the-gnome-file-manager-with-nautilus-actions/)

works really well and you can add whatever functions you require.

There are also a number of functions built in which you can apply. Examples;

[[IMG]http://img513.imageshack.us/img513/7608/workspace1021.th.png[/IMG]]("http://img513.imageshack.us/i/workspace1021.png/")

I am a new Ubuntu/linux  user, but as I understand it this also replaces various functions that were available in previous versions and have been removed.  I have only ever used 12.04 and I have been using it for four weeks.

---

### Post by Thinkintuit on 2012-06-07
Thanks for your reply, Traditionalist! 

As a non-technical user, I find the phrase "it is somewhat complex" a bit intimidating. :shock:

But I will have a look at the link you posted and maybe it won't be too scary...

---

### Post by traditionalist on 2012-06-07
> **Thinkintuit said:**
> Thanks for your reply, Traditionalist! 

As a non-technical user, I find the phrase "it is somewhat complex" a bit intimidating. :shock:

But I will have a look at the link you posted and maybe it won't be too scary...

It's not that bad, just not really something for absolute beginners. It is really good though, you can set up anything you like as a nautilus function.

You might also find this very useful;

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

there is a lot of stuff already set up for you, you just need to click on it. Very useful indeed.

This makes scripts easier to set up:

[[IMG]http://img18.imageshack.us/img18/9932/ubuntusoftwarecenter023.th.png[/IMG]](http://img18.imageshack.us/i/ubuntusoftwarecenter023.png/)

---

### Post by LewisTM on 2012-06-07
Some info on how the notes are handled, and how to set and retrieve them:
[http://askubuntu.com/questions/14669/are-file-notes-exclusive-to-nautilus-is-there-a-terminal-cli](http://askubuntu.com/questions/14669/are-file-notes-exclusive-to-nautilus-is-there-a-terminal-cli)
Note that [MATE]("http://mate-desktop.org/"), the GNOME 2 fork, still supports notes and emblems. It runs fine under 12.04 and should be able to read and write your notes.
In fact once you have the MATE repo added you only have to install Caja, the Nautilus equivalent. This will bring in minimal MATE dependencies. Run:
```
caja --no-desktop
``` and you should be good to go. 

Cheers!

---

### Post by traditionalist on 2012-06-07
> **LewisTM said:**
> Some info on how the notes are handled, and how to set and retrieve them:
[http://askubuntu.com/questions/14669/are-file-notes-exclusive-to-nautilus-is-there-a-terminal-cli](http://askubuntu.com/questions/14669/are-file-notes-exclusive-to-nautilus-is-there-a-terminal-cli)
Note that [MATE]("http://mate-desktop.org/"), the GNOME 2 fork, still supports notes and emblems. It runs fine under 12.04 and should be able to read and write your notes.
In fact once you have the MATE repo added you only have to install Caja, the Nautilus equivalent. This will bring in minimal MATE dependencies. Run:
```
caja --no-desktop
``` and you should be good to go. 

Cheers!

 Be aware that mate will not run on all 12.04 systems. It will shoot the graphics down on some systems and the machine is then very difficult to recover. So make sure you have a good backup before you try it.

---

### Post by LewisTM on 2012-06-07
If he does the Caja-only trick he's in no danger since he's not taking over the desktop or WM. I'm running Caja here on XFCE to read my old notes, although Thunar is my day-to-day file manager. Both support emblems but only Caja supports Notes.

---

### Post by traditionalist on 2012-06-07
> **LewisTM said:**
> If he does the Caja-only trick he's in no danger since he's not taking over the desktop or WM. I'm running Caja here on XFCE to read my old notes, although Thunar is my day-to-day file manager. Both support emblems but only Caja supports Notes.

I tried it twice. Shot my graphics down. According to this you need the core;

[http://mate.karapetsas.com/index.php?page=package&package=caja](http://mate.karapetsas.com/index.php?page=package&package=caja)

and I am fairly sure that the core is what shoots the graphics down.

I also asked about it on the mate forums. No answer.

[http://forums.mate-desktop.org/viewtopic.php?f=6&t=175&p=965#p965](http://forums.mate-desktop.org/viewtopic.php?f=6&t=175&p=965#p965)

---

### Post by LewisTM on 2012-06-07
Nope, not on the latest PPA from packages.mate-desktop.org
I don't have core installed.

```
Package: caja
Source: mate-file-manager
Version: 1.2.2-1+precise
Architecture: amd64
Maintainer: Stefano Karapetsas <stefano@karapetsas.com>
Installed-Size: 4012
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.14), libcairo2 (>= 1.2.4), libcaja-extension (= 1.2.2-1+precise), libexempi3 (>= 2.2.0), libexif12, libgail18 (>= 1.18.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.31.8), libgtk2.0-0 (>= 2.24.0), libice6 (>= 1:1.0.0), libmateconf, libmatedesktop, libpango1.0-0 (>= 1.20.0), libselinux1 (>= 1.32), libsm6, libunique-1.0-0 (>= 1.0.0), libx11-6, libxml2 (>= 2.7.4), libxrender1, shared-mime-info, desktop-file-utils, mate-vfs, libglib2.0-data, caja-common (= 1.2.2-1+precise)
```

---

### Post by traditionalist on 2012-06-07
> **LewisTM said:**
> Nope, not on the latest PPA from packages.mate-desktop.org
I don't have core installed.

```
Package: caja
Source: mate-file-manager
Version: 1.2.2-1+precise
Architecture: amd64
Maintainer: Stefano Karapetsas <stefano@karapetsas.com>
Installed-Size: 4012
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.14), libcairo2 (>= 1.2.4), libcaja-extension (= 1.2.2-1+precise), libexempi3 (>= 2.2.0), libexif12, libgail18 (>= 1.18.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.31.8), libgtk2.0-0 (>= 2.24.0), libice6 (>= 1:1.0.0), libmateconf, libmatedesktop, libpango1.0-0 (>= 1.20.0), libselinux1 (>= 1.32), libsm6, libunique-1.0-0 (>= 1.0.0), libx11-6, libxml2 (>= 2.7.4), libxrender1, shared-mime-info, desktop-file-utils, mate-vfs, libglib2.0-data, caja-common (= 1.2.2-1+precise)
```

In that case I will try it again because I really wanted to try caja. Although I have now modified nautilus to do what I want.

---

### Post by traditionalist on 2012-06-07
So how did you install it?  I have just tried a couple of times just to install caja and I can't get it to work.

---

### Post by LewisTM on 2012-06-08
I ran these commands (from [here]("http://mate-desktop.org/install/#ubuntu")):
```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu precise main"
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
sudo apt-get install caja
caja --no-desktop
```

If this doesn't work for you then you need to provide more information. Do you get some sort of output when running caja in a terminal?

---

### Post by LewisTM on 2012-06-08
Just a note about something I just found.

Old-style 'notes' are stored in a metadata database which is considered a hassle and only works locally i.e. for the user that is logged in.

What one can do is use file and folder extended attributes to gain the same level of metadata but at the filesystem level.
As long as you are running a recent kernel (>3.0) and a regular Linux filesystem, user extended attributes are enabled by default.

To edit them just install package **eiciel**. It integrates nicely into Nautilus and adds two extra properties tabs: Access Control Lists and Extended Attributes. Use the second one to add as many notes or other info as you want.

Those attributes are retained upon copy or move as long as you remain on a Linux file system. Eiciel can also be run standalone and can take a filename as argument. I think using user-xattr is safer than old-style Nautilus notes because they're part of the filesystem specifications and not a DE feature.

One final tip: Eiciel might not seem to support multiple lines for attributes but that is misleading. Just edit your note in a text editor and paste it in Eiciel. You can also insert a newline character with Ctrl-Shift-U then 000A + Enter.

---

### Post by Morbius1 on 2012-06-09
When I found the time I decided to follow my own advice and looked at the link I posted above: [http://askubuntu.com/questions/90853/file-notes-tab-gone-in-nautilus-3-2-1](http://askubuntu.com/questions/90853/file-notes-tab-gone-in-nautilus-3-2-1)

The very last suggestion - the one that got no votes at all - is the one I focused on since it seemed the most direct way and had all the gvfs elements that [COLOR=Blue]LewisTM[/COLOR] talked about in earlier posts. It's for a nautilus-script but I use Xubuntu so instead I created a Thunar "User Custom Action" using it:

**Name**: Notes
**Command**:
```
/home/morbius/MyScripts/notes-uca %f
```**Appearance Conditions**: Marked everything

In /home/morbius/MyScripts/notes-uca I placed the suggested script:
```
#!/bin/bash
for arg do
if i=`gvfs-info "$arg" | grep -A 1000000 metadata::annotation: | sed s/\metadata::annotation:\// | grep -v metadata:: | zenity  --text-info --editable  --ok-label="ok" --cancel-label="cancel" --checkbox="change"`; then `gvfs-set-attribute -t string "$arg" metadata::annotation "$i"`; else exit
fi
done
```And made it executable:
```
chmod +x /home/morbius/MyScripts/notes-uca
```Since it works as a Thunar custom action I suspect it will work as a nautilus-script assuming gnome still allows a nautilus-script.:wink:

[COLOR=Blue]*Worst case install Thunar ( you can never have too many file managers ) and enjoy it's other benefits like creating custom file associations.*[/COLOR]

---

### Post by Thinkintuit on 2012-06-09
> **Morbius1 said:**
> Remember this is Gnome. If it's a feature it will eventually go away.

Dang...I didn't know about that undocumented metafeature of Gnome. :wink:

Thanks for the link; that helps explain why that feature disappeared. Evidently not many people used it...for me at least, it became incredibly useful, but it sounds like I was very much in the minority there.

I very much appreciate all the efforts to help me resolve this problem. However, almost everything here (or linked to) is over my head by about two orders of magnitude. I read though as much as I could, becoming more and more confused as I went...:confused::confused::confused:

For now my takeaway is: the features I need are simply no longer available in 12.04. Unless I figure out a solution that I can actually implement (which seems extremely unlikely at this point) then I'm going to have to:

a) Continue to use my old laptop, running 10.04, do to my work, and hope it doesn't die anytime soon.
b) Figure out a completely different way to do my job, using the reduced features available on 12.04.

What a drag. :(

---

### Post by Thinkintuit on 2012-06-26
I have a solution, of sorts, to the missing "notes" option: install KDE.

KDE uses a file management system called Dolphin that has a notes field; it also has the ability to put from 1 to 5 stars on a file.

So I could use KDE for working with my files and use something like my old work system. However, that would involve getting used to working with KDE. Currently I'm leaning towards coming up with a different approach to my editing work, using Unity. I mourn the loss of notes, but somehow I will get over it and someday I will learn to love again...  

Thanks again, everyone, for your input on this problem. And thanks especially to my friend Charles V., who took on this problem and eventually pointed me in the direction of KDE.

---

### Post by le_phoceen on 2012-06-30
Hi,

I'm understanding in this thread that emblems associated with files are no longer supported in Gnome 3 or Unity. However, there is a music note emblem with the Music folder in my home folder.

Can someone tell me if I'm mistaken and if emblems still exist in Ubuntu 12.04 with Unity ?

Thanks

---

### Post by Thinkintuit on 2012-07-04
> **le_phoceen said:**
> Hi,

I'm understanding in this thread that emblems associated with files are no longer supported in Gnome 3 or Unity. However, there is a music note emblem with the Music folder in my home folder.

Can someone tell me if I'm mistaken and if emblems still exist in Ubuntu 12.04 with Unity ?

Thanks

[Elsewhere]("http://ubuntuforums.org/showthread.php?t=1998382") blackbird34 hipped me to **Thunar**, which is a different file manager you can install that does support emblems. It's available through the Ubuntu Software Center, or you can install it in terminal by entering **sudo apt-get install thunar**

It will put an icon that looks like a hammer on the left side of the screen, and if you access your files through that you can attach and view emblems.

The emblems you're talking about (e.g. on the video and music folders) look to me like something that's being done by 12.04 but not (easily) changeable at the user level as far as I can tell. I think it's just the way 12.04 is programmed to display those particular preset folders.

---

### Post by LewisTM on 2012-07-04
Those particular folders are called user dirs.
They can be changed by editing file ~/.config/user-dirs.dirs
You can't change their emblems, those are set by the system.
Thunar will allow you to assign emblems to files and folders. However, at least on my system, they don't show in Nautilus.

---

