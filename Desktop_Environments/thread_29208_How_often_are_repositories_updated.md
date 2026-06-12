---
title: "How often are repositories updated?"
date: 2005-04-23
forum: Desktop Environments
---

### Post by GTKpower on 2005-04-23
How often are updates available on the repositories?

How bleeding-edge are they?  

I have GNOME 2,10 (Hoary), so can install GNOME 2.12 from the repositories when the times comes?  Just how long can I keep updating Ubuntu Hoary?  I assume through Synaptic I can get the Breezy Badger updates, as well as maybe a couple of releases after that?

(wonderful to be here, by the way.  Ubuntu and GNOME 2.10 are just phenomenal!)

---

### Post by XDevHald on 2005-04-23
With Hoary you keep yourself updated through the Ubuntu Update Manager, also with Gnome 2.12 that will be coming available soon, but possibly hit Breezy first before Hoary, I could be wrong, but with Breezy, in order to get updates such as repositories, you'll have to change your sources.list in your /etc/apt and change all **hoary **to **breezy **then remove the CD at the top the sources.list and then use the Ubuntu Update Manager to start using Breezy.

On a very very serious note, please do not use Breezy at this time as it is very unstable to almost every repository, if you want to contribute to helping them with sending bug reports, feel free in doing that, but in order to do so, you'll need to be using Breezy repo's in order to fill in with them on that job.

---

### Post by GTKpower on 2005-04-23
[QUOTE=Doc]With Hoary you keep yourself updated through the Ubuntu Update Manager, also with Gnome 2.12 that will be coming available soon, but possibly hit Breezy first before Hoary, I could be wrong, but with Breezy, in order to get updates such as repositories, you'll have to change your sources.list in your /etc/apt and change all **hoary **to **breezy **then remove the CD at the top the sources.list and then use the Ubuntu Update Manager to start using Breezy.

On a very very serious note, please do not use Breezy at this time as it is very unstable to almost every repository, if you want to contribute to helping them with sending bug reports, feel free in doing that, but in order to do so, you'll need to be using Breezy repo's in order to fill in with them on that job.[/QUOTE]

Thank you kindly for the reply.

So I suppose all I need to do is edit the sources.list.  

Will there be an announcement as to when a Hoary user will need to edit their Sources.list in order to start updating relatively STABLE breezy packages?  I don't want to get left behind with respect to GNOME 2.12, yet I also want to update to Breezy. 

Do I udpate to GNOME 2.12 BEFORE Breezy, or vice-versa?  Does it matter?

Thanks again!

---

### Post by XDevHald on 2005-04-23
September is when Breezy will be coming out, also note that [[color=black]Gnome.org[/color]]("http://www.gnome.org") will keep you updated with all news based on their new upcoming events.

Also note that the members from UbuntuForums will be posting this if and when it does come out, so you will be posted up to date no matter what, but when Gnome 2.12 comes out....I really don't have the answer for you on that question. :)

---

### Post by GTKpower on 2005-04-23
I'm just a little bit confused (sorry, bear with me  ;-)

Can't I just leave my sources.list file alone, and keep all the standard Hoary repositories and update through those?  Or, will I not have access to the Breezy packages if I do this?

---

### Post by gil-galad on 2005-04-23
[QUOTE=GTKpower]I'm just a little bit confused (sorry, bear with me  ;-)

Can't I just leave my sources.list file alone, and keep all the standard Hoary repositories and update through those?  Or, will I not have access to the Breezy packages if I do this?[/QUOTE]

The hoary packages do not change except for security updates.

---

### Post by Simian on 2005-04-23
Sorry I know this is slightly off topic but it is repository related. When I apt-get update i get a load of error messages from the backport repositories. any ideas?

---

### Post by XDevHald on 2005-04-23
[QUOTE=GTKpower]I'm just a little bit confused (sorry, bear with me  ;-)

Can't I just leave my sources.list file alone, and keep all the standard Hoary repositories and update through those? Or, will I not have access to the Breezy packages if I do this?[/QUOTE]

You will need to change your sources.list to get these updates from breezy.

---

### Post by XDevHald on 2005-04-23
[QUOTE=Simian]Sorry I know this is slightly off topic but it is repository related. When I apt-get update i get a load of error messages from the backport repositories. any ideas?[/QUOTE]

If you're doing [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) then yes the site is down at the moment due to xml or parser errors. The formatted text from the error has been sent to the site admin for further updates to take place.

---

