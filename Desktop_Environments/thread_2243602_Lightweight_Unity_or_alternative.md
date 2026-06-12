---
title: "Lightweight Unity or alternative?"
date: 2014-09-10
forum: Desktop Environments
---

### Post by jerm10272 on 2014-09-10
Hello community! I use to use Ubuntu a while ago, I believe 12.04 was the last Ubuntu I used (I use Mint now primarily) and there were certain things I really like about Unity. However, I didn't like the direction Conanical was taking with Unity, so I stopped using Ubuntu and switched to Mint as my daily driver, so I may be a little out of touch with the specifics of Ubuntu...

The thing I love about Unity is the efficient use of screen real estate. On Netbooks, it's particularly helpful given the utter lack of it. However it seems Unity has become entirely too bloated to use on netbooks, which is a real shame considering how compact it is. I know Ubuntu Netbook Remix is no longer is service, but I recall a Unity2D, but I can't seem to find on Ubuntu 14.04, or any netbook optimization options. 

The Netbook I'm trying to use Ubuntu/Unity on is an older HP Mini, with an N270 Atom CPU, 512MB RAM, 8GB SSD, Intel GMA 945, and 1024x600 resolution. Thinking there was a lightweight Unity built in (documentation [here]("https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Netbook_Edition")), I went ahead and installed the full Ubuntu 14.04 Desktop, and needless to say, performance leaves much to be desired

I was wondering if a lightweight version of Unity is even in existence anymore, and if not, what are my options to retain the compact look and feel of Unity in lighter environment? Because of the scarce resolution, I don't think a traditional desktop layout would work, especially given the scarce vertical resolution.

---

### Post by TheFu on 2014-09-10
LXDE can be used. Just place the lxpanel on the left side of the screen.

---

### Post by jerm10272 on 2014-09-10
I don't suppose I'd be able to integrate program menus into the top panel as Unity does, could I? It's part of the compact features I like.
[IMG]http://i.imgur.com/xiyb0J8.png[/IMG]

---

### Post by TheFu on 2014-09-10
Wouldn't know - doubtful.

You actually LIKE THAT?  Ewwwww.

I find that the most offensive aspect of Unity - besides demanding a GPU with 3D-accel support in hardware.  That 2nd requirement doesn't work well inside virtual machines, which is how I run almost everything.

A $200 Chromebook (Acer C720) can easily run Unity, if that is your desire. The lack of HW GPU support is the main issue with your netbook, though the CPU is really slow compared to current-gen APUs.  I switched from a similar Asus Eee about 8 months ago - it didn't have good GPU support either and used the same APU. The new Haskell CPUs are amazing with great GPU support built-in.  

However, everything isn't great with the C720 - it comes with an odd keyboard layout and many, many missing keys.  For example, it doesn't have a DEL key and the power key is where the DEL belongs. Took me over 2 months to stop hitting the DEL key 20 times a day (caused the machine to power off). Dell sells any 11" notebook that I'd get. Also saw a new Acer 11" notebook for $180 last week at the local computer box store. Main thing is to get the Haskell CPU - low power, yet relatively high performance.

I get the desire for small, travel-ready, devices.  I've tried traveling with just a tablet - that didn't turn out well at all.  Just not enough OS in that platform for my needs.  The C720 has great battery - 8+ hrs - nice performance (like a 1st Gen Core i5 mobile CPU), it is light and higher resolution. Video playback is 100% GPU-based, not CPU. If it had more RAM (not upgradeable) and a standard keyboard, I'd be very, very happy with this $200 machine.

---

### Post by thnewguy on 2014-09-10
Ubuntu 12.04 was the last release to offer Unity 2-D, the light 2-D option has since been dropped. We now get Unity 3-D or nothing. I think this is a shame since I generally preferred the 2-D experience. You can still install Ubuntu 12.04 and run it on your netbook as that release is supported through until 2017.

SymphonyOS offers a strange interface where windows are always full screen and the menu bar is thus always at the top of the display. The latest release is very buggy, but the desktop environment they use is very lightweight. Symphony is based on Ubuntu so you would be using most of the same packages.

---

### Post by vasa1 on 2014-09-10
> **jerm10272 said:**
> Hello community! I use to use Ubuntu a while ago, I believe 12.04 was the last Ubuntu I used (I use Mint now primarily) and there were certain things I really like about Unity. However, I didn't like the direction Conanical was taking with Unity, so I stopped using Ubuntu and switched to Mint as my daily driver, so I may be a little out of touch with the specifics of Ubuntu...
...
One of the claims Mint users make is that the Mint developer listens to users. So why not ask for this feature in Mint? That way, you won't need to worry about the direction Canonical is taking.

---

### Post by jerm10272 on 2014-09-10
> **TheFu said:**
> Wouldn't know - doubtful.

You actually LIKE THAT?  Ewwwww.

I find that the most offensive aspect of Unity - besides demanding a GPU with 3D-accel support in hardware.  That 2nd requirement doesn't work well inside virtual machines, which is how I run almost everything.

 I like it when I only 600 pixels of vertical space. Outside of that, I can't stand it. Hence why I use Mint on most other machines. I think Unity just has a personality disorder - it really doesn't know what it wants to be.

> **thnewguy said:**
> Ubuntu 12.04 was the last release to offer Unity 2-D, the light 2-D option has since been dropped. We now get Unity 3-D or nothing. I think this is a shame since I generally preferred the 2-D experience. You can still install Ubuntu 12.04 and run it on your netbook as that release is supported through until 2017.

SymphonyOS offers a strange interface where windows are always full screen and the menu bar is thus always at the top of the display. The latest release is very buggy, but the desktop environment they use is very lightweight. Symphony is based on Ubuntu so you would be using most of the same packages. I tried 12.04.5, and while faster, there was less options compared to 14.04, such as UI/border scaling. I ultimately ended up going Linux Mint 17 MATE. It strikes a nice balance of light weight (~160MB RAM usage idle) while still being full-featured and customization options.

> **vasa1 said:**
> One of the claims Mint users make is that the Mint developer listens to users. So why not ask for this feature in Mint? That way, you won't need to worry about the direction Canonical is taking. Because forking GNOME 2 and GNOME 3 wasn't enough redundant work. Let's fork Unity, trim the fat, and offer yet another DE choice because Mint doesn't quite have enough. I think as other users pointed out, it may be better just to try to manually tweak another DE to get the look and feel down, maybe even adding a dock instead of a panel. Again, I decided Mint MATE was a good way to go. It struck a nice balance, and was quite usable on 512MB, but I guess it helps that the swap in on a SSD.

Thanks for the input guys. I'm still a little bummed about Unity, but I think MATE will work out.

---

