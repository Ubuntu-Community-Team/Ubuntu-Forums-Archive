---
title: "Installing  The Opera Programme Problem"
date: 2005-10-26
forum: Desktop Environments
---

### Post by rickon on 2005-10-26
Installing  The Opera Programme Problem

Hi all,

Having problems installing The Opera programme (and programmes in general).

I am following the instructions in the Wiki which are very clear but always seem to come unstuck because I don't understand everything.

The instructions say to download onto the Desktop which I have done.  Do I then have to extract these files or do something else?????

I get stuck next with the instruction: sudo dpkg -i opera<Tab key>.deb.  I know I type this in the Terminal and am happy using my password etc.  However I am not sure about the tab key part.....do  I hit the tab key or have I got to put something else in there.

I have tried looking in the forum etc, but I keep getting stuck....can you help please.

Thanks

Rickon

---

### Post by madjo on 2005-10-26
where it says <Tab key> just press the tab key...
what that does is autofill the filename.. in most cases it is enough to do this:
sudo dpkg -i opera<Tab key>
that will fill in for instance: opera-8.4-ubuntu.deb or whatever filename it is :)

---

### Post by rickon on 2005-10-27
Thanks for the reply, however when I hit the tab key nothing happens apart from a beep noise.

When I have downloaded the file to the desktop do I have to extract it to the desktop, and then do I have to do anything else.

Sorry I am so new to this I might be making lots of mistakes.

Rickon

---

### Post by MarioFrick on 2005-10-27
It's very easy, just type:

cd Desktop
ls

and take a look at the opera file you just downloaded, it should be something like:
opera_8.50-20050916.6-shared-qt_en_etch_i386

Then type:

sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb

I installed it last night, so the version should be the same.

---

### Post by rickon on 2005-10-27
[QUOTE=MarioFrick]It's very easy, just type:

cd Desktop
ls

and take a look at the opera file you just downloaded, it should be something like:
opera_8.50-20050916.6-shared-qt_en_etch_i386

Then type:

sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb

I installed it last night, so the version should be the same.[/QUOTE]

MarioFrick, Thanks, that has made my day, week, year, etc....I was missing the part about typing CD Desktop, it works great now.

Can you tell me where you found this knowledge is there a user guide about this somewhere?

Brilliant

Rickon

---

### Post by MarioFrick on 2005-10-27
Oh, I'm just a newbie to Linux, I just spent the last months trying different distros and now I'm back to Ubuntu! :) But I grew up using DOS so it's not so hard to use the command line again! :D

Anyway there are surely tons of documentations about linux commands, but I never had the time to read them all! :D Just read this wonderful forum and try to understand what you are going to do, don't just copy and paste... it helps, believe me! And ask, there are very nice and friendly people here.

---

### Post by rickon on 2005-10-27
thanks for the reply, Opera works ok now apart from a message about plugins and installing Motif.........any ideas how to cure this problem?

Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/netscape/plugins-libc6/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
/usr/lib/netscape/plugins-libc6

Regards

Rickon

---

### Post by majkmil on 2005-10-30
I have this problem also need to install Motif but it is not in synaptic or apt. HELP!

---

### Post by kvlastos on 2005-10-30
I also had this problem earlier. I think there is a problem with a Mozilla plugin, etc. The Motif noted in the error messaage is part of the Opera Ubuntu install package so when that error message appears it is because the package did not install properly.

In any case, the last install I did worked and the entire Opera package loaded properly. Also, I had been working with a Hoary to Breezy update done simply with repository editing and the last go round with Opera was with a fresh install from the Breezy cd.

If you have continuing problems, you can always install the Deb static package which may solve the problem another way.

Good luck.

K

---

### Post by Xian on 2005-10-30
[QUOTE=majkmil]I have this problem also need to install Motif but it is not in synaptic or apt. HELP![/QUOTE]
It is in Synaptic but the version is not compatable.

