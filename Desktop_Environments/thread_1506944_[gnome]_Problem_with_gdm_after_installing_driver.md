---
title: "[gnome] Problem with gdm after installing driver"
date: 2010-06-10
forum: Desktop Environments
---

### Post by QpSmiley on 2010-06-10
Okay So here is what happened
I installed 10.04 LTS Ubuntu
I updated everything
I went to apply a desktop effect, asked me to enable a driver
I enabled a driver
it told me to restart
I restarted

When I restarted GDM went out of control and I was brought to my first tty1 login screen
I freaked out, 
Then I went to the irc and people tried helping me.
they had me reinstall ubuntu-desktop
they had me restart gdm
a bunch of stuff like that, nothing worked

Then someone told me to sudo jockey-text --help
that was useful because it let me see the drivers that were availible

my list showed that xorg:nvidia_173 was enabled xorg:nvidia_96 was disabled and xorg:nvidia_default was disabled

So I disabled xorg:nvidia_173 and enabled xorg:nvidia_96

I didn't know what to do then so I sudo gdm
Then it brought me to a blank screen so I pressed the power button.

Then it restarted hello tty1 again I missed you.

What should I do now?

SOLVED!
____ following for future reference
I was told to backup my xorg.conf by typing in
sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf-bak
that copies your xorg.conf into a backup xorg.conf
then 
sudo nano /etc/X11/xorg.conf
it opens up a text editor, then I was told to change the line
Driver: "nvidia" to Driver: "nv"
nv is an open source driver

then pressed ctrl+x and then y to save
then i typed sudo gdm to reload my Gnome Desktop Manager and it ran! yayy!
My graphic card was GeForce 6150SE nForce 430 by the way

---

