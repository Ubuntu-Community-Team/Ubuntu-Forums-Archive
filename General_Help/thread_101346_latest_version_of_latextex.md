---
title: "latest version of latex/tex"
date: 2005-12-09
forum: General Help
---

### Post by jordilin on 2005-12-09
I am currently working with latex and I've seen that Ubuntu doesn't provide the latest stable version of latex/tex.
When I run the command "latex filename.tex", appears the version LaTeX2e <2001/06/01>. The latest version is from 2003. Why Ubuntu doesn't provide the latest stable version, since it's from 2 years now?? :-( 
This is something quite disappointing.

---

### Post by ember on 2005-12-09
You can include the backports repository and install tetex. The most recent version is in there (3.0).

Best,
ember

---

### Post by jordilin on 2005-12-09
I've put these two lines in my sources.list:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse
 
and done apt-get update. But when I go to synaptic tetex remains the same version. There's no update?

---

### Post by ow50 on 2005-12-09
It's not in backports. See the following thread to see why it was rejected
[http://ubuntuforums.org/showthread.php?t=89896](http://ubuntuforums.org/showthread.php?t=89896)

The reason for the long delay for Ubuntu is that tetex entered Debian unstable not so long ago on Fri, 14 Oct 2005 16:28:11 +0200. Why was the Debian packaging such slow, that I do not know.

---

### Post by jordilin on 2005-12-09
Thanks, I've read the posts, and it seems incredible. Other distros ship the latest versions of tex without any problem. I am deeply disappointed since I like ubuntu very much and I don't want to change to another distro just for the sake of latex. :(

---

### Post by ekarni on 2005-12-09
No need to switch distros -- you can install debian packages using the dpkg -i command.  Just grab the latest and greatest from the Debian site and install it that way.  Sure, I agree that it would be nice to have in the mainstream repositories, but installing one package manually is a heck of a lot easier than installing a whole new distro.

---

### Post by ow50 on 2005-12-09
Installing from debian unstable or dapper might result in dependency issues, if not now, possibly when upgrading to dapper. Best would be to build your own deb from dapper sources, if you know how to do that. That's what I did and it works good. I don't remember what source change it required, but it wasn't anything difficult. I'd host those tetex packages in my repository if they weren't so huge (including sources 183.8 MB.)

---

### Post by dada1958 on 2005-12-12
I love Ubuntu; it's an OS with huge potentials with just a few cons. The default brownish interface is one of them. Not that big deal because you can overcome that one easily by changing it.
Not bringing tetex 3 into the repositories is a **major** shortcoming. LaTeX is a worldwide standard, used by many people with an eye for superior typography and hanging punctuation and margin kerning aren't just minor features. Once you've tasted the beauty of typesetting that way, you can't live without it anymore. It's essential.
Fortunately I have a Mac which enables me working with tetex 3 but that's not the way if you want to promote Ubuntu as an all-round OS.
Tetex 3 should have been in the repositories for quite a time but it is overseen and still not there and that's a shame :confused:

---

### Post by ember on 2005-12-12
It definitely is in backports. You have to include breezy-backports-staging, I think. At least I have installed it, so it must be there ;)

---

### Post by jordilin on 2005-12-18
No, it is not in backports or backports-staging. I have the backports repository in my sources.list and I've done an apt-get update and doesn't appear a tetex upgrade in synaptic. 
I don't understand anything. The most stable software in the world and is not in the current release, what a shame!! I'm truly thinking about switching to Fedora or another distro.

---

### Post by bojaren on 2005-12-19
Same Opinion One More..
I can't understand why tetex 3 isn't in breezy...tetex 2 is sooooo out-dated.

---

### Post by JNewman on 2005-12-24
Add me to the list of people suggesting this upgrade. 

My own reason is that the current version includes version 1.10b of pdflatex, which is badly out of date (2003) and makes some things difficult (for example, using truetype fonts) that are made easier by more current versions, and updating only pdflatex is discouraged by the documentation because of the complex integration of the various components of the teTeX package.

I'm trying to figure out how to compile the packages for Breezy from source; if anyone's gone down that road and can help, I'd certainly be grateful.

--JN

---

### Post by neoflight on 2006-01-08
would you guys please help me solve this issue i am having...

i use gnome. but use kile as frontend for latex ... i installed the texlive2005 from ctan.org. i dont wanna use tetex that comes with kile....when i tried to remove tetex then kile also goes? is that strange?

my question is how to tell kile to use my texlive2005 installation.? i cudnt find a solution by myself...btw iam using kile v = 1.8.1.

thanks

---

### Post by JNewman on 2006-01-08
I ended up by backporting tetex from Dapper, and if I remember correctly when I uninstalled the old tetex, it uninstalled kile too. After I had finished the backport I reinstalled kile. 

This was a couple of weeks ago, and I've had no problems with the backported tetex 3 and kile 1.8.1.

Hope this helps ...

---

### Post by neoflight on 2006-01-08
[QUOTE=JNewman]I ended up by backporting tetex from Dapper, and if I remember correctly when I uninstalled the old tetex, it uninstalled kile too. After I had finished the backport I reinstalled kile. 

This was a couple of weeks ago, and I've had no problems with the backported tetex 3 and kile 1.8.1.

Hope this helps ...[/QUOTE]

well iam not sure what u meant by backporting?  how do u do it? would you please give me the step by step commands/process etc...that would be great.

thanks

---

### Post by JNewman on 2006-01-09
Let me start with this: I'm a newbie, and I highly recommend you look for more experienced help than I can give you. That being said, what I did wasn't too hard to do. I found help, though, and very willing, thorough, and experienced help, in the #ubuntu channel on *irc.freenode.net*.

**Backporting** is the process of taking software from a newer release than the one you have installed, and getting it to work with the one you have installed. For example, the Dapper Duck release will include tetex 3, while we poor deprived Breezy users are suffering with tetex 2, so when I say that I backported tetex 3, what I mean is that I built the .debs for tetex 3 on my Breezy box, using as *little* as I could of Dapper to resolve dependency issues.

The general process is this, assuming that you're running Breezy. 

1. Edit your *sources.list* file so that all of the deb-src lines and ONLY the deb-src lines point to Dapper, while the deb lines still point to Breezy. Here's an example of one pair of deb and deb-src lines:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **breezy** universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **dapper** universe

2. Use apt-get to try to build the new (backported) package. If you're successful in building it, try to install it (dpkg -i *the-package*):

2a. apt-get update
2b. apt-get build-dep *the-package*
2c. apt-get -b source *the-package*

At this point you will either have built the package or identified unmet dependencies that prevent the package from being built. Repeat the 2b and 2c steps for each unmet dependency, and install each one. Then try to build the package again.

If memory serves, you'll have to do this for tetex-base, tetex-common, tetex-doc, tetex-bin, and tetex-extra to get to tetex 3. You'll need some library files that you'll also have to backport; here my memory is hazier but I think I remember hanging up on libxaw8 ...

When you're done, remember to edit your sources.list so that the deb-src lines point to breezy again.

To end up where I started out -- I'd recommend taking advantage of the help the kind folks in the #ubuntu chan on irc.freenode.net offer. 

Hope this helps.

---

### Post by neoflight on 2006-01-09
thanks a lot for your input Jnewman.

---

### Post by neoflight on 2006-01-10
[QUOTE=JNewman]
1. Edit your *sources.list* file so that all of the deb-src lines and ONLY the deb-src lines point to Dapper, while the deb lines still point to Breezy. Here's an example of one pair of deb and deb-src lines:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **breezy** universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **dapper** universe

2. Use apt-get to try to build the new (backported) package. If you're successful in building it, try to install it (dpkg -i *the-package*):

2a. apt-get update
2b. apt-get build-dep *the-package*
2c. apt-get -b source *the-package*

At this point you will either have built the package or identified unmet dependencies that prevent the package from being built. Repeat the 2b and 2c steps for each unmet dependency, and install each one. Then try to build the package again.

If memory serves, you'll have to do this for tetex-base, tetex-common, tetex-doc, tetex-bin, and tetex-extra to get to tetex 3. You'll need some library files that you'll also have to backport; here my memory is hazier but I think I remember hanging up on libxaw8 ...

When you're done, remember to edit your sources.list so that the deb-src lines point to breezy again.

To end up where I started out -- I'd recommend taking advantage of the help the kind folks in the #ubuntu chan on irc.freenode.net offer. 

Hope this helps.[/QUOTE]


i followed this guide and i am not getting tetex -3... . this is a part of the command line output iam getting when running the second command...

dh_md5sums -i
dh_builddeb -i
dpkg-deb: building package `tetex-base' in `../tetex-base_2.0.2c-8_all.deb'.
dpkg-deb: building package `tetex-extra' in `../tetex-extra_2.0.2c-8_all.deb'.
dpkg-deb: building package `tetex-doc' in `../tetex-doc_2.0.2c-8_all.deb'.
echo -en "\a"
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included).


u said "the-package"...is it tetex or tetex3 or something? please let me know...thanks a lot

---

### Post by JNewman on 2006-01-10
[QUOTE=neoflight]
dpkg-deb: building package `tetex-base' in `../tetex-base_2.0.2c-8_all.deb'.
dpkg-deb: building package `tetex-extra' in `../tetex-extra_2.0.2c-8_all.deb'.
dpkg-deb: building package `tetex-doc' in `../tetex-doc_2.0.2c-8_all.deb'.
[/QUOTE]

Hi -

I'm not sure, being no expert, but this looks to me as if you either did not update the deb-src lines in your sources.list file to point to dapper instead of breezy, or did not do an apt-get update. You shouldn't be seeing, for example, tetex-base_2.0.anything; if all had gone well (i.e., building the tetex-base package from dapper source repositories) that would have been tetex-base_3.0.something.

The packages you should be trying to build are tetex-base, tetex-common, tetex-extra, tetex-doc, and tetex-bin. You'll also need to build one or two (I'm going from memory -- one, two, or a few) support libraries. I remember problems with libxaw8, at a minimum.

