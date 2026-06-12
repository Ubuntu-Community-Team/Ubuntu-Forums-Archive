---
title: "Nintendo on Ubuntu: How do I install ZSNES"
date: 2007-07-12
forum: Gaming &amp; Leisure
---

### Post by Seth Leonard on 2007-07-12
I am trying to install the data from Feisty to my terminal from Ubuntu Feisty to use Nintendo for Ubuntu.  I am really new at this and I don't have any idea what I am doing.  I tried copy/paste the computer jargon into the terminal, but it was very confusing, and the terminal rejected everything.  The instructions are below.  I really couldn't figure out what to do, please help.

 Super Nintendo Emulator (ZSNES) 1.510 for i386/AMD64

    * Read #General Notes 

For support or questions please see this thread [http://ubuntuforums.org/showthread.php?t=432642](http://ubuntuforums.org/showthread.php?t=432642)

echo "deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main" | sudo tee -a /etc/apt/sources.list
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O- | sudo apt-key add -
sudo apt-get update

sudo apt-get install zsnes32 #for amd64 users
sudo apt-get install zsnes   #for everyone else

    * Applications > Games > zsnes or zsnes32

[email]shleonard@gmail.com[/email]

---

### Post by hikaricore on 2007-07-12
Not to discourage you from learning how to use command line, but if you want a simple way to install the latest zsnes.

You can download it at GetDeb.net: [http://www.getdeb.net/app.php?name=ZSNES](http://www.getdeb.net/app.php?name=ZSNES)

Download the package, install it, and it's done.  ^_^

---

### Post by cogadh on 2007-07-12
I would go with hikaricore's suggestion, just for the ease of the install, but if you want to try the terminal, do this with the info you already have:

[LIST=1]
[*]Select and copy each line one at a time. 
[*]Paste them into the terminal by pressing the middle mouse button, or by clicking on Edit > Paste. 
[*]After pasting each line, hit the enter key. 
[*]When asked for a password, put in your login password. 
[/LIST]

For that last line (the "sudo apt-get..." ones) leave off everything from the # and you only need to do the one that applies to your system. If you do not have a system with a 64-bit processor, then use "sudo apt-get install zsnes".

---

### Post by dfreer on 2007-07-12
If you want, I can go through want each command means, that way you can learn something (and get zsnes installed as well). Note ZSNES is a SNES emulator, not a NES emulator btw.

```
echo "deb http://packages.dfreer.org feisty main" | sudo tee -a /etc/apt/sources.list
```
This command simply adds the line "deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main" to the file /etc/apt/sources.list.
There are 2 commands here, seperated by the | character. The first command, echo, will simply print whatever text follows it. The second command tee -a will append (write) to the file /etc/apt/sources.list, and the | character is called a pipe, you will need to read up more on that on your own. Note the last bit begins with the command **sudo**. This command lets you run other commands as root, this is needed.
```
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
```
Once again, there are two commands here. The first command wget will download any file from the internet you require, it is very useful. Here we are downloading my GPG key which is needed to use my server. The last bit is once again complicated, in short it will allow you to use my GPG key.
```
sudo apt-get update
```
This updates the repository list, which basically checks all of the repositories (repositories are servers you download programs from) for new packages. This is needed to check my server for the first time.
```
sudo apt-get install zsnes #for everyone else
```
First off, anything following a # sign is ignored. So it makes no difference if you type the above or the below:
```
sudo apt-get install zsnes
```
apt-get is used to download a program from the repository, and "install" means simply that. zsnes is the name of the program.

Anyways, hope this helps! Lemme know if you need more help getting zsnes installed, a simpler method would be to use the getdeb link hikaricore suggested above. Save it to your desktop then double-click the file to start the install process.

---

### Post by acoustibop on 2007-07-15
FWIW I've tried dfreer's package for pSX and, although I found I prefer to use the simpler method (which you can't use with ZSNES) of just tarring it into a folder, his packages _do_ seem to work nicely. ;)

---

