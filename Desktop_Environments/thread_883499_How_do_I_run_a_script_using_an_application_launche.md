---
title: "How do I run a script using an application launcher/main menu entry?"
date: 2008-08-08
forum: Desktop Environments
---

### Post by Chuckaluphagus on 2008-08-08
I have found a very useful program for translators ([Swordfish]("http://www.maxprograms.com/products/swordfish.html")) that launches via a shell script ("swordfish.sh" - I've added the contents of the script at the end).  

I can run the script fine from the command line, or by double-clicking on it in Nautilus, but I'd like to add it to the Applications Menu.  I've created an entry using the menu editor that runs the command "/home/charles/Swordfish/swordfish.sh", but when I click on the entry to launch the program nothing happens. 

Could anyone tell me why how to get this to work?

(I'm sorry if this has already been solved before, but I can't find it by searching either here or in a general Google query; I get the feeling I'm just not searching with the right terms, though.)

swordfish.sh:
[INDENT]#!/bin/sh
export CP="lib/dtd.jar:lib/mysql-connector-java-3.1.8-bin.jar:lib/ojdbc14.jar:lib/hsqldb.jar:lib/resolver.jar:lib/swordfish.jar:lib/xercesImpl.jar:lib/xml-apis.jar:lib/GTK/swt.jar"
java -Xmx999M -cp $CP com.maxprograms.swordfish.Swordfish $1 2>>logs/swdfish_error.log[/INDENT]

---

### Post by p_quarles on 2008-08-08
Two things spring to mind: 

1) You might just need to "release" the shell that runs the command so that it doesn't immediately shut off. In this case, the command should be:
```
/home/charles/Swordfish.sh &
```
2) If this application needs to run in a terminal, you will need to use one to launch it:
```
xterm -e /home/charles/Swordfish.sh
```
Gnome-terminal has a similar option, but I do not remember what it is.

---

### Post by mlissner on 2009-04-16
Hmmm...I have a very similar problem trying to get a basic script to launch from the application menu. It works from a desktop launcher, and as a program, but not from the menu itself. Confusing!

---

### Post by fermulator on 2009-05-08
I've found that using
```
gnome-terminal --command="/home/username/scripts/foo_script.sh"
```

works well.

---

### Post by mlissner on 2009-05-08
Yeah, still no dice. Parts of the script I'm running work, but other parts fail (notes below):```
% more bin/Altova.sh 
#!/bin/bash
# A stupid script to clean up altova. 
# Date: 4-16-09

/bin/mv /home/mlissner/.altova /home/mlissner/Altova #This command doesn't happen

env WINEPREFIX="/home/mlissner/.wine"  #this one seems to, I think

wine "C:\Program Files\Altova\XMLSpy2008\XMLSpy.exe" # this command happens.

/bin/mv /home/mlissner/Altova /home/mlissner/.altova # hard to tell if this one works...
```

Seems like it ought to work, but it fails for some reason I can't figure out. It works fine in a terminal...

---

### Post by fermulator on 2009-05-16
> **mlissner said:**
> Yeah, still no dice. Parts of the script I'm running work, but other parts fail (notes below):```
% more bin/Altova.sh 
#!/bin/bash
# A stupid script to clean up altova. 
# Date: 4-16-09

/bin/mv /home/mlissner/.altova /home/mlissner/Altova #This command doesn't happen

env WINEPREFIX="/home/mlissner/.wine"  #this one seems to, I think

wine "C:\Program Files\Altova\XMLSpy2008\XMLSpy.exe" # this command happens.

