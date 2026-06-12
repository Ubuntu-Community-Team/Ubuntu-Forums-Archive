---
title: "OpenOffice.org 3 Stopped Working, Uninstalled it, now Can't Reinstall OOo from Repos!"
date: 2009-02-02
forum: General Help
---

### Post by OzzyFrank on 2009-02-02
OOo3 was a bit of a pain to install via guides I found, but it worked. But slowly with each system update it died. First, files wouldn't open from email attachments, but would if I double-clicked the saved files... then they wouldn't open that way, but would if I opened Writer or Impress or whatever then used File > Open... then OOo3 died altogether and none of the programs would open at all. Now I've uninstalled it, but can't reinstall the Ubuntu-friendly one in the repos! So now I have no OOo at all.

Some of the packages have been installed, like **openoffice.org-core**, **openoffice.org-base-core** and **openoffice.org-common**, and others Synaptic marked for installation, but when I try to mark the metapackage **openoffice.org** for installation I get this:

[B][COLOR="Indigo"]openoffice.org:
 Depends: openoffice.org-writer but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
 Depends: openoffice.org-impress but it is not going to be installed
 Depends: openoffice.org-draw but it is not going to be installed
 Depends: openoffice.org-math but it is not going to be installed
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-report-builder-bin but it is not going to be installed[/COLOR][/B]

No other info but that it isn't going to install those packages. When I try to install **openoffice.org-writer** alone, it says all the openoffice.org-* packages are going to bne removed, but then complains:

[COLOR="#4b0082"][B]openoffice.org-writer:
 Depends: openoffice.org-core but it is not going to be installed
 Recommends: openoffice.org-emailmerge but it is not going to be installed[/B][/COLOR]
Any ideas on how to get my office suite back? This seems to be a real mess! I figured uninstalling OOo3 would let me reinstall the supported version, but this isn't the case.

---

### Post by bapoumba on 2009-02-02
How did you install OOo 3 ?
Can you please post your sources.list ?

---

### Post by OzzyFrank on 2009-02-02
Oh OK, seems some of the **openoffice.org-*** packages were in fact left over from OOo3. Actually, don't quote me on that, as the corresponding packages for the latest version often started with **ooobasis3** or something and I think **openoffice.org3-***, and they all got uninstalled... but anyway, manually marking everything starting with **openoffice.org-** for uninstallation let me mark **openoffice.org** metapackage for installation, and no complaints this time. I'll see how it goes once it's finished downloading the files.

As for OOo3, it took more than adding some sources - there are a few guides around for all the steps needed. Adding the repos was mostly for updates, unless I am remembering wrongly (I used the source archive downloaded from the site - unless that didn't work and I have forgotten that too! Sorry, I got somewhat muddled with the mess of installing it, hehe). Anyway, here is the source:

**deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main**

I personally wouldn't recommend going through the hassle. I mean, what benefits are there *really*? For me it just turned out to be much more hassle than it was worth. It wasn't so much the installing part, but just watching a working program (or suite of programs) gradually die and then not working at all when I actually needed it. Not sure if Ubuntu is to blame or OOo3, but since I can't remember getting any updates for OOo3 since installing it, I'd put my money on the former!

---

### Post by OzzyFrank on 2009-02-02
Looks like I got back OOo 2.4 just fine after the last steps outlined. Another reply I got elsewhere just before says I could have done this via terminal:

[B]sudo apt-get remove openoffice*
[/B]
I wasn't sure if a wildcard (*) would work, or how to go about it (I would have thought openoffice.org-*), but there it is.

---

### Post by OzzyFrank on 2009-02-02
[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

For those who want to run both versions... it works on 8.10 too.

---

### Post by juanp.contreras on 2009-02-17
Hi...

I had a "great idea" about installing a lot of fonts I've found on gnome art. After the installation (using a script posted in somewhere in this forum), openoffice began to confuse (not only openoffice... but other programs also have this problem although it is not serious in them) the fonts. Since that, operations like "cut and paste" take a lot of time and generally OO freezes until I have to end the process... Do you think that reinstalling OO (Intrepid package) can solve this problem?

Thanks

---

### Post by OzzyFrank on 2009-02-17
Not sure reinstalling OOo would make a difference with that problem, since you say it affects other programs too, even if not as badly. Sounds like a pretty weird problem... I'd be interested in hearing more about this script and what it did exactly. Installing some fonts shouldn't do more than give you more fonts to work with.

---

### Post by juanp.contreras on 2009-02-17
This is the thread I've mentioned previously...:

[http://ubuntuforums.org/showthread.php?t=275202]("http://ubuntuforums.org/showthread.php?t=275202")

Thanks for your interest.... the first posts initiated by me were solved effectively and quickly... but since I'm a newbie, I had post other questions but not answered questions from other people so I think that there is a "karma" system or something like that to encourage positive interaction... I'm right or is only my fancy?

---

### Post by juanp.contreras on 2009-02-19
Hi... As you said, reinstalation does nothing on openoffice, I've reinstalled because I'm becoming desperate since modifying a document is impossible by now....

---

### Post by OzzyFrank on 2009-02-19
Have you tried totally uninstalling it? I never had your font problem, but in the end couldn't even open any of the OOo apps, so uninstalled 3.0 and replaced it with the Ubuntu-friendly version in the repos. All is fine now.

PS: Asking if Karma works here is like asking if there is a God (or if He uses Linux!)... but I would like to think so. I've had some important questions answered and a lot of help offered, so do my best to help others when I can.

---

### Post by juanp.contreras on 2009-02-19
sorry... how do I:

1) totally uninstall OO?
2) switch repositories and select the one you recommended?
3) know what to install then?

