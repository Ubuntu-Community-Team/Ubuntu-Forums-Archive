---
title: "xgl-ati-compiz HELP"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by shadycuz on 2007-09-04
Hey every one.

I'm new too linux =). And I just broke my xgl =).  Help me put it back togeather?

Okay so... I had this all working right. Then I tried to play cs:s with wine, and when i rebooted. I got xsession errors or what not.

So here is the situation. When I reboot it says.. blah blah blah, session lasted less then 10 secconds. and it points me to some error file. So here is my session error file.

Please help. also that gtk warring it list is not the warning i get at boot, at boot it says gtk warning cant open display.

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "levi"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/levi-server:/tmp/.ICE-unix/12614

(gnome-session:12614): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gnome-panel:12680): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Initializing gnome-mount extension
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "murrine",

(nautilus:12681): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
/usr/bin/restricted-manager:243: GtkWarning: Unable to locate theme engine in module_path: "murrine",
  xml = gtk.glade.XML("/usr/share/restricted-manager/manager.glade")

(update-notifier:12698): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
evolution-alarm-notify-Message: Setting timeout for 35971 1188950400 1188914429
evolution-alarm-notify-Message:  Tue Sep  4 20:00:00 2007

evolution-alarm-notify-Message:  Tue Sep  4 10:00:29 2007


(nm-applet:12708): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1875 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Tue Sep  4 20:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/levi/.evolution/calendar/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/levi/.evolution/calendar/local/system - Calendar Open Async... 0x6bcac0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:456 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x6c46a0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/levi/.evolution/tasks/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/levi/.evolution/tasks/local/system - Calendar Open Async... 0x6cb140
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/levi/.evolution/memos
(search:12696): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(evolution-alarm-notify:12703): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gnome-cups-icon:12716): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/levi/.evolution/memos/local/system - Calendar Open Async... 0x6cf660
alarm-notify.c:393 (cal_opened_cb) file:///home/levi/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/levi/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/levi/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6babc0: Received at thread 41042940
alarm-queue.c:2008 (alarm_queue_add_async) - 0x6bcac0
alarm-queue.c:560 (load_alarms_for_today) - From Tue Sep  4 10:00:30 2007
 to Tue Sep  4 10:00:30 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6babc0: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x62c7b0: Received at thread 41042940
alarm-queue.c:2008 (alarm_queue_add_async) - 0x6c46a0
alarm-queue.c:560 (load_alarms_for_today) - From Tue Sep  4 10:00:30 2007
 to Tue Sep  4 10:00:30 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x62c7b0: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6c62c0: Received at thread 41042940
alarm-queue.c:2008 (alarm_queue_add_async) - 0x6cb140
alarm-queue.c:560 (load_alarms_for_today) - From Tue Sep  4 10:00:30 2007
 to Tue Sep  4 10:00:30 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6c62c0: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6cca00: Received at thread 410Debug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
Debug: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
Debug: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(swiftfox-bin:12795): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(swiftfox-bin:12795): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(swiftfox-bin:12795): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a0000a
QMetaObject::findSignal:ClientStream: Conflict with Stream::readyRead()
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: ListTask
Transfer ACCEPTED by: ListTask
Transfer ACCEPTED by: ListTask
Transfer ACCEPTED by: ListTask
Transfer ACCEPTED by: ListTask
Transfer ACCEPTED by: ListTask
Transfer ACCEPTED by: ListTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Transfer ACCEPTED by: MailNotifierTask
Transfer ACCEPTED by: StatusNotifierTask
Transfer ACCEPTED by: MessageReceiverTask
Transfer ACCEPTED by: PictureNotifierTask
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
QGArray::find: Index 0 out of range
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished

(swiftfox-bin:12795): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
QFont::setPointSize: Point size <= 0 (-1)
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished

(swiftfox-bin:13198): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(swiftfox-bin:13198): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(swiftfox-bin:13198): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished

(metacity-dialog:13302): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Killed

(firefox-bin:13309): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(firefox-bin:13309): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13344): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13344): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13344): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13379): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13379): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13379): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13406): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13406): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13406): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13423): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13423): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13478): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13478): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13478): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13502): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13502): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13715): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13715): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13715): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13838): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13838): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13838): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:13961): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:13961): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:13961): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14058): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14058): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14058): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14073): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14073): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14073): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14093): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14093): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14093): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14222): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14222): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14222): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14266): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14266): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14266): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14306): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14306): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14306): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14333): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14333): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14333): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14409): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14409): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14409): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14424): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14424): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14522): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14522): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14522): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14539): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14539): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14539): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14596): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14596): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14596): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14616): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14616): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14616): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
Transfer ACCEPTED by: PictureNotifierTask
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14679): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14679): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14679): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14700): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14700): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14700): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14743): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14743): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14743): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14761): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14761): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14761): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14779): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14779): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14779): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14797): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14797): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14797): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14830): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14830): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14830): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14890): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14890): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14890): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14918): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14918): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14918): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:14966): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:14966): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:14966): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15004): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15004): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15004): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15040): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15040): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15040): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15079): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15079): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15079): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15119): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15119): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15119): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15150): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15150): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15150): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15184): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15184): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15184): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15215): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15215): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15215): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15253): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15253): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15253): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15289): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15289): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15289): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:15353): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:15353): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:15353): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x796400 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x796400 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
Transfer ACCEPTED by: StatusNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: RequestPictureTask: Task::done()
CLIENT: RequestPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
Transfer ACCEPTED by: PictureNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: StatusNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
checking for valid crashreport now
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: MailNotifierTask
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
QApplication::postEvent: Unexpected null receiver
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: PictureNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
Transfer ACCEPTED by: StatusNotifierTask
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:27868): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:27868): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:27868): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:27922): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:27922): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:27922): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:27937): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:27937): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:27937): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:27960): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:27960): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:27960): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:27993): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:27993): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:27993): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:28018): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:28018): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:28018): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:28045): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(npviewer.bin:28045): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(npviewer.bin:28045): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x260003c (Desktop Se)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished

(gnome-terminal:29144): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished
CLIENT: Task: Task::done()
CLIENT: Task: emitting finished

(nautilus:29561): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gedit:29578): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
```

---

### Post by shadycuz on 2007-09-04
Any one have a suggestion? 

How to uninstall and reinstall xgl?

Any thing? Like I said it was all working. Then when I loaded up steam, my computer rebooted and i got errors on login.

---

### Post by wjuniorr on 2007-09-04
> **shadycuz said:**
> Any one have a suggestion? 

How to uninstall and reinstall xgl?

Any thing? Like I said it was all working. Then when I loaded up steam, my computer rebooted and i got errors on login.

Hi my friend, you can use this tutorial : **[http://mundogeek.net/archivos/2007/08/27/ubuntu-compiz-fusion-ati/](http://mundogeek.net/archivos/2007/08/27/ubuntu-compiz-fusion-ati/)**

It is in spanish, but you can translate with ** [http://translate.google.com/translate_t](http://translate.google.com/translate_t)**


I hope it can help you!!!

Good luck ok?! :)

---

### Post by shadycuz on 2007-09-04
> **wjuniorr said:**
> Hi my friend, you can use this tutorial : **[http://mundogeek.net/archivos/2007/08/27/ubuntu-compiz-fusion-ati/](http://mundogeek.net/archivos/2007/08/27/ubuntu-compiz-fusion-ati/)**

It is in spanish, but you can translate with ** [http://translate.google.com/translate_t](http://translate.google.com/translate_t)**


I hope it can help you!!!

Good luck ok?! :)

Thank you very much. How ever my xgl is working, just crashed.

---

