---
title: "How do you get details of installs in Software Center?"
date: 2010-01-21
forum: Desktop Environments
---

### Post by Pro_D on 2010-01-21
In previous versions of Ubuntu as well as the current version package manager there is a way to get details about the installation process, beyond the progress bar.  I haven't figured out how to bring this up in the new Software Center though.

I am particularly curious right now as an installation process seems stalled at the moment and since I can't figure out how to bring up the details, if it's possible, so I can't tell why it's stalled...  I have figured out that you can cancel if it's still downloading but once the download finishes you are stuck with nothing more than the progress bar to figure out whats up.

---

### Post by marin123 on 2010-01-21
it's unpacking files and installing and that could take some time... depending on the size of the application it can take a few minutes.. just wait for 5-10 mins, it should be installed (i never had problems with software center so i dont think it froze)...

---

### Post by howefield on 2010-01-21
What's the application you are installing ?

---

### Post by Pro_D on 2010-01-23
I think I know what happened, mostly from doing something resembling 'dpkg -a' from having interrupted the process before.  I gave it about 35 minutes more and then had to shut off the computer and so an installation was interrupted.

Anyway I was installing adobe-flash.  Having watched it from the details of the package manager the internet connection was likely interrupted during the download and so the package manager stalled.  I have a flaky internet connection and long downloads sometimes get interrupted if I don't make sure that the modem (crummy qwest dsl modem) is close to overloaded (it's NAT sucks but I have to leave it on or it won't talk to the internet - oversimplified).

I suppose I may need to figure out how to add something to the wishlist and request a details screen for installs in Software Center.  I actually did pick up a few things having watched those details go by.  It's fine to hide details but sometimes you just want to see (and more rare, need to see).

---

### Post by marin123 on 2010-01-23
can you simply search for programs in software center and then install it in synaptic? synaptic shows all details.. or if you want to you can use aptitude (apt-get)...

---

### Post by carusoswi on 2011-01-16
I know this is an old thread, but what is causing the install to stall.  I am trying to install RawTherapee from the Software Center.  It seems simple enough.  Why is it stalling?
Any help would be appreciated.  I am running a fresh install of 10.10 Desktop

Caruso

---

### Post by Krytarik on 2011-01-16
> **carusoswi said:**
> I know this is an old thread, but what is causing the install to stall.  I am trying to install RawTherapee from the Software Center.  It seems simple enough.  Why is it stalling?
Any help would be appreciated.  I am running a fresh install of 10.10 Desktop

Caruso
I would try to install the package(s) with Synaptic, under "System -> Administration", it should give you more output, and is generally more transparent.

---

### Post by carusoswi on 2011-01-23
> **Krytarik said:**
> I would try to install the package(s) with Synaptic, under "System -> Administration", it should give you more output, and is generally more transparent.

Thanks.  I tried it.  It worked.  But why have two routes to install the same software.

I do not understand.

Thanks again for your reply.

Caruso

---

### Post by Frogs Hair on 2011-01-23
The Synaptic package manager can be used to build and repair packages which the USC cannot , It also displays a detailed list of individual dependencies . [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)

---

### Post by Krytarik on 2011-01-23
There are even some more ways, e.g. the command "apt-get" at the command line, upon which the package managers are build, and some other GUIs may also exist, have used some back in Gutsy 7.10.;)

I don't use Ubuntu Software Center at all, it's more of a we-decide-for-you way, it installs dependend packages without asking, and may even not install the correct app package, e.g. in the case of EasyTag.

---

