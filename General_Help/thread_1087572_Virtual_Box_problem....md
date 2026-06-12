---
title: "Virtual Box problem..."
date: 2009-03-05
forum: General Help
---

### Post by Chaosleet on 2009-03-05
Alright, first off I'll admit that I'm a linux noob. I have VirtualBox installed on my dedicated server that's running Ubuntu Desktop and I am controlling it through NX.

VirtualBox is installed fine, but when I try and run Windows from it I get this error:

[IMG]http://i42.tinypic.com/16gisfr.jpg[/IMG]

I have tried what it said in blue, and this is the error I get:
```
admin@ks359837:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                            Opening /proc/modules: No such file or directory
 *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
```

And in the log file it says:
[IMG]http://i39.tinypic.com/33dikno.jpg[/IMG]

From what I know already, I think it means that my version of Ubuntu is using an unsupported version for VirtualBox or something, not sure at all though.

Any help on the matter would be really appreciated, as I'm running out of time for my dedi :)

Cheers.

---

### Post by kestrel1 on 2009-03-05
Did you get the download from the official site? [http://www.virtualbox.org/](http://www.virtualbox.org/)
Is you username in the vbox users group?

---

### Post by Tibuda on 2009-03-05
> **kestrel1 said:**
> Is you username in the vbox users group?

If it is not in the group, you can add it by running adduser as sudo in the terminal:```
sudo adduser $USER vboxusers
```

---

### Post by Chaosleet on 2009-03-05
Alright thanks guys.

I added my user to the vbox group and I still get the error.

And yeah I downloaded it from the official site :)

Thanks for the help so far.

---

### Post by kelvin spratt on 2009-03-05
try this in the term 
 sudo vbox_build_module

---

### Post by kestrel1 on 2009-03-05
Have you tried re-installing VirtualBox. It looks as though something has not installed correctly. You may want to remove it first.
I think this will work, off the top of my head:```
sudo dpkg -r VirtualBox
```

---

### Post by Chaosleet on 2009-03-05
kestral1, when I run that command I get this:

```
admin@ks359837:~$ sudo dpkg -r VirtualBox
dpkg - warning: ignoring request to remove virtualbox which isn't installed.
```

Says it isn't installed, but it is, as it appears in the System Tools menu and I can run the program but just not run any virtual OS with it :-k

---

### Post by kestrel1 on 2009-03-06
OK, I have just had a look & it should be```
sudo dpkg -r VirtualBox-2.1
```
Sorry about that, but I wasn't on my usual machine at the time of writing.

---

### Post by col48 on 2009-03-08
I'm not sure if this is the right place for this, bear with me, but it did seem related to this thread.

I have a more basic puzzle.  I have virtualbox2.1 installed and my id is in the user group but when I try to run virtualbox in Terminal (as me) it says I need to install virtualbox-ose.  I tried that in Synaptic and in the process it uninstalled virtualbox.  Then when I try to run virtualbox it denies all knowledge of it.

So I haven't got as far as setting up a virtual machine yet.

What's going on?

---

### Post by kestrel1 on 2009-03-08
VirtualBox OSE is the Open Source Edition & is available in the reppo's. 
If you want to use the OSE version then to install it all you need do is type the following in a terminal:```
sudo apt-get install virtualbox
```
Then to run it from the terminal type```
virtualbox
```
However I suspect that you downloaded & installed the closed version from Sun, which is the way I use it. That way you install the deb file from their website & if you want to run it from the terminal you would type:```
VirtualBox
```
Notice the capital 'V' & 'B' in the words. that is what makes the difference.
If you have uninstalled it I would sugest re-installing the latest version from Sun Version 2.1.4 at this time.

---

### Post by col48 on 2009-03-09
Thanks, kestrel1.

You've got it spot-on.

I am still not 100% at home with seeing the two Cases as distinct.  Too many years of Windows to blame!  But it'll come, I'm sure.

---

### Post by kestrel1 on 2009-03-10
I am afraid you sometimes have to think outside of the box with Linux, but it is more logical when you get used to it.

---

