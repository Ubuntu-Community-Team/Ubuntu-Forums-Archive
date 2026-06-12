---
title: "Changing the Kubuntu boot splash theme at startup"
date: 2010-07-22
forum: Desktop Environments
---

### Post by Drone4four on 2010-07-22
I recently installed kubuntu-kde and it changed the boot splash theme from an orange logo on a purple background to tourqoise on blue.  How do I change it back?

In KDE, I can navigate to Settings > System Settings > Appearance > Splash Screen but that's not what i'm looking for.  I'm not trying to change KDE's Splash Screen that shows when you load the KDE window manager after logging in as a user. Further, I'm not trying to change grub's boot splash image, which renders [this]("http://linuxers.org/howto/how-change-grub2-splash-images") guide useless.

I want to change the boot splash theme which lasts 25 seconds that is shown between the time your select the kernel in grub2 and the time gdm loads.  Right now it says "Kubuntu" in an ugly way and I want to change it back to what it was originally before I installed KDE.  I want it to say "Ubuntu" as it should by default.

How can I better describe what I am trying to do so I can search for it on Google?  What Google search terms will yield the results I am looking for?

---

### Post by Drone4four on 2010-07-22
CkhiKuzad in #Ubuntu on FreeNode recommended startupmanager.  With startupmanager installed, I changed the Display Resolution from 640*480 to 1600*1200.  I also changed the Bootloader menu resolution from 640*480 to 1600*1200.  I changed the colour depth from 8bits to 24bits.  I ticked the "Show boot splash" option on.  I changed the timeout in seconds from 10 to 30.  And then I clicked close.

ActionParsnip also in #Ubuntu recommended [**this**]("http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html") link.  As per that guide, I haphazardly entered the following commands:

```

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u

```

I reboot my computer and whammy! Now on my desktop I have a framebuffer problem as per the low res attached screenshot.  [**Here**]("http://img130.imageshack.us/f/screenshotfbproblems.png/") is the same screenshot in full resolution on ImageShack.  In retrospect, I prolly shouldn't have changed all those options in startupmanager and entered all those update-alternatives commands all at once.

How do I better describe my problem?  How do I get rid of the frame buffer? Is there a command I can use to undo the update-alternatives command? I suppose I should be asking the author of that plymouth guide, but unfortunately s/he isn't available.  A post under the General Help category might not give rise to the answer to my question.  So where else would be a good place to ask?

---

### Post by overdrank on 2010-08-03
Moved to Desktop Environments and bumped :)

---

### Post by Yuri sss on 2010-08-03
> **Drone4four said:**
> I recently installed kubuntu-kde and it changed the boot splash theme from an orange logo on a purple background to tourqoise on blue.  How do I change it back?

Remove the Kubuntu boot screen which is included in the following package:
```
sudo apt-get remove kubuntu-default-settings
```

After that, install the purple Ubuntu boot screen which is included in the package:
```
sudo apt-get install plymouth-theme-ubuntu-logo
```

---

### Post by Drone4four on 2010-08-03
> **Yuri sss said:**
> Remove the Kubuntu boot screen which is included in the following package:
```
sudo apt-get remove kubuntu-default-settings
```

After that, install the purple Ubuntu boot screen which is included in the package:
```
sudo apt-get install plymouth-theme-ubuntu-logo
```

I forgot to mention in my second post that between the advice given to me by  ActionParsnip and CkhiKuzad I successfully changed the bootsplash from KDE back to the default purple splash.  However now I am having frame buffer problems, which changes the the purpose of this thread.  I changed the topic, but in the forum it doesn't look like it has changed.  Should I start a new thread?

Given the nature of my new frame buffer problem, should I file a bug report? If a developer saw my frame buffer problem, could I get a solution that way?

---

### Post by Drone4four on 2010-08-04
If I was to make a new thread about my frame buffer problem, which sub forum should I put it in?

---

### Post by Maverick_Meerkat on 2010-08-04
To fix the delayed loading of the splash:

```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
```

---

### Post by Drone4four on 2010-08-04
> **Maverick_Meerkat said:**
> To fix the delayed loading of the splash:

```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
```

I entered those 3 commands.  I rebooted and I still have the same problem.  The contents of my /etc/initramfs-tools/conf.d/splash look like this:

```
FRAMEBUFFER=y
FRAMEBUFFER=y

```
I am changing the contents to this to see if it fixes my problem:

```
FRAMEBUFFER=n
```

And then I run:

```
update-initramfs -u
```

---

### Post by Drone4four on 2010-08-04
Now when Ubuntu loads at startup I don't see a logo at all.  The frame buffer is truly messed up.  But does this solve the framebuffer problem at the desktop as was the case before? I see a minor improvement. See attached for, what I call, my framebuffer problem.  Since I disabled the framebuffer in /etc/initramfs-tools/conf.d/splash, and my problem persists, could this mean that what I am experiencing in the attached image is not a framebuffer problem at all?  **If it's not a framebuffer problem, then wtf is it?**

Here is a higher resolution version of the attached desktop screenshot:
[http://img805.imageshack.us/img805/1108/screenshotfbproblems2.png](http://img805.imageshack.us/img805/1108/screenshotfbproblems2.png)

edit: I just checked: my virtual terminals are unusable because the framebuffer problem as a result of changing the contents of /etc/initramfs-tools/conf.d/splash.  I'm forced to change the FRAMEBUFFER option back to "y" instead of "n".

---

### Post by Maverick_Meerkat on 2010-08-04
The commands I posted should only effect the splash screen shown at boot (Plymouth). It would not effect the problem you are experiencing on the desktop. Sorry, I didn't realize you had that issue as well.

Unfortunately, I have no idea how to resolve that (desktop) problem. I certainly hope someone can provide a solution.

---

### Post by Drone4four on 2010-08-04
That's ok, Maverick_Meerkat.

I've now looked at the update-alternatives man page and I am going to try this command:

```
sudo update-alternatives --remove-all default.plymouth
sudo update-initramfs -u
```

I will reboot my computer and report back to this thread. brb

---

### Post by Drone4four on 2010-08-04
That command worked.  If only I read the man page I could have solved my problem before asking in the forum.:D

---

