---
title: "Postal fudge pack/10th anniversary dvd issue"
date: 2009-12-11
forum: Gaming &amp; Leisure
---

### Post by singerie on 2009-12-11
Hello everyone,

I have some issue while installing postal 10th anniversary.

I launch the linux-installer, no issue.

after selecting all the game i want to install and pressing install, the installer ask me to mount the dvd.

I got this issue with 2 different computer, running ubuntu 9.10 32 bit.


Any idea ?


Thanks.

---

### Post by singerie on 2009-12-11
just got an email from the postal team :

this will probably work, from the Terminal:

  SETUP_CDROM=/media/cdrom0 /media/cdrom0/linux_installer.sh

("/media/cdrom0" is probably correct, but it should be wherever Ubuntu mounted the disc.)

Ubuntu used to report the disc's filesystem as "iso9660", but now DVD-ROMs (correctly) report themselves as "udf" and it confuses the installer, so that command line just forces it to look in the right place.

=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

I didn't tested it yet, I will let everyone know tonight...

---

### Post by singerie on 2009-12-12
it worked fine :D

---

### Post by PatheticMoFo on 2009-12-15
Wow thanks for that! I just bought this and was really hoping I didn't just get screwed! Setting that variable before the command worked perfectly.

---

### Post by Quarn on 2011-01-22
On the new Ubuntu 10.10 the disk is already reported as UDF, but when running the installer I get:

Verifying archive integrity... All good.
Uncompressing Postal 10th Anniversary for x86 GNU/Linux...................................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'

Any idea someone

---

### Post by dieklaue on 2011-02-02
> **Quarn said:**
> On the new Ubuntu 10.10 the disk is already reported as UDF, but when running the installer I get:

Verifying archive integrity... All good.
Uncompressing Postal 10th Anniversary for x86 GNU/Linux...................................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'

Any idea someone

I managed to get it installing, running it still however causes problems (no sound in Postal 1 / Postal 2 AW,, the "normal" Postal 2 exits with "Exiting due to error"). However, here's what to do:

```

# 1. Copy linux_installer.sh from the DVD to some location where you have write access, e.g. I did:

$ cp linux_installer.sh $HOME/

# 2. Open linux_installer.sh in an editor, and in line 13, change "keep=n" to "keep=y"

# 3. Run linux_installer.sh normally

# 4. Go to /tmp/postal_fudge_pack_installer

# 5. Open "setup.sh" in an editor, and in linux 267, change "try_run setup.gtk2 $args $*" to "try_run setup.gtk $args $*"

```

This runs the GTK1.2 installer instead of the GTK2 installer, which doesn't seem to have the problem. I can only guess why the GTK2 installer doesn't work (anymore?), probably because some XML library changed its behaviour?

Hope that helps.

---

### Post by kDDs on 2011-02-02
I have the problem above, but I can't do step 2. I get an error in gedit about the character encoding?

I'm using the Fudge Pack edition, not that I'd think it would make much difference.

---

### Post by dieklaue on 2011-02-02
> **kDDs said:**
> I have the problem above, but I can't do step 2. I get an error in gedit about the character encoding?

I'm using the Fudge Pack edition, not that I'd think it would make much difference.

It's probably a gedit problem. The file contains binary data, maybe gedit gets confused. I edited it with vim.

---

### Post by dieklaue on 2011-02-02
For the "Exiting due to error" problem, see [https://bugzilla.icculus.org/show_bug.cgi?id=2955](https://bugzilla.icculus.org/show_bug.cgi?id=2955). For the "no sound" problem, it's because someone  decided to drop OSS emulation in Ubuntu 10.0 :-(. I think I'm going back to Debian, no time for such ignorance :-(.

---

### Post by kDDs on 2011-02-02
Ok, changed the keep in vim, but I still get the same error...

---

### Post by dieklaue on 2011-02-02
I don't know which error you get, and when you get it. maybe you should just post it :)

---

### Post by kDDs on 2011-02-02
I get the 

> Uncompressing Postal 10th Anniversary for x86 GNU/Linux............................................. ......................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'

error still, even when changing the keep=n to keep=y.

---

### Post by dieklaue on 2011-02-02
Continue with step 4, the error is normal. Maybe I should have mentioned that ;)

---

### Post by kDDs on 2011-02-02
Ahah, thank you very much, the installer is running now :D

---

### Post by SnaveZ on 2011-02-07
even after editing linux_installer.sh and setup.sh I still get the XML error and no installer launches..

EDIT:

Nevermind I got it lol

