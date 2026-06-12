---
title: "Xubuntu vs Kubuntu low fat vs Ubuntu Unity 2d"
date: 2012-04-19
forum: Desktop Environments
---

### Post by springshades on 2012-04-19
I'm trying to prepare for 12.04 by deciding which flavor to go with. I'd like to stick with one particular interface for several computers and will probably be installing this on 3 or 4 computers with varying specs. The one computer I will be using the most is a netbook with an atom processor, so the thing that matters the most for me is to find a fairly full featured DE which I don't have to spend a ton of time on (imagine tweaking one system then multiply it by 3 or 4) and which doesn't hit GPU or CPU terribly hard. RAM is going to be less noticeable on the system as during normal use for me, I always hit a CPU or GPU bottleneck first on these computers.

I've seen some qualitative assessments out there, but that is very hard to extend to multiple systems with different specs. There is a website that compares the different environments, but that is from 11.04 days before low-fat-settings existed (I think) and seems to suggest that Unity barely touches the CPU which really doesn't seem to be the case anymore.

I'd rather not have to clog up the ubuntu servers by downloading a ton of images, and it will also save me quite a bit of time optimizing and tweaking if others have experience with these already.

To start with, I've tossed out Lubuntu/LXDE as there are simply too many things that I expect in a DE that don't exist or would require hefty tweaking.

Xubuntu. This is what I've currently been using. Right now, it's only using about 120 MB RAM and is almost negligible on CPU at idle (<1% on the netbook) which is really nice. I'm a bit hesitant about using it in the LTS for several reasons:

* No reasonable menu editor. I can install a graphical menu editor to at least rearrange the menu, but anything more than that requires messing with text files. To put this into perspective, I've messed with those files to fix something or other on three separate occasions, and I still can't remember off hand exactly where they are located.

* No default way to mount certain file systems like iso and rather heavy tweaking (in 11.10 at least) to get things working. User isn't set up with permissions to be able to do this by default, and the best GUI option requires install (no big deal) and doesn't default to running with GKSU causing issues... like not being able to unmount afterwards. Command line option is again one of those which I rarely remember off hand when I need to and therefore end up needing to google every time.

* Ristretto is the default to open up images by double click. For me, this results in trying to open an image in a folder full of 100s of images and it only opens one at a time. No option for slide show. You *can* open a folder of images... if you want to navigate through its full menu, then browse to that folder. No simple, intuitive double clicking. Try explaining how to do this to someone who doesn't use the computer that often. They'd rather boot up a different computer to do the same thing instead of using the one that's already open. GThumb works better but seems to default to not fitting images to screen size... and it goes back to the default every time you switch image... I'm sure there's a way to streamline this, but again, 4 computers and at least 2 accounts per computer.

* I like Thunar's interface, but it's definitely missing some features.

* Working with an NTFS partition isn't bad, but working with a usb stick is a bit unwieldy (if you want to format it or partition it).

* No GUI way to change timezone when you travel with your computer. Again, the command line version is something convoluted and unintuitive that I'll probably never bother to memorize. When you travel sometimes you don't even have internet to google it.

* Good power management requires installing an additional package.

Not much when looked at individually, but when added together and multiplied by 4 computers and in addition to the small odds and ends that are bound to pop up... I decided I'm willing to take a 100 MB RAM hit (or more if necessary) to not have to deal with these things.

Ubuntu w/ Unity 2d doesn't hit the GPU. However, many people seem to show that it hits both RAM and CPU pretty hard. I was wondering whether anyone has experience/numbers from 12.04 (or 11.10 if not). I think I can get used to the interface itself, so that's less of an issue. It's whether it will be responsive. One computer I'm looking at installing this on has 512 MB RAM... now it doesn't need to run super smooth because it won't be used often, but if Ubuntu 12.04 is pushing 400 MB RAM there may be issues. Again, I'm more worried about CPU overhead caused by just moving around the interface. If anyone has experience with that, it could potentially save me a ton of headaches.

