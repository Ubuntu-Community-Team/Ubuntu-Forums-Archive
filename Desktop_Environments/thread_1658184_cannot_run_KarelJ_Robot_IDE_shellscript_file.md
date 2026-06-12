---
title: "cannot run KarelJ Robot IDE shellscript file"
date: 2011-01-02
forum: Desktop Environments
---

### Post by doubleOh on 2011-01-02
i am using ubuntu 10.10, i just downloaded KarelJIDE. according to installation instructions;

[http://www.st.informatik.tu-darmstadt.de/static/pages/lectures/inf1/kareljide/KarelJIDEDocumentation.html](http://www.st.informatik.tu-darmstadt.de/static/pages/lectures/inf1/kareljide/KarelJIDEDocumentation.html)

i am supposed to simply run the shellscript file in order to start the program, but i can't get it to start!!it opens up a gedit window...where do i go from there?
please help,i have an urgent programming assignment.
thanks

---

### Post by Wobblybob on 2011-01-02
right click on the KarelJIDE.sh file select [Properties], [Permissions] and select the option to make executable then you can double click on it and it should give you the option to run in a terminal.

---

### Post by doubleOh on 2011-01-02
thanks Wobblybob, i have changed permissions to allow execute, but when i try to run it in terminal the terminal window only opens for about a second and quickly disappears.

---

### Post by Wobblybob on 2011-01-02
ok it says you need a version of java higher than 1.5 so check out your current version with.

sudo update-alternatives --config java

I'd be inclined to install the latest sun java with

sudo apt-get install sun-java6-jre

then use the command above to make it the default..

and try your script again from a Terminal opened in the folder the script is in with

./KarelJIDE.sh

---

### Post by doubleOh on 2011-01-02
i had already installed java according to instructions, so when i ran the update command i got the reply'there is only one alternative in link group java...nothing to configure'.
how do i "try the scripit from a terminal opened in the folder the script is in" 
-the script is in my desktop.
sorry i'm rather new to ubuntu :(

---

### Post by Wobblybob on 2011-01-02
ok on the java, can you open a Terminal and type;

java -version

and post the result,

re running the script, when you open a terminal it automatically opens in your home directory/folder so to change to your desktop which in Linux is just another directory/folder type

cd Desktop

[cd = change directory], the prompt should now show ~/Desktop$

to check type; 
ls
and it should list all the files on your Desktop including your KarelJIDE.sh 

run it by typing

./KarelJIDE.sh

and pressing enter

---

### Post by doubleOh on 2011-01-02
here's the java- version result;

Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: version.  Program will exit.

---

### Post by Wobblybob on 2011-01-02
that's your problem then :p java

I'd remove java in a terminal

sudo apt-get remove --purge java*

or use the synaptic package manager and search for java, then uninstall it

then reinstall

sudo apt-get install sun-java6-jre

or again use synaptic to do so...

---

### Post by doubleOh on 2011-01-02
:O java!! thanks so much.

ok i just removed and reinstalled java

now when i run the karelJIDE.sh this is the result;


oyala@oyala-desktop:~/Desktop$ ./KarelJIDE.sh
./KarelJIDE.sh: line 1: javaw: command not found
oyala@oyala-desktop:~/Desktop$ ls
doc                  karel.ico      KarelJIDE.jar  usr
iptv_tv_unicast.m3u  KarelJIDE.bat  KarelJIDE.sh

---

### Post by Wobblybob on 2011-01-02
ok I see you have the main program file KarelJIDE.jar on your desktop which should now open using the command

java -jar KarelJIDE.jar

in a terminal, if that works you can then ammend the KarelJIDE.sh file [which is only a launcher] by editing it entering in a Terminal;

gedit KarelJIDE.sh

then changing the line from

javaw -jar KarelJIDE.jar

to

java -jar KarelJIDE.jar

and resaving, now when you double click on the KarelJIDE.sh it should open your program.

---

### Post by doubleOh on 2011-01-02
yaaay!!

i honestly feel a lot smarter, now to get on with my assignment.

thank you kindly, Wobblybob :)

---

### Post by Wobblybob on 2011-01-02
congrats, glad your up and running.

---

### Post by doubleOh on 2011-01-02
thank you kindly Wobblybob,

now to get on with my assignment :)

---

