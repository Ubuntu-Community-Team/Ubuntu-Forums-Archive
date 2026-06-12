---
title: "Uh Oh!.. edited xorg.conf"
date: 2006-08-19
forum: Desktop Environments
---

### Post by joshier on 2006-08-19
Hello

I edited the /etc/X11/xorg.conf file, and made all the 640x screen res to 1280x768 for my laptop display, but everytime I go into ubuntu, I get a really fuzzy looking aweful display, one so bad I cannot even see what I'm doing.

I'm aware that I cannot change files from one linux distro to another (I'm in mepis now, and it has trouble even seeing the ubuntu partition ~etx3) so it's no hope for me editing the file in there.

What are my options?.. I don't want 1024x768.

My display hardware is an S3 graphics UniChrome Pro IGP but ubuntu did not install it, and it also set it on 'VESA'. 

I tried to install the S3 graphics UniChrome Pro IGP before but the instruction were far too complex, and even the guide said you needed to be more than a novice before you even attempt it.

---

### Post by Tomosaur on 2006-08-19
Press ctrl+alt+f2 to switch to a virtual terminal, and edit your xorg.conf file that way. Reboot when you're done, and test out your new settings. You could also just try booting directly into recovery mode, which is essentially just a terminal.

---

### Post by mlind on 2006-08-19
You can use dpkg-reconfigure to get sane defaults in xorg.conf
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by joshier on 2006-08-19
> **Tomosaur said:**
> Press ctrl+alt+f2 to switch to a virtual terminal, and edit your xorg.conf file that way. Reboot when you're done, and test out your new settings. You could also just try booting directly into recovery mode, which is essentially just a terminal.

I've tried this but I don't know how to open the file. I tried sudo gedit /etc/X11/xorg.conf no luck.

---

### Post by DirtDawg on 2006-08-19
> **joshier said:**
> I've tried this but I don't know how to open the file. I tried sudo gedit /etc/X11/xorg.conf no luck.

Not fancy, but it will get the job done. Try ```
sudo nano -w /etc/X11/xorg.conf
```

Or maybe emacs or vim will work?

---

### Post by Lunar_Lamp on 2006-08-19
if you're in a terminal interface like that, you can't use gedit as it has no graphical interface.  There are several editors you can use; vim, emacs, nano.  I usually find nano to be the most intuitive to a first-time user.  Just replace "gedit" with "nano".  There are the shortcut keys listed at the bottom of teh screen, just remember than ^X = CtrlX.  I would try the reconfigure option first, it's fixed many things for me previously.

---

### Post by joshier on 2006-08-19
Well, I fixed it with sudo dpkg-reconfigure xserver-xorg but I'm back to square one. I stil have 1024x768.

---

### Post by joshier on 2006-08-19
Someone needs to write a script for the S3 graphics UniChrome Pro IGP, and then they need to implement it in edgy eft for automatic instillation.

---

### Post by mlind on 2006-08-19
Make sure that the refresh rates are correct for your monitor in xorg.conf and then just select desired resolution from GNOME (or KDE). I think gdm (or kde) should respect and use that resolution too.

---

### Post by joshier on 2006-08-19
> **mlind said:**
> Make sure that the refresh rates are correct for your monitor in xorg.conf and then just select desired resolution from GNOME (or KDE). I think gdm (or kde) should respect and use that resolution too.

I don't know what the correct refresh rate is for 1280x768.

I'm using Gnome and it only displays up to 1024x768

---

### Post by mlind on 2006-08-19
> **joshier said:**
> I don't know what the correct refresh rate is for 1280x768.

I'm using Gnome and it only displays up to 1024x768

If you monitor is capable for higher resolution than 1024x768, then find its manual and lookup the refresh rate values. Google may know those too.

btw. Wrong values might damage the monitor..

---

### Post by joshier on 2006-08-19
> **mlind said:**
> If you monitor is capable for higher resolution than 1024x768, then find its manual and lookup the refresh rate values. Google may know those too.

btw. Wrong values might damage the monitor..

I know, brilliant :roll: 

It's a LCD screen so refresh rates aren't really on the table, but it doesn't seem happy with 1280x768. In mepis this worked (just changing the values) but for some reason ubuntu doesn't like it.

Might have to go into mepis again and get the refresh rates.

---

### Post by mlind on 2006-08-19
> **joshier said:**
> I know, brilliant :roll: 

It's a LCD screen so refresh rates aren't really on the table, but it doesn't seem happy with 1280x768. In mepis this worked (just changing the values) but for some reason ubuntu doesn't like it.

Might have to go into mepis again and get the refresh rates.

You've requested this display mode on xorg.conf ?
Not sure if it's a valid mode, but 1280x1024 should work.

---

### Post by joshier on 2006-08-19
> **mlind said:**
> You've requested this display mode on xorg.conf ?
Not sure if it's a valid mode, but 1280x1024 should work.


Yeah that's what I thought, and did do, but sadly it really screwed the display up.

---

### Post by mlind on 2006-08-19
> **joshier said:**
> Yeah that's what I thought, and did do, but sadly it really screwed the display up.

Maybe you should post xorg.conf and specs of your gfx card and monitor.

---

### Post by joshier on 2006-08-20
> **mlind said:**
> Maybe you should post xorg.conf and specs of your gfx card and monitor.

S3 graphics UniChrome Pro IGP
14" widescreen Ultrabright™ XGA TFT

---

### Post by mlind on 2006-08-20
> **joshier said:**
> S3 graphics UniChrome Pro IGP
14" widescreen Ultrabright™ XGA TFT

And xorg.conf ?

---

### Post by joshier on 2006-08-21
> **mlind said:**
> And xorg.conf ?

Fixed the screen resolution now.

I followed these instructions;
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)



> Before You Start

    *

      You must have administrative privileges to install packages.
    *

      See Installing Software for instructions about how to install software in Ubuntu.
    *

      Make sure you have enabled the Universe and Multiverse repositories.
      See Managing Repositories in Ubuntu or Kubuntu for help with this.


openChrome 2D driver compilation

    *

      Install needed packages
          o

            Install the following packages to successfully compile openChrome:
          o

            subversion
          o

            build-essential
          o

            automake1.9
          o

            libtool
          o

            pkg-config
          o

            xserver-xorg-dev
          o

            libxvmc-dev
          o

            x11proto-gl-dev
          o

            libglu1-mesa-dev
          o

            x11proto-core-dev
          o

            libxvmc-dev
          o

            xserver-xorg-dev
          o

            x11proto-gl-dev
          o

            libgl1-mesa-dev
          o

            cvs
    *

      Start the real fun
          o

            We will now compile the openChrome 2D driver
          o

            Create a new directory

            mkdir openchrome

          o

            Change into the newly created directory

            cd openchrome

          o

            Get the openChrome sourcecode

            svn co [http://svn.openchrome.org/svn/trunk](http://svn.openchrome.org/svn/trunk)

          o

            Change into the sourcecode directory

            cd trunk

          o

            Run autogen.sh with the prefix option so that the driver is being installed in the correct directory

            ./autogen.sh --prefix=/usr/

          o

            Compile openChrome

            make

          o

            Install openChrome

            sudo make install

    *

      Change the XOrg driver to via

      Now we have to edit /etc/X11/xorg.conf and change the Device Driver to via

      sudo gedit /etc/X11/xorg.conf

      Go to

      Section "Device"

      and change

      Driver          "blahblah"

      to

      Driver          "via"

      Save the file.

      Finally, we have to restart our Xorg server by pressing Ctrl-Alt-Backspace. If Xorg does not start anymore, log in in a console and change the Driver in the Device section back with an editor like nano.


---

