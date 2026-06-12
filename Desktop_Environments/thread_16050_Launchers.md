---
title: "Launchers"
date: 2005-02-18
forum: Desktop Environments
---

### Post by animalstyle on 2005-02-18
okay i know this sounds real easy, but its just one of those things that i wouldnt know where to look, but is actually probably really simple.  

to run limewire i type,

~/LimeWire/sh runLime.sh

It works fine if i type it in from the command line, but i want to be able to just click n launch.  So what i want to do is to be able to put this in the applications menu as a launcher.  I click applications, click internet menu, right click, add new item to menu.  Then under command I type in the command I stated above.  It gives me the error:  "Details: Failed to execute child process "~/LimeWire/sh" (No Such file or directory)"  Now I see that im doing something totally wrong here, because it thinks that sh is a directory.  So what should i do to make it a "command"?  I tried turning it into a script, "limewirerun"  That had the lines:

!#/bin/sh
cd ~/LimeWire
sh runLime.sh

Again, it worked when i typed ~/limewirerun on the command line, but not as a launcher.

Any Help out there?

---

### Post by kassetra on 2005-02-18
Ok, first of all, are you using gnome/nautilus?
 
 if you're using gnome/nautilus, right clicking in the menu usually makes a new directory, not a launcher...  so try it this way:
 
 1. Open Nautilus
 2. In the location bar, type:
  ```
applications:///
``` 
 and press enter.
 3. Double click on "Internet" to open that application menu.
 4. Right click in the window and then left click on "Create Launcher"
 5. Fill in the information and give it an icon.
 6. Try it now?

---

### Post by WW on 2005-02-18
Try using the full path instead of ~. For example, if your user name is username and your home directory is in /home, you would use /home/username/Limewire/sh instead of ~/Limewire/sh.

---

### Post by animalstyle on 2005-02-18
I can get the launchers working okay, there isnt a problem with that.  I tried typing in the whole directory, still no dice.  I think my question was a little confusing.  Basically how do i get the command "sh runLime.sh" into a launcher is my question?  Im not sure if im using the correct terminology, but i think im trying to run a "shell script"? maybe? i dont know what it means when you type "sh" before typing the file name, but it runs the program.

---

### Post by TravisNewman on 2005-02-18
are you sure you aren't running "sh ~/Limewire/runLime.sh" to get it running? I haven't used Limewire in ages, but I DO get commands mixed up a lot.

---

### Post by WW on 2005-02-18
OK, I think I see the problem.  Enter this as the Command in the launcher:```
sh /home/username/Limewire/runLime.sh
``` (but replace "username" with your user name).

Also, try it both without and with "Run in terminal" checked.

---

### Post by animalstyle on 2005-02-18
okay, so i tried sh ~/LimeWire/runLime.sh on the command line.  It says 

"unable to access jarfile LimeWire.jar
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?"

But when i go to the LimeWire directory (still on the command line), and type "sh runLime.sh" it runs just fine.  I feel like im missing something here.....

EDIT

okay, now i tried typing in the whole directory

sh /home/pzensius/LimeWire/runLime.sh 

on the command line.  It did work here.  But still, when i put it in the launcher, with or without "run in a terminal" it does nothing.  No error message nothing.

---

