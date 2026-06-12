---
title: "banshee alarm plugin trouble"
date: 2009-01-05
forum: General Help
---

### Post by nkobel003 on 2009-01-05
Hello everyone! I'm trying to install the alarm extension for banshee, but I keep getting a weird error/return that I have no idea what to do. Here is what I've done so far after unzipping the tar.gz file to /home/user/Public folder via drag and drop.

**./configure**
```
mannequin@NAMELESS:~/Public/banshee-alarm-extension-0.4.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.35.0... 0.37.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO_MODULE... yes
checking for gmcs... /usr/bin/gmcs
checking for mono... /usr/bin/mono
checking for BANSHEE... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating build/Makefile
config.status: creating src/Makefile
config.status: creating src/AssemblyInfo.cs
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
# INTLTOOL_MAKEFILE

Extension will be installed in /usr/local/lib/banshee-1/Extensions

```

**make**
```
mannequin@NAMELESS:~/Public/banshee-alarm-extension-0.4.2$ make
Making all in build
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
Making all in po
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/po'
Making all in src
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
/usr/bin/gmcs -debug -out:Banshee.AlarmClock.dll -target:library -r:/usr/lib/banshee-1/Banshee.Widgets.dll -r:/usr/lib/banshee-1/Banshee.ThickClient.dll -r:/usr/lib/banshee-1/Banshee.Services.dll -r:Mono.Cairo -r:/usr/lib/banshee-1/Hyena.Gui.dll -r:/usr/lib/banshee-1/Banshee.Core.dll -r:System -r:/usr/lib/banshee-1/Mono.Media.dll -r:/usr/lib/cli/taglib-sharp-2.0/taglib-sharp.dll -r:/usr/lib/cli/ndesk-dbus-1.0/NDesk.DBus.dll -r:/usr/lib/cli/ndesk-dbus-glib-1.0/NDesk.DBus.GLib.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll -r:/usr/lib/cli/mono-addins-0.2/Mono.Addins.dll -r:System.Data -r:Mono.Data.SqliteClient -r:Mono.Posix -r:/usr/lib/banshee-1/Hyena.dll -r:/usr/lib/banshee-1/MusicBrainz.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll    -resource:./Banshee.AlarmClock.addin.xml,Banshee.AlarmClock.addin.xml  -resource:./AlarmMenu.xml,AlarmMenu.xml ./Alarm.cs ./AlarmClockService.cs ./AlarmConfigDialog.cs ./ConfigurationDialog.cs ./ConfigurationSchema.cs ./SleepTimerConfigDialog.cs ./VolumeFade.cs ./AssemblyInfo.cs
if test -w banshee-plugin-alarm.schemas.in -o \( ! -e banshee-plugin-alarm.schemas.in -a -w . \); then \
		/usr/bin/mono /usr/lib/banshee-1/gconf-schema-extractor.exe Banshee.AlarmClock.dll ./banshee-plugin-alarm.schemas.in; \
	fi
LC_ALL=C /usr/bin/intltool-merge -s -u -c ../po/.intltool-merge-cache ../po banshee-plugin-alarm.schemas.in banshee-plugin-alarm.schemas
Found cached translation database
Merging translations into banshee-plugin-alarm.schemas.
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2'

```

