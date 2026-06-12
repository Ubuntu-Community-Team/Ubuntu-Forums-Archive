---
title: "How I got Nvidia and special effects working (gusty gibon)"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by comfortablynumb on 2007-10-22
I just did an upgrade from Fiesty Fawn (which was a clean install when it came out) to Gusty Gibon. I never did get the Nvidia drivers to work right in Fiesty Fawn (Geforce 2), so some of this post won't apply to clean installs. After preforming the upgrade, it had installed the restricted drivers, and they still where not working, and I also had an old version of Envy installed that wasn't removed during the upgrade.

- I removed the restricted drivers
- I removed the old version of [Envy]("http://albertomilone.com/nvidia_scripts1.html") 
- Installed the new version of Envy, ran the uninstall Nvidia drivers
- Restarted computer, Ran Envy install Nvidia drivers, I let Envy configure X and Restarted computer.

After the restart, I was still unable to enable the new Visual effects so I:

- Installed Compiz (installable through Synaptic)

- Restarted X (alt cntrl backspace)

Now I was getting a Composite error trying to enable the effects, I did a search through the posts and found this which helped fix that error:
- go to terminal, sudo gedit /etc/X11/xorg.conf

Section "extensions"
                Option        "Composite" "1"   If it has a 0 or disable change to 1


I restarted X and thought for sure that would have to do it, still wasn't working. After more searching I discovered I was missing  **XGL** 
- Installed xserver-xgl through Synaptic Package Manager

Restarted X server and was then able to  run the new Visual Effects

---

