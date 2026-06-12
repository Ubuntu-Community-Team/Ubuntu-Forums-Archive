---
title: "Make problem"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Vinze on 2006-03-10
Hey, I tried to install GiftUI as the one that's in the Ubuntu repository always gives a segmentation fault (even on a fresh install), but I got the following results with make:
> $ make
Making all in data
make[1]: Entering directory `/home/vincent/installers/gift/giftui-0.4.1/data'
Making all in icons
make[2]: Entering directory `/home/vincent/installers/gift/giftui-0.4.1/data/icons'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/vincent/installers/gift/giftui-0.4.1/data/icons'
make[2]: Entering directory `/home/vincent/installers/gift/giftui-0.4.1/data'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/vincent/installers/gift/giftui-0.4.1/data'
make[1]: Leaving directory `/home/vincent/installers/gift/giftui-0.4.1/data'
Making all in po
make[1]: Entering directory `/home/vincent/installers/gift/giftui-0.4.1/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/vincent/installers/gift/giftui-0.4.1/po'
Making all in src
make[1]: Entering directory `/home/vincent/installers/gift/giftui-0.4.1/src'
make  all-am
make[2]: Entering directory `/home/vincent/installers/gift/giftui-0.4.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT configure.o -MD -MP -MF ".deps/configure.Tpo" \
          -c -o configure.o `test -f 'configure.c' || echo './'`configure.c; \
        then mv -f ".deps/configure.Tpo" ".deps/configure.Po"; \
        else rm -f ".deps/configure.Tpo"; exit 1; \
        fi
configure.c: In function ‘giftui_config_get_list’:
configure.c:126: warning: return from incompatible pointer type
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT event.o -MD -MP -MF ".deps/event.Tpo" \
          -c -o event.o `test -f 'event.c' || echo './'`event.c; \
        then mv -f ".deps/event.Tpo" ".deps/event.Po"; \
        else rm -f ".deps/event.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT io.o -MD -MP -MF ".deps/io.Tpo" \
          -c -o io.o `test -f 'io.c' || echo './'`io.c; \
        then mv -f ".deps/io.Tpo" ".deps/io.Po"; \
        else rm -f ".deps/io.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT main.o -MD -MP -MF ".deps/main.Tpo" \
          -c -o main.o `test -f 'main.c' || echo './'`main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
        else rm -f ".deps/main.Tpo"; exit 1; \
        fi
main.c: In function ‘giftui_init’:
main.c:196: warning: implicit declaration of function ‘bind_textdomain_codeset’
main.c:197: warning: implicit declaration of function ‘bindtextdomain’
main.c:198: warning: statement with no effect
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT util.o -MD -MP -MF ".deps/util.Tpo" \
          -c -o util.o `test -f 'util.c' || echo './'`util.c; \
        then mv -f ".deps/util.Tpo" ".deps/util.Po"; \
        else rm -f ".deps/util.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT gtkcellrendererprogress.o -MD -MP -MF ".deps/gtkcellrendererprogress.Tpo" \
          -c -o gtkcellrendererprogress.o `test -f 'gtkcellrendererprogress.c' || echo './'`gtkcellrendererprogress.c; \
        then mv -f ".deps/gtkcellrendererprogress.Tpo" ".deps/gtkcellrendererprogress.Po"; \
        else rm -f ".deps/gtkcellrendererprogress.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_parent.o -MD -MP -MF ".deps/ui_parent.Tpo" \
          -c -o ui_parent.o `test -f 'ui_parent.c' || echo './'`ui_parent.c; \
        then mv -f ".deps/ui_parent.Tpo" ".deps/ui_parent.Po"; \
        else rm -f ".deps/ui_parent.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_child.o -MD -MP -MF ".deps/ui_child.Tpo" \
          -c -o ui_child.o `test -f 'ui_child.c' || echo './'`ui_child.c; \
        then mv -f ".deps/ui_child.Tpo" ".deps/ui_child.Po"; \
        else rm -f ".deps/ui_child.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_menu.o -MD -MP -MF ".deps/ui_menu.Tpo" \
          -c -o ui_menu.o `test -f 'ui_menu.c' || echo './'`ui_menu.c; \
        then mv -f ".deps/ui_menu.Tpo" ".deps/ui_menu.Po"; \
        else rm -f ".deps/ui_menu.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_notebook.o -MD -MP -MF ".deps/ui_notebook.Tpo" \
          -c -o ui_notebook.o `test -f 'ui_notebook.c' || echo './'`ui_notebook.c; \
        then mv -f ".deps/ui_notebook.Tpo" ".deps/ui_notebook.Po"; \
        else rm -f ".deps/ui_notebook.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_about.o -MD -MP -MF ".deps/ui_about.Tpo" \
          -c -o ui_about.o `test -f 'ui_about.c' || echo './'`ui_about.c; \
        then mv -f ".deps/ui_about.Tpo" ".deps/ui_about.Po"; \
        else rm -f ".deps/ui_about.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_browse.o -MD -MP -MF ".deps/ui_browse.Tpo" \
          -c -o ui_browse.o `test -f 'ui_browse.c' || echo './'`ui_browse.c; \
        then mv -f ".deps/ui_browse.Tpo" ".deps/ui_browse.Po"; \
        else rm -f ".deps/ui_browse.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_connect.o -MD -MP -MF ".deps/ui_connect.Tpo" \
          -c -o ui_connect.o `test -f 'ui_connect.c' || echo './'`ui_connect.c; \
        then mv -f ".deps/ui_connect.Tpo" ".deps/ui_connect.Po"; \
        else rm -f ".deps/ui_connect.Tpo"; exit 1; \
        fi
ui_connect.c: In function ‘giftui_connect’:
ui_connect.c:69: warning: not enough variable arguments to fit a sentinel
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_icon.o -MD -MP -MF ".deps/ui_icon.Tpo" \
          -c -o ui_icon.o `test -f 'ui_icon.c' || echo './'`ui_icon.c; \
        then mv -f ".deps/ui_icon.Tpo" ".deps/ui_icon.Po"; \
        else rm -f ".deps/ui_icon.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_pref.o -MD -MP -MF ".deps/ui_pref.Tpo" \
          -c -o ui_pref.o `test -f 'ui_pref.c' || echo './'`ui_pref.c; \
        then mv -f ".deps/ui_pref.Tpo" ".deps/ui_pref.Po"; \
        else rm -f ".deps/ui_pref.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_search.o -MD -MP -MF ".deps/ui_search.Tpo" \
          -c -o ui_search.o `test -f 'ui_search.c' || echo './'`ui_search.c; \
        then mv -f ".deps/ui_search.Tpo" ".deps/ui_search.Po"; \
        else rm -f ".deps/ui_search.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_search_cb.o -MD -MP -MF ".deps/ui_search_cb.Tpo" \
          -c -o ui_search_cb.o `test -f 'ui_search_cb.c' || echo './'`ui_search_cb.c; \
        then mv -f ".deps/ui_search_cb.Tpo" ".deps/ui_search_cb.Po"; \
        else rm -f ".deps/ui_search_cb.Tpo"; exit 1; \
        fi
ui_search_cb.c:151: warning: ‘meta_print’ defined but not used
if gcc -DHAVE_CONFIG_H -I. -I. -I.     -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -MT ui_transfer.o -MD -MP -MF ".deps/ui_transfer.Tpo" \
          -c -o ui_transfer.o `test -f 'ui_transfer.c' || echo './'`ui_transfer.c; \
        then mv -f ".deps/ui_transfer.Tpo" ".deps/ui_transfer.Po"; \
        else rm -f ".deps/ui_transfer.Tpo"; exit 1; \
        fi
ui_transfer.c: In function ‘giftui_transfer_pause_iter’:
ui_transfer.c:321: error: ‘GtkCellRendererProgressColor’ undeclared (first use in this function)
ui_transfer.c:321: error: (Each undeclared identifier is reported only once
ui_transfer.c:321: error: for each function it appears in.)
ui_transfer.c:321: error: syntax error before ‘status’
ui_transfer.c:323: error: ‘status’ undeclared (first use in this function)
ui_transfer.c:325: error: ‘GTK_CELL_RENDERER_PROGRESS_CANCELED’ undeclared (first use in this function)
ui_transfer.c:329: error: ‘GTK_CELL_RENDERER_PROGRESS_PAUSED’ undeclared (first use in this function)
ui_transfer.c:331: error: ‘GTK_CELL_RENDERER_PROGRESS_ACTIVE’ undeclared (first use in this function)
make[2]: *** [ui_transfer.o] Error 1
make[2]: Leaving directory `/home/vincent/installers/gift/giftui-0.4.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/vincent/installers/gift/giftui-0.4.1/src'
make: *** [all-recursive] Error 1


