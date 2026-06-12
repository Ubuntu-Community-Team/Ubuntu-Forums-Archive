---
title: "Things Windows does better"
date: 2005-02-07
forum: Desktop Environments
---

### Post by ioliver on 2005-02-07
I've been using Ubuntu for a couple of weeks for some projects that need to be on Linux, and would generally say that I have a positive attitude to Linux. But there are some things that work so badly on the Ubuntu desktop that I really won't be switching any time soon.  Here's hoping that Ubuntu is a force that can address such issues in the future.

1)
Screen resolution.
Ubuntu has at no point detected my monitor correctly. When I use Mepis, I get to select my monitor manufacturer and model and it will put the info. into the relevant files, but Ubuntu can't even do this. Beginners will not be firing up a CLI or an editor, looking up frequencies in their manuals, and then fiddling with files. 

Ubuntu needs to get monitor selection right and let it be changed from the GUI.

2)
Network browsing. 
It's pretty much totally broken. It was fragile in Warty, I tried Hoary to see if it was better, but it's either so slow as to be unusable, totally fails to show network shares, or gives unhelpful error messages. Oh, and trying to access by main debian box fires off hundreds of copies of smbd on it (eventually I had to reboot it after three months uptime)  Mounting using smbclient works a treat so my network is OK. I've searched for hours, and tried fixes that have worked for a few others (but not for everyone) and it's slightly better but still mostly broken.

Ubuntu needs to get network browsing slick and reliable. And every dialog needs to let you access the network to save/load files.

There are dozens of other things that are undoubtedly rough edges, but the two above are to my mind things that either made initially using Ubuntu a painful experience or which prevent me effectively using it on a daily basis.

They are also things that Windows does a whole load better.

Regards

Ian

---

### Post by nocturn on 2005-02-07
I agree with point 1 to some extend.

But on point 2, you are talking about the smb networking protocol right?
This is not a native Linux/Unix protocol.

I would vote to work on nfsv4 first and support other protocols secondary.

---

### Post by t.rei on 2005-02-07
well - I guess I'd have to agree that the 2 abouve issues should be in a state called "working" for hoary. 
 
 I had several issues on various computers regarding the screen-resolution. In fact the only one who got it right was on my powerbook. IBM a20p failed miserably on xorg. And on my athlon 1.4 I had to do some guessing to get a proper resolution - an this far I still have only 75MHz on 1280x960 on a monitor that supports 1280x1024@100 :( - This is definately one major issue of ubuntu setup.
 
 As for the networking - I have not figured out so far how when and why i need to restart apache or not to get to see my friends gnome-shares and him to see mine. We tried for about two hours and then reverted back to "apt-get install ftpd gftp" ;)
 
 so yes - those 2 things should be fixed.
 
 However there are soooooo many things ubuntu does way better then any other desktop distro - I wouldnt touch windows if I had the choice.

---

### Post by Gtaylor on 2005-02-07
> 
1)
Screen resolution.
Ubuntu has at no point detected my monitor correctly. When I use Mepis, I get to select my monitor manufacturer and model and it will put the info. into the relevant files, but Ubuntu can't even do this. Beginners will not be firing up a CLI or an editor, looking up frequencies in their manuals, and then fiddling with files. 

Ubuntu needs to get monitor selection right and let it be changed from the GUI.

Without any information about your hardware, there isn't much hope of figuring out what went wrong in your case.
> 
2)
Network browsing. 
It's pretty much totally broken. It was fragile in Warty, I tried Hoary to see if it was better, but it's either so slow as to be unusable, totally fails to show network shares, or gives unhelpful error messages. Oh, and trying to access by main debian box fires off hundreds of copies of smbd on it (eventually I had to reboot it after three months uptime)  Mounting using smbclient works a treat so my network is OK. I've searched for hours, and tried fixes that have worked for a few others (but not for everyone) and it's slightly better but still mostly broken.

Ubuntu needs to get network browsing slick and reliable. And every dialog needs to let you access the network to save/load files.