I just did sudo gedit Setup.sh and changed the line that way.  Before I was just opening it with an editor, changing the line, saving and quitting.  But it wasn't storing the edit I made because I didn't sudo.

SnaveZ

---

### Post by Quarn on 2011-02-14
I haven't been there in the last 3 weeks, so I didn't try it yet, 
but thanks a lot [COLOR=black]Dieklaue for the precious information. I will try it [/COLOR]tonight.
):P

---

### Post by ELD on 2011-02-14
If you have problems with no sounds you can always try running it using padsp in the terminal, works for me with LGP's shadowgrounds.

---

### Post by cor2y on 2011-05-17
Sorry to resurrect this thread but i am using the 10th anniversay dvd and i tried editing the linux_installer.sh and got this error 
> Uncompressing Postal 10th Anniversary for x86 GNU/Linux............................................. ......................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml' 

and there was no folder created in the /tmp directory

Also 64bit ubuntu 11.04 with the ia32 libraries installed.

---

### Post by pig0826usanj on 2011-06-09
For those that don't have the folder in the tmp, just copy every thing from the iso to a folder on the desktop, do the steps, then you'll find the folder.

---

### Post by BearIsGood on 2011-06-11
Ok this is how [SIZE=4][COLOR=Red]_**I INSTALED**_[/COLOR][/SIZE]
This is How to instal Postal 2 Fudge Pack:

[LIST=1]
[*]Open up terminal Ctr+Alt+T
[*]Type in sudo su
[*]Type your password and hit enter (password is invisible)
[*]Next type mkdir /media/cdrom0
[*]Now you need to have program called Gmount-iso, you can finde that prgogram in ubuntu software center
[*]Mount your iso to your /media/cdrom0 with some software(Gmount-iso)
[*]Open up setup.sh you can download folder with setup.sh form here [URL="http://www.multiupload.com/13H1WB4V0M"]http://www.multiupload.com/13H1WB4V0M
[/URL]
[*]Open that file
[*]You will need 7zip (you can finde it in ubuntu software center)
[*]Copy folder inside to /tmp (extract), you need to copy it to that specific location or it will not work
[*]Open new extracted folder and run setup.sh
[*]Folow instalation guide and that is all.
[*]The game is installed to /home/Your Profile Name/postal or something like that
[*]Now we need to find out how to run this  game.
[/LIST]
Now if you have any other Postal 2 linux release you will need to get your own setup.sh:

----------------------------------------------------OPTIONAL--------------------------------------------------------
This is the alternative way to get setup.sh, it is described up  here in quote from this thread:
This is my version of quote:

