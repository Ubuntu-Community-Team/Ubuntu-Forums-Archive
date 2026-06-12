---
title: "Wolfenstein: Enemy Territory - Finally Ported"
date: 2007-09-03
forum: Gaming &amp; Leisure
---

### Post by rcdegges on 2007-09-03
Hi everyone. I am a big fan of the game Wolfenstein: Enemy Territory. It's a really amazing first person shooter game. It is a freely available game, which is Windows, Mac, and Linux compatible. Usually, the Linux version of this game is a bit of a hassle to get installed correctly. First of all, you have to register at [www.fileplanet.com](www.fileplanet.com) and wait in a public download queue (for free users), which takes a while, then you have to figure out how to install it correctly. And lastly, you have to figure out how to patch the game manually, since there is no auto patching feature. This whole process is really unnecessarily tedious for a Linux novice, and is very time consuming.

To make life easier for everyone else, I decided to make a small installer script for the game. It works much like a package, it is very simple to install, and very straightforward. My package includes the official Wolfenstein: Enemy Territory Linux game client and Linux patch 2.60b (the latest version of the game). To install the game, you simply download my package, and type in a few commands into a terminal to get it installed correctly. And the best part is, that if you are a novice, just choose the default options and everything will work just fine for you. And once the game has been installed, simply open a terminal and type 'et' to run the game!

I hope you all enjoy the installer. If you have any questions or comments about it, let me know and I will fix it appropriately. It has already been tested on a few different Linux distributions (Ubuntu, Gentoo, and Slackware), and has worked flawlessly each time.

You can download my full installer here:

[http://projectb14ck.org/files/code/shell_scripts/wolfenstein_install.tar.gz](http://projectb14ck.org/files/code/shell_scripts/wolfenstein_install.tar.gz)

Which contains everything you need to get the game installed and running in no time!

INSTALLATION INSTRUCTIONS
----------
1) download the installer from the link above
2) open up a terminal and 'cd' into the directory where you downloaded the installer
3) type the following commands into your terminal:

tar xvf wolfenstein_install.tar.gz
cd wolfenstein_install/
./install.sh

4) at this point, the installer should be running. just choose the defaults, and when asked if you want to run the game, say NO!
5) once the installer has finished running, open a terminal and type 'et' to play the game
6) enjoy
----------

For more information about the game, visit the official Wolfenstein website:

[http://www.planetwolfenstein.com/](http://www.planetwolfenstein.com/)

-Randall

ADDED:

There is a known issue getting sound working in this game, to troubleshoot and fix your sound problem, please follow this link and read the thread.

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

### Post by stinger30au on 2007-09-03
awesome!!! thanks

---

### Post by ZylGadis on 2007-09-03
Erm

[http://www.splashdamage.com/?page_id=14]("http://www.splashdamage.com/?page_id=14")

Actually this is the official site of the game (i.e., the developers' one). The latest full version there, which includes the patch, works, confirmed by me last week.

Don't be so rash in reinventing the wheel next time.

---

### Post by sc3252 on 2007-09-03
> **ZylGadis said:**
> Erm

[http://www.splashdamage.com/?page_id=14]("http://www.splashdamage.com/?page_id=14")

Actually this is the official site of the game (i.e., the developers' one). The latest full version there, which includes the patch, works, confirmed by me last week.

Don't be so rash in reinventing the wheel next time.

I am going to agree with zylgadis, enemy territory was at lots of sites when it was first launched.  I bet if you looked around a bit that you would see that it is at other sites that don't make you wait 38 mins to download, also it isnt hard to patch or get it working in Linux.

---

### Post by chuckyp on 2007-09-04
getting sound to work out of the box is an issue with this game.

---

### Post by rcdegges on 2007-09-04
Sorry about the incorrect official site. I was under the impression that planetwolfenstein was. But in regards to other sites having it, yes, you can get it from other sites as well. Just as I've mirrored it, so have many other people. But there is no other installer for the game, and it is definitely not very easy for a new person to get installed. I was reading comments on the wolfenstein linux forums about people not knowing what to do with the .run file, etc. So my installer is simply an easy to use alternative. It is the latest version (patched), and works flawlessly from my tests. So feel free to use it if you don't want to go through the hassle of installing it by other means.

---

### Post by ZylGadis on 2007-09-04
A .run file is as executable as a .sh file is. I don't see your point. The official file I linked installs the entire game, including the patch. The user has to write a single command in terminal (as opposed to your three commands), because .run files are auto-decompressing archives.

Anyway, diversity is always good, because there is natural selection to take care of it. Good luck and have fun.

---

### Post by cogadh on 2007-09-04
Wasn't ET ported to Linux a looong time ago? The thread title seems a little bit deceptive and the subject itself really unecessary since the default package installs and runs fine normally.

---

### Post by rcdegges on 2007-09-04
Maybe I'm missing something, but I haven't seen an enemy territory package. I don't see one in the repositories at all. And like I said before, I just offer my program as an alternative to downloading and installing the game from another site.

The difference between the installation process of the game, and the installation process of my installer is a few commands.

If you choose to download the game and patch it yourself, you would have to do something like:

1) download game and patch
2) install game
3) move patch files into installation directory

My installer just does:

1) download installer
2) run install.sh

