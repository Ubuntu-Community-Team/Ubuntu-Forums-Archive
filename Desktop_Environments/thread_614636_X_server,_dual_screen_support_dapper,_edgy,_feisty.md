---
title: "X server, dual screen support dapper, edgy, feisty, Gutsy"
date: 2007-11-16
forum: Desktop Environments
---

### Post by jmaryinchina on 2007-11-16
My Laptop is a compaq EVO N160, quite old computer with radeon card, running smoothly with a pentium III.

With pain I succed to configure a dual screen on Dapper. I could have benefit of a nice dual screen, displaying a 2048x768 Desktop.

When Dapper move to Edgy, my xorg.conf file had to be modified, small modif but workable.
When Feisty arrived, nothing was possible to do, I had to choose to run on the external screen in 1280x1024 or on the the laptop screen in 1024x768.
When Gutsy arrived, it became even worse, I can't use anymore the external screen, I'm confined to the laptop screen.

Using the external screen (Dell 1704FPT) is producing some very strange effects : the resolution is a mix between 1024x768 and 1280x1024.

The desktop is displayed from the top left corner using 1024 pixel x 768 pixel for gnome desktop, but the mouse can move everywhere like if it was a 1280x1024 screen.

The displayconfig-gtk utility has only one effect freezing the system at kernel level, no ssh connection is possible from another computer.

Conclusion : My nicely made xorg.conf file couldn't be kept across versions, and the more I saw evolutions to be announced, the most my display config was ****** up.

That's a fact, I can't say quality is increasing, what I saw is exactly the opposite. Just make me want to go back to Dapper.

My graphic card is :01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
I have already spent several days to try to solve this issues ... nobody knows ... I got just silence.

---

### Post by niqdanger on 2007-11-16
I have the same issue. Only i had dual screens working in Feisty via the mergedfb option. Seems it is busted somewhere in one of the later updates. I updated from Fiesty to Gutsy and it was fine. Used it single monitor these last 2 weeks, done a bunch of updates and now today, no dual monitor. Ugh.

From what I can find, it seems to be a driver issue with the proprietary ati driver. There are some notes about downgrading back to xorg from fiesty (including the drivers) but I cant find the links I had saved. Annoying it seems to be only with the older ATI Radeons including the M6 LY but not all ATI Mobility Radeons as I've followed a bunch of how to's that dont work for me.

---

### Post by niqdanger on 2007-11-17
After doing some debugging, it seems the MergedFB option was removed from the ati driver. You have to use xrandr now to do a dual desktop setup. The fglrx driver does not work at all with the radion mobility M6, it just craps out and goes to a vesa driver. My best option seems to be the opensource driver "ati"

Old link:  [http://ubuntuforums.org/showthread.php?p=1773710](http://ubuntuforums.org/showthread.php?p=1773710)

I followed mergedfb under feisty and it worked. That is not an option under gutsy due to something changing. Look at your /var/log/Xorg.0.log and you'll see the message about mergedfb going away.

[INDENT]Xorg.0.log:(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
Xorg.0.log:(WW) RADEON(0): Option "MergedNonRectangular" is not used
Xorg.0.log:(WW) RADEON(0): Option "MergedXineramaCRT2IsScreen0" is not used
Xorg.9.log.old:(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
Xorg.9.log.old:(WW) RADEON(0): Option "MergedFB" is not used[/INDENT]


I googled around for xrandr and found quite a few help pages. I dont have dual desktops working yet, but I did get both monitors up/on, and I can turn them on/off independently. I just didnt finish last night before I signed off. I'll get it working today I hope :-)

Try this link for useful info

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by shawnc_nmb on 2007-11-17
I too have had problems w/ the xorg.conf,  but after reconfiging my xorg for gutsy, and reading about xrandr i have made it work,    except after 2048x2048  total  screen  size  it break's  compiz,  but you still get 2 screens. I wrote a blog  post about it  with [information here]("http://www.shawnc.org/2007/10/30/ubuntu-gutsy-upgrade-dual-head-monitors-now-working/")

Theres actually a good bit of information thee, my  video card is the Intel card but the xrandr info will still work for you.

---

### Post by veloce on 2007-11-17
Good blog shawnc_nmb

My "definitive" source for xrandr and dual screens is: [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

But I certainly agree that this whole dual screens thing has been a cat's breakfast. I'm hoping xrandr 1.3 will be the answer ...

---

### Post by jmaryinchina on 2007-11-18
YES !!!!! My dual head is back.

There is something stange by the way, my external screen must be on the right.
No other choice. The laptop screen is refusing to start to display at position 1024x0.

The link [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12) saved my life. I'm so happy, web development with 2 screens is far much convenient.

Thanks for your help.

---

### Post by veloce on 2007-11-19
> **jmaryinchina said:**
> 
The link [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12) saved my life. 


I tried to find a way to thank the author of that page but can't seem to find an easy way.  It has certainly helped a lot of people!

---

