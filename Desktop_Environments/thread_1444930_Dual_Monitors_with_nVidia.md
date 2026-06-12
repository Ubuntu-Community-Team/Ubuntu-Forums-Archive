---
title: "Dual Monitors with nVidia"
date: 2010-04-01
forum: Desktop Environments
---

### Post by Forgotten2191 on 2010-04-01
I am having several issues setting up dual monitors.  I'm using the NVIDIA X Server Settings interface to configure everything.

The interface recognizes my second monitor as a CRT.  It's a 19" Philips LCD, and at one point, I got it to understand that.  Then I had GUI issues and had to reset the configuration and can't seem to remember how to apply the changes again.  

Saving the settings directly from the interface doesn't work.  I have to manually change the xorg.conf file and restart to see anything on the second monitor.  When there is a change made, the monitor's set in low resolution, I'm assuming 640x480.  This also messes with the appearance of my primary monitor - irritating distortions and such.

So currently, I have a strange xorg.conf file that I don't remember how to reset and an LCD that's pretending to be a CRT.  I've looked through other posts, but none of them can help me completely.

I'm using Ubuntu 9.10 and my graphics card is an nVidia GeForce 8500 GT.

Can anyone lend me a hand?  Thanks.

---

### Post by BobVila on 2010-04-02
> **Forgotten2191 said:**
> I am having several issues setting up dual monitors.  I'm using the NVIDIA X Server Settings interface to configure everything.

The interface recognizes my second monitor as a CRT.  It's a 19" Philips LCD, and at one point, I got it to understand that.  Then I had GUI issues and had to reset the configuration and can't seem to remember how to apply the changes again.  

Saving the settings directly from the interface doesn't work.  I have to manually change the xorg.conf file and restart to see anything on the second monitor.  When there is a change made, the monitor's set in low resolution, I'm assuming 640x480.  This also messes with the appearance of my primary monitor - irritating distortions and such.

So currently, I have a strange xorg.conf file that I don't remember how to reset and an LCD that's pretending to be a CRT.  I've looked through other posts, but none of them can help me completely.

I'm using Ubuntu 9.10 and my graphics card is an nVidia GeForce 8500 GT.

Can anyone lend me a hand?  Thanks.

make a backup of your xorg.conf and then try ```
sudo nvidia-settings
```
The app won't write to your xorg.conf file if invoked from the gui due to lack of permissions. It'll save you from mucking about with the conf file, and you'll have a failsafe backup in case you totally hose the x server.

---

### Post by Forgotten2191 on 2010-04-02
Thanks, but I already tried messing around with those settings.  I know I can edit the configuration there and copy the preview code, then paste it in the xorg.conf file, but that doesn't really help.  I can't change the resolution of the second monitor from there, and it still messes with the settings of the primary monitor.

---

### Post by quimkaos on 2010-04-10
will this problem ever get solved?
i just rebuild my system thinking this was long ago solved, not backing up my xorg.conf and now i have to figure it out all over again...

the nvidia-settings dialog won't write to xorg.conf! even using sudo! it will crash the aplication saying that is unable to save the file... then exits...
anyone knows how to solve this? and i mean using nvidia-config?
if not can anyone get me an example of a xorg.conf file using dual monitor?

btw this is corrected in 10.4 beta... why not in 9.04?

---

### Post by quimkaos on 2010-04-10
And this is the simpliest way i configured this:

1 - open a console and rename xorg.conf

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bakup
```2 - open nvidia-settings using sudo

```
sudo nvidia-settings
```3 - now you can save to X configuration file. it will open an dialog asking were you want to save the configuration. just put /etc/X11/xorg.conf

this way you can allways reconfigure your settings using nvidia-settings!
note that the xserver folder is X11 not x11...

**Hope this helps anyone having trouble using nvidia-settings**

---

### Post by northking on 2010-04-18
I'm new to Linux, so forgive me if I sate the obvious.

I have the same problem with the xorg.conf file. NVIDIA X Server Settings returns "Failed to parse existing X config file '/etc/X11/xorg.conf'." I am guessing this is a permissions problem, that is, nvidia-settings doesn't have write permission for that file or one of the folders it's contained in. I also have tried various hacks. Sigh.

I am using a GeForce 9600 GSO with two DVI ports, and it works fine with two flat panel monitors (one is HD). Are you using one or two video cards? If two, you may need a different driver for the card connected to the offending monitor.
-Dave

---

### Post by northking on 2010-04-18
Ooooooops! For some reason my browser did not display the other replies you received. The last reply fixed my xorg.conf problem. Thanks! (it was permissions, I think).

I apologize for jumping the thread. Hope you get your monitor problem resolved.

-Dave

---

