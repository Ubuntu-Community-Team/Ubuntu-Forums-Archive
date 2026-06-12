---
title: "FireFox/SwiftFox YouTube and other video.."
date: 2006-07-20
forum: Desktop Environments
---

### Post by shawnrgr on 2006-07-20
I can't seem to get youtube to work for the past few days. Everything worked fine before I re-installed ubuntu. now in firefox i have video but no sound, and with swiftfox it tells me that i need to turn on java or upgrade flash. so flash is working in firefox but with no sound, why doesn't it work in swiftfox? and how can i get my sound working?

---

### Post by Jasper Houtman on 2006-07-20
Just (re)install java and the flash plug-in. Should be fine after that.

---

### Post by justintime32 on 2006-07-20
Firstly, exit out of all other applications that generate sound of any kind.

Then run this command:

```

killall esd

```

Now restart Firefox and see if that helps.

The reason Swiftfox doesn't play it is because it has a different plugin directory than Firefox does. I did this and it helped. (note: I'm assuming you installed Swiftfox in /usr/lib/swiftfox, if you installed it elsewhere modify the following accordingly)

```

sudo mv /usr/lib/swiftfox/plugins /usr/lib/swiftfox/plugins-old
sudo ln -s /usr/lib/firefox/plugins /usr/lib/swiftfox/plugins

```

That will give you all the Firefox plugins. The advantage of this is that when you add/remove firefox plugins in Synaptic it will apply to Swiftfox too.

---

### Post by shawnrgr on 2006-07-20
is it safe to remove firefox & just keep swiftfox?

---

