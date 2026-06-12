---
title: "Descent 3"
date: 2005-04-21
forum: Gaming &amp; Leisure
---

### Post by kelvinq on 2005-04-21
I tried installing Descent 3 for Linux yesterday. Installation went fine but when I tried to start, I get this error:
```

kelvinq@ubuntu:~/Desktop/downloads/bt/d3/Descent 3 Mercenary$ descent3
Creating Loki preferences directory: /home/kelvinq/.loki/
Creating descent3 preferences directory: /home/kelvinq/.loki/descent3

Descent 3 Message(Error: Unable to find version key for Descent 3)

System Error
```

Does anyone else have these errors? I tried to patch by using the official patches, no luck in applying the patches either.

---

### Post by waverave on 2005-08-18
I've got the same problem...i found some hints that renaming some files would do the trick:

 su - to root, cd to your Descent 3 directory (/usr/local/games/descent3, usually). Then ln -s ppics.hog PPics.Hog

...but it didn't help!! Anyone has the remedy for our problem, PLZ!

Best regards

---

### Post by Mishura on 2005-08-19
[http://www.easylinuxguide.com/index.php?name=PNphpBB2&file=viewtopic&t=735](http://www.easylinuxguide.com/index.php?name=PNphpBB2&file=viewtopic&t=735)

Scroll down for Descent 3.  That *may* help.

---

### Post by waverave on 2005-08-19
Sadly enough, renaming symlink ppics.hog to PPics.Hog doasn't work...probabaly it's only a part of the solution.

I'm new to linux, but as I understand ubuntu is version of debian, therefore, installing the binarys to /usr/local/sbin instead of /usr/local/bin might help..but the game reports the same problem.

Any other suggestions?!

Regards

---

### Post by Mishura on 2005-08-20
The only difference between /usr/local/bin and /usr/local/**sbin** is that sbin is for your root commands, while normal bin is user commands.  If you put an executable in sbin, then theres a good chance only Root can play it.

Not recommended.

I do have a copy of Decent3 Linux somewhere, I'll try it out and see whats up.. last time I played it was on Mepis, which ran a mix of Sarge and Sid (back when Sarge was testing).

---

### Post by Mishura on 2005-08-20
**_HOWTO: Install Descent 3 (The Loki Version, not the Windows version) for Ubuntu Linux_**

Requirements:

LokiGames Descent 3, Disc 1 and 2
LibGTK1.2 files installed (For Loki_Setup)
3D Hardware Acceleration (nVidia recommended)

Recommended:

Decent 3 Mercenaries Expansion Pack (Windows version will do)
Gamepad or Joystick

I just finished installing Descent 3.  It works, and its kinda easy.

1.  Mount Descent 3 Disc 1  (Assume:  /media/cdrom)
2.  Open up a terminal, and CD into your CD-Rom's path. [ # cd /media/cdrom ]
3.  Type:  sh ./setup.sh
4.  When the installer launches, tell it to install in your home directory (Assume:  /home/user/descent3)
5.  Tell Setup to install both the Base and Mission packs.  Takes up more space, but will make level loading *MUCH MUCH* quicker.
6.  Hit Install, and wait.  Get you a Coke or coffee or something.
7.  Once its installed, exit setup.
8.  Unmount Descent 3 CD 1
9.  Mount Descent 3 CD 2
10.  Go to your Descent3's install directory.
11.  Type this:  ln -s ppics.hog PPics.Hog  (Yes, its case-sensitive.)
12.  ./descent3  and have fun.

Notes:

1.   Have CD 2 mounted every time you play.  Some mission files are on CD 2, and who knows what.  Setup didn't ask for CD 2 during Install, which means something is on there, that the game will most likely need.

2.  Updating Decent3 will be a B***H.  Why?  Because the Loki_patch binary that's inside each patch file is compiled with a crappy version of GCC and glibc.  It is not compatible in any freakin way.  There is something called Loki_Patch-fix (Look at happypenguin.org for it) that can allow you to patch it.  Keep in mind that my copy already installed with 1.4 already patched, and the only other patches are 1.4a and 1.4b.  I have no idea what these do.  Also, last time I seen a Descent 3 online server, was nearly 3 years ago.. if that.  You probably won't need the patch.

Included is a screenshot of the install process, and a in-game screenshot.  (Not windowed, sorry, not sure how to do that.)

---

### Post by Mishura on 2005-08-20
[QUOTE=waverave]Sadly enough, renaming symlink ppics.hog to PPics.Hog doasn't work...probabaly it's only a part of the solution.
[/QUOTE]

If my Howto doesn't help (It really doesn't add much).. then can you post your console output?  What kind of error *exactly* are you getting?

---

### Post by waverave on 2005-08-25
[QUOTE=Mishura]If my Howto doesn't help (It really doesn't add much).. then can you post your console output?  What kind of error *exactly* are you getting?[/QUOTE]
 After a succefully installing Descent3, I get this:

> waverave@lahajeha:/home/user/waverave/Descent3$ sudo ln -s ppics.hog PPics.Hog
waverave@lahajeha:/home/user/waverave/Descent3$ ls
custom         demo         FAQ.txt   missions  online     README.mercenary
d3.hog         descent3     icon.bmp  movies    ppics.hog  uninstall
d3-linux.hog   extra13.hog  icon.xpm  netgames  PPics.Hog
Dedicated.cfg  extra.hog    imd.bmp   nettest   README
waverave@lahajeha:/home/user/waverave/Descent3$ ./descent3
Creating Loki preferences directory: /home/waverave/.loki/
Creating descent3 preferences directory: /home/waverave/.loki/descent3

Descent 3 Message(Error: Unable to find version key for Descent 3)

System Error


waverave@lahajeha:/home/user/waverave/Descent3$

...same problem, doasn't matter where I install the game or the binaries. I've seen you are running KDE, I have gnome environament, but that shouldn't matter...anyway I'm running Ubuntu 5.04 Intel x86 for that matter. I don't get it! Could it be the Radeon x600, but 3D acceleration works nicely?! (Neverball, Vegastrike work!)

TNX!

Regards

---

### Post by Mishura on 2005-08-26
> Descent 3 Message(Error: Unable to find version key for Descent 3)

I get that same message when I try to install Desent 3 Mercenary. (A Linux install copy, not Windows CD)  I can't install it, because it thinks that it's not installed.

Looking in my ~/.loki folder, I tried to find these "game keys".

Now if I do a "ls" in my ~/.loki/installed folder, I do get this:

```
mishura@mystra:~/.loki/installed$ ls -a
.              cxoffice.xml         glest.xml        Loki_Uninstall.xml  Savage.xml
..             enemy-territory.xml  hexen2.xml       Loki_Update.xml     tremulous.xml
bin            equake.xml           jedioutcast.xml  nexuiz.xml          warzone.2100.xml
coderedaa.xml  fakk2.xml            locale           nogravity.xml


```

There is no Descent 3 key, if *these* are the keys.  If I "cat" one of these files, lets say, fakk2.xml (Heavy Metall FAKK2), which is also a Loki Game, I get:

```
<?xml version="1.0"?>
<product name="fakk2" desc="Heavy Metal: FAKK2" xmlversion="1.6" root="/home/mishura/apps/fakk2" update_url="http://liflg.org/updates/fakk2/updates.txt">
  <component name="Default" version="1.02-english" default="yes">
    <option name="Base Install">
      <file md5="c56e0be8fbbc5996f579fbbb33bf16d1" mode="0644">README</file>
      <file md5="6c48095975c45958617ccd6d50830bea" mode="0755">libz.so.1.1.4</file>
      <file md5="818a3c67a8eac4ffc888e52fa2a8577f" mode="0644">fakk/pak4.pk3</file>
      <file md5="d3f7b94fabf21e6f566bab3bcea4939c" mode="0644">README.loki</file>
      <file md5="ab34de14ef033d32a61e971d5fd52f4b" mode="0644">fakk/pak3.pk3</file>
      <file md5="d473a969e581c2118313f3f5ab6e9729" mode="0644">fakk/pak2.pk3</file>
      <file md5="17d1f58558b9cb0ed92a148bfd3d5974" mode="0644">fakk/pak1.pk3</file>
      <file md5="2ddf304b65ed11fc41019d3050bb8728" mode="0644">fakk/pak0.pk3</file>
      <file md5="6becddb0f9678b116a4f14e6e8a1b702" mode="0644">fakk/default.cfg</file>
      <file md5="b5b641d0b4daa5e455d5c35775409908" mode="0644">fakk/autoexec.cfg</file>
      <file md5="02bfc8a84fa868bb51d3dfbe872a76e9" mode="0644">icon.xpm</file>
      <file md5="6c5ee9383349c42fc02d1e082e7fce80" mode="0755">fakk/fgame.so</file>
      <file md5="fba9097d9a14824c3dae909a1c697f6e" mode="0755">fakk/cgame.so</file>
      <file md5="1f4617856ac472ccd011ab19b7caee2e" mode="0755">fakk2</file>
      <symlink dest="/home/mishura/apps/fakk2//fakk2.sh" mode="0777">/home/mishura/bin/fakk2</symlink>
      <file md5="427fad0a52fb515012f31ec31adfa3dd" mode="0755">fakk2.sh</file>
      <directory mode="0755">fakk</directory>
      <directory mode="0755">/home/mishura/apps/fakk2</directory>
    </option>
  </component>
</product>

```

From what I can see, it just lists all the files installed, and their MD5 hashes, as well as installed directories.  Kind of reminiscent of a Windows Registry, is it not?

*thinks for a sec*

I will try something..  I'll create a fake key, following the same XML code as another loki game, excluding the MD5s.  **Maybe** I can fake it.  If so, then the "Key" thing will be resolved, I think.

---

### Post by Mishura on 2005-08-26
OK, I was right.  Ready to do some XML hacking?  Don't worry, its easy.

Load up your favorite Text Editor (Mines Kate.).

Copy this into your text editor:

```
<?xml version="1.0"?>
<product name="descent3" desc="Descent 3" xmlversion="1.6" root="/home/mishura/apps/descent3" update_url="localhost">
  <component name="Default" version="1.04" default="yes">
    <option name="Base Install">
      <file md5="c56e0be8fbbc5996f579fbbb33bf16d1" mode="0644">README</file>
      <file md5="6c48095975c45958617ccd6d50830bea" mode="0755">d3.hog</file>
      <file md5="818a3c67a8eac4ffc888e52fa2a8577f" mode="0644">d3-linux.hog</file>
      <file md5="d3f7b94fabf21e6f566bab3bcea4939c" mode="0644">README.loki</file>
      <file md5="ab34de14ef033d32a61e971d5fd52f4b" mode="0644">Dedicated.cfg</file>
      <file md5="d473a969e581c2118313f3f5ab6e9729" mode="0644">extra13.hog</file>
      <file md5="17d1f58558b9cb0ed92a148bfd3d5974" mode="0644">extra.hog</file>
      <file md5="2ddf304b65ed11fc41019d3050bb8728" mode="0644">PPics.Hog</file>
      <file md5="6becddb0f9678b116a4f14e6e8a1b702" mode="0755">descent3</file>
      <file md5="b5b641d0b4daa5e455d5c35775409908" mode="0755">descent3.dynamic</file>
      <file md5="02bfc8a84fa868bb51d3dfbe872a76e9" mode="0644">icon.xpm</file>
      <symlink dest="/home/mishura/apps/descent3" mode="0777">/home/mishura/bin/descent3</symlink>
      <file md5="427fad0a52fb515012f31ec31adfa3dd" mode="0755">descent3</file>
      <directory mode="0755">custom</directory>
      <directory mode="0755">demo</directory>
      <directory mode="0755">missions</directory>
      <directory mode="0755">movies</directory>
      <directory mode="0755">netgames</directory>
      <directory mode="0755">online</directory>
      <directory mode="0755">/home/mishura/apps/fakk2</directory>
    </option>
  </component>
</product>

```

Now were not finished yet.  If you look, you'll see that it has *my* stuff in there, like my install path, etc.  You need to replace every instance of "/home/mishura/apps/descent3" with your Descent 3 path.  You notice that not ALL files are listed.  It looks as if you don't need to.  

When you're done, save it as "descent3.xml" and place it in your ~/.loki/installed folder.  Case sensitive and all that...

Because of this, I was able to install the Mercenary expansion pack.  So my whole "NO KEY!!!" error is fixed.  This should help out a lot.. I hope.

---

### Post by waverave on 2005-08-26
Well...

1. Descent3 is the only Loki game I have... the .loki folder doasn't contain an installed folder, only

> root@lahajeha:/home/waverave/.loki # ls
descent3
[email]root@lahajeha:/home/waverave/.loki[/email] #

[email]root@lahajeha:/home/waverave/.loki[/email]/descent3 # ls
custom  descent3.xml  missions  netgames
[email]root@lahajeha:/home/waverave/.loki[/email]/descent3 #

2. You can see I've cp there the descent3.xml (modified) but its obviouslly in the wrong place, I think?! Another thing, I had to use the root terminal to get access to the .loki folder, this didn't work

> waverave@lahajeha:~$ cd .loki
bash: cd: .loki: Permission denied
waverave@lahajeha:~$ sudo cd .loki
sudo: cd: command not found
waverave@lahajeha:~$

I wonder what I could do...maybe inastall another Loki game in order to obrain the /.loki/installed folder.

I have another question...when you install ubuntu -  you are not root, you are a superuser, could this be a problem...must I change the line in descent3.xml file containing > root="/home/waverave/descent3" to something else?? (I'm not shure I asked corectlly.) Furthermore, could I create a root account? And thanks for the quick course in xml hacking!!

Best regards

---

### Post by Mishura on 2005-08-26
Hmm.. its definately a permissions problem.  Fortunately, that can be fixed real quick.

Go to your home directory.  Assuming your user name is "waverace", we do a: (AS ROOT OR SUDO)

```
cd /home/waverace
chown waverace:waverace * -R
```

Chown bascially means "Change ownership."  The first "waverace" is Owner, and the second is Group.  Ubuntu defaults the user group to be the same as owner.  Other Linux systems like Suse 9.x used "users" as its group, and shared it with other users.   Don't worry too much about this, just explaining it for others.

This will make sure everything in /home/waverace is owned by you, thus fixing ownership problems.

Now, In order to access directories, they must be **executable**.  Just to make sure .loki is executable, do this in your home directory as User:

EDIT:  I forgot to mention that folders should be readable and writable as well to users.  Change made.

```
chmod a+rwx .loki
```

Chmod = Change attributes.  The DOS equivalent would be "attrib" I believe.
a = all attributes such as owner, group, and.. other (i think).
r = readable
w = writable
x = executable

*Note:  A more common way of chmod'ing stuff is by using a numerical format like 0699 etc..  I'm not familiar with this, but its well preferred by accomplished Unix/Linux hackers.  We don't need to worry about that.

Now that .loki folder should be executable and owned by you, you should be able to get this working right.

```
cd ~/.loki
mkdir installed
```

This creates your /installed directory.  Now, go back to my previous post, do as I tell you and have that descent3.xml file in your ~/.loki/installed folder.  Everything *should* work  ( I know I keep saying this, just bear with me )  :grin: 

*Note:  I reread your post and saw that descent3.xml was located in ~/.loki/descent3 .  Take a look at it with a text editor, and see if the paths (Where it is installed) is correct.  If so, then just copy or symlink that file into ~/.loki/installed.

Also, with all permissions/ownership problems fixed with your /.loki folder, you'll now be able to access your save games and stuff when you do start playing.  If you started playing Descent 3, and ~/.loki was owned by root, you'd never be able to save your changes or games.  Believe me, I know!  ;)

Permissions/Ownership problems are the chief reason why most Linux newbies have problems, from what I can tell.  It's much different and more draconic than the Windows way of handling it.  Keep in mind that they are there for a reason:  To keep files that you own away from other users, and to prevent yourself from accidently doing something stupid.  (Like removing files that are needed..)  Unix, which Linux derives from, is by nature a mutli-user system, while Windows was predominately a Single-User system until recently.  Because of this, you have to think "differently" than you'd normally will.   Don't worry, it becomes clear in no time, and there is ample documentation out there to explain in detail.

( Believe me, I had similar problems, and frustrations years ago when I started using Linux when dealing with permissions.  We all go through this.  Its cool. )

---

### Post by waverave on 2005-08-27
> **Mishura]Hmm.. its definately a permissions problem.  Fortunately, that can be fixed real quick.

Go to your home directory.  Assuming your user name is "waverace", we do a: (AS ROOT OR SUDO)

```
cd /home/waverace
chown waverace:waverace * -R
```

Chown bascially means "Change ownership."  The first "waverace" is Owner, and the second is Group.  Ubuntu defaults the user group to be the same as owner.  Other Linux systems like Suse 9.x used "users" as its group, and shared it with other users.   Don't worry too much about this, just explaining it for others.

This will make sure everything in /home/waverace is owned by you, thus fixing ownership problems.

Now, In order to access directories, they must be **executable**.  Just to make sure .loki is executable, do this in your home directory as User:

EDIT:  I forgot to mention that folders should be readable and writable as well to users.  Change made.

```
chmod a+rwx .loki
```

Chmod = Change attributes.  The DOS equivalent would be "attrib" I believe.
a = all attributes such as owner, group, and.. other (i think).
r = readable
w = writable
x = executable

*Note:  A more common way of chmod'ing stuff is by using a numerical format like 0699 etc..  I'm not familiar with this, but its well preferred by accomplished Unix/Linux hackers.  We don't need to worry about that.

Now that .loki folder should be executable and owned by you, you should be able to get this working right.

```
cd ~/.loki
mkdir installed
```

This creates your /installed directory.  Now, go back to my previous post, do as I tell you and have that descent3.xml file in your ~/.loki/installed folder.  Everything *should* work  ( I know I keep saying this, just bear with me )  :grin: 

*Note:  I reread your post and saw that descent3.xml was located in ~/.loki/descent3 .  Take a look at it with a text editor, and see if the paths (Where it is installed) is correct.  If so, then just copy or symlink that file into ~/.loki/installed.

Also, with all permissions/ownership problems fixed with your /.loki folder, you'll now be able to access your save games and stuff when you do start playing.  If you started playing Descent 3, and ~/.loki was owned by root, you'd never be able to save your changes or games.  Believe me, I know!   said:**
> 
 OK, (now I own my own folder;)...I moved the descent3.xml to /.loki/installed ...had to change ownership once more, probabaly because of this line in the file

> <product name="descent3" desc="Descent 3" xmlversion="1.6" root="/home/waverave/descent3" update_url="localhost">

should I put user instead of root? And now, I get this msg

[QUOTE]waverave@lahajeha:/$ descent3

Descent 3 Message(Error: Couldn't find the string table.)

System Error

so what comes next...

Another thing, I noticed that I have a descent3 file in /usr/local/bin left from the numerous installations of the game, namely several times when installing the game got the mag

> can't find /bin/x86/descent3
can't find /bin/x86/nettest

and the files were lacated in /bin/x86/glib-2.1...so I aborted the install and retried...and suddenlly it was OK, that's an odd one, isn't it?!

(Kinda) Reply to linux vs. windows...the problems windows has with malware are due to it's singel-user design, and since it's a commecial platform there's money in malware. In my oppinion, if you wonna leard bout comps open source is the only way to go!

---

### Post by waverave on 2005-08-27
OK, (now I own my own folder;)...I've moved the descent3.xml file to the /.loki/installed folder...I had to change ownership once more, I suspect it's because of this line in the descent3.xml like

> <product name="descent3" desc="Descent 3" xmlversion="1.6" root="/home/waverave/descent3" update_url="localhost">

should I change root to user? But now... I get this msg

> waverave@lahajeha:/$ descent3

Descent 3 Message(Error: Couldn't find the string table.)

System Error

What's next?

An observation I made...I got a decsent3 file left in /usr/local/bin, it's form a previous installation, namely a few times got the msg

> can't find /bin/x86/descent3
can't find /bin/x86/nettest

and the files are in /bin/x86/glib-2.1...after several tries it installed properly, but that's odd, isn't it?! Yesterday I installed doom3 and works great...had to killall esd before playing, that's all.

(Kinda) Reply to linux vs. windows...the problems windows has with malware are probably due to it's designe as a singel-user platform, and since it's commercial there's money in malware;). In my oppinion, if you wonna learn about computers open source is the only way to go!

Best regards

---

### Post by Mishura on 2005-08-28
> **waverave]OK, (now I own my own folder said:**
> 

I believe that "root" here doesn't mean "user", but like "root directory of installation".  Kinda confusing.  Leave as is.

[QUOTE]


An observation I made...I got a decsent3 file left in /usr/local/bin, it's form a previous installation.. 

Kill that file.  You want to run the descent executable from /home/waverace/descent3.  If you want to put a symlink, so you don't have to do "/home/waverace/descent3/descent3", symlink it either in /usr/local/bin/ or /home/waverace/bin or /home/waverace/.local/bin.

Wow..  I'm starting to run out of ideas dude.  :o

The files /bin/x86/descent and /bin/x86/nettest;  aren't they part of the loki_setup program, found on the CD usually with a path like /setup.data/Linux/glibc-2.1/x86/ ?

If you may be missing any files, here is a list of my Descent 3 directory (With Mercenary installed):

```

mishura@mystra:~/apps/descent3$ ls -al
total 421756
drwxr-xr-x   8 mishura mishura       760 2005-08-26 00:00 .
drwxr-xr-x  36 mishura mishura       936 2005-08-26 23:43 ..
drwxr-xr-x   6 mishura mishura       144 2005-08-20 02:01 custom
-rw-r--r--   1 mishura mishura 194030423 2005-08-20 02:01 d3.hog
-rw-rw-r--   1 mishura mishura  11749905 2005-08-20 02:01 d3-linux.hog
-rw-r--r--   1 mishura mishura      3638 2005-08-25 23:58 d3merc.ico
-rw-r--r--   1 mishura mishura       290 2005-08-20 02:01 Dedicated.cfg
drwxr-xr-x   2 mishura mishura       104 2005-08-20 02:01 demo
-rwxr-xr-x   1 mishura mishura   3226500 2005-08-20 01:59 descent3
-rwxr-xr-x   1 mishura mishura   3226500 2005-08-20 01:59 descent3.dynamic
-rw-r--r--   1 mishura mishura    278329 2005-08-20 02:01 extra13.hog
-rw-r--r--   1 mishura mishura    476566 2005-08-20 02:01 extra.hog
-rw-r--r--   1 mishura mishura      7839 2005-08-20 01:59 FAQ.txt
-rw-r--r--   1 mishura mishura      6966 2005-08-20 01:59 icon.bmp
-rw-r--r--   1 mishura mishura      8930 2005-08-20 01:59 icon.xpm
-rw-r--r--   1 mishura mishura    201246 2005-08-20 02:01 imd.bmp
-rw-r--r--   1 mishura mishura 212406907 2005-08-26 00:00 merc.hog
drwxr-xr-x   2 mishura mishura       800 2005-08-26 00:01 missions
drwxr-xr-x   2 mishura mishura        96 2005-08-26 00:00 movies
drwxr-xr-x   2 mishura mishura       328 2005-08-20 02:01 netgames
-rwxr-xr-x   1 mishura mishura     41524 2005-08-20 01:59 nettest
drwxr-xr-x   2 mishura mishura       128 2005-08-20 02:01 online
-rw-r--r--   1 mishura mishura   5611278 2005-08-20 02:01 ppics.hog
lrwxrwxrwx   1 mishura mishura         9 2005-08-20 02:04 PPics.Hog -> ppics.hog
-rw-r--r--   1 mishura mishura      7172 2005-08-20 02:03 README
-rw-r--r--   1 mishura mishura      2990 2005-08-26 00:01 README.mercenary
-rwxr-xr-x   1 mishura mishura       660 2005-08-26 00:01 uninstall
-rw-r--r--   1 mishura mishura    135168 2005-08-26 00:00 unmerc.exe

```

Nettest and descent3 are in that folder.. hmm..  

We can try a few things, first make sure all files are removed from the previous install.  Second, we can do some patching.  Now, remember when I said patching will be a pain in the a**?   I wasn't joking.

LokiGames Mirror:
[ftp://ftp.planetmirror.com/pub/lokigames/updates/descent3](ftp://ftp.planetmirror.com/pub/lokigames/updates/descent3)

Download the Descent3 1.4.0b patch.

If you don't get an error when you run it, then you're patched, and you got lucky.  More than likely, since we're on the same Distro sans Desktop,  you'll need to "hack" it to work.

Download the fix!
[http://goldenfiles.sourceforge.net/index.php?page=lokipatchfix](http://goldenfiles.sourceforge.net/index.php?page=lokipatchfix)

Use this program to "launch" the binary patch.  It dynamically replaces the old loki_patch binary with a more newer compiled binary, so it can work with our more modern Glibc.

Once the game is patched, you should also get a new file:  descent3.dynamic.  This binary is compiled to dynamically link to libraries present on your system, instead of using the statically linked libraries that were included.  Try this and ./descent3 again.

P.S.:  Kill ESD for this one too.  I recommend finding a way to remove the need for ESD entirely, and if you don't believe me, parse some of the threads in the Gaming forum, with "sound" as a keyword.  It's an overwhelming problem with ESD and games, while playing in Gnome.  As a Kubuntu user, I've hadn't had problems with this, as ESD isn't included; so I'm spoiled ;) .    Try to use ALSA as much as possible.  (We need "ONE" sound manager for GNU/Linux, and This is it, IMHO.)

P.P.S.: If *THIS* doesn't work, then we'll probably need to do something drastic, like, I give you my configurations, and compare files, which is beyond this forum.  Just send me an email if it doesn't work and we'll play around with some ideas (my email is my username at gmail.com)  If it does work, then just post "SUCESS!!" here and have fun.

---

### Post by waverave on 2005-08-30
The files I mentioned above are part of the install process...sorry I wasn't clear enough. I found it weard that the install script didn't find them at once, I had to retry several times, but eventualy it installed properly. And I cleared the old files!

Well...I hadn't patched it yet, but I'm not shure it would help...after I arranged the descent3.xml file, I didn't restart the cpu...however, now at least I can watch the intro as many times I wont ;-). Now I'm getting this

> waverave@lahajeha:~$ descent3
gd error (glide): Can't find or access Banshee/V3 board
Failed to load library [libGL.so].

Descent 3 Message(Error: Failed to load library [libGL.so].
)

System Error


waverave@lahajeha:~$

...as I understand it libGL.so part of the openGL, which is a video driver (if I'm correct) and I got the xorg-driver-fglrx 3D acceleration driver. Could I install openGL, isn't it an older "version"?

Anyway, I would like to thank you for all your help...I learned a few things and that's the point anyway, isnt't it?!

BEST regards

---

### Post by jckeil on 2005-11-07
ok i got the program installed and when tryed to run it but the only thing that happend waS the opening vid played and then i got this

root@inaus:/home/jim # sh /media/cdrom/setup.sh
----====== Descent 3 installation program ======----

You are running a x86 machine with glibc-2.1
Hit Control-C anytime to cancel this installation program.

Would you like to read the README file ? [Y/n] n
Please enter the installation path [/usr/local/games/Descent3]
Please enter the path for binary installation [/usr/local/bin]
Install Base Install? [Y/n/?] y
Install Mission Data? [N/y] y
Do you want to install desktop items? [Y/n] y
Installing to /usr/local/games/Descent3
43993 MB available, 509 MB will be installed.

Continue install? [Y/n] y
Installing descent3 binary ...
 100% - /usr/local/games/Descent3/descent3
Installing nettest binary ...
 100% - /usr/local/games/Descent3/nettest
Installing Base Install ...
 100% - /usr/local/games/Descent3/README
 100% - /usr/local/games/Descent3/README.mercenary
 100% - /usr/local/games/Descent3/FAQ.txt
 100% - /usr/local/games/Descent3/icon.xpm
 100% - /usr/local/games/Descent3/icon.bmp
 100% - /usr/local/games/Descent3/d3.hog
 100% - /usr/local/games/Descent3/Dedicated.cfg
 100% - /usr/local/games/Descent3/demo/empty
 100% - /usr/local/games/Descent3/demo/Secret2.dem
 100% - /usr/local/games/Descent3/extra.hog
 100% - /usr/local/games/Descent3/extra13.hog
 100% - /usr/local/games/Descent3/imd.bmp
 100% - /usr/local/games/Descent3/missions/bedlam.mn3
 100% - /usr/local/games/Descent3/missions/dementia.mn3
 100% - /usr/local/games/Descent3/missions/frenzy.mn3
 100% - /usr/local/games/Descent3/missions/fury.mn3
 100% - /usr/local/games/Descent3/missions/training.mn3
 100% - /usr/local/games/Descent3/online/Direct TCP~IP.d3c
 100% - /usr/local/games/Descent3/online/Parallax Online.d3c
 100% - /usr/local/games/Descent3/ppics.hog
 100% - /usr/local/games/Descent3/d3-linux.hog
 100% - /usr/local/games/Descent3/netgames/Anarchy.d3m
 100% - /usr/local/games/Descent3/netgames/co-op.d3m
 100% - /usr/local/games/Descent3/netgames/ctf.d3m
 100% - /usr/local/games/Descent3/netgames/entropy.d3m
 100% - /usr/local/games/Descent3/netgames/hoard.d3m
 100% - /usr/local/games/Descent3/netgames/hyperanarchy.d3m
 100% - /usr/local/games/Descent3/netgames/monsterball.d3m
 100% - /usr/local/games/Descent3/netgames/robo-anarchy.d3m
 100% - /usr/local/games/Descent3/netgames/tanarchy.d3m
Installing Mission Data ...
 100% - /usr/local/games/Descent3/missions/d3.mn3
 100% - /usr/local/games/Descent3/missions/d3_2.mn3
 100% - /usr/local/games/Descent3/missions/d3voice1.hog
 100% - /usr/local/games/Descent3/missions/d3voice2.hog
 100% - /usr/local/games/Descent3/README

Installation complete.
Would you like launch the game now? [Y/n] y
If you run a game as root, the preferences will be stored in
root's home directory instead of your user account directory.
Continue? [N/y] y
root@inaus:/home/jim # Creating Loki preferences directory: /root/.loki/
Creating descent3 preferences directory: /root/.loki/descent3
Failed to load library [libGL.so].

Descent 3 Message(Error: Failed to load library [libGL.so].
)

System Error
 any ideas?

---

### Post by bobmatino17 on 2008-12-18
I tried running the shell script and 



link@family:~$ cd /media/cdrom0/
link@family:/media/cdrom0$ sh ./setup.sh
./setup.sh: 9: function: not found
x86
link@family:/media/cdrom0$ 


:confused::confused:

---

### Post by bobmatino17 on 2008-12-21
i cd'd to the cd and ran the shell script (used the full path)
and I got

link@family:~$ cd /media/cdrom0
link@family:/media/cdrom0$ sudo /bin/sh ./setup.sh
./setup.sh: 9: function: not found
x86
link@family:/media/cdrom0$

any help would be very greatly apreciated.

---

