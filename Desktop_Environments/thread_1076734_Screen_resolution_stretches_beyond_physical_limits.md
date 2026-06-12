---
title: "Screen resolution stretches beyond physical limits!"
date: 2009-02-21
forum: Desktop Environments
---

### Post by linuxisevolution on 2009-02-21
I was trying to unclutter my desktop when I saw an extra option in screen resolution settings to enlarge my screen area. I selected this and nothing happened. So I went in Applications >> Other >> screen and graphics and then selected my monitor and then the new resolution was activated. I restarted X and logged back in to see my Gnome Panel does not reach the full screen and neither do my application windows. What do I change to be able to see my full desktop?

---

### Post by lukjad on 2009-02-21
There is a way. Go to your home folder and press Ctrl+H. Then rename the .comfig folder to something like [DOT]config. Reboot your system.

---

### Post by linuxisevolution on 2009-02-21
> **lukjad007 said:**
> There is a way. Go to your home folder and press Ctrl+H. Then rename the .comfig folder to something like [DOT]config. Reboot your system.

That did not fix it. Sorry...

---

### Post by lukjad on 2009-02-21
Hmmm... And you can't reset it with System->Preferences->Screen Resolution?

---

### Post by linuxisevolution on 2009-02-21
> **lukjad007 said:**
> Hmmm... And you can't reset it with System->Preferences->Screen Resolution?

