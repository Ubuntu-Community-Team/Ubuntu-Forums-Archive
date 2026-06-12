---
title: "Installed ubuntu-desktop over Kubuntu"
date: 2006-08-25
forum: Desktop Environments
---

### Post by ThrobbingBrain66 on 2006-08-25
but for some reason I can't login to ubuntu.  I can still login to Kubuntu however....ive installed ubuntu-desktop over Kubuntu a few times and never had this happen.  To explain further, i get to the login screen to enter my userid and password....however, if i try to login to gnome, the screen just stays on a brown background and nothing happens.  anyone ever have this happen?

---

### Post by ThrobbingBrain66 on 2006-08-25
bump

---

### Post by aysiu on 2006-08-25
Have you tried creating a new user and seeing if that new user can log into Gnome?

---

### Post by ThrobbingBrain66 on 2006-08-25
> **aysiu said:**
> Have you tried creating a new user and seeing if that new user can log into Gnome?

I just tried this and it did not make a difference.  I still stall out after I type in the username and password. My computer doesn't freeze up or anything like that...it just kind of hangs.

EDIT:  Seems I spoke too soon.  Gnome DOES load....it just takes a really long time.  I'm guessing around 3-4 minutes.  any ideas there?

---

### Post by aysiu on 2006-08-25
That's really weird. So, let me get this straight.

You log into KDE, and it loads up immediately (or in a timely fashion). This happens with both your regular user and your new test user.

You log into Gnome, and you get a brown screen. You can still move your mouse cursor around (so it hasn't frozen), but it takes 3-4 minutes to get a working desktop. This happens for both users.

Is that correct?

---

### Post by ThrobbingBrain66 on 2006-08-25
> **aysiu said:**
> That's really weird. So, let me get this straight.

You log into KDE, and it loads up immediately (or in a timely fashion). This happens with both your regular user and your new test user.

You log into Gnome, and you get a brown screen. You can still move your mouse cursor around (so it hasn't frozen), but it takes 3-4 minutes to get a working desktop. This happens for both users.

Is that correct?

You are exactly correct.

---

### Post by aysiu on 2006-08-25
Hm.

And the only thing you did was install *kubuntu-desktop*? That's weird.

Have you tried removing *ubuntu-desktop*? If you installed it with *aptitude* and updated beforehand, you should be able to remove it with this command: ```
sudo aptitude remove ubuntu-desktop
``` If not, then you may have to use this workaround (which isn't perfect) to remove it: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

See if that makes a difference. If it does, and you still want Gnome, you might want to try installing *gnome* or *gnome-core* instead of *ubuntu-desktop*.

---

### Post by ThrobbingBrain66 on 2006-08-25
> **aysiu said:**
> Hm.

And the only thing you did was install *kubuntu-desktop*? That's weird.

Have you tried removing *ubuntu-desktop*? If you installed it with *aptitude* and updated beforehand, you should be able to remove it with this command: ```
sudo aptitude remove ubuntu-desktop
``` If not, then you may have to use this workaround (which isn't perfect) to remove it: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

See if that makes a difference. If it does, and you still want Gnome, you might want to try installing *gnome* or *gnome-core* instead of *ubuntu-desktop*.

I started out a couple days ago with a fresh Kubuntu install and got it all customized to my liking.  Then today I installed ubuntu-desktop, and as I mentioned it takes close to 5 minutes to load completely.  I did use aptitutde to install it and I have removed it and reinstalled it a few times to try and fix it.  the time i removed it however, i didn't use the purge command to get rid of the config files....could this help?

---

### Post by aysiu on 2006-08-25
> **ThrobbingBrain66 said:**
> I started out a couple days ago with a fresh Kubuntu install and got it all customized to my liking.  Then today I installed ubuntu-desktop, and as I mentioned it takes close to 5 minutes to load completely.  I did use aptitutde to install it and I have removed it and reinstalled it a few times to try and fix it.  the time i removed it however, i didn't use the purge command to get rid of the config files....could this help?
You could always try.

Remember there are also configuration files in your Home directory, too:

/home/throbbingbrain/.gnome
/home/throbbingbrain/.gnome2
/home/throbbingbrain/.gconf
/home/throbbingbrain/.gconfd
/home/throbbingbrain/.metacity
/home/throbbingbrain/.nautilus

---

### Post by ThrobbingBrain66 on 2006-08-25
thanks for all your help.  assuming this last attempt doesnt work, how does installing ubuntu on a seperate partition sound?  I assume I can use the same swap and home partitions that i use in kubuntu right?

---

### Post by aysiu on 2006-08-25
It's kind of sad that it would come to that. The situation you're in (Kubuntu and Ubuntu interfering with one another) isn't extremely uncommon, but it *does* happen from time to time.

Theoretically, of course, Kubuntu and Ubuntu can use the same /home partition (certainly the same swap), but theoretically they should be able to exist on the same partition, too--apparently, on your computer they can't. So there's no telling what will happen if they share the same /home.

I'm sorry this is happening to you, but I'll try to help out any way I can.

---

