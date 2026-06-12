---
title: "Lightweight desktop?"
date: 2015-05-02
forum: Desktop Environments
---

### Post by Ian_Grant on 2015-05-02
I've just instaled 14.04 LTS on a 2.4GHz celeron with 512MB RAM, It's unusable though. The main problem is compiz is configured to do lots of fancy fade-ins etc, I tried metacity, and it's a lot better, but I can't launch apps.

Can anyone give me a recipe for getting a usable window-manager and menu system working? Also can anyone tell me how to trim the running processes. I don't need evolution calendar factories, or gphoto volume monitor. There used to be a system settings for this.

Don't get me wrong, I *love* the new simple system settings, pity it doesn't let you do anything anymore though :-)

Ian

---

### Post by Bashing-om on 2015-05-02
Ian_Grant; Hi ! Welcome to the forum .

If you do not have the horse power, you do not have the horse power.
Consider:
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]workie great, last long time
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-05-03
> I tried metacity, and it's a lot better, but I can't launch apps.
You swapped metacity with compiz maybe using the 'metacity --replace' command?
or ..
Did you install a desktop that uses metacity, like flashback?
```
sudo apt-get install gnome-session-flashback
```

Bashing has a point.  Lubuntu should run faster than a metacity (gnome) desktop.

---

### Post by kerry_s on 2015-05-03
> **Ian_Grant said:**
> I've just instaled 14.04 LTS on a 2.4GHz celeron with 512MB RAM, It's unusable though. The main problem is compiz is configured to do lots of fancy fade-ins etc, I tried metacity, and it's a lot better, but I can't launch apps.

Can anyone give me a recipe for getting a usable window-manager and menu system working? Also can anyone tell me how to trim the running processes. I don't need evolution calendar factories, or gphoto volume monitor. There used to be a system settings for this.

Don't get me wrong, I *love* the new simple system settings, pity it doesn't let you do anything anymore though :-)

Ian

with 512ram your always going to be struggling to find something usable, if at all possible you should upgrade, even with 1gb it's not enough, you'll get lockups from apps that need more, just using a modern browser like firefox or chrome you'll be well into 512mb just starting it.
if you can get at least 2gb of ram you can use any current linux with very little issues.

i'm currently using a hp mini 210 netbook, that started off with 1gb ram, while usable you could tell it was struggling, i upgraded it to the max 2gb & have no issues with standard use. i only encounter issues when i go dual monitor with my tv & try to run more apps then i should. lol

---

### Post by grahammechanical on 2015-05-03
No one has mentioned the graphic adapter. If the motherboard only has 512 MB RAM, then how much memory does the graphic adapter have? I consider anything less than 512 memory in the graphic adapter as borderline.

If the graphic adapter is incapable of doing hardware accelerated 3D rendering then it cannot run Unity 3D and the system will be running on llvmpipe. This is an open source video driver that tries to give an approximation of Unity 3D. But it definitely is slow.

Another consideration is the possibility that the proprietary video drivers have dropped support for that video adapter. So, the drivers that come with 14.04 are not suitable. There may be an older (legacy) driver in the software centre that can be installed.

This command will say if the video card can run Unity 3D which is default in Ubuntu

```
/usr/lib/nux/unity_support_test -p
```

It should show something like this
> 
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.5.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Regards.

---

### Post by RobGoss on 2015-05-03
If you want to be able to enjoy the different flavors of Ubuntu, you'll need to upgrade your ram to at least 2-GB so you will not have these problems. I have one of my machines with 1.5GB of Ram it works good but! could be better.

---

### Post by wildmanne39 on 2015-05-04
I recommend installing lubuntu or xubuntu they are lighter then ubuntu or you could even do a minimal install to get the most out of your computer.
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