As mentioned, samba isn't a native Linux/Unix protocol. It is a hacked way of communicating with the very Windows boxes it competes with in the market. Therefore I could conclude using your reasoning that Windows support for NFS is broken.
> 
There are dozens of other things that are undoubtedly rough edges, but the two above are to my mind things that either made initially using Ubuntu a painful experience or which prevent me effectively using it on a daily basis.

They are also things that Windows does a whole load better.

Ubuntu is a relatively new distribution. It has not had time to mature anywhere near long as many of the others out there. It also doesn't have anywhere near the corporate funding of Microsoft. The developers work on this great distro on their free time and have no motivation other than making a good platform for people to operate on.

Compare that to the bloodsucking Microsoft mentality and I find that reason alone to avoid Windows like the plague. If you think rampant spyware, large scale networked virus problems, and having to reformat at intervals better, by all means run Windows :) 

Could Windows be better in some cases? Sure. But it is in no way a superior product, they each have their strong points and Ubuntu's is that it is a free, easy to use distribution and it has great potential.

---

### Post by JackDog on 2005-02-07
1. Yes Ubuntu really needs better X configuration. Ouf of 4 machines I have installed it on, only one worked properly. But even that box did not enable DRI.

2. the SMB "ioslave" or whatever gnome wants to call it, has never worked well for me. In this case I would recommend that your use konqueror. besides smb, it supports nfs, sftp, imap, pop3, nntp, cups, ldap and iso (among many others) right from the file manager. Its transparent to the user. You can check your email in file view right from the file browser. Actually the main bonus with that ioslave is that other email apps can use and reuse the same connections. Log in once with one app, and another can use the same connection. Try it out, its very nice and will change your standards for file browsers. Nautilus is simple which I like, but as developer I need power over simplicity.

---

### Post by AndersAA on 2005-02-07
I gotta agree with JackDog, kde's file manager features (which builds into every kde app) is ridiculusly much better than gnome.  Supports a lot more protocols, and is more stable.

I've had a few problems with gnome's network browsing on smb servers, none with kde.

---

### Post by ioliver on 2005-02-08
[QUOTE=Gtaylor]Without any information about your hardware, there isn't much hope of figuring out what went wrong in your case.[/QUOTE]

Looking through the forums, and looking through the various online guides, I'm not sure monitor detection has worked for many people. And the documented ways of fixing it are all hacks. Unless there is some GUI monitor utility hidden somewhere.

As I say, this is easy on Windows, works well on Mepis, and is a pain in the butt on Ubuntu.

[QUOTE=Gtaylor] As mentioned, samba isn't a native Linux/Unix protocol. It is a hacked way of communicating with the very Windows boxes it competes with in the market.[/QUOTE]

Agreed, but samba is working for me on all of my other Linux boxes and even works on Ubuntu as long as you don't want to use it with the supplied GUI tools.

The ability to browse SMB shares needs to be fixed as it's core functionality that people expect to just work. If it can't be fixed then it needs to be removed!

[QUOTE=Gtaylor] Compare that to the bloodsucking Microsoft mentality and I find that reason alone to avoid Windows like the plague. If you think rampant spyware, large scale networked virus problems, and having to reformat at intervals better, by all means run Windows :)[/QUOTE]

All great reasons to avoid windows, and if there was somewhere to jump for desktop use, then I'd be jumping personally and dragging my company and relatives with me! (As it happens, we already use a lot of Linux at work, for servers, for development machines, and we're also busy porting Linux to a *totally* new architecture.)

I'm going to keep using Ubuntu, and will temporarily use work-arounds to access samba shares, but I really want to see Ubuntu (or just some Linux desktop) really succeed, which is why it's frustrating to see some of the basics still not right. But here's hoping it all gets sorted for April.

BTW, I'm currently playing with fuse and there's a strong chance that one of the "browse smb via the VFS" solutions may pan out. It strikes me that this is a very *Linux* way of handling things and would "just work" no matter what applications wanted to browse/load/save on the network.

Regards

Ian

---

