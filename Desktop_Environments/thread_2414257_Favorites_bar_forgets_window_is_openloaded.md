---
title: "Favorites bar forgets window is open/loaded"
date: 2019-03-07
forum: Desktop Environments
---

### Post by alan-james-gale on 2019-03-07
if this is in the wrong section, I do appologise, I be happy if it was moved.

OK, so I'm not new with stuff, but all I can see is names that is presented with me, and no google fu can come up with an answer, so searching here gives me only 4 items with nothing to do with the "Favorites bar"

but the issue is, after a few hours or so, the favorites bar refreshes or something, and loaded chromium is forgotten, and the icon is showing its not loaded, clicking the icon usually pulls the window front, but instead loads a new session, whilst the old session is still working fine, I have to Alt-Tab to the window instead (which can be a little annoying tabbing though several windows over a single click.)

so on that note, I don't know what you need for "Logs" and "Stats" to prove something is happening, but I do have a little screenshot:
[img]https://i.imgur.com/Wc922yh.png[/img]

Shows thunderbird loaded, but the focused window chromium, not loaded in the bar..

---

### Post by alan-james-gale on 2019-04-07
Wowee! look at all the activities here boys! not even one person cares to look!

---

### Post by QIII on 2019-04-07
The view counter is broken.  There may in fact have been hundreds of views.  

If you do not receive a reply within 12 hours, feel free to bump your thread back to the top.

Nobody goes looking at the bottom of the sea for something that drifted down to sink into the muck.  Don't blame the community if your thread gets covered.

---

### Post by alan-james-gale on 2019-07-22
> **QIII said:**
> The view counter is broken.  There may in fact have been hundreds of views.  

If you do not receive a reply within 12 hours, feel free to bump your thread back to the top.

Nobody goes looking at the bottom of the sea for something that drifted down to sink into the muck.  Don't blame the community if your thread gets covered.

yeah, good point, Le BUMP, back to the 1st page we go then ;)

Still happening mind you.

---

### Post by alan-james-gale on 2019-08-02
still nothing? bump again..

---

### Post by coffeecat on 2019-08-04
Hi there. Sorry to see that you are not getting any responses for your specific problem. From your screenshot it appears you are using the gnome desktop. Although now the default desktop for Ubuntu, my impression is that probably fewer than 50% of forum members use gnome, when you consider the number that use other flavours such us Xubuntu, Mate or Lubuntu, or eccentrics such as myself who dislike gnome so much they install the now-discontinued Unity desktop. Perhaps there has been no one who would know what the problem is who has seen your thread. To increase visibility a bit, I've added the gnome prefix to your thread title. 

Although I have scant gnome desktop experience, I do have a few suggestions that may help to narrow down what the problem might be. The question in my mind is whether this is a bug in gnome, or in chromium, or whether something funky has happened with your account settings.

