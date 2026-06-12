---
title: "Inspiron 530n nVidia GLX"
date: 2007-08-10
forum: Dell  Ubuntu Support
---

### Post by HeavyAl on 2007-08-10
I feel like this question has been touched on all over the place but I can't find a definitive answer.

My dad got one of the Dell Inspiron 530n series machines with Ubuntu Feisty preinstalled. It came with the nVidia 6300GS card.

On booting up everything appears fine, though the resolution is 1024x768 which I know is lower than what this card can do (he opted for the 19inch flat panel so you can imagine that 1024x768 looks pretty darned big on this).

On checking System/Hardware/Hardware Information the video is reported as generic.

I checked /etc/X11/xorg.conf and found that the generic nv driver was being used.

Running restricted drivers manager says no restricted drivers are needed.

Went to add/remove and installed the nvidia binary x.org driver from there (nvidia-glx I believe). Found in another thread that even though the driver gets installed it's not setup automatically so I ran the config utility that sets it up and replaces the xorg.conf file.

On re-examining the xorg.conf file I see that nv has been replaced with nvidia. Thinking all was well I rebooted and on startup X fails with a bunch of errors leaving me at the cl.

Swapping out the new xorg.conf for the old version sets everything back to normal for the most part except there is still no acceleration.

Running glxinfo at the cl returns a lot of stuff about "extension "GLX" missing on display ":0.0".". I'm not at his machine right now or I'd post the exact information and the xorg.conf.

I've seen here and there that some people suggest just grabbing the binary driver from nVidia and running that. Others suggest trying 'envy', but I get the impression that is more for legacy support. What it looks like to me is that there is a module missing that is supposed to load up GLX support but I have no idea how to go about finding it or getting it installed.

I know the information here is rather limited, but could anyone give me a pointer or two as to what I can do to get acceleration working on this device?

---

### Post by ridgeland on 2007-08-10
I have an Dell-Ubuntu E520n with a nVidia graphics card.  I used ENVY to install the nvidia driver which replace nv.  I like the ease, and now nvidia settings are an option on the menu.

---

### Post by HeavyAl on 2007-08-10
Is envy actually in the repos somewhere? I've never been able to figure out what exactly has to be downloaded to get it going.

---

### Post by ridgeland on 2007-08-10
I use synaptics package manager. (menu->System->Administration->)
There I see Envy.
Do you see it there?
If not let's search which repositories are enabled.

---

### Post by HeavyAl on 2007-08-11
Oh, good, so it is in the repositories. That makes it easier to uninstall if something goes wrong. 

Thanks! I'll give that a try!

---

### Post by rcdegges on 2007-08-13
Hey. I'm actually trying to follow your instructions and try to get my driver installed with Envy, but I cannot find Envy in the repositories. Could you help me get it working? Thanks. I searched through the package manager for it (and found nothing), as well as with aptitude:

$ aptitude search envy
$

---

### Post by HeavyAl on 2007-08-13
I couldn't find Envy in the repos so I just downloaded the .deb from the site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

The thing works as advertised. I removed the old driver that the repos allow you to install first (apt-get remove nvidia-glx) then installed and ran Envy which basically went out and downloaded everything it needed and wrote the xorg.conf file. After that I rebooted and was pleasantly surprised that acceleration was working in full.

I love it when a plan comes together!

---

### Post by ridgeland on 2007-08-13
I might have done that too!
HeavyAl, does it show up in Synaptics now, after the download?  Maybe that is why I see it there.

---

### Post by HeavyAl on 2007-08-14
> **ridgeland said:**
> I might have done that too!
HeavyAl, does it show up in Synaptics now, after the download?  Maybe that is why I see it there.

Oh, you know, I didn't actually check, but I imagine it would since it was an actual .deb that it was installed from. Most stuff I install from source doesn't show up in Synaptic but .deb's often do.

So far I haven't heard anything bad from my dad about the operation (it was his computer that required the update), but I'll check it next time I'm on the machine and see if it's in Synaptic now (Envy that is). 

Actually, come to think of it, is there a command line method of seeing what is installed using apt-get? I built SSH into my dads machine so I could fix it remotely if needed so I could just check from there and it'd be nice to know.

Wow, what a lot to write about a such a small thing!

---

### Post by ridgeland on 2007-08-14
$ dpkg -l envy
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-================
ii  envy                    0.9.5-0ubuntu1          "Envy" is an application written in Python which will download

But I don't know if this means it's also in Synaptics.

---

### Post by rcdegges on 2007-09-11
I wrote a small script to install the correct network and video card driver. It won't hurt to install them both, so if you want to use my program (it comes bundled with the appropriate drivers), you can find it here:

[http://ubuntuforums.org/showthread.php?t=540926](http://ubuntuforums.org/showthread.php?t=540926)

(read the post). It will get the proper video driver installed and working in no time.

---

