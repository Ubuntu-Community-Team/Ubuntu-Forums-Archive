---
title: "Mint desktop packages"
date: 2010-06-14
forum: Desktop Environments
---

### Post by ajtwin on 2010-06-14
i've been using ubuntu for a few months now, and I'm starting to learn quickly thanks to this forum. i was wondering if there is a package that can install the linux mint 9 desktop. i know they have the ubuntu-desktop package that installs the ubuntu desktop environment, but is there one for mint?  i'm just doing a little experimenting, and im not really worried about messing it up. i did install the ubuntu-desktop package (and btw i know its not its own package, just points to a lot of other packages) on a linux mint 9 install. and i like the outcome quite a bit, but i'd rather have ubuntu lucid as the base. thanks for the help in advance. ):p

Edit: im using 64-bit if it matters

---

### Post by SlidingHorn on 2010-06-14
well, if I'm understanding you correctly, you're wanting to install mint and it's packages and you're already running ubuntu?

If that's the case, as far as I know, Linux Mint is a whole 'nother distro -- based off of Ubuntu.  It's not necessarily another "flavor" of Ubuntu like Xubuntu or Kubuntu.  You would have to do a dual boot with linux mint as a second operating system, or you could install it in a virtual machine like virtualbox to try it out.

There is no metapackage (i.e. ubuntu-desktop) that will install linux mint

---

### Post by ajtwin on 2010-06-14
that's exactly what i wanted to know. thanks a lot. =D well, atleast it works if i install linux mint first, because ubuntu does have a meta package. i just feel like i get the best of both by doing that. and of course i remove the parts of both that i don't like. and it's kinda funny that you're the one who replied, i was just reading one of your threads. well, back to marking each individual package of a fresh install of linux mint.. sigh.

---

### Post by ajtwin on 2010-06-14
also, im new to this, how do i mark this as [SOLVED] ?


EDIT: nevermind. xD

---

### Post by narnie on 2010-06-14
Mint is another distro, but you can get many of its features by adding the linux mint repositories, updating, and then installing those features you want from those packages (like mintmenu, eg).

I'm not at a Mint computer right now, but I'll post back the repo when I get to one.

After installing the repos, just start synaptic, reload from synaptic, then search for mint.

You will likely get an error when you reload, btw, because you haven't added a key for the Mint repositories. You can either ignore this, or search around for the keys (I'll do the same and post back if I find them).

I really like Mint and use it on my desktops and laptops. I use Ubuntu Netbook Edition on my netbooks. I recommend Mint to new starts.

Yours,
Narnie

Here are the repos

deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) isadora main upstream import

The above is for an Ubuntu base of 10.04. Change isadora to whichever version (9.10 is Helena, 9.04 is Gloria, if you are using before 9.04, IT IS TIME FOR AN UPDATE, hehe)

to add the keyring, add the linuxmint-keyring package by doing

```

sudo aptitude install linuxmint-keyring
```
This will avoid future occurrences of the above error message.

Regards

---

### Post by ajtwin on 2010-06-15
thanks so much narnie!:p i'll give it a try right now and post back with the results.

---

### Post by ajtwin on 2010-06-15
> **narnie said:**
> 
to add the keyring, add the linuxmint-keyring package by doing

```

sudo aptitude install linux-keyring
```
This will avoid future occurrences of the above error message.

Regards

shouldn't it be...
 ```

sudo aptitude install linuxmint-keyring
```

or am i mistaken?

---

### Post by ajtwin on 2010-06-15
i believe i found that meta package i was looking for after i updated the repos. mint-metax64. =D  I'm installing it now, we'll see how it goes.


well, that meta package didn't work because of some dependency errors. (some packages can't be installed the same time as others)  oh well, i can still install individual mint packages. ;)

---

### Post by narnie on 2010-06-15
> **ajtwin said:**
> shouldn't it be...
 ```

sudo aptitude install linuxmint-keyring
```

or am i mistaken?

Yes, you are absolutely right. I'm sorry. Glad you caught it. I updated my post to reflect the correction.

:)

Narnie

---

