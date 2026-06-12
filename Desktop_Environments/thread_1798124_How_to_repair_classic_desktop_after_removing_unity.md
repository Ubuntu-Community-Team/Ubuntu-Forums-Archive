---
title: "How to repair classic desktop after removing unity?"
date: 2011-07-05
forum: Desktop Environments
---

### Post by noloader on 2011-07-05
[FONT=Arial][SIZE=2]Hi All,

I upgraded from a fairly stock 10.10 installation to 11.04. For whatever [brilliant] reason, Unity was installed on my wide screen laptop (Unity is the tablet-top and net-top window manager).[/SIZE][/FONT][FONT=Arial][SIZE=2]

Using Synaptic, I uninstalled everything related to Unity. Unity, being burrowed in like a virus, was entangled with some stuff I use, such as Evolution (and empathy, ubuntu one, et al). After rebooting, my classic desktop was missing its launchers.[/SIZE][/FONT][FONT=Arial][SIZE=2]

How do I repair this mess created by Unity? I'm very interested in getting my launchers back since I don't know all the command lines required. Neither `[/SIZE][/FONT][FONT=Arial][SIZE=2]
sudo -u gdm gconftool-2 --recursive-unset /` nor `gdm --reset` worked.

```

jeffrey@studio:~$ gdm --reset
** (gdm-binary:1957): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.43" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file[/SIZE][/FONT][FONT=Arial][SIZE=2]
** (gdm-binary:1957): WARNING **: Could not acquire name; bailing out[/SIZE][/FONT]

```[FONT=Arial][SIZE=2]

Jeff[/SIZE][/FONT]

---

### Post by noloader on 2011-07-05
"Unity is designed for netbooks and related touch-based devices." - from [http://unity.ubuntu.com/projects/unity/](http://unity.ubuntu.com/projects/unity/).

Why in the world would Ubuntu decide to replace a perfectly  well-functioning desktop environment with a tablet-top/netbook-top  manager?

---

### Post by noloader on 2011-07-05
[Bug report filed: https://bugs.launchpad.net/ubuntu/+source/unity/+bug/806295]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/806295")

---

### Post by mcduck on 2011-07-06
Whatever the description says, as Unity is the default desktop for 11.04 and all the following Ubuntu releases it, at this point, is designed for desktop as well.

Anyway, the easy (and correct) way to use the old Gnome desktop instead of Unity would be simply selecting it at the login screen. No need to uninstall Unity.

What comes to fixing the situation, it sounds like you ended removing a bit more than just Unity and that's the problem. I'd recommend reinstalling the ubuntu-desktop package which should give you back everything that belongs to the default setup. And after that choosing the "Ubuntu Classic" option as your session from the login screen instead of trying to remove Unity.

---

### Post by dFlyer on 2011-07-06
Restore unity and select classic gnome from the login menu, or just reinstall 11.04.

---

### Post by MARP1961 on 2011-07-06
If you dislike Unity this much, the Classic Gnome is fine until you finally upgrade to Ubuntu 11.10 or later. When this happens, Ubuntu will no longer come with the trusty old Gnome 2 but rather the revamped Gnome 3. You will no longer have a 'classic' option and only Unity (3D or 2D) will be default login options!

However, in the Ubuntu 11.10 repositories will be an alternative 'shell' to Unity that you can install and use. This 'Gnome Shell' is so much better than Unity I would urge you to try it out right now. There is a ppa for the Gnome 3 Team that will convert your present 11.04 installation into Gnome 3. The only problem is that because the present Unity is being run on top of Gnome 2 then doing this will break Unity. Somehow I think you will not mind this happening!

I followed the instructions for installing via the Gnome 3 Team ppa and am very pleased with the results. If you want to try it out first, then get yourself a live CD of Fedora 15 and try it without installing. Interestingly, Gnome 3 has a fallback option for those computers that do not have 3D graphics capability. That fallback mode is very similar to the old classic Gnome 2 you like. So if by chance you do not like either Unity Shell or Gnome Shell there is Gnome 3 fallback for the future. All Linux distros will eventually abandon Gnome 2 anyway so it's time to look to alternatives. Nothing except this universe is forever.

---