Yes. But I need a larger screen resolution :(

---

### Post by linuxisevolution on 2009-02-21
How do I enlarge my screen resolution without encountering this problem? Thanks for any help!

---

### Post by lukjad on 2009-02-21
Hmm... Sorry. I'll see if I can find someone who can help you more.

---

### Post by jgoguen on 2009-02-21
What type of video card are you using?  nVidia, ATi, Intel...?

---

### Post by linuxisevolution on 2009-02-21
> **jgoguen said:**
> What type of video card are you using?  nVidia, ATi, Intel...?

I'm using Nvidia Geforce 8600gt. Thanks for all your help! ( I WILL get this to work lol )

---

### Post by jgoguen on 2009-02-21
OK, try this out:

[LIST]
[*]Press Alt+F2
[*]In the box that appears, enter the command: **nvidia-settings**
[*]If this command is not found, go to System -> Administration -> Synaptic Package Manager, search for **nvidia-settings**, install it, and start from step 1 again.
[*]Click the **X Server Display Configuration** entry in the list on the left side
[*]Under Resolution choose **Auto** (or if this is already chosen, choose your desired resolution)
[*]Click the **Advanced** button.  The blue-ish box near the top of the window gives you a resolution.  The text in the **Panning** box must match the resolution in that blue box (which prevents what you're seeing)
[*]Click the **Apply** button, don't be surprised if the screen flickers for a bit, and then it should be fine.  If it isn't, you can say that you don't want to keep the changes (and let us know what you tried and that it didn't work!) or if it's so bad that you can't see anything just wait about 30 seconds and it'll revert on its own.  If the changes are good, be sure you say you want to keep them
[/LIST]

Don't restart or log out too quickly though, if this works it's not saved.  Come back and let us know how this works.  If it's what you want, leave the nVidia settings window open and we'll let you know how to save this so it always works.

---

### Post by linuxisevolution on 2009-02-21
> **jgoguen said:**
> OK, try this out:

[LIST]
[*]Press Alt+F2
[*]In the box that appears, enter the command: **nvidia-settings**
[*]If this command is not found, go to System -> Administration -> Synaptic Package Manager, search for **nvidia-settings**, install it, and start from step 1 again.
[*]Click the **X Server Display Configuration** entry in the list on the left side
[*]Under Resolution choose **Auto** (or if this is already chosen, choose your desired resolution)
[*]Click the **Advanced** button.  The blue-ish box near the top of the window gives you a resolution.  The text in the **Panning** box must match the resolution in that blue box (which prevents what you're seeing)
[*]Click the **Apply** button, don't be surprised if the screen flickers for a bit, and then it should be fine.  If it isn't, you can say that you don't want to keep the changes (and let us know what you tried and that it didn't work!) or if it's so bad that you can't see anything just wait about 30 seconds and it'll revert on its own.  If the changes are good, be sure you say you want to keep them
[/LIST]

Don't restart or log out too quickly though, if this works it's not saved.  Come back and let us know how this works.  If it's what you want, leave the nVidia settings window open and we'll let you know how to save this so it always works.

It fixed the problem, but I still can't set my resolution to the desired 1400x1050. This is the Gateway Ev700. Is it possible my monitor is too old?

---

### Post by jgoguen on 2009-02-21
OK, well first let's save our progress so it's not all lost, then we'll look at why you can't set your resolution to what you want.

In the same place you changed all those settings, click the **Save to X Configuration File** button.  Uncheck the **Merge with existing file** box, then enter **/home/username/xorg.conf** in the text box, replacing *username* with your username.  Now, open a terminal (Applications -> Accessories -> Terminal) and move it into place.  Run these commands, one after the other, entering your password when prompted:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_orig
sudo cp xorg.conf /etc/X11/xorg.conf
```
If you're asked if you want to overwrite existing files, say yes.  This will make sure that the current settings are what get applied next time you start your computer.

---

### Post by jgoguen on 2009-02-21
Now, on to setting that resolution for you.

When you were choosing the resolution from the list in the nvidia-settings window, was 1400x1050 an available option?  Can you post the first few resolutions available to you under the **Auto** option?

If 1400x1050 is available, can you try choosing that one and clicking **Apply** and see if that works?  If it doesn't, let us know what the error message is.

---

### Post by linuxisevolution on 2009-02-21
> **jgoguen said:**
> Now, on to setting that resolution for you.

When you were choosing the resolution from the list in the nvidia-settings window, was 1400x1050 an available option?  Can you post the first few resolutions available to you under the **Auto** option?

If 1400x1050 is available, can you try choosing that one and clicking **Apply** and see if that works?  If it doesn't, let us know what the error message is.

That is not one of the available ones listed, but it is listed under System >> Prefrences >> Screen Resolution. :(

---

### Post by jgoguen on 2009-02-21
Can you post a few of the resolutions that are available close to it?

This may not mean much to you, but I'm putting it here mostly for my own reference later: you need a resolution that gives you a 1.(3):1 ratio.

---

### Post by linuxisevolution on 2009-02-21
> **jgoguen said:**
> Can you post a few of the resolutions that are available close to it?

This may not mean much to you, but I'm putting it here mostly for my own reference later: you need a resolution that gives you a 1.(3):1 ratio.

The resolution that is working is the highest in the list 1280X1024. I can't see the list because I'm on my laptop and my mother asked me to go downstairs to wait for the pizza. I can't ssh into my desktop either because I have the firewall on. I'll be back in a few minutes :)

EDIT: I'm back. Xrandr gives the same results so I will just copy and paste from terminal :)

 1280x1024      50.0*    89.0  
   1280x960       51.0     68.0  
   1152x864       52.0  
   1024x768       53.0     54.0     55.0     56.0     57.0     72.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0  
   640x480        64.0     65.0     66.0     67.0     77.0     78.0  
   1280x800       69.0  
   1280x768       70.0  
   1152x768       71.0  
   800x512        73.0  
   720x450        74.0  
   720x400        75.0  
   700x525        76.0  
   640x400        79.0  
   640x350        80.0  
   576x384        81.0  
   512x384        82.0     83.0     84.0  
   400x300        85.0  
   320x240        86.0     87.0  
   320x175        88.0  
   1400x1050      50.0     89.0     90.0

---

### Post by jgoguen on 2009-02-21
If 1280x1024 is the highest on the list, that's the highest resolution the nvidia driver thinks the monitor can support.  Let's make sure your GNOME panel is set to make use of the full screen area.  Right-click on an empty area of the panel and choose **Properties**.  In the settings window, make sure the **Expand** item is checked.

---

### Post by linuxisevolution on 2009-02-21
> **jgoguen said:**
> If 1280x1024 is the highest on the list, that's the highest resolution the nvidia driver thinks the monitor can support.  Let's make sure your GNOME panel is set to make use of the full screen area.  Right-click on an empty area of the panel and choose **Properties**.  In the settings window, make sure the **Expand** item is checked.

Expand is checked. Thanks for your consistency on this :)

---

### Post by jgoguen on 2009-02-21
I'm running out of ideas :(

One last idea for now.  Open a terminal again (Applications -> Accessories -> Terminal) and enter this command:```
xrandr
```
Paste the output of that here.  It'll tell us some information about your available resolutions.  It's Shift+Ctrl+C to copy from Terminal.

---

### Post by linuxisevolution on 2009-02-21
> **jgoguen said:**
> I'm running out of ideas :(

One last idea for now.  Open a terminal again (Applications -> Accessories -> Terminal) and enter this command:```
xrandr
```
Paste the output of that here.  It'll tell us some information about your available resolutions.  It's Shift+Ctrl+C to copy from Terminal.

I just did that a few posts ago.:D post 16

---

### Post by jgoguen on 2009-02-21
Sorry, completely missed that :)

According to xrandr 1400x1050 is supported.  But it's at the bottom of the list here, which makes me wonder if it's also at the bottom in nvidia-settings.  Open nvidia-settings again (press Alt+F2, enter **nvidia-settings**) and go back to **X Server Display Configuration**.  Check in the Resolution list, this time look at all the resolutions all the way down to the very bottom of the list, see if 1400x1050 is there.  If it is, choose it and click Apply.

---

### Post by linuxisevolution on 2009-02-21
> **jgoguen said:**
> Sorry, completely missed that :)

According to xrandr 1400x1050 is supported.  But it's at the bottom of the list here, which makes me wonder if it's also at the bottom in nvidia-settings.  Open nvidia-settings again (press Alt+F2, enter **nvidia-settings**) and go back to **X Server Display Configuration**.  Check in the Resolution list, this time look at all the resolutions all the way down to the very bottom of the list, see if 1400x1050 is there.  If it is, choose it and click Apply.

It's not there. I already thought of that :( Thanks for your help, but I think I finally have an excuse to ask my parents or a new monitor, or at least for a job :).

---

