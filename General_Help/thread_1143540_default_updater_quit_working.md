---
title: "default updater quit working"
date: 2009-04-30
forum: General Help
---

### Post by paydaydaddy on 2009-04-30
I get the icon showing that updates are available, but when I click on it nothing happens. What should happen is that clicking the icon should open adept installer with a list of available updates. I have synaptic installed and can use it to get updates, but I would like to either get adept working as it should or else make synaptic the default installer/package manager. I tried re-installing adept and the notifier (using synaptic) but it did not change anything. Suggestions Appreciated.

---

### Post by Sef on 2009-04-30
If you are on Kubuntu, then open the Konsole and copy and paste this command:

```
kdesu apt-get update && kdesu apt-get upgrade
```

If you get any error messages, then copy and paste them here.

---

### Post by Zorael on 2009-04-30
I'm assuming you're on 9.04 now.
> **Sef said:**
> If you are on Kubuntu, then open the Konsole and copy and paste this command:

```
kdesu apt-get update && kdesu apt-get upgrade
```

If you get any error messages, then copy and paste them here.
First, **kdesu** is not a valid command in 9.04; only **kdesudo**.
```
$ which kdesu kdesudo
/usr/bin/kdesudo
```
Second, you may as well use **sudo** when performing terminal commands. Do educate me if I'm wrong, but kdesudo is supposed to be a sudo wrapper for graphical applications, calling them as the root user and not your own user elevated to root permissions (which can screw up file permissions in your home folder). Some terminal commands plain won't work when used with kdesudo as opposed to sudo; try **kdesudo nano** and watch it do nothing.
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
Lastly, apt-get in its own glory, **aptitude** can/will often do a better job at resolving dependencies, at the expense of taking extra time to perform the tasks given to it. Usually you needn't worry, but if you're installing/upgrading something with apt-get and it freaks out on you, try aptitude instead.
```
$ sudo aptitude update
$ sudo aptitude safe-upgrade    # comparable to apt-get upgrade
$ sudo aptitude full-upgrade    # comparable to apt-get dist-upgrade, more aggressive upgrading which can remove packages
```


> **paydaydaddy said:**
> I tried re-installing adept and the notifier (using synaptic) but it did not change anything. Suggestions Appreciated.
I'd try reinstalling **kpackagekit** (which replaces Adept in 9.04) to make sure nothing went wrong with it somehow. It may be wise to tag the  update notifier itself for reinstallation, too.
```
$ sudo aptitude **reinstall** kpackagekit update-notifier-kde
```

Else, you may want to try (temporarily) creating a new user when you know there's an update available, and see if the notification works properly for him/her/it. I'm not sure if update-notifier-kde keeps some user-specific settings saved in your home folder, but kpackagekit probably does, and logging in as a new user is an easy way to find out. Just delete it afterwards if you want.

---

### Post by paydaydaddy on 2009-04-30
Thanks for the replies. It turns out that kpackagekit was not installed. I installed it with synaptic. The next time there are updates I will see if it fixed the problem. Oh, and I am using 9.04 which I upgraded from 8.10.

---

