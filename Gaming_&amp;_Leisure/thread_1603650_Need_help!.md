---
title: "Need help!"
date: 2010-10-23
forum: Gaming &amp; Leisure
---

### Post by kevinls on 2010-10-23
[FONT=monospace]Code:

glxinfo | grep direct

Output:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I've been trying to play Enemy Territory on my Ubuntu 9.04 but it's very slow which makes it impossible to play.  So I could use a little help to remedy the problem.  Please tell me what to do.  Thanks!

[/FONT]

---

### Post by Cresho on 2010-10-23
what graphics card do you have?  There is a minimum spec to run that game.  That line basically says you don't have direct rendering and no drivers installed.  go into system->administration->hardware drivers and install the video card driver there.

---

### Post by kevinls on 2010-10-23
The game works fine but now I have a different problem...

I followed the instructions from this page:  [http://adammichaelroach.com/blog/050409-wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904](http://adammichaelroach.com/blog/050409-wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904)

Scroll down and you'll find a section called "Updating Punkbuster." My problem occurred with the code:  sudo chmod +x pbweb.x86.

[Quote="text taken from (above) website"]**Updating Punkbuster**
 Finally, we can update Punkbuster.  This is a multi-step process, but  I assure you if you follow these instructions, it will work just fine.   In the terminal:
 
cd /usr/local/games/enemy-territory/pb/htm/
sudo wget [http://www.evenbalance.com/downloads/cod2/pbsecsv.htm](http://www.evenbalance.com/downloads/cod2/pbsecsv.htm)
cd ..
_**sudo chmod +x pbweb.x86**_
sudo ./pbweb.x86[/QUOTE]

After I pasted that line of text into a terminal it gave me this output:

[QUOTE="terminal"]chmod: cannot access `pbweb.x86': No such file or directory[/QUOTE]

So, what should I do?  Thanks!

---

### Post by sakuramboo on 2010-10-23
You could try finding where pbweb.x86 is located.

---

### Post by kevinls on 2010-10-23
I did something which updated punkbuster but now when I try playing the game I cannot enable punkbuster.  I'll click on the enable button but it won't enable!

I guess something else went wrong.

Please help!

---

### Post by kevinls on 2010-10-23
> desktop:~$ cp /usr/local/games/enemy-territory/pb/pbweb.x86 ~/.etwolf/pb
desktop:~$ cd ~/.etwolf/pb
desktop:~/.etwolf/pb$ ./pbweb.x86
PBWEB v2.2
This program is (C) Copyright 2002-2005 by Even Balance, Inc., All Rights Reserved.

pbweb must be launched from the home "pb" folder where the game is installed.
If launched from another location, pbweb will not be able to update PunkBuster.

If you experience a problem with this program, please visit our support center
at [http://www.evenbalance.com](http://www.evenbalance.com).

Starting pbweb to check for PunkBuster updates via world wide web
Initializing ... (please wait - ctrl+c to cancel)
Resolving [www.evenbalance.com]("http://www.evenbalance.com")
Resolved to 72.51.33.156
Checking for PB Client updates
Game: et
Attempting to download pbsec.htm (please wait)

**ERROR from Web Server: 302 Found

File already exists: htm/la001382.htm

ERROR: Htm-to-Binary Conversion Failed ... htm/la001382.htm Removed

Attempting to download htm/lc002236.htm (please wait)

**ERROR from Web Server: 302 Found
I've been trying to resolve this problem on my own but I have little idea as to what to do.

To be more precise:

When I tried to connect to a game server it blocked me because punkbuster (PB) wasn't enabled (for some reason, it became disabled AFTER I had successfully updated PB).  So I tried to enable it by clicking on the "enable punkbuster" button.  A window came up and I pressed yes (to enable PB), the window closed, but, and here's the problem, PB wasn't enabled because it still said "enable punkbuster" instead of saying "disable punkbuster" (which is what it's supposed to say when PB is on).

I can't play this game without having PB enabled.

---

### Post by kevinls on 2010-10-23
> ******Punkbuster update**
 If you cannot update punkbuster and you get kicked out every time, try the graphical user interface (GUI) application: 
[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php) 
You have to extract the .zip file, run pbsetup.run, "Add a Game" > Enemy territory. Then hit "Check for updates". 
 


How do I run pbsetup.run?  What do I type into a terminal?

---

### Post by kevinls on 2010-10-24
> download et-2.60.x86.run and install et
download et-260b.zip patch and apply the patch (if you havent already done this)
chmod u+x [et-install-dir]/pb/pbweb.x86
cd to [et-install-dir]/pb/
run pbweb.x86
copy pbweb.x86 to ~/.etwolf/pb/
cd to ~/.etwolf/pb/
run pbweb.x86

I don't know how to follow those instructions.  Can someone please help me, step by step...

---

### Post by kevinls on 2010-10-24
[QUOTE="sakuramboo"]You could try finding where pbweb.x86 is located.[/QUOTE]

How do I do this?

---

### Post by kevinls on 2010-10-24
I followed these instructions:

> Alternative PB updating
1. Open console and type: wget [http://websec.evenbalance.com/downloads/...bsetup.run]("http://websec.evenbalance.com/downloads/linux/pbsetup.run")
2. After loaded, type: sudo chmod a+x pbsetup.run && ./pbsetup.run
-> If the program wont execute, U are probably missing an important
thingie. MOVE TO NEXT STEP, IF IT DID EXECUTE!
2.1) type (in console): sudo apt-get install upx-ucl
2.2) After loaded and installed, type: sudo upx -d pbsetup.run && ./pbsetup.run
3. Accept all licenses
4. Press "Add game" and choose ET.
5. Press "Check for updates"
6. You should be now able to play on PB servers. Also, try pb_security 0 for just in case!


And I got this:

> desktop:~$ wget [http://websec.evenbalance.com/downloads/...bsetup.run](http://websec.evenbalance.com/downloads/...bsetup.run)
--2010-10-24 01:22:35--  [http://websec.evenbalance.com/downloads/...bsetup.run](http://websec.evenbalance.com/downloads/...bsetup.run)
Resolving websec.evenbalance.com... 12.47.44.79, 74.208.184.102
Connecting to websec.evenbalance.com|12.47.44.79|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php) [following]
--2010-10-24 01:22:36--  [http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)
Resolving [www.evenbalance.com](www.evenbalance.com)... 72.51.33.156, 64.251.14.78
Connecting to [www.evenbalance.com|72.51.33.156|:80](www.evenbalance.com|72.51.33.156|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7794 (7.6K) [text/html]
Saving to: `...bsetup.run'

100%[======================================>] 7,794       --.-K/s   in 0.1s    

2010-10-24 01:22:36 (77.3 KB/s) - `...bsetup.run' saved [7794/7794]

desktop:~$ sudo chmod a+x pbsetup.run && ./pbsetup.run

(pbsetup.run:17385): Gtk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gtk/gtkwidget.c:9103: widget class `GtkPizza' has no property named `row-ending-details'
rpl@rpl-desktop:~$ sudo apt-get install upx-ucl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libucl1
The following NEW packages will be installed:
  libucl1 upx-ucl
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 406kB of archives.
After this operation, 1520kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main libucl1 1.03-3 [27.3kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main upx-ucl 3.01-3 [378kB]
Fetched 406kB in 1s (262kB/s)   
Selecting previously deselected package libucl1.
(Reading database ... 109603 files and directories currently installed.)
Unpacking libucl1 (from .../libucl1_1.03-3_i386.deb) ...
Selecting previously deselected package upx-ucl.
Unpacking upx-ucl (from .../upx-ucl_3.01-3_i386.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up libucl1 (1.03-3) ...

Setting up upx-ucl (3.01-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
rpl@rpl-desktop:~$ sudo upx -d pbsetup.run && ./pbsetup.run
                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.01        Markus Oberhumer, Laszlo Molnar & John Reiser   Jul 31st 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
   3457316 <-   1177444   34.06%  linux/elf386   pbsetup.run

Unpacked 1 file.

(pbsetup.run:17476): Gtk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gtk/gtkwidget.c:9103: widget class `GtkPizza' has no property named `row-ending-details'
desktop:~$ 


...

---

