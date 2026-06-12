---
title: "Installing VLC 1.0.0?"
date: 2009-04-24
forum: General Help
---

### Post by Greg Xix on 2009-04-24
Okay.

I ran into the "VLC Opening Video in Two Separate Windows" problem similar to this:

[http://ubuntuforums.org/showthread.php?t=1134536](http://ubuntuforums.org/showthread.php?t=1134536)


And found a potential solution by installing VLC 1.0.0, but dont understand what the heck to do:


[http://ubuntuforums.org/showthread.php?t=1111272](http://ubuntuforums.org/showthread.php?t=1111272)



Somebody explain this to me like I am a 7-year old. Step-by-step. Because the instructions given on that PPA site didnt work nor did adding the "deb [http://nightlies.videolan.org/build/intrepid-i386/arch](http://nightlies.videolan.org/build/intrepid-i386/arch) ./", and I am a complete novice. But everybody on that forum seemed to understand how to do it.

Or is there another way to install VLC 1.0.0?

---

### Post by paradigm2 on 2009-04-24
You are using Jaunty now right?

2am here and I need to sleep for now but in the mean time here are some good links to learn what you need to do to install from the PPA.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you still need help and no one else helps you, I will stop by again sometime tomorrow.  Good luck.

---

### Post by Greg Xix on 2009-04-24
> **paradigm2 said:**
> You are using Jaunty now right?

2am here and I need to sleep for now but in the mean time here are some good links to learn what you need to do to install from the PPA.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you still need help and no one else helps you, I will stop by again sometime tomorrow.  Good luck.

Yes I am currently using Jaunty.

I did everything there basically, except make and install the "Key" file.

The VLC 1.0.0 test-version is up and running okay on my Ubuntu now.


What was wrong with 0.9.9a, doing that weird video box separated setup?

Also, when is the "Official" release of 1.0.0 coming out? This 1.0.0 already looks good, and it appears to have also solved another problem I had a while back as well: 


[http://ubuntuforums.org/showthread.php?t=1064668](http://ubuntuforums.org/showthread.php?t=1064668)



PS...I tried Amarok and that didnt play anything on here.

---

### Post by ubu-for on 2009-04-24
Add this PPA to your repository and import the OpenPGP key.

[https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

```
## VLC 1.0
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
```

---

### Post by jtsop on 2009-05-04
to import the  keys for the vlc ppa run these:

gpg --keyserver keyserver.ubuntu.com --recv-keys 2F021AC1
gpg --armor --export 2F021AC1 | sudo apt-key add -

---

### Post by binbash on 2009-05-04
[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

### Post by talk2ankit29 on 2009-06-25
I have recently installed UBUNTU-9.04 and when i try to install VLC i m getting these error..
please help me out...
i m also not able to install any other player as well.
thanks in advance.

ankit@Ankit-Gupta-Lapy:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.9.9a-2ubuntu1) but it is not going to be installed
       Depends: libtar but it is not installable
E: Broken packages

---

### Post by cyan15 on 2010-04-18
I got those nox errors too, went away after removing the jaunty lines in /etc/apt/sources.list

---

### Post by Nick Elliott on 2010-07-10
Hey guys, first time ubuntu user using 10.4 "lucid lynx," apparently. Got the same problem, when I connect a second monitor, vlc and movie player videos appear as a blank window even when still on my laptop screen. All this advice seems to be for jaunty. Any help for a confused noob? Cheers guys.

---

