---
title: "I'm attempting to install Beryl on Gutsy"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by Mardok45 on 2007-10-25
I'm not happy with the Compiz-fusion and just want the regular Beryl eye candy back.

I downloaded the Beryl-Core package and attempted to install it.  When I ran the configure file, I got the following output.

[I]
checking for LIBBERYLDECORATION... configure: error: Package requirements (xrender >= 0.8.4) were not met:

No package 'xrender' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBBERYLDECORATION_CFLAGS
and LIBBERYLDECORATION_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/I]

I have no idea what to do from here.  Can someone help out?

---

### Post by overdrank on 2007-10-25
> **Mardok45 said:**
> I'm not happy with the Compiz-fusion and just want the regular Beryl eye candy back.

I downloaded the Beryl-Core package and attempted to install it.  When I ran the configure file, I got the following output.

[I]
checking for LIBBERYLDECORATION... configure: error: Package requirements (xrender >= 0.8.4) were not met:

No package 'xrender' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBBERYLDECORATION_CFLAGS
and LIBBERYLDECORATION_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/I]

I have no idea what to do from here.  Can someone help out?
Hi and I would just recommend adding a feisty repo and install that way
The first thing we need to do is add the security key, do this by pasting into a terminal:

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Then type in:

```
gksudo gedit /etc/apt/sources.list
```

This will open a file, add this to the very bottom by pasting:
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Then save and exit.

You will need to update again, so paste into a terminal:

```
sudo apt-get update
```

BERYL
Now to install Beryl (and Emerald window decorator) paste this into a terminal:

```
sudo apt-get install beryl beryl-manager beryl-core beryl-plugins beryl-settings emerald emerald-themes
```

---

### Post by Mardok45 on 2007-10-25
Thank ye, good sir.

---

### Post by vajjala1986 on 2007-10-26
I too got the same error while trying to install beryl. But I haven't got internet, so i downloaded "DD800CD9.gpg" from my frnd's PC, and also I got all files in link "http://download.tuxfamily.org/3v1deb" , as I don't know which one to select. I got beryl 0.2.1 packages also from beryl-ubuntu website.

can u tell me how to do it offline.

---

### Post by ewalk on 2007-12-08
Hi, I'm brand new to Gutsy and would like to install Beryl, however I tried following the steps above in konsole but got the error:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages


Do I need to get the packages from another repo? Am I missing a package?  Please help.

Thanks!

---

### Post by jrela2000 on 2007-12-11
^^^ I got the same thing

---

### Post by Fonon on 2007-12-11
so did I.  I had Emerald installed once before, through apt-get, but now it won't work.

I can't even tell if Beryl installed right.

---

### Post by Espreon on 2007-12-12
Well, what is wrong with CF? It has all of Beryl's plugins available (and much more), and lots of those plugins are installed by default. Just install CCSM and then you can get a real CF set up. IDK what the Gusty developers where thinking of not putting CCSM in Gutsy by default (since there is no default way of configuring CF). I think someone put something into the Gutsy developer's food...

---

### Post by jesusfreak107 on 2008-03-25
I know this is a fairly old post, but I am having the same problem, can someone help?  here is my exact error, in case it differs.

> ******@************:~# sudo apt-get install beryl beryl-manager beryl-core beryl-plugins beryl-settings emerald emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages


also, Emrald wont update, it shows up in the update manager, but it is not a selectable option, I am confused.

---

### Post by overdrank on 2008-03-25
> **jesusfreak107 said:**
> I know this is a fairly old post, but I am having the same problem, can someone help?  here is my exact error, in case it differs.



also, Emrald wont update, it shows up in the update manager, but it is not a selectable option, I am confused.

Hi and have you enabled all your repos
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by jesusfreak107 on 2008-03-25
oh, yes, in fact, I just spent quite a while fixing them.  they were all missing a "/"  (ANNOYING!)

anyway, an update:  I have libwnck22, and libwnck-common.  I tried downloading libwnck18 directly from the repo, off of the internet.  I managed to find the .deb file, and attempt a graphical installation.  It wouldn't install because I need "libwnck-common."  I DO!  It looks like a fiesty package, but I don't think that that is the problem.  And, I figured out why Emerald (and compiz fusion, too) won't update: they need libwnck18!!!  ugh..
help?

oh, and, yes, I reinstalled libwnck22 and libwnck-common.  I'm not a first level Ubuntu-user, as my profile suggests.  I like to consider myself an intermediate.

---

### Post by jesusfreak107 on 2008-03-25
that is for the 6.** versions of Ubuntu.  I am using 7.10

---

### Post by overdrank on 2008-03-25
> **jesusfreak107 said:**
> that is for the 6.** versions of Ubuntu.  I am using 7.10

Hi and I understand but the process is similar. The  last I tried to install beryl on Gutsy I ran into several dependency issues and I stopped. :(

---

