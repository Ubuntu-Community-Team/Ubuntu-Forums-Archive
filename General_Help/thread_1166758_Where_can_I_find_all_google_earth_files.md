---
title: "Where can I find all google earth files?"
date: 2009-05-22
forum: General Help
---

### Post by wersdaluv on 2009-05-22
Google Earth was running smoothly for me until an upgrade that happened earlier this week. This time, whenever I zoom, my view becomes light blue without the images of the map as if the place is very foggy. This doesn't happen to the same version of Google Earth on Windows. I'm assuming that I just have to delete all my Google Earth configuration files so I can have a fresh install.

I already deleted my ~/.googleearth and purged googleearth but the issue still isn't fixed and I can notice that my old settings are preserved. Where can I find all Google Earth files? :)

---

### Post by Soul-Sing on 2009-05-22
Depending how and where you installed googleearth:

```
sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth
```

---

### Post by DeMus on 2009-05-22
> **wersdaluv said:**
> Google Earth was running smoothly for me until an upgrade that happened earlier this week. This time, whenever I zoom, my view becomes light blue without the images of the map as if the place is very foggy. This doesn't happen to the same version of Google Earth on Windows. I'm assuming that I just have to delete all my Google Earth configuration files so I can have a fresh install.

I already deleted my ~/.googleearth and purged googleearth but the issue still isn't fixed and I can notice that my old settings are preserved. Where can I find all Google Earth files? :)

Maybe a strange question, but you did not switch on the layer Weather, did you? Look at the lower left side of your screen to see if this layer is on, or not before you un-install everything.

---

### Post by Soul-Sing on 2009-05-22
> **DeMus said:**
> Maybe a strange question, but you did not switch on the layer Weather, did you? Look at the lower left side of your screen to see if this layer is on, or not before you un-install everything.

indeed the weather option/layer disabled gives a foggy screen.+1

---

### Post by wersdaluv on 2009-05-22
Nope. Weather is disabled. As I zoom in, images disappear. See screenshots.

Thanks for the replies :)

---

### Post by Soul-Sing on 2009-05-22
you should enable it.

---

### Post by wersdaluv on 2009-05-22
> **leoquant said:**
> you should enable it.
Strong :)

May I know what layers are enabled by default? :)

---

