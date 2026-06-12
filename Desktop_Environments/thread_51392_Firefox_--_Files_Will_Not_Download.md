---
title: "Firefox -- Files Will Not Download"
date: 2005-07-23
forum: Desktop Environments
---

### Post by harrisxml on 2005-07-23
I just installed Ubuntu.  AMD64 is my version.  When I click on a link for downloading nothing happens...  What is wrong with Firefox and/or Ubuntu that is not allowing any download windows to show at all?

---

### Post by super on 2005-07-23
have you tried right-clicking on the download link and selecting "save link as"

---

### Post by TravisNewman on 2005-07-23
It could be a problem with the way the web page is coded as well. Have you tried multiple sites that are known to work?

---

### Post by ingvildr on 2005-07-23
i'm having the same issue along with themes and extentions not installing because when i try to install one it just makes firefox vanish.

---

### Post by harrisxml on 2005-07-23
I have tried on multiple sites.  I can't download ANYTHING.

---

### Post by pailhead on 2005-07-23
[QUOTE=harrisxml]I have tried on multiple sites.  I can't download ANYTHING.[/QUOTE]
 I'm having the same issue with FF 1.0.2. I click on any link and it doesn't do anything. I may uninstall and reinstall FF. Epiphany worked fine.

---

### Post by danns on 2005-07-23
I'm pretty sure this is a problem with the recent update to Firefox that Ubuntu packaged.  I did a fresh install of Hoary last night and that was one of the first things I noticed; clicking on a file would not initiate the download window (how my preferences are set).  I had to right click and select "save link as."  Now I do not have to do this on my Debian or Ubuntu PPC systems.  

That coupled with the tab problem and not being able to install extensions compelled me to download the latest firefox from Mozilla and install that into /opt/firefox.  Now these problems are gone for me.

---

### Post by harrisxml on 2005-07-23
Awesome.  I appreciate your help.

---

### Post by bytewolf on 2005-07-24
[QUOTE=harrisxml]Awesome.  I appreciate your help.[/QUOTE]
 Me too! I think it may be a bug of mozilla-firefox 1.0.2-0ubuntu5.4
So I :> sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5 
Then,everything goes well. Perhaps this is helpful to you too :-)

---

### Post by Oxygene on 2005-07-24
[QUOTE=bytewolf]Me too! I think it may be a bug of mozilla-firefox 1.0.2-0ubuntu5.4
So I :
Then,everything goes well. Perhaps this is helpful to you too :-)[/QUOTE]
 I switched to Ubuntu today and had exactly the same problem.

Thanks for your help, bytewolf, downgrading to mozilla-firefox 1.0.2-0ubuntu5 fixed the issue immediately.

In mozilla-firefox 1.0.2-0ubuntu5.4 you could delete compreg.dat and it would work for the session started after that. But if you quit firefox and open it again, it would not work.

---

### Post by harrisxml on 2005-07-24
You can also just go System>>Administration>>Synaptic Package Manager; then search for "Firefox" and select the install/reinstall box and update.  That works.

---

### Post by tyson133 on 2005-07-24
I'm having the very same issue, I just installed kubuntu on this machine a few days ago.  I hope this package gets fixed soon

---

### Post by dskloet on 2005-07-25
I downgraded firefox and it fixed the problem for me. But when I want to upgrade my system (sudo apt-get upgrade) it wants to upgrade firefox again. Is there a way to upgrade my system except for firefox?

thanks,
David

---

### Post by enemy_z on 2005-07-25
Reinstalling the package with synaptics as described above does temporarily solve the problem, but then it reemerges after a period of use.

I haven't tried a backport yet, as I don't want to have to manually selected packages for system upgrades (i.e. I want to still be able to apt-get upgrade).

---

### Post by yccheok on 2005-07-25
I also having the same problem :(

Since ubuntu firefox has a large user community, perhaps this package can be fixed soon. Should we drop a mail to this package owner? ;)

---

### Post by dongdongdog on 2005-07-27
There is a quick solution.

1, enable universe repository.

2, do a search in Synaptic for "firefox".

3, click on mozilla-firefox for upgrade. This will upgrade firefox to the lastest version, 1.0.6

4, click apply and restart firefox. 

You will have the fully working lastest Firefox 1.0.6.

For people not familiar with enabling the universe repository, please refer to this link,

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

