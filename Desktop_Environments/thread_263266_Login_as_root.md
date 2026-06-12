---
title: "Login as root?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by mmmpancakes on 2006-09-22
I'm trying to login as root so I can change permissions on a couple files. I can't seem to find 'root' under my user accounts. Any advice?

---

### Post by draco1889 on 2006-09-22
Use sudo:
```
sudo <command>
```

---

### Post by aysiu on 2006-09-22
Don't log in as root.

Press Alt-F2 and type ```
gksudo nautilus
``` Now you're browsing as root.

If you prefer the terminal, type ```
sudo -s
```

More info here: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by Omnios on 2006-09-22
In Ubuntu its not recomended to log in as root. Ubuntu uses the sudo command that allows you to do things as foot, for example 
```

sudo gedit /etc/MyFIle 

``` to open the a text file as  root. This also carrys over to other commands like sudo mv or sudo cp.

 There is also the " sudo nautilus " trick to allow you to use the file manager as root. 

 As for permtions doing it in terminal is donw with chmod
```

tom@miko:~$ chmod --help
Usage: chmod [OPTION]... MODE[,MODE]... FILE...
  or:  chmod [OPTION]... OCTAL-MODE FILE...
  or:  chmod [OPTION]... --reference=RFILE FILE...
Change the mode of each FILE to MODE.

  -c, --changes           like verbose but report only when a change is made
      --no-preserve-root  do not treat `/' specially (the default)
      --preserve-root     fail to operate recursively on `/'
  -f, --silent, --quiet   suppress most error messages
  -v, --verbose           output a diagnostic for every file processed
      --reference=RFILE   use RFILE's mode instead of MODE values
  -R, --recursive         change files and directories recursively
      --help     display this help and exit
      --version  output version information and exit

Each MODE is of the form `[ugoa]*([-+=]([rwxXst]*|[ugo]))+'.

Report bugs to <bug-coreutils@gnu.org>.


```

 oopsies two people beet me to this one lol.

---

### Post by mmmpancakes on 2006-09-22
Wonderful! I used 

sudo nautilus

To login as root, and added full permissions to booth my boot and raw1394 files. Restarted, and my DV camera works beautifully. I've been working on this for a couple days now, so I appreciate everyone's help on this. 

Thanks!

---

### Post by aysiu on 2006-09-22
I would recommend *gksudo nautilus* instead of *sudo nautilus*. Read more details about the difference here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

