---
title: "KDE 4.3 Repository?"
date: 2009-05-12
forum: Desktop Environments
---

### Post by Naatan on 2009-05-12
Is there a repository for KDE 4.3 Beta yet?

Quick question :P

---

### Post by Skripka on 2009-05-12
There isn't an announcement of Beta1 on [http://www.kubuntu.org/news](http://www.kubuntu.org/news) yet....although we Archers have had it available for a little bit.

Early reports suggest there is noticeably higher system resource usage (especially RAM).

[http://chakra-project.org/bbs/viewtopic.php?id=828](http://chakra-project.org/bbs/viewtopic.php?id=828)

---

### Post by Naatan on 2009-05-12
Having 4GB ram I'm not to concerned about that, I'm quite eager to see how KDE 4.3 improves the integration with GTK.

What do you mean by "we Archers" ?

---

### Post by Skripka on 2009-05-12
> **Naatan said:**
> Having 4GB ram I'm not to concerned about that, I'm quite eager to see how KDE 4.3 improves the integration with GTK.

What do you mean by "we Archers" ?

"Archers"= Adj. Pl. Person(s) who use Arch Linux.

---

### Post by KhaaL on 2009-05-13
I'm also quite keen on a kde4 repo, can't wait to get my hands dirty :>

---

### Post by gijsterbeek on 2009-05-18
There is one, BUT it has some serious dependency problems at the moment!

@ your own risk:

[http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu)

---

### Post by luisdavila on 2009-05-18
> **gijsterbeek said:**
> There is one, BUT it has some serious dependency problems at the moment!

@ your own risk:

[http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu)

hi, I can confirm that, mainly problem is with:
kdebase-runtime-data kdebase-workspace-bin packages.  I don't know what can I do about KDE, the simplest solution for me (waiting for solution) was start my fluxbox session and all my importants applications works fine, even with the KDE 4.3beta 1 version, like this example:

KMail
Version 1.11.90
Using KDE 4.2.85 (KDE 4.2.85 (KDE 4.3 Beta1))

and kopete, amarok, kontact, konqueror (and others) are the same thing, works fine with the same 4.3 beta1 version.

thanks if somebody found a solution and share with us, or wait for dependencies solution for this repository.  

LIKE YOU SAY:
"There is one, BUT it has some serious dependency problems at the moment!
@ your own risk:"

GOOD LUCK !!
[COLOR="PaleTurquoise"][/COLOR]

---

### Post by Izobalax on 2009-05-18
Also wondering if this Beta overwrites your current KDE4 install or not?

/izo\

---

### Post by SteveMcQwark on 2009-05-18
Should have checked here before following the instructions on Kubuntu.org :) I just had to completely remove kde and reinstall it in order to revert back to what I had before. Still waiting for the process to finish. I always wonder if the people who post those things *know* the packages are severely broken...

> **Izobalax said:**
> Also wondering if this Beta overwrites your current KDE4 install or not?

/izo\

It does. It fully replaces your current KDE4. In order to downgrade, you have to remove the ppa from your sources.list (software sources) remove the beta, then reinstall the kubuntu-desktop.

---

### Post by luisdavila on 2009-05-18
> **Izobalax said:**
> Also wondering if this Beta overwrites your current KDE4 install or not?

/izo\

and... yes, this overwrite your current install, is not another parallel desktop session.  all my session settings are ok, only different libs and with the dependencies problems the KDE session doesn't works.. but fluxbox session is good sometimes :p (some hours, or some days), I like fluxbox too

---

### Post by Izobalax on 2009-05-18
> **SteveMcQwark said:**
> It does. It fully replaces your current KDE4. In order to downgrade, you have to remove the ppa from your sources.list (software sources) remove the beta, then reinstall the kubuntu-desktop.
> **luisdavila said:**
> and... yes, this overwrite your current install, is not another parallel desktop session.  all my session settings are ok, only different libs and with the dependencies problems the KDE session doesn't works.. but fluxbox session is good sometimes :p (some hours, or some days), I like fluxbox too


Thought so. 

I think I'll leave it for now and wait 'till July. 

/izo\

---

### Post by SteveMcQwark on 2009-05-18
For those willing to try, I found this worked:
```

sudo apt-get clean
sudo apt-get dist-upgrade
sudo dpkg -i --force-overwrite /var/cache/apt/archives/*.deb
sudo apt-get dist-upgrade
sudo apt-get install plasma-widget-folderview
```

---

### Post by xebian on 2009-05-18
If you want to try 4.3 B1 without replacing 4.2.3, try the project neon nightly build

