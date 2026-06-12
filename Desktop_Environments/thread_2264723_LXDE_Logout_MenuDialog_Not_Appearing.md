---
title: "LXDE Logout Menu/Dialog Not Appearing"
date: 2015-02-09
forum: Desktop Environments
---

### Post by King of Heart 4711 on 2015-02-09
Hello all,

I'm building a new system image for deployment running Ubuntu 14.04.1 LTS x64. I've installed normal Ubuntu as a base then installed lubuntu-core (with a few other packages) to use Lubuntu LXDE desktop. I'm having one small issue with the build so far. When I goto Menu -> Logout the logout menu/dialog is not appearing on screen, and does not seem to start at all. Running top/htop to view running processes seems to be the case.... sometimes. The application lxsession-logout sometimes appears in running process others it does not. Regardless if launched in the background or not it does not appear on screen. if tried running: lxsession-logout --display=$DISPLAY to force the current X display but issue remains. I get no output/warnings/errors. cannot seem to find where the application logs (not even sure if it does), no can I find a command option to run program verbose. I haven't the slightest clue what is broken here but need to fix. This small of an issue hasn't bothered me in a long time :)

Any thoughts. Thank you much!!!

---

### Post by tea for one on 2015-02-09
Good evening

Lubuntu (LXDE desktop) currently has Synaptic installed as the package manager.

I suggest that you open Synaptic (or install it if it is not present).
Locate "lxsession-logout"
Right click and select "Mark for Reinstallation"

It is possible that an updated version is available, which may bring in a new package to solve your problem.

Best wishes

---

### Post by King of Heart 4711 on 2015-02-10
Good Morning Tea,

I tried reinstalling using:

```
apt-get install --reinstall lxsession-logout
```

However the issue remains. If I spam "menu -> logout" the menu will eventually appear. I've also installed straight LXDE and issue also remains there.
I am on using the latest package in the official Ubuntu 14.04 repo: 

```
lxsession-logout_0.4.9.2+git20140410-0ubuntu1.1_amd64.deb
```

Cannot seem to find a later version to install (Which may be a good thing. Would like to try and avoid "Dependency Hell")
I'm going to try again using a fresh build of Ubuntu 14.04 and straight LXDE.

---

### Post by tea for one on 2015-02-10
> **King of Heart 4711 said:**
> Good Morning Tea,

If I spam "menu -> logout" the menu will eventually appear. 


I am intrigued by your comment - What does spam mean in this context and how do you "spam" the appearance of a shutdown menu?

Anyway, I use Lubuntu on my netbook and I have not (yet) encountered any problems with the logout/shutdown menu.

There may be some conflict/dependency dilemma when you add LXDE to an existing Ubuntu installation - hopefully some other users will chip in soon.

If you are keen to use LXDE, then you may wish to install Lubuntu first and then add other software later.

I will check the version of lxsession-logout on my netbook when I arrive home later.

Kind regards

---

### Post by King of Heart 4711 on 2015-02-10
By spamming the I mean contentiously going to "menu -> logout" until the dialog appears.

Just installed a clean Ubuntu 14.04 with LXDE installed on top (normal LXDE not Lubuntu) but issue is also apparent without Ubuntu modifications in Lubuntu.
once the logout menu/dialog appears, it will work without issue.

---

### Post by tea for one on 2015-02-10
As promised earlier, here is the version of lxsession-logout in Lubuntu 14.04:-

```
0.4.9.2+git20140410-0ubuntu1
```

My Lubuntu version is 32bit from the 14.04 release in April 2014.

I notice that your version is slightly different i.e. xxxxxxxxxxxxxx1.1_amd64.deb.

I doubt if 32 bit and 64 bit software behave differently, however yours is not the same version as mine.

I also have a Desktop, where I use Ubuntu 14.04 (64 bit) with Gnome Shell and the lxsession-logout version available via synaptic is:-

```
0.4.9.2+git20140410-0ubuntu1
```

Have you installed Synaptic to see which version is available? Possibly the LXDE bundle automatically installs a version that is not 100% compatible with Ubuntu?

I would be interested to hear the outcome.

Best wishes

---

### Post by herend on 2015-05-22
I verify this issue. Ubuntu 15.04, lubuntu desktop.
Dialog of lxsession-logout appears only at first time, never again. Despite of clicking on logout icon, or start it manually.
It can be seen in running process, if i kill it, it can appear again. 

Our pc has more users, if one of them logs out, the others can not. :) Because lxsession-logout is running, and it cannot be asked to appear again.

It seems to be a bug.

---

### Post by avol on 2016-05-03
The problem still exists in Ubuntu 16.04.
Did anyone has any solution or write bugreport?

---

### Post by avol on 2016-05-09
Bug on lauchpad: [https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1534798](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1534798)

---

### Post by papiaud on 2016-12-08
hello,
again, thanks Avol for your temporarily solution
again : when this bug will be fixed ?
Why this bug appeared ? Two weeks ago I had no problem
On my computer I had only administrator user, I added recently a common user.
On the common user I have this problem
But if I logon my account and logout immediately it works . So what is done to disable automatically this command lxsession-logout ?
Thanks to give me some answers on this bug and is there a shorter solution to logout than the one given by avol ?

---

### Post by papiaud on 2016-12-19
hello
me again, I am sorry but it is disappointing to see that there is no answer or correction for this bug.
Please @avol or @kingofheart  have you solved this problem ? And what was your latest solution ?
Thanks for any reply.

---

### Post by sleppa on 2017-02-08
Well, I've been upset by this problem for a loong time and, as dumb as it seems, I just got it fixed with a simple "sudo apt-get install lxsession-logout". There.

---

### Post by yermawsbit on 2017-02-08
Brilliant!  I've been looking to the solution to this for about 30 minutes.  Thankyou!

---

### Post by pwomack on 2017-11-10
> **sleppa said:**
> Well, I've been upset by this problem for a loong time and, as dumb as it seems, I just got it fixed with a simple "sudo apt-get install lxsession-logout". There.

Thank you! I can now run lxde-logout from the command line.

Now I just need to get a entry into the panel, top right.

Baby steps.

 BugBear

---

