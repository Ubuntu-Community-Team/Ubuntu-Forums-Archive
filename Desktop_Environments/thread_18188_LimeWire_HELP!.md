---
title: "LimeWire HELP!"
date: 2005-03-05
forum: Desktop Environments
---

### Post by cnastiuk on 2005-03-05
I've downloaded LimeWire PRO and have no trouble running the program.  However, I want to be able to run the program from the panel.  When I downloaded it from LimeWire there was no installation necessary, just change to the LimeWire directory and type "sh runLime.sh" or "java -jar LimeWire.jar" in the terminal to get it to run.  However, when attempting to run it from the panel, I've gotten nowhere.  I've tried to make a symbolic link from the directory to /usr/bin/LimeWire and just running LimeWire from the panel, but no luck there, please any help is appreciated. ~ NASTI

---

### Post by brk3 on 2005-03-05
The way i do it is install the folder under /usr/share/Limewire/ , make a sym link in /usr/bin to the script thats just called 'Limewire'. Then you can make a shortcut on your desktop or panel or whatever that calls the command 'Limewire' and it should start up.

---

### Post by bored2k on 2005-03-05
> **brk3]The way i do it is install the folder under /usr/share/Limewire/ , make a sym link in /usr/bin to the script thats just called 'Limewire'. Then you can make a shortcut on your desktop or panel or whatever that calls the command 'Limewire' and it should start up.[/QUOTE]
 i get this my making a script of the file

mine would be

[quote]#!/bin/sh
cd /opt/Limewire said:**
> 

then [quote]chmod 755 script.sh


and  i make the shortcut with that script

nice method brk3 has ... imma try it out thnx

---

### Post by cnastiuk on 2005-03-05
brk3 - I can't "install" LimeWire so to speak.  They just give me a .zip file and I run                  "sh runLime.sh" in the terminal after changing to the unzip directory I downloaded.  LimeWire runs straight from the folder that I download from LimeWire, no installation required.  Do I make a symoblic link to LimeWire the folder or a particular file in that folder.

bored2k - As for the making of a script for the file, I don't know where to start with the directions you've given, possible for a more... step-by-step approach.  Thanks!

---

### Post by bored2k on 2005-03-05
> **cnastiuk]brk3 - I can't "install" LimeWire so to speak.  They just give me a .zip file and I run                  "sh runLime.sh" in the terminal after changing to the unzip directory I downloaded.  LimeWire runs straight from the folder that I download from LimeWire, no installation required.  Do I make a symoblic link to LimeWire the folder or a particular file in that folder.

bored2k - As for the making of a script for the file, I don't know where to start with the directions you've given, possible for a more... step-by-step approach.  Thanks![/QUOTE]

Allrighty here it goes :

Applications > Accesories > Text Editor

First save the file to script.sh or the name you desire, with the .sh extension.

The text file will contain this:
*ill pretend you have the file in /home/cnastiuk/Limewire
> 
#!/bin/sh
cd /home/cnastiuk/Limewire said:**
> 

After saved, on ur File Manager right clic > properties 
File Permissions, and make it look like this :
[IMG]http://img221.exs.cx/img221/9050/file3os.jpg[/IMG] 


After his , put the script in ur home directory [not /home/ , but /home/cnastiuk/]
When adding the panel, simply input
[QUOTE]sh script.sh 
or
[QUOTE]./script.sh 

---
Hope it works
btw, what Limewire Pro are you using ? I'm stuck with 4.2 and at startup it keeps telling me to update [i.e. to pay]  ](*,)

---

### Post by cnastiuk on 2005-03-05
[QUOTE=bored2k]Allrighty here it goes :

Applications > Accesories > Text Editor

First save the file to script.sh or the name you desire, with the .sh extension.

The text file will contain this:
*ill pretend you have the file in /home/cnastiuk/Limewire


After saved, on ur File Manager right clic > properties 
File Permissions, and make it look like this :
[IMG]http://img221.exs.cx/img221/9050/file3os.jpg[/IMG] 


After his , put the script in ur home directory [not /home/ , but /home/cnastiuk/]
When adding the panel, simply input
 
or
 

---
Hope it works
btw, what Limewire Pro are you using ? I'm stuck with 4.2 and at startup it keeps telling me to update [i.e. to pay]  ](*,)[/QUOTE]
 Well tried what you said, but still no responses.  I click it and it does absolutely nothing...  Any other ideas???  Might the permissions on the LimeWire folder make a difference?  I am using LimeWire PRO 4.6.  When you purchase PRO, you only get free updates for 6 months after that you have to pay again.  Gimmick, I know...

---

