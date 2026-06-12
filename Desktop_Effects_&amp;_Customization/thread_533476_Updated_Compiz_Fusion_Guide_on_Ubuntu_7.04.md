---
title: "*Updated* Compiz Fusion Guide on Ubuntu 7.04"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by Vorian on 2007-06-22
[B][COLOR=Red]DO NOT INSTALL COMPIZ FUSION IF YOU ARE A NEW USER
USING 3RD PARTY REPOSITORIES IS NOT RECOMMENDED

[/COLOR][/B][B][COLOR=blue]If you are adamant about installing Compiz Fusion from a 3rd party repository, this is the only method I recommend. 

[/COLOR][/B][B][COLOR=Red] *updated to reflect Amaranth's guide*[/COLOR]
[/B][https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
Amaranth is the developer/maintainer of Compiz  for Ubuntu.  These are packages backported directly from the Gutsy Repository.  This repository does not have a pgp key, to remind users that they are installing/updating from a 3rd party repository.  

[COLOR=RoyalBlue][B] **compiling links at the bottom of this post
[/B][/COLOR] 
 *please remove any repositories you were using (*i.e. Treveno eyecandy*)
** also purge Treveno's packages
```
sudo apt-get --purge remove compiz* libcompizconfig*
```** First add Amaranth's repository:**

OR

Go to synaptic search for compiz, and remove every compiz package, then reinstall.

[COLOR=Black]***The Following commands should be entered after hitting ALT+F2 (looks like this)**[/COLOR]
[IMG]http://vorian.org/wp-content/uploads/2007/06/run2.png[/IMG]
To [B]Run Compiz Fusion
[COLOR=Red]use alt+F2 and enter
[/COLOR][/B] ```
compiz --replace
```**To configure Compiz**
[COLOR=Red]alt+F2 and enter[/COLOR]
```
ccsm
```You can also configure Compiz Fusion by going to System>Preferences>CompizConfig Settings Manager

Have Fun :)

[COLOR=Blue]**TO COMPILE COMPIZ FUSION FIRST RELEASE 0.5.2**[/COLOR]
> 
The Compiz Fusion 0.5.2 tarballs are available at [http://releases.compiz-fusion.org/0.5.2/](http://releases.compiz-fusion.org/0.5.2/) . You can verify these tarballs using the sha1sums in [http://releases.compiz-fusion.org/0.5.2/compiz-fusion-0.5.2.sha1](http://releases.compiz-fusion.org/0.5.2/compiz-fusion-0.5.2.sha1) , which are signed by Compiz Fusion Release Team GPG key (C2B8F46E) at [http://releases.compiz-fusion.org/0.5.2/compiz-fusion-0.5.2.sha1.asc](http://releases.compiz-fusion.org/0.5.2/compiz-fusion-0.5.2.sha1.asc) . The matching Compiz Core tarball is available in the compiz/ subdirectory.
 Instructions on upgrading from Beryl can be found [here]("http://forum.compiz-fusion.org/showthread.php?mode=hybrid&t=3157")
 For more information, see onestone&#8217;s forum post [here]("http://forum.compiz-fusion.org/showthread.php?p=22174#post22174")
[more info at the compiz fusion blog....]("http://smspillaz.wordpress.com/2007/08/13/compiz-fusion-our-first-release-052/")
**Some quick tricks:**
- Hold CTRL + ALT keys and with the left mouse button rotate the cube
- Super + E activates the Expo plugin
- Hold Super + Shift and with your mouse paint fire on your desktop
- Super + Shift + C will erase the fire paint
- Super + Tab activates the Ring Switcher plugin

---

### Post by src2206 on 2007-08-31
I used this method exactly as you described, but now System>Preferences>Desktop Effects is gone! :(
Moreover as I enable Compiz using the command you specified above, all the three buttons for maximize/restore, minimize and close are gone! I can't even get the multiple workplaces.

:((

---

### Post by Zenham on 2007-08-31
Use the System->Preferences->CompizConfig Settings Manager. Emerald Theme Manager is also there if you're using Emerald.

Compiz Fusion is not part of Ubuntu, hence it doesn't use Ubuntu's configuration applets.

---

### Post by praet on 2007-09-13
Hey Vorian, 

First. thanks for this great post. I recommend lots of irc people to read this and was hoping you could update the post again.

The repo urls have changed as per Amaranth and this guide:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main
```

Thanks again.

---