[http://ppa.launchpad.net/project-neon/ubuntu/](http://ppa.launchpad.net/project-neon/ubuntu/)

[COLOR="Red"]USE at YOUR OWN RISK[/COLOR]

Install kde-nightly.
When you logon, select the session type - KDE or KDE NEON

---

### Post by luisdavila on 2009-05-19
> **SteveMcQwark said:**
> For those willing to try, I found this worked:
```

sudo apt-get clean
sudo apt-get dist-upgrade
sudo dpkg -i --force-overwrite /var/cache/apt/archives/*.deb
sudo apt-get dist-upgrade
sudo apt-get install plasma-widget-folderview
```

thanks, my KDE 4.3beta1 works !!, :D
and until now is more securely use the KDE NEON project like another session like proposed, because is not an easy and safety "upgrade" .. thanks for this solution... 

ciao

---

### Post by zika on 2009-05-19
is anybody else having a problem with Amarok after using this kubuntu-experimental ppa to upgrade (I'm using Gnome but Amarok needs a lot of KDE stuff): namely all the icons in Amarok and its icon while it is in tray are gone ...?

---

### Post by SteveMcQwark on 2009-05-19
**edit*** oops, wrong thread.

---

### Post by hoppy785 on 2009-05-19
thanks for the solution... thought i broke my system till i saw i needed to force those overwrites... something i didnt think of prior to this was how do i go back haha.  i dont have to go back to 4.2.3, but if i wanted to is there a way to do this?  also once kde 4.3 goes final will this repo keep updating to that point and eventually give me the final?

---

### Post by SteveMcQwark on 2009-05-20
To remove it you just have to remove the ppa, then reinstall (remove then install) kubuntu-desktop. You will have a couple packages that won't downgrade from this, but these should show up as errors and you can remove them manually. Like:

package xxxx requires yyyy (= 4.2.2 blah blah blah) but yyyy (4.2.85 blah blah blah) is installed.

then you'd just remove yyyy then apt-get -f install to continue where you left off. (or install kubuntu-desktop again, shouldn't make much difference unless it won't let you).

I hope this is clear enough, I generally tend to just wing it.

And last time, it did update all the way to the final version, if I remember correctly.

---

### Post by SuperSonic4 on 2009-05-20
> **Skripka said:**
> There isn't an announcement of Beta1 on [http://www.kubuntu.org/news](http://www.kubuntu.org/news) yet....although we Archers have had it available for a little bit.

Early reports suggest there is noticeably higher system resource usage (especially RAM).

[http://chakra-project.org/bbs/viewtopic.php?id=828](http://chakra-project.org/bbs/viewtopic.php?id=828)

Is it stable(ish)? I don't want to enable KDEmod unstable yet if it's unstable

---

### Post by shadeslayer on 2009-05-27
hi i cant even log into KDE neon or KDE 4.3 Beta 1.It says kbuildsycoa has crashed and so on.
Backtrace : [http://paste.ubuntu.com/181772/](http://paste.ubuntu.com/181772/)
Any help would be appreciated.I have all the required packages installed(checked via synaptic)
edit : improved backtrace

---

### Post by Naatan on 2009-06-08
> **SteveMcQwark said:**
> For those willing to try, I found this worked:
```

sudo apt-get clean
sudo apt-get dist-upgrade
sudo dpkg -i --force-overwrite /var/cache/apt/archives/*.deb
sudo apt-get dist-upgrade
sudo apt-get install plasma-widget-folderview
```

Worked perfectly! I had to do an "apt-get install -f" at the end though (64bit).

My install says I'm using KDE 4.3 Beta 2.. thought that was gonna be released tomorrow.. odd :)

---

### Post by vmatherly on 2009-06-08
> **Naatan said:**
> Worked perfectly! I had to do an "apt-get install -f" at the end though (64bit).

My install says I'm using KDE 4.3 Beta 2.. thought that was gonna be released tomorrow.. odd :)


I can confirm that! install worked just like you said "apt-get install -f" and all. I have what claims to be KDE4.3 beta 2 or 4.2.90. 

Awesome!!! I love being one of the first!

---

### Post by oobuntoo on 2009-06-10
I find it odd that I've not added any kde 4.3 repositories, but my system was updated to kde 4.3 beta 2 (kde 4.2.9). I only added repo for kde 4.2.4 posted on Kubuntu.org. When I rebooted my system, I got the checkered-desktop. Any body getting this problem?

---

### Post by jbernardo on 2009-06-10
Try "sudo apt-get update; sudo apt-get install kubuntu-deskto; sudo apt-get dist-upgrade" now. The repository seems to now have all the updated kde 4.3 beta2 packages, and was missing some (notably plasma related ones) a couple of hours ago.

---

### Post by zenarcher on 2009-06-10
Working great here, as well.  I see we don't have the cool wallpapers, like globe, virus, weather and such yet, as are working in 9.10 Alpha.  Sure will be happy to see those!  They are great!

Cheers,
zenarcher

---

### Post by MickS on 2009-06-19
I've just done that and it broke my system, I got a new error for me:-
At the login I got the background picture and an error message saying No greeter widget loaded, check the configuration.

Fixed it by dropping to a command line and running apt-get install kdebase-workspace.

Hope that helps some one else, I found it by googling with the live CD.


Mick

---

