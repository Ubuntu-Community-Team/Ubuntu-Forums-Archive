---
title: "Installing drivers for a game"
date: 2007-03-14
forum: Gaming &amp; Leisure
---

### Post by lawentzel on 2007-03-14
I am installing a game, and it requires Allegro drivers.  During the installation it requires me to run a command as follows.

```
su -c "make install"
```

When I do, it asks me for a password.  I am assuming this is the normal password I use for logging in and so forth.  When I type it in, I am getting the following.

> su: Authentication failure
Sorry.

So... what am I doing wrong?  Does Ubuntu have any other passwords other then the default one I set up for my login?  Thanks in advance.

---

### Post by mac.ryan on 2007-03-14
I am far from being a linux guru, but intuitively, I would type

```
sudo make install
```

In my understanding of the manual of "su", the option "-c" simply run a command, and therefore "sudo" should work the same.

Alternatively you could type

```
sudo -i
make install
```

in this way - however - you will be logged for the full session as root, therefore you should really pay attention to what you will be typing!

---

### Post by lawentzel on 2007-03-15
Thank you for your help.  The first command:

```
sudo make install
```

Did the trick.  I am one step closer to playing Kraptor!  Got Allegro installed, just need to get the audio files installed.  (Dumb)  And I am good to go.

---

### Post by Lystrodom on 2007-03-15
Yeah, su asks for your root password, which you have to explicitly set up, by doing```
sudo passwd
```

But there's not much point to it, unless you prefer to be logged in as root.

---

