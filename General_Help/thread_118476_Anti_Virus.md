---
title: "Anti Virus?"
date: 2006-01-17
forum: General Help
---

### Post by MJSOnline on 2006-01-17
Hi all.
di I need to install an anti virus packed on my system?  I see that [http://www.free-av.com/]("http://www.free-av.com/") AntiVir have a Free one for Linux.

Any good?

What about a firewall?  Anti spyware?

How do  configure them both?
Is there a drain on the system?

Thanks in advance.
Matthew

---

### Post by audax321 on 2006-01-17
Spyware on Linux is pretty much non-existant. Viruses exist but your chance of catching one is very very small... so it is up to you if you want the anti-virus or not. If you can.. install a firewall.

Now, if you are dual-booting with Windows or share files with other computers on your network that are running Windows and can get a virus scanner that will scan for Windows viruses.. that might be a good idea.

I haven't used an anti-virus before.. but a good firewall for Gnome is firestarter and for KDE is guarddog. Both of these can be found in either universe or multiverse repositories and have GUIs... although in my opinion the firestarter GUI is a LOT easier to configure.. but not as "tweakable" as guarddog. After installation firestarter should be in Applications > System Tools.

---

### Post by MJSOnline on 2006-01-17
Thats good news.

I have heard a lot about this "Firestarter" firewall.  How do i get it and configure it?

I just have Ubuntu now. Did have a dual boot but, asfter a lot of seaching, found the one package in Linux that was holding be back from getting rid of Windows.

Thanks again.
Matthew

---

### Post by Mr_Grieves on 2006-01-17
I recommend installing Automatix, via Automatix you can get Firestarter up and running, and alot of other useful things, when getting your Ubuntu installations fit for fight.

Read more here: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by audax321 on 2006-01-17
To get Firestarter:

1. In a Terminal (Applications > Accessories > Terminal): sudo gedit /etc/apt/sources.list

2. Make sure the following line exists (or uncomment it by removing the  # in front of it):
[INDENT]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe[/INDENT]

3. Save and exit Gedit.

4. Install firestarter (two ways):

```

The SHORT way:

In a terminal:
sudo apt-get update
sudo apt-get install firestarter

```

```

The LONG way:

1. Open Synaptic (System > Administation > Synaptic Package Manager).

2. Click the Reload button, then search for firestarter.

3. Select the checkbox to install it and then push Apply to actually install it.

```

5. Open Firestarter by going to Applications > System Tools > Firestarter to launch the GUI.

That's it. The configuration is very straight forward and intuitive. Also when you are finished, you might want to do 'sudo gedit /etc/apt/sources.list' and comment out the line for the universe repository (put a # in front of it) if you're done with it.

---

### Post by tkjacobsen on 2006-01-17
Be careful with automaitx. It messed up my system so i have to reinstall, 'cause it installs a lot of packages that are not in the ubuntu repos... Try instead to install from universe ore multiverse, else find the packages yourself

---

### Post by handy on 2006-01-17
Just use what you need out of the Automatix selection menu.

Re: Virus, here's an interesting link:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

All the best!

---

### Post by munroe on 2006-01-17
You could do this as well.

[http://www.grisoft.com/doc/Programs/](http://www.grisoft.com/doc/Programs/)

AVG(Grisoft) has a Linux client of their awesome anti-virus. Never tried it myself(don't need to), but if you're worried you could install that.

---

### Post by jaywatkins on 2006-01-17
You could try ClamAV.  That is also free, but a pain in the ass to configure.  Read the docs before attempting!!!  ClamAV also places a performace hit on your machine, so don't do what I did.  Install it on a Pentium 400 w/ 256MB RAM.

---

### Post by handy on 2006-01-17
I thought I'd have a look at Aegis-virus-scan out of interest, NOT paranoia, :rolleyes: 

Aegis-virus-scan, found lots of M$ viruses on my machine...  **THAT WERE NOT REALLY THERE!!!**

I verified that there were infact none by runnning ZoneAlarmSuite's Vet, from windoze.

So I could never recomend that anyone trust Aegis-virus-scan after my experience.

Though, I'm sure it will only keep on improving, like the rest of us...

---

