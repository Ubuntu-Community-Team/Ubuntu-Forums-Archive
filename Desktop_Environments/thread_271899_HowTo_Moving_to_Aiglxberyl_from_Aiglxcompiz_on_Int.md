---
title: "HowTo: Moving to Aiglx/beryl from Aiglx/compiz on Intel i915 Video Card"
date: 2006-10-05
forum: Desktop Environments
---

### Post by sarhento_lobo on 2006-10-05
Hi all, a simple how-to here for moving to beryl from compiz (quinnstorm). This howto is based on [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX").IF you've been able to get Aiglx/compiz to work based on this [http://wiki.beryl-project.org/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.beryl-project.org/index.php/Aiglx/compiz_on_an_Intel_i915_video_card") and want to move to beryl (the fork), then proceed as follows:

1. Add repository; change the aiglx/compiz repositories in /etc/apt/sources.list to
```
deb http://ubuntu.beryl-project.org/ dapper main aiglx
```

2. Update the package list
```
sudo aptitude update
```

3. Install beryl and themes```

sudo aptitude install beryl
sudo aptitude install emerald-themes
```
This removes cgwd and components and skips the "install aiglx" step in the beryl howto (no longer needed since this was already done)

4. Start aiglx and beryl
Log out, then on the login screen, press ctrl-alt-backspace to restart X, this should load aiglx; then:
```
beryl-manager
```

Hope this helps even a bit :)

Cheers

---