[LIST=1]
[*]Copy linux_installer.sh from the DVD to some location where you have write access (desktop or /)
[*]Download program called Vim (or GVim) (or any other TextEditor) from ubuntu software center
[*]Open that linux_installer.sh in that editor, and in line 13, change "keep=n" to "keep=y"
[*]Run that modified linux_installer.sh normally
[*]Go to /tmp/postal_fudge_pack_installer
[*]Open "setup.sh" in that editor, and in line 267, change "try_run setup.gtk2 $args $*" to "try_run setup.gtk $args $*" <-do not insert quote makrks(")
[/LIST]
And here is original quote:
> # 1. Copy linux_installer.sh from the DVD to some location where you have write access, e.g. I did:

$ cp linux_installer.sh $HOME/

# 2. Open linux_installer.sh in an editor, and in line 13, change "keep=n" to "keep=y"

# 3. Run linux_installer.sh normally

# 4. Go to /tmp/postal_fudge_pack_installer

# 5. Open "setup.sh" in an editor, and in linux 267, change "try_run setup.gtk2 $args $*" to "try_run setup.gtk $args $*"EDIT:
I know how to run but game is runing crapy!!
-------------------------------------------------------QUESTION----------------------------------------------------------------
If some1 know how to run this games plz say

---

### Post by ssvt on 2011-07-16
quote:

[LIST=1]
[*]Copy linux_installer.sh from the DVD to some location where you have write access (desktop or /)
[*]Download program called Vim (or GVim) (or any other TextEditor) from ubuntu software center
[*]Open that linux_installer.sh in that editor, and in line 13, change "keep=n" to "keep=y"
[*]Run that modified linux_installer.sh normally
[*]Go to /tmp/postal_fudge_pack_installer
[*]Open "setup.sh" in that editor, and in line 267, change "try_run setup.gtk2 $args $*" to "try_run setup.gtk $args $*" <-do not insert quote makrks(")
[/LIST]


Ok, I did all of these steps, but when I choose what games to install it can't seem to find my DVD. I did this: SETUP_CDROM=/media/Disc /media/Disc/linux_installer.sh  (I'm running MInt 10) which started the install but the game still does not see my DVD as mounted. Any suggestions?

If I make the contents of my DVD into a ISO, can I use my modified installer as part of the ISO? and won't the installer still look for the mounted DVD?

---

### Post by BearIsGood on 2011-07-27
> **ssvt said:**
> quote:

[LIST=1]
[*]Copy linux_installer.sh from the DVD to some location where you have write access (desktop or /)
[*]Download program called Vim (or GVim) (or any other TextEditor) from ubuntu software center
[*]Open that linux_installer.sh in that editor, and in line 13, change "keep=n" to "keep=y"
[*]Run that modified linux_installer.sh normally
[*]Go to /tmp/postal_fudge_pack_installer
[*]Open "setup.sh" in that editor, and in line 267, change "try_run setup.gtk2 $args $*" to "try_run setup.gtk $args $*" <-do not insert quote makrks(")
[/LIST]


Ok, I did all of these steps, but when I choose what games to install it can't seem to find my DVD. I did this: SETUP_CDROM=/media/Disc /media/Disc/linux_installer.sh  (I'm running MInt 10) which started the install but the game still does not see my DVD as mounted. Any suggestions?

If I make the contents of my DVD into a ISO, can I use my modified installer as part of the ISO? and won't the installer still look for the mounted DVD?

You did not read whole post well.
Read again.
You quoted only OPTIONAL guide to get setup.sh 
You can also download premodifed setup.sh, from linked above.
Mint is not same as ubuntu but it will not be hard to adapt guide.

> 
SETUP_CDROM=/media/Disc /media/Disc/linux_installer.sh  (I'm running  MInt 10) which started the install but the game still does not see my  DVD as mounted. Any suggestions?
I used /media/cdrom0 in ubuntu , so its difrent in mint?

> 
If I make the contents of my DVD into a ISO, can I use my modified  installer as part of the ISO? and won't the installer still look for the  mounted DVD?[/QUOTE]
You can modify iso the way you want, just don't change label.
That is also not needed if you download premodified setup.sh.


Also if you can, it is recomanded that you burn your iso to DVD dual layer, blue ray or whatever.
[COLOR=Red]If you have DVD, then you dont need this tutorial.[/COLOR]
If you still have problems then you might have 2 cd readers or some virtual cd.
make sure that cd is in cdrom0

---

### Post by fdm on 2011-09-17
I finally got this running! Installed using the fixed installer from previous post. Then I copied the missing Default.ini and DefUser.ini to ~/postal_fudge_pack/postal2game/System as in the bug report:

[https://bugzilla.icculus.org/show_bug.cgi?id=2955](https://bugzilla.icculus.org/show_bug.cgi?id=2955)
[http://www.multiupload.com/3HERT3AG6V](http://www.multiupload.com/3HERT3AG6V) (mirror)

Then I ran:
```
sudo ln -sf /lib/libgcc_s.so.1 ~/postal_fudge_pack/postal2game/System/libgcc_s.so.1
```
to fix a library issue.

Finally I launched with padsp for OSS emulation.
```
padsp sh ~/postal2
```

---

### Post by Shadyboy on 2012-02-18
okey, so now I have been all over the internet looking an solution. So I have followed the step, but right now I think I have come over something that I haven`t found a solution for.

This is my terminal when I do a try at extraction from linux_installer.sh

> darkbringer@TheDarkRealm:~/fudgepack$ sudo ./linux_installer.sh /home/darkbringer/postal2/
Copying to a temporary location...
Creating directory postal_fudge_pack_installer
Verifying archive integrity... All good.
Uncompressing The Postal Fudge Pack for x86 GNU/Linux...Extraction failed.

The "/home/darkbringer/postal2" was on my last try, and it was then I got the error.

I am running Ubuntu 10.10 64 bit system ( might that has something to do with it? And if yes, what and how can I fix it with? )

---

### Post by williammartindale on 2012-04-06
I purchesed the Postal X dvd. I moved the file and edited it but when I run linux_installer.sh I get this

```
rex@N55SF: ./linux_installer.sh
Creating directory postal-10th-linux-x86
Verifying archive integrity... All good.
Uncompressing Postal 10th Anniversary for x86 GNU/Linuxgzip: stdin is encrypted -- not supported
.Extraction failed.
.Terminated
```I cant get past this part please help...

BTW im on 11.10

---

### Post by williammartindale on 2012-04-09
Ive tried everything I can think of but to no avail. The link is not working to get the alternate setup.sh  if someone could please upload it or something it would be greatly appreciated.

---

