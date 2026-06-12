---
title: "Installation and Terminal Commands"
date: 2009-05-02
forum: General Help
---

### Post by Sliiice on 2009-05-02
Hey I am new to Linux (Xubuntu), I was wondering if anyone could explain how the terminal works and how to decide what to enter in order to Install programs. 

Thanks.

---

### Post by mali2297 on 2009-05-02
For installing packages via the command line:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

For using the terminal in general:
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Paqman on 2009-05-02
To install a program:
```

sudo apt-get install packagename

```

What that means:
**sudo** = Super User DO. Executes the command as an administrator. Your account doesn't have enough privileges to install software without this command. It means you'll have to use your password.

**apt-get** = APT is the Advanced Packaging Tool. It handles installing, removing and upgrading software.

**install** = Tells APT what you want to do

When this command is run the system first authenticates that you are a human who knows the password, it then checks that the package is available from a repository, downloads it along with any dependencies and installs the whole lot.

---

### Post by delcypher on 2009-05-02
Welcome to Linux. The command-line in my opinion is the most important part of learning to use linux. You'll never learn everything but here's a good place to [start]("http://lowfatlinux.com/") and [here]("https://help.ubuntu.com/community/UsingTheTerminal")

As for installing programs there's three ways.

1. From repositories (think of them as an online software library approved your particular linux distro).

apt-get is the main program for doing this. You read about it and more [here]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto")



2. Download the installation binary
Simply download the file (in this example it's called myprogram), make executable, then run it.
```

#The line below makes myprogram executable
chmod u+x myprogram
#The line below executes myprogram (the ./ part tells BASH that the program is in the . directory (current directory))
./myprogram
```


3. Download the sourecode, compile and run.

There's a nice guide [here]("http://www.tuxfiles.org/linuxhelp/softinstall.html")

Have fun!

---

### Post by Sliiice on 2009-05-02
Looks like I have some reading to do! Thanks for the resources.

---