and it will auto patch the game when it's done. I basically wrote it to make it easier for people who aren't comfortable with using the terminal and doing things manually. And to me, it is more convenient to download the entire game and patch and a relatively simple installer all at the same time.

-Randall

---

### Post by maddog39 on 2007-09-04
Yes ET was ported years ago.... the source code is also availible on the ET resource site at [www.enemy-territory.com](www.enemy-territory.com)

---

### Post by cogadh on 2007-09-04
The package is not in the repositories (not everything is), it is available from the ET website and it already includes the patch. The only thing you need to do to install it is download it then run "sudo ./et-linux-2.60.x86.run". I just don't see how the install script you created is any easier than that.

---

### Post by univremonster on 2007-09-09
ah give the guy a break... I've never gamed before other than stuff that comes preinstalled and either by luck or because the filetypes aren't common in other fields, I for one had never seen a .run file before, I had only dealt with .tar, .tar.gz and .deb on a regular basis.  Personally, I think it's admirable to have people writing installers or anything else, and as someone said before, this is what natural selection is for if it's truly a waste of time.  For me personally, since I was getting errors involving glibc and setup files, this is a nice solution, gift-wrapped and ready to go.  So cheers, I say!

---

### Post by rcdegges on 2007-09-09
Thanks for the kind words ;) I'm glad it is helpful to some people. Just so you know, since I've hosted my packaged installer, over 200 people have downloaded it. I even received a lot of emails from people who used it and liked it who weren't able to figure out how to install it on their own. I'm glad to help.

-Randall

---

### Post by univremonster on 2007-09-10
rcdegges, the installer works great, the only problem I had was a lack of sound, which I understand to be my computer's issue more than the installer. You may want to include a link to this site: [https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

which was helpful for troubleshooting

---

### Post by rcdegges on 2007-09-10
Noted and updated, thanks.

---

### Post by weed-n-linux on 2008-02-11
hey i installed the script but i forgotu said and pressed run in the end of the script , now when i type 'et' in terminal it says command not found ,though the installer says it all went succesfully.

---

### Post by Sockerdrickan on 2008-02-12
Yes this sure isn't new at all

---

### Post by nocnoc94 on 2008-02-12
what does ''cd'' mean and how do i do that?

---

### Post by Perfect Storm on 2008-02-12
I'm closing this thread as the title is "mis-leading" as it have been out for awhile and shouldn't have been resurrected from the dead.

If anyone have trouble use our excellent search button, if it doesn't help make a new thread.

---

