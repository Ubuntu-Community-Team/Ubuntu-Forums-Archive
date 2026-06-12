---
title: "After update today Beryl messed up"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by acwspoon on 2007-04-29
I've been running Beryl for the past couple days with no problem at all.  I have a ATI card and today I got an automatic update that was all Beryl related.  After shutting my computer down and restarting it just now, My beryl is not working, the metacity is.  


Someone help please I have no idea what it could be, Thanks for the help in advance!

---

### Post by rolf-c on 2007-04-29
What Beryl version are you running post-update, and what version where you running pre-update?

---

### Post by acwspoon on 2007-04-29
post update  it is 0.2.1.dfsg+git20070318-0ubuntu2 but i know what the previous install was... I just followed a followed a how to guide and it worked.... I added the beryl deb and then just sudo apt-get update and that's what I used.... do you know the previous version?

---

### Post by rolf-c on 2007-04-29
Hmm.  Pre-update must have been 0.2.0, which is what I'm running.  I see the 0.2.1 sitting and waiting to be loaded on my box, however.  Not sure how easy this is for you, but you could downgrade to 0.2.0.  If that's not simple to you, don't try it without asking your favorite search engine how to downgrade a debian package.

If you force beryl-manager to use Beryl (left click on Beryl icon, goto Select Window manager, click Beryl button), does that make any difference?

---

### Post by acwspoon on 2007-04-29
Yeah I'll check out some downgrading stuff, but My windows manager is on beryl right now but it's still running metacity and if i click metacity and then back to beryl it still doesn't do anything but ill check out some downgrading hopefully that will work.. thanks  ill post back on here if that works

---

### Post by acwspoon on 2007-04-29
alright so I figured it out... you have to go to synaptic and click on beryl and press control+e and it gives you the option of a downgrade... but how would i prevent it from doing the automatic update

---

### Post by rolf-c on 2007-04-29
This is weak, but I know there is a way to tell Synaptic to stay on a particular version of any file...I'll have to search for that option, though, because I don't know it off hand.  My apologies, I will find it and post here.  For now just ignore those upgrade suggestions (if downgrading worked for you, that is).

---

### Post by rolf-c on 2007-04-29
I should have looked before my last post -

To lock a particular version in Synaptic:

Launch Synaptic Package Manger

Left click on the package you wish to lock

Click on the Package menu and select 'Lock version'

:)

---

### Post by acwspoon on 2007-04-29
Awesome, Everything is working again and the update is gone, thanks so much for the help!  I really appreciate it!  Hopefully eventually I can update beryl eventually without it screwing up

---

### Post by nuttiplutt on 2007-04-30
I have the same problem that I got a message of updating through Update manager from Beryl 0.2.1 to 0.3.0, but after the update, Beryl doesn't work. When I try to choose Beryl as window manager, it flickers and goes back to Metacity. I've tried to roll back (downgrade) to 0.2.1, but with the same result.

When I first got the message of updating, there were 12 updates and the update manager said that one program had to be uninstalled, but now I don't remember which. It also said that only parts of the updates could be done.

Any advice of how to proceed?

---

### Post by rolf-c on 2007-04-30
I believe the 0.3.x release of beryl is not yet part of the Feisty repositories.  I'm only showing 0.2.1 as the latest version - and I have not installed it.  I'm working fine on 0.2.0.  My only advice to you at this point is downgrade to 0.2.0 and proceed from there.  Likely if 0.3.x is not part of Feisty, you will need to compile from source.

---

### Post by nuttiplutt on 2007-04-30
The only problem is that when I try to downgrade through Synaptic package manager, I can only downgrade to 0.2.1. And the 0.2.1 version worked very well.

I'll try it again... Maybe a reinstallment of Nvidia drivers is nessesary?

---

### Post by rolf-c on 2007-04-30
Well, maybe, but shouldn't need to do that unless you had a kernel change along the way?  

So you're back on 0.2.1, which worked prior to upgrading to 0.3.x, and now downgrading back to 0.2.1 and that's not working now.

Try --purge (or in Synaptic, "Mark for complete removal") for all your beryl goodies, then reinstall 0.2.1.

---

### Post by nuttiplutt on 2007-05-01
I've now uninstalled Beryl completely and then had quite a few problems getting Compiz properly installed, again since I've probably added some repositories that wanted me to upgrade to versions that wasn't still in the Ubuntu standard repository. But after downgrading Compiz to 1.0.3.6, at least Compiz is working fine and I get the famous Cube working.

Now I'm not sure if I dare to install Beryl again if it will ruin my now functioning desktop. Would Beryl interfere too much with Compiz?

---

### Post by rolf-c on 2007-05-01
compiz should not be an issue, in fact if compiz is running successfully I think Beryl should practically drop right on your system without a whimper.

However that is just speculation on my part!

I've got compiz 1:0.3.6 and Beryly 0.2.0 installed and am using the nVidia 9631 driver.

---

