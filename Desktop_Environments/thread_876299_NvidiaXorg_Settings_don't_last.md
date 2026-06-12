---
title: "Nvidia/Xorg Settings don't last"
date: 2008-07-31
forum: Desktop Environments
---

### Post by mythik on 2008-07-31
So in the past two days I've had a lot of issues with my screen resolution and being able to use the closed source nvidia drivers.  I'm not sure what happened why it broke, but for awhile I couldn't get past 800x600 resolution.  Long story short, using envyng allowed me to use the nvidia driver.

So now, using nvidia-settings I can set my resolution and all that jazz.  Unfortunately for me, it only lasts every session and I have to redo it each time I log in.  Any thoughts?

Attached is my xorg.conf

---

### Post by tamoneya on 2008-07-31
nvidia-settings isnt able to save your settings unless you call it with gksudo.  Hit alt-F2 and type```
gksudo nvidia-settings
```

---

### Post by Shmifty on 2008-07-31
Run > sudo dpkg-reconfigure xserver-xorg on a new session, fill everything in and see if that helps.

---

### Post by mythik on 2008-07-31
> **tamoneya said:**
> nvidia-settings isnt able to save your settings unless you call it with gksudo.  Hit alt-F2 and type```
gksudo nvidia-settings
```

I've done that and I've confirmed that the xorg.conf modified date is updated, still no change.

---

### Post by Shmifty on 2008-07-31
> sudo dpkg-reconfigure xserver-xorg

Then restart X (ctrl + alt + backspace).

---

### Post by mythik on 2008-07-31
> **Shmifty said:**
> Then restart X (ctrl + alt + backspace).

Seemingly only asks about keyboard layout and options.

What it does do, however, is bring me back to the correct resolution, unfortuantely,it's because I'm now using the nv driver.  So things like glxgears and nvidia-settings don't work.

Like I said, I had a lot of issues with X recently =(  Oh well.

---

### Post by Shmifty on 2008-07-31
Do you even have a driver installed? It should ask you what resolution you want to run at, what model your card is and what driver you'd like to use (nvidia should be one of the options).

---

### Post by mythik on 2008-07-31
> **Shmifty said:**
> Do you even have a driver installed? It should ask you what resolution you want to run at, what model your card is and what driver you'd like to use (nvidia should be one of the options).

It's installed.  I couldn't get it to register by installed nvidia-glx-new though only by using envyng (new frontend for envy scripts)

---

### Post by Shmifty on 2008-07-31
Retry installing the nvidia-glx-new package, run the dkpg-reconfigure xserver-xorg and then restart X.

I'm not familiar with envyng, but this is how installed my card (8800GT).

---

### Post by mythik on 2008-07-31
So I guess the real issue is that I'm having trouble installing the nvidia driver.  More importantly, I'd like to know what happened where it got messed up.  I know 2.6.24-20 came out around the same time kde 4.1 did - maybe that was too much of an update?

I've tried purging nvidia-glx-new and reinstalling it, but it didn't work.  Are there other packages I have to worry about?

---

### Post by Shmifty on 2008-07-31
How are you trying to install it? If you use apt-get or aptitude it should tell you what's failing on the install and that should give you a clue to what's wrong.

---

### Post by mythik on 2008-07-31
> **Shmifty said:**
> How are you trying to install it? If you use apt-get or aptitude it should tell you what's failing on the install and that should give you a clue to what's wrong.

normal stuff "sudo apt-get install nvidia-glx-new" - It doesn't error out, it just doesn't do anything...that's why I said it failed.

---

### Post by Shmifty on 2008-07-31
Go to your hardware drivers. It should say NVIDIA accelerated graphics driver (latest cards) and it should be enabled and in use. If it's not you have a problem.

---

### Post by mythik on 2008-07-31
> **Shmifty said:**
> Go to your hardware drivers. It should say NVIDIA accelerated graphics driver (latest cards) and it should be enabled and in use. If it's not you have a problem.


I don't have that now - and that's due to using envy (and documented on ubuntu wiki).

However when it DID show up, I could still only use the nv driver - having it "in use" didn't really make it actually in use.  Odd eh?

---

### Post by Shmifty on 2008-07-31
Can you uninstall envyng and it's associated stuff and try installing it from scratch?

---

### Post by mythik on 2008-07-31
> **Shmifty said:**
> Can you uninstall envyng and it's associated stuff and try installing it from scratch?

Did that, even reinstalled the headers and new kernel stuff.

Reinstalled nvidia-glx-new.  Started up the hardware drivers, and the driver is not listed under components.

---

### Post by Lathilde on 2008-08-01
Can I assume you are basically referring to driver settings such as OpenGL accelleration and all that schnazz? If so, try this.

Download the latest binary driver from Nvidia's website. Sure, it ain't open-source, but if you want your hardware to work at the max, which you -paid- for (I know I do) then use this. The instructions for installation are very simple, and are given on Nvidia's website.

Once you've done that, and rebooted, open nvidia-settings using a root terminal. Tweak everything to your desired settings, optimising OpenGL, gamma and whatever. Then open Nautilus, and ensure hidden files are visible. Go to your Home directory. Do you notice the .nvidia-settings-rc file? I don't know the exact spelling of the file (I'm not using Linux now, sadly), but this little file stores your settings from the nvidia-settings program. 

For some silly X-server related reason, these settings are wiped and restored to default every time X is started/restarted. This leads to the problems you are facing now. So, with your nvidia settings now tweaked, copy this file and place it somewhere else, let's say, in /opt. Then, remove the file from your home directory, and create a symlink to that file which now resides in /opt, and put it in your home directory. Name the symlink '.nvidia-settings.rc' or whatever it was called originally (again, I can't remember exactly).

And that's it. Restart X, and your settings from your last session will remain. If you ever wish to change it, remove the symlink, restart X, tweak nvidia-settings and repeat the process.

Hope this helps!

---

