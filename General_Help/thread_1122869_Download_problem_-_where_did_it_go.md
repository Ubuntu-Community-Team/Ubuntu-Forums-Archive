---
title: "Download problem - where did it go?"
date: 2009-04-11
forum: General Help
---

### Post by Len Tyree on 2009-04-11
i downloaded the hplip-3.9.2.tar.gz package from sourceforge net to attempt to update my hp printer.   but now i can not find it to get it into
the synaptic package manager to use.

where did it go??

i tried the find command, no luck, the locate command, no luck.
the ls -a i see the .hplip, but not the -3.8.2.tar.gz??

i am not too sharp with downloads.  

the hplip-2.8.7 is loaded into my system now, as shown on synaptic, and anything i try to do to load 3.9.2 says i am running the most recent version.

thanks for any help... len tyree

---

### Post by Diabolis on 2009-04-11
Synaptic will install packages(**.deb**) files, not archived(**.tar**) and compressed(**.gz**) files.

You probably have to extract the contents, cd to the file and the run
./configure
make
makeinstall

---

### Post by djbushido on 2009-04-11
Diabolis is right. Plus, you can't install from file with synaptic, only from the web.
try this command in the folder the file is in - "tar xvzf <your_filename>"
And tell us what files result.
Also, if the older version is installed, why do you need the new one? Why fix what isn't broken?

---

### Post by Diabolis on 2009-04-11
> **djbushido said:**
> Plus, you can't install from file with synaptic, only from the web.

If by web you mean the Ubuntu repository, then you are wrong. You can install any file through synpatic as long as its a .deb.

```
tar xvzf "file name"
```
Will extract and decompress your file, but you can also do it with a **right click**.

---

### Post by djbushido on 2009-04-11
> **Diabolis said:**
> If by web you mean the Ubuntu repository, then you are wrong. You can install any file through synpatic as long as its a .deb.

True, but that's not really the safest thing to do.
Anyway, extract the files and tell us what there is.
If there is a file called "MAKEFILE" and "config" then do this:
```
./config
make
sudo make install
```
Tell us what happens.

---

### Post by Len Tyree on 2009-04-12
for djbushido, tried your method, got this.

len@len-desktop:~$ ./config make 
bash: ./config: No such file or directory
len@len-desktop:~$ sudo ./config make 
[sudo] password for len: 
sudo: ./config: command not found
len@len-desktop:~$ sudo make install hplip-3.8.2.tar.gz
make: *** No rule to make target `install'.  Stop.
len@len-desktop:~$ ./config
bash: ./config: No such file or directory
len@len-desktop:~$ 


the old version is broken, unable to scan photos.

i am doing something not wright...len

---

### Post by Len Tyree on 2009-04-12
for diabolis, tried what you said, got this?

len@len-desktop:~$ tar xvzf hplip-3.9.2.tar.gz
tar: hplip-3.9.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
len@len-desktop:~$ sudo tar xvzf hplip-3.9.2.tar.gz
tar: hplip-3.9.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
len@len-desktop:~$ 

don't know what i am doing...len

---

### Post by Len Tyree on 2009-04-12
could something be wrong with the 'configure' animal on my system?

have trouble using it,  or trying to use it?

len.

---

### Post by nrballard on 2009-04-12
If you're trying to compile from source, you'll probably need to download the build kit first.  Open a console and type:

sudo apt-get install build-essential

...and answer 'y' to any dependency prompts.

Then do the following

cd ~/Desktop/[file].tar.gz
(Firefox downloads files to Desktop by default)

tar zxvf [file].tar.gz
./configure
make
sudo make install


Just out of curiosity, have you tried using the printer out-of-the-box?  Most Linux distributions include drivers for HP printers...

---

### Post by Len Tyree on 2009-04-12
for nrballard

tried it...got this...maybe you can make sense of it.


len@len-desktop:~$ cd -/desktop/hplip-3.9.2.tar.gz     //  this one no good, used '-' not '~'
bash: cd: -/: invalid option
cd: usage: cd [-L|-P] [dir]
len@len-desktop:~$ cd ~/desktop/hplip-3.9.2.tar.gz
bash: cd: /home/len/desktop/hplip-3.9.2.tar.gz: No such file or directory
len@len-desktop:~$ sudo cd ~/desktop/hplip-3.9.2.tar.gz
sudo: cd: command not found


says no such file or directory...  but it is still showing in my downloads folder/whatever?? 

more help please, we're getting there...len.

---

### Post by coffeecat on 2009-04-12
I'm posting from Jauntu Beta, and synaptic tells me that the Jaunty version of hplip is the one you want - 3.9.2. I'm not suggesting you upgrade to Jaunty, but if you can get the Jaunty .deb file onto your desktop, all you have to do is double-click it. You'll probably also need the hplip-data package as a dependency.

Alternatively, enable the backports repository from the settings menu in Synaptic. Version 3.9.2 might be in the Intrepid backports repo - I don't know but it's worth having a look. If you succeed in getting it from backports, you might then want to disable backports to stop all sorts of newer stuff getting through.

While you're about it, why not install the hplip-gui package which doesn't come with a default install.

---

### Post by Diabolis on 2009-04-12
If you plan on switch from Windows to Linux/GNU, it is a good idea that you read a bit of this:
[cd manual]("http://www.ss64.com/bash/cd.html")
```
man tar
man gzip
```

[URL="http://www.cyberciti.biz/faq/run-execute-sh-shell-script/"]
How to run the .sh file in shell script in Linux / UNIX[/URL]

None of what you have tried will ever work if you are not positioned in the same directory of the the file/folder that you want to modify/execute.

[This will work most of the times.]("http://www.google.com/search?hl=en&ei=Eh_iSaO2AsPinQfuw-yiCQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+how+to+install+.tar.gz&spell=1")

---

### Post by djbushido on 2009-04-12
try this:
```
cd ~/Downloads
ls
``` where that second command is LS on lowercase. Output what happens.
Also, if it works, do ```
tar xvzf <your_file>
ls
``` and tell us what happens.

---

### Post by Len Tyree on 2009-04-13
for nrballard

did the build-essentisl thing, returned statement saying it is already the newest edition.
but did not seem to have any effect on what i was doing/trying to do.

could it be possible to reload the part of my system, terminal, or whatever that controls the commands givin to terminal???

the configure don't work
the rm does not work
can't find files using 'ls' or 'locate'

i'm going nuts here....   a little help please, anyone??  thanks, len.

---

### Post by 3rdalbum on 2009-04-13
> **Len Tyree said:**
> 
len@len-desktop:~$ cd ~/desktop/hplip-3.9.2.tar.gz
bash: cd: /home/len/desktop/hplip-3.9.2.tar.gz: No such file or directory

Linux is case-sensitive. That should be an uppercase D in Desktop. Also, you can't change the current directory to a file, that doesn't make any sense.

```
cd Desktop
```

will move your terminal to the Desktop folder.

And you should double-click the .tar.gz compressed archive and extract it onto the desktop as well, so you should end off with a folder called hplip-2.9.2 on your desktop. Then you will need to "change directory" into it, in the same way that you "changed directory" into the Desktop directory.

As you're a new user I'd suggest that you upgrade to Jaunty; it'll be out in two weeks and it has the version of the package that you want. For someone who doesn't know anything about using a terminal, this will be the easiest option.

---

