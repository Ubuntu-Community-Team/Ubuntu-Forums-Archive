---
title: "How to get ndiswrapper into Synaptic package manager?"
date: 2005-02-03
forum: Desktop Environments
---

### Post by Chris in Texas on 2005-02-03
ok,

Trying to set up my wireless card and in the process I am doing my best to install ndiswrapper.

I tried to use the reload then search functions in the Synaptic manager, but I cannot find the ndiswrapper anywhere.  I'm sure I'm doing something wrong and it's probably an easy fix.  Unfortunately I'm new to Linux and it's still a fairly foreign language to me.

I had version 0.12 of Nsidwrapper and tried it from my desktop, a floppy, then the USB jumpdrive.  None of these seem to help.  Perhaps I'm placing the file in the wrong place. I went to the Ndiswrapper website and then downloaded v 1.0, still no luck.  I've read everything on here and on their website and it seems like it should be obvious from the descriptions I've read.  Unfortunately it's not working that way.

Any help or hints?

---

### Post by poofyhairguy on 2005-02-03
[QUOTE=Chris in Texas]

I tried to use the reload then search functions in the Synaptic manager, but I cannot find the ndiswrapper anywhere.  I'm sure I'm doing something wrong and it's probably an easy fix.  Unfortunately I'm new to Linux and it's still a fairly foreign language to me.
[/QUOTE]

