---
title: "Black box where Flash should be"
date: 2007-12-26
forum: Desktop Environments
---

### Post by andrewski on 2007-12-26
A friend who just started using Linux (Ubuntu Gutsy) is having some trouble with Flash that I don't really know how to troubleshoot. He's seeing a black box where the Flash items should be.

When he first started Firefox and it asked him to install Flash, he chose Gnash. When that didn't work he uninstalled Gnash and installed Adobe's Flash player. I wonder if having Gnash first caused the problem, though I may be biased because I only really tried the pre-release test packages.

I recommended a new Firefox profile, as he only has one user on the system. I also suggested removing Adobe's Flash player and then reinstalling it. Any other ideas that may help?

---

### Post by kellemes on 2007-12-26
Have you installed the plugin?

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by andrewski on 2007-12-26
> **kellemes said:**
> Have you installed the plugin?

```
sudo apt-get install flashplugin-nonfree
```
Yes.

---

### Post by kellemes on 2007-12-26
Just a thought..
Firefox-Options -> file types -> click "manage".. here you can set the download-actions..
Is SWF set to the correct plugin (the non-free one)? Could it be it's still set to gnash or however it's called?

---

### Post by JK2Silly on 2007-12-29
Hello. I am the person that Andrewski is refering to. I used the package manager to remove bot adobe flash as well as gnash and then recreated the firefox profile. Set up firefox again but on my iGoogle homepage there is a flash widget that displays as a white box. I installed the Adobe Flash plugin again and it still shows as a white box. If i install the Gnash plugin It becomes a black box. Unless Gnash is installed Firefox prompts to download missing plug-ins. 
As Kellemes suggested I checked the file types manager and SWF applications are set to use Movieplayer until Gnash is loaded then they are set to use flash plugin. 
This is also affecting most video streams as well so it putting a serious dampener on my internet experience here. ;-)
Any help would be appreciated...

---

### Post by JK2Silly on 2007-12-30
OK Issue resolved here. Since I am just setting up I reloaded gutsy with a complete reformat of the disc. ](*,) I downloaded the Flash tar from Adobe directly and ran the installer with that. Horray! Flash works! \\:D/ This also seemed to take care of a few other minor problems that I was having with display issues. Much obliged guys!

---

### Post by andrewski on 2008-01-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Here's a bit of context on the problem with Flash: [http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore](http://tombuntu.com/index.php/2007/12/31/why-cant-ubuntu-install-adobe-flash-player-anymore). Here's the bug that links to: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890).

---

