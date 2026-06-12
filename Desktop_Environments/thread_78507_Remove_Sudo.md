---
title: "Remove Sudo?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by nixhead on 2005-10-18
Is it possible to remove sudo from Kubuntu without breaking things? I always keep a root submenu which contains apps which are root only, such as firewalls or editors. For instance, I have an menu item titled "Root Editor," with the command for that entry being "kdesu kate." The problem is, kdesu expects the sudo user password, not the root password. (I have already set a separate root password.) If I remove sudo from Kubuntu, will the kdesu command then act normally, ie, accept the root password instead of the sudo user password?

Any help is appreciated.

---

### Post by Takis on 2005-10-18
It could possibly break things. What's wrong with using the sudo password (i.e. your own - or at least, it should be)?

---

### Post by nixhead on 2005-10-18
[QUOTE=Takis]It could possibly break things. What's wrong with using the sudo password (i.e. your own - or at least, it should be)?[/QUOTE]

I am checking out Kubuntu for two friends who wish to try Linux. Neither have used Linux before. They need to learn how to use it correctly. First of all, sudo is very confusing if you wish to teach someone the difference between root and user permissions. If they start out with Kubuntu, they will come to expect the user password to allow root access. If they later wish to switch to a different Linux, it will appear to be broken because it will work correctly, ie a user password will work for user apps, while a root password will work for root only apps. This will leave them thinking any Linux that doesn't use sudo is broken.

I can't recommend Kubuntu for them anyway, since the only KDE video player available in Kubuntu is Kaffeine, which crashes constantly. KDE apps, which integrate perfectly with the KDE environment and work every time without crashing, such as Kplayer or Kmplayer are not available. Lack of a decent KDE video player is a deal breaker, for them as well as myself.

---

### Post by Takis on 2005-10-19
I dunno I kinda like Kaffeine - but, like you say, it does have a tendency to crash left right and centre. I guess because I've managed to stabilise my version I'm a bit more lenient to it now.

Well, don't remove sudo, what you might like to do instead is set the root password, and don't tell your friends about sudo. If you type
```
sudo su
```and then
```
passwd
```you'll set the root password. Then all your friends need to do is 'su' and use the root password.

Of course, you could take the time to teach them the different way that the distros work.

---

### Post by earobinson on 2005-10-19
ya i wouldent remove sudo, that could break a lot of things

---