```
$ sudo apt-cache policy libmotif3
libmotif3:
  Installed: 2.2.3-1
  Candidate: 2.2.3-1
  Version table:
 *** 2.2.3-1 0
        500 http://us.archive.ubuntu.com breezy/multiverse Packages
        100 /var/lib/dpkg/status
```

Install the lesstif2 package instead.

```
$ sudo apt-get install lesstif2
```

```
$ sudo apt-cache policy lesstif2
lesstif2:
  Installed: 1:0.93.94-11.4ubuntu3
  Candidate: 1:0.93.94-11.4ubuntu3
  Version table:
 *** 1:0.93.94-11.4ubuntu3 0
        500 http://us.archive.ubuntu.com breezy/universe Packages
        100 /var/lib/dpkg/status
```

EDIT: Be sure to install this version if not using the static build of Opera:

[opera_8.50-20050916.5-shared-qt](http://mirrors.symetrix.net/pub/ftp.opera.com/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb)

.

---

### Post by Princey on 2005-10-31
[QUOTE=kvlastos]
If you have continuing problems, you can always install the Deb static package which may solve the problem another way.

Good luck.

K[/QUOTE]

I have the static version installed on a freesh breezy instal on a clean new hard drive and I'm getting the same error. I followed the next tip on using lesstif2 but I get this error message:

sudo apt-get install lesstif2
Reading package lists... Done
Building dependency tree... Done
Package lesstif2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lesstif2 has no installation candidate

Does that mean lesstif2 is also not installed? Any help is appreciated.


------------------------------------------------------------------
Update:

I installed Synaptic since adept doesn't allow you to search for files in non standard repositories (correct me if I'm wrong of a way how to). I found it in an "unstable" repository and installed it. The moment I did, I closed Opera, re-opened and voila! it worked perfectly fine. Thanks for the help. I guess that's the curve towards learning--got to use the brain to figure some work arounds

---

### Post by Effect on 2005-11-04
I don't know what I"m doing wrong but I still can't get this to install. I've tried with the guide says. I tried using the "static" version but still nothing installs. I'm in the correct folder while in the terminal but nothing.

Can anyone give a an easier way of installing a deb file?

When I tried SuSE, it was so much easy with YAST. Is there anything like this for Ubuntu where you just view the file in one thing and get the option to just click a button for a program to install it? No fuss or anything?

Thanks.

---

### Post by Princey on 2005-11-04
[QUOTE=Effect]I don't know what I"m doing wrong but I still can't get this to install. I've tried with the guide says. I tried using the "static" version but still nothing installs. I'm in the correct folder while in the terminal but nothing.

Can anyone give a an easier way of installing a deb file?

When I tried SuSE, it was so much easy with YAST. Is there anything like this for Ubuntu where you just view the file in one thing and get the option to just click a button for a program to install it? No fuss or anything?

Thanks.[/QUOTE]

Here's my way I went about it. I have made a few alterations to aid you avoiding some of the error problems that some of encountered.


1. Be sure to install lesstif2 first. You can do that using Synaptic. Do a search for it and install it.

2. Download opera using this link [http://www.opera.com/download/index.dml?step=2&opsys=Linux%20i386&platform=linux]("http://www.opera.com/download/index.dml?step=2&opsys=Linux%20i386&platform=linux")
(be sure to chose ubuntu from the distribution vendor from the drop down box and chose which version. I'm assuming you're using breezy so chose ubunty breezy and then chose a location closest to you.)

3. Assuming you downloaded it to your desktop, open konsole and type in the following:

cd Desktop

followed by this command

sudo dpkg -i opera (press tab at this point to make it autocomplete the file name) 

press enter

it should prompt for your password at this time, type in your password. 


4. Everything should run smoothly at this time. Just close konsole and check in your internet folder from your kde menu. If you want, right click on the shortcut in the start menu and chose to create a shortcut on the desktop for easier access. 


Good luck!!!

---

