---
title: "problem installing wine"
date: 2009-04-04
forum: General Help
---

### Post by 2roombas on 2009-04-04
I have 8.04 (Hardy) on my mini and tried to install wine through the repository. The check box would not check at all... so I tried a simple command line install.  I got this message.  What does it mean? What should I do?

[B][INDENT]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
E: Broken packages[/INDENT][/B]

---

### Post by 2roombas on 2009-04-04
I just did a system update via Update Manager. Someone told me that might work on another forum..  I then rebooted and tried it all again...the box "would not" check in the repository, and after trying a command line install again I get the same message as before.  Rats, this mini is less then a month old and I was hoping to get "Bookworm" on it before I go on vacation in a week. Looks like my flight will be boring now.:(

---

### Post by jmszr on 2009-04-04
2roombas,
 For starters```
sudo apt-get update

```
and```
sudo apt-get upgrade
```  

 You might go with:[http://wiki.winehq.org/HowTo](http://wiki.winehq.org/HowTo) and get it straight from WineHQ. It will be the newest version of Wine.

Hope this helps.

---

### Post by 2roombas on 2009-04-04
> **jmszr said:**
> 2roombas,
 You might go with:[http://wiki.winehq.org/HowTo](http://wiki.winehq.org/HowTo) and get it straight from WineHQ. It will be the newest version of Wine.

Hope this helps.

This how-to only shows me how to get the beta. How can I get the latest stable version?

---

### Post by taurus on 2009-04-04
If I were you, I would definitely have a look at the /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by JK3mp on 2009-04-04
> **taurus said:**
> If I were you, I would definitely have a look at the /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

I agree with the above make sure your repository list is in order cause its not installing all its dependencies or something..

---

### Post by 2roombas on 2009-04-04
> **taurus said:**
> If I were you, I would definitely have a look at the /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```
This is what it says after I do that....

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe
multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main
universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main
universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates
main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main
universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security
main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base
main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/)
hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini
main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini
main universe multiverse restricted
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu
8.10 "Hsrdy Ibex"

---

### Post by taurus on 2009-04-04
> **2roombas said:**
> This is what it says after I do that....

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe
multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main
universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main
universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates
main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main
universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security
main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base
main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/)
hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini
main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini
main universe multiverse restricted
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) **[COLOR="Red"]intrepid[/COLOR]** main #WineHQ - Ubuntu
8.10 "Hsrdy Ibex"

Try replacing the **intrepid** from the last line with **hardy** since you are running hardy, not intrepid.

Then save it and run

```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by 2roombas on 2009-04-04
> **taurus said:**
> Try replacing the **intrepid** from the last line with **hardy** since you are running hardy, not intrepid.



How do I do this?  The curser will not move.  Isn't it suppose to be editable in the terminal?

---

### Post by taurus on 2009-04-04
```
gksudo gedit /etc/apt/sources.list
```
or

```
sudo nano -Bw /etc/apt/sources.list
```

---

### Post by 2roombas on 2009-04-04
All fixed now..thank you!:)

---

