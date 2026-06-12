---
title: "&quot;Transcode&quot; package"
date: 2005-11-07
forum: Desktop Environments
---

### Post by escobar on 2005-11-07
Would anyone happen to know where to locate this? 

I tried googling it...nothing.

Tried using some of the repos (albeit vanilla debian repos) from apt-get.org to install it but this couldn't be done due to unmet dependencies.

Tried installing from source but it wouldn't complile due to unmet dependencies.

Searching around these forums, a few others have had same issue but I never came across a resolution.

Unfortunately I'm not at home to post what dependencies it's missing but there's quite a few. I'm imagining some have gotten this installed. Can someone post the steps they've taken? It's driving me crazy. I need this for a few video editing apps to work properly.

---

### Post by Harleen on 2005-11-07
Enabling the multiverse repository should be enough to be able to install transcode.

If you want to know where a specific package can be found, [http://packages.ubuntu.com](http://packages.ubuntu.com) is very helpful.

---

### Post by escobar on 2005-11-07
[QUOTE=Harleen]Enabling the multiverse repository should be enough to be able to install transcode.

If you want to know where a specific package can be found, [http://packages.ubuntu.com](http://packages.ubuntu.com) is very helpful.[/QUOTE]


Unfortunately not. I have the universe, and multiverse repos enabled. I've also searched over the link you provided going into each sub-category to find "transcode". Nothing found. "gtranscode" appears but attemping to install that fails in Synaptic. Why? You guessed it, it depends on transcode which couldn't be installed. Thanks for your help.

---

### Post by daveisadork on 2005-11-07
[QUOTE=escobar]Unfortunately not. I have the universe, and multiverse repos enabled. I've also searched over the link you provided going into each sub-category to find "transcode". Nothing found. "gtranscode" appears but attemping to install that fails in Synaptic. Why? You guessed it, it depends on transcode which couldn't be installed. Thanks for your help.[/QUOTE]
Hmmm... I have the transcode package installed. Maybe it came from the hoary-backports repo at mirrormax. Why do you need it, exactly? Is it for MythTV by any chance?

---

### Post by Harleen on 2005-11-07
I've installed transcode without a problem. The mirrors should have exactly the packages, that my link lists. If not, the mirror is probably broken. Which one are you using?

The German mirror obviously has the missing transcode packages: [http://de.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode)

---

### Post by escobar on 2005-11-08
[QUOTE=Harleen]I've installed transcode without a problem. The mirrors should have exactly the packages, that my link lists. If not, the mirror is probably broken. Which one are you using?

The German mirror obviously has the missing transcode packages: [http://de.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode)[/QUOTE]

Maybe a dumb question but can I use the German package if I don't read/speak German? Here's my sources.list which took me a little while to put together so feel free to use it:
[I]
## Uncomment the following two lines to fetch updated software from the 
network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.## Uncomment the following two lines to fetch updated software from 
the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

# Official Backport
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe 
multiverse restricted

# Backport Mirror
# deb [http://people.hazent.com/~jrp/ubuntu](http://people.hazent.com/~jrp/ubuntu) hoary hazent

# Java 
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

# Multimedia  
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) hoary main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) hoary main

# Wine
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/

# Opera Web Browser:
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free[/I]

Using both the official and Backport mirror I still wasn't able to find the package. I need it to install some DVD Authoring tools.

---

### Post by Harleen on 2005-11-08
Forget what I've written before. I just realised, that you are using Hoary and not Breezy. That really doesn't contain transcode by default. It's strange, that gtranscode is contained in it.

But as far as I know transcode is contained in the hoary-extras repository. You can enable that repository by adding the following line to your sources.list:
> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

That repository is not fully official, but a look at your souces.list tells me, that this won't bother you much. ;)

---

### Post by escobar on 2005-11-08
[QUOTE=Harleen]Forget what I've written before. I just realised, that you are using Hoary and not Breezy. That really doesn't contain transcode by default. It's strange, that gtranscode is contained in it.

But as far as I know transcode is contained in the hoary-extras repository. You can enable that repository by adding the following line to your sources.list:


That repository is not fully official, but a look at your souces.list tells me, that this won't bother you much. ;)[/QUOTE]

If it has trascode. I'm with it. I'll try it out later. Thanks.

---

### Post by escobar on 2005-11-08
[QUOTE=Harleen]Forget what I've written before. I just realised, that you are using Hoary and not Breezy. That really doesn't contain transcode by default. It's strange, that gtranscode is contained in it.

But as far as I know transcode is contained in the hoary-extras repository. You can enable that repository by adding the following line to your sources.list:


That repository is not fully official, but a look at your souces.list tells me, that this won't bother you much. ;)[/QUOTE]

God must want me to not have this package. Added the line to my sources and STILL it cannot be found. I can now see the 'transcode-doc' package. A step in the right direction I guess.:???:

---

