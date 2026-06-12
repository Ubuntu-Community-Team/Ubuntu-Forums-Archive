---
title: "Unable to install GUI after uninstalling unity in 11.10"
date: 2012-09-16
forum: Desktop Environments
---

### Post by aluminum on 2012-09-16
Hello,
I am having a very troublesome issue.

It all began after I upgraded from Ubuntu 11.04 to 11.10. The default interface in 11.10 is Unity, and I wanted to switch to gnome. I followed the directions on this site [http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html]("http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html"). 
After restarting the computer, I had no GUI to speak of. It would load into a black screen with text (a non-graphical interface?)
I could still use the terminal with ctrl+alt+f1, however, many errors began showing up.
When trying to install anything with apt-get each package had "Failed to fetch" in front of it and it finally said ```
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
None of this has solved the issue.

In addition, when logging in it states ```
New release '12.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

And when I do so it states the following ```
Checking for a new ubuntu release.
No new release found.
```

I hope someone can help. I'll be glad to provide more info if necessary. 

Thanks,
aluminum

---

### Post by DogMatix on 2012-09-16
How far through the directions given on that link did you get before you lost your desktop environment. They seem to be badly translated instructions. I wouldn't feel confident following them at all. Step 1 seems OK but the following steps would make me a little nervous. You don't have to remove Unity to install Gnome you can choose a Gnome session at the login screen. Did you get a Gnome desktop working at all?

Regarding the 'Unable to fetch some archives' error I was wondering if your internet connection is still working OK?

Hopefully someone a little more clued up on things will be along shortly to offer you more productive advice.

---

### Post by aluminum on 2012-09-16
> **DogMatix said:**
> How far through the directions given on that link did you get before you lost your desktop environment. 
I did them all. Then I restarted my computer to see if it worked.
> **DogMatix said:**
> They seem to be badly translated instructions. I wouldn't feel confident following them at all. Step 1 seems OK but the following steps would make me a little nervous. You don't have to remove Unity to install Gnome you can choose a Gnome session at the login screen. Did you get a Gnome desktop working at all?
No, gnome never worked at all. 

> **DogMatix said:**
> Regarding the 'Unable to fetch some archives' error I was wondering if your internet connection is still working OK?
Internet is fine. I am using the same connection now. 

> **DogMatix said:**
> Hopefully someone a little more clued up on things will be along shortly to offer you more productive advice.
Thanks for the reply. I hope so too.

---

### Post by kansasnoob on 2012-09-17
This would have been a much safer approach:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

But now that it's broken try opening a terminal again and running:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

```
sudo apt-get -f install
```

---

### Post by aluminum on 2012-09-21
@Kansasnoob, thanks but that didn't work. The problem I have I think is separate from the GUI issue. It is an apt-get issue which prevents me from downloading any packages. As described above, it simply says "failed to fetch" before every package.

I am still looking for some help!

---

