---
title: "Stupidly broke firefox"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-14
I'd been using Swiftfox for the past few days, but decided to go back to firefox as I didn't notice any significant speed increase.  I deleted the swiftfox folder, but I can't use firefox as I get this error:

```
~$ firefox
GTK Accessibility Module initialized
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libdocshell.so: undefined symbol: PR_GetPhysicalMemorySize
~$ mozilla-firefox
GTK Accessibility Module initialized
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libdocshell.so: undefined symbol: PR_GetPhysicalMemorySize
```


I uninstalled and reinstalled firefox using apt-get with the same result.  I think it may be to do with me linking things for the use of swiftfox, but I have no idea what I have done so don't know how to undo them.  I just want to get firefox working!  (I'd prefer opera, but it doesn't seem to remember what plugins I am using, so annoys me).

---

### Post by orb9220 on 2006-07-14
Did you delete the swiftfox folder or uninstall the proper way>

If you did the BIG! No-No [-(  Then try to reinstall swiftfox and see that it 
is running ok then uninstall it.

??

Hope it works for you.

---

### Post by Lunar_Lamp on 2006-07-14
I didn't ever 'install' it per se.  I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=142798](http://ubuntuforums.org/showthread.php?t=142798)

I then set up some symlinks so directed elsewhere on the forums.

---

### Post by philippe_carlo on 2006-07-14
Maybe doing this helps:
```

sudo aptitude reinstall firefox

```

---

