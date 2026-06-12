---
title: "Conky script doesn't load anymore"
date: 2009-05-24
forum: General Help
---

### Post by xjgnsdof on 2009-05-24
Ever since upgrading my kernel to 2.6.28-12, I notice that the following script refuses to load:

```

text_buffer_size 1100

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont arial:size=11

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none
#alignment middle_left
#alignment middle_right
#alignment bottom_middle

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

text_buffer_size 1100

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

color1 white
color3 7AB42F

TEXT
${color #7AB42F} ${font Arial:bold:size=12}SCHEDULE$font ${hr 2}$color
${execpi 30 conkyGoogleCalendar --username=XXXXXX --password=XXXXXXXXX --template=/home/emones/.conkyGoogleCalendar.template}

${color #7AB42F} ${font Arial:bold:size=12}TO-DO LIST$font ${hr 2}$color
${execi 30 cat /home/emones/Dropbox/TODO.txt | fold -w40 }
```

When I try to run Conky from the command line (conky -c ~/.conkyrc1), I get this error message:
> Conky: desktop window (14000a7) is subwindow of root window (b1)
Conky: window type - override
Conky: drawing to created window (0x4a00001)
Conky: drawing to double buffer
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
*** buffer overflow detected ***: conky terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7b40da8]
/lib/tls/i686/cmov/libc.so.6[0xb7b3eeb0]
/lib/tls/i686/cmov/libc.so.6[0xb7b3e495]
conky[0x805d4d9]
conky[0x805d7b1]
conky[0x8062355]
conky[0x8063308]
conky[0x8064b05]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7a59775]
conky[0x804c471]
======= Memory map: ========
08048000-0807f000 r-xp 00000000 08:01 92278      /usr/bin/conky
0807f000-08080000 r-xp 00036000 08:01 92278      /usr/bin/conky
08080000-08081000 rwxp 00037000 08:01 92278      /usr/bin/conky
08081000-0808e000 rwxp 08081000 00:00 0 
09b2a000-09b8e000 rwxp 09b2a000 00:00 0          [heap]
b74ef000-b74fc000 r-xp 00000000 08:01 2599       /lib/libgcc_s.so.1
b74fc000-b74fd000 r-xp 0000c000 08:01 2599       /lib/libgcc_s.so.1
b74fd000-b74fe000 rwxp 0000d000 08:01 2599       /lib/libgcc_s.so.1
b750c000-b7552000 r-xp 00000000 08:01 108875     /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b7552000-b7596000 r-xp 00000000 08:01 108975     /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b7596000-b759c000 r-xs 00000000 08:01 107221     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b759c000-b759f000 r-xs 00000000 08:01 107230     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b759f000-b75a2000 r-xs 00000000 08:01 110016     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b75a2000-b75a3000 r-xs 00000000 08:01 107216     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b75a3000-b75a6000 r-xs 00000000 08:01 107222     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b75a6000-b75a9000 r-xs 00000000 08:01 107218     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b75a9000-b75ac000 r-xs 00000000 08:01 107228     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b75ac000-b75b4000 r-xs 00000000 08:01 107231     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b75b4000-b75bf000 r-xs 00000000 08:01 107211     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b75bf000-b75e1000 r-xs 00000000 08:01 109838     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b75e1000-b75e8000 r-xs 00000000 08:01 107225     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b75e8000-b75ee000 r-xs 00000000 08:01 107210     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b75ee000-b762d000 r-xp 00000000 08:01 13369      /usr/lib/locale/en_US.utf8/LC_CTYPE
b762d000-b7630000 rwxp b762d000 00:00 0 
b7630000-b7654000 r-xp 00000000 08:01 9618       /usr/lib/libexpat.so.1.5.2
b7654000-b7656000 r-xp 00023000 08:01 9618       /usr/lib/libexpat.so.1.5.2
b7656000-b7657000 rwxp 00025000 08:01 9618       /usr/lib/libexpat.so.1.5.2
b7657000-b765b000 r-xp 00000000 08:01 9372       /usr/lib/libXdmcp.so.6.0.0
b765b000-b765c000 rwxp 00003000 08:01 9372       /usr/lib/libXdmcp.so.6.0.0
b765c000-b765f000 r-xp 00000000 08:01 2603       /lib/libgpg-error.so.0.3.0
b765f000-b7660000 rwxp 00002000 08:01 2603       /lib/libgpg-error.so.0.3.0
b7660000-b7662000 r-xp 00000000 08:01 2608       /lib/libkeyutils-1.2.so
b7662000-b7663000 r-xp 00001000 08:01 2608       /lib/libkeyutils-1.2.so
b7663000-b7664000 rwxp 00002000 08:01 2608       /lib/libkeyutils-1.2.so
b7664000-b766b000 r-xp 00000000 08:01 9962       /usr/lib/libkrb5support.so.0.1
b766b000-b766c000 r-xp 00006000 08:01 9962       /usr/lib/libkrb5support.so.0.1
b766c000-b766d000 rwxp 00007000 08:01 9962       /usr/lib/libkrb5support.so.0.1
b766d000-b766e000 rwxp b766d000 00:00 0 
b766e000-b7670000 r-xp 00000000 08:01 2584       /lib/libcom_err.so.2.1
b7670000-b7671000 r-xp 00001000 08:01 2584       /lib/libcom_err.so.2.1
b7671000-b7672000 rwxp 00002000 08:01 2584       /lib/libcom_err.so.2.1
b7672000-b7694000 r-xp 00000000 08:01 9954       /usr/lib/libk5crypto.so.3.1
b7694000-b7695000 r-xp 00022000 08:01 9954       /usr/lib/libk5crypto.so.3.1
b7695000-b7696000 rwxp 00023000 08:01 9954       /usr/lib/libk5crypto.so.3.1
b7696000-b7725000 r-xp 00000000 08:01 9960       /usr/lib/libkrb5.so.3.3
b7725000-b7727000 r-xp 0008e000 08:01 9960       /usr/lib/libkrb5.so.3.3
b7727000-b7728000 rwxp 00090000 08:01 9960       /usr/lib/libkrb5.so.3.3
b7728000-b773e000 r-xp 00000000 08:01 10188      /usr/lib/libsasl2.so.2.0.22
b773e000-b773f000 r-xp 00015000 08:01 10188      /usr/lib/libsasl2.so.2.0.22
b773f000-b7740000 rwxp 00016000 08:01 10188      /usr/lib/libsasl2.so.2.0.22
b7740000-b7752000 r-xp 00000000 08:01 6205       /lib/tls/i686/cmov/libresolv-2.9.so
b7752000-b7753000 r-xp 00011000 08:01 6205       /lib/tls/i686/cmov/libresolv-2.9.so
b7753000-b7754000 rwxp 00012000 08:01 6205       /lib/tls/i686/cmov/libresolv-2.9.so
b7754000-b7757000 rwxp b7754000 00:00 0 
b7757000-b7787000 r-xp 00000000 08:01 2649       /lib/libpcre.so.3.12.1
b7787000-b7788000 r-xp 0002f000 08:01 2649       /lib/libpcre.so.3.12.1
b7788000-b7789000 rwxp 00030000 08:01 2649       /lib/libpcre.so.3.12.1
b7789000-b7791000 r-xp 00000000 08:01 9396       /usr/lib/libXrender.so.1.3.0
b7791000-b7792000 r-xp 00007000 08:01 9396       /usr/lib/libXrender.so.1.3.0
b7792000-b7793000 rwxp 00008000 08:01 9396       /usr/lib/libXrender.so.1.3.0
b7793000-b7805000 r-xp 00000000 08:01 6233       /usr/lib/libfreetype.so.6.3.20
b7805000-b7809000 r-xp 00071000 08:01 6233       /usr/lib/libfreetype.so.6.3.20
b7809000-b780a000 rwxp 00075000 08:01 6233       /usr/lib/libfreetype.so.6.3.20
b780a000-b7835000 r-xp 00000000 08:01 9628       /usr/lib/libfontconfig.so.1.3.0
b7835000-b7836000 r-xp 0002a000 08:01 9628       /usr/lib/libfontconfig.so.1.3.0
b7836000-b7837000 rwxp 0002b000 08:01 9628       /usr/lib/libfontconfig.so.1.3.0
b7837000-b7839000 r-xp 00000000 08:01 9361       /usr/lib/libXau.so.6.0.0
b7839000-b783a000 r-xp 00001000 08:01 9361       /usr/lib/libXau.so.6.0.0
b783a000-b783b000 rwxp 00002000 08:01 9361       /usr/lib/libXau.so.6.0.0
b783b000-b783c000 rwxp b783b000 00:00 0 
b783c000-b7854000 r-xp 00000000 08:01 10329      /usr/lib/libxcb.so.1.1.0
b7854000-b7855000 r-xp 00017000 08:01 10329      /usr/lib/libxcb.so.1.1.0
b7855000-b7856000 rwxp 00018000 08:01 10329      /usr/lib/libxcb.so.1.1.0
b7856000-b78bc000 r-xp 00000000 08:01 2601       /lib/libgcrypt.so.11.4.4
b78bc000-b78bd000 r-xp 00065000 08:01 2601       /lib/libgcrypt.so.11.4.4
b78bd000-b78bf000 rwxp 00066000 08:01 2601       /lib/libgcrypt.so.11.4.4
b78bf000-b78cf000 r-xp 00000000 08:01 10253      /usr/lib/libtasn1.so.3.0.16
b78cf000-b78d0000 r-xp 0000f000 08:01 10253      /usr/lib/libtasn1.so.3.0.16
b78d0000-b78d1000 rwxp 00010000 08:01 10253      /usr/lib/libtasn1.so.3.0.16
b78d1000-b7968000 r-xp 00000000 08:01 9769       /usr/lib/libgnutls.so.26.4.6
b7968000-b796d000 r-xp 00097000 08:01 9769       /usr/lib/libgnutls.so.26.4.6
b796d000-b796e000 rwxp 0009c000 08:01 9769       /usr/lib/libgnutls.so.26.4.6
b796e000-b7997000 r-xp 00000000 08:01 9809       /usr/lib/libgssapi_krb5.so.2.2
b7997000-b7998000 r-xp 00028000 08:01 9809       /usr/lib/libgssapi_krb5.so.2.2
b7998000-b7999000 rwxp 00029000 08:01 9809       /usr/lib/libgssapi_krb5.so.2.2
b7999000-b799a000 rwxp b7999000 00:00 0 
b799a000-b79da000 r-xp 00000000 08:01 9971       /usr/lib/libldap_r-2.4.so.2.4.1
b79da000-b79db000 ---p 00040000 08:01 9971       /usr/lib/libldap_r-2.4.so.2.4.1
b79db000-b79dc000 r-xp 00040000 08:01 9971       /usr/lib/libldap_r-2.4.so.2.4.1
b79dc000-b79dd000 rwxp 00041000 08:01 9971       /usr/lib/libldap_r-2.4.so.2.4.1
b79dd000-b79de000 rwxp b79dd000 00:00 0 
b79de000-b79ea000 r-xp 00000000 08:01 9966       /usr/lib/liblber-2.4.so.2.4.1
b79ea000-b79eb000 r-xp 0000b000 08:01 9966       /usr/lib/liblber-2.4.so.2.4.1
b79eb000-b79ec000 rwxp 0000c000 08:01 9966       /usr/lib/liblber-2.4.so.2.4.1
b79ec000-b7a1c000 r-xp 00000000 08:01 9934       /usr/lib/libidn.so.11.5.39
b7a1c000-b7a1d000 ---p 00030000 08:01 9934       /usr/lib/libidn.so.11.5.39
b7a1d000-b7a1e000 r-xp 00030000 08:01 9934       /usr/lib/libidn.so.11.5.39
b7a1e000-b7a1f000 rwxp 00031000 08:01 9934       /usr/lib/libidn.so.11.5.39
b7a1f000-b7a33000 r-xp 00000000 08:01 2695       /lib/libz.so.1.2.3.3
b7a33000-b7a34000 r-xp 00013000 08:01 2695       /lib/libz.so.1.2.3.3
b7a34000-b7a35000 rwxp 00014000 08:01 2695       /lib/libz.so.1.2.3.3
b7a35000-b7a37000 r-xp 00000000 08:01 6183       /lib/tls/i686/cmov/libdl-2.9.so
b7a37000-b7a38000 r-xp 00001000 08:01 6183       /lib/tls/i686/cmov/libdl-2.9.so
b7a38000-b7a39000 rwxp 00002000 08Aborted


---

### Post by Liolikas on 2009-05-24
Try conky latest version 1.7.0.

If this will not help submit conky bug. ([http://sourceforge.net/projects/conky/](http://sourceforge.net/projects/conky/)) you will have to register in that page.

---

### Post by xjgnsdof on 2009-05-24
I tried that, but I eventually get this error message:

> checking for XdbeQueryExtension in -lXext... no
configure: error: Could not find XdbeQueryExtension in -lXext

---

### Post by xjgnsdof on 2009-05-24
up

---

