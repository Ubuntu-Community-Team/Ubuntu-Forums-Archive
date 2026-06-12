---
title: "Nautilus thumbnail generation for mp4 files fails after ubuntu upgrade to 24.04.1 LTS"
date: 2024-10-06
forum: Desktop Environments
---

### Post by lister171254 on 2024-10-06
After upgrading to 24.04.1 LTS, the thumbnail generation for mp4 files fails

Running nautilus in debug mode I get the following

```
(org.gnome.Nautilus:82993): nautilus-file-DEBUG: 17:39:09.416: file:///home/llist/tmp/YouTubetest.mp4
(org.gnome.Nautilus:82993): nautilus-async-jobs-DEBUG: 17:39:09.416: starting extension info in 0x5c3fd85025f0
(org.gnome.Nautilus:82993): nautilus-async-jobs-DEBUG: 17:39:09.417: stopping extension info in 0x5c3fd85025f0
(org.gnome.Nautilus:82993): nautilus-async-jobs-DEBUG: 17:39:09.417: starting extension info in 0x5c3fd85025f0
(org.gnome.Nautilus:82993): nautilus-view-DEBUG: 17:39:09.417: Files changed in window (0x5c3fd6e2cf80) file:///home/llist/tmp
(org.gnome.Nautilus:82993): nautilus-file-DEBUG: 17:39:09.417: file:///home/llist/tmp/YouTubetest.mp4
(org.gnome.Nautilus:82993): nautilus-async-jobs-DEBUG: 17:39:09.417: stopping extension info in 0x5c3fd85025f0
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:09.417: tmp: file changed
(org.gnome.Nautilus:82993): nautilus-async-jobs-DEBUG: 17:39:09.423: stopping file list in 0x5c3fd85025f0
(org.gnome.Nautilus:82993): nautilus-file-DEBUG: 17:39:09.518: Called file_get_icon(), at size 256
(org.gnome.Nautilus:82993): nautilus-thumbnails-DEBUG: 17:39:09.518: (Main Thread) Adding thumbnail: file:///home/llist/tmp/YouTubetest.mp4
(org.gnome.Nautilus:82993): nautilus-file-DEBUG: 17:39:09.518: Called file_get_icon(), at size 256
(org.gnome.Nautilus:82993): nautilus-window-DEBUG: 17:39:09.518: Finished loading window for uri file:///home/llist/tmp
(org.gnome.Nautilus:82993): nautilus-thumbnails-DEBUG: 17:39:09.538: (Main Thread) Creating thumbnails thread
(org.gnome.Nautilus:82993): nautilus-thumbnails-DEBUG: 17:39:09.538: (Thumbnail Thread) Creating thumbnail: file:///home/llist/tmp/YouTubetest.mp4
(org.gnome.Nautilus:82993): GnomeDesktop-DEBUG: 17:39:09.539: About to launch script: bwrap --ro-bind /usr /usr --ro-bind-try /etc/ld.so.cache /etc/ld.so.cache --symlink /usr//bin /bin --symlink /usr//lib64 /lib64 --symlink /usr//lib /lib --symlink /usr//sbin /sbin --ro-bind-try /var/cache/fontconfig /var/cache/fontconfig --setenv GST_REGISTRY_1_0 /home/llist/.cache/gnome-desktop-thumbnailer/gstreamer-1.0/gstreamer-1.0.registry --bind /home/llist/.cache/gnome-desktop-thumbnailer/gstreamer-1.0 /home/llist/.cache/gnome-desktop-thumbnailer/gstreamer-1.0 --ro-bind-try /etc/alternatives /etc/alternatives --proc /proc --dev /dev --chdir / --setenv GIO_USE_VFS local --unshare-all --die-with-parent --setenv G_MESSAGES_DEBUG all --bind /tmp/gnome-desktop-thumbnailer-Y0JIV2 /tmp --ro-bind /home/llist/tmp/YouTubetest.mp4 /tmp/gnome-desktop-file-to-thumbnail.mp4 --seccomp 45 /usr/bin/totem-video-thumbnailer -s 256 file:///tmp/gnome-desktop-file-to-thumbnail.mp4 /tmp/gnome-desktop-thumbnailer.png 

(totem-video-thumbnailer:2): GLib-GIO-DEBUG: 06:39:09.568: _g_io_module_get_default: Found default implementation local (GLocalVfs) for ‘gio-vfs’
(org.gnome.Nautilus:82993): GnomeDesktop-DEBUG: 17:39:09.666: Failed to launch script: OpenBLAS blas_thread_init: pthread_create failed for thread 6 of 16: Resource temporarily unavailable
OpenBLAS blas_thread_init: RLIMIT_NPROC 63149 current, 63149 max

(org.gnome.Nautilus:82993): nautilus-thumbnails-DEBUG: 17:39:09.666: (Thumbnail Async Thread) Thumbnail failed: file:///home/llist/tmp/YouTubetest.mp4 (Child process exited with code 130)
(org.gnome.Nautilus:82993): nautilus-view-DEBUG: 17:39:09.666: Files changed in window (0x5c3fd6e2cf80) file:///home/llist/tmp
(org.gnome.Nautilus:82993): nautilus-file-DEBUG: 17:39:09.666: file:///home/llist/tmp/YouTubetest.mp4
(org.gnome.Nautilus:82993): nautilus-thumbnails-DEBUG: 17:39:09.667: (Thumbnail Async Thread) Exiting
(org.gnome.Nautilus:82993): nautilus-file-DEBUG: 17:39:09.767: Called file_get_icon(), at size 256
(org.gnome.Nautilus:82993): dconf-DEBUG: 17:39:13.552: change_fast
(org.gnome.Nautilus:82993): nautilus-window-DEBUG: 17:39:13.552: Setting new slot (nil) as active, old slot inactive 0x5c3fd7624b30
(org.gnome.Nautilus:82993): nautilus-window-DEBUG: 17:39:13.558: Destroying window
(org.gnome.Nautilus:82993): nautilus-window-DEBUG: 17:39:13.558: Removing slot 0x5c3fd7624b30
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:13.580: tmp: disconnecting file
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:13.580: llist: disconnecting file
(org.gnome.Nautilus:82993): nautilus-previewer-DEBUG: 17:39:13.585: Unable to create NautilusPreviewer2 proxy: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.NautilusPreviewer was not provided by any .service files
** (org.gnome.Nautilus:82993): DEBUG: 17:39:25.571: *** Cancel Results Meta requests
(org.gnome.Nautilus:82993): dconf-DEBUG: 17:39:25.572: sync
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:25.572: Documents: disconnecting file
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:25.572: Pictures: disconnecting file
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:25.572: Videos: disconnecting file
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:25.572: Downloads: disconnecting file
(org.gnome.Nautilus:82993): nautilus-bookmarks-DEBUG: 17:39:25.572: ourcloud: disconnecting file
(org.gnome.Nautilus:82993): dconf-DEBUG: 17:39:25.572: unwatch_fast: "/org/gnome/desktop/lockdown/" (active: 2, establishing: 0)
(org.gnome.Nautilus:82993): Tracker-DEBUG: 17:39:25.572: Cleaning up stale resource URIs
(org.gnome.Nautilus:82993): Tracker-DEBUG: 17:39:25.573: Freed 1 readonly interfaces

```

I have a desktop running the same version of Ubuntu and the thumbnail generation works fine there.
Not sure why OpenBLAS needs all those resources.

---

### Post by simone-c on 2024-11-21
I also had an issue with thumbnails. To resolve I uninstalled totem thumbnailer, installed ffmpegthumbnailer and also deleted /usr/share/thumbnailers/totem.thumbnailer file.

Then after clearing (rm -r ~/.cache/thumbnails/*) thumbnails were back

---

### Post by lister171254 on 2024-11-21
Thanks,

That's how I resolved the issue as well. I posted this on the gnome forum and forgot about my post here.

---

