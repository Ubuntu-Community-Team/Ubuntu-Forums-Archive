---
title: "How to get XWiiMote to work so I can use WiiU Pro Controller"
date: 2014-07-26
forum: Gaming &amp; Leisure
---

### Post by ilovemysillybanana on 2014-07-26
Has anyone here gotten xwiimote to work on Ubuntu 14.04LTS? I'm trying to install it but it shows a pin then immediately says it failed to connect :/ anyone know what to do? I really want this to work

I've installed it using this: 
[http://www.ubuntuupdates.org/package/core/trusty/universe/base/xwiimote](http://www.ubuntuupdates.org/package/core/trusty/universe/base/xwiimote)

I have wii u pro black controller.

---

### Post by ilovemysillybanana on 2014-07-26
I did a search on the forums and it seems that this guy found a solution:
[http://ubuntuforums.org/showthread.php?t=2210618&highlight=xwiimote](http://ubuntuforums.org/showthread.php?t=2210618&highlight=xwiimote)

But I have no idea how to apply, I don't know how to compile BlueZ...:/ anyone have any ideas?

```

```[COLOR=#FF0000][FONT=Ubuntu Mono]--- /home/jg/Téléchargements/bluez-4.101-old/plugins/wiimote.c[/FONT][/COLOR][COLOR=#008000]+++ /home/jg/Téléchargements/bluez-4.101/plugins/wiimote.c[/COLOR]
@@ -56,12 +56,24 @@
  * is pressed.
  */
 
[COLOR=#008000]+static uint16_t wii_ids[][2] = {
+    { 0x057e, 0x0306 },
+    { 0x057e, 0x0330 },
+};
+
+static const char *wii_names[] = {
+    "Nintendo RVL-CNT-01",
+    "Nintendo RVL-CNT-01-TR",
+    "Nintendo RVL-WBC-01",
+};
+[/COLOR]
 static ssize_t wii_pincb(struct btd_adapter *adapter, struct btd_device *device,
                         char *pinbuf, gboolean *display)
 {
     uint16_t vendor, product;
     bdaddr_t sba, dba;
     char addr[18], name[25];
[COLOR=#008000]+    unsigned int i, len;[/COLOR]
 
     adapter_get_address(adapter, &sba);
     device_get_address(device, &dba, NULL);
@@ -73,11 +85,24 @@
     device_get_name(device, name, sizeof(name));
     name[sizeof(name) - 1] = 0;
 
[COLOR=#ff0000]-    if (g_str_equal(name, "Nintendo RVL-CNT-01") ||
-                (vendor == 0x057e && product == 0x0306)) {
-        DBG("Forcing fixed pin on detected wiimote %s", addr);
-        memcpy(pinbuf, &sba, 6);
-        return 6;[/COLOR]
[COLOR=#008000]+    len = sizeof(wii_ids) / sizeof(wii_ids[0]);
+    for (i = 0; i < len; ++i) {
+        if (vendor == wii_ids[i][0] && product == wii_ids[i][1])
+            {
+            printf("Forcing fixed pin on detected wiimote %s\n", addr);
+            memcpy(pinbuf, &sba, 6);
+            return 6;
+            }
+    }
+
+    len = sizeof(wii_names) / sizeof(wii_names[0]);
+    for (i = 0; i < len; ++i) {
+        if (g_str_equal(name, wii_names[i]))
+            {
+            printf("Forcing fixed pin on detected wiimote %s\n", addr);
+            memcpy(pinbuf, &sba, 6);
+            return 6;
+            }[/COLOR]
     }
 
     return 0;

---

