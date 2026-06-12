---
title: "xorg update, now no nautilus?"
date: 2005-09-13
forum: Desktop Environments
---

### Post by OneSeventeen on 2005-09-13
I just ran the last few updates, and it had an issue since I'm using ATI's fglrx drivers from their website.

So I went in and manually installed xlibmesa-gl using --force-overwrite, then did an apt-get upgrade to make sure all of the new updates were installed,
Then I replaced the libGL.so.1.2 with the ATI one (by re-installing my fglrx drivers with --force-overwrite)

So now, I'm basically where I started, but with all the updates minus libGL.so.1.2

I rebooted, and can browse the web, check email, run most applications, except one minor application.... nautilus.

So this means I can't browse my filesystem, which is rather major to me.  If I open gnome-terminal and type in nautilus I get this:
```

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(nautilus:13683): Gtk-WARNING **: Theme directory scalable/mimetypes of theme eXperienceCrystal has no size field

```

Any ideas?  Did I screw something up?

And will I ever be able to use ATI drivers from Ubuntu instead of ATI, so things can be managed better? (Using a laptop w/ATI Radeon Xpress 200M)

---

### Post by jeffreyvergara.NET on 2005-09-13
i have also a problem with:

E: /var/cache/apt/archives/xlibmesa-dri_6.8.2-10.1_i386.deb:  corrupted filesystem tarfile - corrupted package archive: Success

---

### Post by OneSeventeen on 2005-09-13
Weird... that one came across just fine for me.

After rebooting a couple of times, it is now working fine... kind of weird, but I'm happy :)

---

### Post by Hairy_Palms on 2005-09-14
same thing happened to me but i just reinstalled nvidia drivers aand everythings fine again.. maybe its ATIS poor linux drivers again? i know they caused hell on my bros desktop with ubuntu

---

