---
title: "Can't compile auctex (LaTeX not found)"
date: 2010-04-27
forum: Education &amp; Science
---

### Post by 5au1 on 2010-04-27
Hi,

A couple of days ago I installed Texlive 2009. Since the installation guide says (but doesn't explain)  that it can be installed for a dual boot system, I installed in the following location: /media/Documentos instead of the default /usr/local. After changing the .profile file I was able to work with tex files

The next step was to build auctex, however I couldn't do that because latex wasn't found. I followed the instructions posted in [http://http://ubuntuforums.org/showthread.php?t=1406003]("http://http://ubuntuforums.org/showthread.php?t=1406003") without success. More over, after changing the environment file I wasn't able to run latex :confused:

Is there a way to tell auctex where the required files are?

Thanks in advance

P.S. I tried different directories for the option
```
./configure --with-texmf-dir=/DIR
```

---

### Post by 5au1 on 2010-04-28
Hi again,

Today I reinstalled Texlive with the following command:
```
sudo perl install-tl -gui
```
With that I was able to create symlinks which in turn allowed me to run the first two commands for the auctex installation with no problem. 
```
sudo ./configure --with-texmf-dir=/media/Documentos/texlive/2009/texmf
sudo make
```
However when I ran the last command (make install) I got this
```
/tex/latex/preview//usr/bin/install -c -m 644 preview.dvi 
/usr/bin/install: missing destination file operand after «preview.dvi»
Try `/usr/bin/install --help' for more information.
make[2]: *** [install-texmf-doc] Error 1
```

Any suggestions?

---

### Post by hubie on 2010-04-30
The problem with that install statement is that you're telling it to install the file preview.dvi somewhere, but you're not telling it where.  Of course "you" here is your script, not you...

A lot of times problems when running "make install" result from doing that not from a privileged account.  Are you running "make install" or "sudo make install"?

---

### Post by 5au1 on 2010-05-01
I'm running all the commands with sudo. Now, the error I got was because the path I stated wasn't the correct. After changing it to /media/Documentos/texlive the error disappeared. Still Auctex is not installed :confused:

Looking in the output of sudo make install I've found this warning message:
```
Warning: Cannot update ls-R database in /media/Documentos/tex/latex/preview/../../..
```

At this point I've run out of ideas, more over I tried different options for the command sudo ./configure that now I have copies of the auctex files in the wrong places. So the questions are: 
1. How can I erase all the auctex files installed in my previous tries? and
2. How can I solve this warning message?

---

### Post by hubie on 2010-05-03
To remove them, you could try running make clean, or make distclean to see if that does it for you.  If you installed several different variants you could try running .config with those options first, then run make clean to see if it removes it.

That is an odd directory path you show in your warning message.  It climbs all the way down to the preview directory, then climbs back up three directories to end up in /media/Documentos

You can try running ```
sudo texhash
``` and (though this most likely is unrelated to the issues you are having) ```
sudo updmap
``` and see if that helps.

---

### Post by 5au1 on 2010-05-07
Hi,

Finally I make it work. The trick was to install Texlive in the default location (i.e. /usr/local/) and then compile Auctex and Reftex (both without problems). After that, I moved the Texlive folder to the location I was trying to install in the first place, /media/Documentos, and created a symlink. Now I can work with tex files in Ubuntu and win.

A minor problem in win is that I don't have any icons, but that's ok since I spend most of the time in Ubuntu ;)

Cheers

---

