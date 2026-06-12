---
title: "The Pain with ATI, how do i fix it?"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by SpinningAround on 2007-12-11
I recently bought a Asus X51R laptop with the a ATI Radeon Xpress 1100 or X1100 this do cause loads of problem (start wishing I did get a Nvidia card ;) )

I have tried the following using the ATI made drivers that simply don't work, the latest thing that happened was that the screen went black even after I tried with the backup xorg.conf

This is what I have tried.

Installed the drivers throw Restricted drivers, the result was that i was that 3d still wasn't working, even if glxgears did run better. Things that stop working was the hibernate and sleep.

So I did get Envy and installed Ati drivers from there with the result that  3d start working but with bugs, windows didn't update, when you moved a window didn't the things in the window follow but did stay where they was from the beginning.

So I uninstalled the drivers throw Envy and ended up with a blackscreen even if I used the backup that was create after I installed the restricted drivers.

So what should I do to get 3d working, hibernate and sleep working?

---

### Post by zaomaster on 2007-12-11
you could try this [http://ubuntuforums.org/showthread.php?t=636827](http://ubuntuforums.org/showthread.php?t=636827)

It's what helped me get my ati card to work with desktop effects.

hope it helps

---

### Post by emko on 2008-02-15
I`m having the same problem with my asus x51r... someone help !

zaomaster our video cards are Radeon Xpress 1100 and i don`t think the links are going to help... 
> (start wishing I did get a Nvidia card  ) me too

---

### Post by SpinningAround on 2008-02-15
> **emko said:**
> I`m having the same problem with my asus x51r... someone help !

zaomaster our video cards are Radeon Xpress 1100 and i don`t think the links are going to help... 
 me too

I got my working ok, i think there is some problem with the direct 3d rending since it requierd some setting to get the 3d effects on the workspaces to work.

What I did:
Installed Ubuntu
Installed the Restricted drivers
(can't remember exact but think the console gave the info, possible when running glxgear that xgl (?) was missing)
Installed xgl (xorg/xserver)

Well it's working ok atm, MPlayer don't work since it for some reason are setting the screen over two workspaces. Good thing is that vlc is almost working flawless (get a transparent diagonal line over the screen in a few cases)

ndiswrapper fixed the wlan, (I think I needed to blacklist ath_pci to stop the madwifi to interfere (maybe fixed now with the new kernel (if there is a new one))

---

### Post by X51r-user on 2008-04-20
HI

   Just a note for user spinningaround and other user of the laptop x51r i enable my hibernat and standby with the following

   edit /etc/dafault/acpi-support

    SAVE_VBE_STATE=false
    POST_VIDEO=false

thanks to user r!ots for this info.

---

### Post by Saint Angeles on 2008-04-20
check out my post here:

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

first, remove xserver-xgl as the latest fglrx driver does not need it.

---

