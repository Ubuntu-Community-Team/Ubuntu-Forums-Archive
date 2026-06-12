---
title: "Loss After Upgrade"
date: 2011-10-01
forum: Desktop Environments
---

### Post by peacefulvet on 2011-10-01
I have updated from ubuntu 2.6.32.33 generic-pae
to
ubuntu 2.6.32.34 generic-pae

I was prompted to do this from the update manager, upon restart I have lost everything in my home folder, all my favorites and settings.  I just can't believe that.  I have updated many times before and this has never happened.  Am disappointed as I believe in Linux.  I suspect all this information is saved somewhere, maybe the lost and found file, but I can't access it accept in root and I'm not able to log into root.

---

### Post by Krytarik on 2011-10-01
Sorry, man, but I don't believe that a kernel upgrade can cause this!

And this indicates to me that you may have messed a bit too much with the root account:
> **peacefulvet said:**
> but I can't access it accept in root and I'm not able to log into root.
Which is capable to make you lose access to your home directory, namely:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Can you find your files in "/home/USERNAME", if you browse it as root?

If yes, try this:
```
sudo chown USERNAME:USERNAME -R /home/USERNAME
```Or do you possibly have an encrypted home directory?

Hope that helps!

---

### Post by peacefulvet on 2011-10-02
I can't log into root, I have never tried to log into root until this problem occurred. In earlier installs, you are asked to create a root password, but with these later installs it just asks you to create a user name and password. Its strange how that link talks about firefox.  I wanted to have two firefox profiles, so I created a second profile.  When I discovered the second profile would not do what I wanted it to, i deleted it.  Then when I restarted the computer as it asked me too after the upgrade, everything was gone. Wasn't a great loss, it was only a week old install and my favorites were backed up.  I tried the string you suggested, it didn't work, but, I wasn't logged in as root either, so.  Thanks though.

---

### Post by Krytarik on 2011-10-02
- I don't think that the Firefox profile thing is related to the wider issue, but thanks for pointing that out.

- You did get that you need to replace every occurrence of "USERNAME" by your actual user name, right?

- One more question to add to those in my initial reply: Do you get any error messages when you log in? But you would have already mentioned that, right?

Here is more info about using "sudo" and "gksudo":

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In short:

- Running the given command with "sudo" is sufficient.

- You can open Nautilus to easier browse the files/dirs with:
```
gksudo nautilus
```But if you already accepted your apparent loss of files/settings, just say it. Then we can stop here.

---

### Post by lisati on 2011-10-02
In Ubuntu, logging in as root is disabled by default, partly to help avoid this kind of problem.

Please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by peacefulvet on 2011-10-02
Thanks gksudo nautilus allowed me to get into lost and found, there's nothing there and also thanks for the explanation for not being able to log into root.

My favorites where all backed up and the only thing in my download file were install files, so no big deal, I can live with the loss, so we can quit, it is just weird that this happened.  I've been using linux for years and never had an update do this before, maybe it was an error on my hard drive, Is there a chkdisk for linux.

I want to say that Linux is really cool.  You can install it on almost any computer and have everything work without having to search for drivers, it's usually faster and more secure than windows and when updates come, you rarely have to restart your computer.  You can do almost anything in linux than you can in windows.  You could probably do any windows function in linux with some research and work, AND it's free.

I just have to say that each new version seems to be less functional, though better looking.  I installed Ubuntu 11 and said, what is this, I can't use this, and found the older 10 and put that on.  I can understand the need for security updates, but if it isn't broken don't fix it and if it works ok, leave it alone.  We like the volkswagon just the way it is.  Don't have to be like everybody else and have upgrades just to have upgrades. Linux is supposed to be different.  Be good, be different. Thanks

---

### Post by Krytarik on 2011-10-02
> **peacefulvet said:**
> Thanks gksudo nautilus allowed me to get into lost and found, there's nothing there...
Well, I wasn't referring to that location *at all*, but anyway... ;-)

---