Kubuntu w/ low-fat-settings. Shouldn't hit the GPU at all. Some people are reporting getting RAM consumption down to ~200 MB after disabling unnecessary services. That would be golden. I'm perfectly fine with anything up to ~300 MB RAM as even Windows XP + basic AV takes out ~260 MB RAM at idle... and linux doesn't make you wait for that huge AV/Windows update spike right at the beginning. I'm not sure about CPU on this setup as it seems like there is conflicting information. The other thing I ran into in 11.10 is that it seems like every time I touched Muon it borked the system. I don't mind doing the initial update from command line, but it would be nice to have the periodic updates applied graphically and automatically. Not sure if anyone has observations on Muon in 12.04 or if anyone knows of a good KDE alternative.

If all else fails, I'll stick with Xubuntu, but Kubuntu seems like it might treat me well if a couple things work well enough. Plus, it might be nice to be able to go the mainstream route with Ubuntu, but things aren't looking as hopeful there on the CPU usage front.

---

### Post by LewisTM on 2012-04-19
There is no short simple answer for you. Few people have tried all three setups in depth. I'll try to answer some Xubuntu-related issues and leave the rest to others.

1) _No reasonable menu editor_. That's fixed in 12.04.

2) _No default way to mount certain file systems like iso_. Installing Nautilus will add the 'Open with Archive Mounter' option to the Thunar right-click menu. Having Nautilus installed won't break anything.

3) _Ristretto_. I agree gThumb is much better. Go to Preferences/Viewer and set it to fit the image to the Window after each opening.

4) _Thunar_. Could you be more specific? Much can be added to Thunar through custom actions and plugins. More improvements will most likely appear in 12.10.

5) _USB stick_. Use the Disk Utility (palimpsest) to format etc.

6) _No GUI way to change timezone._ Install gnome-time-admin or the full gnome-system-tools. 

7) _Power Management_. Do you mean the Jupiter applet? It can be handy in some situations but is not always necessary since Xfce also has a power manager.

I agree Xubuntu is pretty barebones in its default configuration but it can be easily tailored to suit your needs. Once that's done it's relatively straightforward to copy settings from one user or system to another. The bonus is that the interface is less alien than Unity and it's more stable than KDE.

Cheers!

---

### Post by springshades on 2012-04-19
Yeah, I was hoping there might be one person who had tried out Kubuntu low-fat, one person who had tried Unity 2d, etc. Not so much a single person who had tried them all as that is a rather unreasonable expectation.

1. It will be nice to see a good menu editor. I'll definitely try it out. I'm pretty sure that it was alacarte that got me about halfway there but didn't have the ability to change anything that was actually important (like an application installed with an incorrect command).

2. I'd considered installing Nautilus even in 11.10. It's definitely something that I should try as it *might* fix several issues.

3. Here's the issue... install gThumb on 4 computers. Change the default program to open various image extensions in every account on all of these computers. Go into the menu to change this setting in every account... it's just a very strange default setting in my opinion and not worth bothering with for the 20-30 minutes it would take to make this single change on all the computers. If I miss a single setting on a single account, basically no one in my family is going to touch that computer again because they think it's broken. That, and similar issues like it, is why I was thinking of using a more fully featured DE.

4. There are many, and I realize that many things can be added through customization. Back to number 3 again. Being able to right click on certain file types or folders or devices and being given certain options... file previews... the fact that my desktop trash icon sometimes works and sometimes freezes for 30 seconds then gives an error saying it couldn't connect to the trash (I've googled the actual error message, it's not terribly uncommmon.) It's possible that Nautilus might fix some of these or it might add new issues. I'll probably play with it before the 12.04 release date.

5. I currently use two utilities to do everything I need to do. They work fine. I'll try your suggestion as it might be nice to have it down to just one (if it does everything I need). The main issue is whether other people can figure out how to use it or not... or whether they decide it will just be faster to boot another computer up instead.

7. For laptops. I think the package is called laptop-mode. Usually requires some slight file configurations. In 11.10, it wasn't installed by default which is fine as most computers aren't laptops. Not a terribly big deal as it's not something I have to install on all computers and it's not per account.

Thanks for your pointers. :)

---

### Post by theos911 on 2012-04-19
I recently tried Ubuntu 12.04 and am currently using Xubuntu 12.04.

System:
Pentium 4 HT 2.8GHz
1GB RAM
Nvidia 9800GT



**********************************************************
RAM after clean boot/login with automatic updates, update notifier, and bluetooth removed from startup apps as reported by htop.

