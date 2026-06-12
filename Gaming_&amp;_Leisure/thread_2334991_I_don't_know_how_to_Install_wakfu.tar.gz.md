---
title: "I don't know how to Install wakfu.tar.gz"
date: 2016-08-24
forum: Gaming &amp; Leisure
---

### Post by kupaiceace on 2016-08-24
Recently I changed my OS on my laptop to Ubuntu 16.04 LTS 64-bit OS I was using Windows before on it i wanted to play Wakfu on laptop but I've no idea how to install it or setup it cause it's not simple as windows so if any one can give me instruction to know how to install it .
By the way the game site is [http://www.wakfu.com/](http://www.wakfu.com/)
the game is available in .tar.gz and again I've no idea how to install it i tried to extract it but i got no where with this step so please help me with that problem :D :confused::confused:

---

### Post by TheFu on 2016-08-24
I don't know **anything** about wakfu.

Linux is very flexible. There are many different ways to get programs on and installed on all Linux systems.  tar.gz is the same as tgz.  These are usually "source" packages. Basically a tgz file is like a ZIP file, but with full Unix permissions and directories included. This can be very important, as Linux or Unix is a multi-user OS to a different level than Windows. At the core, from the beginning, Unix is multi-user.

Anyway - this might help: [http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file)

Source installations can be easy or very difficult. There is always a README or INSTALL file included inside those pkgs which should describe the installation process. That isn't always the case, since these programs are usually NOT commercial. If you want better installations, send the dev team a few bucks. That will get their attention.

Linux is not Windows. Learn it. Know it. Love it.

---

### Post by Bucky Ball on 2016-08-24
Just for the record, the address to the game page [is here]("http://www.wakfu.com/en/mmorpg/download"). They do not make the instructions for installing on Linux obvious or even there that I can find.

As for extracting it, double click and compression software should pop up to do it for you. Just hit 'Extract' and it should extract to the same folder the tar.gz is in.

If an app doesn't pop up, install Xarchiver then double click the tar.gz file again. Xarchiver should deal with it. Saves you compiling and from what I can see in the tar.gz file, there is nothing to compile, no make file, so don't know that the link TheFu has posted will be of much help. :|

For everyone's info, find attached a pic of what's in the tar.gz. I'm wondering if it's as easy as extracting and simply double clicking the 'wakfu' file. :-k

---

### Post by kupaiceace on 2016-08-24
Thanks I'll check it out

---

### Post by kupaiceace on 2016-08-24
> **Bucky Ball said:**
> Just for the record, the address to the game page [is here]("http://www.wakfu.com/en/mmorpg/download"). They do not make the instructions for installing on Linux obvious or even there that I can find.

As for extracting it, double click and compression software should pop up to do it for you. Just hit 'Extract' and it should extract to the same folder the tar.gz is in.

If an app doesn't pop up, install Xarchiver then double click the tar.gz file again. Xarchiver should deal with it. Saves you compiling and from what I can see in the tar.gz file, there is nothing to compile, no make file, so don't know that the link TheFu has posted will be of much help. :|

For everyone's info, find attached a pic of what's in the tar.gz. I'm wondering if it's as easy as extracting and simply double clicking the 'wakfu' file. :-k

It's not just that simple

---

### Post by lisati on 2016-08-25
> **Bucky Ball said:**
> For everyone's info, find attached a pic of what's in the tar.gz. I'm wondering if it's as easy as extracting and simply double clicking the 'wakfu' file. :-k

I had a quick look, the wakfu file appears to be a bash script to start the game. There's also mention on the website that you need an account in order to play the game.

---

### Post by Bucky Ball on 2016-08-25
> **kupaiceace said:**
> It's not just that simple

Thanks for sharing. Pity. In that case, if you know it's not that simple perhaps you also know how it can be installed and could help by sharing that, too. Any ideas? :)

---

### Post by TheFu on 2016-08-25
Took a look at the package.  No install included/needed.  The de-compression will create a directory structure for a Qt-based program.  They also are clear that an online account is mandatory for this to work. The only "installation" is to de-tar the file where you'd like it to be located permanently.  I'd put it in ~/games/ myself, but anywhere under your HOME would be fine.

After the tar.gz is expanded, there is a startup script ... Wakfu/Wakfu to be run.  chdir into the Wakfu/ directory and run ./Wakfu to see the program startup.

---

### Post by nargaroth_reg on 2016-08-27
I tried this game with steam and didn't have any issues, perhaps you could try installing it via steam.

---

### Post by pebbles2 on 2016-09-05
:KS Here's how I solved it.
I extracted the .tar.gz file (tarball) with archive manager. I had extracted it to Downloads.

Then in the terminal I typed:
```
cd Downloads
cd Wakfu
cd transition
chmod + X transition
./transition
```

It should start installing. (Earlier I had tried cd Downloads cd Wakfu chmod + X Wakfu ./Wakfu. It asked to me accept the terms of service but stopped at 68% and then I was denied access to it.)
You may be told that a file named libsomething12.0 is missing. Simply copy the file name and search the internet for the missing file. Installation steps are on the internet.

Keywords: Fedora 24 (Linux 64bit) Wakfu 3.11.1 installation without steam.

---

### Post by pebbles22 on 2016-09-06
(Lost email. I'm pebbles2. Mods, plz forgive. 8-[ )

I almost did the install with the steps above. However, I get an
 > Error : U04020092
An error occurred whilst writing to disk. Check that there is sufficient space and that you have the necessary rights.
Could not write contents/sounds/musics/musics_full.pk.

I go to the Wakfu site and it says I need to enable permissions, but only says how to do it on windows.

How do I enable it to have permissions so I can complete the installation of Wakfu on Linux 64bit (in my case fedora)?
 
Edit: I have tried opening the./Wakfu file in root but it tells me not to use root for this. I almost did open ./transition in root, but it did not load. I only get an "this application is opened..." in the window list. [[I used tweak tools software to get the window list extension, which is how I have this result.]]

---

