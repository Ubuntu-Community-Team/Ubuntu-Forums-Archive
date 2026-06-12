---
title: "Trash Deletion error"
date: 2009-02-12
forum: Desktop Environments
---

### Post by LordOOTFD on 2009-02-12
Alrighty, I have recently become aware of a strange problem with my Trash folder. I have ~800 files taking up 1.7 GB which absolutely will not delete. pressing the empty trash button it goes through he motions but does not delete the files. Isolating the files and trying to delete them it says there was an error deleting the files, under details is says: "Error removing file: Permission denied" 

I haven't seen this problem before and I have no idea why permission would be denied, I moved these files form my desktop or folders therein into the trash.

---

### Post by mttman on 2009-02-12
you could try ```
 sudo chmod 666 trash:/// 
``` and then try to empty the trash

I'm not sure if this will work but it's worth a try

also try to change the permissions on the files inside the trash to do this you would probably need to ```
 sudo nautilus 
``` and then use the side panel to get to the trash

<Mttman>

---

### Post by LordOOTFD on 2009-02-13
Alrighty trying the first It outputs this
"chmod: cannot access `trash:///': No such file or directory"
I'm not sure If I had to specify something more specific as my experience with the console is fairly limited.

Starting nautilus It outputs this and fails:
"seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:8531): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:8531): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:8531): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:8531): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault"

I believe it should pop up with a file browser of some sort, from what I've read.

---

### Post by sisco311 on 2009-02-13
```
sudo chown -R $USER: ~/.local/share/Trash/
```then try to empty the trash.

---

### Post by _noob_ on 2009-02-13
Look in the *_/home/user/.local_* for the Trash file. 
Hope that helps. :)

---

### Post by sisco311 on 2009-02-13
> **LordOOTFD said:**
> Alrighty trying the first It outputs this
"chmod: cannot access `trash:///': No such file or directory"
I'm not sure If I had to specify something more specific as my experience with the console is fairly limited.

Starting nautilus It outputs this and fails:
"seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:8531): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:8531): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:8531): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:8531): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault"

I believe it should pop up with a file browser of some sort, from what I've read.

It's a known bug. Remove any blank cd/dvd from the drive and try again.

```
gksu nautilus ~/.local/share/Trash/
```

---

### Post by LordOOTFD on 2009-02-13
Excellent! that solved it Thanks sisco311!

---

### Post by JRV on 2009-02-14
Thanks for pointing me in the right direction.

---

