---
title: "Freedom of choice"
date: 2006-02-01
forum: Desktop Environments
---

### Post by AlexanRO on 2006-02-01
Hello all of my fine Ubuntu compadres,

I have a small dilemma, I am trying to install KDE on my Ubuntu machine ( Ahhh! That's hot! Please hold the flames down for a moment..) and I am running into a dep issue.  I Had just finished configuring my sources and did the following:

```
root@ubu510:/etc/apt# apt-get install kde
```

here is my unexpected output

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not installable
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not installable
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not installable
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: kdewebdev but it is not installable
       Depends: kdesdk but it is not going to be installed
       Depends: kdeaccessibility but it is not going to be installed
       Depends: kdevelop3 but it is not going to be installed
E: Broken packages
root@ubu510:/etc/apt#
```

I read some of the threads on the forum, some suggest

```
root@ubu510:/etc/apt# apt-get install kubuntu-desktop
```

but as you can see...

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop
root@ubu510:/etc/apt#
```

this was obviously not the desired outcome.  Having said that it should now be apparent that the reason why I posted is to seek the assistance of my fellow colleagues and distinguished guests.

I appreciate any support that you are able to lend.

P.S. Why KDE you ask?  Oh I am merely exercising my freedom of choice --I want them both Gnome and KDE. TIA

AlexanRO

---

### Post by Gustav on 2006-02-01
either you have a strange /etc/apt/sources.list or you are still using Warty

---

### Post by cwaldbieser on 2006-02-01
[QUOTE=AlexanRO]Hello all of my fine Ubuntu compadres,

I have a small dilemma, I am trying to install KDE on my Ubuntu machine ( Ahhh! That's hot! Please hold the flames down for a moment..) and I am running into a dep issue.  I Had just finished configuring my sources and did the following:

```
root@ubu510:/etc/apt# apt-get install kde
```

here is my unexpected output

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not installable
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not installable
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not installable
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: kdewebdev but it is not installable
       Depends: kdesdk but it is not going to be installed
       Depends: kdeaccessibility but it is not going to be installed
       Depends: kdevelop3 but it is not going to be installed
E: Broken packages
root@ubu510:/etc/apt#
```

I read some of the threads on the forum, some suggest

```
root@ubu510:/etc/apt# apt-get install kubuntu-desktop
```

but as you can see...

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop
root@ubu510:/etc/apt#
```

this was obviously not the desired outcome.  Having said that it should now be apparent that the reason why I posted is to seek the assistance of my fellow colleagues and distinguished guests.

I appreciate any support that you are able to lend.

P.S. Why KDE you ask?  Oh I am merely exercising my freedom of choice --I want them both Gnome and KDE. TIA

AlexanRO[/QUOTE]

MAybe you should try a new /etc/apt/sources.list from source-o-matic?
[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by AlexanRO on 2006-02-02
[QUOTE=cwaldbieser]MAybe you should try a new /etc/apt/sources.list from source-o-matic?
[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")[/QUOTE]

Problem solved!! See I knew that I could count on you, the Ubuntu Forum has my back. :D  

BTW that source-o-matic is very impressive and very reminiscent of Mandriva's [Easy URPMI]("http://easyurpmi.zarb.org/").

Thanks again

AlexanRO

---

### Post by Lord Illidan on 2006-02-02
No one is going to jump on you for choosing KDE, relax. Have you tried out KDE 3.5?? Here are the breezy repos:


# kubuntu.org packages for KDE 3.5 (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

# kubuntu.org packages for KDE 3.5 (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

---

### Post by az on 2006-02-02
To match the tone of the original post,

*Ahem*

No one gives a rat's arse what desktop environment you run!  Run XFCE, fluxbox, windowmaker, twm, if you want!  Who cares?

*Cough*

Excuse me.  (*Flips though Code of Conduct to see if he is still okay...*)







Sorry.


Happy you solved your problem, cheers.

---