Ubuntu 12.04 Beta
Unity 3D- Sorry, it seems I forgot to mark this one down... :(
Unity 2D- 290
GNOME Fallback (No Effects) - 168
MATE 1.2 - 183

Unity 3D felt sluggish and had my gfx card fan hauling within minutes with just firefox and update manager open. Unity 2D was easier on the GPU, but felt as slow. Sorry, I forgot to mark 3D, but IIRC 2D & 3D had similar ram usage. GNOME fallback was slower than Ubuntu Classic on 11.04, but a LOT faster than Unity. Unfortunately, it was still too different from Ubuntu classic for me. MATE was just a whim, but felt as snappy as Ubuntu classic on 11.04

**********************************************************


**********************************************************
RAM after clean boot/login with automatic updates, update notifier, and bluetooth removed from startup apps as reported by htop.

Xubuntu 12.04 Beta
Xubuntu Session - 153

Feels quicker than Ubuntu classic on 11.04, but just a tad slower than MATE.

**********************************************************

---

### Post by springshades on 2012-04-19
Thanks for the results. It's pretty useful to know that even if Unity 2d doesn't work out, fallback might be a better option for some of the computers.

---

### Post by springshades on 2012-04-19
Actually, if someone happens to post average RAM/CPU load of Kubuntu 12.04 + low-fat-settings, my question has been completely answered.

I already have a decent sense of the usage of Xubuntu and Ubuntu 12.04 from theos911's post. If Unity 2d is slow on the test machine, it will absolutely crawl on some of the computers I will be installing on, but fallback should work just fine.

---

### Post by jerome1232 on 2012-04-20
I wanted to point out that Ubuntu 2D will actually be heavier on cpu usage than 3d, since 3d offloads work to the gpu and 2D does not, Ubuntu 2D is **not** a lightweight alternative to 3d, it's just an option if your gpu won't run compiz.

as an after thought: I find it funny that every instance of 2D I capitalized, but every instance of 3d I didn't.

---

### Post by theos911 on 2012-04-20
> **jerome1232 said:**
> as an after thought: I find it funny that every instance of 2D I capitalized, but every instance of 3d I didn't.

I capitalized both.

> **jerome1232 said:**
> I wanted to point out that Ubuntu 2D will  actually be heavier on cpu usage than 3d, since 3d offloads work to the  gpu and 2D does not, Ubuntu 2D is **not** a lightweight alternative to 3d, it's just an option if your gpu won't run compiz.

Yes, that is an important point to mention. Unity 2D is more for "business" grade PCs with decent CPUs, but usually lousy integrated graphics. It decreases GPU load _at the expense of CPU load_.

---

### Post by springshades on 2012-04-20
Thanks for that info as it's something I didn't realize. I think I read too many of the early 2011 news stories when 2d was less featured than 3d and was advertised as a less resource intensive option. It makes sense now that 2d would have a heavy load since both versions now do basically the same thing.

Thanks again to LewisTM. I got around to fooling around with Nautilus, and I think it helped me to decide to take Xubuntu off my list of options. The result wasn't disastrous in particular, but it wasn't all that wonderful either... enough to convince me that if I want to use Nautilus, Ubuntu is going to be a better option for me. I'm sure I could get Xubuntu working but again it's the amount of tinkering it would require.

If nothing else, this has gotten me down to two possibly viable options of Ubuntu fallback and Kubuntu low-fat which will end up saving a lot of time and headaches. Thanks again to everyone.

My side note: Pretty sure I didn't capitalize any. Also, one of the posts I responded to doesn't exist anymore. Makes it look like I was talking to myself. XD

---

### Post by squilookle on 2012-04-20
I am also trying to determine which DE I want to run with when 12.04 is released (this is after about 18 months away from Linux and things have changed quite abit!)

I used Kubuntu at Beta 1 (but not with low fat settings, it idled at about 500mb ram), I have been using Xubuntu 12.04 for the last week, and last night did a clean install of Ubuntu 12.04 and will stick with it for atleast a week. 

I find that Xubuntu 12.04 uses about 190mb ram when I start it up, without running any applications. Typical usage (web browser, spotify, Geany) saw it go upto about 4-500mb. 

Ubuntu with Unity 3D starts at roughly the 300mb mark before starting any applications, and I have seen it go to over 700mb with the same apps running.

Contrary to the posts about CPU usage in Unity 2D and 3D (although I would have said they were right in theory) my CPU usage in Unity 2D sits on the 1% mark, but sits at 2% for Unity 3D. In Xubuntu, it sits at 0 - 1% when idle. 

In Unity 3D, I had to set blur to static as it was laggy otherwise. 

Generally, I feel that Xubuntu is snappier than Unity. Thunar starts immediately where Nautilus takes a few seconds. I have also found Xubuntu more stable, as Compiz crashed twice on me last night and had to be restarted, although, I have a few updates to do so will save any further judgement on stability until I have everything set up properly. 

I will post exact figures over the weekend if I get the chance. 

I'm using a computer with a Pentium 4 HT at 3ghz, 2.7mb ram, and a NVidia Geforce card.

---

### Post by theos911 on 2012-04-20
> **squilookle said:**
> Generally, I feel that Xubuntu is snappier than Unity. Thunar starts immediately where Nautilus takes a few seconds. I have also found Xubuntu more stable, as Compiz crashed twice on me last night and had to be restarted, although, I have a few updates to do so will save any further judgement on stability until I have everything set up properly. 

Xfce is DEFINITELY snappier than Unity. I would even say faster than regular Gnome Classic IMO.

In my quest to make Xfce look like Ubuntu Classic, I learned I needed a compositor for "transparency stuff". Compiz was nothing but a pain in the butt, while the default Xfce compositor has worked flawlessly since I enabled it **and** with nearly *no noticeable overhead*. (I was mainly looking to replicate Ubuntu's transparent purple terminals.)

I may have time over the weekend to try Kubuntu low-fat so you can have benchmarks from all three on the same [modest] rig.

---

### Post by springshades on 2012-04-20
I agree, one of my favorite things about Xubuntu is how well its compositor works for very basic stuff. It's just enough to make the desktop pleasing to the eye, and it might tick a hardly noticeable amount of extra CPU cycles when you're actually maneuvering windows. Outside of that, it has an almost completely negligible performance cost.

If it weren't for the multiple computers and multiple users thing, I'm pretty sure I'd stick with it and just use extra applications for the functionality I needed/wanted.

BTW, don't go to the trouble of testing Kubuntu out unless you were going to already. If no one else does, I'll try it out after the official release and post back some numbers for anyone interested. That makes the most sense since it's for my own benefit anyway. The thread was intended to be just in case others had already tried these things out already.

---

### Post by LewisTM on 2012-04-20
From the Software Center, it's possible to [synchronize]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/") the applications running on different computers. That might facilitate your administration.

Also you probably know all settings are saved in hidden files and directories inside the home folder. So you can set up one machine to work perfectly, take a snapshot and copy all or some of the config files over to the other users/machines.
You can use rsync for that in conjunction with SSH. SSH is also handy to remotely adjust the ownership of the new settings files and to perform routine upgrades and maintenance. So in effect you don't have to physically log in and play with menus and preferences for each user. This can be automated.

---

### Post by entangled on 2012-04-21
Though I haven't got anything on Xubuntu you might be interested in some timed results from running a Qt app (my own build of the Life program) on Unity and Kde.
The same program is used in each case, only the desktop login is different. 

I'm running Ubuntu 12.04 (up to date) as a dual boot on an iMac partition (OSX Lion is on the main partition).
The Qt app creates a gridLayout in a QWidget window and populates it with the next evolution of Life when a button is pressed. The processing comprises generating the next grid from the existing grid and displaying it as a new gridLayout of characters.
I thought this would run best on Kde but I found it was much quicker on Unity!

Timings of 'time ./life' for 10 evolutions, by manual button press (2 program runs):
            Kde 4.8.2         Unity 3-D       Unity 2-D
real        27.6 & 29.1       25.0 & 20.5     20.5 & 21.2
user        16.9 & 16.7       12.8 & 11.6     10.6 & 10.6
sys         0.21 & 0.20       0.19 & 0.15     0.14 & 0.12

So, for this particular program, just logging into the Kde desktop instead of Unity 2-D increases by over 50% the user time processing, and that's using a Qt application that Kde should handle well.

I don't know if this is relevant to your question but I am curious to know what is slowing down Kde.

---

### Post by springshades on 2012-04-21
That's pretty interesting since I would expect the operation to be bottlenecked by CPU, and according to previous posts, that means that Unity 3d should outperform Unity 2d since 2d should hit the CPU harder. I guess it's possible that it's the actual display step that is the bottleneck in which case, who knows.

I'm going to add my own input after having the chance to test Kubuntu as the last piece. Note that I use the free -m command which may not line up perfectly with the numbers given by others. This was done on a netbook, so the Plasma Desktop might show different numbers. I rounded my numbers to the nearest 5 or so.

Running as a "live" session RAM usage: 235 MB.
Running after install with everything default: 330 MB. (a lot more for some reason)
Running after install with lots of the desktop effects turned off and some unnecessary services off (e.g. Bluetooth). I also turned off the news "page" that I find unnecessary (somewhat similar to turning off an unused workspace): 300 MB.
Running w/ low fat settings installed: 220 MB.
Turning off some additional services that some people use but tend to hog resources (nepomuk and akonadi): 180 MB.

This isn't final of course. Just the result of a small amount of fiddling, but most of the big stuff is off. I should probably switch to Plasma Desktop for completeness. One issue here is that it's rather difficult in the Netbook workspace to run a very light CPU monitor while using the computer since apps default to full screen and cover up the CPU widgets. 

At idle with low fat settings, CPU usage averaged 2-3% load on my netbook ATOM 1.6 GHz CPU which was at the time downclocked to 800 MHz according to the monitor. Basic menu navigation (which involves some whooshy animations and such in the netbook workspace) caused CPU load to move up to about 20% max.

Qualitatively, most things are very responsive. Dolphin is much much faster to start than Nautilus in Xubuntu and comparable to Thunar in Xubuntu. Menu navigation is slower in KDE due to the icon animations than the simple Xubuntu menu. One note there though, I had to turn Xubuntu menu icons off in 11.10 because there was a notable lag when I opened the menu the first time after each boot caused by them, so the comparison is with a very simple, pure text Xubuntu menu. Synaptic is much faster than the built in Kubuntu package managers though come to think of it, I'm not sure if that was installed by default in Xubuntu either. KDE is of course significantly slower to start up than Xfce (might be about an extra 10 seconds on this machine), but I think shutdown is roughly the same.

I probably should mark this as solved now since there are results for all 3 setups. I might try to flip over to desktop and post back in case others are interested. I'm probably not the only one comparing the options right now.

EDIT: Hi again. Switching to desktop pushed RAM consumption up to 230 MB but had no noticeable effect on CPU. I believe at least part of the difference (~50 MB more) comes from the actual switch since changing back to plasma-netbook did not free up the extra RAM.

---

### Post by theos911 on 2012-04-22
Sort of related:

Clean install of openSUSE 12.1 KDE Plasma weighs in at 292 with all default settings.

---

### Post by Cheesemill on 2012-04-22
Another option is to use Ubuntu but with Gnome Classic instead of Unity.

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/)

---

### Post by theos911 on 2012-04-22
GNOME Classic/Gnome-panel != Ubuntu Classic

Edit - Though, anymore I don't really care. I've learned how: XFCE can look identical to Ubuntu Classic; KDE can do eyecandy without being in-your-face about it; and how LXDE provides a lightning slick, but extremely easy to understand option for older systems. If Ubuntu hadn't gone all Unity, I would never have looked into the others I now like. (Still kinda iffy on KDE, but I haven't used it long enough to judge it.)

---

### Post by dniMretsaM on 2012-04-22
What are you missing in LXDE (Lubuntu)? I personally find quite good, especially for slower computers. If you're feeling up to it, you might try rolling your own. That way you only get what you want without all that extra junk to slow your computer down. Granted, this is a slightly more advanced option, but well worth it.

---

### Post by springshades on 2012-04-22
Roll your own is sort of the opposite of the intention of the first post, and Debian is probably better at that than *buntu anyway.

I actually have quite a bit of experience with LXDE since one of my computers is a laptop from the stone age with 256 MB RAM. I've used quite a few light distros on it from an LXDE offshoot of Mandriva, to Lubuntu, to antiX. Currently it has Debian + Xfce for a grand total of ~60-70 MB RAM consumption though.

LXDE is great for that type of hardware but sadly it's just plain archaic when comparing the features and amount of tinkering required relative to most other DEs. I'm convinced that has less to do with it being light and more to do with the fact that it simply isn't finished yet. It comes down to having to install 3rd party applications for basic configuration sort of stuff. For now, I'm willing to take a performance hit for features on the computers that can actually handle it.

---

