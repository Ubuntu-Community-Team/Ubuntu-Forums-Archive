---
title: "Jessie Guayadeque 0.3.7 Crash - Segmentation Fault"
date: 2015-01-26
forum: Debian
---

### Post by Adam_GUI on 2015-01-26
So, I've done an upgrade from Debian 7 (Stable) to Debian 8 (Testing).
Running Guayadeque from repositories.
Guayadeque 0.3.7-ds0-2.1 (Arch AMD64).

Running Guayadeque from term gives me this:
```
guayadeque
05:40:44 PM: Initialized locale ( en_US )
05:40:44 PM: MediaViewer 'My Music' => '54C43A15' ==>> 00000000
05:40:44 PM: Library Db Version 21
05:40:44 PM: SetViewMode -1 => 0

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed
05:40:44 PM: guLibPanel::IniPanelData( 13101 )
05:40:44 PM: guLibPanel::DoTextSearch( '' )

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed
05:40:44 PM: OnCollectionCommand 13100  0 0  1

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:29049): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed
05:40:45 PM: Updating the podcasts...
```

So far, so good, I guess.
The program launches and I can play music.

However, whenever I go to right click anything in my playlist or album list and select "Edit Songs", 
Guayadeque crashes and xterm tells me:

```
05:43:13 PM: StatusChanged( 2, 0, 0, 0 )
Segmentation fault
```

I've double-checked dependencies against the Debian page and seem to have everything it needs.
Attempting to install the i386 version gave me a warning about uninstalling stuff that looked system important.
So, I didn't attempt installing the i386 version.

The only thread I remember addressing anything similar had someone suggest installing the version from Sid.
Tried that and got the same result.  Rolled back to the repository version.

Couldn't find a place to report problems to AnonBeat.  Figured here was as good as any.

Thanks.

---

### Post by Adam_GUI on 2015-03-29
So, I've run GDB.  Output:
> gdb guayadeque
GNU gdb (Debian 7.7.1+dfsg-5) 7.7.1
Copyright (C) 2014 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from guayadeque...Reading symbols from /usr/lib/debug/.build-id/20/a1663c4c0b3e6b1109e5ed7a9971d8af7785cb.debug...done.
done.
(gdb) run
Starting program: /usr/bin/guayadeque 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
01:51:04 PM: Initialized locale ( en_US )
[New Thread 0x7fffe6e11700 (LWP 31282)]
01:51:04 PM: Mount Added...
01:51:04 PM: IconStr: '. GThemedIcon drive-optical drive'
01:51:04 PM: MediaViewer 'My Music' => '54C43A15' ==>> 00000000
01:51:04 PM: Library Db Version 21
01:51:04 PM: SetViewMode -1 => 0

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed
01:51:04 PM: guLibPanel::IniPanelData( 13101 )
01:51:04 PM: guLibPanel::DoTextSearch( '' )

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed
01:51:04 PM: OnCollectionCommand 13100  0 0  1

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'width >= -1' failed

(guayadeque:31274): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'height >= -1' failed
[New Thread 0x7fffe6124700 (LWP 31283)]
01:51:05 PM: guMainFrame::OnVolumeMonitorUpdated
01:51:05 PM: Updating the podcasts...
[New Thread 0x7fffe58c3700 (LWP 31284)]
[Thread 0x7fffe58c3700 (LWP 31284) exited]

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff73a52b5 in wxTextEntry::DoSetValue(wxString const&, int) ()
   from /usr/lib/x86_64-linux-gnu/libwx_gtk2u_core-3.0.so.0


The Signal SIGSEEGV at the end is what happens when I right-click an album and select "Edit".

Maybe I'm missing a GTK dependency?  

I've considered building from source.  Not sure how to proceed from here.

---

### Post by monkeybrain20122 on 2015-06-19
0.3.5 would work [http://guayadeque.org/index.php?p=/discussion/1849/no-libwxsqlite3-2-8-dev-in-15-04-vivid](http://guayadeque.org/index.php?p=/discussion/1849/no-libwxsqlite3-2-8-dev-in-15-04-vivid)

---

