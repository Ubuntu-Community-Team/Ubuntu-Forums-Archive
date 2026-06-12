---
title: "Vlc"
date: 2006-02-11
forum: Desktop Environments
---

### Post by namit on 2006-02-11
I am looking for something like VLC 

Any chance that i can get it installed on Ubuntu have had no joy with it.

Or does anyone else have a good idea for another player that i could play my Divx on?

---

### Post by bluevoodoo1 on 2006-02-11
How about xine? Get "xine-ui" in Synaptic.

---

### Post by FlakJacket on 2006-02-11
The only way I could get VLC was through Automatix

Flak

---

### Post by namit on 2006-02-11
na it does not work

any other ones?

---

### Post by engla on 2006-02-11
Where did you get VLC and what is wrong with it?
I've installed VLC and it works just fine on my installation... be sure to get it from breezy-backports, as there were some great changes to the better from the breezy version.

---

### Post by namit on 2006-02-11
yes i tried to install vnc by compiling it but no joy. I use it in windows but then its just a exe. 

what is breezy-backports and where would i download vlc from?

---

### Post by eriefisher on 2006-02-11
I have VLC. I got the source line from thier web site[http://videolan.org]("http://videolan.org") but now I've noticed it shows as failed when I reload synaptic so maybe they might be down now due to the law change in Europe.

eriefisher

---

### Post by gingermark on 2006-02-11
[QUOTE=namit]what is breezy-backports and where would i download vlc from?[/QUOTE]

Breezy Backports in an unofficial (?) repository. Basically you edit the sources.list file located in /etc/apt/. You can also use the Repository options in Adept of Synaptic.

Either way, it is a localised repository.

In the UK for example, you would add
```
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
``` to enable the repository.

Use the link in my sig if you're not sure what it would be for your country, but I think it's just a case of changing the country code.

So, for the US it would be deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

You'll then need to reload the package list, or in a terminal type
```
sudo apt-get update
```

After that, use Synaptic or Adept to install the package "wxvlc", or type
```
sudo apt-get install wxvlc
```

That's it, and it should make a lot of other packages easily available to you as well. Do be careful using unofficial repositories though.

EDIT: You also might wanna check out some of the vlc plugins. Alongside a Firefox one, there is support for different sound output methods (inluding ARTS, which is used in KDE). Browse them in Adept or Synaptic by searching for vlc.

---

### Post by namit on 2006-02-13
na no joy with that

Any more shots with this?

---

### Post by gingermark on 2006-02-13
[QUOTE=namit]na no joy with that
Any more shots with this?[/QUOTE]

If you're referring to my instructions, they work. Just checked them again. VLC is definitely in backports. And I didn't write those instructions for fun. I did them to help.

So maybe instead of "na no joy" you could post a helpful reply, maybe telling us where things went wrong, and maybe what the problem was. And possibly you could tell me what country you are from so I can tell you your correct repository?

The method works, so if there is a problem it is with you.

And I'm sure many folks would be happy to help you resolve your (computer-related) problems, so why not give a little info?

---

### Post by namit on 2006-02-13
Hey sorry about that

Just says that it can not find file and i update it all and it works

I have tried to do a search also but no joy

---

### Post by gingermark on 2006-02-13
Ok, you need to edit your sources.list file located in /etc/apt - this file controls what repositories you can download packages from. I thought doing it in Adept would be easier, but this way is simpler to describe.

Again, could really do with knowing what country you are from, but anyways.

Run Konsole.

Type ```
sudo kedit /etc/apt/sources.list
```
If you don't have kedit installed, replace that command with your text editor of choice, ie gedit, kate.

Add the following line to the file:
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

This is the British repository, I guess we can figure out your local one later. This definitely works.

Save the file, and close your text editor.

Now type ```
sudo apt-get update
```
This reloads the sources.list file you have just edited, and checks what packages are now available to you.

Then type
```
sudo apt-get install wxvlc
``` to install VLC.

You might also want to have a look at this: [https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)
Keep in mind it is for Ubuntu rather than Kubuntu, but you can install Synaptic Package Manager in Kubuntu if you like, or use Adept instead. Either way, that page should give you a decent overview of how to install software.

You might also want to look at a user recommended sources.list file here: [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

Again, if you have any problems say what you did and what happened and someone can sort them out for you.

---

### Post by namit on 2006-02-15
ok i tried that and got an error message all the mirrors seam to update but it can not find wxvlc

> 
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Fetched 140kB in 4s (33.9kB/s)
Reading package lists... Done
root@ubuntumu:/home/namit# sudo apt-get install wxvlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wxvlc
root@ubuntumu:/home/namit# sudo apt-get install wxvlc     



---

### Post by gingermark on 2006-02-15
That is just plain odd. It works for me. And it should be there for you (as shown [here](https://launchpad.net/distros/ubuntu/breezy/i386/wxvlc)).

Unless....... are you using the AMD64 or PowerPC versions of Kubuntu by chance?

If you are using the x86 version, [Automatix](http://ubuntuforums.org/showthread.php?t=66563) will install vlc for you (but only along with several other players).

---

### Post by namit on 2006-02-15
yes i am using x86 version

---

### Post by gingermark on 2006-02-15
Ok, well I have no idea why it isn't working for you. Seems very strange. I would suggest using Automatix to install VLC, you can always remove the other players it installs afterwards if you don't want them.

---

### Post by orev on 2006-02-15
Install VLC from Automatix (link in sig).

Easy like .exe

---

### Post by medialover on 2007-11-10
I am running ubuntu gutsy gibbon 7.10 (the stable official release).  I followed your instructions, and they did not work.  I got this error message:




medialover@medialover-laptop:~$ sudo apt-get install wxvlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wxvlc: Depends: vlc but it is not going to be installed
E: Broken packages
medialover@medialover-laptop:~$ sudo apt-get install wxvlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wxvlc: Depends: vlc but it is not going to be installed
E: Broken packages




How do I fix this?  I can't get DVDs to play on my system.  VLC did this before, but I had to re-install ubuntu and now I can't install VLC.  Why?  What is causing the above error message?

---

### Post by Rhubarb on 2007-11-10
To install vlc, just type in:
```
sudo aptitude install vlc
```
To be able to play DVDs, you'll want to visit:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

If you can't get libdvdcss2 for some reason, get it here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

