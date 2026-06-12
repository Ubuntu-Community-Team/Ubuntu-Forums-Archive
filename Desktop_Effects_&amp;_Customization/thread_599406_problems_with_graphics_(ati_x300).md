---
title: "problems with graphics (ati x300)"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by tadah on 2007-11-01
Hello,

I have an ATI sapphire Radeon X300SE and I can't get it all right. Mainly it's because Desktop effects don't work.

I go to the Restricted Drivers Manager and check ATI accelerated graphics driver to be enabled. Then I'm asked for a reboot. After rebooting I get this message: "Ubuntu is running in low-graphics mode". So I click "Configure". My monitor settings somehow are set to: "Model: Plug'n'Play, Res: 800x600", so I set Model to "Generic LCD Panel 1280x1024" (I have CTX S730A+ 17" LCD 500:1 16ms monitor, but I didn't find that model in the list, so I chose that one (bad idea?)). Then I'm asked to restart again. Now I go to the Restricted Drivers Manager and the ATI accelerated graphics driver is disabled. Why is that? What do I do wrong?

And one more thing to the same topic. I go to the Screen and Graphics Preferences to choose a driver. I pick ATI Radeon (fglrx). Ctrl+Alt+Backspace. And now I have like about 25% from the bottom of the screen light brown like a shade. I can move the mouse over it, but everything else goes underneath it.

Thanks for any advice.

---

### Post by Person98 on 2007-11-01
I had a similar problem, i find the GUI configuration tool just messes things up try 
  sudo dpkg-reconfigure -phigh xserver-xorg
in the terminal it just resets and updates your graphics configuration file; it worked for me

good luck

---

