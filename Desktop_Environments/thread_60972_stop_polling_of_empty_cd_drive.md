---
title: "stop polling of empty cd drive"
date: 2005-08-30
forum: Desktop Environments
---

### Post by chunk on 2005-08-30
Is there anyway to stop gnome-volume-manager from constantly polling my empty cd drive without turning off automounting?

Certainly my cd drive throws some kind of signal to the OS when a cd is inserted. So why all the polling?

---

### Post by skoal on 2005-08-30
H...
A...
L....

demon (no 'a')

\\//_

---

### Post by chunk on 2005-08-30
[QUOTE=skoal]H...
A...
L....

demon (no 'a')

\\//_[/QUOTE]
 Do you know an easy way to get it integrated with ubuntu?

---

### Post by skoal on 2005-08-30
[QUOTE=chunk]Do you know an easy way to get it integrated with ubuntu?[/QUOTE]
Well, I don't know exactly what you mean by 'integrated', but the hal demon is pretty much poking his pitch fork at your system right now at ~2 sec intervals (i bet), which is manifested by the IDE activity light "beeping" and "boo bopping" at you.

I really don't know how to manage it in Gnome.  I use KDE and I am losing an arm wrestling battle with it's kioslave (which is comparable to Gnome's volume manager I suppose).

Anyways, I got rid of my IDE polling (of CD-Roms) this way:

I have 2 CD-Roms on my second IDE channel, tagged as hdc and hdd by the colonel. I dropped this little gem into my /etc/hal/fdi folder:

```
skoal@morpheus://~ $ cat /etc/hal/fdi/cdrom-stfu.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
        <device>
                <match key="block.device" string="/dev/hdc">
                        <merge key="storage.media_check_enabled" type="bool">false</merge>
                </match>
        </device>
        <device>
                <match key="block.device" string="/dev/hdd">
                        <merge key="storage.media_check_enabled" type="bool">false</merge>
                </match>
        </device>
</deviceinfo>

```
...and restarted the dbus-1 script, as such:
```
skoal@morpheus://~ $ sudo /etc/init.d/dbus-1 restart
 * Stopping Hardware abstraction layer: 
   ...done.
 * Stopping system message bus: 
   ...done.
 * Starting system message bus: 
   ...done.
 * Starting Hardware abstraction layer: 
   ...done.
```
* That will get rid of that polling for you on those CD-Rom drives.  Of course, change your CD-Rom paths accordingly, and more than likely, you may want to name that file something other than I did (but it reflects my sentiments well)...

I tried setting the /etc/hal/hald.conf "<storage_media_check_enabled>" and "<storage_automount_enabled_hint>" to _false_ instead, but they were as useless to me as my own nipples.  To get the desired affect you want, however, they might serve you better than the sol'n I gave above.  I really haven't dug deeper into the bowels of hal code yet (to get a better fix), and quite frankly, who would want to...

You may lose some functionality in Gnome, however.  For example, when I fire off the KDE control center, I can no longer access the KDE components > Service Manager, giving me "Unable to Open KDEAD" or sump'n sump'n liek at...

...but, it works! ...and the way I _want_ it to...

\\//_

---

