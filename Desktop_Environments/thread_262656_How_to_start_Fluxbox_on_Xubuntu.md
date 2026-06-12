---
title: "How to start Fluxbox on Xubuntu?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by snakyjake on 2006-09-22
I need some help installing Fluxbox on my Xubuntu machine.  The problem is I cannot (or do not know how) to start Fluxbox.

I installed Fluxbox version 1.0rc2 from source.  I did ./configure and make.  

What am I supposed to do next?

I'm also new to Linux and hope someone can explain what and why.  I also want to install from source, not from a package. 

Most of what I find is specific to versions, distributions, or specific problems.  I hope this thread will be generic enough to help all of those that come across this same issue.

I tried using this [site]("http://ubuntuforums.org/showthread.php?t=116759"), but couldn't write to the file in step 8 as root.

Some sites mention folders for "fluxbox" or "session", but I do not see any in /etc/gdm or /usr/local/bin or /usr/share/xsessions/fluxbox.desktop.

I'm not sure why there are multiple websites that explain how to install/start Fluxbox differently, and yet I still can't get it to work.  Please help.

I also want to make sure I'm getting the real Fluxbox, not a hybrid Fluxbox+Xubuntu.  Fluxbox's advantage is being light weight, so I don't want to load Xfce+Fluxbox.  If I need to clean my machine, that's okay.

Thank you,

Jake

---

### Post by croak77 on 2006-09-22
After make, do 'sudo make install'. Or you can just use the fluxbox that's in the repo.

---

### Post by snakyjake on 2006-09-25
I did the "make install".  But in step 9 [(site)]("http://ubuntuforums.org/showthread.php?t=116759")
the fie "fluxbox-desktop" is looking for "Exec=/home/(username)/.fluxbox/startup".  I went to my /home/jake folder and typed "ls -a", the file does not exist.  

When I rebooted, the Xubuntu GDM came up, I chose Fluxbox, and proceeded with login.  An error message was returned "xsession unable to launch.../home/jake/.fluxbox/startup not found".

The ./configure, make, and make install completed without error.

Thanks again for the help.

Jake

P.S. Venting a bit...None of this really makes any sense to me.  The how-to seems to be broken or no longer applies to this version.  The learning process is difficult and the links to information seem like ether (thank God for the people on ubuntuforums.  Am I in the minority with this difficulty?  What can I do to make these types of issues easier?

---

### Post by snakyjake on 2006-09-26
After searching the Net, I came across another way to configure Fluxbox.  Here's a summary of what I've done to install Fluxbox.

1. Went to fluxbox.org and download [fluxbox-1.0rc2.tar.gz]("http://prdownloads.sourceforge.net/fluxbox/fluxbox-1.0rc2.tar.gz")

2. ```
tar -zxfv fluxbox-1.0rc2.tar.gz
```

3. ```
./configure
```

4. ```
make
```

5. ```
make install
```

6.  

```
vi /usr/share/xsessions/fluxbox.desktop
```

Add to that file the following information:

```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configureable low resource X11 Window Manager
Exec=/usr/local/bin/startfluxbox
Terminal=False
TryExec=/usr/local/bin/startfluxbox
Type=Application
```

There might be a step that I don't have mentioned because I tried 100 different things to finally get it to work.  If anyone else gets lost, please open up a new thread, and send me a PM.

Thanks everyone.

---

