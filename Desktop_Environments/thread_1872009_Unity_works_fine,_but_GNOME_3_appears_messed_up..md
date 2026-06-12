---
title: "Unity works fine, but GNOME 3 appears messed up."
date: 2011-10-29
forum: Desktop Environments
---

### Post by LinuxLearner123 on 2011-10-29
Hi. I recently did a fresh install of Ubuntu 11.10 over my previous 11.04 installation. I was very excited because Ubuntu finally includes GNOME 3, and I need something more stable than Fedora to run on my system. I've installed a GNOME 3 Metapackage from the Software Center, plus I installed GNOME-Session and GNOME-Shell in the Terminal (reinstalled multiple times.) For those who care, GNOME-Desktop3-Data and Mutter are both also installed, included in the metapackage. _Keep in mind that both Unity and GNOME Fallback (Classic) work flawlessly_ (well, no system is flawless, but you  know what I mean.) The GNOME 3 sessions work perfectly fine, but I can't see what I'm clicking (rendering it 'not fine'), and it's ugly. I'll post an attachment with a screenshot of some of the broken things. I know what GNOME 3 is supposed to look like, as I used it on Fedora for multiple months before switching to Ubuntu. I tried posting this on LinuxQuestions.org, with no luck; just people telling me that I don't know what I'm doing. I am annoyed that this only seems to apply to me, and surprised at how few people tried getting GNOME 3 working on Ubuntu.

