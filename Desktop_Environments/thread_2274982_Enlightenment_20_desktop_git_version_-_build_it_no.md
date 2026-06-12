---
title: "Enlightenment 20 desktop git version - build it now!"
date: 2015-04-23
forum: Desktop Environments
---

### Post by batden on 2015-04-23
[INDENT]                     [COLOR=#ff0000]_DISCONTINUED DUE TO LACK OF COMMUNITY INTEREST_[/COLOR]
[FONT=Ubuntu][SIZE=2]
[COLOR=#008000]But still being deve[/COLOR][/SIZE][/FONT][FONT=Ubuntu][SIZE=2][COLOR=#008000]loped   [/COLOR][/SIZE][/FONT][FONT=Ubuntu][SIZE=2]):P[/SIZE][/FONT][FONT=Ubuntu][SIZE=2] 
[COLOR=#008000]Here you go:[/COLOR]

[[COLOR=#008000]http://build-enlightenment.monsite-orange.fr/[/COLOR]]("http://build-enlightenment.monsite-orange.fr/")

[COLOR=#ffffff][/COLOR][COLOR=#ffffff]_______________________________________________________________[/COLOR]

E20 build scripts for Ubuntu Trusty and Ubuntu Wily.[/SIZE][/FONT][COLOR=#008000][FONT=Ubuntu][SIZE=2]

[/SIZE][/FONT][/COLOR][FONT=Ubuntu][SIZE=2]_Bash scripts_[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]

The scope of these scripts is limited to the Intel 32/64-bit x86 architecture.

[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]Download [/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]. . .

[/SIZE][/FONT][COLOR=#000000][FONT=Ubuntu][SIZE=2]GnuPG-signed[/SIZE][/FONT][/COLOR][FONT=Ubuntu][SIZE=2] script for [/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]Ubuntu 14.04.4 LTS [/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2](save file):
[https://dl.dropboxusercontent.com/u/58695863/twenty.sh.gpg](https://dl.dropboxusercontent.com/u/58695863/twenty.sh.gpg)
[/SIZE][/FONT][COLOR=#008000][FONT=Ubuntu][SIZE=2]**[Final version:  1.3]**

[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][SIZE=2]GnuPG-signed[/SIZE][/FONT][/COLOR][FONT=Ubuntu][SIZE=2] script for [/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]Ubuntu 15.10[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2] with systemd support (save file):
[https://dl.dropboxusercontent.com/u/58695863/twentywil.sh.gpg](https://dl.dropboxusercontent.com/u/58695863/twentywil.sh.gpg)[/SIZE][/FONT][COLOR=#008000][FONT=Ubuntu][SIZE=2]
**[Final version:  1.2]**[/SIZE][/FONT][/COLOR][COLOR=#008000][FONT=Ubuntu][SIZE=2]
[/SIZE][/FONT][/COLOR][FONT=Ubuntu][SIZE=2]
[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]Access . . .[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]

Open GNOME Terminal, change (cd) to the download folder,
copy and paste the appropriate command to access the file:

gpg --output twenty.sh --decrypt twenty.sh.gpg
[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]or[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]
gpg --output twentywil.sh --decrypt twentywil.sh.gpg

[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]Use . . .[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]

1. In [/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]GNOME Terminal[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]

[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]14.04 LTS[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]: Edit > Profile Preferences > Scrolling > set Scrollback to 'Unlimited'
[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]15.10[/SIZE][/FONT]**[FONT=Ubuntu][SIZE=2]: Edit > Profile Preferences > Scrolling > uncheck 'Limit scrollback to'

2. Make the script executable with

chmod +x ./twenty.sh
[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]or[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]
chmod +x ./twentywil.sh

3. Run it with

./twenty.sh
[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]or[/SIZE][/FONT]*[FONT=Ubuntu][SIZE=2]
./twentywil.sh

[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]
[/SIZE][/FONT][FONT=Ubuntu][SIZE=2][U]Useful links

[/U][/SIZE][/FONT][FONT=Ubuntu][SIZE=2][URL="https://www.enlightenment.org/"]https://www.enlightenment.org/
[/URL][https://git.enlightenment.org/](https://git.enlightenment.org/)[URL="http://e17-stuff.org/index.php?xcontentmode=7000"]
[/URL][/SIZE][/FONT][https://phab.enlightenment.org/w/](https://phab.enlightenment.org/w/)[FONT=Ubuntu][SIZE=2]
[https://www.mail-archive.com/enlightenment-users@lists.sourceforge.net/maillist.html](https://www.mail-archive.com/enlightenment-users@lists.sourceforge.net/maillist.html)
[/SIZE][/FONT][COLOR=#008000][FONT=Ubuntu][SIZE=2][https://www.mail-archive.com/enlightenment-devel@lists.sourceforge.net/maillist.html](https://www.mail-archive.com/enlightenment-devel@lists.sourceforge.net/maillist.html)
[/SIZE][/FONT][/COLOR][FONT=Ubuntu][SIZE=2][https://phab.enlightenment.org/w/e_configuration_options_compendium/](https://phab.enlightenment.org/w/e_configuration_options_compendium/)
[URL="http://www.bodhilinux.com/w/bodhi-linux-how-to/"]http://www.bodhilinux.com/w/bodhi-linux-how-to
[/URL]  [/SIZE][/FONT]      [irc://irc.freenode.net/e](irc://irc.freenode.net/e)

[/INDENT]

---

### Post by matt_symes on 2015-04-23
Hi

> gpg --output nineteen.sh --decrypt nineteen.sh.gpg
*or*
gpg --output nineteenviv.sh --decrypt nineteenviv.sh.gpg

...and i get the public key from where ?

Why are the scripts encrypted ?

Kind regards

---

### Post by batden on 2015-04-23
You don't need the public key to access the files, it's purely optional.

See the screenshots section (batden-pubkey.png) for info.

---

### Post by batden on 2015-04-23
The new scripts will be uploaded soon... Please be patient.

---

### Post by matt_symes on 2015-04-23
Hi

> **batden said:**
> You don't need the public key to access the files, it's purely optional.

See the screenshots section (batden-pubkey.png) for info.

Excellent. I should have checked before posting. I'll give it a try :)

Kind regards

---

### Post by batden on 2015-04-23
Upload problem fixed.
New scripts now online (see first post).

Enjoy!

---

### Post by batden on 2015-04-25
Screencast \\:D/

Medium quality (17.9 MB):
[http://dazibao.perso.sfr.fr/Vids/E20.mp4](http://dazibao.perso.sfr.fr/Vids/E20.mp4)

High-quality (61.4 MB):
[http://dazibao.perso.sfr.fr/Vids/E20.mkv](http://dazibao.perso.sfr.fr/Vids/E20.mkv)

---

### Post by Dr.InSide on 2015-05-05
(sorry for my bad English)

I am not a Linux expert, but I hope you can help me ...

My Ubuntu-Version:  Xubuntu 15.04 (German)

I get the following error when I start the script:


```


------------------------------------------------------------------------
emotion_generic_players 1.14.0-beta3
------------------------------------------------------------------------

Configuration Options Summary:
  Build Profile..........: dev

Players:
  VLC....................: yes

Compilation..............: make (or gmake)
  CPPFLAGS...............: -I/usr/local/include
  CFLAGS.................: -g -O2
  CXXFLAGS...............: 
  LDFLAGS................: -L/usr/local/lib

Installation.............: make install (as root if needed, with 'su' or 'sudo')
  prefix.................: /usr/local
  emotion generic players: /usr/local/lib/emotion/generic_players/v-1.14


make -j 4 --no-print-directory all-am
  CC       src/vlc/src_vlc_vlc-emotion_generic_vlc.o
  CCLD     src/vlc/vlc
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `_eo_add_end'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_event_freeze_count_get'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_constructor'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `_eo_call_resolve'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_hook_call_post'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `_eo_add_internal_start'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `_eo_do_end'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_parent_set'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_finalize'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_event_thaw'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_event_callback_call'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_destructor'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_event_freeze'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `_eo_do_start'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `_eo_api_op_id_get'
/usr/local/lib/libecore.so: Nicht definierter Verweis auf `eo_hook_call_pre'
collect2: error: ld returned 1 exit status
Makefile:447: recipe for target 'src/vlc/vlc' failed
make[1]: *** [src/vlc/vlc] Error 1
Makefile:340: recipe for target 'all' failed
make: *** [all] Error 2

  BUILD ERROR - TRY AGAIN LATER. 
 

```

---

### Post by batden on 2015-05-05
Weird, everything builds fine here (Ubuntu 14.04 and 15.04).

```
------------------------------------------------------------------------
emotion_generic_players 1.14.0-beta3
------------------------------------------------------------------------

Configuration Options Summary:
  Build Profile..........: dev

Players:
  VLC....................: yes

Compilation..............: make (or gmake)
  CPPFLAGS...............: -I/usr/local/include
  CFLAGS.................: -g -O2
  CXXFLAGS...............: 
  LDFLAGS................: -L/usr/local/lib

Installation.............: make install (as root if needed, with 'su' or 'sudo')
  prefix.................: /usr/local
  emotion generic players: /usr/local/lib/emotion/generic_players/v-1.14


make -j 4 --no-print-directory all-am
  CC       src/vlc/src_vlc_vlc-emotion_generic_vlc.o
  CCLD     src/vlc/vlc
make[1]: Nothing to be done for `install-exec-am'.
 /bin/mkdir -p '/usr/local/lib/emotion/generic_players/v-1.14'
  /usr/bin/install -c src/vlc/vlc '/usr/local/lib/emotion/generic_players/v-1.14'
```

Did you relaunch the script?

Please post the output of the following command if you are still getting the same error:
dpkg -s libvlc-dev | grep Version

---

### Post by Dr.InSide on 2015-05-06
I have the script restart several times. It always ended at this point.

```

[COLOR=#000000]dpkg -s libvlc-dev | grep Version
[/COLOR]Version: 2.2.0-1

```

Addendum: 
I have now removed libvlc-dev manually and then the script restarted. 
It has libvlc-dev reinstalled. But the script ends at the same point.

---

### Post by titiou on 2015-05-06
Hello [COLOR=#000000]batden thank you for your script
I wanted to use your script on PclinuxOs, I've tested but I've always this error:
[/COLOR]```
[COLOR=#000000][FONT=dejavu sans mono]/bin/grep: /usr/lib/libFLAC.la: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]/bin/sed: can't read /usr/lib/libFLAC.la: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libtool: link: `/usr/lib/libFLAC.la' is not a valid libtool archive[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:14432: recipe for target 'lib/ecore_audio/libecore_audio.la' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[4]: *** [lib/ecore_audio/libecore_audio.la] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[4]: *** Waiting for unfinished jobs....[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:33789: recipe for target 'all-recursive' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[3]: *** [all-recursive] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:11962: recipe for target 'all' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[2]: *** [all] Error 2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:2437: recipe for target 'all-recursive' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: *** [all-recursive] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:1582: recipe for target 'all' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make: *** [all] Error 2[/FONT][/COLOR]
```
I've you some ideas? It's a missing librarie? I've tested withe easy_efl and I've the same error.
If you can help me it's very cool.
No error on ubuntu Thank you for your job

---

### Post by batden on 2015-05-06
**@ Dr.InSide**

I have updated the script (delete the old one) with an option to disable vlc support.

Get it here:
[http://dazibao.perso.sfr.fr/Scripts/twentyviv.sh.gpg](http://dazibao.perso.sfr.fr/Scripts/twentyviv.sh.gpg)

Please test and report back!

---

### Post by titiou on 2015-05-07
I've tested twenty.sh on pclinuxos but I've the same error


[COLOR=#000000][FONT=dejavu sans mono]/bin/grep: /usr/lib/libFLAC.la: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]/bin/sed: can't read /usr/lib/libFLAC.la: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libtool: link: `/usr/lib/libFLAC.la' is not a valid libtool archive[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:14432: recipe for target 'lib/ecore_audio/libecore_audio.la' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[4]: *** [lib/ecore_audio/libecore_audio.la] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[4]: *** Waiting for unfinished jobs....[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:33789: recipe for target 'all-recursive' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[3]: *** [all-recursive] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:11962: recipe for target 'all' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[2]: *** [all] Error 2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:2437: recipe for target 'all-recursive' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make[1]: *** [all-recursive] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Makefile:1582: recipe for target 'all' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]make: *** [all] Error 2


[/FONT][/COLOR]I can't test twentyviv.sh because pclos doen't have systemd
what is the commande line to enable vlc?
I've changed all dependencies for pclos :

ImageMagick x11-server-xephyr automake libibus1.0_5 scim-gtk scim \
ccache cowsay doxygen libfreeglut-devel git libblkid-devel libbullet-devel \
libfontconfig-devel libfreetype6-devel libfribidi-devel libgif-devel \
libglib2.0-devel libgstreamer1.0-devel libgstreamer-plugins-base1.0-devel \
libharfbuzz-devel libjpeg-devel luajit luajit-devel libmount-devel \
libpam0 libpng-devel libpoppler-devel libpulseaudio-devel LibRaw-devel librsvg2-devel \
libsndfile-devel libspectre-devel libopenssl-devel libtiff-devel libtool libudev0-devel \
udisks2-devel libunibreak-devel vlc-devel libwebp-devel libxcb-util-image-devel libflac++6 \
libxcb-util-keysyms-devel libxcomposite-devel libxcursor-devel libxine-devel libflac++6-devel \
libxinerama-devel libxp-devel libxrandr2-devel libxtst-devel valgrind wmctrl libxscrnsaver-devel \
autoconf avr-binutils gettext-devel byacc lua5.0" 

If you can help us it's very cool, thank you Batden

---

### Post by batden on 2015-05-08
Sorry titiou, I can't help you.
I know nothing about PCLinuxOS.

---

### Post by batden on 2015-05-08
Check out these cool **E20 compatible themes**:
[http://e17-stuff.org/index.php?xcontentmode=7000](http://e17-stuff.org/index.php?xcontentmode=7000)
(OpenGEU ones)

Screenshot:
[http://www.enlightenment.org/ss/e-554cb54baf0b57.92544811.jpg](http://www.enlightenment.org/ss/e-554cb54baf0b57.92544811.jpg)

Another great E theme:
[http://avduma.deviantart.com/art/Bodhi-Linux-E19-Theme-519724678](http://avduma.deviantart.com/art/Bodhi-Linux-E19-Theme-519724678)
(download link on the top right)

---

### Post by heero2 on 2015-06-19
This is so extremely awesome... thanks for this enormous effort!

---

### Post by batden on 2015-06-20
Cheers, 8-)

---

### Post by JohnyPea on 2015-06-29
Thanks batden for your cotribution. I was able to use your script to compile e20 on Raspberry Pi2 (with a small persisting bug, which I will investigate later). On Ubuntu 15.04 the compilation fails on elementary, probably to some leftover libraries from previous tests (works ok in clean lxc container). I am learning a lot from your scripts, keep up the good work.

---

### Post by batden on 2015-06-29
> **JohnyPea said:**
> I am learning a lot from your scripts [...].

I'm glad you found them helpful. Keep experimenting!

---

### Post by iwonderwhy5 on 2015-10-01
Fails for me too (15.04) ..  output : 

Ideas anyone ?

```

make -j 16  all-am
make[4]: Entering directory `/home/sam/Enlightenment20/elementary/src/lib'
make[4]: warning: -jN forced in submake: disabling jobserver mode.
  CC       libelementary_la-elc_ctxpopup.lo
  CC       libelementary_la-elc_fileselector.lo
  CC       libelementary_la-elc_fileselector_button.lo
  CC       libelementary_la-elc_fileselector_entry.lo
  CC       libelementary_la-elc_hoversel.lo
  CC       libelementary_la-elc_multibuttonentry.lo
  CC       libelementary_la-elc_naviframe.lo
  CC       libelementary_la-elc_popup.lo
  CC       libelementary_la-elc_player.lo
  CC       libelementary_la-elc_scrolled_entry.lo
  CC       libelementary_la-elm_access.lo
  CC       libelementary_la-elm_actionslider.lo
  CC       libelementary_la-elm_app_common.lo
  CC       libelementary_la-elm_app_server_eet.lo
  CC       libelementary_la-elm_app_server.lo
  CC       libelementary_la-elm_app_server_view.lo
  CC       libelementary_la-elm_app_client.lo
  CC       libelementary_la-elm_app_client_view.lo
  CC       libelementary_la-elm_atspi_app_object.lo
  CC       libelementary_la-elm_atspi_bridge.lo
  CC       libelementary_la-elm_bg.lo
  CC       libelementary_la-elm_box.lo
  CC       libelementary_la-elm_bubble.lo
  CC       libelementary_la-elm_button.lo
  CC       libelementary_la-elm_calendar.lo
  CC       libelementary_la-elm_check.lo
  CC       libelementary_la-elm_clock.lo
  CC       libelementary_la-elm_cnp.lo
  CC       libelementary_la-elm_colorselector.lo
  CC       libelementary_la-elm_color_class.lo
  CC       libelementary_la-elm_config.lo
  CC       libelementary_la-elm_conform.lo
  CC       libelementary_la-elm_container.lo
  CC       libelementary_la-elm_datetime.lo
  CC       libelementary_la-elm_dayselector.lo
elm_calendar.c: In function '_format_month_year':
elm_calendar.c:175:4: warning: return discards 'const' qualifier from pointer target type [enabled by default]
    return eina_tmpstr_strftime(E_("%B %Y"), selected_time);
    ^
elm_calendar.c: In function '_format_month':
elm_calendar.c:181:4: warning: return discards 'const' qualifier from pointer target type [enabled by default]
    return eina_tmpstr_strftime(E_("%B"), selected_time);
    ^
elm_calendar.c: In function '_format_year':
elm_calendar.c:187:4: warning: return discards 'const' qualifier from pointer target type [enabled by default]
    return eina_tmpstr_strftime(E_("%Y"), selected_time);
    ^
  CC       libelementary_la-elm_dbus_menu.lo
  CC       libelementary_la-elm_diskselector.lo
  CC       libelementary_la-elm_flip.lo
  CC       libelementary_la-elm_entry.lo
  CC       libelementary_la-elm_flipselector.lo
  CC       libelementary_la-elm_font.lo
  CC       libelementary_la-elm_frame.lo
  CC       libelementary_la-elm_gengrid.lo
  CC       libelementary_la-elm_genlist.lo
  CC       libelementary_la-elm_gesture_layer.lo
  CC       libelementary_la-elm_gesture_layer_extra_gestures.lo
  CC       libelementary_la-elm_glview.lo
  CC       libelementary_la-elm_grid.lo
  CC       libelementary_la-elm_hover.lo
  CC       libelementary_la-elm_icon.lo
  CC       libelementary_la-elm_image.lo
  CC       libelementary_la-elm_index.lo
  CC       libelementary_la-elm_interface_atspi_accessible.lo
  CC       libelementary_la-elm_interface_atspi_action.lo
  CC       libelementary_la-elm_interface_atspi_component.lo
  CC       libelementary_la-elm_interface_atspi_editable_text.lo
  CC       libelementary_la-elm_interface_atspi_image.lo
  CC       libelementary_la-elm_interface_atspi_selection.lo
  CC       libelementary_la-elm_interface_atspi_text.lo
  CC       libelementary_la-elm_interface_atspi_value.lo
  CC       libelementary_la-elm_interface_atspi_widget_action.lo
  CC       libelementary_la-elm_interface_atspi_window.lo
  CC       libelementary_la-elm_interface_fileselector.lo
  CC       libelementary_la-elm_interface_scrollable.lo
  CC       libelementary_la-elm_inwin.lo
  CC       libelementary_la-elm_label.lo
  CC       libelementary_la-elm_layout.lo
  CC       libelementary_la-elm_list.lo
  CC       libelementary_la-elm_main.lo
  CC       libelementary_la-elm_map.lo
  CC       libelementary_la-elm_mapbuf.lo
  CC       libelementary_la-elm_menu.lo
  CC       libelementary_la-elm_module.lo
  CC       libelementary_la-elm_notify.lo
  CC       libelementary_la-elm_panel.lo
  CC       libelementary_la-elm_panes.lo
  CC       libelementary_la-elm_photo.lo
  CC       libelementary_la-elm_photocam.lo
  CC       libelementary_la-elm_plug.lo
  CC       libelementary_la-elm_prefs.lo
  CC       libelementary_la-elm_prefs_data.lo
  CC       libelementary_la-elm_progressbar.lo
  CC       libelementary_la-elm_radio.lo
  CC       libelementary_la-elm_route.lo
  CC       libelementary_la-elm_scroller.lo
  CC       libelementary_la-elm_segment_control.lo
  CC       libelementary_la-elm_separator.lo
  CC       libelementary_la-elm_slider.lo
  CC       libelementary_la-elm_slideshow.lo
  CC       libelementary_la-elm_spinner.lo
  CC       libelementary_la-elm_store.lo
  CC       libelementary_la-elm_systray.lo
  CC       libelementary_la-elm_systray_watcher.lo
  CC       libelementary_la-elm_sys_notify.lo
  CC       libelementary_la-elm_table.lo
  CC       libelementary_la-elm_theme.lo
  CC       libelementary_la-elm_thumb.lo
  CC       libelementary_la-elm_toolbar.lo
  CC       libelementary_la-elm_transit.lo
  CC       libelementary_la-elm_util.lo
  CC       libelementary_la-elm_url.lo
  CC       libelementary_la-elm_video.lo
  CC       libelementary_la-elm_view_list.lo
  CC       libelementary_la-elm_view_form.lo
  CC       libelementary_la-elm_web2.lo
  CC       libelementary_la-elm_widget.lo
  CC       libelementary_la-elm_win.lo
  CC       libelementary_la-elm_win_standard.lo
  CC       libelementary_la-elm_helper.lo
elm_main.c: In function 'elm_language_set':
elm_main.c:1154:30: warning: unused parameter 'lang' [-Wunused-parameter]
 elm_language_set(const char *lang)
                              ^
  CC       libelementary_la-els_box.lo
  CC       libelementary_la-els_cursor.lo
  CC       libelementary_la-els_tooltip.lo
make[4]: *** No rule to make target `eldbus_elementary_colorclass.c', needed by `libelementary_la-eldbus_elementary_colorclass.lo'.  Stop.
make[4]: *** Waiting for unfinished jobs....
  CC       libelementary_la-elu_ews_wm.lo
make[4]: Leaving directory `/home/sam/Enlightenment20/elementary/src/lib'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/sam/Enlightenment20/elementary/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sam/Enlightenment20/elementary/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sam/Enlightenment20/elementary'
make: *** [all] Error 2


 BUILD ERROR——TRY AGAIN LATER. 

```

---

### Post by batden on 2015-10-01
Hello iwonderwhy5

This commit seems to be causing your problem:

[https://git.enlightenment.org/core/elementary.git/commit/?id=5471505d0f24a05c7d96a83540fcdd2b14785433](https://git.enlightenment.org/core/elementary.git/commit/?id=5471505d0f24a05c7d96a83540fcdd2b14785433)
(Recent changes in elementary_colorclass)

The simple way to fix this is to uninstall (select option #3) and reinstall E20.
You may want to back up your settings folders (~/.e and ~/.elementary) before uninstalling.

---

### Post by batden on 2015-10-13
NEW build script for **Ubuntu 15.10**!
[https://dl.dropboxusercontent.com/u/58695863/twentywil.sh.gpg](https://dl.dropboxusercontent.com/u/58695863/twentywil.sh.gpg)

Previous (no longer maintained **&#407; **) scripts still available here:
[http://dazibao.perso.sfr.fr/HTML/scriptings.html](http://dazibao.perso.sfr.fr/HTML/scriptings.html)

---

### Post by batden on 2015-12-01
Enlightenment 20 is officially out!
[https://phab.enlightenment.org/phame/live/3/post/e20_release/](https://phab.enlightenment.org/phame/live/3/post/e20_release/)

---

### Post by batden on 2016-03-09
[COLOR=#ff0000]Discontinued due to lack of community interest.[/COLOR]

---

### Post by JohnyPea on 2016-03-10
That is sad. I was using your scripts regularly. Haven't written here in a while because they just worked excellently. Actually I was just working on adapting them for Raspberry Pi2. I was also going "Full throttle, baby!" for a while without problems.

---

### Post by batden on 2016-06-16
[FONT=Ubuntu][SIZE=2]Build script for Ubuntu 16.04 LTS[/SIZE][/FONT][FONT=Ubuntu][SIZE=2][FONT=Ubuntu][SIZE=2] (Enlightenment 21 devel)[/SIZE][/FONT] :

cd to the download folder,
wget [https://dl.dropboxusercontent.com/u/58695863/onexenius.sh](https://dl.dropboxusercontent.com/u/58695863/onexenius.sh)

Or here:
[/SIZE][/FONT][FONT=Ubuntu][SIZE=2][http://dazibao.perso.sfr.fr/HTML/index.html](http://dazibao.perso.sfr.fr/HTML/index.html)

NO SUPPORT.


[/SIZE][/FONT]

---

### Post by batden on 2016-07-01
Enlightenment 21 is officially released:
[https://www.enlightenment.org/news/e21_release](https://www.enlightenment.org/news/e21_release)

---

