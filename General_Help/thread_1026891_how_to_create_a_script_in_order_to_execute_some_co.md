---
title: "how to create a script in order to execute some commands"
date: 2008-12-31
forum: General Help
---

### Post by gdp77 on 2008-12-31
Hallo everyone (and a happy new year!!! )

In order to enable my laptop's wireless card I have to enter each time in terminal :

```

sudo bash

``` now the system asks for my password

```

modprobe acerhk
echo "on" > /proc/driver/acerhk/wirelessled

```

how can i create a batch file to execute these commands?

---

### Post by MaxIBoy on 2008-12-31
First off, don't use sudo bash. That's very un-elegant. Just add sudo the beginning of each command. Or, if you have to, type in "su" once and "exit" when you're done (but don't use that in your scripts.)



METHOD 1 (not recommended method for this particular situation):
[LIST=1]
[*]Open a text editor.
[*]Type up the commands in order.
[*]Add ```
#! /bin/bash
``` to the beginning.
[*]Save the file with a .sh file extension (the .sh extension isn't required, but it's traditional.)
[*]Pull up a terminal, run ```
sudo chmod +x [name of file]
``` to allow the file to run as a program.
[*]Now, you can cd to the directory and type in ```
./nameOfFile.sh
``` to run it, (or you can double-click it, IF you use "gksudo" instead of "sudo" when writing your script.)
[/LIST]

METHOD 2 (recommended method):
[LIST=1]
[*]Open ~/.bashrc with a text editor.
[*]type ```
alias wifiactivate=' [whatever the commands are]'
```
[*]Save .bashrc.
[*]Restart.
[*]Now, when you type wifiactivate in the terminal, the commands run automatically. Or, if you use "gksudo" instead of "sudo" when you're creating your alias, you can run it by hitting alt-f2 and typing it in, or binding it to a key combo.
[/LIST]

---

### Post by benign on 2008-12-31
You can use the 'visudo' command to edit the permessions of sudoers..

run 'visudo' from the terminal and add this to the last line:

'username ALL= NOPASSWD: /pathtoscript/script'

pathtoscript is wherever your script is, like /home/user/scriptname

---

### Post by gdp77 on 2008-12-31
please explain to me:

1) why sudo bash is "un-elegant" ?
2) what "#! /bin/bash" does ?
3) what ".sh" file extension means.


thank you

---

### Post by MaxIBoy on 2008-12-31
[LIST=1]
[*]"Sudo bash" circumvents the whole point of "sudo," which is to run ONE SINGLE command as the root user. The idea is, if you're running around as root all the time, you might mess something up. Sudo allows you to run one single command as root that you understand completely. "su" allows you to open a root terminal and run more than one command in a row as root without adding sudo to the beginning. (It's not that big a deal, but things like that bug me.)
[*]When you add "#!" to the beginning of a text file, that's UNIX-speak for "open me with." "#! /bin/bash" means "open me with /bin/bash."
[*]When you're typing commands into a terminal, you're using a textmode shell (a shell is what you use to tell the OS what to do, there are textmode shells and graphical shells.) A shell script is basically a batch file. ".sh" means "shell script." Like I said, it's traditional, it's not required.
[/LIST]

---

### Post by arm-c on 2009-02-02
Well,

Thought I would add to here a python utility/gui that I wrote to address the wireless / bluetooth functionality of the acerhk driver.

Hope it helps someone.  The readme has some helpful information and good place to start.

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

v/r
ARM-C

---

### Post by ratmandall on 2009-02-02
> how can i create a batch file to execute these commands?

Batch is made for DOS\Windows and OS/2. Bash is made for Linux, MacOSX and other 'Unix-like' OS's. But also can run on windows with Cygwin ^-^

---

