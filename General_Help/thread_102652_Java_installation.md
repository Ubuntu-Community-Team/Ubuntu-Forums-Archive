---
title: "Java installation?"
date: 2005-12-12
forum: General Help
---

### Post by Helljumper on 2005-12-12
Ok, I give up looking on the internet and on the Ubuntu forums :(  I have been going insane. I don't know how to install Java onto the Firefox browser. I follow everything the guide says but it says "under the command line enter to where you saved it" or something like that. I don't know what to do from there :( Any help would be appericeated. (sp?)

---

### Post by amohanty on 2005-12-12
The most straightforward solution is to install sun-jre from the plf repos:

add the following to /etc/apt/sources.list -
> 
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

at the terminal type:
```
apt-get update
```

fire up synaptic and search for sun
install (I am not 100%sure of the names):
sun-jre1.5
sun-jdk1.5 

comment out the abovementioned lines in your /etc/apt/sources.list ie prepend a '#' (without the quotes) at the front of each line. This is so that you do not accidentally update something from those repos.

Now remove gcj using synaptic.
At the terminal if you type:
```
java -version
```
the response should be the hotspot client.

This should install the jre plugin for FF.

HTH

---

### Post by Helljumper on 2005-12-12
Ok, so how do I make the file editable? It only lets me read only. (The first set of instructions).

---

### Post by cdsboy on 2005-12-12
don't know about the last thing. but the easiest way it to use Automatrix

---

### Post by pertti on 2005-12-12
[QUOTE=Helljumper]Ok, so how do I make the file editable? It only lets me read only. (The first set of instructions).[/QUOTE]

To edit that file in write mode you must be root. The easiest way is to open a console and type:

```
sudo gedit /etc/apt/sources.list
```

Then enter your password and the file will be opened in Gedit in write mode.

---

### Post by Helljumper on 2005-12-12
Ok, When I try to put "apt-get update" I get this. 
```
   apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

:( Anyone know how to get out of this bunch?

---

### Post by RAOF on 2005-12-12
Do you have another apt-get type program open (Synaptic, the update-manager, etc?).  That error is, translated into English:

"It seems that another program has access to the apt cache.  If I were to mess with it now, I could break your system.  So I won't.  Please close the program that's accessing the apt cache, and try again"

---

### Post by Helljumper on 2005-12-12
[QUOTE=RAOF]Do you have another apt-get type program open (Synaptic, the update-manager, etc?).  That error is, translated into English:

"It seems that another program has access to the apt cache.  If I were to mess with it now, I could break your system.  So I won't.  Please close the program that's accessing the apt cache, and try again"[/QUOTE]

Nope, The only things I have open is Gaim and Firefox. No other apt-get type program is open :(

---

### Post by pecanov on 2005-12-12
Ok... the easies way to get Java:

Download it from java.sun.com, linux version.
Unpack the zip somewhere in your home directory: /home/username/Java for ex.

than write:

```
cd  ~/.mozilla/plugins
ln -s /home/username/Java/jre/plugin/i386/ns7/libjavaplugin_oji.so .
```

... and your done!

If you want to use java everywhere:

Open console and type:
```

sudo gedit /etc/bash.bashrc
```

... it will prompt for password, enter your password and gedit will popup, and at the end write:

```
JAVA_HOME=/home/username/Java
PATH=$JAVA_HOME/bin:$PATH
export JAVA_HOME PATH

```

... and save. 

That's it.
Don't forget to replace /home/username with your actual home directory (append your username to /home/)

---

### Post by RAOF on 2005-12-12
[QUOTE=Helljumper]Nope, The only things I have open is Gaim and Firefox. No other apt-get type program is open :([/QUOTE]
Well, due to the magic of antiquated lockfile systems, you can sometimes get a program to crash and retain a hold of the lockfile, so that nothing else can use it.  Perhaps a reboot first?  You could also try "lsof /var/lib/apt/lists/lock" - that will show what process has the lockfile opened.

---

### Post by pertti on 2005-12-13
[QUOTE=Helljumper]Ok, When I try to put "apt-get update" I get this. 
```
   apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

:( Anyone know how to get out of this bunch?[/QUOTE]

Try this:

```
sudo apt-get update
```

In Ubuntu/Linux some operations (like editing system config files like sources.list or messing with the package manager) requiere special permissions. To execute one of this operations in the command line with these special permissions you have to put "sudo " at the beginning of the command, and then enter your password. This will execute the following command as if you were the all-mighty "super user" :) (sudo means "Super User DO").

This permissions are also called root permissions. root is the name of a special user in linux that has all these permissions. So if you're asked to do something as if you were root, put "sudo" at the beginning of the line.

Hope this helps.

Edit: by the way, most, if not all, gnome programs that require these special permissions will prompt you for your password. Synaptic is one of these programs, and is a graphical front-end for apt. You could've added those lines to sources.list from synaptic: (i'm translating on-the-fly from the spanish version, so this may be innacurate) Configuration > Repositories > Add > Custom > write the line. And to do an "apt-get update" just press the Update button on the top-left.

---

