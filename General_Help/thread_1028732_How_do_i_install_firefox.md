---
title: "How do i install firefox?"
date: 2009-01-02
forum: General Help
---

### Post by Secret Neo on 2009-01-02
I just got kubuntu and i want firefox but iunno how the hell to install anything. i clicked the icon and it didnt do anything.

---

### Post by ispy on 2009-01-02
open a terminal and use this command:

```
sudo apt-get install firefox
```

---

### Post by stderr on 2009-01-02
I use Ubuntu, but surely Firefox is already installed... I mean, this is how to do it:

```
sudo apt-get install firefox
```

but it should already be installed for you. Try opening a terminal and typing

```
firefox
```

---

### Post by SuperSonic4 on 2009-01-02
> **stderr said:**
> I use Ubuntu, but surely Firefox is already installed... I mean, this is how to do it:

```
sudo apt-get install firefox
```

but it should already be installed for you. Try opening a terminal and typing

```
firefox
```

Konqueror is the default browser in Kubuntu.

```
sudo apt-get install firefox
``` will work fine

---

### Post by Secret Neo on 2009-01-02
its not installed. it says it need the package.

---

### Post by ispy on 2009-01-02
can you copy and paste the output of the command?

---

### Post by Secret Neo on 2009-01-02
sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package firefox-3.0

---

### Post by stderr on 2009-01-02
Could you post the output of:

```
cat /etc/apt/sources.lst
```

and

```
apt-cache search firefox-3.0
```

---

### Post by goinglinux on 2009-01-02
> **Secret Neo said:**
> sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package firefox-3.0

I don't think you need the "firefox-3.0". It should install using simply "firefox" in the command. The Kubuntu package manager installs Firefox 3.0 by default.

---

### Post by Secret Neo on 2009-01-02
the first said no such file or directory and the second did nothing. im doing it in Konsole, is that the right place?

---

### Post by Secret Neo on 2009-01-02
> **goinglinux said:**
> I don't think you need the "firefox-3.0". It should install using simply "firefox" in the command. The Kubuntu package manager installs Firefox 3.0 by default.
 said same thing either way.

---

### Post by SuperSonic4 on 2009-01-02
> **Secret Neo said:**
> the first said no such file or directory and the second did nothing. im doing it in Konsole, is that the right place?

yeah that's right, what if you do it the GUI way in Adept?

---

### Post by stderr on 2009-01-02
Ah, maybe it's sources.list in Kubuntu... try

```
cat /etc/apt/sources.list
```

If not, ignore me, I haven't got a Kubuntu install handy to test :)

---

### Post by goinglinux on 2009-01-02
Which version of Kubuntu are you using? I'm assuming it's 8.10. You might try the graphical method of installing the firefox package:

Kubuntu provides the Adept Package Manager for installing new software packages. In Kubuntu 8.04 and earlier, Adept is usually available from Kubuntu's System selection in the K-Menu. In 8.10, if you click the Kickoff menu and select the Applications tab, choose Add/Remove Programs to start Adept.

   1. After launching Adept, you will be able to search by name or description for the application you want to install.
   2. Right-click the package that you want to install and choose Request Install.
   3. Click the Apply Changes icon in the toolbar and your installation begins.

(Here is a link to an article from my website on how to install software using Linux. It might be useful. [http://goinglinux.com/articles/PackageRepositories.html]("http://goinglinux.com/articles/PackageRepositories.html"))

---

### Post by goinglinux on 2009-01-02
Correction: Just checked on the Kubuntu screen shots page and the Adept Installer is available on the "Computer" tab from the Kickoff menu.

---

### Post by Secret Neo on 2009-01-02
i searched adept for firefox, found nothing. i saved it to a folder, its still there, whats up?

linux is really getting on my nerves.

---

### Post by goinglinux on 2009-01-02
OK, I think Firefox is available in one of the software repositories that is not enabled by default. This link describes what a repository is and how to enable repositories in Kubuntu. [https://help.ubuntu.com/community/Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Kubuntu"). 

You should enable Restricted, Universe and Multiverse, then try your search again.

---

### Post by oilchangeguy on 2009-01-02
before i installed kubuntu 8.10, i was able to install firefox from adept while using the live cd. then installed it again after i installed kubuntu. when you open adept just type firefox in the search bar and press enter. then scroll down the list until you find it, and install it.

---

