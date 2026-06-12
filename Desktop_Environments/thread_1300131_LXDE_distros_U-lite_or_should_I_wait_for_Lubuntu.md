---
title: "LXDE distros: U-lite or should I wait for Lubuntu?"
date: 2009-10-24
forum: Desktop Environments
---

### Post by Lavabug on 2009-10-24
Hi everyone,
I'm finally hopping aboard the ubuntu/linux train and getting the OS for my older laptop with very modest specs. I've already tried Xubuntu but didn't notice a significant improvement in speed over XP, so I want to try an even lighter version running LXDE. 

When is Lubuntu coming out as an installable CD? Is the U-lite project any good? Is it worth waiting for Lubuntu or will U-lite do well as a permanent OS for my older laptop?

---

### Post by lazy-devil on 2009-10-24
I don't know when we'll see Lubuntu. I'm hoping shortly after we see 9.10 come out. I have no experience with U-lite, but have been very pleased with LXDE running on 9.04 Ubuntu on an old Compaq tablet. The tablet was very slow with XP tablet edition. Changing to Xubuntu saw a slight speed increase, but the a much more stable operation. Changing from XFCE to LXDE saw real a speed increase. The RAM usage is much lower for LXDE.

Whenever Lubuntu comes out, I urge you to try LXDE now. Install plain Ubuntu with the Alternate installer CD, then install LXDE on top of that. I'm sure you'll like it. The minimal Ubuntu + LXDE installation is covered here:

[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

Chuck

---

### Post by XubuRoxMySox on 2009-10-24
Lubuntu may be aiming to do only the LTS releases rather than every six months. If an official Lubuntu release doesn't appear by the end of November, it may not actually be released until April 2010 (the next LTS). Until then, "lubuntu-desktop" may be a metapackage available in Karmic. To get Lubuntu Karmic, install minimal Ubuntu, then

```
sudo apt-get install lubuntu desktop
```

Assuming that the metapackage will indeed be available with Karmic. If not, simply running LXDE on top of "regular Ubuntu" hugely increases it's speed and simplicity.

LXDE itself has a lot of components that are still under heavy development, which I'm guessing accounts for some of the delay in getting Lubuntu out as an .iso.

U-Lite (formerly Ubuntulite) was the earliest Ubuntu-based LXDE distro. It is available as an .iso and based on Ubuntu 8.04, Hardy Heron. The jaunty version is installed by means of a script on top of a minimal Ubuntu (CLI) installation.

-Robin

---

### Post by shae on 2009-10-25
This is actually rather cool to see this come up here.  Hi I am Shae from U-Lite and I would like to say it should not hurt to give it a try.  If you are already comfortable with Linux and the thought of a commandline install does not cause you to fret, I would suggest you try our version based on Ubuntu 9.04.  I think it works really well, but in some ways we are stuck against Lubuntu moving forward looking for a way to be "different".

Just to make a simple note, U-lite does not stick to "stock" LXDE as much as Lubuntu will.  We certainly put our own look on it and hopefully it is something that people enjoy using.  Let me know how else I can help out.

Shae Smittle
U-Lite Linux Project

---

### Post by Lavabug on 2009-10-25
Thanks everyone, but now I'm actually confused as to what is best for me lol. Would a minimal install of Ubuntu + LXDE be faster than U-lite? Installing Ubuntu on my system might be painfully slow. I really just need the easiest-to-use/install and fastest lxde version I can get with the least compatibility problems. By now it should be obvious I'm not a power user lol, I just want something that works.

What about other distros that come with lxde preinstalled or as a default(like opensuse 11.1, knoppix and fedora)?

---

### Post by earthpigg on 2009-10-25
LXDE from a command line install is [sort of broken (but kind of still works)]("http://ubuntuforums.org/showthread.php?t=1299214") in 9.10 unless you want to install GNOME as well.

i very strongly suggest you install xdm ***before*** installing lxde. for now.

im working on a proper solution now that does not use xdm and it's very basic functionality, and does not rely on 9.04 packages. i will post & document it when i do find it.

---

### Post by Lavabug on 2009-10-25
> **earthpigg said:**
> LXDE from a command line install is [sort of broken (but kind of still works)]("http://ubuntuforums.org/showthread.php?t=1299214") in 9.10 unless you want to install GNOME as well.

i very strongly suggest you install xdm ***before*** installing lxde. for now.

im working on a proper solution now that does not use xdm and it's very basic functionality, and does not rely on 9.04 packages. i will post & document it when i do find it.
I'm sorry but you kind of lost me. :p What is xdm? Isn't there any LXDE-based distro that's usable right out of the box for a total newbie? It's going to be installed on an old laptop used by mainly non-techies.

---

### Post by earthpigg on 2009-10-25
> **Lavabug said:**
> I'm sorry but you kind of lost me. :p What is xdm? Isn't there any LXDE-based distro that's usable right out of the box for a total newbie? It's going to be installed on an old laptop used by mainly non-techies.

sorry, my post was out of place in this thread. i was pretty tired when i wrote that -- people that install command-line-only systems and add lxde manually need to worry about the stuff in my prev post, not others. my bad!

here is a list of lxde-based distributions:
[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

cheers, and happy ubuntu-ing!

---

