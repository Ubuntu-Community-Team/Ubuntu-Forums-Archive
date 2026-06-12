---
title: "I cannot see all the icons in the notification area"
date: 2011-04-19
forum: Desktop Environments
---

### Post by Hotshot5000 on 2011-04-19
At the left of the Fusion Icon (see the attachment) there is a small green dot. That is the icon for Skype. How do I make it so that all the icon is shown? Every time I try to move the three small lines to the left (after unlocking of course) hoping to let Skype icon show, I move the Fusion Icon and nothing changes.

---

### Post by Hotshot5000 on 2011-04-19
Anyone?

---

### Post by bond17_007 on 2011-04-19
I am having the exact same problem. I had upgraded my ubuntu to 11.04 beta. I thought it was because of the upgrade. 
Btw, did you try deleting ".Skype" folder found in your home folder?
I un-installed and installed skype, deleted .Skype folder but no luck.
I will hunt around for solution. If I find it I will post.

---

### Post by bcarlowise on 2011-04-21
I have recently installed 11.04 Beta and have noticed that the notification area does not display icons for certain programs like previous versions of ubuntu. For instance, I run truecrypt in order to access some encrypted external drives. Once I mount the encrypted drive and click the "exit" button in truecrypt, the truecrypt icon would normally show up in the notification area.....but not anymore since installing 11.04. This is a problem because I then cannot unmount the drives. Clicking on the Truecrypt app icon produces an error stating that Truecrypt is already running. has anyone else noticed this?

---

### Post by Frogs Hair on 2011-04-21
Take a look at the link.[http://www.webupd8.org/search/label/systray?max-results=10](http://www.webupd8.org/search/label/systray?max-results=10)

---

### Post by Hotshot5000 on 2011-04-22
Looks like it has been fixed by an update.

---

### Post by bcarlowise on 2011-04-22
> **Frogs Hair said:**
> Take a look at the link.[http://www.webupd8.org/search/label/systray?max-results=10](http://www.webupd8.org/search/label/systray?max-results=10)

Thanks for the info. That worked. My only real beef at this point is that it is too convoluted to enable. Should be much easier to do...something that any basic user would feel comfortable doing. The functionality to do so would really best be served by including a simple button or setting within the tray by right clicking on it.

---

### Post by Frogs Hair on 2011-04-22
> **bcarlowise said:**
> Thanks for the info. That worked. My only real beef at this point is that it is too convoluted to enable. Should be much easier to do...something that any basic user would feel comfortable doing. The functionality to do so would really best be served by including a simple button or setting within the tray by right clicking on it.

I will be installing 11.04 next week , I just happened run across that fix while surfing . Hoshot5000 wrote that the issue was solved by an update .

---

### Post by Hotshot5000 on 2011-04-23
The issue was solved but somehow they managed to release another set of updates that brought the problem back. So now the icon is back to being a green dot. What are they doing there?

Note: I use Ubuntu Classic so the above solution doesn't work since it's for Unity desktop and I can't stand that crap.

---

### Post by RebateFX on 2011-04-27
Me too? :)

I am on 11.04 now and the Skype icon is gone at startup (Skype is one of the startup programs). I have to remove and re-add the notification area to get the icon to show. I had a similar problem in 10.10 but I fixed it there by metacity --replace then compiz --replace.

Just wondering, are you guys also using ATI graphics?

---

### Post by Hotshot5000 on 2011-04-28
Yes I have an ATI Radeon 3400 series. From what I've read the issue is with Qt library in Gnome Classic. It sucks, I mean they clearly rushed to launch a flawed and unfinished product. I was hoping to get rid of this and other (lots of) bugs until launch on 28 but it seems we'll have to wait and see....

---

### Post by bond17_007 on 2011-05-17
I did a clean install of Ubuntu 11.04 and the problem still exists. 
I see a small dot instead of full Skype icon on the task bar.
This has started becoming really annoying. Anyone with solution?

---

### Post by neurobot on 2011-06-02
> **Frogs Hair said:**
> Take a look at the link.[http://www.webupd8.org/search/label/systray?max-results=10](http://www.webupd8.org/search/label/systray?max-results=10)

That worked for me too.  I'm running Ubuntu 11.04 Linux 2.6.39-0-generic.  All I did was type in terminal ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

---

### Post by mattzab on 2011-10-11
I'm on gnome and I'm having the same problem. Small dot instead of a full icon.
After hours of searching, still no luck. Anyone know of a fix?

---

