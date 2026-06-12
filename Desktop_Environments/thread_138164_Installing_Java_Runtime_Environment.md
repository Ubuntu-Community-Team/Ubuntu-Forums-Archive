---
title: "Installing Java Runtime Environment"
date: 2006-03-01
forum: Desktop Environments
---

### Post by diogoschneider78 on 2006-03-01
Greetings!

How do I get to install Java? I have looked over the large list when I issue:

aptitude search java

But I could find no JRE or something like that...

So if I download the RPM file from java.sun.com and convert it with alien, after installing the new .deb file there's still no JRE avaliable... :-k

Any tips? Thanks in advance!

---

### Post by Perfect Storm on 2006-03-01
[http://ubuntuforums.org/showthread.php?t=76735&highlight=java](http://ubuntuforums.org/showthread.php?t=76735&highlight=java)

---

### Post by diogoschneider78 on 2006-03-01
Ok, not quite sure if I should reply to this post or that post, but here we go:

When I do:
aptitude install java-package

It says:
Couldn't find any package whose name or description matched "java-package"

And I bet that's why when I issue the command:
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

It says:
/usr/bin/fakeroot: line 150: make-jpkg: command not found

The multiverse lines in /etc/apt/sources.list are uncommented and they look like:
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

I have also tried both with aptitude update; aptitude install java-package and apt-get update; apt-get install java-package.

And just to make sure there was nothing evil in the mirror I was using, I switched to the US mirror and tried everything again.

Please tell me... What else can I do?! :confused:

Thanks!

---

### Post by Perfect Storm on 2006-03-01
Another option is using PLF sourcelist, but it violent the US law so it's on your own risk. But it's legal here in EU. Only work on i386 x86 breezy

```
sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install sun-j2re1.5
```

Note that it's  version 1.5 + update 5 and not the newest 1.5 + update 6

---

### Post by Winux123 on 2006-03-01
I went thru the GUI to install java on my machine.

Administration ....i think
Synaptic package manager 
then i found some java packages and marked em for installation.

---

### Post by diogoschneider78 on 2006-03-02
Guess what happened?

aptitude: Couldn't find any package whose name or description matched "sun-j2re1.5"

Looks like I'm completely out of luck... Or that's my destiny anyway, to get as far as possible away from Java... I hate that resource hog anyway, just wanted to try a few stupid apps that didn't like the runtime environment that comes preinstalled with Ubuntu... [-(

---

### Post by Perfect Storm on 2006-03-02
Okay try this go to [http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/java/](http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/java/)
Grab the j2re package and save it to your desktop

then:

```
cd Desktop
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb

```

---

### Post by akiro.yamamoto on 2006-03-02
Please install fakeroot, build-essentials.
Ubuntu installs Blackdown Java by default.
Then check my sig for more info.
Use the FAQ and look for the JAVA section. ;)

---

### Post by akiro.yamamoto on 2006-03-02
Damn AI your quick! ;)

---

### Post by Perfect Storm on 2006-03-02
Got the fastest mouse hand in the west :cool: :mrgreen:

---

### Post by diogoschneider78 on 2006-03-02
# apt-get install fakeroot build-essentials
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
E: Couldn't find package build-essentials

Is my system fscked up or what? :cry:

PS: Just found out that "apt-setup" is not installed. I'm sure it used to be... How do I install it back? :confused:

---

### Post by Perfect Storm on 2006-03-02
Please post your sourcelist, it seems there's some problems with it.

---

### Post by diogoschneider78 on 2006-03-02
Right now it looks like this: (comments filtered out)

deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) dapper universe
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

I have just issued "aptitude dist-upgrade" to have everything updated to its latest version from dapper.

But by the time we were struggling with the JRE it was like this:

deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy universe
deb [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

I've just replaced "breezy" with "dapper" with vi.

I hope you can understand what's going on, hehe! :rolleyes:

---

