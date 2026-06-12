---
title: "Package dependencies cannot be resolved - no matter what I installed"
date: 2010-12-10
forum: Desktop Environments
---

### Post by Louigi Verona on 2010-12-10
Hey guys!

For several days now I am unable to install any software on my system. No matter what app I install, no matter what I use - Software Center, Synaptic or a deb file - it says "Package dependencies cannot be resolved".

Tried recovery mode, "fix broken packages", but it did not help. I did have some custom repositories installed, like Pidgin. I unchecked them but it changed nothing.

---

### Post by sikander3786 on 2010-12-10
Hi.

Go to Applications > Accessories > Terminal and post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

While posting, click the # icon in post menu and paste your text in between generated code tags.

---

### Post by Louigi Verona on 2010-12-10
```
louigi@louigi-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil50 libvpx0 libva1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
louigi@louigi-laptop:~$ sudo dpkg --configure -a
louigi@louigi-laptop:~$ 

```

---

### Post by sikander3786 on 2010-12-10
That output seems pretty ok.

Which software were you trying to install via Software Center?

Try installing from apt-get and post the output.

```
sudo apt-get install name-of-package
```

---

### Post by Louigi Verona on 2010-12-10
```
louigi@louigi-laptop:~$ sudo apt-get install openshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openshot: Depends: melt but it is not going to be installed
            Depends: python-mlt but it is not installable or
                     python-mlt2 but it is not going to be installed
E: Broken packages

```

```
louigi@louigi-laptop:~$ sudo apt-get install kcoloredit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kcoloredit: Depends: kdebase-runtime (>= 4:4.3.95) but it is not going to be installed
              Depends: kdelibs5 (>= 4:4.4.0) but it is not going to be installed
              Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
E: Broken packages

```

---

### Post by Louigi Verona on 2010-12-10
I checked some of those, for instance kdebase-runtime I do have installed and it fits the requirements.

---

### Post by sikander3786 on 2010-12-10
Which version of Ubuntu is this?

If you have any PPAs or external software sources enabled, disable them. Go to Software Center > Edit > Software Sources > Other Software Tab and disable any PPAs.

Then from Terminal,

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install -f openshot
```

```
sudo apt-get install -f kcoloredit
```

If aptitude is installed, it might help here.

```
sudo aptitude install kcoloredit
```

---

### Post by Louigi Verona on 2010-12-10
sikander3786: Thanks for your responsiveness! The matter was solved by using aptitude. What is started doing was downgrading several packages for kcoloredit, for openshot it found new packages and upgraded to them. All installed nicely.

I wonder why apt did not do that?

---

### Post by sikander3786 on 2010-12-10
You are Welcome :-)

aptitude is better in resolving dependencies than apt-get (in my opinion).

Google aptitude vs apt-get and you'll find more info ;-)

If you are satisfied with the solution, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

