---
title: "Copy Flash to Songbird? permissions"
date: 2008-12-07
forum: General Help
---

### Post by van_be on 2008-12-07
I've been playing with Songbird in 8.10 64bit and am having trouble understanding how to copy the flash file from the Mozilla plug-ins to Songbird's plug-ins.  I have no desire to permanently change permissions, just to copy and paste the file, so I guess my question is, if i need to change permissions, how?, and once done, how to change them back as before? 

Thanks for any insight, I'm relatively new to Ubuntu and this one is out of my experience.

---

### Post by agim on 2009-01-02
I am surprised that you never received an answer. Anyway, here is what I did

I keep Songbird folder in my home directory

```

cp /usr/lib/mozilla/plugins/flashplugin-alternative.so ~/Songbird/plugins/

```

Hope this helps. Songbird is f*ing amazing.

Edit: Of course, you will have to change the Songbird/plugins/ directory when you code it yourself, depending on where you keep your Songbird file.

---

