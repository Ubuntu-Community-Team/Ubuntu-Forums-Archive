---
title: "Make/Make Install/ etc problems"
date: 2006-03-03
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-03-03
Any help please

```
crowell@ubuntu:~/pv2tool-for-linux$ sudo make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
cc -c   -fno-common -ffast-math -W -Wall -Wshadow -Wcast-align -Wredundant-decls -Wbad-function-cast -Wcast-qual -Wwrite-strings -Waggregate-return -Wstrict-prototypes -Wmissing-prototypes -O2 -s       download_flash.c -o download_flash.o
In file included from globals.h:11,
                 from download_flash.c:1:
io/io.h:4:17: error: usb.h: No such file or directory
io/io.h:6:18: error: glib.h: No such file or directory
In file included from globals.h:11,
                 from download_flash.c:1:
io/io.h:11: error: syntax error before ‘*’ token
io/io.h:11: warning: type defaults to ‘int’ in declaration of ‘m_p_handle’
io/io.h:11: warning: data definition has no type or storage class
io/io.h:63: error: syntax error before ‘ControlMessageWrite’
io/io.h:63: warning: type defaults to ‘int’ in declaration of ‘ControlMessageWrite’
io/io.h:63: warning: data definition has no type or storage class
io/io.h:64: error: syntax error before ‘ControlMessageRead’
io/io.h:64: warning: type defaults to ‘int’ in declaration of ‘ControlMessageRead’
io/io.h:64: warning: data definition has no type or storage class
io/io.h:68: error: syntax error before ‘ReadSector’
io/io.h:68: warning: type defaults to ‘int’ in declaration of ‘ReadSector’
io/io.h:68: warning: data definition has no type or storage class
io/io.h:72: error: syntax error before ‘Open’
io/io.h:72: warning: type defaults to ‘int’ in declaration of ‘Open’
io/io.h:72: warning: data definition has no type or storage class
io/io.h:73: error: syntax error before ‘Init’
io/io.h:73: warning: type defaults to ‘int’ in declaration of ‘Init’
io/io.h:73: warning: data definition has no type or storage class
io/io.h:74: error: syntax error before ‘CheckCameraOpen’
io/io.h:74: warning: type defaults to ‘int’ in declaration of ‘CheckCameraOpen’
io/io.h:74: warning: data definition has no type or storage class
In file included from globals.h:12,
                 from download_flash.c:1:
widgets/widgets.h:3:21: error: gtk/gtk.h: No such file or directory
In file included from globals.h:12,
                 from download_flash.c:1:
widgets/widgets.h:11: error: syntax error before ‘*’ token
widgets/widgets.h:11: warning: type defaults to ‘int’ in declaration of ‘main_window’
widgets/widgets.h:11: warning: data definition has no type or storage class
widgets/widgets.h:12: error: syntax error before ‘*’ token
widgets/widgets.h:12: warning: type defaults to ‘int’ in declaration of ‘m_ctl_progress’
widgets/widgets.h:12: warning: data definition has no type or storage class
widgets/widgets.h:16: error: syntax error before ‘*’ token
widgets/widgets.h:16: warning: type defaults to ‘int’ in declaration of ‘bitrate_label’
widgets/widgets.h:16: warning: data definition has no type or storage class
widgets/widgets.h:39: error: syntax error before ‘GtkWidget’
widgets/widgets.h:39: warning: no semicolon at end of struct or union
widgets/widgets.h:40: warning: type defaults to ‘int’ in declaration of ‘b’
widgets/widgets.h:40: warning: data definition has no type or storage class
widgets/widgets.h:41: error: syntax error before ‘}’ token
widgets/widgets.h:41: warning: type defaults to ‘int’ in declaration of ‘double_widget’
widgets/widgets.h:41: warning: data definition has no type or storage class
widgets/widgets.h:45: error: syntax error before ‘MessageBoxTextTwo’
widgets/widgets.h:45: error: syntax error before ‘gpointer’
widgets/widgets.h:45: warning: type defaults to ‘int’ in declaration of ‘MessageBoxTextTwo’
widgets/widgets.h:45: warning: function declaration isn’t a prototype
widgets/widgets.h:45: warning: data definition has no type or storage class
widgets/widgets.h:46: error: syntax error before ‘MessageBox’
widgets/widgets.h:46: warning: type defaults to ‘int’ in declaration of ‘MessageBox’
widgets/widgets.h:46: warning: data definition has no type or storage class
widgets/widgets.h:48: error: syntax error before ‘MessageBoxConfirm’
widgets/widgets.h:48: warning: type defaults to ‘int’ in declaration of ‘MessageBoxConfirm’
widgets/widgets.h:48: warning: data definition has no type or storage class
widgets/widgets.h:49: error: syntax error before ‘set_progress_bar’
widgets/widgets.h:49: warning: type defaults to ‘int’ in declaration of ‘set_progress_bar’
widgets/widgets.h:49: warning: data definition has no type or storage class
widgets/widgets.h:50: error: syntax error before ‘set_bitrate’
widgets/widgets.h:50: warning: type defaults to ‘int’ in declaration of ‘set_bitrate’
widgets/widgets.h:50: warning: data definition has no type or storage class
widgets/widgets.h:51: error: syntax error before ‘watch_progress_bar’
widgets/widgets.h:51: error: syntax error before ‘data’
widgets/widgets.h:51: warning: type defaults to ‘int’ in declaration of ‘watch_progress_bar’
widgets/widgets.h:51: warning: function declaration isn’t a prototype
widgets/widgets.h:51: warning: data definition has no type or storage class
In file included from download_flash.c:1:
globals.h:80: error: syntax error before ‘toggle_camera_lcd_screen_is_on’
globals.h:80: warning: type defaults to ‘int’ in declaration of ‘toggle_camera_lcd_screen_is_on’
globals.h:80: warning: data definition has no type or storage class
globals.h:83: error: syntax error before ‘*’ token
globals.h:83: warning: type defaults to ‘int’ in declaration of ‘m_directory_tree’
globals.h:83: warning: data definition has no type or storage class
globals.h:85: error: syntax error before ‘*’ token
globals.h:85: warning: type defaults to ‘int’ in declaration of ‘icon_blankdir’
globals.h:85: warning: data definition has no type or storage class
globals.h:86: error: syntax error before ‘*’ token
globals.h:86: warning: type defaults to ‘int’ in declaration of ‘icon_avifile’
globals.h:86: warning: data definition has no type or storage class
globals.h:87: error: syntax error before ‘*’ token
globals.h:87: warning: type defaults to ‘int’ in declaration of ‘icon_binfile’
globals.h:87: warning: data definition has no type or storage class
globals.h:88: error: syntax error before ‘*’ token
globals.h:88: warning: type defaults to ‘int’ in declaration of ‘icon_jpgfile’
globals.h:88: warning: data definition has no type or storage class
globals.h:89: error: syntax error before ‘*’ token
globals.h:89: warning: type defaults to ‘int’ in declaration of ‘icon_txtfile’
globals.h:89: warning: data definition has no type or storage class
globals.h:90: error: syntax error before ‘*’ token
globals.h:90: warning: type defaults to ‘int’ in declaration of ‘icon_wavfile’
globals.h:90: warning: data definition has no type or storage class
globals.h:91: error: syntax error before ‘*’ token
globals.h:91: warning: type defaults to ‘int’ in declaration of ‘icon_zbmfile’
globals.h:91: warning: data definition has no type or storage class
globals.h:100: error: syntax error before ‘flipper_capture’
globals.h:100: warning: type defaults to ‘int’ in declaration of ‘flipper_capture’
globals.h:100: warning: data definition has no type or storage class
globals.h:109: error: syntax error before ‘open_camera’
globals.h:109: error: syntax error before ‘*’ token
globals.h:111: warning: type defaults to ‘int’ in declaration of ‘open_camera’
globals.h:111: warning: function declaration isn’t a prototype
globals.h:111: warning: data definition has no type or storage class
globals.h:112: error: syntax error before ‘close_camera’
globals.h:112: error: syntax error before ‘*’ token
globals.h:114: warning: type defaults to ‘int’ in declaration of ‘close_camera’
globals.h:114: warning: function declaration isn’t a prototype
globals.h:114: warning: data definition has no type or storage class
globals.h:115: error: syntax error before ‘unlock_camera’
globals.h:115: error: syntax error before ‘*’ token
globals.h:117: warning: type defaults to ‘int’ in declaration of ‘unlock_camera’globals.h:117: warning: function declaration isn’t a prototype
globals.h:117: warning: data definition has no type or storage class
globals.h:118: error: syntax error before ‘sdram_scan’
globals.h:118: error: syntax error before ‘*’ token
globals.h:120: warning: type defaults to ‘int’ in declaration of ‘sdram_scan’
globals.h:120: warning: function declaration isn’t a prototype
globals.h:120: warning: data definition has no type or storage class
globals.h:121: error: syntax error before ‘format_camera’
globals.h:121: error: syntax error before ‘*’ token
globals.h:123: warning: type defaults to ‘int’ in declaration of ‘format_camera’globals.h:123: warning: function declaration isn’t a prototype
globals.h:123: warning: data definition has no type or storage class
globals.h:125: error: syntax error before ‘update_directory_listing’
globals.h:125: error: syntax error before ‘*’ token
globals.h:127: warning: type defaults to ‘int’ in declaration of ‘update_directory_listing’
globals.h:127: warning: function declaration isn’t a prototype
globals.h:127: warning: data definition has no type or storage class
globals.h:128: error: syntax error before ‘take_pic’
globals.h:128: error: syntax error before ‘*’ token
globals.h:130: warning: type defaults to ‘int’ in declaration of ‘take_pic’
globals.h:130: warning: function declaration isn’t a prototype
globals.h:130: warning: data definition has no type or storage class
globals.h:131: error: syntax error before ‘download_file’
globals.h:131: error: syntax error before ‘*’ token
globals.h:133: warning: type defaults to ‘int’ in declaration of ‘download_file’globals.h:133: warning: function declaration isn’t a prototype
globals.h:133: warning: data definition has no type or storage class
globals.h:134: error: syntax error before ‘download_flash’
globals.h:134: error: syntax error before ‘*’ token
globals.h:136: warning: type defaults to ‘int’ in declaration of ‘download_flash’
globals.h:136: warning: function declaration isn’t a prototype
globals.h:136: warning: data definition has no type or storage class
globals.h:140: error: syntax error before ‘enable_buttons’
globals.h:140: error: syntax error before ‘*’ token
globals.h:142: warning: type defaults to ‘int’ in declaration of ‘enable_buttons’
globals.h:142: warning: function declaration isn’t a prototype
globals.h:142: warning: data definition has no type or storage class
globals.h:146: error: syntax error before ‘value’
globals.h:146: warning: function declaration isn’t a prototype
globals.h:147: error: syntax error before ‘GtkWidget’
globals.h:147: warning: function declaration isn’t a prototype
globals.h:150: error: syntax error before ‘DownloadFile’
globals.h:150: warning: type defaults to ‘int’ in declaration of ‘DownloadFile’
globals.h:150: warning: data definition has no type or storage class
download_flash.c:4: warning: no previous prototype for ‘Download_Flash’
download_flash.c: In function ‘Download_Flash’:
download_flash.c:26: warning: implicit declaration of function ‘ReadFlash’
download_flash.c: At top level:
download_flash.c:56: warning: no previous prototype for ‘download_flash_start_thread’
download_flash.c: In function ‘download_flash_start_thread’:
download_flash.c:57: error: ‘FALSE’ undeclared (first use in this function)
download_flash.c:57: error: (Each undeclared identifier is reported only once
download_flash.c:57: error: for each function it appears in.)
download_flash.c:59: error: ‘TRUE’ undeclared (first use in this function)
download_flash.c: At top level:
download_flash.c:66: error: syntax error before ‘download_flash’
download_flash.c:66: error: syntax error before ‘*’ token
download_flash.c:68: warning: return type defaults to ‘int’
download_flash.c:68: warning: function declaration isn’t a prototype
download_flash.c: In function ‘download_flash’:
download_flash.c:70: error: ‘GError’ undeclared (first use in this function)
download_flash.c:70: error: ‘error’ undeclared (first use in this function)
download_flash.c:71: error: ‘FALSE’ undeclared (first use in this function)
download_flash.c:73: warning: implicit declaration of function ‘get_download_filename’
download_flash.c:73: warning: assignment makes pointer from integer without a cast
download_flash.c:77: warning: implicit declaration of function ‘g_thread_create’download_flash.c:77: error: ‘GThreadFunc’ undeclared (first use in this function)
download_flash.c:77: error: syntax error before ‘download_flash_start_thread’
download_flash.c:78: error: ‘a’ undeclared (first use in this function)
download_flash.c: At top level:
download_flash.c:78: error: syntax error before ‘while’
download_flash.c:79: warning: type defaults to ‘int’ in declaration of ‘EnableControls’
download_flash.c:79: warning: parameter names (without types) in function declaration
download_flash.c:79: error: conflicting types for ‘EnableControls’
globals.h:146: error: previous declaration of ‘EnableControls’ was here
download_flash.c:79: warning: data definition has no type or storage class
download_flash.c:80: error: syntax error before ‘return’
make: *** [download_flash.o] Error 1
crowell@ubuntu:~/pv2tool-for-linux$ sudo make install
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
cc -c   -fno-common -ffast-math -W -Wall -Wshadow -Wcast-align -Wredundant-decls -Wbad-function-cast -Wcast-qual -Wwrite-strings -Waggregate-return -Wstrict-prototypes -Wmissing-prototypes -O2 -s       download_flash.c -o download_flash.o
In file included from globals.h:11,
                 from download_flash.c:1:
io/io.h:4:17: error: usb.h: No such file or directory
io/io.h:6:18: error: glib.h: No such file or directory
In file included from globals.h:11,
                 from download_flash.c:1:
io/io.h:11: error: syntax error before ‘*’ token
io/io.h:11: warning: type defaults to ‘int’ in declaration of ‘m_p_handle’
io/io.h:11: warning: data definition has no type or storage class
io/io.h:63: error: syntax error before ‘ControlMessageWrite’
io/io.h:63: warning: type defaults to ‘int’ in declaration of ‘ControlMessageWrite’
io/io.h:63: warning: data definition has no type or storage class
io/io.h:64: error: syntax error before ‘ControlMessageRead’
io/io.h:64: warning: type defaults to ‘int’ in declaration of ‘ControlMessageRead’
io/io.h:64: warning: data definition has no type or storage class
io/io.h:68: error: syntax error before ‘ReadSector’
io/io.h:68: warning: type defaults to ‘int’ in declaration of ‘ReadSector’
io/io.h:68: warning: data definition has no type or storage class
io/io.h:72: error: syntax error before ‘Open’
io/io.h:72: warning: type defaults to ‘int’ in declaration of ‘Open’
io/io.h:72: warning: data definition has no type or storage class
io/io.h:73: error: syntax error before ‘Init’
io/io.h:73: warning: type defaults to ‘int’ in declaration of ‘Init’
io/io.h:73: warning: data definition has no type or storage class
io/io.h:74: error: syntax error before ‘CheckCameraOpen’
io/io.h:74: warning: type defaults to ‘int’ in declaration of ‘CheckCameraOpen’
io/io.h:74: warning: data definition has no type or storage class
In file included from globals.h:12,
                 from download_flash.c:1:
widgets/widgets.h:3:21: error: gtk/gtk.h: No such file or directory
In file included from globals.h:12,
                 from download_flash.c:1:
widgets/widgets.h:11: error: syntax error before ‘*’ token
widgets/widgets.h:11: warning: type defaults to ‘int’ in declaration of ‘main_window’
widgets/widgets.h:11: warning: data definition has no type or storage class
widgets/widgets.h:12: error: syntax error before ‘*’ token
widgets/widgets.h:12: warning: type defaults to ‘int’ in declaration of ‘m_ctl_progress’
widgets/widgets.h:12: warning: data definition has no type or storage class
widgets/widgets.h:16: error: syntax error before ‘*’ token
widgets/widgets.h:16: warning: type defaults to ‘int’ in declaration of ‘bitrate_label’
widgets/widgets.h:16: warning: data definition has no type or storage class
widgets/widgets.h:39: error: syntax error before ‘GtkWidget’
widgets/widgets.h:39: warning: no semicolon at end of struct or union
widgets/widgets.h:40: warning: type defaults to ‘int’ in declaration of ‘b’
widgets/widgets.h:40: warning: data definition has no type or storage class
widgets/widgets.h:41: error: syntax error before ‘}’ token
widgets/widgets.h:41: warning: type defaults to ‘int’ in declaration of ‘double_widget’
widgets/widgets.h:41: warning: data definition has no type or storage class
widgets/widgets.h:45: error: syntax error before ‘MessageBoxTextTwo’
widgets/widgets.h:45: error: syntax error before ‘gpointer’
widgets/widgets.h:45: warning: type defaults to ‘int’ in declaration of ‘MessageBoxTextTwo’
widgets/widgets.h:45: warning: function declaration isn’t a prototype
widgets/widgets.h:45: warning: data definition has no type or storage class
widgets/widgets.h:46: error: syntax error before ‘MessageBox’
widgets/widgets.h:46: warning: type defaults to ‘int’ in declaration of ‘MessageBox’
widgets/widgets.h:46: warning: data definition has no type or storage class
widgets/widgets.h:48: error: syntax error before ‘MessageBoxConfirm’
widgets/widgets.h:48: warning: type defaults to ‘int’ in declaration of ‘MessageBoxConfirm’
widgets/widgets.h:48: warning: data definition has no type or storage class
widgets/widgets.h:49: error: syntax error before ‘set_progress_bar’
widgets/widgets.h:49: warning: type defaults to ‘int’ in declaration of ‘set_progress_bar’
widgets/widgets.h:49: warning: data definition has no type or storage class
widgets/widgets.h:50: error: syntax error before ‘set_bitrate’
widgets/widgets.h:50: warning: type defaults to ‘int’ in declaration of ‘set_bitrate’
widgets/widgets.h:50: warning: data definition has no type or storage class
widgets/widgets.h:51: error: syntax error before ‘watch_progress_bar’
widgets/widgets.h:51: error: syntax error before ‘data’
widgets/widgets.h:51: warning: type defaults to ‘int’ in declaration of ‘watch_progress_bar’
widgets/widgets.h:51: warning: function declaration isn’t a prototype
widgets/widgets.h:51: warning: data definition has no type or storage class
In file included from download_flash.c:1:
globals.h:80: error: syntax error before ‘toggle_camera_lcd_screen_is_on’
globals.h:80: warning: type defaults to ‘int’ in declaration of ‘toggle_camera_lcd_screen_is_on’
globals.h:80: warning: data definition has no type or storage class
globals.h:83: error: syntax error before ‘*’ token
globals.h:83: warning: type defaults to ‘int’ in declaration of ‘m_directory_tree’
globals.h:83: warning: data definition has no type or storage class
globals.h:85: error: syntax error before ‘*’ token
globals.h:85: warning: type defaults to ‘int’ in declaration of ‘icon_blankdir’
globals.h:85: warning: data definition has no type or storage class
globals.h:86: error: syntax error before ‘*’ token
globals.h:86: warning: type defaults to ‘int’ in declaration of ‘icon_avifile’
globals.h:86: warning: data definition has no type or storage class
globals.h:87: error: syntax error before ‘*’ token
globals.h:87: warning: type defaults to ‘int’ in declaration of ‘icon_binfile’
globals.h:87: warning: data definition has no type or storage class
globals.h:88: error: syntax error before ‘*’ token
globals.h:88: warning: type defaults to ‘int’ in declaration of ‘icon_jpgfile’
globals.h:88: warning: data definition has no type or storage class
globals.h:89: error: syntax error before ‘*’ token
globals.h:89: warning: type defaults to ‘int’ in declaration of ‘icon_txtfile’
globals.h:89: warning: data definition has no type or storage class
globals.h:90: error: syntax error before ‘*’ token
globals.h:90: warning: type defaults to ‘int’ in declaration of ‘icon_wavfile’
globals.h:90: warning: data definition has no type or storage class
globals.h:91: error: syntax error before ‘*’ token
globals.h:91: warning: type defaults to ‘int’ in declaration of ‘icon_zbmfile’
globals.h:91: warning: data definition has no type or storage class
globals.h:100: error: syntax error before ‘flipper_capture’
globals.h:100: warning: type defaults to ‘int’ in declaration of ‘flipper_capture’
globals.h:100: warning: data definition has no type or storage class
globals.h:109: error: syntax error before ‘open_camera’
globals.h:109: error: syntax error before ‘*’ token
globals.h:111: warning: type defaults to ‘int’ in declaration of ‘open_camera’
globals.h:111: warning: function declaration isn’t a prototype
globals.h:111: warning: data definition has no type or storage class
globals.h:112: error: syntax error before ‘close_camera’
globals.h:112: error: syntax error before ‘*’ token
globals.h:114: warning: type defaults to ‘int’ in declaration of ‘close_camera’
globals.h:114: warning: function declaration isn’t a prototype
globals.h:114: warning: data definition has no type or storage class
globals.h:115: error: syntax error before ‘unlock_camera’
globals.h:115: error: syntax error before ‘*’ token
globals.h:117: warning: type defaults to ‘int’ in declaration of ‘unlock_camera’globals.h:117: warning: function declaration isn’t a prototype
globals.h:117: warning: data definition has no type or storage class
globals.h:118: error: syntax error before ‘sdram_scan’
globals.h:118: error: syntax error before ‘*’ token
globals.h:120: warning: type defaults to ‘int’ in declaration of ‘sdram_scan’
globals.h:120: warning: function declaration isn’t a prototype
globals.h:120: warning: data definition has no type or storage class
globals.h:121: error: syntax error before ‘format_camera’
globals.h:121: error: syntax error before ‘*’ token
globals.h:123: warning: type defaults to ‘int’ in declaration of ‘format_camera’globals.h:123: warning: function declaration isn’t a prototype
globals.h:123: warning: data definition has no type or storage class
globals.h:125: error: syntax error before ‘update_directory_listing’
globals.h:125: error: syntax error before ‘*’ token
globals.h:127: warning: type defaults to ‘int’ in declaration of ‘update_directory_listing’
globals.h:127: warning: function declaration isn’t a prototype
globals.h:127: warning: data definition has no type or storage class
globals.h:128: error: syntax error before ‘take_pic’
globals.h:128: error: syntax error before ‘*’ token
globals.h:130: warning: type defaults to ‘int’ in declaration of ‘take_pic’
globals.h:130: warning: function declaration isn’t a prototype
globals.h:130: warning: data definition has no type or storage class
globals.h:131: error: syntax error before ‘download_file’
globals.h:131: error: syntax error before ‘*’ token
globals.h:133: warning: type defaults to ‘int’ in declaration of ‘download_file’globals.h:133: warning: function declaration isn’t a prototype
globals.h:133: warning: data definition has no type or storage class
globals.h:134: error: syntax error before ‘download_flash’
globals.h:134: error: syntax error before ‘*’ token
globals.h:136: warning: type defaults to ‘int’ in declaration of ‘download_flash’
globals.h:136: warning: function declaration isn’t a prototype
globals.h:136: warning: data definition has no type or storage class
globals.h:140: error: syntax error before ‘enable_buttons’
globals.h:140: error: syntax error before ‘*’ token
globals.h:142: warning: type defaults to ‘int’ in declaration of ‘enable_buttons’
globals.h:142: warning: function declaration isn’t a prototype
globals.h:142: warning: data definition has no type or storage class
globals.h:146: error: syntax error before ‘value’
globals.h:146: warning: function declaration isn’t a prototype
globals.h:147: error: syntax error before ‘GtkWidget’
globals.h:147: warning: function declaration isn’t a prototype
globals.h:150: error: syntax error before ‘DownloadFile’
globals.h:150: warning: type defaults to ‘int’ in declaration of ‘DownloadFile’
globals.h:150: warning: data definition has no type or storage class
download_flash.c:4: warning: no previous prototype for ‘Download_Flash’
download_flash.c: In function ‘Download_Flash’:
download_flash.c:26: warning: implicit declaration of function ‘ReadFlash’
download_flash.c: At top level:
download_flash.c:56: warning: no previous prototype for ‘download_flash_start_thread’
download_flash.c: In function ‘download_flash_start_thread’:
download_flash.c:57: error: ‘FALSE’ undeclared (first use in this function)
download_flash.c:57: error: (Each undeclared identifier is reported only once
download_flash.c:57: error: for each function it appears in.)
download_flash.c:59: error: ‘TRUE’ undeclared (first use in this function)
download_flash.c: At top level:
download_flash.c:66: error: syntax error before ‘download_flash’
download_flash.c:66: error: syntax error before ‘*’ token
download_flash.c:68: warning: return type defaults to ‘int’
download_flash.c:68: warning: function declaration isn’t a prototype
download_flash.c: In function ‘download_flash’:
download_flash.c:70: error: ‘GError’ undeclared (first use in this function)
download_flash.c:70: error: ‘error’ undeclared (first use in this function)
download_flash.c:71: error: ‘FALSE’ undeclared (first use in this function)
download_flash.c:73: warning: implicit declaration of function ‘get_download_filename’
download_flash.c:73: warning: assignment makes pointer from integer without a cast
download_flash.c:77: warning: implicit declaration of function ‘g_thread_create’download_flash.c:77: error: ‘GThreadFunc’ undeclared (first use in this function)
download_flash.c:77: error: syntax error before ‘download_flash_start_thread’
download_flash.c:78: error: ‘a’ undeclared (first use in this function)
download_flash.c: At top level:
download_flash.c:78: error: syntax error before ‘while’
download_flash.c:79: warning: type defaults to ‘int’ in declaration of ‘EnableControls’
download_flash.c:79: warning: parameter names (without types) in function declaration
download_flash.c:79: error: conflicting types for ‘EnableControls’
globals.h:146: error: previous declaration of ‘EnableControls’ was here
download_flash.c:79: warning: data definition has no type or storage class
download_flash.c:80: error: syntax error before ‘return’
make: *** [download_flash.o] Error 1
crowell@ubuntu:~/pv2tool-for-linux$ make check
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
make: *** No rule to make target `check'.  Stop.
crowell@ubuntu:~/pv2tool-for-linux$ sudo make check
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
make: *** No rule to make target `check'.  Stop.

```

---

### Post by Mez on 2006-03-03
```
 sudo apt-get install libgtk2.0-dev
```

---

### Post by Ptero-4 on 2006-03-03
you need to install the gtk2 development packages (the development packages use the -dev suffix before the arch and filename suffix info).

Edit. Mez beated me by a split second.

---