Is this only affecting chromium, or do you see the same behaviour with icons for other apps? If only chromium, and if you have no objections to trying out the proprietary Chrome browser (which is 99% chromium anyway), try installing Chrome and see if you get the same thing. Chrome is not in the Ubuntu repositories; you have to download and install it from here: [https://www.google.com/chrome/](https://www.google.com/chrome/)

And/or try creating another account. Log into that, and see if the chromium browser icon misbehaves in the new account. If it doesn't misbehave in a new account, then it would suggest a problem in your account settings somewhere.

---

### Post by alan-james-gale on 2019-09-16
> **coffeecat said:**
> Hi there. Sorry to see that you are not getting any responses for your specific problem. From your screenshot it appears you are using the gnome desktop. Although now the default desktop for Ubuntu, my impression is that probably fewer than 50% of forum members use gnome, when you consider the number that use other flavours such us Xubuntu, Mate or Lubuntu, or eccentrics such as myself who dislike gnome so much they install the now-discontinued Unity desktop. Perhaps there has been no one who would know what the problem is who has seen your thread. To increase visibility a bit, I've added the gnome prefix to your thread title.

Well now, im using Ubuntu 18.04.3 LTS, so is it now a "discontinued Unity desktop?" wow. so there is no one caring to support it for another year? Seriously, its "Long Term Support", 5 year service, if ubuntu/Canonical is not living up to its promised commitments, see you all later.

> **coffeecat said:**
> Although I have scant gnome desktop experience, I do have a few suggestions that may help to narrow down what the problem might be. The question in my mind is whether this is a bug in gnome, or in chromium, or whether something funky has happened with your account settings.

as in my local login? possibly. not into restarting that now, i'll do that on 20.04LTS.

> **coffeecat said:**
> Is this only affecting chromium, or do you see the same behaviour with icons for other apps? If only chromium, and if you have no objections to trying out the proprietary Chrome browser (which is 99% chromium anyway), try installing Chrome and see if you get the same thing. Chrome is not in the Ubuntu repositories; you have to download and install it from here: [https://www.google.com/chrome/](https://www.google.com/chrome/)

Its installed, it only happens to Chromium. not one other program. I don't use chrome for personal use, since I use multiple google accounts, and it demands and forces you to sign in the browser to that account and basically logs all your usage, that's the reason why I use Chromium. I was using firefox, till things gotten funky there (I cant remember what, but there was a major issue using it last year.)

> **coffeecat said:**
> And/or try creating another account. Log into that, and see if the chromium browser icon misbehaves in the new account. If it doesn't misbehave in a new account, then it would suggest a problem in your account settings somewhere.

Fine fine.. that means moving at least the bookmarked and histories across so I have a reason to use it.. I'll update when I have some info.

Anyway, its only a papercut, 3rd party even, maybe thats why its getting ignored.

---

### Post by CatKiller on 2019-09-16
You should try to be less hostile to other users that might volunteer to help you in their own free time for no other reward. 

> **alan-james-gale said:**
> Well now, im using Ubuntu 18.04.3 LTS, so is it now a "discontinued Unity desktop?" wow. so there is no one caring to support it for another year? Seriously, its "Long Term Support", 5 year service, if ubuntu/Canonical is not living up to its promised commitments, see you all later.
Unity was a desktop environment that Canonical introduced in 2010 to unify their desktop and mobile ambitions. The mobile side never took off, so they switched to Gnome as their default with 18.04 to focus their development resources elsewhere. That has absolutely nothing to do with Long Term Support: were you using 16.04, which is still supported, Unity would still be your default.

Your task bar issue is because you have a mismatch between the name of the .desktop file that controls the launcher and the WM_CLASS of the window that it creates. Renaming your file, or creating a new one to use, so that it matches the WM_CLASS of your application's window will make it work as the others do.

---

### Post by deadflowr on 2019-09-17
Do you know which chromium version is installed?
Is it the legacy apt package version?
Or the newer snap package version?

If installed through Software program, it's more likely the snap version.

---

### Post by alan-james-gale on 2019-09-18
Yeah, its Snap:
Version 76.0.3809.132 (Official Build) snap (64-bit)

---

### Post by alan-james-gale on 2019-09-18
> **CatKiller said:**
> You should try to be less hostile to other users that might volunteer to help you in their own free time for no other reward. 
You're right, im sorry

> **CatKiller said:**
> Your task bar issue is because you have a mismatch between the name of the .desktop file that controls the launcher and the WM_CLASS of the window that it creates. Renaming your file, or creating a new one to use, so that it matches the WM_CLASS of your application's window will make it work as the others do.

should a simple "remove from favorites" and add it back be enough? or do I need to edit the "chromium_chromium.desktop" file? i don't see a WM_CLASS in it, a "StartupWMClass=chromium" maybe?

---

### Post by CatKiller on 2019-09-18
> **alan-james-gale said:**
> should a simple "remove from favorites" and add it back be enough? or do I need to edit the "chromium_chromium.desktop" file? i don't see a WM_CLASS in it, a "StartupWMClass=chromium" maybe?
I'm typing from my phone, so I can't check, but I believe the WM_CLASS of the Chromium window is "chromium_browser". You could rename the file to that, or create a new one called that with the same stuff in. There are tools that will allow you to find out the window properties of a given window but, again, I can't check just now. (Edit: from a quick search, **xprop** is probably what I was thinking of: you can then click on any window and it will print out all of its properties.) 

Alternatively, you've already found the StartupWMClass entry, which should allow you to set the WM_CLASS to whatever you want. It doesn't actually matter what the file is called or what the class is, so long as they match: that's how the launcher keeps track of which entry gets the dot when the application is already open.

---

### Post by alan-james-gale on 2019-09-18
ok, it says 

```
WM_CLASS(STRING) = "chromium", "Chromium"
```

im wondering if it has 2 items written in the string, next time the bar refreshes or what ever, it thinks instead of "Chromium" it looks for "chromium" and doesn't see the other one?

---

### Post by PaulW2U on 2019-09-19
I'm not sure what I can add to this thread but I have the snap version of Chromium installed and the .desktop file is called 'chromium_chromium.desktop', a naming convention that seems to apply to all snaps. The file is located in '/var/lib/snapd/desktop/applications/'.

I see 'StartupWMClass=chromium' but no 'WM_CLASS(STRING)' entry in the .desktop file. Everything is working as it should apart from the known bugs or limitations of running the snap version of Chromium. As I am aware the snap is listed correctly in menus and docks.

[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap) is a list of issues currently affecting the Chromium snap but I don't see your issue or anything similar listed.

Does the discussion on bug [1750243]("https://launchpad.net/bugs/1750243") help clarify what is needed in the .desktop file?

---

### Post by vanadium on 2019-09-19
So to continue diagnosis, temporarily remove the snap version and install the regular "apt" version: 'sudo apt install chromium-browser' to see if the issue also persists with that version. The snap package format is rather new, so it is not unlikely that the issue is related to the packaging format.

---

### Post by alan-james-gale on 2019-09-20
> **vanadium said:**
> So to continue diagnosis, temporarily remove the snap version and install the regular "apt" version: 'sudo apt install chromium-browser' to see if the issue also persists with that version. The snap package format is rather new, so it is not unlikely that the issue is related to the packaging format.

I'll see how it goes

---