### Post by narnie on 2010-06-15
> **ajtwin said:**
> i believe i found that meta package i was looking for after i updated the repos. mint-metax64. =D  I'm installing it now, we'll see how it goes.


well, that meta package didn't work because of some dependency errors. (some packages can't be installed the same time as others)  oh well, i can still install individual mint packages. ;)

If you are using synaptic to install, sometimes it isn't the best with dependency resolution.

You might give aptitude a try from the command line.

You can just run

```
sudo aptitude
```

in a terminal. It will bring up a mouse clickable text window. You can search for the metapackage, and then select it for installation (using the "+" key is the quickest or from the Package menu) and then install it from the Actions menu and see what the aptitude resolver can do.

Some things will be removed and replaced by linux mint versions, but what you are doing in looking for the individual packages might be better.

Cheers,
Narnie

---

### Post by ajtwin on 2010-06-16
alright, well everything worked great. :D i choose to go back and force version some stuff (Plymouth) back to the ubuntu version simply because i prefer the ubuntu boot screen and such.initially it wasn't going to work because it wanted to remove ALL my packages, but i worked around it by clicking mark all possible upgrades and then doing it. but now everything works great, i have ambiance theme, with the mint menu(which has the control center that i like), mint backup tool, mint dropbox integration, mint desktop settings, all on my ubuntu 10.04 install. and i'm loving it.

then on my laptop, i installed mint 9, then installed the ubuntu-desktop meta package. so i got the ubuntu me menu, the ubuntu themes (ambiance), i made the default ubuntu panels, with the exception of the mint menu. got empathy back. =D this was way easier to figure out than starting with ubuntu. but i love both of the installs and i feel like im getting the best of both ubuntu and mint.


and again narnie, thanks for the help. ;)


here are a couple of screenshots of the outcome

[IMG]https://dl.dropbox.com/u/8126831/ubuntumint1.png[/IMG]

[IMG]https://dl.dropbox.com/u/8126831/ubuntumint.png[/IMG]

the first one is ubuntu with mint packages, the second is mint with the ubuntu meta package.

---

### Post by narnie on 2010-06-16
Great Job, ajtwin!!!

Congrats!

I'm very please you are happy with the results.

Your persistence paid off.

You are so right, it is easier to start with Mint, but I hate suggesting a "reinstall" just after someone got an install up and running.

Your screencaps look GREAT! Thanks for sharing them.

I'm glad to have been of some help. I try to give back all I can to a community that has given so much to me!!!

Yours,
Narnie

---

### Post by santiagogaitan@gmail.com on 2011-02-17
> **ajtwin said:**
> alright, well everything worked great. :D i choose to go back and force version some stuff (Plymouth) back to the ubuntu version simply because i prefer the ubuntu boot screen and such.initially it wasn't going to work because it wanted to remove ALL my packages, but i worked around it by clicking mark all possible upgrades and then doing it. but now everything works great, i have ambiance theme, with the mint menu(which has the control center that i like), mint backup tool, mint dropbox integration, mint desktop settings, all on my ubuntu 10.04 install. and i'm loving it.

then on my laptop, i installed mint 9, then installed the ubuntu-desktop meta package. so i got the ubuntu me menu, the ubuntu themes (ambiance), i made the default ubuntu panels, with the exception of the mint menu. got empathy back. =D this was way easier to figure out than starting with ubuntu. but i love both of the installs and i feel like im getting the best of both ubuntu and mint.


and again narnie, thanks for the help. ;)


here are a couple of screenshots of the outcome

[IMG]https://dl.dropbox.com/u/8126831/ubuntumint1.png[/IMG]

[IMG]https://dl.dropbox.com/u/8126831/ubuntumint.png[/IMG]

the first one is ubuntu with mint packages, the second is mint with the ubuntu meta package.

ajtwin thanks for the post. Though I have some time running on Ubuntu, I am not a Unix surfer yet =(

I am very interested on apply some of the LinuxMint features on my LucidLynx, but I am not sure on how can I do it. Could you please resume the steps and the code required?

thanks for your help,

Santiago.

---

