---
title: "can someone simplify this install process for me?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by maddbaron on 2006-07-29
I am trying to install voice and video to gaim using gaim-vv I downloaded the tarbell to my home folder like it said but i dont know what to do next, should i move the tarbell to the gaim folder? it says make and install but i am not sure how.

here are the instructions:
> 1) Download and save the gaim-vv-1.2.0 tarball to your home directory
2) Extract it by doing tar xzf gaim-vv-1.2.0.tar.gz
3) cd gaim-vv-1.2.0
4) ./configure && make
5) su
6) make install

thanks in advance

---

### Post by ardchoille on 2006-07-29
> **maddbaron said:**
> I am trying to install voice and video to gaim using gaim-vv I downloaded the tarbell to my home folder like it said but i dont know what to do next, should i move the tarbell to the gaim folder? it says make and install but i am not sure how.

here are the instructions:


thanks in advance

I would advise to download it to a ~/Documents/Downloads folder or something like that (maybe need to create this path first) to keep all downloads seperate. Maybe even ctreate a "testing" folder or "compiling" folder to do all compiling in. But, as for the rest, that is what I normally have people do when they compile an app.

Make should be run as user because it takes care of compiling the app and any needed files. Make install needs to be run as root (sudo) because make install simply copies the needed files to the system.

---

### Post by H.E. Pennypacker on 2006-08-03
madbarron, I'll explain the instructions in simple English, because often times, programmers assume people understand what they're telling them.

First, let me begin by saying that what you have downloaded is not an installer.  An installer, from the perspective of Windows, is something that takes care of installing applications for us.  As Windows users, we always took for granted the simplicity of installing applications.  Everything was being done for us automatically.

With Linux, many programmers will not give you an installer (remember, the installer is what installs everything for you automatically with only a few clicks).  This is because some distributions don't accept installers provided by other distributions.  Some distributions (distros) share a type of installer, but many times, they don't.

That means these programmers (the people who create software) have to create an installer for all distributions, which is something that would take them a long while.  Instead, they expect the user (the person downloading the files) to do things on their own.

So, what you've downloaded is actually the LANGUAGE in which the software was written in.  But you must still translate to the computer that language.  This is what those instructions do.  This paragraph may not make sense.  Simply proceed.

Follow these instructions:

1.  Assuming the file you downloaded is in your /home directory, create a new directory that is only for downloads.  Place it in your /home directory.  In the end, it should say something like /home/downloads.

2.  Place the downloaded file into that directory.

3.  Start the terminal, and *cd* into that directory.  If you don't know how to use cd (this does not stand for cd-rom), read a guide on how to use the terminal.

4.  Type *./configure*.

5.  Type *make*.

6.  Type *checkinstall*.  You should have checkinstall installed before you can use it.  Read more about checkinstall via Google to learn more about it.

I am not quite sure if I ever had any luck doing this myself.  Most of the time, something goes wrong.  This a problem caused by too many Linux distributions not listening to eachother.  Again, I don't expect you to understand what I am talking about.

---

