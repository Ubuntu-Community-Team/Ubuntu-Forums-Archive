---
title: "gimp 2.6.6 install ??"
date: 2009-04-25
forum: General Help
---

### Post by snlnluvnit45 on 2009-04-25
I am attempting to install gimp 2.6.6.. right now I have ver 2.4.5.  I have downloaded it but don't quite understand what to do next.. I have attempted the apt-get install gimp from the terminal and it said that I all ready have the most up to date version... any guidance would be much appreciated.  I am running Ubuntu ver 8.04

Thanks, Scott

---

### Post by stwschool on 2009-04-25
If the download is a .deb file then you can just double-click it and it'll install. If it's .tgz or anything like that you might have to compile it which is where a more experienced user might be able to guide you more effectively.

---

### Post by Paddy Landau on 2009-04-25
Save yourself lots of work. Delete your downloaded version, and head to the [Ubuntu precompiled releases]("http://www.getdeb.net/").

Search for gimp and choose your distribution.

---

### Post by 0cton on 2009-04-25
Correct me if I am wrong but gimp 2.6.6 is already in ubuntu's repositories <.<

---

### Post by snlnluvnit45 on 2009-04-25
I downloaded the deb version as you suggested.. I geta dependentcy not satisfiable error gimp data. Do I need to unintall the earlier version first??
Scott

---

### Post by kpkeerthi on 2009-04-25
> **snlnluvnit45 said:**
> I downloaded the deb version as you suggested.. I geta dependentcy not satisfiable error gimp data. Do I need to unintall the earlier version first??
Scott

No. You need to download all the three deb files posted in getdeb.

---

### Post by Lunx on 2009-04-25
> **kpkeerthi said:**
> No. You need to download all the three deb files posted in getdeb.


Yep, there are three packages you need. Install the gimp-data one first, then there's one I can't recall name of to install next. Depending on the version you already have, the last package g-mp may or may not need to be installed as it may just update with the first two (that's how it went for me with installing  2.6.6 to Intrepid)

---

### Post by snlnluvnit45 on 2009-04-25
> **kpkeerthi said:**
> No. You need to download all the three deb files posted in getdeb.

I downloaded 5 files that were available on the page. all are .deb files.. when I try to install, I get  the same message on one package, and the other tells me that there is an older version available in a software  channel.. 

Still confused, Scott

---

### Post by snlnluvnit45 on 2009-04-25
> **Lunx said:**
> Yep, there are three packages you need. Install the gimp-data one first, then there's one I can't recall name of to install next. Depending on the version you already have, the last package g-mp may or may not need to be installed as it may just update with the first two (that's how it went for me with installing  2.6.6 to Intrepid)

I tried to install gimp-data first as you suggested.. it is the one that tells me there is an older version available in another channel??? so I chose to install package anyway... it fails ???

Scott

---

### Post by Paddy Landau on 2009-04-25
> **0cton said:**
> Correct me if I am wrong but gimp 2.6.6 is already in ubuntu's repositories <.<
Not for Hardy 8.04, which snlnluvnit45 is using.

---

### Post by Paddy Landau on 2009-04-25
> **snlnluvnit45 said:**
> I downloaded the deb version as you suggested.. I geta dependentcy not satisfiable error gimp data. Do I need to unintall the earlier version first??
Scott

[LIST=1]
[*]Ensure that you have the right version. On the [gimp page]("http://www.getdeb.net/release/4054"), you should see "[FONT=Arial][SIZE=2]*For: Ubuntu Hardy (32 bits)*" on the right next to the video. If you have the wrong version, make sure you navigate to the right version for you.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Download, and install, in order from right to left. In other words, start with *libgegl-0.0-0* and finish with *gimp*. There are five in all.
[/SIZE][/FONT]
[/LIST]

---

### Post by snlnluvnit45 on 2009-04-25
> **Paddy Landau said:**
> Not for Hardy 8.04, which snlnluvnit45 is using.

To all who responded to my request for help.. I did a "sudo apt-get install -f" from the terminal and then I double clicked on each package til I it told me I could install. then just went on to the next package that would install.  I had to do them in a specific order.. although I can't remember the order.  It seems to work and the new version is installed... can I delete the packages that are now residing on my desktop???

Thanks to all for your help and patience with a Linux newbie..
Scott

---

### Post by snlnluvnit45 on 2009-04-25
> **Paddy Landau said:**
> [LIST=1]
[*]Ensure that you have the right version. On the [gimp page]("http://www.getdeb.net/release/4054"), you should see "[FONT=Arial][SIZE=2]*For: Ubuntu Hardy (32 bits)*" on the right next to the video. If you have the wrong version, make sure you navigate to the right version for you.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Download, and install, in order from right to left. In other words, start with *libgegl-0.0-0* and finish with *gimp*. There are five in all.
[/SIZE][/FONT]
[/LIST]

unfortunately your reply was not available when I finally got it to install.. but many thanks anyway... I had to do a "sudo apt-get install -f" first.. did that uninstall the previous version of gimp???

---

### Post by Paddy Landau on 2009-04-25
> **snlnluvnit45 said:**
> can I delete the packages that are now residing on my desktop???
Yes.

> **snlnluvnit45 said:**
> did that uninstall the previous version of gimp???
You should have only the one version of gimp on your machine now.

---

### Post by snlnluvnit45 on 2009-04-25
> **Paddy Landau said:**
> Yes.


You should have only the one version of gimp on your machine now.

Thanks for the assistance!!
Scott

---

### Post by Paddy Landau on 2009-04-25
> **snlnluvnit45 said:**
> Thanks for the assistance!!
With pleasure. Have fun gimping.

---