### Post by darkaudit on 2005-04-23
But will a bug like this one:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6615](https://bugzilla.ubuntu.com/show_bug.cgi?id=6615)

showing 'Pending Upload', see an update in Hoary?

---

### Post by XDevHald on 2005-04-23
If you have a repo that is needing to be updated, but is sitting there in the Update Manager and is not installing but shows an error after the update, then you need to lock it until it gets fixed.

Also note that the bug will not see it until it gets fixed.

---

### Post by Simian on 2005-04-23
[QUOTE=Doc]If you're doing [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) then yes the site is down at the moment due to xml or parser errors. The formatted text from the error has been sent to the site admin for further updates to take place.[/QUOTE]
 Thanks Doc.
As long as it's not just me then :)

---

### Post by GTKpower on 2005-04-24
So, when I change my sources.list to reflect Breezy, I will still get updates to Firefox, Evolution, Gaim etc., as they come in, I assume?

When might be a good time to change the list to Breezy, assuming that I want relatively stable apps, but I'm too impatient to wait until September?  I know my question sounds a bit nebulous, but when can I expect the Breezy packages to be less "volatile"?

The reason I'm asking this is because I'm used to PClinuxOS' repositories.  There is a "stable" and "unstable", section, configurable directly through Synaptic.  No file editing needed.  I originally downloaded and burnt PClinuxOS Preview 8.0.  I just ran Synaptic on a weekly basis to get updates/new packages.  By doing this I automatically updated to KDE 3.4 eventually, and also got changes to the distro itself, such as udev, etc, thus updating to Preview 8.1 at the same time.  I usually waited for most of the updates to find their way into the "stable" repositories, but if I saw an update to an app I liked (i.e., amaroK) that was in the unstable section, I downloaded that.  If it was buggy, I just waited a bit until it showed up in the stable section, if it needed fixing.

I know I'm being difficult, but I'm just having a bit of trouble understanding ubuntu's way of updating.  Hehe . . .  forgive my greenness.

---

### Post by GTKpower on 2005-04-24
I know I'm being a bit of a pain, but I'd love a few more details (with respect to my very las post here), and then I'll leave it alone.

*bump*

---

### Post by c_dog on 2005-04-24
```
So, when I change my sources.list to reflect Breezy, I will still get updates to Firefox, Evolution, Gaim etc., as they come in, I assume?

When might be a good time to change the list to Breezy, assuming that I want relatively stable apps, but I'm too impatient to wait until September?  I know my question sounds a bit nebulous, but when can I expect the Breezy packages to be less "volatile"?

```
 
You can jump on the Breezy bandwagon at any time. Just like Hoary, Breezy probably wouldn't be stable until September. There were showstopers with Hoary almost every other day during it's development. Things were constantly being broken and fixed. There were sometimes hundreds of updates in single day. This continued up until the 4 "weekly" releases on the last day. So, Breezy may always be volatile until September. If you really want to play, but are worried about stability, just set Breezy up on a seperate partition and multi-boot it. Just remember that you don't want to mix the Hoary and Breezy repositories. This is just like the fact that was not a good idea to mix Warty with Hoary.
Hoary will probably get the Universe and Multiverse Updates over time, but as mentioned before Main will most likely only get security updates.

---

### Post by XDevHald on 2005-04-27
[QUOTE=GTKpower]I know I'm being a bit of a pain, but I'd love a few more details (with respect to my very las post here), and then I'll leave it alone.

*bump*[/QUOTE]

I can't exactly give you all the information based on Breezy, but you can deffinently check out the provided link.

> [http://www.ubuntulinux.org/wiki/BreezyBadger]("http://www.ubuntulinux.org/wiki/BreezyBadger")

Also note that NOW is not a good time to jump in with Breezy being loaded on your box, which you already know as it's getting worst in the dev field with bugs in the apps.

And just like c_dog noted, September would be the best time to actually jump on board with Breezy.

Here's another link that will give you even more useful updates as far as breezy is doing and what you should do for now.

> [http://www.ubuntuforums.org/showthread.php?t=29565]("http://www.ubuntuforums.org/showthread.php?t=29565")

---

### Post by Alexander Kirillov on 2005-04-27
[QUOTE=darkaudit]But will a bug like this one:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6615](https://bugzilla.ubuntu.com/show_bug.cgi?id=6615)

showing 'Pending Upload', see an update in Hoary?[/QUOTE]
 Likely not. So if you want to see this bug fixed, you'll have to use Breezy - or backports from Breezy to Hoary.

---

### Post by GTKpower on 2005-04-27
Actually, I've now reconciled myself with this 6-month release cycle.  If someone wants  newer packages, they're there, but more attention is paid by the devs to stabilizing the distro as a whole.  Something I can agree with, especially now that I see how well Ubuntu behaves on a daily basis.  6 months, while it may seem longish to those of us used to a distro with roling updates, isn't that far off, and one could do a dist-upgrade a month or two before that and be assured of relatively fair stability.

Ubuntu has indeed grown on me during the short week and a half I've had it, and I've changed a few of my distro-related views and beliefs because of it.

A minimum of eye-candy (just enough to keep it interesting) and a very simplified and "to the point" interface, means I can work in a less irritating environment, where the only thing in my way is my work, and not a flashy, bubbly interface that is crammed with so-called "features."  Finally, a clean window toolbar and menu!

---

