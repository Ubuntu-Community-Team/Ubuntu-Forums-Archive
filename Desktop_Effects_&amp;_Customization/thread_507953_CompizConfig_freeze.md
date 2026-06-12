---
title: "CompizConfig freeze"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by Moses on 2007-07-23
Hi

I've just taken the plunge from compiz vanilla (which has worked flawlessy for the passed 5 months) to compiz-fusion. It seems to be working correctly, but as soon as I change any setting in the CompizConfig setting manager, I have total lockup, i.e., screen/keyboard/mouse unresponsive, have to reboot manually.

Any ideas?

This is quite frustrating, as at the moment I can't even set multiple desktops!

---

### Post by openSourceRoy on 2007-07-23
Me too. Exact same symptoms.

The effects work by default when the machine is booted.  As soon as anything in the compizConfig settings window is enabled - total lockup.

I have fiesty, nVidia 5200FX, amd64.

---

### Post by Moses on 2007-07-24
So there are only two of us with this problem?

Just to clarify:

I'm using Fiesty with gnome.
Running an ATI X800pro, but not using the restricted driver.

---

### Post by Moses on 2007-07-24
I have made a little progress in diagnosing the problem.

I installed compiz-settings (a settings manager I have used in the passed) and then reinstalled compizconfig-settings-manager. I then ran compizconfig and it stopped freezing. I can now change any setting without problems... however these settings have no effect - with the exception of the cube settings (e.g., transparency, inside cube). All other settings I can change with no effect, e.g., the minimize animation is always zoom (what it was in the passed with compiz vanillla), no matter what I change it to in the compizconfig manager. 

I have since uninstalled the compiz-settings applicaton, but this has no effect on the influence of compizconfig-settings-manager.

I was always using a manager called "gl desktop" (I think), but I don't think this is the package name. This was a very basic settings manager that only had a few settings for cube on/off inside/outside, and a few transparency settings. I'm not sure where this app went (can't remember its name), but is it possible that it is causing these problems?

Also, where is the compiz config file? Perhaps I can dick around in there to see what is happening.

Thanks!


EDIT: I found the package I was using originally "gnome-compiz-manager", but it is uninstalled, so I don't know now what to try... :(

---

### Post by openSourceRoy on 2007-07-24
Is it possibly a problem with changing the settings while the compiz fusion effects are in operation? How can you turn the effects off?

Perhaps it is just a problem with the setting manager GUI and changing settings from the command line would solve the problem in the meantime? Do you know of any commands for any of the settings to test this?

---

### Post by chrisblue on 2007-07-27
No, I am having the same problem as well. Fresh install of Feisty, nvidia graphics card. Everything seemed to install OK, but trying to change anything caused the screen to lock up. Mouse cursor still works though.

---

### Post by atomkarinca on 2007-07-27
i had the same problem. i couldn't overcome so i did this:

followed this guide: [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769) and it came with compiz fusion icon. on the boot the corrupt compiz automatically starts, then i open the beryl manager and disable compiz, then i start compiz fusion icon and start compiz fusion.

i couldn't find a way so this is the workaround i could get.

---

### Post by nelio2k on 2007-10-27
For me it is a different issue...

Compiz-config manager works totally fine.
But, on any restart, it'll freeze up my Gnome, and I'll get stuck on the orange screen forever. I had to apt-get remove compiz-config-manager to have Gutsy boot successfully.

I have Nvidia GeForce 7025, which is relatively new, so I'm using the proprietary driver. 

Any thoughts? Right now I've got no compiz-config manager, but I'm using gconf-editor to customize my compiz... 

If you don't know... you dont REALLY need the compiz-config manager to make changes, but you can go start the program (Alt + F2), then type gconf-editor, and go under apps -> compiz -> plugins and do work there.

It's not as pretty, but it works.

---

### Post by nelio2k on 2007-10-30
Nevermind, even now it's still freezing. I ran sudo apt-get remove compiz- and its random add ons... now i think I've screwed up the GDM. I'm gonna probably reinstall 7.10. For some reason I suspect it is with my graphcs card, because it's rather new...

I really hope I don't get dissapointed with Gutsy. It runs reali reali well on my laptop

---

### Post by k0rfain on 2007-10-30
what is compiz-vanilla?

---

