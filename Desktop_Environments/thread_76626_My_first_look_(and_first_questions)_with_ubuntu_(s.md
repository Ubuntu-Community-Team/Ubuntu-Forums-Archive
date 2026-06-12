---
title: "My first look (and first questions) with ubuntu (sorry, long post)"
date: 2005-10-15
forum: Desktop Environments
---

### Post by BRODEL on 2005-10-15
I've been using Windows for over 10 years now so it's just what I know. I've tried different distributions of Linux before and have been able to get most of them to do basic stuff after the install. The main problem was getting it to do anything else I wanted that wasn't included with the installation. Installing programs never worked out for me. 

For me to even think of using it, it has to do basic stuff that I do everyday or I will only pick it up when I want to sit down and try to fight it to get it to do what I want. If I can't browse the web or use Gaim or check my e-mail at the very least on my laptop with wireless then it's worthless to me. 

Another big pain was when I went somewhere for help with something I never got any answers. They all just didn't seem to want to help a Linux newbie. 

I've been reading things all over the Internet lately about ubuntu so I did some looking around. After doing a little research on the web and browsing these forums, (I've seen a lot of help given on these forums and thought this might be a good place to get some help when I needed it.) I figured I'd try yet another Linux distribution and maybe this time I would be able to stick with it. I installed Ubuntu on a spare laptop I had and was amazed that after the install it could connect to the wireless access point and get on the Internet without me having to jump through a billion hoops! I've read the "Is ubuntu for you" post on here and it seemed like a good fit to me. 

Anyway just wanted to say that so far I like this distribution better than any other I've ever bothered with. 

Ok, now for a few questions I have after installing.

I went to download VLC and tried to go by the debian install instructions. When I ran apt-get update I got this:

> apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"

I tried doing su - (something I picked up from trying other distributions) but it didn't take the password. Is there a better way to get root access in the terminal window? 

I also tried using the synaptic package manager and installed libxine1c2. At least I think it installed it. Problem is.. if it did install it, I don't know where it put it or how to start it. I just want something to be able to play MP3s and maybe some videos. 

When I tried to install another theme I found on the Internet, I browsed to the tar.gz file and it said something about being an invalid file format. I'm not sure what went wrong there. 

Anyway, I haven't had it installed long, so that's about all I have for questions (for now) 

Hopefully I can get stuff figured out and be around here for a while to ask some more. It would be great to be able to help people later on as well, but I'm a long ways from being able to do that right now. The dream is to ditch Windows.. but that's so far away it's just a dream. Especially since I deal with Windows all day at work. 

Thanks in advance for your help and sorry for the long first post!

---

### Post by adwait on 2005-10-15
Try sudo
```
sudo <any command>
```
Use your own password, and it will execute the command as root.

---

### Post by Kokanee on 2005-10-15
Synaptic must be closed too.

---

### Post by mcduck on 2005-10-15
You don't need to unzip the thepe package, instead just drag+drop it to the Theme Preferences window (System/Preferences/Theme). (or unzip them to ~/.themes) 