I have no idea what to do...

---

### Post by cwaldbieser on 2006-03-11
[QUOTE=Vinze]Hey, I tried to install GiftUI as the one that's in the Ubuntu repository always gives a segmentation fault (even on a fresh install), but I got the following results with make:


I have no idea what to do...[/QUOTE]
I can't tell from the output if the configure script just didn't detect you were missing some header file or if there is a bug in the code.  You should probably just join the project mailing list or contact the author(s) and explain the problem.  It looks like it is just an undefined symbol and is probably not too hard to correct.

---

### Post by adamkane on 2006-03-11
Good advice. It looks like giftUI requires gtk+-2.5 and glib-2.5, and Breezy  is still using 2.0.
[http://giftui.sourceforge.net/download/]("http://giftui.sourceforge.net/download/")

---

### Post by Vinze on 2006-03-12
Yeah but that's for the CVS version I think.. 

Anyway, I read somewhere that the Debian version worked, so I installed that, and I got the following error when I tried to run giftUI: > $ giftui
giftui : No host to connect /apps/giftui/daemon/host.


---

### Post by adamkane on 2006-03-12
Apologies for asking a lame question, but isn't giftui available in universe? It's available through synaptic or apt-get on my machine.

---

### Post by Vinze on 2006-03-13
[QUOTE=adamkane]Apologies for asking a lame question, but isn't giftui available in universe? It's available through synaptic or apt-get on my machine.[/QUOTE]
> I tried to install GiftUI as the one that's in the Ubuntu repository always gives a segmentation fault

So yes, I tried to, but doesn't yours give a segmentation fault when you run it?

---

### Post by adamkane on 2006-03-13
I wasn't able to get giftui working with apt-get, but I was able to get giftui to work by installing it with klik:

[http://klik.atekon.de]("http://klik.atekon.de")
[http://giftui.klik.atekon.de]("http://giftui.klik.atekon.de")

Install gift and giftd. Run gift-setup once to see what options you need to setup. You need to have some ports open, so configure the necessary port forwards through your firewall if necessary. Run gift-setup again. Whenever gift-setup asks for your IP address, enter the IP address of your local machine 192.168.0.xxx, and enable the LAN interface, or keep LOCAL as the default if you are directly connected to the internet.

Summary:
Install gift and giftd.
Run gift-setup.
Run giftd -d.
Run klik giftui.

See:
[http://gentoo-wiki.com/HOWTO_giFT_p2p]("http://gentoo-wiki.com/HOWTO_giFT_p2p")

You may also want to try to install an RPM version of giftui with alien or install from source.

---

### Post by Vinze on 2006-03-13
[QUOTE=adamkane]I wasn't able to get giftui working with apt-get, but I was able to get giftui to work by installing it with klik:

[http://klik.atekon.de]("http://klik.atekon.de")
[http://giftui.klik.atekon.de]("http://giftui.klik.atekon.de")

Install gift and giftd. Run gift-setup once to see what options you need to setup. You need to have some ports open, so configure the necessary port forwards through your firewall if necessary. Run gift-setup again. Whenever gift-setup asks for your IP address, enter the IP address of your local machine 192.168.0.xxx, and enable the LAN interface, or keep LOCAL as the default if you are directly connected to the internet.

Summary:
Install gift and giftd.
Run gift-setup.
Run giftd -d.
Run klik giftui.

See:
[http://gentoo-wiki.com/HOWTO_giFT_p2p]("http://gentoo-wiki.com/HOWTO_giFT_p2p")

You may also want to try to install an RPM version of giftui with alien or install from source.[/QUOTE]
Yeah, I hadn't even thought of Klik, but it won't install: > $ wget klik.atekon.de/client/install -O -|sh
--16:14:34--  [http://klik.atekon.de/client/install](http://klik.atekon.de/client/install)
           => `-'
Resolving klik.atekon.de... 134.169.172.48
Connecting to klik.atekon.de|134.169.172.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,890 (15K) [text/plain]

100%[====================================>] 14,890        --.--K/s

16:14:34 (138.05 KB/s) - `-' saved [14890/14890]

sh: line 53: Xdialog: command not found


---

### Post by adamkane on 2006-03-13
Here is klik.atekon.de/client/install: 

```

#!/bin/bash

#
# klik 0.5.1 installer w/ cmg support
# GPL
# point-and-klik software installation
# by probono at myrealbox dot com
# thanks for valuable help from bfree and Kano
#

export PATH=/sbin:$PATH # Fedora needs this

# store the dir to return to it
ORIGDIR=$(pwd)
cd $HOME

if [ -z "$DIALOG" ] ; then
# Determine which dialog to use in which situation:
# Xdialog (in all other cases)
export DIALOG=Xdialog
# kdialog (in case there is no console available and we are running KDE)
pidof -x kdeinit >/dev/null && export DIALOG=kdialog 
# zenity (in case of GNOME)
pidof -x gnome-panel >/dev/null && export DIALOG=zenity
# dialog (in case there is a console available)
GUIMODE=$(tty)
( echo $GUIMODE | grep /dev/tty[:digit:] >/dev/null ) && export DIALOG=dialog
fi

# by Alexey
if test "$DISPLAY" == ""; then
DIALOG=dialog
fi

# Setup defaults for whatever dialog we are using
case $DIALOG in
 kdialog)
 DIALOG_OPTIONS=" --caption klik" ;
 KLIKDIR=":klikdir" ;;
 Xdialog|dialog)
 DIALOG_H=12
 DIALOG_W=60
 DIALOG_OPTIONS=" $DIALOG_H $DIALOG_W" ;
 KLIKDIR="~" ;;
esac

dmsgbox(){
case $DIALOG in
 zenity)
 zenity --info --text="$1" --title="klik"
 ;;
 *)
 $DIALOG --msgbox "$1" $DIALOG_OPTIONS
 ;;
 esac
}
dyesno(){
 $DIALOG --yesno "$1" $DIALOG_OPTIONS
}
dwarningyesno(){
 case $DIALOG in
 kdialog)
  $DIALOG --warningyesno "$1" $DIALOG_OPTIONS 
 ;;
 Xdialog|dialog)
  $DIALOG --yesno "Warning: $1" $DIALOG_OPTIONS 
 ;;
 esac
}
derror(){
 case $DIALOG in
 zenity)
 zenity --error --text="$1" --title="klik"
 ;;
 kdialog)
 $DIALOG --error "$1" $DIALOG_OPTIONS 
 ;;
 Xdialog|dialog)
 $DIALOG --msgbox "ERROR: $1" $DIALOG_OPTIONS 
 ;;
 esac
}

cat > $HOME/.klik <<\EOF
#!/bin/bash

# klik client 0.2
# GPL
# point-and-klik KDE software installation
# by probono at myrealbox dot com
# thanks to bfree for non-KDE part

export PATH=/sbin:$PATH # Fedora needs this

# try to get the human-readable version of the host OS
export VERSION=$(cat /etc/*-version 2>/dev/null | head -n 1)

#
# support different types of dialog, thanks bfree
#

if [ -z "$DIALOG" ] ; then
# Determine which dialog to use in which situation:
# Xdialog (in all other cases)
DIALOG=Xdialog
# kdialog (in case there is no console available and we are running KDE)
pidof -x kdeinit >/dev/null && DIALOG=kdialog 
# GNOME
pidof -x gnome-panel >/dev/null && DIALOG=zenity 
# dialog (in case there is a console available)
GUIMODE=$(tty)
( echo $GUIMODE | grep /dev/tty[:digit:] >/dev/null ) && DIALOG=dialog
fi

# by Alexey
if test "$DISPLAY" == ""; then
DIALOG=dialog
fi

export DIALOG

# Setup defaults for whatever dialog we are using
case $DIALOG in
 kdialog)
 DIALOG_OPTIONS=" --caption klik" ;
 KLIKDIR=":klikdir" ;;
 Xdialog|dialog)
 DIALOG_H=12
 DIALOG_W=60
 DIALOG_OPTIONS=" $DIALOG_H $DIALOG_W" ;
 KLIKDIR="~" ;;
esac

dmsgbox(){
 $DIALOG --msgbox "$1" $DIALOG_OPTIONS
}
dyesno(){
 $DIALOG --yesno "$1" $DIALOG_OPTIONS
}
dwarningyesno(){
 case $DIALOG in
 kdialog)
  $DIALOG --warningyesno "$1" $DIALOG_OPTIONS 
 ;;
 Xdialog|dialog)
  $DIALOG --yesno "Warning: $1" $DIALOG_OPTIONS 
 ;;
 esac
}
derror(){
 case $DIALOG in
 zenity)
 zenity --error --text="$1" --title="klik"
 ;;
 kdialog)
 $DIALOG --error "$1" $DIALOG_OPTIONS 
 ;;
 Xdialog|dialog)
 $DIALOG --msgbox "ERROR: $1" $DIALOG_OPTIONS 
 ;;
 esac
}
dexistingdir(){
 case $DIALOG in
 kdialog)
 $DIALOG --getexistingdirectory $KLIKDIR $DIALOG_OPTIONS 
 ;;
 Xdialog)
 $DIALOG --dselect $KLIKDIR $DIALOG_OPTIONS 
 ;;
 dialog)
 $DIALOG --fselect $KLIKDIR $DIALOG_OPTIONS
 ;;
 esac
}

# important to export those variables so that they can be accessed by the recipes
##export SUSE=$(cat /etc/SuSE-release 2>/dev/null | head -n 1 | cut -d \( -f 1) 2>/dev/null
UBUNTU=$(zcat /usr/share/doc/ubuntu-base/changelog.gz 2>/dev/null | head -n 1 | cut -d \; -f 1 ) 2>/dev/null
export UBUNTU=$(echo ${UBUNTU/ubuntu-meta/Ubuntu})
##export FEDORA=$(cat /etc/fedora-release 2>/dev/null | head -n 1)
export FEDORA=$(cat /etc/*release | tr -d [[:cntrl:]] 2>/dev/null)
export RUN=`echo $1 | sed s@klik:\/\/@@` && (wget -q http://134.169.172.48/apt/?package=$RUN -U "klik/0.1.3cli (`uname -a` @$VERSION$UBUNTU$SUSE$FEDORA@)" -O - | sh || derror "Error while trying to run $RUN" )

EOF
chmod 700 ~/.klik

#
# create helper protocol for konqueror to send klicks to the klik script
#

[ x"$KDEHOME" = x ] && KDEHOME=$HOME/.kde

mkdir -p $KDEHOME/share/services/
cat > ${KDEHOME}/share/services/klik.protocol <<EOF
# klik 0.2
# helper protocol for konqueror to send klicks to the klik script
# by probono
[Protocol]
exec=$HOME/.klik '%u'
protocol=klik
input=none
output=none
helper=true
listing=false
reading=false
writing=false
makedir=false
deleting=false
icon=package
Description=klik
EOF

#
# create ~/.kde/share/applnk/klik
#

mkdir -p  ${KDEHOME}/share/applnk/klik

cat > ${KDEHOME}/share/applnk/klik/.directory <<EOF
[Desktop Entry]
Encoding=UTF-8
Name=Applications (installed by klik)
Name[de]=Programme (installiert mit klik)
Icon=rebuild
#package_applications
EOF

#
# link to the store
#

cat > ${KDEHOME}/share/applnk/klik/klik.desktop <<EOF
[Desktop Entry]
Encoding=UTF-8
Exec=konqueror http://klik.atekon.de?from=profile
Icon=package_network
Name=Install more software...
Name[de]=Weitere Software installieren...
EOF


#
# set klik protocol handler in Mozilla (tested with Firefox 0.9.3)
#

PROFILES=$(find $HOME/.mozilla/ | grep prefs.js$)
if [ -z "$PROFILES" ]
then
dmsgbox "You need to start the mozilla/firefox browser once before running the klik installer if you want it to support klik.  If you do not use mozilla/firefox you can ignore this message.  If you plan on using mozilla/firefox with klik please run and exit the browser and then install klik again."
else
for i in $PROFILES
do
    USERJS="$(dirname "$i")/user.js"
    ( cat $USERJS 2>/dev/null | grep "klik" >/dev/null 2>&1 ) || ( echo "user_pref(\"network.protocol-handler.app.klik\", \"~/.klik\");" >> $USERJS )
done

( ps -d | grep mozilla ) && dmsgbox "You need to restart Mozilla/Firefox before you will be able to use klik there."
fi

#
# Add support for the klik protocol to elinks
#
[ -e $HOME/.elinks ] || mkdir -p $HOME/.elinks
[ -e $HOME/.elinks/elinks.conf ] || touch $HOME/.elinks/elinks.conf
cat >> $HOME/.elinks/elinks.conf <<EOF

## protocol
## protocol.user 
## protocol.user.klik 
## protocol.user.klik._template_ <str> 
set protocol.user.klik._template_ = "" 
## protocol.user.klik.unix <str> 
set protocol.user.klik.unix = "~/.klik %h" 
## protocol.user.klik.unix-xwin <str> 
set protocol.user.klik.unix-xwin = "~/.klik %h"
EOF

#
DESCRIPTION="EXPERIMENTAL implementation of cmg-compressed AppDirs (AppImages, really) for klik. Using this technology, every app is contained inside one file that is mounted and unmounted transparently on demand."
#

mkdir -p ${KDEHOME}/share/mimelnk/all
cat > ${KDEHOME}/share/mimelnk/all/cmg.desktop <<\EOF
[Desktop Entry]
Comment=
Hidden=false
Icon=view_remove
MimeType=application/x-extension-cmg
Patterns=*.cmg
Type=MimeType
EOF

mkdir -p ${KDEHOME}/share/applnk/.hidden
cat > ${KDEHOME}/share/applnk/.hidden/AppRun.desktop<<\EOF
[Desktop Entry]
Comment=
Exec=$HOME/.zAppRun %U
Icon=view_remove
InitialPreference=2
MimeType=application/x-extension-cmg;Application
Name=
ServiceTypes=
Terminal=false
Type=Application
EOF

cat > $HOME/.zAppRun <<\EOF
#!/bin/bash

# by probono at myrealbox dot com
# thanks to bfree
# GPL

export PATH=/sbin:$PATH # Fedora needs this

#
# ok we need dialogs now
#
if [ -z "$DIALOG" ] ; then
# Determine which dialog to use in which situation:
# Xdialog (in all other cases)
export DIALOG=Xdialog
# kdialog (in case there is no console available and we are running KDE)
pidof -x kdeinit >/dev/null && export DIALOG=kdialog
pidof -x gnome-panel > /dev/null && export DIALOG=zenity 
# dialog (in case there is a console available)
GUIMODE=$(tty)
( echo $GUIMODE | grep /dev/tty[:digit:] >/dev/null ) && export DIALOG=dialog
fi

# by Alexey
if test "$DISPLAY" == ""; then
DIALOG=dialog
fi

# Setup defaults for whatever dialog we are using
case $DIALOG in
 kdialog)
 DIALOG_OPTIONS=" --caption klik" ;
 KLIKDIR=":klikdir" ;;
 Xdialog|dialog)
 DIALOG_H=12
 DIALOG_W=60
 DIALOG_OPTIONS=" $DIALOG_H $DIALOG_W" ;
 KLIKDIR="~" ;;
esac

derror(){
 case $DIALOG in
 zenity)
 $DIALOG --error --text "$1" --title="klik"
 ;;
 kdialog)
 $DIALOG --error "$1" $DIALOG_OPTIONS 
 ;;
 Xdialog|dialog)
 $DIALOG --msgbox "ERROR: $1" $DIALOG_OPTIONS 
 ;;
 esac
}

# check fstab and warn if neccessary entries are not there
# better use /media/klik according to FSH?
if [ -z "$(cat /etc/fstab | grep app/7)" ]
then
  derror "Your /etc/fstab is not yet prepared for mounting .cmg images. 
  As root, please make /tmp/app writeable and add the following lines:
  
  ################################################################
/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
################################################################"
  exit 1
fi

# rewrite cmdline to use absolute instead of relative paths, thanks bfree
NEWCMD=$(perl -e '$newcmd=shift(@ARGV);foreach $arg (@ARGV){ @part=split(/\=/,$arg); foreach $part (@part){ (-e "$ENV{PWD}/$part") && ($part="$ENV{PWD}/$part");}$newcmd.=" ".join ("=",@part);} print "$newcmd";' $@)
set -- $NEWCMD

# if no arguments are passed and 
# there is a .cmg in the same directory as this
# script, then use the .cmg
DIRNAME=$(dirname $0)
if [ -z $1 ]
then
  CMG=$(find "$DIRNAME" -iname '*.cmg'|head -n 1) || exit 1
  echo "Found $CMG, using it"
else
  CMG="$1"
  shift
fi

# make path to CMG absolute, thanks bfree
case $CMG in
/*) ;; 
*) CMG=$(pwd)/$CMG ;; 
esac

# determine which filesystem is used as .cmg
#file $CMG | grep ": data" >/dev/null && FS=squash # who knows a better way to recognize it?
##file $CMG | grep "Compressed ROM" >/dev/null && FS=cram
##file $CMG | grep "ISO 9660" >/dev/null && FS=iso

##if [ -n "$FS" ]
##then
  NUMBERS="7 6 5 4 3 2 1"
  for NUMBER in $NUMBERS
    do
    [ -e "/tmp/app/$NUMBER" ] || MNTNUM=$NUMBER
  done
  case $FS in
    squash) MOUNT=/tmp/squash/$MNTNUM ;;
    *) MOUNT=/tmp/app/$MNTNUM ;;
  esac
  mkdir -p $MOUNT || exit 1
  ln -s $CMG $MOUNT/image || exit 1
  mount $MOUNT || derror "Unable to mount $MOUNT"
##else
##  # NOTE: exit now cause our cmg isn't mounted
##  derror "$CMG does not appear to be either a squashfs, iso9660 or a cramfs file"
##  exit 1
##fi
    
  #
  # execute the wrapper
  # the wrapper should take care to keep running until its app closes
  #
  
  # we need this so that on the cmdline, pipes etc work
  CMDLINE="yes"
  ( tty | grep ^/dev/tty >/dev/null ) && CMDLINE=""
  ( tty | grep ^/dev/pts >/dev/null ) && CMDLINE=""
  if [ "$CMDLINE" = "yes" ] ; then
    RESULT=$($MOUNT/wrapper $@ 2>&1) || derror "$RESULT" 
  else
    $MOUNT/wrapper $@
  fi

  # kill all child processes
  # kill $(pidof -x -o %PPID $!) # 2>/dev/null
  
  # unmount and clean up
  umount $MOUNT
  rm -f $MOUNT/image
  rm -r $MOUNT/
    
    ##################
    # update klik menu
    
    CMGDIR=$(dirname $CMG)
    [ x"$KDEHOME" = x ] && KDEHOME=$HOME/.kde

    # find cmg files
    CMGFILES=$(find $CMGDIR/*.cmg 2>/dev/null)
    
    # remove old menu entries
    rm -rf ${KDEHOME}/share/applnk/klik/*.cmg.desktop
    
    # create new menu entries
    for CMGFILE in $CMGFILES
    do
    #echo $CMGFILE
    BASENAME=$(basename "$CMGFILE")
    APPNAME=$(echo $BASENAME | sed 's/.cmg//g' | cut -d _ -f 1)
    firstchar=${APPNAME:0:1}   # First character.
    restchar=${APPNAME:1}       # Rest of string(s).
    firstchar=$(echo "$firstchar" | tr a-z A-Z)
    APPNAME=$firstchar$restchar
    cat > $KDEHOME/share/applnk/klik/$BASENAME.desktop <<EOmooF
    [Desktop Entry]
    Encoding=UTF-8
    Type=Application
    Exec=$HOME/.zAppRun $CMGFILE
    Icon=
    Name=$APPNAME
EOmooF
    done
EOF

chmod 777 $HOME/.zAppRun 

#
# Create the script for root to install cmg support
#

if [ -z "$(cat /etc/fstab | grep app/7)" ]
then

cat > "$HOME/klik-cmg-install-root" <<EOF
#!/bin/bash
echo >> /etc/fstab "
/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
"
if ! [ -e /tmp/app ]
then
mkdir -p /tmp/app
chmod 0777 /tmp/app
#dmsgbox "/tmp/app has been created so it can be used by anyone. You may want to make /tmp/app only writable by one group (like users) which you could do with: \nchgrp users /tmp/app \nchmod 770 /tmp/app\"
fi
EOF
chmod 777 "$HOME/klik-cmg-install-root"

(sudo sh "$HOME/klik-cmg-install-root" && rm -f "$HOME/klik-cmg-install-root") || (dmsgbox "Your /etc/fstab is not setup to use cmg files. Please run $HOME/klik-cmg-install-root as root.") 
fi

#
#
#

case $DIALOG in
Xdialog) BROWSER="firefox http://klik.atekon.de?from=profile" ;;
zenity) BROWSER="firefox http://klik.atekon.de?from=profile" ;;
dialog) BROWSER="elinks http://klik.atekon.de?from=profile" ;;
*) BROWSER="konqueror http://klik.atekon.de?from=profile" ;;
esac

kbuildsycoca 2>/dev/null
dmsgbox "Now you can start installing software. \n Opening the klik point-and-klik software store..." && $BROWSER &

cd $ORIGDIR

#
# GNOME support for cmg - added by probono Aug 21, 2005
#

# how to make $HOME variable here?
mkdir -p $HOME/.local/share/applications/
cat > $HOME/.local/share/applications/.zAppRun.desktop << EOF
[Desktop Entry]
Encoding=UTF-8
Name=.zAppRun
MimeType=application/x-extension-cmg;
Exec='$HOME/.zAppRun'
Type=Application
Terminal=false
NoDisplay=true
EOF

mkdir -p $HOME/.local/share/mime/packages/
cat > $HOME/.local/share/mime/packages/Override.xml << EOF
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
 <mime-type type="application/x-extension-cmg"><comment>Compressed Application Image</comment><glob pattern="*.cmg"/></mime-type>
</mime-info>
EOF

update-mime-database ~/.local/share/mime/ >/dev/null  2>&1
update-desktop-database -v ~/.local/share/applications/ >/dev/null 2>&1

mkdir -p $HOME/.local/share/applications $HOME/.gnome2/vfolders/applications  2>/dev/null
 ln -sf $KDEHOME/share/applnk/klik $HOME/.local/share/applications 2>/dev/null
 ln -s $KDEHOME/share/applnk/klik $HOME/.gnome2/vfolders/applications 2>/dev/null

```

Line 53 says:

```

$DIALOG --msgbox "$1" $DIALOG_OPTIONS

```

Do you have zenity, dialog and xdialog installed?

---

### Post by Vinze on 2006-03-14
I only had Zenity, I installed the others and now it works, thanks :D 

I would never have found that :P 

Anyway, it now runs but can't connect, however, it seems that it isn't as feature complete as I thought it was :P

---