**sudo make install**
```
mannequin@NAMELESS:~/Public/banshee-alarm-extension-0.4.2$ make install
Making install in build
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
make[2]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
Making install in po
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/po'
linguas="fr "; \
	for lang in $linguas; do \
	  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
	  /bin/sh /home/mannequin/Public/banshee-alarm-extension-0.4.2/install-sh -d $dir; \
	  if test -r $lang.gmo; then \
	    /usr/bin/install -c -m 644 $lang.gmo $dir/banshee-alarm-plugin.mo; \
	    echo "installing $lang.gmo as $dir/banshee-alarm-plugin.mo"; \
	  else \
	    /usr/bin/install -c -m 644 ./$lang.gmo $dir/banshee-alarm-plugin.mo; \
	    echo "installing ./$lang.gmo as" \
		 "$dir/banshee-alarm-plugin.mo"; \
	  fi; \
	  if test -r $lang.gmo.m; then \
	    /usr/bin/install -c -m 644 $lang.gmo.m $dir/banshee-alarm-plugin.mo.m; \
	    echo "installing $lang.gmo.m as $dir/banshee-alarm-plugin.mo.m"; \
	  else \
	    if test -r ./$lang.gmo.m ; then \
	      /usr/bin/install -c -m 644 ./$lang.gmo.m \
		$dir/banshee-alarm-plugin.mo.m; \
	      echo "installing ./$lang.gmo.m as" \
		   "$dir/banshee-alarm-plugin.mo.m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
/usr/bin/install: cannot remove `/usr/local/share/locale/fr/LC_MESSAGES/banshee-alarm-plugin.mo': Permission denied
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/banshee-alarm-plugin.mo
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/po'
Making install in src
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[2]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[2]: Nothing to be done for `install-exec-am'.
if [ -z "" ]; then \
		GCONF_CONFIG_SOURCE="" /usr/bin/gconftool-2 --makefile-install-rule banshee-plugin-alarm.schemas; \
	fi
Attached schema `/schemas/apps/banshee/plugins/alarm/alarm_command' to key `/apps/banshee/plugins/alarm/alarm_command'
Installed schema `/schemas/apps/banshee/plugins/alarm/alarm_command' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/alarm_hour' to key `/apps/banshee/plugins/alarm/alarm_hour'
Installed schema `/schemas/apps/banshee/plugins/alarm/alarm_hour' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/alarm_minute' to key `/apps/banshee/plugins/alarm/alarm_minute'
Installed schema `/schemas/apps/banshee/plugins/alarm/alarm_minute' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/fade_duration' to key `/apps/banshee/plugins/alarm/fade_duration'
Installed schema `/schemas/apps/banshee/plugins/alarm/fade_duration' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/fade_end_volume' to key `/apps/banshee/plugins/alarm/fade_end_volume'
Installed schema `/schemas/apps/banshee/plugins/alarm/fade_end_volume' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/fade_start_volume' to key `/apps/banshee/plugins/alarm/fade_start_volume'
Installed schema `/schemas/apps/banshee/plugins/alarm/fade_start_volume' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/is_enabled' to key `/apps/banshee/plugins/alarm/is_enabled'
Installed schema `/schemas/apps/banshee/plugins/alarm/is_enabled' for locale `C'
test -z "/usr/local/lib/banshee-1/Extensions" || /bin/mkdir -p "/usr/local/lib/banshee-1/Extensions"
 /usr/bin/install -c 'Banshee.AlarmClock.dll' '/usr/local/lib/banshee-1/Extensions/Banshee.AlarmClock.dll'