### Post by bored2k on 2005-03-05
[QUOTE=cnastiuk]Well tried what you said, but still no responses.  I click it and it does absolutely nothing...  Any other ideas???  Might the permissions on the LimeWire folder make a difference?  I am using LimeWire PRO 4.6.  When you purchase PRO, you only get free updates for 6 months after that you have to pay again.  Gimmick, I know...[/QUOTE]
 ill get working on it , im not using the menu at the time but ill try making it work again and reply ASAP

---

### Post by bored2k on 2005-03-05
I just did it and it WORKED .

> user@root:~ $ cat lime.sh
#!/bin/bash
cd /opt/Limewire/; sh runLime.sh

user@root:~ $ ls -l lime.sh
-rwxrwxrwx    1 user      user            46 2005-03-05 16:44 lime.sh

The "cat" thing shows what my script has inside .
The "ls -l" shows my file with its attibutes.

It has read/write support for all users .

So substitute with your values, and right clic > permissions, and check everyone for read/write/execute support .

BTW, my user has full read write support to the entire Limewire directory.

edit > i just double clicked on it and it opened, so the icon should do so.

---

### Post by cnastiuk on 2005-03-05
[QUOTE=bored2k]I just did it and it WORKED .



The "cat" thing shows what my script has inside .
The "ls -l" shows my file with its attibutes.

It has read/write support for all users .

So substitute with your values, and right clic > permissions, and check everyone for read/write/execute support .

BTW, my user has full read write support to the entire Limewire directory.

edit > i just double clicked on it and it opened, so the icon should do so.[/QUOTE]
 I dunno what I didn't do the first time, but it works now!  I appreciate your help.

---

### Post by bored2k on 2005-03-05
[QUOTE=cnastiuk]I dunno what I didn't do the first time, but it works now!  I appreciate your help.[/QUOTE]
 Good to hear .

Btw, how better is Limewire 4.6 than 4.2 ?? its gotta be a LOT differente cuz the startup thing gets on my nervers !@:@

---

### Post by cnastiuk on 2005-03-05
[QUOTE=bored2k]Good to hear .

Btw, how better is Limewire 4.6 than 4.2 ?? its gotta be a LOT differente cuz the startup thing gets on my nervers !@:@[/QUOTE]
 Check your messages in UbuntuForum!

---

### Post by bored2k on 2005-03-05
[QUOTE=cnastiuk]Check your messages in UbuntuForum![/QUOTE]
 :D

---

### Post by telmo on 2005-04-03
[QUOTE=cnastiuk]Well tried what you said, but still no responses.  I click it and it does absolutely nothing...  Any other ideas???  Might the permissions on the LimeWire folder make a difference?  I am using LimeWire PRO 4.6.  When you purchase PRO, you only get free updates for 6 months after that you have to pay again.  Gimmick, I know...[/QUOTE]

I think the problem lies here:

#!/bin/bash
cd /opt/[COLOR=DarkOrange]Limewire[/COLOR]/; sh runLime.sh

My directory is called LimeWire and not Limewire. Change it and it's solved! :D
(running LimeWire Pro 4.8.1)

---

### Post by Swab on 2005-05-16
This is driving me nuts, I can call runLime.sh from within its install directory under terminal... but I can't start it from a gnome menu.  Also if I setup a sym link or another script to call the file I get the following...

> Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2_05]
Configuring environment...
Loading LimeWire:
Unable to access jarfile LimeWire.jar

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_05-b04)
Java HotSpot(TM) Client VM (build 1.4.2_05-b04, mixed mode)


Currently Limewire is installed in usr/bin/share which is in my path... any ideas?

---

### Post by zab on 2005-05-17
[QUOTE=bored2k]:D[/QUOTE]

Uncool.

---

### Post by DiamondGirl on 2005-06-01
[QUOTE=bored2k]i get this my making a script of the file

mine would be



then 


and  i make the shortcut with that script

nice method brk3 has ... imma try it out thnx[/QUOTE]
 new to computer thing...think you can help

---

### Post by bored2k on 2005-06-01
[QUOTE=DiamondGirl]new to computer thing...think you can help[/QUOTE]
Sure, I could help. Where are you stuck ?

[SIZE=1]P.S. -  [-X to "help" **P**rivate-**M**essages ;)[/SIZE]

---

### Post by Gordon Freeman on 2005-06-01
Has anyone tried downloading the windows version through Wine? I did and got a Java environment missing error. Downloaded that and still got the same error. Anyone done this?

---

### Post by bored2k on 2005-06-01
[QUOTE=Gordon Freeman]Has anyone tried downloading the windows version through Wine? I did and got a Java environment missing error. Downloaded that and still got the same error. Anyone done this?[/QUOTE]
 Why would you want to run the windows version ? We have a Linux native one.

1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install sun-j2re1.5
4. [http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

Your name reminds me of my best gaming experience. Ever.

---

