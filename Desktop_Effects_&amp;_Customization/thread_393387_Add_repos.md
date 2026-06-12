---
title: "Add repos"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by Chris4 on 2007-03-25
Not working out for me I'm afraid. This is just the first of my problems.
I'm following [this]("http://ubuntuforums.org/showthread.php?t=263851") guide to install Beryl. So Step 1 add the repos...

```
sudo apt-get update
```

I get..

```

...
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures were invalid: BADSIG 3FF0DB166A7476EA Nicholas Thomas (Repository signing key) <root@lupine.me.uk>
W: You may want to run apt-get update to correct these problems

```

Then..

```
sudo apt-get upgrade
```

I get..

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  nvidia-kernel-2.6.17-11-386: Depends: nvidia-kernel-common (>= 20050829) but it is not installed
  nvidia-kernel-source: Depends: dpatch (>= 2.0.0) but it is not installed
E: Unmet dependencies. Try using -f.


```

Then..

> sudo apt-get dist-upgrade

I get..

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  nvidia-kernel-2.6.17-11-386: Depends: nvidia-kernel-common (>= 20050829) but it is not installed
  nvidia-kernel-source: Depends: dpatch (>= 2.0.0) but it is not installed
E: Unmet dependencies. Try using -f.

```


So after that I go to system>admin>software sources and add this:
```
deb http://ubuntu.beryl-project.org edgy main
```

then I get...

```
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures were invalid: BADSIG 3FF0DB166A7476EA Nicholas Thomas (Repository signing key) <root@lupine.me.uk>

```

All nvidia drivers are installed using Envy

Any help appreciated :(

---

### Post by Waappu on 2007-03-26
Hi

Type in terminal```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```
That will add GPG key. I think you miss that step from guide. Type in terminal ```
sudo apt-get update
```
Now sources.list should be ok



This isn't in guide but next you can do these steps to install Beryl:

Use envy to install nvidia driver and let it configure your xorg.conf. I think it's easiest way install driver.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Then type in terminal```
sudo aptitude install beryl emerald emerald-themes
```

---