/usr/bin/install: cannot remove `/usr/local/lib/banshee-1/Extensions/Banshee.AlarmClock.dll': Permission denied
 /usr/bin/install -c 'Banshee.AlarmClock.dll.mdb' '/usr/local/lib/banshee-1/Extensions/Banshee.AlarmClock.dll.mdb'
/usr/bin/install: cannot remove `/usr/local/lib/banshee-1/Extensions/Banshee.AlarmClock.dll.mdb': Permission denied
make[2]: *** [install-pluginSCRIPTS] Error 1
make[2]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make: *** [install-recursive] Error 1
mannequin@NAMELESS:~/Public/banshee-alarm-extension-0.4.2$ sudo make install
Making install in build
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
make[2]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/build'
Making install in po
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/po'
linguas="fr "; \
	for lang in $linguas; do \
	  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
	  /bin/sh /home/mannequin/Public/banshee-alarm-extension-0.4.2/install-sh -d $dir; \
	  if test -r $lang.gmo; then \
	    /usr/bin/install -c -m 644 $lang.gmo $dir/banshee-alarm-plugin.mo; \
	    echo "installing $lang.gmo as $dir/banshee-alarm-plugin.mo"; \
	  else \
	    /usr/bin/install -c -m 644 ./$lang.gmo $dir/banshee-alarm-plugin.mo; \
	    echo "installing ./$lang.gmo as" \
		 "$dir/banshee-alarm-plugin.mo"; \
	  fi; \
	  if test -r $lang.gmo.m; then \
	    /usr/bin/install -c -m 644 $lang.gmo.m $dir/banshee-alarm-plugin.mo.m; \
	    echo "installing $lang.gmo.m as $dir/banshee-alarm-plugin.mo.m"; \
	  else \
	    if test -r ./$lang.gmo.m ; then \
	      /usr/bin/install -c -m 644 ./$lang.gmo.m \
		$dir/banshee-alarm-plugin.mo.m; \
	      echo "installing ./$lang.gmo.m as" \
		   "$dir/banshee-alarm-plugin.mo.m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/banshee-alarm-plugin.mo
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/po'
Making install in src
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[2]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[2]: Nothing to be done for `install-exec-am'.
if [ -z "" ]; then \
		GCONF_CONFIG_SOURCE="" /usr/bin/gconftool-2 --makefile-install-rule banshee-plugin-alarm.schemas; \
	fi
Attached schema `/schemas/apps/banshee/plugins/alarm/alarm_command' to key `/apps/banshee/plugins/alarm/alarm_command'
Installed schema `/schemas/apps/banshee/plugins/alarm/alarm_command' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/alarm_hour' to key `/apps/banshee/plugins/alarm/alarm_hour'
Installed schema `/schemas/apps/banshee/plugins/alarm/alarm_hour' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/alarm_minute' to key `/apps/banshee/plugins/alarm/alarm_minute'
Installed schema `/schemas/apps/banshee/plugins/alarm/alarm_minute' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/fade_duration' to key `/apps/banshee/plugins/alarm/fade_duration'
Installed schema `/schemas/apps/banshee/plugins/alarm/fade_duration' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/fade_end_volume' to key `/apps/banshee/plugins/alarm/fade_end_volume'
Installed schema `/schemas/apps/banshee/plugins/alarm/fade_end_volume' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/fade_start_volume' to key `/apps/banshee/plugins/alarm/fade_start_volume'
Installed schema `/schemas/apps/banshee/plugins/alarm/fade_start_volume' for locale `C'
Attached schema `/schemas/apps/banshee/plugins/alarm/is_enabled' to key `/apps/banshee/plugins/alarm/is_enabled'
Installed schema `/schemas/apps/banshee/plugins/alarm/is_enabled' for locale `C'
test -z "/usr/local/lib/banshee-1/Extensions" || /bin/mkdir -p "/usr/local/lib/banshee-1/Extensions"
 /usr/bin/install -c 'Banshee.AlarmClock.dll' '/usr/local/lib/banshee-1/Extensions/Banshee.AlarmClock.dll'
 /usr/bin/install -c 'Banshee.AlarmClock.dll.mdb' '/usr/local/lib/banshee-1/Extensions/Banshee.AlarmClock.dll.mdb'
test -z "/usr/local/etc/gconf/schemas" || /bin/mkdir -p "/usr/local/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'banshee-plugin-alarm.schemas' '/usr/local/etc/gconf/schemas/banshee-plugin-alarm.schemas'
make[2]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2/src'
make[1]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2'
make[2]: Entering directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2'
make[1]: Leaving directory `/home/mannequin/Public/banshee-alarm-extension-0.4.2'

```

What's going on? How do I fix this? I just want to wake up in the morning, lol. Thank you!

---

### Post by Tim Sharitt on 2009-01-06
I'm not sure I see the problem. The errors you got from "make install" were because you didn't have permissions to edit the filed, but running "sudo make install" solved that problem. Are you getting errors when trying to run it banshee?

---

### Post by nkobel003 on 2009-01-07
Woops. It was giving me a different error, though. I upgraded to 8.10 but I still get the error, except now it's different. I'm getting the same error as in this thread [http://ubuntuforums.org/showthread.php?p=6511408](http://ubuntuforums.org/showthread.php?p=6511408), so I'll just continue it there.

---

### Post by nkobel003 on 2009-06-27
works on upgrade :D

---

### Post by coolen on 2009-08-26
Hey, this post is kind of old, but I'm trying to build this myself.

You said you had success. Was that using Jaunty? Did you, by any chance, come up with an error during ./configure about mono not being found?

```
checking for MONO_MODULE... configure: error: Package requirements (mono >= 1.2.5) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I'm running Banshee 1.4.3, if it makes any difference.

---

### Post by afrodeity on 2010-04-26
Anyone know how to start banshee without plugins? I think one of them is freezing the app.

---

