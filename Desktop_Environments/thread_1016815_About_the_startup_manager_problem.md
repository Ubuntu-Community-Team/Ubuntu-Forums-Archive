---
title: "About the startup manager problem"
date: 2008-12-20
forum: Desktop Environments
---

### Post by hihiboy on 2008-12-20
[SIZE="4"]while i start with my "Start-Up Manager"
I doesn't exist proberly..
I get the message as below..[/SIZE]


-----
hihiboy@hihiboy-desktop:~/&#26700;&#38754;$ sudo startupmanager
/usr/share/startupmanager/gtk_frontend.py:159: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
self.glade_xml = gtk.glade.XML(GLADE_FILE, None ,APP_NAME)
Grub2 not detected
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd1,1)/boot/grub/splashimages/1208_splash.xpm.gz

Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash detected
Splashy not detected
Traceback (most recent call last):
File "/usr/sbin/startupmanager", line 37, in
main()
File "/usr/sbin/startupmanager", line 34, in main
SumGui()
File "/usr/share/startupmanager/gtk_frontend.py", line 190, in __init__
self.setup_widgets()
File "/usr/share/startupmanager/gtk_frontend.py", line 208, in setup_widgets
self.set_usplash_widgets()
File "/usr/share/startupmanager/gtk_frontend.py", line 388, in set_usplash_widgets
default_usplash = self.usplash.get_active_theme()
File "/usr/lib/python2.5/site-packages/bootconfig/usplash.py", line 90, in get_active_theme
self.add_theme(current_usplash_path)
File "/usr/lib/python2.5/site-packages/bootconfig/usplash.py", line 124, in add_theme
shutil.copy(path, self.themes_directory)
File "/usr/lib/python2.5/shutil.py", line 85, in copy
copyfile(src, dst)
File "/usr/lib/python2.5/shutil.py", line 51, in copyfile
fsrc = open(src, 'rb')
IOError: [Errno 2] &#27794;&#26377;&#27492;&#19968;&#27284;&#26696;&#25110;&#30446;&#37636;: '/usr/local/usplash/Blue-chrome.so'
---

[SIZE="4"]Anyone would like to do me a favour about this?

Thank You... ^^
[/SIZE]

---