I'd offer you the .debs, but a couple of them are large -- one's 80+ MB -- so that is fairly impractical.

Check that you're running your apt-get commands against the dapper source repositories. (But I want to emphasize that only the deb-src repositories should point to dapper. The idea is to install breezy packages where they exist, and build packages from dapper source where breezy packages don't exist.)

If you keep running into trouble, check out the #ubuntu chan on irc.freenode.net; the people there were extremely helpful and generous with their time when I went through this.

Hope this helps ...

---

### Post by ember on 2006-01-10
I just noticed that I have tetex 3 from the seveas repositories (and not backports). Try adding them to your sources.list:
[http://seveas.ubuntulinux.nl/]("http://seveas.ubuntulinux.nl/")

Best,
ember

---

### Post by neoflight on 2006-01-11
[QUOTE=ember]I just noticed that I have tetex 3 from the seveas repositories (and not backports). Try adding them to your sources.list:
[http://seveas.ubuntulinux.nl/]("http://seveas.ubuntulinux.nl/")

Best,
ember[/QUOTE]


thanks a lot guys...

i tried both..let me tell u how i did it.

i changed the source file to dapper... (all of them[including deb and src] except backports) and disabled whatever is not necessary. then updated and then installed tetex-blahs...

it brought tetex3!!!! ....
i manged to get kile without tetex2 this time using apt-get instead of synaptic. now its working but still trying to fugure out how to properly link tetex3 and kile. since i cant find tetex2 iam assuming that kile uses tetex3...
not sure how to check this thing tho...

and i cudnt get it from [seveas]("http://seveas.ubuntulinux.nl")... i followed instructions in the repository page and put in proper keys and all to correct errors i got during the first time...

i.e.,
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -

thanks again and any comments would be welcome...

---

