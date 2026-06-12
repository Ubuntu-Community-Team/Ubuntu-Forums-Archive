---
title: "Is it wise to remove the evolution package"
date: 2005-02-12
forum: Desktop Environments
---

### Post by nanaban on 2005-02-12
Hi all, I just installed Ubuntu and I have to say I like it a lot.
I use Thunderbird as my mail client, is it wise to remove evolution?
The ubuntu-desktop package depends on it, so it will be removed as well...

TIA!

---

### Post by TravisNewman on 2005-02-12
Basically, if you plan on upgrading to  hoary without doing a fresh install, you want to keep that ubuntu-desktop package around. It's a virtual package that depends on the desktop system, essentially. With hoary, things have changed, and if you delete that package your system won't be as it should be.

If you're planning on staying with this installation for a while without upgrading to hoary, then it's safe to delete it.

---

### Post by cblack on 2005-02-12
> Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system
 .
 It is safe to remove this package if some of the desktop system packages are
 not desired. 

It's just a meta package and doesn't do any configuration of your machine or the like. Not sure why the previous poster says it'd be a bad thing to remove it. Should you ever want to see if the ubuntu-desktop package will install anything you'd want you can always do a sudo apt-get install ubuntu-desktop and look at what packages it wants to install.

---

### Post by TravisNewman on 2005-02-12
Please educate yourself before telling someone something like this, cblack.

Hoary is running Xorg, Warty is running XFree86. Hoary is running gamin, Warty is running fam. If you get rid of ubuntu-desktop and then do a dist-upgrade, you won't get Xorg and you won't get Fam, and some bad things could come of it. These are just two examples, but there are others. It can break things. 

Seriously, just search for ubuntu-desktop on these forums. This has been discussed many many times. It can most definitely cause problems when you're upgrading.

---

### Post by woodstock on 2005-02-12
If I understand correctly I wouldn't think that the meta-package would be needed for a fully functional upgrade to hoary.

I understand the Xfree will need to be replaced with Xorg and same goes for fam and Gamin, but I would think that this information would reside not only in the meta-package but also in their corresponding packages. What I mean is, the Xorg package will have data saying that it needs to replace XFree and same for Fam and Gamin...

Once again I could be wrong, I am not an expert and I am a little rusty when it comes to making .debs. I haven't gotten up to speed on thinking the "Debian (ubuntu) Way". It's been a while.

Correct me if I'm wrong.

---

### Post by TravisNewman on 2005-02-12
You're mostly right, but most people aren't going to know that they need to replace fam with gamin, and they'll wonder why their folder information only updates when they tell it to reload. Some people will not know they need to replace XFree, and come looking for help saying they're running Hoary, but when asked about their xorg.conf they can't find it. 

So yes, it's possible to have a functional system after removing ubuntu-desktop, it's just a major hassle, and you have to know what you're looking for or you're bound to miss something.

---

### Post by woodstock on 2005-02-12
I understand what you mean now. Lol.

I thought that maybe apt would still see Xfree and just download Xorg (same for fam/gamin). I thought that maybe the Xfree package is already setup with the correct info inside the package stating that Xorg will replace it when the time comes.

Either way, it really doesn't hurt to just apt-get ubuntu-desktop on the same day as when you want to upgrade to hoary.

---

### Post by DJ_Max on 2005-02-12
Long story short, don't remove ubuntu-desktop, it'll save you a lot of trouble, and it's not worth removing.

---

### Post by nanaban on 2005-02-12
Thanks all for the prompt replies!  :-P

---

### Post by Sam on 2005-02-19
I have the same question than nanaban, but after reading this thread I haven't found the answer. How to remove evolution without removing ubuntu-desktop ?

---

### Post by kassetra on 2005-02-19
Well, as far as I know there is no way of removing evolution without removing ubuntu-desktop...
 
 Here is what I am currently doing.  Now, I don't know if this is so wise (I've been known to do really stupid things before), but it's what I'm trying.
 
 I don't use emacs, so in order for me to remove it I had to remove ubuntu-desktop.  Ok.  So, I know that the upgrade process essentially relies upon this meta-package, so I downloaded the [source files]("http://higgs.djpig.de/ubuntu/www/hoary/base/ubuntu-desktop") and I'm editing out the dependency upon emacs, and then I'll rebuild & reinstall the file.  Most likely I'll either end up building my own deb package or using the deb package that checkinstall sees.
 
 Again, I say, I don't know if this is so wise, but it's what I'm trying.  Since I won't be upgrading to Hoary until the official release, I figure I'm safe for a while... and if all else fails, I'll dump my special ubuntu-desktop package, install the real one (along with emacs and everything else it wants), upgrade and then remove emacs again.
 
 I can explain further if I'm not making any sense to you here.  :)

---

### Post by Sam on 2005-02-19
Hi kassetra

I understood the process you described, but I'm a linux newbie, so I will not make this kind of things for the moment.... And I will upgrade to Hoary; I will keep evolution until this.

Thank you for your reply!!! ;-)

---

### Post by kassetra on 2005-02-19
yeah, I certainly don't suggest doing what I'm doing to most people, and if you're a newbie that wants to upgrade without problems, I'd say, don't listen to me at all.  heh.  ;)

---

### Post by MrData on 2005-07-14
Greetings,

If I can't easily uninstall (remove) Evolution, fine. But, shouldn't there be a way to stop it from running? I have been researching this for a couple of months, without result. I even figured out that "evolution --force-shutdown" would close Evolution (releasing memory and CPU resources), and this seemed to work for a time.

However, now, when I try to kill Evolution, it comes back automatically in seconds. Why is Evolution so difficult to kill and keep dead?

Sincerely,
Israel Steinmetz, PDA Editor
BellaOnline.com: PDA Help and Information
[http://pda.bellaonline.com/](http://pda.bellaonline.com/)

---

### Post by bagatonovic on 2005-08-04
I just removed evolution and the ubuntu-desktop package last night.  I noticed Evolution was taking up about 200mb of ram.  This is unacceptable for a program I dont even use.   I've read through this thread, and my question is this: when I go to upgrade, would I just be able to install the ubuntu-desktop package before I run the upgrade and still be ok?

I run the x86_64 edition of v5.04.  Does this issue even apply to me since this thread is for Warty?

I thank everyone in advance for their help.

---

### Post by anwarlorenzo on 2005-08-05
[QUOTE=MrData]Greetings,

If I can't easily uninstall (remove) Evolution, fine. But, shouldn't there be a way to stop it from running? I have been researching this for a couple of months, without result. I even figured out that "evolution --force-shutdown" would close Evolution (releasing memory and CPU resources), and this seemed to work for a time.

However, now, when I try to kill Evolution, it comes back automatically in seconds. Why is Evolution so difficult to kill and keep dead?

Sincerely,
Israel Steinmetz, PDA Editor
BellaOnline.com: PDA Help and Information
[http://pda.bellaonline.com/](http://pda.bellaonline.com/)[/QUOTE]


Ditto :)

---

