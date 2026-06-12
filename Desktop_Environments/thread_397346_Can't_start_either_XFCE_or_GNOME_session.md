---
title: "Can't start either XFCE or GNOME session"
date: 2007-03-30
forum: Desktop Environments
---

### Post by Raptor Ramjet on 2007-03-30
Sadly I'm having problems running either XFCE or GNOME sessions for my current user.  I can however log in to KDE (I've installed several DEs to try them all out)   I can also log in to both an XFCE or GNOME sessions for a different user that I set up.

When starting GNOME I get multiple errors which seem to relate to themes and always get an error saying:

"There was an error starting the GNOME Settings Daemon".

Additionally when I go to "Preferences" > " Themes" I cannot change the widget set ("controls") in use - that's if the "Themes Manager" doesn't crash when I use the "change theme" button (sorry can't remember the exact text)

When I try to start XFCE I get a blank screen (Ubuntu Human colour) with one small black oblong in the bottom centre of the screen and nothing further happens until I use "Ctrl & Alt & Backspace" to kill the X Server.

I'd therefore be grateful if anyone could tell me if it's possible to delete some "dot" files/folders to restore me to "vanilla" GNOME/XFCE installations ?

Failing I'd be grateful to know how to reinstall a default GNOME/XFCE setup just for my user ?

Thankyou.

---

### Post by x1a4 on 2007-03-30
Hi,

To reset Xfce settings delete/rename _~/.config/_, then try logging-in to Xfce.

---

### Post by Raptor Ramjet on 2007-03-31
Cheers for the reply,

However renaming ~/.config didn't help much.  When I log into XFCE I now get a blank blue screen and a mouse cursor but nothing else - which is quite entertaining in a "minimalist" kind of way :)

However further investigation and renaming a few ~/.gnome fongi files has got me back in to Gnome after a fashion.  However I can't run the "Themes" applet (going into Theme Details makes it hang) and I was getting errors relating to "gnome-settings-daemon".  So... trying to run gnome-settings-daemon from a terminal gives me dumps something similar to the following:

Memory status: size: 29376512 vsize: 0 resident: 29376512 share: 0 rss: 8269824 rss_rlim: 0
CPU usage: start_time: 1175366777 rtime: 0 utime: 14 stime: 0 cutime:12 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-settings-daemon'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)                            /* <------ Multiple lines of this */
[Thread debugging using libthread_db enabled]
[New Thread -1226729808 (LWP 5119)]
[New Thread -1229063264 (LWP 5123)]
(no debugging symbols found)                            /* <------ Multiple lines of this */
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb77a334b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ea01b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0806915d in keyboard_config_registry_get_type ()
#5  0xb77d389a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#6  0xb77ba952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#7  0xb77b8bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#8  0xb77b973f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#9  0xb77b98f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
#11 0x080551ea in gnome_settings_daemon_new ()
#12 0x08053efc in main ()

Thread 2 (Thread -1229063264 (LWP 5123)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb77a23fb in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb770a45d in g_main_context_wakeup () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb772738f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb779c504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb765a51e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1226729808 (LWP 5119)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb77a334b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ea01b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0806915d in keyboard_config_registry_get_type ()
No symbol table info available.
#5  0xb77d389a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#6  0xb77ba952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb77b8bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb77b973f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb77b98f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
No symbol table info available.
#11 0x080551ea in gnome_settings_daemon_new ()
No symbol table info available.
#12 0x08053efc in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

So somethings definitely afoot !  Any further help would be most appreciated.

---

### Post by Raptor Ramjet on 2007-04-01
Well this is thoroughly boring...  After much experimentation deleting various "dotfiles" etc. I can now run the gnome theme manager again.  But it doesn't work properly as the widgets etc. don't change and I'm stuck using a really ugly looking set of buttons (not sure from which theme).   Nautilus is also slow as molasses and my entire GNOME desktop is unusable.

On top of that trying an XFCE session still gets me a blue screen and a mouse pointer but absolutely nothing else.

So, I would be most grateful if anyone could tell me how I can completely destroy all the GNOME and XFCE settings for my user ?

Or should I just delete my user altogether (which I'm guessing will be a major pain as I also own loads of stuff in the file system (media files on various hard drives attached to various mount points) ?

As I said in a previous post the other user on the box works fine and can use GNOME and XFCE quite happily so it's definitely a problem local to my user.

Ta very glad.

---

### Post by drubulvr on 2008-06-24
> **x1a4 said:**
> Hi,

To reset Xfce settings delete/rename _~/.config/_, then try logging-in to Xfce.

thanks for this tip, it worked for me!

:)

---

