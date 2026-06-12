---
title: "compiz-plugins-unsupported 0.8.2 jaunty"
date: 2009-04-26
forum: General Help
---

### Post by Wartender on 2009-04-26
well i recently upgraded to jaunty all excited because of the new plugins that compiz 0.8.2 has... but the package with all those new plugins is not available from synaptic... i have tried downloading th tarball and compiling it but it tells me
```
checking for COMPIZ... configure: error: Package requirements (compiz) were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
what can i do?

---

### Post by Wartender on 2009-04-26
noone?

---

### Post by Wartender on 2009-04-28
nobody has any idea what to do
(god i hate bumping)

---

### Post by qamelian on 2009-04-28
I think it is looking for the compiz-dev package to be installed first. Otherwise, you will probably be missing some header information that the plugins will need to compile successfully.

---

### Post by Wartender on 2009-04-29
well i downloaded compiz-dev and the bcop whatever, and it compiled and installed succesfully. i restarted in hope of having all they new fandy plugins but when i opened ccsm (which is at version 0.8.2 btw, like everything else) there were no new plugins...
if it means anything (i know it probably doesn't) compiz-plugins-unsupported is still marked as 0.7.8 in synaptic...

---

### Post by qamelian on 2009-04-29
That's because apps you compile from source won't appear in Synaptic...only things installed from a repo or from a downloaded DEB file. I'm not sure what else might need to be done to make them work once you've compiled them and installed them.

---

### Post by Wartender on 2009-04-29
what? ARE the unsupported plugins anyway? there are some new ones right? because maybe i do have them but there's nothing new...

---

### Post by Wartender on 2009-04-29
oh look
the unsupported plugins i AHD don't work, which means they're still 0.7.8
i'm going to try to remove them from synaptic and install the 0.8.2 again

---

### Post by Wartender on 2009-04-29
i did that, nothing happened, they're still not there, not even the ones i had when 0.7.8 was installed, so i'm sure it didn't install

---

### Post by Wartender on 2009-04-29
huh. weird. i went to usr/share/compiz and there's a snow.xml file there, snow is one of the unsupported plugins, but it doesn't show on ccsm... maybe ccsm is the problem... i'll try to reinstall it and see

---

### Post by Wartender on 2009-04-29
well that worked... theer are a couple of new plugins now, snow is back, and the new ones are cube 3d models and grid... but i've seen so many other effects on like youtube and stuff (e.g. one guys rotating this single windw like if it was a two-workspace cube, making water ripple when he moved windows, and so on) can someone point me in the direction of those (or any other new settings within existing plugins)?

---

### Post by Wartender on 2009-04-30
yep i reinstalled ccsm and it works now, all the old unsupported plugins are there, along with a couple of new ones... but they're not the ones i'm looking for... i was looking for somethign like in the youtube videos (eg. manipulating windows like a 2-workspace cube, making water ripple when moving windows, etc.) can someone point me in the right direction?

---

### Post by Wartender on 2009-04-30
oh crap lol double post i hadn't seen the last one cause i wasn't aware of a second page XD ignore that :P

---

