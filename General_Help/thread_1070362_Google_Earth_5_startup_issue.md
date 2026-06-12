---
title: "Google Earth 5 startup issue"
date: 2009-02-15
forum: General Help
---

### Post by summersk on 2009-02-15
Newbie!!
I've installed Google Earth ver 5.0 
When trying to start I get the following error:Could not create directory:

/root/.googleearth/Cache

Then when I click "OK" I get the following:

Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:

My Places Path: "/home/username/.googleearth"
Cache Path: "/home/username/.googleearth/Cache"

The program tries to load then quits at the question of the day
I've turned off the Visual Effects to "None"

What should I try next?

Linux username-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Hardware: Macbook 2.0 GHz 1GB MB

---

### Post by cyberdork33 on 2009-02-15
it sounds like you are trying to run it while logged in as root or something, or at least it thinks you are root. You should use Google Earth as a normal user.

---

### Post by summersk on 2009-02-15
Not really, followed the steps from google:

Start the installation by downloading the Linux installer.

Open a terminal and change to the directory where the installer downloaded to. If it’s on your desktop you can use this command:
cd ~/Desktop

Change the permissions on the installer so you can run it:
chmod +x GoogleEarthLinux.bin

Run the installer as the root user:
sudo ./GoogleEarthLinux.bin

Trying to remove now, permission are root, trying to start from the
beginning. any help please!

---

### Post by skotos on 2009-02-15
> **summersk said:**
> The program tries to load then quits at the question of the day
I've turned off the Visual Effects to "None"

What should I try next?

Linux username-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Hardware: Macbook 2.0 GHz 1GB MB
Following these instructions - [http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en) - I made GoogleEarth starting up fine. HTH.

But the following remains:
> **summersk said:**
> When trying to start I get the following error:Could not create directory:

/root/.googleearth/Cache

Then when I click "OK" I get the following:

Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:

My Places Path: "/home/username/.googleearth"
Cache Path: "/home/username/.googleearth/Cache"

Any idea on how to solve this annoying message?

---

### Post by jhmos on 2009-03-09
For the "Could not create directory: /root/.googleerth/Cache" problem, edit your .config/Google/GoogleEarthPlus.conf replacing /root with your home directory for the following two lines:

KMLPath=/root/.googleearth
CachePath=/root/.googleearth/Cache

---

### Post by aviv27 on 2009-03-14
> **jhmos said:**
> For the "Could not create directory: /root/.googleerth/Cache" problem, edit your .config/Google/GoogleEarthPlus.conf replacing /root with your home directory for the following two lines:

KMLPath=/root/.googleearth
CachePath=/root/.googleearth/Cache

Hi, tried that and the error message disappeared but the startup problem remains - google earth starts and then quits immediately.

---

### Post by edWAR6 on 2009-03-14
> **aviv27 said:**
> Hi, tried that and the error message disappeared but the startup problem remains - google earth starts and then quits immediately.

I have this same problem please help

When i run google earth from the console i get this...

bat@bat-desktop:~$ googleearth
Warning: Unable to create prefs directory '/home/bat/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

---

### Post by tod1d on 2009-03-16
I'm having the same problems as mentioned above

why is it so hard to install this program?
I'm a newb to linux in general so bare with me please

---

### Post by Vaphell on 2009-03-16
because Googlor guys messed up a little :-)

about that libcrypto.0.9.8 thing - renaming said library in /opt/google-earth does help. I think it forces GE to use system one instead of its own, apparently broken version.

in terminal window, assuming default install path:
cd /opt/google-earth
sudo mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak

---

### Post by coolbrook on 2009-03-16
Thanks Vaphell.

---

### Post by Rasmussen.JP on 2009-03-28
thanks for helping

---

### Post by gdp77 on 2009-03-29
I have the exact problem as the original poster. Any idea how to solve it?

---

### Post by dcstar on 2009-03-29
> **summersk said:**
> Newbie!!
I've installed Google Earth ver 5.0 
When trying to start I get the following error:Could not create directory:

**/root**/.googleearth/Cache
........
What should I try next?


Do **not** use sudo.

---

### Post by skotos on 2009-04-02
> **jhmos said:**
> For the "Could not create directory: /root/.googleerth/Cache" problem, edit your .config/Google/GoogleEarthPlus.conf replacing /root with your home directory for the following two lines:

KMLPath=/root/.googleearth
CachePath=/root/.googleearth/Cache
Thank you very much! I did not know where this info was stored. Now it runs perfectly.

A note for others having the same issue: before proceeding, your user may have to take the ownership of

[LIST=1]
[*]/home/my_user/.config/Google/
[*]/home/my_user/.config/Google/GoogleEarthPlus.conf
[/LIST]
:popcorn:

---

