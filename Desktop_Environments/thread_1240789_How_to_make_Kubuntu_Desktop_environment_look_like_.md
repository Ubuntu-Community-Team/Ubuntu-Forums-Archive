---
title: "How to make Kubuntu Desktop environment look like Windows XP"
date: 2009-08-15
forum: Desktop Environments
---

### Post by shanali4 on 2009-08-15
[SIZE=4]I yestterday switched to Kubuntu from Windows XP. I m new linux useer. Kubuntu desktop environment is too dificult to understand for me. Is there anyway to make it look like XP. so it would be easy for me to use Kubuntu.[/SIZE]

---

### Post by Chronon on 2009-08-15
You could apply a theme, but it will only be cosmetic.  

Any particular trouble you're having?

---

### Post by lisati on 2009-08-15
You might find this thread interesting: [http://ubuntuforums.org/showthread.php?t=462353](http://ubuntuforums.org/showthread.php?t=462353)

---

### Post by XubuRoxMySox on 2009-08-15
I use a different desktop environment that looks and acts much more "familiar" than KDE does, and it is *much* lighter on resources than KDE or WinXP.

In fact the reason I use it is *because* it has that XP-like familiarity and simplicity, *and* because it's so lightweight that it makes that old low-resource computer fly along at mind-bending speed.

A lot of kids share this computer at a dance studio, and I wanted everybody to be able to just sit down and use it without needing instructions and without the "geek mystique" associated with the very mention of the word Linux.

I suggest regular Ubuntu, and after it installs and updates, just add the LXDE desktop using this command in a terminal window:

```
sudo apt-get install lxde
```

Or use Synaptic Package Manager to install it.

Then log out. When you log back in you'll see an "Options" menu on the lower left of the Login screen. Use it to choose LXDE as your Session (you can make it the default session if you wish), then log in.

Your applications appear as icons in the folder *usr/share/applications*. Using LXDE's built in (and super-simple) file manager, take the applications you want and drag their icons to the desktop. Or if you prefer, put them in the task bar.

I renamed some of the icons just in case some of the kids didn't recognize the names. The Firefox icon, for example, I renamed "Browse the Web," and OpenOffice Writer is renamed "Word Processor," etc. Kids have no trouble doing everything they need to. I get regular compliments about how fast and easy that computer is. And people are amazed to learn that it's a Linux machine!

Click on my signature for more info on this super-simple, super lightweight desktop environment. I've become a major fanboy.

-Robin

---

### Post by SuperSonic4 on 2009-08-15
> **dixiedancer said:**
> I use a different desktop environment that looks and acts much more "familiar" than KDE does, and it is *much* lighter on resources than KDE or WinXP.

In fact the reason I use it is *because* it has that XP-like familiarity and simplicity, *and* because it's so lightweight that it makes that old low-resource computer fly along at mind-bending speed.

A lot of kids share this computer at a dance studio, and I wanted everybody to be able to just sit down and use it without needing instructions and without the "geek mystique" associated with the very mention of the word Linux.

I suggest regular Ubuntu, and after it installs and updates, just add the LXDE desktop using this command in a terminal window:

```
sudo apt-get install lxde
```

Or use Synaptic Package Manager to install it.

Then log out. When you log back in you'll see an "Options" menu on the lower left of the Login screen. Use it to choose LXDE as your Session (you can make it the default session if you wish), then log in.

Your applications appear as icons in the folder *usr/share/applications*. Using LXDE's built in (and super-simple) file manager, take the applications you want and drag their icons to the desktop. Or if you prefer, put them in the task bar.

I renamed some of the icons just in case some of the kids didn't recognize the names. The Firefox icon, for example, I renamed "Browse the Web," and OpenOffice Writer is renamed "Word Processor," etc. Kids have no trouble doing everything they need to. I get regular compliments about how fast and easy that computer is. And people are amazed to learn that it's a Linux machine!

Click on my signature for more info on this super-simple, super lightweight desktop environment. I've become a major fanboy.

-Robin

Don't do it that way - that just uses unnecessary bandwidth and the bloat of ubuntu is still on your pc. Instead grab the minimal cd [here]("https://help.ubuntu.com/community/Installation/MinimalCD") and run ```
sudo apt-get install lxde
``` which gives lxde without ubuntu stuff. You can also pick and choose what to install such as epiphany or abiword etc

---

### Post by XubuRoxMySox on 2009-08-15
> **SuperSonic4 said:**
> Don't do it that way - that just uses unnecessary bandwidth and the bloat of ubuntu is still on your pc. Instead grab the minimal cd [here]("https://help.ubuntu.com/community/Installation/MinimalCD") and run ```
sudo apt-get install lxde
``` which gives lxde without ubuntu stuff. You can also pick and choose what to install such as epiphany or abiword etc

This is correct - a minimal install with LXDE is what I use and the best way to go. 

Sometimes, however, when suggesting a desktop environment to someone who is unfamiliar with it, it's easier to *look at at first*, take it for a "test drive," and *then* decide if it's worth a whole new installation.

Being an LXDE fanboy, I chose the minimal Ubuntu CD installation + LXDE and my favorite applications.

But to *try* it first, it's easy enough to install and easy enough to remove if you don't like it (using Synaptic is the best way).

-Robin

---

### Post by gjoellee on 2009-08-15
I don't think you should do so much about it. Just use two weeks to learn about KDE and Linux and you will soon begin to know KDE. KDE is in fact the desktop environment I find most similar to Windows.

I think you should give KDE a try. Just experiment with everything, and if something suddenly happens that you don't like, just get help in the forums.

---

### Post by Fzang on 2009-08-15
Why did you change to KDE if you want it to look like XP? If it's too hard to use linux you shouldn't have switched.

---

### Post by shanali4 on 2009-08-15
> **dixiedancer said:**
> I use a different desktop environment that looks and acts much more "familiar" than KDE does, and it is *much* lighter on resources than KDE or WinXP.

In fact the reason I use it is *because* it has that XP-like familiarity and simplicity, *and* because it's so lightweight that it makes that old low-resource computer fly along at mind-bending speed.

A lot of kids share this computer at a dance studio, and I wanted everybody to be able to just sit down and use it without needing instructions and without the "geek mystique" associated with the very mention of the word Linux.

I suggest regular Ubuntu, and after it installs and updates, just add the LXDE desktop using this command in a terminal window:

```
sudo apt-get install lxde
```Or use Synaptic Package Manager to install it.

Then log out. When you log back in you'll see an "Options" menu on the lower left of the Login screen. Use it to choose LXDE as your Session (you can make it the default session if you wish), then log in.

Your applications appear as icons in the folder *usr/share/applications*. Using LXDE's built in (and super-simple) file manager, take the applications you want and drag their icons to the desktop. Or if you prefer, put them in the task bar.

I renamed some of the icons just in case some of the kids didn't recognize the names. The Firefox icon, for example, I renamed "Browse the Web," and OpenOffice Writer is renamed "Word Processor," etc. Kids have no trouble doing everything they need to. I get regular compliments about how fast and easy that computer is. And people are amazed to learn that it's a Linux machine!

Click on my signature for more info on this super-simple, super lightweight desktop environment. I've become a major fanboy.

-Robin
Thank you very much it solved my problems

---

### Post by shanali4 on 2009-08-15
> **Fzang said:**
> Why did you change to KDE if you want it to look like XP? If it's too hard to use linux you shouldn't have switched.
[SIZE=3]Previously i was using a pirated copy of Windows XP. Then i decided to stop using pirated things so i switched to linux because it is Freeware. Also i want to support Open Source. I love Open Source. I don't want to pay a lot of dollars for buying windows. and also windows is much heavier then linux. Linux is very lighweight[/SIZE]

---

