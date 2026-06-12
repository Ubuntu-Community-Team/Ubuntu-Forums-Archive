---
title: "Few questions..."
date: 2005-09-06
forum: Desktop Environments
---

### Post by Daandaan on 2005-09-06
I recently installed Ubuntu but some things dont work perfect.
- First of all the biggest problem is that I can't hear any sound...I have a vt8233/a/8235/8237 ac97 audio controller and i'm totally new to linux so i dont know how to solve that problem. 

- I was wondered if there is any suspend to ram mode ( put my computer on standby) in ubuntu?

- Is it possible to have a root account? So that I can log in as root and do whatever I want so I don't have to open always root terminal.

- Wenn I try to install NumlockX 1.0 I get the following message 

creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

Ok there may be other ways to turn on numlock automatic when gnome starts but it bothers me also that he says that there is no gcc and cc...What can I do about that?? I think i'm gonna need these things to install other programs...

I hope someone has an answer to (one of) my questions.
-= Greetz Daan =-

---

### Post by frodon on 2005-09-06
Login as root is quite dangerous if you don't know what you do. To become permanently root in a terminal ```
sudo su
```To run a single command as root just add sudo before your command. If you still wanting to login as root (i don't recommend that at all !) look at this [thread](http://ubuntuforums.org/showthread.php?t=31053) .

---

### Post by macgyver2 on 2005-09-06
Welcome!

[QUOTE=Daandaan]- First of all the biggest problem is that I can't hear any sound...I have a vt8233/a/8235/8237 ac97 audio controller and i'm totally new to linux so i dont know how to solve that problem.[/QUOTE]
Hmm, unfortunately I don't know any specifics here.  I know there are a lot of threads about sound problems.  Maybe [this one]("http://www.ubuntuforums.org/showthread.php?t=26567") will help you.  There's also [this sticky]("http://www.ubuntuforums.org/showthread.php?t=21211").  If those don't help, try searching the forums (or hopefully someone more knowledgeable will come along).

[QUOTE=Daandaan]- I was wondered if there is any suspend to ram mode ( put my computer on standby) in ubuntu?[/QUOTE]
[https://wiki.ubuntu.com/SuspendHowto]("https://wiki.ubuntu.com/SuspendHowto")

[QUOTE=Daandaan]- Is it possible to have a root account? So that I can log in as root and do whatever I want so I don't have to open always root terminal.[/QUOTE]
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

[QUOTE=Daandaan]- Wenn I try to install NumlockX 1.0 I get the following message 

creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

Ok there may be other ways to turn on numlock automatic when gnome starts but it bothers me also that he says that there is no gcc and cc...What can I do about that?? I think i'm gonna need these things to install other programs...[/QUOTE]
gcc isn't included in the default install. Fire up Synaptic (System --> Administration --> Synaptic Package Manager) and either look in the Development section or just search for gcc. If you install the package 'gcc' (not gcc-<anything>) you'll get the default compiler. If you want to play around with other versions you'll see them there as well.

Hope this helps some.

---

### Post by Steve1961 on 2005-09-06
If you're going to install packages from source just open a terminal and type:

sudo apt-get install debhelper build-essential fakeroot linux-headers-$(uname -r)

This will install the necessary compilers and just about everything else you'll need.  There's no harm in installing these before you look at packages you want to install.

As for sound, lots of people have problems with this, especially onboard ac97.  Post the output from dmesg and lspci -v here so we can see if your system is picking up your sound card.  From the information you've provided it looks like it might be a via ac97 chip and I've managed to get one of these working.

---

### Post by parktownprawn on 2005-09-06
[QUOTE=Daandaan]
Ok there may be other ways to turn on numlock automatic when gnome starts but it bothers me also that he says that there is no gcc and cc...What can I do about that?? I think i'm gonna need these things to install other programs...
[/QUOTE]

to install numlockx see [http://www.ubuntuguide.org/#numlockx](http://www.ubuntuguide.org/#numlockx) 

you probably don't need to install gcc *unless* you want to compile things yourself.

If you *do* want to compile stuff yourself, open a console and type 
```
sudo apt-get install build-essential
```

---

