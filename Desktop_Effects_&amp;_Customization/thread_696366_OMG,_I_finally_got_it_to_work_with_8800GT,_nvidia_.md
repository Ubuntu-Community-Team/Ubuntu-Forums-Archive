---
title: "OMG, I finally got it to work with 8800GT, nvidia drivers, ubuntu 7.10, and compiz"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by jeffeb3 on 2008-02-13
Here's the skinny:

I had Ubuntu 7.10, with an nvidia card (7300, I think), and I had all the nifty desktop effects enabled.

I bought a new card 8800GT, from ECS.  I thought it would be simple and fast to upgrade.

It wasn't the nvidia drivers are too new, and ubuntu doesn't help you install them.  I installed them using envy, there are some guides around for that.  But basically, it installs it from the blah_blah_blah.run package you can find on nvidia's site.

BUT THEN, somehow, through all the configuration, and reconfiguration, or something, I would get only the white cube of death, the thing where your screen won't draw any of the textures, so you get a white screen, even though your desktop is functioning behind it.  You can rotate the cube, and see the cube, but no textures.  You can go to the top right corner, and do that shaded application switchy thing, but it just turns the screen gray except for a couple white boxes.  It's miserable.

I just wanted to post something on how I fixed this, because I couldn't find a great amount of info on the subject.  

The problem is that the nvidia driver doesn't like xgl.  I fixed it by disabling xgl.
```
touch ~/.configure/xserver_xgl/disable
```

Just hit Ctrl+Alt+F1 to get to a fresh terminal, and execute that.  If it complains because xserver-xgl doesn't exist, then make it:
```
mkdir ~/.configure/xserver-xgl
```

Maybe there's a better way to disable xgl, and maybe there's a way to get nvidia to work with xgl, but I'm happy as a clam right now with this :)  10610 fps in glxgears

---