/bin/mv /home/mlissner/Altova /home/mlissner/.altova # hard to tell if this one works...
```

Seems like it ought to work, but it fails for some reason I can't figure out. It works fine in a terminal...

What if you try putting the "&" character at the end of the command lines.  I've heard that running a script from the gnome applet might be 'blocked' by X server somehow .. so if you don't put your script(s) into the background, it won't execute properly.

I can't really confirm this 100%, but sometimes it has made my script(s) work by putting them into the background.

---

### Post by mlissner on 2009-05-16
Well, I added & to the end of every line in the script. No luck. We're missing something here.

---

### Post by kamni on 2009-05-17
I just had a similar problem trying to make an application launcher for a script that I had located in in /home/<my-username>/bin.  The script would run from the command line, or if I double-clicked the file in Nautilus.  However, the application wouldn't run from the launcher.  Here's how I fixed the problem:

First, check to make sure that the file is set to the correct permissions.  Mine was, but sometimes that can cause a problem.

```
chmod 755 <path-to-script>/myscript
```

For me, I figured out that the problem was only happening to scripts owned by me.  When I moved the script to /usr/bin with permissions root:root, the launcher stopped complaining or not working at all.  

```
sudo cp <path-to-script>/myscript /usr/bin
```

Then I set up my launcher as follows:
```
Type: Application
Name: MyScript
Command: xterm -e "myscript && read"
```

The "read" keeps xterm from closing immediately.  For some reason the same setup with gnome-terminal --command="...." doesn't work.  Hope this helps you!

---

### Post by mlissner on 2009-05-23
Nope, still no luck. The script currently says:```
% more /usr/bin/Altova.sh 
 #!/bin/bash
 # A stupid script to clean up altova. See the frostwire script for the inspiration
 # Date: 4-16-09
 
 /bin/mv /home/mlissner/.altova /home/mlissner/Altova 
 
 env WINEPREFIX="/home/mlissner/.wine" 
 
 wine "C:\Program Files\Altova\XMLSpy2008\XMLSpy.exe" 
 
 /bin/mv /home/mlissner/Altova /home/mlissner/.altova 
 
```
 
 It's located in /usr/bin/Altova.sh. It's owned by root, and has execute permissions. When it is run, the first line doesn't work. The second does, the third does, and the fourth does not.
 
 Baffled.

---

### Post by fermulator on 2009-05-27
> **kamni said:**
> I just had a similar problem trying to make an application launcher for a script that I had located in in /home/<my-username>/bin.  The script would run from the command line, or if I double-clicked the file in Nautilus.  However, the application wouldn't run from the launcher.  Here's how I fixed the problem:

First, check to make sure that the file is set to the correct permissions.  Mine was, but sometimes that can cause a problem.

```
chmod 755 <path-to-script>/myscript
```

For me, I figured out that the problem was only happening to scripts owned by me.  When I moved the script to /usr/bin with permissions root:root, the launcher stopped complaining or not working at all.  

```
sudo cp <path-to-script>/myscript /usr/bin
```

Then I set up my launcher as follows:
```
Type: Application
Name: MyScript
Command: xterm -e "myscript && read"
```

The "read" keeps xterm from closing immediately.  For some reason the same setup with gnome-terminal --command="...." doesn't work.  Hope this helps you!

This worked for me!

---

### Post by sh_roohani on 2010-02-21
Hi,

I had a similar problem with [MMC]("http://www.miksoft.net/products/mmc-lin.tar.gz"). There is a MobileMediaConverter shell script within the package:

```

#!/bin/bash
export LD_LIBRARY_PATH=./lib
./lib/mmc "$@"

```

which runs fine from a terminal, but does nothing from a menu item. I noticed that the menu item does not set the working directory of the script properly. So, I changed it like this:

```

#!/bin/bash
MMC_DIR=`dirname $0`
export LD_LIBRARY_PATH=$MMC_DIR/lib
$MMC_DIR/lib/mmc "$@"

```

and then the menu item also worked fine.

I know this topic is rather old. Just thought it might help someone.

---

### Post by Ve5ahchoo8ah on 2010-11-01
I have the same problem with Phun and Tor!
if I click on the file it works! desktop luncher works! a link in a different directory works! but when I add it to menu it doesn't do anything!!

---

