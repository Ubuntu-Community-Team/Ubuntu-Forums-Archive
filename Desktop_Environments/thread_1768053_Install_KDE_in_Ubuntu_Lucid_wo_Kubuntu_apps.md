---
title: "Install KDE in Ubuntu Lucid w/o Kubuntu apps"
date: 2011-05-26
forum: Desktop Environments
---

### Post by blauendonau on 2011-05-26
Hello! I have Ubuntu 10.04 Lucid Lynx. I'm interested in installing KDE alongside GNOME - I like both almost equally from previous experience and like to have some choice. :P I know it's possible to use

```
sudo apt-get install kubuntu-desktop
```but that would also install various Kubuntu-default applications such as KOffice, which I'm not interested in. (I know I can simply uninstall them individually but I'm looking for something more convenient.) Is there a way to install just a base package without (or with a minimum of) KDE applications? Maverick has packages called "kde-base" and "kde-core" that provide this functionality but they apparently are not available in Lucid when I try apt-get in a terminal. Any suggestions?

Thanks!

---

### Post by ivanovnegro on 2011-05-26
Are you sure, they are not available, thats exactly what I wanted to suggest you, to install kde-base?

---

### Post by blauendonau on 2011-05-26
> **ivanovnegro said:**
> Are you sure, they are not available, thats exactly what I wanted to suggest you, to install kde-base?

I just tried it again. "sudo apt-get install kde-base" results in "E: Couldn't find package kde-base". It worked fine in Maverick, are the package repositories different in Lucid ?

EDIT: Tried installing the other package, "kde-core", but also without success.

---

### Post by marl30 on 2011-05-26
[LEFT]Koffice doesn't get installed with KDE desktop. The best you could do is uninstall the packages you don't need after installing KDE desktop. Make sure to add the Kubuntu backport ppa so you can have the latest KDE (4.6.3).
[/LEFT]

---

### Post by blauendonau on 2011-05-26
> **marl30 said:**
> [LEFT]Koffice doesn't get installed with KDE desktop. The best you could do is uninstall the packages you don't need after installing KDE desktop. Make sure to add the Kubuntu backport ppa so you can have the latest KDE (4.6.3).
[/LEFT]


Thanks! Okay, that's what I might end up doing. What's the command for installing the backport PPA once again?

---

### Post by marl30 on 2011-05-26
> **blauendonau said:**
> Thanks! Okay, that's what I might end up doing. What's the command for installing the backport PPA once again?

Add these repositories:```
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) lucid main 

 deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) lucid main 
``````
ppa:kubuntu-ppa
```

---

### Post by blauendonau on 2011-05-26
Thanks marl30! I just pushed the trigger on the install, see how it works. I guess it's not too difficult to uninstall the packages I don't need. (BTW, out of curiosity, what office program does come default with kubuntu-desktop? OpenOffice?)

---

### Post by ivanovnegro on 2011-05-26
> **blauendonau said:**
> Thanks marl30! I just pushed the trigger on the install, see how it works. I guess it's not too difficult to uninstall the packages I don't need. (BTW, out of curiosity, what office program does come default with kubuntu-desktop? OpenOffice?)

On 10.04 yes, Open Office, so you have it yet installed.

---

### Post by blauendonau on 2011-05-26
I've installed the package successfully, but there is a minor problem: in GNOME, the cursor turns to the "Oxygen" style when in Firefox, but switches to the standard GNOME cursor when moved outside of firefox. Can anyone help correct this?

---

### Post by marl30 on 2011-05-26
> **blauendonau said:**
> I've installed the package successfully, but there is a minor problem: in GNOME, the cursor turns to the "Oxygen" style when in Firefox, but switches to the standard GNOME cursor when moved outside of firefox. Can anyone help correct this?
That's part of the issue with running two DE in one install. You could change the cursor to the Gnome default from within KDE.

---

### Post by blauendonau on 2011-05-26
Heh, I tried that, and then the GNOME cursor became Oxygen system-wide, even after a few log-ins and -outs. Weird.

