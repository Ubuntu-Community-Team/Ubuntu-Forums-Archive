---
title: "Domino on ubuntu"
date: 2005-12-31
forum: General Help
---

### Post by gilagila on 2005-12-31
Helo
   anyone have any "how-to" for me to read on installing Domino 7 on linux

thx

Patrick:)

---

### Post by faperezg on 2006-11-11
I have found and read some installation howtos, but almost all of them presume that you know the linux packages or libraries installation way. Well, this is not always true. I am an expert Lotus Domino programmer since version 3.30, but I am a rookie in the linux administration. 

I have spent hours reading howtos that say: install or link the xxx.so library, but no one says HOW! Another pages suggest installing the yyyy.rpm package using alien, and put the command to do that. But I want a pure ubuntu / debian installation, so, why I should use a Red Hat package? Yes, I know that it works, but is a matter of personal style!

Well, I won't bother you with more useless details. I have installed the Ubuntu 6.06 LTS SERVER, and obviously, it has no graphical interface, so, I should know all the linux console commands to do the job. Let's begin!

First, allow all the apt repositories. Open the sources.list file with this command:

[COLOR="SeaGreen"]sudo nano /etc/apt/sources.list[/COLOR]

Uncomment all te lines begginning with 'deb ' . Save the file using Ctrl-X and tell apt to reload them:

[COLOR="SeaGreen"]sudo apt-get update[/COLOR]

Next, install the prerequisites

[COLOR="SeaGreen"]sudo apt-get install libstdc[+][+]2[.]10-.*
sudo apt-get install libstdc++5
sudo apt-get install libxmu6
sudo apt-get install libxp6
sudo apt-get install libxp-java
sudo apt-get install libxtst6[/COLOR]

Those prerequisites are libraries needed for Domino 7 to run, and the JVM to start.

Now, Domino needs an user to run. The domino installation package suggests the user 'notes' but I prefer 'domino', so, I created it.

[COLOR="SeaGreen"]sudo adduser domino[/COLOR]

This will create the user domino and the group domino. You must give a password for this user.

Now, begin the Domino installation. I prefer to copy the tar package in the /tmp folder. Let's suppose that you have a cd with the package, and the package name is domino7.tar

[COLOR="SeaGreen"]sudo mount /media/cdrom
cp /media/cdrom/domino7.tar /tmp[/COLOR]

Change to the destination folder and extract the package

[COLOR="SeaGreen"]cd /tmp
sudo tar xvf domino7.tar[/COLOR]

This will create a folder /tmp/linux where the files needed for installation are. Change to that folder and start the installation

[COLOR="SeaGreen"]cd linux
sudo ./install[/COLOR]

Follow all the instructions. You should note two things:

- The user and group selected for domino installation should be the same as the one you created, in this example, is 'domino'
- The installation package will ask you how to create the new server: Manual Server Setup, Local Server Setup and Remote Server Setup. I prefer the Remote Server Setup. If you selected this option, the domino server will run in listen mode, waiting for a remote machine to connect on the 8585 port. Then, go to a windows machine connected to the network, install the Lotus Notes R7 client and in the Start Menu - Programs - Lotus Applications you will find the Remote Server Setup icon. Click it and enjoy the Lotus Domino installation configuration.

Well, you should have your server running. But, this is not all the procedure if you want to start domino as a service. This requires some extra steps:

Find a rc-init script in the internet. I like the one written by Jens Vogel (thank you very much Jens) which you can find at [http://desktux.xs4all.nl](http://desktux.xs4all.nl). I modified it with my installation preferences, which are:

- binary installation folder: /srv/lotus
- data installation folder: /data/lotus
- user: domino
- group: domino
- output: /dev/tty12

The last option is the most important. You can have all the server console in a file, but I prefer it dumped to a virtual console. If you choose this way, the output of the console will be written to this console and you will see it if you press Alt - F12.

After modifying the script, save and copy it to the /etc/init.d folder:

[COLOR="SeaGreen"]sudo cp /etc/init.d[/COLOR]

Change to this folder:

[COLOR="SeaGreen"]cd /etc/init.d[/COLOR]

Change the permissions of the new copied file:

[COLOR="SeaGreen"]sudo chmod 0744 domino[/COLOR]

Finally, tell linux to start domino as a service:

[COLOR="SeaGreen"]sudo update-rc.d domino defaults[/COLOR]

This will create some links in the appropiate folders. Domino will start when you reboot your machine and will dump all the console output into the tty12.

I hope this howto helps someone with very little experience on linux to install Domino 7 on ubuntu.

---

### Post by Parme on 2006-11-17
This works fine in Dapper but in a fresh new installation of Edgy it seems non work. The problem is in install file that cannot found found something not specified. It works ok a Dapper upgraded to Efty.

---

### Post by faperezg on 2006-11-26
what error dou you get? I have installed a fresh copy of edgy and followed the same procedure, and it worked fine. May be if you decribe the error, I can help

---

### Post by Parme on 2006-12-05
Ciao. Sorry for the big late in answer but I was really busy in past days. I've a fresh copy on Ubyntu 6.10 on vmware server, not the server edition but the desktop edition. Here the output

[: 131: TOOLS/NLS/-E: unexpected operator
[: 131: tools/nls/-e: unexpected operator
[: 131: tools/nls/-e;1: unexpected operator
.: 1: -e: not found

It's obviously something that don't work with installation file but I didn't spend so much time beacause here we are using mostly Dapper and there's no problem there...

---

### Post by hhamme on 2006-12-19
Try this command instead, worked for me....:
./install 

Make sure you are in the  linux or linux\domino directory. Depends where the install file is stored.

---

### Post by Parme on 2006-12-19
Tha was the output of the ./install files on the right directory. The same procedure ( untar-cd-./install ) works fine on dapper..... But thank for suggesting to use ./install. it was a really bright idea....

---

### Post by stage on 2006-12-19
I had the same problem with the ./install command ](*,) 

Resolved with this: :-D 

sudo su
./install

thanks for the tutorial ! It really helped me out !

---

### Post by stage on 2007-01-28
Installation went good.

But now i have an error after installation, when server tries to start. It seem like something is wrong with Java. 

I searched everywhere, but can't seem to find the solution to start server and do the remote setup thing.

I use Edgy Server X86 (6.10) and running domino 7.0.2 on VMware.

I installed every package **faperezg** mentionned in is post.

I heard Blackdown java might do the job but, I couldn't install it :confused: 

Here is the output of my error:
[ [IMG]http://www.imagehosting.com/out.php/i159839_afterinstallation.jpg[/IMG]](http://www.imagehosting.com)

And here is the end of /local/notesdata/setuplog.txt :

[ [IMG]http://www.imagehosting.com/out.php/i159840_setuplog.jpg[/IMG]](http://www.imagehosting.com)


So if anyone has a clue, it would be greatly appreciated !

Thanks

Eric

---

### Post by stage on 2007-02-20
ttt
ttt

---

### Post by santo on 2007-02-21
Hi stage, 

you should take a look at windelen's article:
[http://www.windelen.be/windelen/wwwindelen.nsf/(All)/10664EE3D8B77D2BC1257091004D1CE8](http://www.windelen.be/windelen/wwwindelen.nsf/(All)/10664EE3D8B77D2BC1257091004D1CE8)

especially the part about "Lotus Domino on Linux obstacles" will be of interest to you:
[http://www.windelen.be/windelen/wwwindelen.nsf/(all)/BF80D75E986F1D54C1257022002A71FD?OpenDocument](http://www.windelen.be/windelen/wwwindelen.nsf/(all)/BF80D75E986F1D54C1257022002A71FD?OpenDocument)

---

### Post by santo on 2007-02-21
But unfortunately I have a problem too :-(

at startup I get a lot of errors about nsd.sh and more and more instances of it (nsd.sh that is) get started until I run out of memory.

These are the errors that I get:
```

Lotus Domino (r) Server, Release 7.0.2, September 26, 2006
Copyright (c) IBM Corporation 1987, 2006. All Rights Reserved.

tr: missing operand
Try `tr --help' for more information.
/opt/ibm/lotus/notes/latest/linux/nsd.sh: line 86: Linux: command not found
/opt/ibm/lotus/notes/latest/linux/nsd.sh: line 86: -d: command not found
Usage: awk [POSIX or GNU style options] -f progfile [--] file ...
Usage: awk [POSIX or GNU style options] [--] 'program' file ...
POSIX options:          GNU long options:
        -f progfile             --file=progfile
        -F fs                   --field-separator=fs
        -v var=val              --assign=var=val
        -m[fr] val
        -W compat               --compat
        -W copyleft             --copyleft
        -W copyright            --copyright
        -W dump-variables[=file]        --dump-variables[=file]
        -W exec=file            --exec=file
        -W gen-po               --gen-po
        -W help                 --help
        -W lint[=fatal]         --lint[=fatal]
        -W lint-old             --lint-old
        -W non-decimal-data     --non-decimal-data
        -W profile[=file]       --profile[=file]
        -W posix                --posix
        -W re-interval          --re-interval
        -W source=program-text  --source=program-text
        -W traditional          --traditional
        -W usage                --usage
        -W version              --version

To report bugs, see node `Bugs' in `gawk.info', which is
section `Reporting Problems and Bugs' in the printed version.

gawk is a pattern scanning and processing language.
By default it reads standard input and writes standard output.

Examples:
        gawk '{ sum += $1 }; END { print sum }' file
        gawk -F: '{ print $1 }' /etc/passwd
basename: missing operand
Try `basename --help' for more information.
dirname: missing operand
Try `dirname --help' for more information.
Usage: file [-bcikLhnNsvz] [-f namefile] [-F separator] [-m magicfiles] file...
       file -C -m magicfiles
Try `file --help' for more information.
Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  -n, --quiet, --silent
                 suppress automatic printing of pattern space
  -e script, --expression=script
                 add the script to the commands to be executed
  -f script-file, --file=script-file
                 add the contents of script-file to the commands to be executed
  -i[SUFFIX], --in-place[=SUFFIX]
                 edit files in place (makes backup if extension supplied)
  -l N, --line-length=N
                 specify the desired line-wrap length for the `l' command
  --posix
                 disable all GNU extensions.
  -r, --regexp-extended
                 use extended regular expressions in the script.
  -s, --separate
                 consider files as separate rather than as a single continuous
                 long stream.
  -u, --unbuffered
                 load minimal amounts of data from the input files and flush
                 the output buffers more often
      --help     display this help and exit
      --version  output version information and exit

If no -e, --expression, -f, or --file option is given, then the first
non-option argument is taken as the sed script to interpret.  All
remaining arguments are names of input files; if no input files are
specified, then the standard input is read.

E-mail bug reports to: bonzini@gnu.org .
Be sure to include the word ``sed'' somewhere in the ``Subject:'' field.
/opt/ibm/lotus/notes/latest/linux/nsd.sh: line 153: uid=1002(domino): command not found
/opt/ibm/lotus/notes/latest/linux/nsd.sh: line 153: s;[()]; ;g: command not found
/opt/ibm/lotus/notes/latest/linux/nsd.sh: line 153: {print substr($2,1,32);}: command not found
/opt/ibm/lotus/notes/latest/linux/nsd.sh: line 155: Linux: command not found

```
and this is repeating until I run out of memory or kill the nsd.sh processes

I already installed gawk (as suggested here: [http://www-10.lotus.com/ldd/nd6forum.nsf/PlatformAllThreadedweb/a9a9ae98338f98828525724700621e10?OpenDocument](http://www-10.lotus.com/ldd/nd6forum.nsf/PlatformAllThreadedweb/a9a9ae98338f98828525724700621e10?OpenDocument)), but that didn't help

---

### Post by arruah on 2007-05-10
Please help me for starting Domino 6.5 server on Ubuntu 7.04

I've this error since starting Domino server
```

notes@semcrb:/notes/data$ /opt/lotus/bin/server

Lotus Domino (r) Server, Release 6.5.3, September 14, 2004
Copyright (c) IBM Corporation 1987, 2004. All Rights Reserved.

The ID file being used is: /notes/data/server.id
Enter password (press the Esc key to abort):

11.05.2007 12:31:00 AM  Begin scan of databases to be consistency checked
11.05.2007 12:31:00 AM  End scan of databases: 1 found
11.05.2007 12:31:01 AM  Event Monitor started
11.05.2007 12:31:01 AM  Performing consistency check on events4.nsf...
11.05.2007 12:31:02 AM  Completed consistency check on events4.nsf
11.05.2007 12:31:02 AM  Upgrading the design and data of EVENTS4.NSF...
11.05.2007 12:31:02 AM  Admin Process: Unable to find path to server
11.05.2007 12:31:02 AM  Unable to verify server document network info: Unable to find path to server
11.05.2007 12:31:03 AM  Admin Process: Unable to find path to server
11.05.2007 12:31:03 AM  Unable to find path to server
11.05.2007 12:31:03 AM  Admin Process: Unable to find path to server
11.05.2007 12:31:03 AM  Unable to find path to server
Stack base = 0xb350d4f0, Stack size = 9172 bytes
Fatal Error signal = 0x0000000b PID/TID = 32417/-1286546544
Fri May 11 00:31:04   Running cleanup script
NSD is in progress .................

Please attach the following files to your bug report along with the server log:
Log file                : /notes/data/IBM_TECHNICAL_SUPPORT/nsd_all_Linux_semcrb_05_11@00_31.log
Fri May 11 00:31:21   Running NSD
NSD is in progress .................

Please attach the following files to your bug report along with the server log:
Log file                : /notes/data/IBM_TECHNICAL_SUPPORT/nsd_all_Linux_semcrb_05_11@00_31.log
Fri May 11 00:31:37   Termination is in progress
Fri May 11 00:31:37   Terminating tasks
Fri May 11 00:31:42   Freeing resources
Fri May 11 00:31:42   Termination completed


```

---

### Post by arruah on 2007-05-10
please help me !:mad:

---

### Post by bluebird2129 on 2007-05-14
> [: 131: TOOLS/NLS/-E: unexpected operator
[: 131: tools/nls/-e: unexpected operator
[: 131: tools/nls/-e;1: unexpected operator
.: 1: -e: not found


This is frustrating. I'm getting this error on Feisty and I have installed all of the packages. I know this post is a bit old, but has anyone  successfully installed Notes on Feisty who had this error?

---

### Post by porbas on 2007-05-21
Hi,
In feisty (dapper AFAIR too) /bin/sh links to /bin/dash. Change it to /bin/bash:

```

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

```

---

