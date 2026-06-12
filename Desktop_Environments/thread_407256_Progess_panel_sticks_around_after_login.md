---
title: "Progess panel sticks around after login"
date: 2007-04-11
forum: Desktop Environments
---

### Post by actuary286 on 2007-04-11
I am running the latest Feisty beta and I am having a strange problem. When I login to Gnome the progress panel that appears between GDM and the desktop sticks around for about a minute after the desktop loads. Here is a screen shot:

[IMG]http://www.rtjmay.ca/images/Screenshot.png[/IMG]

The progress panel stays on top of everything, but doesn't show-up in the workspace switcher.

Any ideas what is going on and how I can correct it? This only started happening in the last few days after I spent a little bit of time playing with the Desktop Effects control panel, which is now turned off.

---

### Post by dbbolton on 2007-04-12
this might be fixed by checking "Automatically save changes to session" in System > Prefs > Session

---

### Post by Azathoth_ on 2007-04-20
> **dbbolton said:**
> this might be fixed by checking "Automatically save changes to session" in System > Prefs > Session

I have the same problem and it doesn't work for me... and all the programs i load on login, doesn't work. I have the wait one minute to have it working
:S :S .S

**These two screenshots are when i log in Gnome (with the errors)**

[http://ubuntuforums.org/attachment.php?attachmentid=30194&stc=1&d=1177069415](http://ubuntuforums.org/attachment.php?attachmentid=30194&stc=1&d=1177069415)

[http://ubuntuforums.org/attachment.php?attachmentid=30195&stc=1&d=1177069415](http://ubuntuforums.org/attachment.php?attachmentid=30195&stc=1&d=1177069415)

**As your can see in the next picture, when i log in Gnome "secure mode" (i have no errors here) i have more processes.**

[http://ubuntuforums.org/attachment.php?attachmentid=30196&stc=1&d=1177069415](http://ubuntuforums.org/attachment.php?attachmentid=30196&stc=1&d=1177069415)

---

### Post by Azathoth_ on 2007-04-20
I have done: sudo dpkg-reconfigure gnome (all gnome's) and sudo dpkg-reconfigure nautilus (all) and no results

---

### Post by Azathoth_ on 2007-04-20
If anyone read it... i have "solved" it creating a new user and moving some folders of my old user. I think that the problem is in .gnome2 .nautilus or other user hidden configuration files

---

### Post by bignickel on 2007-04-20
I had a similar problem when I installed Feisty.  I would arrange icons on the panel, and then when I logged back in they'd be gone.  I just created a new user, logged in under the new user, and copied .gnome*, .metacity, and .nautilus into my old user.  Then I logged back in as myself and everything was fine.  Then i deleted the other user.  Kind of a roundabout way, but it worked.

---

