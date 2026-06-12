---
title: "Making Ubuntu &quot;Cross-GUI&quot;?"
date: 2007-06-08
forum: Desktop Environments
---

### Post by galvao on 2007-06-08
Greetings.

I'm relatively new to Linux, although I have an above average knowledge, and I'm totally new to Ubuntu.

I recently installed the latest version here (Ubuntu 7.04) and I've noticed it came with Gnome as the default Desktop Environment. That's ok by me, I really don't have a Desktop Environment preference yet, but anyway:

I've installed KDE 3.5 and I've noticed some weird things, like:

1) KDE can't  lock screen
2) The default file browser is Nautilus...

Are there any problems to install one flavor of Ubuntu and then switching to another Desktop Environment?

How can I solve this? If i want to change between DE's I MUST re-install another flavor?

TIA,

---

### Post by merlinus on 2007-06-08
You have to install the other DE flavors.  There are many besides GDM and KDE, e.g. xfce, fluxbox, icewm.

You can select which to use at the login screen.

You can also use a script to switch between them without having to log out each time:

[http://doc.gwos.org/index.php/VirtualX](http://doc.gwos.org/index.php/VirtualX)

-merlin

---

### Post by tgm4883 on 2007-06-08
also is should be mentioned that installing KDE isn't the same as kubuntu.

You can install kubuntu by apt-get install kubuntu-desktop

---

### Post by galvao on 2007-06-08
So let me see if I've got this right:

I should uninstall KDE and install Kubuntu. 

And I'll still be able to switch between KDE and Gnome at the startup screen.

Correct?


Thanks,

---

### Post by tgm4883 on 2007-06-08
No, installing KDE is fine.  You can switch between window managers either way.  I just wanted to post that if you were looking for kubuntu, then you should install kubuntu-desktop, not kde

---

### Post by Orochi on 2007-06-08
> **tgm4883 said:**
> No, installing KDE is fine.  You can switch between window managers either way.  I just wanted to post that if you were looking for kubuntu, then you should install kubuntu-desktop, not kde
I'm also interested in being able to switch between GNOME and KDE. What's the difference between installing kubuntu-desktop and installing KDE?

---

### Post by tgm4883 on 2007-06-08
kubuntu-desktop would give you everything that was installed by default in kubuntu. KDE is just KDE

:EDIT:

There are also some minor changes about looks and such

---

### Post by MaindotC on 2007-06-08
KDE requires a lot less resources than other DE's, as well (all other factors being equal).

---

### Post by tgm4883 on 2007-06-08
> **strAlan said:**
> KDE requires a lot less resources than other DE's, as well (all other factors being equal).

Proof?  I find it hard to believe that it uses less resources than say Xfce or IceWM

---

### Post by merlinus on 2007-06-08
Good info on this here:

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Also see the pages there on installing other de's.

-merlin

---

### Post by galvao on 2007-06-08
Ok, guys. Just two more questions (the first one is kinda obvious, but better safe than sorry):

1) If I uninstall KDE I shouldn't have any problems, since I'm using Ubuntu and I've already made Gnome my default DE. Correct? Any special advices?

2) Now when I try to lock screen with Gnome I get the error message "Screen saver is not running". Is it something related with the mess that took place here since I've installed KDE? Or is it a new problem?

TIA,

---

### Post by MaindotC on 2007-06-09
> **tgm4883 said:**
> Proof?  I find it hard to believe that it uses less resources than say Xfce or IceWM

Sorry, no proof.  Just someone I know who is really reputable on Linux told me.

---

### Post by tgm4883 on 2007-06-09
> **strAlan said:**
> Sorry, no proof.  Just someone I know who is really reputable on Linux told me.

You might want to question them on it, as it makes no sense

---

### Post by timothy_duncan on 2007-07-22
hi all,

instead of posting another question, i will just post here since my question is related to this post.  I've installed Ubuntu feisty and I'm really a kubuntu guy ever since 6.06.  I want to install kubuntu desktop and completely remove ubuntu.  will there be any issues or errors i might encounter.  i really want a working unit and i'm not a typical linux geek.  my point is, i want to spend more time using linux instead of installing and uninstalling them when problem arises..

thanks

---

### Post by xubu_caapn on 2007-07-22
> **tgm4883 said:**
> You might want to question them on it, as it makes no sense

I agree. It's a ridiculous statement.:lolflag:

---

### Post by xubu_caapn on 2007-07-22
> **timothy_duncan said:**
> hi all,

instead of posting another question, i will just post here since my question is related to this post.  I've installed Ubuntu feisty and I'm really a kubuntu guy ever since 6.06.  I want to install kubuntu desktop and completely remove ubuntu.  will there be any issues or errors i might encounter.  i really want a working unit and i'm not a typical linux geek.  my point is, i want to spend more time using linux instead of installing and uninstalling them when problem arises..

thanks

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
to remove gnome, do this command:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

i can't guarantee there'll  be no problems, as i've never done this.

---

