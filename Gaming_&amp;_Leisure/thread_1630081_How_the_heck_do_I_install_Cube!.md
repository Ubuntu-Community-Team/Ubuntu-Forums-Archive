---
title: "How the heck do I install Cube?!"
date: 2010-11-24
forum: Gaming &amp; Leisure
---

### Post by Thelinuxgeek on 2010-11-24
I know there's already a few posts on this, but my problem is slightly different than the otheres. I downloaded Cube (the first one, not Cube 2) from sourceforge.net. I go to the cube homepage cubeengune.com to read the installation wiki cuz there are no install instructions on sourceforge. They tell me to move the cube.tar.gz to my home folder. I do that. then it says open a terminal and type in:
tar -jxvf sauerbraten_YYYY_MM_DD_CODENAME_PLATFORM.tar.bz2
cd sauerbraten

I make required changes to this command so that what I type in says:

tar -jxvf cube_2005_08_29_unix.tar.gz
cd cube

I get the following message:

brainstorm@Flappy:~$ tar -jxvf cube_2005_08_29_unix.tar.gz
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now
brainstorm@Flappy:~$ cd cube
brainstorm@Flappy:~/cube$ 
brainstorm@Flappy:~/cube$

So, I change the tar.gz into a bz2
I type in:

tar -jxvf cube_2005_08_29_unix.tar.bz2
cd cube
YAY! It installs!!! Then the website says and I quote:


[LIST]
[*]To run the game, type: ./sauerbraten_unix
[*]I type it in. The error message returned says no such file or directory. I change sauerbraten into cube and type in:
[*]./cube_unix
[*]This is the returned message:
[*]./bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
[*]HUH? what does that mean? what do I do now???? Someone help, PLEASE!!! And sorry for the long post, but I was just documenting how I've isolated the problem. I'd really appreciate any help on this one...
[/LIST]

---

### Post by wojox on 2010-11-24
See if there in the repo's 

```
sudo apt-get install libsdl-mixer1.2
```

---

### Post by Thelinuxgeek on 2010-11-24
> **wojox said:**
> See if there in the repo's 

```
sudo apt-get install libsdl-mixer1.2
```

OK i installed the package or whatever and tried tor un it but it said this:
./bin_unix/linux_client: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory i tried to install libstdc++ but I got this message:
brainstorm@Flappy:~$ sudo apt-get install libstdc++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libstdc++6' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-dev' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-doc' for regex 'libstdc+'
Note, selecting 'libstdc++2.10-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.8-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-glibc2.1-dev' for regex 'libstdc+'
Note, selecting 'libstdc++3.0-dev' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-pic-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-pic-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-pic-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-cross' instead of 'libstdc++6-armel-dcv1'
libstdc++6 is already the newest version.
libstdc++6-4.4-dev is already the newest version.
libstdc++6-4.4-dev set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libstdc++6-4.4-dbg : Conflicts: libstdc++6-4.3-dbg but 4.3.5-3ubuntu1 is to be installed
 libstdc++6-4.4-dbg-armel-cross : Depends: libgcc1-dbg-armel-cross but it is not going to be installed
 libstdc++6-4.4-doc : Conflicts: libstdc++6-4.3-doc but 4.3.5-3ubuntu1 is to be installed
 libstdc++6-4.5-dbg : Conflicts: libstdc++6-4.3-dbg but 4.3.5-3ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.4-dbg but 4.4.4-14ubuntu5 is to be installed
 libstdc++6-4.5-dbg-armel-cross : Depends: libgcc1-dbg-armel-cross but it is not going to be installed
                                  Conflicts: libstdc++6-4.4-dbg-armel-cross but 4.4.4-14ubuntu4 is to be installed
 libstdc++6-4.5-doc : Conflicts: libstdc++6-4.3-doc but 4.3.5-3ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.4-doc but 4.4.4-14ubuntu5 is to be installed
E: Broken packages

What now???

---

### Post by Perfect Storm on 2010-11-24
It's libstdc++5

```
sudo apt-get install libstdc++5
```

---

### Post by houseworkshy on 2010-11-24
Searching for &quot;libSDL_mixer-1.2.so.0&quot; pulls a lot of info and it could be as simple as installing it.    This one of many seems like it could be ok         [http://blog.wlindley.com/2009/01/resolving-missing-packages-on-ubuntu/](http://blog.wlindley.com/2009/01/resolving-missing-packages-on-ubuntu/)           That said I had a similar problem with a game I liked the look of which in the end turned out to be a dead end because it was 32 bit and I'm using 64 bit.  Some of the good advice I was given may help you out though            [http://ubuntuforums.org/showthread.php?t=1616430](http://ubuntuforums.org/showthread.php?t=1616430)            This is more of a bump for you than advice as I'm out of my depth.  However I note that Assault cube is available in the standard repositories so you could play with that while waiting for someone with more knowlage to chime in, I think it's a mod of cube1.

---

### Post by Thelinuxgeek on 2010-11-24
> **artificial intelligence said:**
> it's libstdc++5

```
sudo apt-get install libstdc++5
```

yes thank you!!!!!!! It works now!!!!!!!! Yeehaw!!!!

---

