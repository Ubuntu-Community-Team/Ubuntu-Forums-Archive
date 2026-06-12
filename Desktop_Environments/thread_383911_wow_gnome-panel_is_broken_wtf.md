---
title: "wow gnome-panel is broken wtf"
date: 2007-03-13
forum: Desktop Environments
---

### Post by tee2 on 2007-03-13
I tried to extract an ISO onto my desktop and while it was extracting I entered the temporary folder. Next thing, gnome-panel crashes and bugbuddy comes up. I clicked close and then gnome-panel closed and came up again only to freeze. I repeated this  a few times in frustration until I rebooted with the terminal window I had open. When I logged in the same thing happened immediately. Then I tried logging in with a failsafe session and it *still* happened. What can I do to fix this? If I boot into recovery mode and startx to log in as root it doesn't happen but I'd rather not do that for security reasons. 

Here is the bugbuddy report if it helps any.

> Memory status: size: 30027776 vsize: 0 resident: 30027776 share: 0 rss: 13037568 rss_rlim: 0
CPU usage: start_time: 1173831582 rtime: 0 utime: 50 stime: 0 cutime:44 cstime: 0 timeout: 6 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225800016 (LWP 4973)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75b3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eab1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb749b770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb749cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76b7122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76b7159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76b71d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b06d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b06dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b02591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76acaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76ae802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76b17df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76b1b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7ab0574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225800016 (LWP 4973)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75b3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eab1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb749b770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb749cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76b7122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76b7159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76b71d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b06d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b06dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b02591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76acaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76ae802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76b17df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76b1b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7ab0574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


---

### Post by daengbo on 2007-03-13
I could be that a file in your config got corrupted. You should login with a session of "Gnome Failsafe" to try to debug the problem, removing extra cruft from your panel. If that doesn't work and you don't have a lot of customization done to the panel, you can try removing the config file from a terminal, then logging in. I suspect that will fix your problem.

It could also be caused by one of the panel applets, in which case you'll want to figure out which one it is and submit a bug report on it.

---

### Post by tee2 on 2007-03-13
How do I delete the config file? Where is it located?

---

### Post by daengbo on 2007-03-13
Start with .gnome2/panel2.d in you home directory, then remove .gnome2 completely if that doesn't help.

First choice should be to try to log in to a safe session.

---

### Post by tee2 on 2007-03-13
I tried logging into a safe session as well as removing .gnome2 and neither worked :(

---

### Post by daengbo on 2007-03-15
Have you tried creating a new account and logging in to see if you have the same situation with it?

---

### Post by Mike_SMD on 2007-03-15
Hey folks,
I'm having what appears to be *exactly* the same problem.

I tried to extract a .iso file on the desktop and bug buddy came up telling me that something had crashed. I believe it said that it was an unknown application, but I'm not precisely positive about that. Gnome panel seems to be trying to restart but failing, bug buddy then comes up informing me of the crash and the whole process just keeps repeating itself in a loop for a good five times or so and then gnome panels stops trying to restart and I'm left with a desktop but no way in which to access anything (no bars on the top or bottom of the screen). 

There is a second account on this computer and when I log in using that instead the problem does not exist.

Below I've included the text dump from bug buddy, however I'm a near newbie and don't really know what to do with the information that it contains.

My questions in a nutshell...

1) How do I report this bug?
2) Is it possible to fix this by reinstalling gnome control panel and how would I go about doing that?
3)How do you boot up in either failsafe or recovery mode? And what do I look for in this in order to help solve the problem?
4) Does anyone have any other advice that I could try?

As a not please pretend that you're talking to a child in your reply, I'm not a Linux hacker and need things explained to me in non-guru terms. I'm trying, but years of being crippled by Windows has definitely left a mark.

Thanks very much!

Mike_SMD

---------------------
Bug Buddy Dump Below
---------------------

Memory status: size: 52584448 vsize: 0 resident: 52584448 share: 0 rss: 13344768 rss_rlim: 0
CPU usage: start_time: 1173911714 rtime: 0 utime: 125 stime: 0 cutime:114 cstime: 0 timeout: 11 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225861456 (LWP 24626)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75a3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e9c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb748c770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb748def3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76a8122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76a8159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76a81d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7af7d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7af7dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7af3591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb769daa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb769f802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76a27df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76a2b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7aa1574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225861456 (LWP 24626)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75a3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e9c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb748c770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb748def3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76a8122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76a8159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76a81d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7af7d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7af7dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7af3591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb769daa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb769f802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76a27df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76a2b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7aa1574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by Mike_SMD on 2007-03-15
Hey again folks,
I tried the removing .gnome2 folder but still had no luck, however there is a fix posted here that I just used and it seems to work.

[http://www.ubuntuforums.org/showthread.php?t=356854&page=3&highlight=reinstall+gnome+panel](http://www.ubuntuforums.org/showthread.php?t=356854&page=3&highlight=reinstall+gnome+panel)

I don't know why or how, but going into terminal (ctrl+alt+f1) and typing the following command:

rm -rf .recently-used.xbel

then switching back to gnome (alt+f7) and then rebooting gnome (crtl+alt+backspace) and logging in again seems to have solved the problem.

Hope that helps, seems more people than just us have been having this issue.

Take care,

Mike_SMD.

---

### Post by tee2 on 2007-03-17
I fixed the problem the other day by opening synaptic in a terminal and reinstalling gnome-panel. Hope it fixes your problem to.

---

