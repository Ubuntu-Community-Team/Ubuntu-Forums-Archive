---
title: "SoundJuicer quitting"
date: 2006-06-13
forum: Desktop Environments
---

### Post by hashimoto on 2006-06-13
Ladies, Gents,

I made a clean Dapper install to my father. He now wants to rip some CD's to hard disk with SoundJuicer. The trouble is that SoundJuicer starts ripping but quits after a short while. I started it from terminal and the error message is:

```
Could not fully determine drive profile 0: Error reading disc information
```

And:
```
(sound-juicer:5338): Gtk-CRITICAL **: gtk_list_store_set: assertion `iter->stamp == list_store->stamp' failed
(sound-juicer:5338): Gtk-CRITICAL **: gtk_list_store_set: assertion `iter->stamp == list_store->stamp' failed 
Segmentation fault
```

I can't figure out the problem. With Breezy there was no problem at all so the drive should be OK. 

The only thing that I can think of causing this is that I finally got his printer (HPLJ1005) working and that required recompiling hotplug. Could that be the problem?

Any suggestions are welcome.

---

### Post by hashimoto on 2006-06-24
Nobody?

---