You could also try the Gnome Art Manager (find it with Synaptic, install and then it's in System/Preferences/Art Manager). It will allow you to browse and install themes and backgrounds from art.gnome.org without even opening your web browser..

---

### Post by DJ-Power on 2005-10-15
I am glad its not just me thats found this problem then. I too am a complete beginner and I have tried to use the su command in the terminal but when it asks for the password it doesnt seem to let you type it in. No matter what i do with the keys nothing is entered the cursor just stays in the same place. I hope someone has got an answer for this problem as so far I am more than pleased with my first steps into linux.

---

### Post by BRODEL on 2005-10-15
sweet apt-get worked.. I think

This kind of concerns me though:
> Fetched 231B in 1s (189B/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

I ran it right after getting that and it didn't give me that error.. I guess it's all ok though. 

Awesome. I'm gonna try to get VLC on here now. Thanks!

---

### Post by BRODEL on 2005-10-15
Or not :(

> brodel@a31p-ubuntu:/$ sudo apt-get install vlc libdvdcss2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc

---

### Post by BRODEL on 2005-10-15
[QUOTE=mcduck]You don't need to unzip the thepe package, instead just drag+drop it to the Theme Preferences window (System/Preferences/Theme). (or unzip them to ~/.themes) 

You could also try the Gnome Art Manager (find it with Synaptic, install and then it's in System/Preferences/Art Manager). It will allow you to browse and install themes and backgrounds from art.gnome.org without even opening your web browser..[/QUOTE]


Tried to drag and drop it looked like it started then gave me "The file format is invalid" again. 

I'll look at the Gnome Art Manager a little later probably. I'd like to have a new theme, but it's not a huge deal. Thanks.

---

### Post by BRODEL on 2005-10-15
[QUOTE=DJ-Power]I am glad its not just me thats found this problem then. I too am a complete beginner and I have tried to use the su command in the terminal but when it asks for the password it doesnt seem to let you type it in. No matter what i do with the keys nothing is entered the cursor just stays in the same place. I hope someone has got an answer for this problem as so far I am more than pleased with my first steps into linux.[/QUOTE]


I think that's supposed to happen. It's not showing anything so it doesn't show the password you're typing in.

---

### Post by Hooplife on 2005-10-15
Hi,
Just wanted to try and clarify your "sudo" question.
Ubuntu doesn't use "root" unless you enable it.  Instead, Ubuntu uses "sudo" which means "superuser do".
Use "sudo" before your command. For example, if I wanted to edit my xorg.conf file I would type "sudo gedit /etc/X11/xorg.conf". You will then be asked for your password, which is the same one you use to log on at startup.

Hope that was some help. If you have any other questions feel free to ask. I've only been using Ubuntu for a few months but have fallen in love with the distro. The ease of use and the help in the forums surpass every other distro I've tried and I've tried Mandrake, Mepis, Fedora, Suse, and Knoppix.

---

### Post by futz on 2005-10-15
For a good guide on the sudo thing, go to [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

The Wiki has a lot of very good help files. Go look: [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by BRODEL on 2005-10-15
Ahh.. actually that does clarify that for me. I like knowing how and why things work the way that they do. Thanks. :)

---

### Post by BRODEL on 2005-10-15
[QUOTE=futz]For a good guide on the sudo thing, go to [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

The Wiki has a lot of very good help files. Go look: [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)[/QUOTE]
Thanks. I don't understand everything in the possible issues section of the sudo guide, but I'm sure I'll get there eventually.

---

### Post by erikpiper on 2005-10-15
To get vlc, etc, you will need to enable extra repositories. Very easy. See the wiki:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)

---

### Post by Hooplife on 2005-10-15
You might also want to check out:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

It pertains to Hoary 5.04 and not the newly released Breezy 5.10 but many of the tips are still valid.

---

### Post by BRODEL on 2005-10-15
[QUOTE=erikpiper]To get vlc, etc, you will need to enable extra repositories. Very easy. See the wiki:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)[/QUOTE]
I added them like it says on their site ([http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html))

but it still doesn't find it. I also found this thread. 

[http://ubuntuforums.org/showthread.php?t=46888&page=3](http://ubuntuforums.org/showthread.php?t=46888&page=3)

but that seems to relate to the Horay release and not the Breezy which is what I have right now. I was hesitant to try it, but I could just do it anyway. 

I guess I should ask where you would normally get the repositories to add. I was manually editing the file like it said on the site for VLC, but I guess your way does the same thing.

---

### Post by Lord Illidan on 2005-10-15
The repos can be found on the Ubuntu Guide..

To search for vlc, try entering into a terminal 

```
sudo apt-cache search vlc
```

or else, use synaptic ```
sudo synaptic
``` to search for vlc in the repositories!

Good luck with Ubuntu.. We need fresh blood...

---

### Post by BRODEL on 2005-10-15
Ok, so I added

```
 deb http://archive.ubuntu.com/ubuntu warty universe
 deb-src http://archive.ubuntu.com/ubuntu warty universe
```

then ran it again and got this..
> 
brodel@a31p-ubuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libflac4 but it is not installable
       Depends: slang1 (> 1.4.9dbs-2) but it is not installable
E: Broken packages


dependencies... I remember seeing that over and over again when I tried to install software on other distros.. just seeing that word again makes my blood begin to boil. :evil:

---

### Post by BRODEL on 2005-10-15
Just tried to install VLC via synaptic and got what I guess is pretty much the same message

> vlc:
 Depends: libflac4  but it is not installable
 Depends: slang1 (>1.4.9dbs-2) but it is not installable
 Depends: wxvlc but it is not going to be installed

---

### Post by Lord Illidan on 2005-10-15
Use Synaptic... and search for slang1.

Then right click on it =>Properties, and Version. There, you can force install a different version of slang1...

However, I think you better take off the Ubuntu Warty repos.. You are asking for trouble, especially if you are now using Breezy Badger!!

---

### Post by jediknight9999 on 2005-10-15
I think your need to edit your sources.  You added    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **warty** universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **warty** universe

warty should be changed to breezy.

---

### Post by BRODEL on 2005-10-15
Ahh I didn't think about just changing warty to breezy. The post I found was for warty so I figured I'd try it. I couldn't find a working repository that had vlc on it. 

Now for the stupid question.. where was that information? I'm just trying to figure out where to find stuff on my own so I don't have to keep bugging you guys. You guys rock though. 

Ok.. it just got done installing.. but umm.. where is it? How do I open it or do I need to do something else first?

Edit: for the heck of it, I typed in VLC in the terminal and it worked. I was shocked.. 

Anyway, for future refrence for other packages I'd still like to know how to find out where apt-get or synaptic puts stuff I have it install.

---

