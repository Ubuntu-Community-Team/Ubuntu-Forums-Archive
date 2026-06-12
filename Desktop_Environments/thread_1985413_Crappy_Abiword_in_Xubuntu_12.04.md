---
title: "Crappy Abiword in Xubuntu 12.04"
date: 2012-05-23
forum: Desktop Environments
---

### Post by jacobite on 2012-05-23
The version of Abiword in Xubuntu is so awful it's almost unusable; very poor decision to include version 2.9.2 which is a development release, especially since 12.04 is LTS. The recommended stable release is 2.8.6 but this isn't available from the repositories, as far as I'm aware. Any idea how I can get it? the Abiword site isn't very helpful because all the packages are out of date.

---

### Post by Jose Catre-Vandis on 2012-05-23
You should be able to browse previous packages on the packages/releases page:

[http://packages.ubuntu.com/oneiric/abiword](http://packages.ubuntu.com/oneiric/abiword)

---

### Post by sparklyprgs on 2012-05-23
> **jacobite said:**
> The version of Abiword in Xubuntu is so awful it's almost unusable; very poor decision to include version 2.9.2 which is a development release, especially since 12.04 is LTS. The recommended stable release is 2.8.6 but this isn't available from the repositories, as far as I'm aware. Any idea how I can get it? the Abiword site isn't very helpful because all the packages are out of date.

I gotta admit I replaced Abiword with LibreOffice within a couple of days. Doesn't answer your question, but I also found it not working well with existing documents I had. LO is not as resource hungry as I thought it would be, it's slower, but not hugely.

---

### Post by rai4shu2 on 2012-05-23
The "recommended stable" version (2.8.6) uses gtk 2 libs. Aside from the fact that gtk 2 is deprecate upstream (and therefore not a viable "stable" product), Unity and Gnome Shell both use gtk 3. There was no way devs were going to continue supporting the old Abiword. If you have a problem with all this, take it up with the Gnome devs.

---

### Post by stedevil on 2012-09-25
There is more info in

[http://ubuntuforums.org/showthread.php?t=2004848](http://ubuntuforums.org/showthread.php?t=2004848)

PS Changing to LO is not a solution for opening/editing existing .abw files... a working Abiword is not optional for me and others.

---

### Post by DeceptiveHornet on 2012-09-25
I had the same issue with Abiword. It crashed and has some strange bugs. Took me whole hour until i removed it from the system and installed LibreOffice. 

Then i switched to Kubuntu. Abi has some ways to go before being a pre-installed piece of wordprocessor in a new linux installation.

---

### Post by rai4shu2 on 2012-09-25
Even the old stable version of Abiword was really only good for small projects that weren't very demanding. The only viable long-term solution is to switch to LO. Kubuntu is a good choice, but I think you'll find yourself using more resources in the long run if you go that direction. Most people who use Xubuntu or Lubuntu are people looking to reduce resource consumption, and that's not going to happen with KDE.

---

### Post by DeceptiveHornet on 2012-09-25
> **rai4shu2 said:**
> Even the old stable version of Abiword was really only good for small projects that weren't very demanding. The only viable long-term solution is to switch to LO. Kubuntu is a good choice, but I think you'll find yourself using more resources in the long run if you go that direction. Most people who use Xubuntu or Lubuntu are people looking to reduce resource consumption, and that's not going to happen with KDE.

Was this directed at me? 

In case that it was ... i was mostly testing out xubuntu to see if it was kinder on my ati GPU, but then i found the solution for the mux system. Then i installed Kubuntu becuase i find it generally more pleasant to work with. But yes, you are correct, Kubuntu and LO does use some more resources but on a medium spec laptop it isn't really much of an issue.

---

### Post by Toz on 2012-09-25
FYI: The previous stable version of abiword (2.8.6) for precise is now available at this PPA: [https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise]("https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise").

---

### Post by stedevil on 2012-09-26
> **DeceptiveHornet said:**
> Abi has some ways to go before being a pre-installed piece of wordprocessor in a new linux installation.

Actually that's wrong. It's just a huge blunder that the UNSTABLE 2.9.2 abiword replaced the STABLE 2.8.6 version in *buntu 12.04.

Abi in general has been working just fine for years for occasional semiadvanced wordprocessing, and in many ways much better than Open Office ever did (anybody trying to use OO in a multilangual environment eg could appreciate the much saner approach use in Abi).

---