### Post by kassetra on 2005-02-18
does just typing "LimeWire" on the command line start it?
  If it does, use that as your command for the launcher.
 
 here's some info on installing limewire & launcher:
 [http://ubuntuguide.org/#limewire]("http://ubuntuguide.org/#limewire")

---

### Post by macewan on 2005-02-18
[QUOTE=kassetra]does just typing "LimeWire" on the command line start it?
  If it does, use that as your command for the launcher.
 
 here's some info on installing limewire & launcher:
 [http://ubuntuguide.org/#limewire]("http://ubuntuguide.org/#limewire")[/QUOTE]
 /opt/LimeWire/LimeWire


I right clicken my Internet section of the menu and added the above - works fine

---

### Post by animalstyle on 2005-02-19
Okay I installed it using the guide kassetra gave....It still works fine from the command  line, hangs when its from the launcher.  However I get some error messages when i start it from the command line that might help solve this problem.  (im a newbie so bear with me).  Could anyone tell me something from this?--

pzensius@animalstyle:/opt/LimeWire $ ./LimeWire
java.io.FileNotFoundException: out.txt (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:70)
        at com.zerog.lax.LAX.setStdOutStdErr(Unknown Source)
        at com.zerog.lax.LAX.setStdOutStdErrOnSupportedPlatforms(Unknown Source)        at com.zerog.lax.LAX.<init>(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)
java.io.FileNotFoundException: err.txt (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:70)
        at com.zerog.lax.LAX.setStdOutStdErr(Unknown Source)
        at com.zerog.lax.LAX.setStdOutStdErrOnSupportedPlatforms(Unknown Source)        at com.zerog.lax.LAX.<init>(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)
/usr/share/themes/Human/gtk-2.0/gtkrc:42: Engine "industrial" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:50: Engine "industrial" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:115: Engine "industrial" is unsupported, ignoring

So it starts up, everything works fine when done from the command line.  But im thinking maybe some of this has to do with the reason why it wont launch from the launcher.  Any ideas?

---

### Post by kassetra on 2005-02-19
animalstyle: that error message is java 1.4.2 trying to find a "gtk-swing theme" that matches the industrial theme you're using... gtkswing doesn't support industrial, it only supports three themes, one of them is bluecurve (if I remember)... so that's what some of that error is... some of it looks like permissions issues with parts of java... I'll look into it further in a second here...
  
 ahh ok, those errors are caused by permissions issues in /opt/LimeWire ... so it looks like you need to change some of the .txt files to permissions of 666 or so.
    
 as to why your launcher won't work... can you check the permissions on your /home/username/.limewire file/directory? If the permissions of that file or directory are incorrect, you wouldn't be able to load limewire from a launcher...

---

### Post by animalstyle on 2005-02-19
Here are the permissions in /home/pzensius/.limewire :

-rw-r--r--    1 pzensius pzensius       82 2005-02-18 18:38 Cookies.dat
-rw-r--r--    1 pzensius pzensius   110710 2005-02-18 20:55 createtimes.cache
-rw-r--r--    1 pzensius pzensius   271471 2005-02-18 18:38 fileurns.bak
-rw-r--r--    1 pzensius pzensius   271471 2005-02-18 20:55 fileurns.cache
-rw-r--r--    1 pzensius pzensius       84 2005-02-18 21:05 filters.props
-rw-r--r--    1 pzensius pzensius    18619 2005-02-18 18:38 gnutella.net
-rw-r--r--    1 pzensius pzensius      172 2005-02-18 21:05 installation.props
-rw-r--r--    1 pzensius pzensius      107 2005-02-18 18:02 licenses.cache
-rw-r--r--    1 pzensius pzensius      641 2005-02-18 21:05 limewire.props
drwxr-xr-x    2 pzensius pzensius     4096 2005-02-18 16:28 META-INF
-rw-r--r--    1 pzensius pzensius     1030 2005-02-18 16:28 public.key
-rw-r--r--    1 pzensius pzensius      214 2005-02-18 16:30 simpp.xml
-rw-r--r--    1 pzensius pzensius    22287 2005-02-18 16:28 splash.gif
-rw-r--r--    1 pzensius pzensius      257 2005-02-18 21:05 tables.props
drwxr-xr-x    7 pzensius pzensius     4096 2005-02-18 18:29 themes
-rw-r--r--    1 pzensius pzensius     4547 2005-02-18 18:38 ttree.cache
-rw-r--r--    1 pzensius pzensius      443 2005-02-18 16:30 update.xml
drwxr-xr-x    6 pzensius pzensius     4096 2005-02-18 18:29 xml

---

### Post by kassetra on 2005-02-19
animalstyle: ok, your permissions look fine (from what I can see there) ...
  so ok a few more tests here...
  
  on the command line, if you just type "limewire" or "LimeWire" does it run the program?
  
  If it doesn't, does typing "/opt/LimeWire/LimeWire" work?
  
 if "/opt/LimeWire/LimeWire" works from the command line, it should also work from the launcher...  and if not, can you make the command "sudo /opt/LimeWire/LimeWire" ... and does *that* work??

---

### Post by animalstyle on 2005-02-19
man I really must have screwed something up   ](*,) 

1. "limewire" "LimeWire" at prompt?  Nope.

2. "/opt/LimeWire/LimeWire" at prompt? Yes (this is the one with the java error messages).

3. It doesnt also work from launcher unfortunately   ](*,) 

4. sudo /opt/LimeWire/LimeWire? Currently, this is hanging on the LimeWire "Loading HTML Engine" screen.

Still a stumper.... ](*,) 

ow.

P.S. sudo /opt/LimeWire/LimeWire *does* work at the command prompt.

---

### Post by kassetra on 2005-02-19
but does sudo /opt/LimeWire/LimeWire work in your launcher?
  
if it works in the launcher as sudo but not without it, there is a permissions issue somewhere... if it doesn't work in the launcher...
 Let's try the "clear it all out and start over" approach: 
 
   move your .limewire files (any and all) to 0.limewire
   rm -rf /opt/LimeWire
   check java: java -version  (this might be the sticking point!!)
   
   Now let's go through the limewire installation from the starter guide:
   [LimeWire]("http://ubuntuguide.org/#limewire")
   
   *if java was the issue, we'll go through the java install the way I did it, ok?

---

### Post by ioliver on 2005-02-19
I doubt it will helpl in this case, but I've found that running a combination of commands from a launcher (without writing a script) means doing something like this for your command -

sh -c "sleep 1 && xset dpms force off"

I have this on a launcher to turn off my monitor after a 1 second sleep (to let me get my hand off the mouse!)

To run LimeWire with a different working directory you may want to have a cd as the 1st command and then the command to run LimeWire.

Regards

Ian

---

### Post by animalstyle on 2005-02-19
wooooooooo  \\:D/ 

Reinstallation fixed it.  Thanks for all the help.

---

### Post by kassetra on 2005-02-19
animalstyle: you're welcome!  I'm glad it works now for you!  WOO!  \\:D/

---

