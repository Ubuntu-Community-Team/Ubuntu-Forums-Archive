---
title: "need insight on the 3-step installation process please"
date: 2009-04-25
forum: General Help
---

### Post by jasonmh on 2009-04-25
**Update**: Yes I know about the built in package manager, but almost everything there that I need is out of date and doesn't work (i.e. Wine).

I've noticed that there is always several steps that need to happen to install a single program. Coming from a Windows environment where I just double click a single icon and the installation just happens, I'm having a hard time wrapping my head around this three step process.

What is happening when I do a...?
[LIST=1]
[*]make
[*]make install
[*]./configure
[/LIST]

What do these commands do, where do these programs get installed into (so far my guess is the ether), and why must I always track down extra packages that these programs require? Why doesn't the program just provide these extra packages along with itself? :confused:

---

### Post by regor210 on 2009-04-25
I have had a lot of issues Using Make over the years like Missing dependency's, un-installing and upgrading. 

So I always use deb's 

Heres some places to find deb's 

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Installing_Mac_OS_X_after_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Installing_Mac_OS_X_after_Ubuntu)

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Note. Downloading and installing software from the Internet can be risky. I have used these sites with out any problems.

---

### Post by zvacet on 2009-04-25
Read [this]("https://help.ubuntu.com/community/CompilingSoftware") for better understanding what are you trying to do.If you want Wine you can get it from [here.]("http://www.winehq.org/download/deb") Just follow instructions.

---

### Post by jasonmh on 2009-04-25
Wonderful! But how did you find that page? I'm also trying to install the newest XFree86 (Getting a BadWindow error with Wine), but I'm not sure what to look for on their website to find the "Software Source" links and keys for XFree86.

---

### Post by 3rdalbum on 2009-04-25
Whoa there buddy, your problem-solving technique is like using a sledgehammer to kill the cockroach climbing up your wall.

The version of Xorg that you have is perfectly fine for Wine. Your problem is elsewhere; what is the exact error you are getting? Replacing an integral part of your Ubuntu system is an absolutely terrible idea that WILL lead to breakage.

The three-step procedure you mention is to compile source code for software. Linux, and even Ubuntu, runs on a variety of different sorts of processors that are incompatible with eachother's instructions; the lowest common denominator is the source code. Windows only runs on three processor architectures - ia32, AMD/EMT64, and ia64 (Itanium); this is why application developers on Windows use those horrid "binary installers". Even so, this practice has caught up to them with the switch to AMD/EMT64 64-bit operating systems and the compatibility problems this is causing. It's also tremendously bad for Itanium systems as they can't run anything that isn't distributed as either source code or as an Itanium binary.

Before going around compiling software, you should first check if there is a Debian package for that software that will install natively on Ubuntu with just a double-click. Better yet, check if there is a software repository that you can add, that will allow yourself to install the software and keep it up to date.

Failing that, see if there is a binary installer (usually known as a ".bin" or ".run" file); and lastly you can compile source code if there's no alternative.

./configure looks for where all your libraries are and allows you to enable compile-time features of the software.
make actually compiles the software.
sudo make install will install the compiled software.

Where does it install to? It's not important to know. The actual binary usually goes into /usr/local/bin with supporting files into /usr/local/share, but you don't need to know that - just type the program's name on the command-line and it will run. Or create a launcher for it?

Some software does come with its own version of the libraries, but honestly would you rather download a 40 megabyte source archive or a 4 megabyte source archive? If you get the dependencies yourself, then you can use them to compile or run other software rather than download them every time you download a new program. This is why iTunes is a 50 megabyte download and Amarok is a 20 megabyte download - the iTunes installer contains a shed-load of things that you probably already have.

Also, sometimes you want to use a later version of a library than what has been distributed along with a program. The new library might contain security or stability fixes, or even new features, that will immediately come into use with any new software that is developed. "Sure", you say "The maker of the program could just release a new version of his/her software that contains the new library"... well this is a needless waste of time and as a software developer I'd hate to have to do this.

---

### Post by jasonmh on 2009-04-25
The Wine crash was caused when I tried to cancel out of the Warhammer installation after it couldn't find nor create the folder it wanted to install into. I manually created the folder for it, which bypassed the crashing. Granted the program still won't run because of a known issue where the primary executable warpatch.exe won't run, but hey :) So I guess that game is being shelved until further notice.

  The deal with the libraries makes alot of sense, but for programs that need to be compiled from source code it seems to me that they should also come with a script that automatically checks for and, if need be, installs any necessary packages. As an example WineHQ's suggested method to install Wine for Ubuntu forced me to manually install .... haha wow okay never mind. I just checked the WineHQ website and it has been altered. The Ubuntu installation is now pointing towards a debian installation instead of a manual developers package. Now I need to figure out how to remove this developers version and git from my system o.0 Truth be, I'm not entirely sure how I installed it in the first place.

  I think that Linux will take along time to get used to for the primary reason that it seems most developers of Linux aren't used to writing manuals/instructions for non-technical types. Personally I require step-by-step instructions which say how to do something instead of a simple "run the program with xyz environmental parameters." For that Wine bug for example I've been asked to set some winedebug environmental parameters, yet they fail to include how I'm supposed to do that. I know I'm not stupid, but after several hours of banging my head against the endless Google search hits on "how to ______ for an outdated version of your program", things can become a little overwhelming.

   Regardless, thank you very much for everyone's comments. I've since added WineHQ to my repository, and will now look for debians instead of source code ;)

---

### Post by 3rdalbum on 2009-04-25
> **jasonmh said:**
> The deal with the libraries makes alot of sense, but for programs that need to be compiled from source code it seems to me that they should also come with a script that automatically checks for and, if need be, installs any necessary packages.

Agreed absolutely. I'm sure it could be done.

---

### Post by CatKiller on 2009-04-25
> **jasonmh said:**
> The deal with the libraries makes alot of sense, but for programs that need to be compiled from source code it seems to me that they should also come with a script that automatically checks for and, if need be, installs any necessary packages. 

That would be apt-get's build-dep option, then?
>        **build-dep**
           build-dep causes apt-get to install/remove packages in an attempt
           to satisfy the build dependencies for a source package.


Just because you don't know about a thing, it doesn't mean that thing does not exist :)

---

