---
title: "How can I create a shortcut of an application?"
date: 2010-08-21
forum: Desktop Environments
---

### Post by al1x on 2010-08-21
Hello there , I 'm trying to create a shortcut for Geogebra instead of navigating through the terminal to the directory where geogebra.sh is and typing : " sh geogebra.sh ".So I'm going to the main menu, pressing New item and then I have a problem.. I don't know how to make this shortcut..what I must do to run the command sh geogebra.sh with a shortcut? Anybody help please ?

---

### Post by ajgreeny on 2010-08-21
> **al1x said:**
> Hello there , I 'm trying to create a shortcut for Geogebra instead of navigating through the terminal to the directory where geogebra.sh is and typing : " sh geogebra.sh ".So I'm going to the main menu, pressing New item and then I have a problem.. I don't know how to make this shortcut..what I must do to run the command sh geogebra.sh with a shortcut? Anybody help please ?
In the command box enter the full pathway to the .sh file and that should do it.  Just make sure the .sh file is executable first or it will fail.

---

### Post by Dinahalye on 2010-08-22
Do you use Gnome or KDE? (Or should I dare to ask Fluxbox etc. :p

---

### Post by kerry_s on 2010-08-22
> **al1x said:**
> Hello there , I 'm trying to create a shortcut for Geogebra instead of navigating through the terminal to the directory where geogebra.sh is and typing : " sh geogebra.sh ".So I'm going to the main menu, pressing New item and then I have a problem.. I don't know how to make this shortcut..what I must do to run the command sh geogebra.sh with a shortcut? Anybody help please ?

use the browse button next to command.

---

### Post by al1x on 2010-08-22
Hmm..inserting the full pathway (/home/user/.../GeoGebra-3.2.40.0-Portable-Java-6u18-Linux-i586/geogebra.sh) would not do the job :/ It always fails and the .sh file is executable..

---

### Post by al1x on 2010-08-22
> **Dinahalye said:**
> Do you use Gnome or KDE? (Or should I dare to ask Fluxbox etc. :p

I'm using Gnome :roll:

---

### Post by Gaygerbil on 2010-08-23
Open up 'Keyboard Shortcuts' under Preferences. W/e command you're using to launch this application from the terminal put that command in a new custom shortcut, assign a shortcut to it, viola.

---

### Post by al1x on 2010-08-23
> **Gaygerbil said:**
> Open up 'Keyboard Shortcuts' under Preferences. W/e command you're using to launch this application from the terminal put that command in a new custom shortcut, assign a shortcut to it, viola.

Hmm..but I want an icon-shortcut to place it to the education (i.e.) menu , plus how do I write the command ? because when I go from terminal I press first 

~~ cd /home/user/.../GeoGebra-3.2.40.0-Portable-Java-6u18-Linux-i586
and then I'm running the geogebra.sh like this:
~~ sh geogebra.sh
How I translate this into a command?
:lolflag:

---

### Post by Gaygerbil on 2010-08-23
That's the same thing for your menu, you just have to create a new item in w/e menu you want.

You will see a line named command in here you want to write something like this:

```
 /home/user/.../GeoGebra-3.2.40.0-Portable-Java-6u18-Linux-i586/geogebra.sh
```

Just basically put the file path to the script file, a script file can be executed as a command. Hope this helps bro. :]

To make sure you get the write command try executing the command in the terminal in one line that's really what you're aiming for.

---

### Post by al1x on 2010-08-23
I tried and executed the code in the terminal and I get this message : "/home/alexadros/GeoGebra/geogebra: 2: jre/bin/java: not found" and then I opened googleearth like you told me(/home/user/google-earth/googleearth.sh) and it worked.So something 's wrong with geogebra..only when I navigate to the directory  via terminal and execute the command "sh geogebra.sh" the program opens.. or if I doubleclick the .sh

---

### Post by Gaygerbil on 2010-08-24
So have you figured out a command in the terminal yet? I'm confused on what happened.

Either way the command is probably not working because there's a space character somewhere in your directory. I think you replace space characters with forward slashes and it'll be fine.

What's your directory?

Just right click on your script, hit properties, and copy paste the location here. I'll tell you the command you'll need.

---

### Post by Vaphell on 2010-08-24
doesn't it say that jre/bin/java is not found?

what happens when you put
sh -c "cd /path/to/your/sh; ./geogebra.sh"
as a shortcut command?

---

### Post by al1x on 2010-08-26
> **Gaygerbil said:**
> So have you figured out a command in the terminal yet? I'm confused on what happened.

Either way the command is probably not working because there's a space character somewhere in your directory. I think you replace space characters with forward slashes and it'll be fine.

What's your directory?

Just right click on your script, hit properties, and copy paste the location here. I'll tell you the command you'll need.

Yep,I figured out how to put the command and I tested it in terminal but it's not responding..I get a message that /jre/bin/jave is not found..

---

### Post by al1x on 2010-08-26
> **Vaphell said:**
> doesn't it say that jre/bin/java is not found?

what happens when you put
sh -c "cd /path/to/your/sh; ./geogebra.sh"
as a shortcut command?

You mean like this? :

sh -c "cd /home/user/Geogebra/geogebra.sh ./geogebra.sh" 
if its like this I checked it and again it's not responding..The terminal appears for a sec and it exits without any commands..lol how hard it's to make a shortcut !? :p

---

### Post by mister_p_1998 on 2010-08-27
If its a java problem, you need to run the java program with the prefix java -jar /home/steve/ted/ted.jar

maybe running the script from the commandline is picking up the java executeable, but the shortcut isnt. Please post the script.

---

### Post by mister_p_1998 on 2010-08-27
or try this:
[http://www.geogebra.org/forum/viewtopic.php?f=20&t=17133](http://www.geogebra.org/forum/viewtopic.php?f=20&t=17133)

---

### Post by mister_p_1998 on 2010-08-27
or get the deb here:
[http://ubuntuforums.org/showthread.php?t=688222](http://ubuntuforums.org/showthread.php?t=688222)

yeah that works fine on my Lucid install, puts a shortcut in Education.
Steve

---

### Post by al1x on 2010-08-27
> **mister_p_1998 said:**
> If its a java problem, you need to run the java program with the prefix java -jar /home/steve/ted/ted.jar

maybe running the script from the commandline is picking up the java executeable, but the shortcut isnt. Please post the script.

Here's the script

```
#!/bin/sh
jre/bin/java -jar geogebra.jar
```

---