haha... I'm so new to linux and ubuntu... excuse me please... but be totally sure about I'll help somebody as soon as I can... jeje

---

### Post by OzzyFrank on 2009-02-19
In Synaptic, right click it and choose it to be removed completely. There will be more than one package, so just type [COLOR="DarkRed"]OpenOffice[/COLOR] in the Search field, and mark for complete removal every package that seems to be part of OOo. At least in my case there was no metapackage that when selected meant everything related would get uninstalled... so I just marked every **openoffice.org** package for total uninstallation. If trying to remove 3.0, then you will need to search for **ooobasis3** packages as well and remove them. Then just use Synaptic to install it again. No need to worry about repos, as the Ubuntu-friendly version will be in the standard repos anyway.

---

### Post by juanp.contreras on 2009-03-02
excuse me for bothering about the problem again....

I installed OO3 again and the problem continued as it was. But I have to solve the problem because wine is very difficult to install (I'm very busy).  

So I googled and then I found this page 

[https://pmc.ucsc.edu/~dmk/notes/]("https://pmc.ucsc.edu/~dmk/notes/")

(dont worry... my firefox said it has a bad security certificate, but I do not think so). The page says that I should replace the file with the script shown and then every would be as it has to be....
also, the page says that the path of the file (and the file) I have to change is /etc/x11/fs/config... but Im not quite sure because I do not want to do a mess with my system again....

thanks for your patience...

---

### Post by OzzyFrank on 2009-03-05
Hi. Not sure how much help I can be on this, but from what I see, it is not a script but just a config file to replace. You can easily create a copy of the original, then try the new config file and see if OOo behaves after that. If it somehow makes things worse, just replace the new config file with the backed up old one.

By the way, why did you mention Wine? And why did you say it is very difficult to install? Just asking since you don't need Wine to run OOo, and Wine is easily installed through Synaptic. Cheers

---

### Post by juanp.contreras on 2009-03-05
thanks... The problem is that in ubuntu's file structure that path is (or I'm thinking that it is) different in my file system. About wine, I only want to say that when I tried to install office on my system, I had to download a lot of libraries and other things... that caused me a lot of trouble because issues like the way I had to configure them....

---

### Post by OzzyFrank on 2009-03-05
Hi. OK, if you still want to try the config file, just search for the correct path on your system. Should be around somewhere. The search tool can be pretty useless, so install Catfish if need be (and search the whole Filesystem not just your home folder).

But if you just uninstall OOo 3 totally with the instructions I've already given, you can reinstall OOo 2.4 via Synaptic. No need to bother with MS Office in Wine! (If you can't install 2.4 properly, it is because you haven't removed EVERYTHING to do with OOo 3 yet, so do so and all will be fine).

---