[https://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](https://www.ubuntulinux.org/support/documentation/howto/ndiswrapper)

Make sure you enable the universe and multiverse and restricted before you try to install it.

Do that by following this step:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by bobmitch on 2005-02-03
I`m a linux/ubuntu noob myself, but I got it working the other day - here's how (roughly):

In the package manager, install linux 386 headers, and gcc.
Unzip/tar ndiswrapper source to a folder.
cd into folder and:  'sudo make'
then: 'sudo make install'

Hopefully ndiswrapper will now be installed - try 'ndiswrapper -l' at the command prompt, you should get some feedback on any drivers installed (none at this point).

Let me know if you get this far and then need any pointers.   These instructions are vague, but like I say, I`m pretty new at this, but can be more detailed if you need.

---

### Post by Chris in Texas on 2005-02-03
> Do that by following this step:    [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)	  Today 12:15 PM 

Ok, I did this step and when I typed the *$  sudo apt-get update* I recieved nothing but error messages.

The messages included:

[I]Failed to fetch...

Couldn't stat source package list...

W: You may want to run apt-get update to correct these problems
E:  Some index files failes to download, they have been ignored, or old ones used instead.[/I]

Do I need an internet connection for this step?  If so that is a no go.  That's why I'm setting up the wireless connection on my laptop.

Thanks,

Chris

---

### Post by Chris in Texas on 2005-02-03
Ok, still working on this and not having much luck.

I've enabled the universe, multiverse, and restricted.  I've gone to the synaptic package manager and reloaded, searched and done just about everything I can think of and the file still does not show up.

I've placed the files on the desktop, I've had them on my flash drive, I've written them to a CD-ROM and I even tried to manually move them into /var/cache/apt/archives/ with the rest of those files, but it says I don't have permission.

No matter what I do I cannot see these files anywhere.  What am I doing wrong?

I know I need to do this step:  [https://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](https://www.ubuntulinux.org/support/documentation/howto/ndiswrapper) , but I can't do that if I can't find the file.

I've tried this with both the tar.gz file and the .deb file.  Nothing is working.

Please help,

Chris

---

### Post by Chris in Texas on 2005-02-03
> In the package manager, install linux 386 headers, and gcc.  Unzip/tar ndiswrapper source to a folder.  cd into folder and: 'sudo make'  then: 'sudo make install' 

I also tried this and it was a no go.  When I get into the console to do it I'm told that there is no target specified and no makefile found.

This is getting a bit frustrating.  Mainly because I know it has to be something simple that is eluding me.

---

### Post by bobmitch on 2005-02-04
Sounds like you downloaded the binary version.  Visit the ndiswrapper sourceforge homepage and download the linux source version.

After dowloading that and unzipping/tarring, you should be able to do a 'sudo make' and 'sudo make install' no problem  - providing you have the linux headers for your kernel version installed along with gcc. 

The only downside to doing it this way is if you decide to upgrade your kernel - you will probably have to recompile and reinstall this app. (Think the module created with modprobe is pointing at specific kernel objects).  No biggie really.

I found I had problems with the ndiswrapper tools from the repositories, which is why I did it this way - seemed to be more compatible with my hardware.  (A wg311v2 from netgear).

---

### Post by Chris in Texas on 2005-02-04
> Sounds like you downloaded the binary version. Visit the ndiswrapper sourceforge homepage and download the linux source version. 

Went to their website and dowloaded v 1.0, when that didn't work I tried the bleeding edge version.  They both extract fine, they just don't do anything after that.  I compiled the kernel exactly like the guide suggested,I also tried it with the kernel patch, no luck.  

Here's a thought, where specifically do I need to save this file?  I've been saving it on either  */home/chris/desktop/ndiswrapper*  or */home/chris/ndiswrapper*.

I tried putting it in with the other packages, but I was told I don't have permission.  Could this be my problem?  Maybe I'm putting it somewhere it doesn't belong.

Thanks again for all the help.

Chris

---

### Post by bobmitch on 2005-02-04
[QUOTE=Chris in Texas]Went to their website and dowloaded v 1.0, when that didn't work I tried the bleeding edge version.  They both extract fine, they just don't do anything after that.  I compiled the kernel exactly like the guide suggested,I also tried it with the kernel patch, no luck.  

Here's a thought, where specifically do I need to save this file?  I've been saving it on either  */home/chris/desktop/ndiswrapper*  or */home/chris/ndiswrapper*.

I tried putting it in with the other packages, but I was told I don't have permission.  Could this be my problem?  Maybe I'm putting it somewhere it doesn't belong.

Thanks again for all the help.

Chris[/QUOTE]

Ok, so you downloaded the source tarball.
You saved this somewhere (doesn`t matter where)
You opened a terminal and cd'd to where you saved the file,
You untarred/unzipped it.  ( 'tar -xvvzf ndiswrapper.tar.gz'  or whatever)
You then typed 'sudo make'
You then typed 'sudo make install'

If you did this, ndiswrapper should be installed in the appropriate binary folder and available on the standard path - eg.  you should be able to just type 'ndiswrapper' and it will give you feedback, rather than 'command not found'

If you didn`t follow the guide above, let me know where you differed.  The method I described should work.   If there are errors regarding the make and make install parts, you probably dont have all the kernel headers or gcc packages installed from the cd repository.

Keep trying - if I can do it, anybody can. :D

---

### Post by Chris in Texas on 2005-02-04
Ok, I finally got the Ndiswrapper installed.

Apparently it was something simple.  I think it part the way I was uncompressing the file, and also when I saw the 'cd" command I mistakenly just hit cd and didn't actually change into the actual directory I needed.  Guess I need to learn more basic commands.  Luckily I had an old RedHat manual so I could figure out what some of them meant.  Told ya I was a noob at this.

I was able to get the drivers installed.  Now I just need to get the wireless card working.

Thanks again for the help and advice

Chris

I'm sure I'll have some more questions in a few minutes.  I feel like a grade school kid trying to take a physics final.

---

### Post by Chris in Texas on 2005-02-04
Bobmitch,

Since you're using a netgear card, did you have any problems getting power to the card?

Everything is installed but the card has no power.  I've tried doing a gedit on the config to see if I can turn the power on, but no luck.  It kicks me out and won't even let me into the file.

I did a quick search on the boards but didn't turn up anything.  I'll see if I can dig a little deeper.  I'm sure I'm not the first person to have this problem.

---

### Post by bobmitch on 2005-02-05
[QUOTE=Chris in Texas]Bobmitch,

Since you're using a netgear card, did you have any problems getting power to the card?

Everything is installed but the card has no power.  I've tried doing a gedit on the config to see if I can turn the power on, but no luck.  It kicks me out and won't even let me into the file.

I did a quick search on the boards but didn't turn up anything.  I'll see if I can dig a little deeper.  I'm sure I'm not the first person to have this problem.[/QUOTE]

Sounds like your card is a USB?  Mine is a pci, and so is getting power no problem anyway.   If your adapter is USB and is getting no power, I`d suggest the problem is more hotplug related.  I`m new to this linux lark as well, but hopefully someone can provide more info.

---

