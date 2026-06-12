---
title: "Ubuntu slower after activating Nvidia drivers"
date: 2011-10-21
forum: Desktop Environments
---

### Post by subehsharma on 2011-10-21
I'm on ubuntu 11.10 with Gnome 3. I've recently activated Nvidia drivers so that the graphical tasks can be transferred to the Nvidia card thereby increasing the speed but to my dismay, what happened was the opposite.

I see delays in almost everything i.e. from scrolling on a webpage to opening apps, the speed has reduced. I need to disable the Nvidia driver, can anybody tell me how i can do that and use the built-in Nouveau driver?

This delay is seen in both Gnome 3 and Unity.

---

### Post by lovinglinux on 2011-10-21
> **subehsharma said:**
> I'm on ubuntu 11.10 with Gnome 3. I've recently activated Nvidia drivers so that the graphical tasks can be transferred to the Nvidia card thereby increasing the speed but to my dismay, what happened was the opposite.

I see delays in almost everything i.e. from scrolling on a webpage to opening apps, the speed has reduced. I need to disable the Nvidia driver, can anybody tell me how i can do that and use the built-in Nouveau driver?

This delay is seen in both Gnome 3 and Unity.

Try the 173 driver. At least for me it has much better performance when scrolling Firefox pages.

---

### Post by subehsharma on 2011-10-21
ok..going to try it now. Lets hope it doesn't screw up anything ;-)

---

### Post by subehsharma on 2011-10-21
it was a disaster!!! pls don't recommend 173 to anyone. Whole system came down to a crawl. I'd to keep power button pressed to shut down Ubuntu. Now i'm back to the "recommend" driver.

---

### Post by teseglet on 2011-10-21
I used to install the Nvidia driver right away because the Nouveau driver always left relics with my icons and was a bit flaky.  I tried Fedora 16 Beta recently and was stuck with the Nouveau driver because I could not install the Nvidia driver.  To my surprise it performed flawlessly.  Now I loaded Ubuntu 11.10 Gnome-Shell and installed the Nvidia driver with the initial boot without thinking and agree it caused great lag, particularly with flash video.  So I removed the driver and installed the Nouveau firmware from the Software Center (not sure that was needed, as the Nouveau driver software was already checked as installed), rebooted, and my system is quite spunky now and none the worse for wear using the current Nouveau driver.  Particularly if you have slower system, Nouveau seems to have eclipsed the Nvidia driver performance, at least for me.

---

### Post by teseglet on 2011-10-21
I just added more speed by removing compiz and installing mutter.

---

### Post by lovinglinux on 2011-10-21
> **subehsharma said:**
> it was a disaster!!! pls don't recommend 173 to anyone. Whole system came down to a crawl. I'd to keep power button pressed to shut down Ubuntu. Now i'm back to the "recommend" driver.

Which card do you have?

---

### Post by randywilharm on 2011-10-21
Disregard recommended driver and go straght to Nvidia source:

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

With all respect to Ubuntu,
"Recommended" drivers are usually 1 or 2 steps behind the current
Nvidia driver...Nvidia may have even fixed your problem without
you knowing it. If not, you're still in a better position to
tackle a problem with the current driver.

Nvidia drivers must be installed by user logged on as root.

You will have to stop Gnome Desktop Manager (gdm) which is now
called lightdm in 11.10. [COLOR="Red"]IN THE TERMINAL, I mean.[/COLOR]

---

### Post by critin on 2011-10-21
<<[I]Disregard recommended driver and go straght to Nvidia source:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)[/I]>>

Randy,

The link scan only works on Windows. Do you know of one for linux?  I've been searching for the longest.

critin

---

### Post by Rodney9 on 2011-10-22
Just choose your Operating System - Linux 64bit or 32bit from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by subehsharma on 2011-10-22
> **teseglet said:**
> I used to install the Nvidia driver right away because the Nouveau driver always left relics with my icons and was a bit flaky.  I tried Fedora 16 Beta recently and was stuck with the Nouveau driver because I could not install the Nvidia driver.  To my surprise it performed flawlessly.  Now I loaded Ubuntu 11.10 Gnome-Shell and installed the Nvidia driver with the initial boot without thinking and agree it caused great lag, particularly with flash video.  So I removed the driver and installed the Nouveau firmware from the Software Center (not sure that was needed, as the Nouveau driver software was already checked as installed), rebooted, and my system is quite spunky now and none the worse for wear using the current Nouveau driver.  Particularly if you have slower system, Nouveau seems to have eclipsed the Nvidia driver performance, at least for me.

Great! Thats what even i am expecting. Cud u be a bit specific as to how you made this switch? I.e. Did u just remove the nvidia driver from the nvidia app screen or did aomething on the command line? Waiting to hear from u on this.

---

### Post by subehsharma on 2011-10-22
> **randywilharm said:**
> Disregard recommended driver and go straght to Nvidia source:

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

With all respect to Ubuntu,
"Recommended" drivers are usually 1 or 2 steps behind the current
Nvidia driver...Nvidia may have even fixed your problem without
you knowing it. If not, you're still in a better position to
tackle a problem with the current driver.

Nvidia drivers must be installed by user logged on as root.

You will have to stop Gnome Desktop Manager (gdm) which is now
called lightdm in 11.10. [COLOR="Red"]IN THE TERMINAL, I mean.[/COLOR]


Thanks man. I will try it soon and see how it performs. So when i ibstall the driver from yhe site, do u first need to remove the one already installed?

---

### Post by randywilharm on 2011-10-22
No, NVIDIA will do that for you...you should see a message box
informing you of this.

---

### Post by subehsharma on 2011-10-24
> **randywilharm said:**
> No, NVIDIA will do that for you...you should see a message box
informing you of this.

Thanks, I tried doing that but i'm getting this message: "You appear to be running an X server; please exit X before        installing."

I tried sudo /etc/init.d/gdm stop but it gives an error: 
"sudo: /etc/init.d/gdm: command not found"

Any idea how to stop X server?

---

### Post by SyntheticShield on 2011-10-26
I believe the command is sudo service lightdm stop.

---

### Post by arisp on 2011-10-26
If you' re feeling adventurous, you can add the x-org edgers ppa, which has the latest nvidia drivers. 
[http://www.ubuntuupdates.org/ppas/87](http://www.ubuntuupdates.org/ppas/87)
Works like a charm on mine.

---

### Post by typhoon_tip on 2011-10-26
Sometimes to a simple problem (slugginesh) there is indeed a simple solution :)

Have the same problems with any kind of accelerated driver (ATI,NVIDIA... slugginesh of response, ugly behaviour and frame rate), this is because by default, before installing the driver, compiz use a setting called SYNC TO VBLANK to avoid tearing the screen when moving stuff around (namely windows).

After you install NVIDIA, this setting is ON by default in the control panel of the card, and compiz is on too... so the result is that you have double random vblanks that are screwing everything up.

Simply try the old method: open compiz, openGL plugin, deselect sync to Vblank. Also, check composite, and bump your frame rate up to the same frequency of the screen or above "in multiples" (I have 60 Hz, I set to 90 fps, better use multiples of the base numbers !), lighting effect also active, texture set to Best.

After you set everything, logout and login again (sometimes even restart is necessary to see the real, super-milky-smooth effect).

EDIT: I forgot, deselect also automatically detect refresh rate, sometimes it just mess things up.

---

### Post by proxy.qtz on 2011-10-26
Uh, the Nouveau drivers are terrible. I suggest using nvidia-current.

---

