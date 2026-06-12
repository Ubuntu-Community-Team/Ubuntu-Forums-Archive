---
title: "NVidia OpenGL &quot;sync to vblank&quot; not sticking with UT2004"
date: 2007-04-02
forum: Gaming &amp; Leisure
---

### Post by cjl2301 on 2007-04-02
Ok I'm having a wierd problem.

I want vsync on for UT2004.  I have the setting set in my nvidia-settings.  However, when I boot up and run the game, it doesn't use vsync.  But then if I exit the game, lauch the nvidia settings app and just exit and run the game again - it does use vsync.

Any ideas how I can have this set permanently?

---

### Post by buttons on 2007-04-02
> **cjl2301 said:**
> Ok I'm having a wierd problem.

I want vsync on for UT2004.  I have the setting set in my nvidia-settings.  However, when I boot up and run the game, it doesn't use vsync.  But then if I exit the game, lauch the nvidia settings app and just exit and run the game again - it does use vsync.

Any ideas how I can have this set permanently?

You have to run the nvidia-settings app before ANY settings take effect, ever.  In order to make this run on startup of X you'll need to stick the following in whatever sessions startup you happen to use (in GNOME, System->Preferences->Sessions):

```
nvidia-settings --load-config-only
```

Which will load everything saved in your config without actually launching the program.  If you don't want to do that for some reason, and would instead like to simply add VSYNC, use the following command:

```
nvidia-settings --assign="SyncToVBlank=1"
```

Hope that helps!

---

### Post by cjl2301 on 2007-04-03
Ah perfect, thanks a lot!

---