Anyways, I decided to remove KDE for the moment because it ruined the GNOME fonts and was running like a hog - taking up 2x more RAM than GNOME and causing the hard disk to click like crazy. Is the new KDE always this resource-demanding?

---

### Post by marl30 on 2011-05-26
> **blauendonau said:**
> Heh, I tried that, and then the GNOME cursor became Oxygen system-wide, even after a few log-ins and -outs. Weird.

Anyways, I decided to remove KDE for the moment because it ruined the GNOME fonts and was running like a hog - taking up 2x more RAM than GNOME and causing the hard disk to click like crazy. Is the new KDE always this resource-demanding?

KDE 4.6.3 in Kubuntu 11.04 isn't as resource hungry as previous KDEs. That is one of the reasons why switching form Gnome since 11.04 was easy for me.

---

### Post by blauendonau on 2011-05-26
> **marl30 said:**
> KDE 4.6.3 in Kubuntu 11.04 isn't as resource hungry as previous KDEs. That is one of the reasons why switching form Gnome since 11.04 was easy for me.

That's good to know if I ever upgrade - although my limited experience with Natty as seen too many bugs for it to be a viable working system. I'm planning to stick with LTS releases. I don't like Unity, so I might jump ship over to Kubuntu 12.04 whenever it comes out.

Even in Lucid though, 600+ MiB is a lot of memory to devote to KWin and friends. I didn't even have most of the desktop effects turned on. Kubuntu's system requirements say 512 MiB is "recommended", but even twice that amount wouldn't be enough to operate comfortably, in my experience.

---

### Post by ivanovnegro on 2011-05-26
> **blauendonau said:**
> That's good to know if I ever upgrade - although my limited experience with Natty as seen too many bugs for it to be a viable working system. I'm planning to stick with LTS releases. I don't like Unity, so I might jump ship over to Kubuntu 12.04 whenever it comes out.

Even in Lucid though, 600+ MiB is a lot of memory to devote to KWin and friends. I didn't even have most of the desktop effects turned on. Kubuntu's system requirements say 512 MiB is "recommended", but even twice that amount wouldn't be enough to operate comfortably, in my experience.

Maybe you should try a fresh install of Kubuntu 11.04 rather than adding the KDE desktop on top of Ubuntu, I was never a fan of things like this, its cluttering your desktop.
Kubuntu 11.04 is a really good release and for me less buggy as the Unity desktop.
Yes it needs more RAM but not too much IMO, dont forget its KDE, 700 MB is normal on my machine, thats quiet acceptable I think for KDE.
If you think its too much and even on Lucid too much I recommend you to try Xubuntu, also no Unity issues and on my machine it consumes about 400 MB when Im browsing the web, listening to music etc.

Your experience with Kubuntu was of course with Lucid, not worth the try in my opinion, I found it laggy, slow, buggy and resource hungry and this KDE version on Lucid just was not/is not good. If you want a really good KDE experience, KDE 4.6 is the way to go, 4.6.2 on Kubuntu and with backports even 4.6.3, what makes it even better.

---

### Post by SeijiSensei on 2011-05-26
One way to install a fairly limited set of KDE applications is to install simply dolphin, the file manager, and let apt get the needed dependencies.

That said, I'd still suggest installing Kubuntu 11.04 rather than some funky dual DE approach.

I usually install synaptic on top of KDE; that will get all the major GNOME libraries automatically as well.  (KPackageKit has come a long way in the past year or so, though, making synaptic less valuable than before.)

---

### Post by blauendonau on 2011-05-26
I tried Xubuntu 11.04, but it was noticeably slower than even GNOME In Maverick or Lucid. I had to go back to 10.04 after finding bugs with Natty that made it almost unusable, the biggest of which prevented the computer from shutting down. In the interests of stability and convenience I stick to LTS releases now.

I've run dual and even triple DEs under one hood before with out problems, in general I like to have as much variety as possible so I don't get bored. It just seems Lucid is giving me more hitches. I guess when it comes time to upgrade to 12.04LTS I'll do a fresh Kubuntu install. Unless Unity is made drastically more productive and customisable it's not an attractive option for me.

---

