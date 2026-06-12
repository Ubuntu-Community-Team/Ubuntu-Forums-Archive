---
title: "Trying to install UE theme pack in 10.04"
date: 2010-06-29
forum: Desktop Environments
---

### Post by caffemisto on 2010-06-29
Hi,
 
I recently installed Ubuntu 10.04 on my laptop. It's a Latitude D830. Everything's working well, which is why I decided to start customizing Ubuntu's look. My first stop was gnomelook.org and the other popular theme website for gnome(cant remember the name).
 
Anyway, I could not find what I wanted in a theme so I turned to Ultimate Edition's website. I followed their instructions to add their repo to sources.list. Then tried to install one of the theme packs, only to be told that 'usplash' could not be installed. WHAT!? So, I went ahead and googled the message and found out that 10.04 no longer uses 'usplash', it uses 'plymouth'. 
 
UE's website claims that their themes can be installed in any version of the official Ubuntu releases. All I had to do was follow their instructions to add the repo to sources.list, which I did.
 
Can I force install a theme pack and bypass the 'usplash' error? maybe at the command line with apt?
 
Thoughts, comments, solutions are welcomed.
 
Thanks. :confused:

---

### Post by Frogs Hair on 2010-06-29
Try some other packages to find out if it is just the one package . I've had corrupt theme packages before that won't load properly.

---

### Post by caffemisto on 2010-06-30
**Update: found another site with the Ultimate Edition themes and direct download links. I installed the latest one(UE 2.6 theme pack), package installer didn't complain, installation was successful, but the theme is nowhere to be found on my system. LOL I even went into Synaptic, searched for the theme, it didn't come up.**
 
:lolflag:

---

### Post by sataris on 2010-07-01
> **caffemisto said:**
> Hi,
 
I recently installed Ubuntu 10.04 on my laptop. It's a Latitude D830. Everything's working well, which is why I decided to start customizing Ubuntu's look. My first stop was gnomelook.org and the other popular theme website for gnome(cant remember the name).
 
Anyway, I could not find what I wanted in a theme so I turned to Ultimate Edition's website. I followed their instructions to add their repo to sources.list. Then tried to install one of the theme packs, only to be told that 'usplash' could not be installed. WHAT!? So, I went ahead and googled the message and found out that 10.04 no longer uses 'usplash', it uses 'plymouth'. 
 
UE's website claims that their themes can be installed in any version of the official Ubuntu releases. All I had to do was follow their instructions to add the repo to sources.list, which I did.
 
Can I force install a theme pack and bypass the 'usplash' error? maybe at the command line with apt?
 
Thoughts, comments, solutions are welcomed.
 
Thanks. :confused:
 
2 Comments concerning your issue.
 
Usplash, xsplash, and the like, were all dropped upon the release of Ubuntu 10.04 Lucid Lynx, and any themes that require those features are not going to work properly, or only partially install.
 
I had the same problem you are having while trying to install some themes from Satanic Edition's Website. 
 
Check out the actual ultimatedition.info or whatever the website address is for the actual distro release, and see if they have information for updated themes/icons/wallpapers and such. The Ultimate Edition versions that are based on Ubuntu 10.04 are 2.6 and 2.7. Any repos, packages, or themes associated with either of those versions should work out fine. 
 
Hopefully that helps you out, OP.

---

### Post by caffemisto on 2010-07-02
:guitar:  Got the themes installed and working:  downloaded the deb pkg and used dpkg to install them.

---