### Post by skotos on 2009-04-02
> **dcstar said:**
> Do **not** use sudo.
Sorry, dcstar, but I strongly disagree.
Installing 3rd party apps with sudo/gksu and similars is a good and recommended practice: *Synaptic*,* apt*, *yum*,... all teach this to us.
_This particular problem rises_ not because you have installed the app with root privileges, but _simply because the Google installer messes up with privileges and default values_: **it is not sane to install in a user directory a directory owned by root with a configuration file that stores paths pointing to root's paths.**
(See my previous/upper post).

A tricky problem, instead, may rise if the sudoed app is a graphical one run by prefixing it with sudo and not with *gksu*: though sudo gedit may run smoothly, many other apps will not work correctly and will deliver configuration files owned by root in your home.
Thus, **it is always a good / recommended practice to run a graphical installer with gksu (in Gnome) and with the gksu correspondent inside KDE/XFCE.**

BTW, to me it is still to be understood why sudo still has to behave so differently since it might automatically detect the environment and load any appropriate library and act accordingly, but this is another long discussed question.

---

### Post by DougAlder on 2009-04-03
Thanks vaphell - that solved the problem

---

### Post by The_R on 2009-04-05
> **jhmos said:**
> For the "Could not create directory: /root/.googleerth/Cache" problem, edit your .config/Google/GoogleEarthPlus.conf replacing /root with your home directory for the following two lines:

KMLPath=/root/.googleearth
CachePath=/root/.googleearth/Cache

Werkt. Just wanted to say thanks.

---

### Post by FirstByté on 2009-08-11
Many thanks to you all!

I initially had GoogleEarth 4.3 which never worked since day 1. I thought I broke something in my file-system sometime when I was working on Apaché, I later discovered I was wrong. GoogleEarth 4.3 just decided not to work on my 8.10 or 9.04.

I was able to fix the root cache problem initially by changing the ownership of the '**root**' "/root/.googleearth/Cache"

```
/root/$ sudo chown -Rf chown -R *mycomputername:mycomputername* /root/.googleearth/Cache
```

and solved the rest by changing the paths in "/.Config/GoogleEarthPlus.conf". However this didn't solve the invisible Globe issues I had. The Globe didn't show. 

I Install GoogleEarth 5.0 and it solved it without any need for tweaking!


Thanks y'all for posting!:P

---

### Post by antjkirk on 2009-08-21
Tried googleearth once but laptop froze so uninstalled and went back to using flashearth.

---

### Post by scouser73 on 2009-08-21
> For the "Could not create directory: /root/.googleerth/Cache" problem, edit your .config/Google/GoogleEarthPlus.conf replacing /root with your home directory for the following two lines:

KMLPath=/root/.googleearth
CachePath=/root/.googleearth/Cache

I had this problem, one of the files was called **KMLPath=/root/.googleearthplus** so I renamed it to **KMLPath=/root/googleearth**

This fixed the startup problems with Google Earth.

---

### Post by Little-Bean-Buntu on 2009-09-05
Hi guys,

I have the exact same problem, on a newly installed Ubuntu 8:10. I tried different versions of GoogleEarth and different installation methods. However I couldn't make to work the solutions suggested by Aviv27 and Vaphell.

To begin with, is there anyone who could tell me where I find the config/google... file?

---

### Post by Vaphell on 2009-09-05
your_home_dir/.config/Google

---

### Post by Little-Bean-Buntu on 2009-09-06
It took me one day to figure out what you were talking about, but now I can find my way through permissions and hidden files.

I did everything that was suggested and I stopped getting error messages, but my google-earth was still messed-up and unusable. If that makes any difference the lib-crypto-thing was in usr/lib/ and not in opt...:?:

Anyway, I uninstalled my 4.3 version. Can someone (who has a version that works) tell me where they got it? I am using an 8:10 (Intreprid)

P.S. Thanks, Vaphell and anyone else how posted here

---

### Post by scouser73 on 2009-09-06
I downloaded it from [http://earth.google.co.uk/]("http://earth.google.co.uk/")

---

### Post by Efwis on 2009-09-06
uninstall it, then copy and paste the following in Terminal
```
 wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin

```

I had a similar issue until I found this dandy little command in the howto section, worked perfectly for me since then. and it installed 5.0

---

### Post by Little-Bean-Buntu on 2009-09-08
The code suggested by Efwis installs the version 5.0, from Google site which was the first thing I did. But in that version the Earth appears pixelled and no map can be seen. For that reason I tried version 4.3 from Medibuntu repository which gave error messages and didn't work either, even after the errors had been corrected.

Could it be that it is something wrong with my Ubuntu version? As I mentioned I have an 8:10.

---

### Post by Efwis on 2009-09-08
it might be something graphics card related.

---

