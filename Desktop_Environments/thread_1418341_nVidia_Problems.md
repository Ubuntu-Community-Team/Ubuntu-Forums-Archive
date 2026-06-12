---
title: "nVidia Problems"
date: 2010-02-28
forum: Desktop Environments
---

### Post by Autumn Night on 2010-02-28
Good afternoon everyone! I am new here, and I am semi-new to Ubuntu. My brother helped me install v9.10 last night and I am having one main problem. I have been searching forums and have found similar problems/solutions to mine, but nothing exactly the same. 
I was stuck, like many others on a resolution of 800x600. I found a fix for it, but then undid it so that I could run my nVidia drivers, as I thought this would be better. So, I did the changes, restarted, and then went into my drivers and turned on the recommended nVidia driver (I think it was 185 or something like that). Well, I restarted yet again, got to the login screen, and then my monitor said something to the effect of "Cannot run video mode. Recommended resolution 1280x1040 60Hz" At this point all I can do is turn off my tower, start it up and run Windows. 
Now, I could try running it in recovery mode, if I knew what to do to make it better. Please let me know if I need to post any other information to help get solutions to this problem. I miss my Ubuntu already!

---

### Post by manoriax on 2010-02-28
My Philips monitor sometimes gives the same error message. The cause for this is the wrong refresh rate set in the system - I guess you will have to change the rate to fix this. But unfortunately I don't know exactly how to do this.

---

### Post by warp99 on 2010-02-28
First make sure you have the nvidia-settings manager installed:

```
sudo apt-get install nvidia-settings
```

Once you have that installed logout and back in again. On the menu go to System Tools > Nvidia X Sever Settings. Open the dialog make "X Server Display Configuration". In the right lower corner you'll see a box marked "Resolution". Choose the resolution that was detected/available and press "Apply" then "Quit". Your settings will be saved in the file ~/.nvidia-settings-rc and reloaded the next time you login.

---

### Post by Autumn Night on 2010-02-28
Thanks, I will try this and let you know.

---

### Post by warp99 on 2010-02-28
If for some reason the icon is not there just press alt-f2 and type in the run dialog "nvidia-settings".

Edit:
The icon is located under System > Administration. I have three different desktops and the nvidia settings icon is located in various locations on each one. Sorry for the confusion.

---

### Post by Autumn Night on 2010-02-28
OK, that might help. I went into recovery mode and typed in the sudo apt-get ... and it said nothing was updated, so I restarted and looked for a menu or settings box on the login screen, and there was nothing. I am in the older version that for some reason Ubuntu keeps, and it says my nVidia driver is enabled but not in use. I will try what you said and see if that helps at all.

---

### Post by Autumn Night on 2010-02-28
Well, I am unable to login to even get to my settings, and I am not sure how to do it through recovery mode. I guess I will have to do some more research.

---

### Post by warp99 on 2010-02-28
You can make a new xorg.conf that will load the nvidia modules by running the following command:

```
sudo nvidia-xconfig
```

There maybe some minor errors with input devices, but ignore them because Ubuntu uses udev instead of input config from xorg.conf. Logout and then login and the nvidia driver should be active. Just check by running nvidia-settings. If it's working then nvidia is loaded.

Edit: You can do this though recovery mode by choosing a root console at the menu.

---

### Post by warp99 on 2010-02-28
If you're at the login screen you don't need to go into recovery mode. Just press ctrl-alt-f1 to get to a console. Login at the prompt, then run "sudo nvidia-xconfig". Press ctrl-alt-f7 to go back to the login, then reboot to reload xserver.

Edit: You can skip pressing crtl-alt-f7 and instead type "sudo reboot" at the prompt if you want.

---

### Post by RJARRRPCGP on 2010-02-28
> **manoriax said:**
> My Philips monitor sometimes gives the same error message. The cause for this is the wrong refresh rate set in the system - I guess you will have to change the rate to fix this. But unfortunately I don't know exactly how to do this.

It likely means that X decided to set the resolution to 1600x1200 or a non-standard res! IIRC, Debian Lenny has this problem with my Acer X193Wb. The Acer X193Wb would display "Input not supported" and all I could do was hard shut down! 

I was required to hook up a CRT to use Debian Lenny, IIRC.

X.Org has a problem where it decides to override the max supported resolution information, with some monitors.

I don't have this issue with Windows. Windows will NEVER assume 1600x1200 or a non-standard res.

Because with my CRT plugged in, I saw the res at 1600x1200, IIRC. 

That suspiciously looks like X assumed 1600x1200 was supported, IIRC.

---

### Post by Autumn Night on 2010-02-28
Well, thanks for all of your help. Nothing is working so far and I finally have nVidia turned off so that I can at least login, even if it is 800x600. I will research and try more things when I have the time. I have lots of homework and an exam to prepare for... I have a lot to learn about this... Thanks again for trying to help!

---

### Post by Autumn Night on 2010-02-28
Hmmm, well I have an older monitor, so maybe I should try it. But it is not a crt either. I will just have to bide my time, and sleep on it. It is weird that it would assume an outrageous resolution like that, and would explain why my monitor won't even try to display it. I tried going in and changing the x-config settings, but i either didn't do something right, or it didn't help, because the same thing happened, and I had to erase the changes and disable nVIDIA. Geeze...

---

