---
title: "Im very disappointed with ubuntu 10.04"
date: 2010-07-07
forum: Desktop Environments
---

### Post by maxenzo2 on 2010-07-07
Hello to everyone,im very disappointed with ubuntu 10.04 x64,for me its the worst version ever made,(the only good thing so far,its the speed),it gives me errors i did not had with the 9.10 x64 version like with the cairo-dock,just look at the pictures,they talk for themselves:


Besides the sound,now i cant update the sound driver,and i dont have 5.1(i dont even understand why the alsa driver is so old on this ubuntu version),but the problem is,i cant go back to ubuntu 9.10 because the repository have old stuff,and it doesnt recognize my windows 7 on the other harddrive.But besides that i didnt had problems with sound,dock,the window buttons on the left,no java(please the open source version of java sucks,it doesnt work right)

But i dont like any other linux distro(they are all very incomplete),i just hoppe they fix all this mess in the next version or i quit using Linux,specially ubuntu.

---

### Post by kingbirdy on 2010-07-07
try reinstalling. you may have messed some things up in important places, and a clean install could help. or if your only problem is AWN then try reinstalling AWN

---

### Post by vangop on 2010-07-07
Hey!
Cairo-dock works flawlessly on my 10.04 laptop. Just reinstall. Moreover, I tried ubuntu 1st on 8.04 release couldn't get my internal mic to work. Now I installed 10.04 and everything worked out of the box + a lot more!

---

### Post by maxenzo2 on 2010-07-07
> **kingbirdy said:**
> try reinstalling. you may have messed some things up in important places, and a clean install could help. or if your only problem is AWN then try reinstalling AWN
How did i messed it up,if its a fresh install? :|
And this is not AWN its cairo-dock,AWN sucks,and i reinstalled 2x cairo-dock.

---

### Post by Calash on 2010-07-07
I have that same version of Cairo and it runs fine.

Double check your installed packages.  I have 5 listed for Cairo, 3 having to do with plugins.

cairo-dock
cairo-dock-core
cairo-dock-data
cairo-dock-plug-ins
cairo-dock-plug-ins-data
cairo-dock-plug-ins-integration

On a side note it may be related to this bug in Cairo dock, not Ubuntu

[https://bugs.launchpad.net/cairo-dock-plug-ins/+bug/545172](https://bugs.launchpad.net/cairo-dock-plug-ins/+bug/545172)

---

### Post by corruptor1972 on 2010-07-07
Hmmm, Cairo Dock works fine for me (both for the upgrade on this machine and new install on a different machine).  

Try this:  in Synaptic, uninstall cairo-dock (Mark for complete removal).

Next remove any old configuration:  Open your home folder in Nautilus, then choose to show hidden files.  Enter the .config directory then - if it exists - delete the cairo-dock directory.

Finally, re-install cairo-dock.

---

### Post by corruptor1972 on 2010-07-07
For the Java:

In synaptic, remove any existing medibuntu repository lines from the repositories list.

Go to [www.medibuntu.org](www.medibuntu.org), click the Repository Howto link.  Follow the instructions for Adding The Repository.

Next open a terminal and enter:  sudo aptitude install ubuntu-restricted-extras

So you should then get java and much other multimedia magicness...

---

### Post by howefield on 2010-07-07
> **corruptor1972 said:**
> For the Java:

You do realise the poster doesn't want the java supplied by restricted-extras, don't you ?

Partner repository is the place to look for him.

Can you explain what Medibuntu has to do with ubuntu-restricted-extras ?

---

### Post by maxenzo2 on 2010-07-07
> **corruptor1972 said:**
> Hmmm, Cairo Dock works fine for me (both for the upgrade on this machine and new install on a different machine).  

Try this:  in Synaptic, uninstall cairo-dock (Mark for complete removal).

Next remove any old configuration:  Open your home folder in Nautilus, then choose to show hidden files.  Enter the .config directory then - if it exists - delete the cairo-dock directory.

Finally, re-install cairo-dock.
That worked,i havent removed the config file before.

---

### Post by maxenzo2 on 2010-07-07
> **corruptor1972 said:**
> For the Java:

In synaptic, remove any existing medibuntu repository lines from the repositories list.

Go to [www.medibuntu.org](www.medibuntu.org), click the Repository Howto link.  Follow the instructions for Adding The Repository.

Next open a terminal and enter:  sudo aptitude install ubuntu-restricted-extras

So you should then get java and much other multimedia magicness...
i dont have medibuntu,only ubuntu-restricted-extras.

---

### Post by corruptor1972 on 2010-07-08
Glad I could help with the Dock.  

Ignore my previous post about the Java, I was in a muddle there: Howefield is quite correct, you want to have the Partner repository enabled.  If it's Sun Java you want, I think the sun-java6-jre and sun-java6-plugin packages are what you're after, although I don't have them installed on my machine so I can't vouch for if that works or not...

---

### Post by maxenzo2 on 2010-07-31
> **corruptor1972 said:**
> Glad I could help with the Dock.  

Ignore my previous post about the Java, I was in a muddle there: Howefield is quite correct, you want to have the Partner repository enabled.  If it's Sun Java you want, I think the sun-java6-jre and sun-java6-plugin packages are what you're after, although I don't have them installed on my machine so I can't vouch for if that works or not...

The java works well,much better than open source version. :D

---

### Post by cariboo on 2010-07-31
This really isn't a testimonial. Moved to Desktop Environments.

---

### Post by maxenzo2 on 2010-08-01
> **cariboo907 said:**
> This really isn't a testimonial. Moved to Desktop Environments.

Well it was,but ended up different ;) thanks for moving the post.

---

### Post by craig10x on 2010-08-01
If you are still around...try Mint 9...it's ubuntu underneath but everything is there out of the box...download it and run the live cd and you will see what i mean...

---

### Post by maxenzo2 on 2010-08-27
> **craig10x said:**
> If you are still around...try Mint 9...it's ubuntu underneath but everything is there out of the box...download it and run the live cd and you will see what i mean...
But ubuntu is working just fine now,and i dont like how the gnome looks on mint.

---

