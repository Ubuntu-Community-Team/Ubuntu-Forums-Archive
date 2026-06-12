---
title: "HARDINFO, Where did it go?"
date: 2009-06-14
forum: General Help
---

### Post by joelop on 2009-06-14
Hi All,

I just downloaded and installed a program ([HardInfo]("http://hardinfo.berlios.de/HomePage")) which comes in a '.package' file; after finding out [how to run it]("http://www.autopackage.org/docs/howto-install/"), I just can't find the program :(, I thought I would find it somewhere in Applications. Has anybody got a clue? (please, bear in mind I'm still new in Ubuntu world) ;)

---

### Post by theozzlives on 2009-06-14
> # Open a terminal and go to the folder in which you saved the package:

[bash@localhost]$ cd YourDownloadsFolder
/home/example/YourDownloadsFolder
[bash@localhost]$ _


Did you copy and past this or did you specify the folder where you downloaded the file?

---

### Post by fooman on 2009-06-14
try running it from a terminal.

open a terminal (applications > accessories > terminal) and simply type:

```
hardinfo
```

then press enter and see if that works.

---

### Post by TheNosh on 2009-06-14
it's under:
     system -> preferences -> system profiler and benchmark

---

### Post by joelop on 2009-06-14
> **theozzlives said:**
> Did you copy and past this or did you specify the folder where you downloaded the file?

Nope, I didn't. I think it didn't ask me for a location... not sure though

---

### Post by joelop on 2009-06-14
> **fooman said:**
> try running it from a terminal.

open a terminal (applications > accessories > terminal) and simply type:

```
hardinfo
```then press enter and see if that works.

Yeah! There it is! But, how comes that I don't have it anywhere in my menus? Not even in: **system -> preferences -> system profiler and benchmark** as *TheNosh* mentions... :( How can I make it appear without having to go to the console?

---

### Post by fooman on 2009-06-14
> **joelop said:**
> Yeah! There it is! But, how comes that I don't have it anywhere in my menus? Not even in: **system -> preferences -> system profiler and benchmark** as *TheNosh* mentions... :( How can I make it appear without having to go to the console?

well,  there is a version available from the repos (look in system > administration > synaptic package manager....search for "hardinfo")...if you had installed it from there,  it would be in the menus like TheNosh said.

btw...you should always check the repos first.  its much easier to search for/install/uninstall software from there.  ;)

---

### Post by joelop on 2009-06-14
> **fooman said:**
> well,  there is a version available from the repos (look in system > administration > synaptic package manager....search for "hardinfo")...if you had installed it from there,  it would be in the menus like TheNosh said.

btw...you should always check the repos first.  its much easier to search for/install/uninstall software from there.  ;)

Well, I first went to Applications / Add/Remove Apps. and I didn't see it there... I didn't know about the synaptic package manager before but you are right, it's there. If I install it now from there, will I have 2 packages in my HD? How can I remove the old stuff?

---

### Post by TheNosh on 2009-06-15
> **joelop said:**
> Well, I first went to Applications / Add/Remove Apps. and I didn't see it there... I didn't know about the synaptic package manager before but you are right, it's there. If I install it now from there, will I have 2 packages in my HD? How can I remove the old stuff?

this should do the trick to COMPLETELY remove the old install
```
sudo apt-get autoremove hardinfo --purge
```

however i don't think it's needed, you could probably just install from synaptic and it should overwrite what you've already installed




[COLOR="White"].[/COLOR]

---

### Post by joelop on 2009-06-15
> **TheNosh said:**
> this should do the trick to COMPLETELY remove the old install
```
sudo apt-get autoremove hardinfo --purge
```[COLOR=White].[/COLOR]

That's weird. I've just done this that you say and I got the message: *'This program was not installed and there was not remove'*. I then checked **Applications / System Tools** and there it was: '**system profiler and benchmark**'... If it's there, it means it's installed...How comes that the command you told me to input didn't find it whatsoever?

Also, even when it's in that location and it woks perfectly, its icon on the menu mentioned above does not look like a proper one. It looks like those icons in Windows when Win doesn't know what program it's tied to.

---

### Post by nikhilk on 2009-06-15
> **joelop said:**
> That's weird. I've just done this that you say and I got the message: *'This program was not installed and there was not remove'*. I then checked **Applications / System Tools** and there it was: '**system profiler and benchmark**'... If it's there, it means it's installed...How comes that the command you told me to input didn't find it whatsoever?


It means that the application was not installed via Ubuntu's package manager. The package manager keeps a database of things it has installed and hence can uninstall whatever it has installed.
You have installed it independently of the package manager, hence it does not have any information about it needed for uninstallation.
If the ".package" you downloaded supports uninstallation use that. Or else you might have to delete the relevant files manually.

---

### Post by TheNosh on 2009-06-15
> **nikhilk said:**
> It means that the application was not installed via Ubuntu's package manager. The package manager keeps a database of things it has installed and hence can uninstall whatever it has installed.
You have installed it independently of the package manager, hence it does not have any information about it needed for uninstallation.
If the ".package" you downloaded supports uninstallation use that. Or else you might have to delete the relevant files manually.

thats odd, because thats how i got rid of opera 10 beta to switch back to 9.64 (cause of issues with hulu) and that was installed from a .deb

then i reinstalled 9.64, again from a .deb, but despite not being installed from repos it still shows up as installed in synaptic

---

