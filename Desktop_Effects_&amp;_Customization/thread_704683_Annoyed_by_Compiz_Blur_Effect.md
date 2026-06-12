---
title: "Annoyed by Compiz Blur Effect"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by TornadoWarning40422 on 2008-02-22
Countless solutions. None of them worked. I have ubuntu gutsy with the current (non-git) release of compiz. I know it's not the hardware. But for some reason, everything in compiz except for the blur plugin works. my graphics card supports direct rendering. when i enable the blur plugin, nothing happens. no lag at all, everything runs smoothly, and still no-go. what up?! in emerald i have the settings config'd right. and in beryl, the blur plugin worked fine. hmph. 

if i could get beryl back. i would. which brings a question to mind. can i get beryl back? not compiz. just beryl. old fashioned beryl that's on feisty.

Thanks, The Dude Who Is Having Problems With His Compiz Blur Plugin

---

### Post by mgmiller on 2008-02-22
Hi, I noticed the same thing in my Gutsy install.  

I found the blur settings only work with emerald themes, not metacity themes as modified by compiz.

So, you need to install the emerald packages:
Do a search in Synaptic for emerald and install emerald and emeraldengine0 
or type the code:
```
sudo apt-get install emerald
sudo apt-get install emeraldengine0
```

after you have that, you can go to gnomelook.org to get an emerald theme you like and import it into the emerald theme manager.  System>Preferences>Emerald Theme Manager.

From the Themes tab click the import button and navigate to the emerald theme you want to import.

Next, change window managers so you are using Emerald.
Open the command window with Alt/F2 and type the command:
```
emerald --replace
```

Finally, follow these instructions to make sure it all works:

```
First turn on blur effects:
in Compiz Config Settings Manager (Advanced Desktop Effects Settings)
Turn on the "Blur Windows" effect.
In the General tab set the Blur Filter to Mipmap for maximum blur or gaussian for less blur.

Finally, enable it for emerald themes:
in emerald theme manager
go to emerald settings tab 
go to compiz decoration blur type 
select either "title bar only" to just blur behind the title bar
or "all decorations" to make everything behind the window border also blur.

```

After all this, you will have emerald themes and a nice blurry border.

I hope all this stuff gets integrated into Hardy as a metapackage along with an easier GUI way to change window managers.

Have fun with yoiur blurry goodness.  :popcorn:

---

### Post by TornadoWarning40422 on 2008-02-22
still a no go. maybe I should update to 6.2git from 6.0...

and i already had emerald config'd with all the blur stuff.

---

### Post by TornadoWarning40422 on 2008-02-22
:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (blur) - Warn: No stencil buffer. Region based blur disabled

here i am, updated, and still nothing i think the last line has something to do with it. i don't have an nVidia card. it's an intel 82845G series.

---

### Post by mgmiller on 2008-02-23
I suspect your video card/driver may be the problem.  I am using Nvidia 7800 GT with the nvidia-new driver from the repos, 100.14.19.

---

### Post by fracturedmorals on 2008-02-23
> **TornadoWarning40422 said:**
> Countless solutions. None of them worked. I have ubuntu gutsy with the current (non-git) release of compiz. I know it's not the hardware. But for some reason, everything in compiz except for the blur plugin works. my graphics card supports direct rendering. when i enable the blur plugin, nothing happens. no lag at all, everything runs smoothly, and still no-go. what up?! in emerald i have the settings config'd right. and in beryl, the blur plugin worked fine. hmph. 

if i could get beryl back. i would. which brings a question to mind. can i get beryl back? not compiz. just beryl. old fashioned beryl that's on feisty.

Thanks, The Dude Who Is Having Problems With His Compiz Blur Plugin

Hi there "Dude who is Having Problems With His Compiz Blur Plugin".

What video card are you running. It may support DRI (Which is nice for AIGLX), but does it support pixel shaders?

I love the blur plugin, but I wasn't able to get the "Real" blur plugin supported on beryl comfortably (back in the day) until I at least got an nvidia geforce 6xxx.

I personally think that compiz fusion should bring back the nonFBO blur.....who here agrees?

---

### Post by TornadoWarning40422 on 2008-02-23
> What video card are you running. It may support DRI (Which is nice for AIGLX), but does it support pixel shaders?

I have an intel 82845g/gl[brookdale-g]/ge/pe. its 64Mb. I don't know if it supports pixel shaders, but i think it does. How would i find that out?

---

### Post by klange on 2008-02-23
Your Intel card will never work with the current blur method. Don't worry, though, we're [working on it](http://forum.compiz-fusion.org/showthread.php?t=5739).

The reason is not because of a lack of shaders (there is a workaround in the Workaraounds plugin that fixes this), but rather the Mesa drivers do not have an extension required for cropping the blur region properly (or at least it doesn't work. The driver is effectively kicked into software rendering when you try and enable the blur plugin, not a good idea...)

---

### Post by fracturedmorals on 2008-02-23
> **WindowsSucks said:**
> Your Intel card will never work with the current blur method. Don't worry, though, we're [working on it](http://forum.compiz-fusion.org/showthread.php?t=5739).

The reason is not because of a lack of shaders (there is a workaround in the Workaraounds plugin that fixes this), but rather the Mesa drivers do not have an extension required for cropping the blur region properly (or at least it doesn't work. The driver is effectively kicked into software rendering when you try and enable the blur plugin, not a good idea...)

So non FBO blur is being revived from it's old Beryl days?

---

### Post by klange on 2008-02-23
> **fracturedmorals said:**
> So non FBO blur is being revived from it's old Beryl days?
Yep. Regular blurring is done, but getting it to blur behind decorations is a difficult task and the dev who is porting it hasn't made much progress. But, yes, it's being worked on.

---