Neither of my screenshot programs (the defaults for GNOME and KDE) are functioning properly in GNOME 3 (They hide everything that's messed up just before taking the picture-go figure), so I will include 5 pictures taken with my iPod. Sorry about the quality issues, but please note that anything that looks wrong is wrong, and that the missing/messed up letters are NOT camera issues. The only issue that my camera added is my picture appearing too bright (due to glare), and everything else is just as messed up as they seem. My apologies for the first photo being sideways.

---

### Post by BigCityCat on 2011-10-29
> **LinuxLearner123 said:**
> Hi. I recently did a fresh install of Ubuntu 11.10 over my previous 11.04 installation. I was very excited because Ubuntu finally includes GNOME 3, and I need something more stable than Fedora to run on my system. I've installed a GNOME 3 Metapackage from the Software Center, plus I installed GNOME-Session and GNOME-Shell in the Terminal (reinstalled multiple times.) For those who care, GNOME-Desktop3-Data and Mutter are both also installed, included in the metapackage. _Keep in mind that both Unity and GNOME Fallback (Classic) work flawlessly_ (well, no system is flawless, but you  know what I mean.) The GNOME 3 sessions work perfectly fine, but I can't see what I'm clicking (rendering it 'not fine'), and it's ugly. I'll post an attachment with a screenshot of some of the broken things. I know what GNOME 3 is supposed to look like, as I used it on Fedora for multiple months before switching to Ubuntu. I tried posting this on LinuxQuestions.org, with no luck; just people telling me that I don't know what I'm doing. I am annoyed that this only seems to apply to me, and surprised at how few people tried getting GNOME 3 working on Ubuntu.

Neither of my screenshot programs (the defaults for GNOME and KDE) are functioning properly in GNOME 3 (They hide everything that's messed up just before taking the picture-go figure), so I will include 5 pictures taken with my iPod. Sorry about the quality issues, but please note that anything that looks wrong is wrong, and that the missing/messed up letters are NOT camera issues. The only issue that my camera added is my picture appearing too bright (due to glare), and everything else is just as messed up as they seem. My apologies for the first photo being sideways.

I never installed gnome session. Just installed gnome shell. Tons of people are using it without a problem. Maybe you have a graphics problem.

---

### Post by Frogs Hair on 2011-10-29
Sorry to here you're having problems . I have been running the shell along with Unity 3D with much success , although I don't use the fall back session.

I would be glad to look at the screen shots when they are posted . If you are running Unity 3D without any problems I doubt if it is hardware related. 

I run the Gnome Shell from the software center and have all available extensions installed , which may differ from your setup.

---

### Post by LinuxLearner123 on 2011-10-29
Here are the screenshots (I tried uploading them to my first post, but I guess it didn't work.)
Once again, some of the problems could easily be passed off as an effect due to camera quality, but many of the letters really appear faded, blurry, missing, or replaced with a randomly colored block. Note that my problems are mostly with system text. I think that GNOME knows something is wrong with it, as every now and then the screen flickers and the problems are moved (different letters are missing, the top bar turns white instead of black), but it always goes back to normal after a second. Once again, I can run GNOME fallback, KDE Plasma, and Unity 3D with no problem, and am convinced that this is a purely software issue. When the screen flickers, it just turns black; it does not actually lose input or turn off.

---

### Post by LinuxLearner123 on 2011-10-29
OK, GNOME just crashed... well, my GNOME 3 session did, anyway. I am  almost convinced that Unity is causing this. The screen flickered again, and now all I see is the "File, Edit, View, Go, Bookmarks, Help" toolbar at the top of the screen. It is **exactly like a "User-Defined Session"**, and like the top of Unity looks like when you log in, before you open any programs but after it gets done loading the interface. Note that all that's there is exactly what you see if you choose "User-Defined Session" as your desktop interface (at the screen where you could also choose KDE or 'Ubuntu'/Unity), and neither the notification area nor the Launcher are present. Looks like I'm gonna have to cut power, as there's no power options available (they were with the notification area.)

---

### Post by stinkeye on 2011-10-29
What you need to be posting,
Is video card and driver
```
lspci -k | grep -A3 VGA
```

---

### Post by typhoon_tip on 2011-10-29
> **stinkeye said:**
> What you need to be posting,
Is video card and driver
```
lspci -k | grep -A3 VGA
```

Yep, and if you have ATI and you did install fglrx, forget about Gnome 3. It is not supported at the moment, the only way to make it work is to revert back to stock ATI driver.

---

### Post by LinuxLearner123 on 2011-10-30
> **typhoon_tip said:**
> Yep, and if you have ATI and you did install fglrx, forget about Gnome 3. It is not supported at the moment, the only way to make it work is to revert back to stock ATI driver.

O.K., here is the output that should tell you my graphics hardware.


jacob@HPPavillion2510us:~$ lspci -k | grep -A3 VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
	Subsystem: Hewlett-Packard Company Device 30f1
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon


Let me tell you one more time that **_GNOME 3 worked PERFECTLY FINE in Fedora on the same computer that I now have Ubuntu on._** Now once again I have people telling me that I don't know what I'm doing, insisting that this is a purely hardware issue. I am thinking about simply installing Fedora again, or maybe Linux Mint. Has anyone else even gotten GNOME 3 working on Ubuntu?

---

### Post by vasa1 on 2011-10-30
> **LinuxLearner123 said:**
> ...Now once again I have people telling me that I don't know what I'm doing, insisting that this is a purely hardware issue. I am thinking about simply installing Fedora again, or maybe Linux Mint. Has anyone else even gotten GNOME 3 working on Ubuntu?

Isn't 11.10 running GNOME 3?

---

### Post by stinkeye on 2011-10-30
I'm not familiar with the ATI issues but that
seems to be the problem.
have a look [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1865257")

---

### Post by qamelian on 2011-10-30
> **LinuxLearner123 said:**
> O.K., here is the output that should tell you my graphics hardware.


jacob@HPPavillion2510us:~$ lspci -k | grep -A3 VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
    Subsystem: Hewlett-Packard Company Device 30f1
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon


Let me tell you one more time that **_GNOME 3 worked PERFECTLY FINE in Fedora on the same computer that I now have Ubuntu on._** Now once again I have people telling me that I don't know what I'm doing, insisting that this is a purely hardware issue. I am thinking about simply installing Fedora again, or maybe Linux Mint. Has anyone else even gotten GNOME 3 working on Ubuntu?
As another poster already mentioned, Gnome-shell does not work properly with FGLRX. I'm using it perfectly with the open source radeon driver, but it will not work currently with FGLRX. This is a known issue with the FGLRX driver.

---

### Post by LinuxLearner123 on 2011-10-30
> **stinkeye said:**
> I'm not familiar with the ATI issues but that
seems to be the problem.
have a look [**_[COLOR=DarkRed]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1865257")

O.K., I had a look at some of the Software Center reviews for GNOME-Shell. Someone said that it didn't work with the closed-source ATI drivers, so I reinstalled Ubuntu, but this time I didn't enable the ATI/Radeon drivers. GNOME 3 works flawlessly now. My hardware supports the full GNOME 3 interface, but I am now using the open-source graphics drivers.

I really hate to mark this as solved, but I got my problem resolved. My apologies to those who are having the same issues as I was but can't do a reinstall (I've been in that boat before.)

---

### Post by BlinkinCat on 2011-10-30
> **LinuxLearner123 said:**
> O.K., I had a look at some of the Software Center reviews for GNOME-Shell. Someone said that it didn't work with the closed-source ATI drivers, so I reinstalled Ubuntu, but this time I didn't enable the ATI/Radeon drivers. GNOME 3 works flawlessly now. My hardware supports the full GNOME 3 interface, but I am now using the open-source graphics drivers.

I really hate to mark this as solved, but I got my problem resolved. My apologies to those who are having the same issues as I was but can't do a reinstall (I've been in that boat before.)

I'm in exactly the same situation as you - I guess we just have to wait for AMD to sort out the problem - I hope it doesn't take too long! - :(

---

### Post by SebSmith on 2011-11-12
I also have the same issue. its just annoying. unity should only be for touchscreen versions of ubuntu distros. too mac/iphone like. gnome 3 makes more sense, but i thought they make gnome 3 testing on all modern hardware? my laptop was made in february.

why is this thread marked solved?

---

