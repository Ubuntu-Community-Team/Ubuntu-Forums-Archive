---
title: "Bittorrent"
date: 2009-05-30
forum: General Help
---

### Post by chmacka on 2009-05-30
I installed Bittorrent through Synaptic and I can't find it anywhere (It's not in any of the menus). I know about Transmission, but I'd really like to use Bittorrent, so please don't suggest me to use Transmission or some else bittorrent client.

These are files that are installed (according to Synaptic):

```
/.
/usr
/usr/bin
/usr/bin/btcompletedir.bittorrent
/usr/bin/btdownloadcurses.bittorrent
/usr/bin/btdownloadheadless.bittorrent
/usr/bin/btlaunchmany.bittorrent
/usr/bin/btlaunchmanycurses.bittorrent
/usr/bin/btmakemetafile.bittorrent
/usr/bin/btreannounce.bittorrent
/usr/bin/btrename.bittorrent
/usr/bin/btshowmetainfo.bittorrent
/usr/bin/bttrack.bittorrent
/usr/share
/usr/share/bittorrent
/usr/share/doc
/usr/share/doc/bittorrent
/usr/share/doc/bittorrent/README.txt
/usr/share/doc/bittorrent/credits.txt
/usr/share/doc/bittorrent/documentation.html
/usr/share/doc/bittorrent/donate.html
/usr/share/doc/bittorrent/download.html
/usr/share/doc/bittorrent/FAQ.html
/usr/share/doc/bittorrent/guide.html
/usr/share/doc/bittorrent/index.html
/usr/share/doc/bittorrent/introduction.html
/usr/share/doc/bittorrent/press.html
/usr/share/doc/bittorrent/protocol.html
/usr/share/doc/bittorrent/bittorrent_logo.png
/usr/share/doc/bittorrent/README.Debian
/usr/share/doc/bittorrent/copyright
/usr/share/doc/bittorrent/examples
/usr/share/doc/bittorrent/examples/bittorrent.init
/usr/share/doc/bittorrent/examples/bittorrent.default
/usr/share/doc/bittorrent/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/bttrack.bittorrent.1.gz
/usr/share/man/man1/btmakemetafile.bittorrent.1.gz
/usr/share/man/man1/btreannounce.bittorrent.1.gz
/usr/share/man/man1/btrename.bittorrent.1.gz
/usr/share/man/man1/btshowmetainfo.bittorrent.1.gz
/usr/share/man/man1/btcompletedir.bittorrent.1.gz
/usr/share/man/man1/bittorrent-downloader.bittorrent.1.gz
/usr/share/man/man1/bittorrent-multi-downloader.bittorrent.1.gz
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/bittorrent
/var
/var/lib
/var/lib/bittorrent
/var/log
/var/log/bittorrent
/usr/share/man/man1/btlaunchmanycurses.bittorrent.1.gz
/usr/share/man/man1/btlaunchmany.bittorrent.1.gz
/usr/share/man/man1/btdownloadheadless.bittorrent.1.gz
/usr/share/man/man1/btdownloadcurses.bittorrent.1.gz

```

I also installed bittorrent-gui:

```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/bittorrent-gui
/usr/share/doc/bittorrent-gui/copyright
/usr/share/doc/bittorrent-gui/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/btcompletedirgui.bittorrent.1.gz
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/bittorrent-gui
/usr/bin
/usr/bin/btcompletedirgui.bittorrent
/usr/bin/btdownloadgui.bittorrent
/usr/share/man/man1/btdownloadgui.bittorrent.1.gz

```

I don't know which one of these I should open to start Bittorrent.

When I type "bittorrent" in terminal, nothing happens (same thing with bittorrent-gui). 

I should also mention that I'm new to Linux.

---

### Post by madmaxou on 2009-05-30
Please go to the dir you installed your client in and post the result of "ls"...

---

### Post by chmacka on 2009-05-30
As I said, I'm new to Linux, so I hope I'm doing this right. The dir where I installed it is /usr/bin, true?

```

defoma-app                             ppdmerge
defoma-font                            ppdpo
defoma-hints                           ppmtolss16
defoma-id                              pr
defoma-psfont-installer                precat
defoma-subst                           prename
defoma-user                            preunzip
delpart                                prezip
desktop-file-install                   prezip-bin
desktop-file-validate                  print
devdump                                printafm
dexconf                                printenv
dfutool                                printf
dh_bash-completion                     prove
dh_installdefoma                       ps2ascii
dh_installxmlcatalogs                  ps2epsi
dh_pycentral                           ps2pdf
dh_pysupport                           ps2pdf12
diff                                   ps2pdf13
diff3                                  ps2pdf14
dig                                    ps2pdfwr
dircolors                              ps2ps
directomatic                           ps2ps2
dirname                                ps2txt
dirsplit                               psed
do-release-upgrade                     psfaddtable
dotlockfile                            psfgettable
dpkg                                   psfstriptable
dpkg-deb                               psfxtable
dpkg-query                             pstree
dpkg-split                             pstree.x11
dpkg-trigger                           pstruct
dprofpp                                ptar
dtsdec                                 ptardiff
du                                     ptx
dumphint                               pulseaudio
dumpkeys                               pulse-session
dvd-ram-control                        purple-remote
dvd+rw-booktype                        purple-send
dvd+rw-format                          purple-send-async
dvd+rw-mediainfo                       purple-url-handler
dvipdf                                 pwdx
dwell-click-applet                     py3_compilefiles
edit                                   pycentral
editor                                 py_compilefiles
editres                                pydoc
eject                                  pydoc2.6
ekiga                                  pygettext
ekiga-config-tool                      pygettext2.6
ekiga-helper                           pysupport-movemodules
enc2xs                                 pysupport-parseversions
enchant                                python
enchant-lsmod                          python2.6
env                                    pyversions
envsubst                               qdbus
eog                                    qpdldecode
eps2eps                                qtconfig
eqn                                    qtconfig-qt4
esc-m                                  qvlc
esd                                    ranlib
esdcat                                 rarian-example
esdcompat                              rarian-sk-config
esdctl                                 rarian-sk-extract
esddsp                                 rarian-sk-gen-uuid
esdfilt                                rarian-sk-get-cl
esdloop                                rarian-sk-get-content-list
esdmon                                 rarian-sk-get-extended-content-list
esdplay                                rarian-sk-get-scripts
esdrec                                 rarian-sk-install
esdsample                              rarian-sk-migrate
espeak                                 rarian-sk-preinstall
espeak-synthesis-driver                rarian-sk-rebuild
evince                                 rarian-sk-update
evince-thumbnailer                     rcp
evolution                              rdesktop
evolution-addressbook-export           rdfpipe
ex                                     readelf
exchange-connector-setup-2.26          readom
expand                                 red
expiry                                 rename
expr                                   rename.ul
extlinux                               renice
extract_dca                            reset
extract_dts                            resize
factor                                 resizecons
faillog                                rev
faked-sysv                             rfcomm
faked-tcp                              rgrep
fakeroot                               rhythmbox
fakeroot-sysv                          rhythmbox-client
fakeroot-tcp                           rlogin
fc-cache                               routef
fc-cat                                 routel
fc-list                                rpcclient
fc-match                               rpcgen
festival-synthesis-driver              rpcinfo
file                                   rpl8
file-roller                            rsh
filesharelist                          rss-glx_install
fileshareset                           rstart
find                                   rstartd
find2perl                              rsync
findsmb                                rtstat
finger                                 runcon
firefox                                run-mailcap
firefox-3.0                            run-with-aspell
flock                                  rview
fmt                                    rvlc
fold                                   s2p
font2c                                 sane-find-scanner
fontconfig-voodoo                      sas_disk_blink
fonttosfnt                             savelog
foo2hiperc                             scanimage
foo2hiperc-wrapper                     scim
foo2hp                                 scim-bridge
foo2hp2600-wrapper                     scim-config-agent
foo2lava                               scim-setup
foo2lava-wrapper                       scp
foo2oak                                screen
foo2oak-wrapper                        screendump
foo2qpdl                               screen-launcher
foo2qpdl-wrapper                       screen-profiles
foo2slx                                screen-profiles-export
foo2slx-wrapper                        screen-profiles-status
foo2xqx                                screen.real
foo2xqx-wrapper                        script
foo2zjs                                scriptreplay
foo2zjs-icc2ps                         scrollkeeper-config
foo2zjs-pstops                         scrollkeeper-extract
foo2zjs-wrapper                        scrollkeeper-gen-seriesid
foomatic-combo-xml                     scrollkeeper-get-cl
foomatic-compiledb                     scrollkeeper-get-content-list
foomatic-configure                     scrollkeeper-get-extended-content-list
foomatic-datafile                      scrollkeeper-get-index-from-docpath
foomatic-perl-data                     scrollkeeper-get-toc-from-docpath
foomatic-ppdfile                       scrollkeeper-get-toc-from-id
foomatic-ppd-options                   scrollkeeper-install
foomatic-ppd-to-xml                    scrollkeeper-preinstall
foomatic-printjob                      scrollkeeper-rebuilddb
foomatic-rip                           scrollkeeper-uninstall
foomatic-searchprinter                 scrollkeeper-update
free                                   scsi_logging_level
fribidi                                scsi_mandat
from                                   scsi_readcap
fslsfonts                              scsi_ready
f-spot                                 scsi_satl
f-spot-import                          scsi_start
f-spot-sqlite-upgrade                  scsi_stop
fstobdf                                scsi_temperature
ftp                                    sdiff
funzip                                 sdptool
gacutil                                seahorse
gacutil2                               seahorse-agent
gamma4scanimage                        seahorse-daemon
gcalctool                              seahorse-preferences
gcc                                    seahorse-tool
gcc-4.3                                see
gconf-editor                           select-default-iwrap
gconf-merge-tree                       select-editor
gconfsharp2-schemagen                  select-screen-profile
gconftool                              sensible-browser
gconftool-2                            sensible-editor
gcore                                  sensible-pager
gcov                                   seq
gcov-4.3                               service
gdb                                    services-admin
gdbserver                              sessreg
gdbtui                                 setarch
gdebi                                  setfacl
gdebi-gtk                              setkeycodes
gdialog                                setleds
gdk-pixbuf-query-loaders               setlogcons
gdm-dmx-reconnect-proxy                setmetamode
gdmdynamic                             setpci
gdmflexiserver                         setsid
gdmphotosetup                          setterm
gdmthemetester                         setxkbmap
gdmXnest                               sftp
gdmXnestchooser                        sg
gedit                                  sg_dd
gencat                                 sg_emc_trespass
genisoimage                            sg_format
geqn                                   sg_get_config
GET                                    sg_ident
getconf                                sginfo
geteltorito                            sg_inq
getent                                 sg_logs
getfacl                                sg_luns
gethostip                              sg_map
getkeycodes                            sg_map26
getopt                                 sgm_dd
gettext                                sg_modes
gettext.sh                             sg_opcodes
getweb                                 sgp_dd
gfloppy                                sg_persist
ggz-config                             sg_prevent
ggz-wrapper                            sg_raw
ghostscript                            sg_rbuf
gimp                                   sg_rdac
gimp-2.6                               sg_read
gimp-console                           sg_read_buffer
gimp-console-2.6                       sg_readcap
gipddecode                             sg_read_long
gksu                                   sg_reassign
gksudo                                 sg_requests
gksu-properties                        sg_reset
glxdemo                                sg_rmsn
glxgears                               sg_rtpg
glxheads                               sg_sat_identify
glxinfo                                sg_scan
gmenu-simple-editor                    sg_senddiag
gnome-about                            sg_ses
gnome-about-me                         sg_start
gnome-appearance-properties            sg_sync
gnome-app-install                      sg_test_rwbuf
gnome-at-mobility                      sg_turs
gnome-at-properties                    sg_verify
gnome-at-visual                        sg_vpd
gnome-audio-profiles-properties        sg_write_buffer
gnome-calculator                       sg_write_long
gnome-character-map                    sg_wr_mode
gnome-codec-install                    sha1sum
gnome-control-center                   sha224sum
gnome-default-applications-properties  sha256sum
gnome-desktop-item-edit                sha384sum
gnome-dictionary                       sha512sum
gnome-display-properties               shares-admin
gnome-doc-prepare                      shasum
gnome-doc-tool                         showconsolefont
gnome-eject                            showfont
gnome-font-viewer                      showkey
gnome-help                             showrgb
gnome-keybinding-properties            shred
gnome-keyboard-properties              shuf
gnome-keyring                          size
gnome-keyring-daemon                   skill
gnome-language-selector                slabtop
gnome-mount                            slogin
gnome-mouse-properties                 slxdecode
gnome-nettool                          smartdimmer
gnome-network-properties               smbcacls
gnome-open                             smbclient
gnome-panel                            smbcquotas
gnome-panel-screenshot                 smbget
gnome-pilot-make-password              smbpasswd
gnome-power-cmd                        smbspool
gnome-power-manager                    smbtar
gnome-power-manager-inhibit            smbtree
gnome-power-preferences                smproxy
gnome-power-statistics                 snice
gnome-screensaver                      soelim
gnome-screensaver-command              soffice
gnome-screensaver-preferences          software-properties-gtk
gnome-screenshot                       sort
gnome-search-tool                      speaker-test
gnome-session                          speechd-synthesis-driver
gnome-session-properties               splain
gnome-session-save                     split
gnome-settings-daemon                  splitfont
gnome-sound-properties                 sprof
gnome-sound-recorder                   ssh
gnome-system-log                       ssh-add
gnome-system-monitor                   ssh-agent
gnome-terminal                         ssh-argv0
gnome-terminal.wrapper                 ssh-askpass
gnome-text-editor                      ssh-copy-id
gnome-thumbnail-font                   ssh-keygen
gnome-typing-monitor                   ssh-keyscan
gnome-umount                           ssh-vulnkey
gnomevfs-cat                           start_kdeinit
gnomevfs-copy                          start_kdeinit_wrapper
gnomevfs-df                            start-pulseaudio-x11
gnomevfs-info                          startx
gnomevfs-ls                            stat
gnomevfs-mkdir                         strace
gnomevfs-monitor                       strings
gnomevfs-mv                            strip
gnomevfs-rm                            sudo
gnome-video-thumbnailer                sudoedit
gnome-volume-control                   sum
gnome-window-properties                svlc
gnome-wm                               synclient
gpasswd                                syndaemon
gpg                                    syslinux
gpg-convert-from-106                   syslinux2ansi
gpgsplit                               system-config-printer
gpgv                                   system-config-printer-applet
gpg-zip                                system-tools-backends
gpic                                   tabs
gpilot-applet                          tac
gpilotd                                tail
gpilotd-control-applet                 tasksel
gpilotd-session-wrapper                taskset
gpilot-install-file                    tbl
gprof                                  tee
groff                                  telnet
grog                                   telnet.netkit
grops                                  test
grotty                                 testparm
groups                                 testparm.samba3
growisofs                              test-speech
gs                                     tgz
gsbj                                   tic
gsdj                                   time
gsdj500                                time-admin
gslj                                   tload
gslp                                   toe
gsnd                                   tomboy
gst-feedback-0.10                      tomboy-panel
gst-inspect-0.10                       top
gst-launch-0.10                        toshset
gstreamer-codec-install                totem
gstreamer-properties                   totem-audio-preview
gst-typefind-0.10                      totem-gstreamer
gst-visualise-0.10                     totem-gstreamer-audio-preview
gst-xmlinspect-0.10                    totem-gstreamer-video-indexer
gst-xmllaunch-0.10                     totem-gstreamer-video-thumbnailer
gtbl                                   totem-video-indexer
gtf                                    totem-video-thumbnailer
gtk-query-immodules-2.0                touch
gtk-update-icon-cache                  tput
gtk-window-decorator                   tr
gucharmap                              tracepath
gvfs-cat                               tracepath6
gvfs-copy                              traceroute6
gvfs-info                              traceroute6.iputils
gvfs-less                              transmission
gvfs-ls                                troff
gvfs-mkdir                             tsclient
gvfs-monitor-dir                       tset
gvfs-monitor-file                      tsort
gvfs-mount                             tty
gvfs-move                              tzselect
gvfs-open                              ubuntu-bug
gvfs-rename                            ucf
gvfs-rm                                ucfq
gvfs-save                              ucfr
gvfs-trash                             ucs2any
gvfs-tree                              ul
h2ph                                   umax_pp
h2xs                                   unattended-upgrade
hal-device                             unexpand
hal-disable-polling                    unicode_stop
hal-find-by-capability                 uniq
hal-find-by-property                   unlink
hal-get-property                       unlzma
hal-is-caller-locked-out               unopkg
hal-is-caller-privileged               unzip
hal-lock                               unzipsfx
hal-set-property                       updatedb
hal-setup-keymap                       updatedb.mlocate
hcitool                                update-desktop-database
hd                                     update-manager
head                                   update-mime-database
HEAD                                   update-mime-database.real
helpztags                              update-notifier
hexdump                                update-pciids
hipercdecode                           uptime
host                                   usb-creator
hostid                                 usb_printerid
hp-align                               users
hp-check                               users-admin
hp-clean                               uuidgen
hp-colorcal                            uxterm
hp-devicesetup                         uz
hp-fab                                 vi
hp-faxsetup                            view
hp-firmware                            viewres
hp-hpdio                               vim.tiny
hpijs                                  vinagre
hp-info                                vino-passwd
hp-levels                              vino-preferences
hp-linefeedcal                         vlc
hp-makecopies                          vlc-wrapper
hp-makeuri                             vmstat
hp-mkuri                               volname
hp-plugin                              w
hp-pqdiag                              w3m
hp-print                               w3mman
hp-printsettings                       wall
hp-probe                               watch
hp-query                               wc
hp-scan                                wftopfa
hp-sendfax                             wget
hp-setup                               whatis
hp-systray                             whereis
hp-testpage                            which
hp-timedate                            whiptail
hp-toolbox                             who
hp-unload                              whoami
i386                                   whois
i486-linux-gnu-cpp                     wodim
i486-linux-gnu-cpp-4.3                 word-list-compress
i486-linux-gnu-gcc                     wpa_passphrase
i486-linux-gnu-gcc-4.3                 w.procps
iceauth                                write
iconv                                  www-browser
id                                     X
iecset                                 X11
ijs_pxljr                              x11perf
imagetops                              x11perfcomp
im-switch                              xargs
info                                   xauth
infobrowser                            xbiff
infocmp                                xbrlapi
infokey                                xcalc
infotocap                              xclipboard
install                                xclock
instmodsh                              xcmsdb
invest-chart                           xconsole
ionice                                 xcursorgen
ipcrm                                  xcutsel
ipcs                                   xdg-desktop-icon
ipod-read-sysinfo-extended             xdg-desktop-menu
isodump                                xdg-email
isoinfo                                xdg-icon-resource
isovfy                                 xdg-mime
ispell-wrapper                         xdg-open
jockey-gtk                             xdg-screensaver
join                                   xdg-user-dir
kab2kabc                               xdg-user-dirs-gtk-update
kaddprinterwizard                      xdg-user-dirs-update
kbuildsycoca                           xditview
kcmshell                               xdpyinfo
kconf_update                           xdriinfo
kcookiejar                             xev
kde-config                             xeyes
kded                                   xfd
kdeinit                                xfontsel
kdeinit_shutdown                       xfsinfo
kdeinit_wrapper                        xgamma
kde-menu                               xgc
kdesu_stub                             xhost
kdontchangethehostname                 xinit
kdostartupconfig                       xinput
kfile                                  xkbbell
kfmexec                                xkbcomp
kgrantpty                              xkbevd
khotnewstuff                           xkbprint
killall                                xkbvleds
kinstalltheme                          xkbwatch
kioexec                                xkeystone
kio_http_cache_cleaner                 xkill
kioslave                               xload
kio_uiserver                           xlogo
klauncher                              xlsatoms
kmailservice                           xlsclients
koi8rxterm                             xlsfonts
kpac_dhcp_helper                       xmag
krename                                xman
ksendbugmail                           xmessage
kshell                                 xml2po
kstartupconfig                         xmlcatalog
ktelnetservice                         xmllint
ktradertest                            xmodmap
kwrapper                               xmore
l2ping                                 Xorg
last                                   xpath
lastb                                  xpcshell-1.9
lastlog                                xprop
launchpad-integration                  xqxdecode
lavadecode                             xrandr
lcf                                    xrdb
ld                                     xrefresh
ldd                                    xsane
less                                   xscreensaver-getimage
lessecho                               xscreensaver-getimage-file
lessfile                               xscreensaver-getimage-video
lesskey                                xscreensaver-gl-helper
lesspipe                               xscreensaver-text
lexgrog                                x-session-manager
lftp                                   xset
lftpget                                xsetmode
libnetcfg                              xsetpointer
line                                   xsetroot
link                                   xsltproc
linux32                                xsm
linux64                                xstdcmap
listres                                xsubpp
lnstat                                 xterm
lnusertemp                             x-terminal-emulator
loadkeys                               xtrapchar
loadunimap                             xtrapin
locale                                 xtrapinfo
localedef                              xtrapout
locate                                 xtrapproto
lockfile-create                        xtrapreset
lockfile-remove                        xtrapstats
lockfile-touch                         xulrunner
logger                                 xulrunner-1.9
logname                                xvidtune
look                                   xvinfo
lorder                                 xwd
lp                                     x-window-manager
lpoptions                              xwininfo
lppasswd                               xwud
lpq                                    x-www-browser
lpr                                    xxd
lprm                                   yelp
lp_solve                               yes
lpstat                                 zdump
lsattr                                 zenity
lsb_release                            zip
lshal                                  zipcloak
lshw                                   zipgrep
lsof                                   zipinfo
lspci                                  zipnote
lspgpot                                zipsplit
lss16toppm                             zjsdecode
lsusb                                  zsoelim

```

---

### Post by hyperdude111 on 2009-05-30
You already have transmission as a bittorrent client pre-installed.

However i think the best one is deluge.

---

### Post by chmacka on 2009-05-30
@**[hyperdude111]("http://ubuntuforums.org/member.php?u=663352")**:
> **chmacka said:**
> I know about Transmission, but I'd really like to use Bittorrent, so please _don't suggest me to use Transmission or some else bittorrent client_.


I'd really want to use Bittorrent, especially now because I don't know how. I want to learn how to act if something like this happens again, rather than go searching for alternative right away.

---

### Post by MJWitter on 2009-05-30
I believe the command  to open it starts with bt so try typing that in, then pressing Tab twice, and it will tell you what is available..

Hope this helps..

---

### Post by _Purple_ on 2009-05-30
How did you install it?

---

### Post by chmacka on 2009-05-30
> **MJWitter said:**
> I believe the command  to open it starts with bt so try typing that in, then pressing Tab twice, and it will tell you what is available..

Hope this helps..
I've tried opening each one of these in /usr/bin through file manager but nothing happens. (**EDIT**: Except for one file (can't remember which). That one opened a window for selecting files to create a new torrent.)

> **_Purple_ said:**
> How did you install it?
> **chmacka said:**
> I installed Bittorrent _through Synaptic_

**EDIT**: Here are the windows that are opening:

---

### Post by MJWitter on 2009-05-30
Yeah, just installed it, tried it out, uninstalled it.
No offense, but it looks like a piece of rubbish.  I'm sure it is fine if you are going to use it as command line only application, but not gui.

May I ask why you want to use this particularly?

---

### Post by chmacka on 2009-05-30
> **MJWitter said:**
> Yeah, just installed it, tried it out, uninstalled it.
No offense, but it looks like a piece of rubbish.  I'm sure it is fine if you are going to use it as command line only application, but not gui.

May I ask why you want to use this particularly?

I really like uTorrent which I used on Windows. I could use it with Wine on Ubuntu, but I thought of trying Bittorrent instead - cause I know it's pretty similar to uTorrent (at least the version 6 for Windows is) - I don't know how Linux version looks like. Now, I would uninstall it if I didn't like it, but it really nerves me that I can't start it after installing it - which is the real reason for my persistence in trying to get it running.

How did you start it?

P. S.: I'll use Transmission.

---

### Post by MJWitter on 2009-05-30
The only gui portions appear to be the two that you managed to open..  I installed the program without the hui first and those were not available, then installed the gui and those two were available.

If you are used to uTorrent, you might like Deluge, I've been told it is a bit similar, also it is more fully featured than Transmission.

---

### Post by oldos2er on 2009-05-30
> **chmacka said:**
> I installed Bittorrent through Synaptic and I can't find it anywhere (It's not in any of the menus). I know about Transmission, but I'd really like to use Bittorrent, so please don't suggest me to use Transmission or some else bittorrent client.

These are files that are installed (according to Synaptic):

```
/.
/usr
/usr/bin
/usr/bin/btcompletedir.bittorrent
/usr/bin/btdownloadcurses.bittorrent
/usr/bin/btdownloadheadless.bittorrent
/usr/bin/btlaunchmany.bittorrent
/usr/bin/btlaunchmanycurses.bittorrent
/usr/bin/btmakemetafile.bittorrent
/usr/bin/btreannounce.bittorrent
/usr/bin/btrename.bittorrent
/usr/bin/btshowmetainfo.bittorrent
/usr/bin/bttrack.bittorrent
/usr/share
/usr/share/bittorrent
/usr/share/doc
/usr/share/doc/bittorrent
/usr/share/doc/bittorrent/README.txt
/usr/share/doc/bittorrent/credits.txt
/usr/share/doc/bittorrent/documentation.html
/usr/share/doc/bittorrent/donate.html
/usr/share/doc/bittorrent/download.html
/usr/share/doc/bittorrent/FAQ.html
/usr/share/doc/bittorrent/guide.html
/usr/share/doc/bittorrent/index.html
/usr/share/doc/bittorrent/introduction.html
/usr/share/doc/bittorrent/press.html
/usr/share/doc/bittorrent/protocol.html
/usr/share/doc/bittorrent/bittorrent_logo.png
/usr/share/doc/bittorrent/README.Debian
/usr/share/doc/bittorrent/copyright
/usr/share/doc/bittorrent/examples
/usr/share/doc/bittorrent/examples/bittorrent.init
/usr/share/doc/bittorrent/examples/bittorrent.default
/usr/share/doc/bittorrent/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/bttrack.bittorrent.1.gz
/usr/share/man/man1/btmakemetafile.bittorrent.1.gz
/usr/share/man/man1/btreannounce.bittorrent.1.gz
/usr/share/man/man1/btrename.bittorrent.1.gz
/usr/share/man/man1/btshowmetainfo.bittorrent.1.gz
/usr/share/man/man1/btcompletedir.bittorrent.1.gz
/usr/share/man/man1/bittorrent-downloader.bittorrent.1.gz
/usr/share/man/man1/bittorrent-multi-downloader.bittorrent.1.gz
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/bittorrent
/var
/var/lib
/var/lib/bittorrent
/var/log
/var/log/bittorrent
/usr/share/man/man1/btlaunchmanycurses.bittorrent.1.gz
/usr/share/man/man1/btlaunchmany.bittorrent.1.gz
/usr/share/man/man1/btdownloadheadless.bittorrent.1.gz
/usr/share/man/man1/btdownloadcurses.bittorrent.1.gz

```I also installed bittorrent-gui:

```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/bittorrent-gui
/usr/share/doc/bittorrent-gui/copyright
/usr/share/doc/bittorrent-gui/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/btcompletedirgui.bittorrent.1.gz
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/bittorrent-gui
/usr/bin
/usr/bin/btcompletedirgui.bittorrent
/usr/bin/btdownloadgui.bittorrent
/usr/share/man/man1/btdownloadgui.bittorrent.1.gz

```I don't know which one of these I should open to start Bittorrent.

When I type "bittorrent" in terminal, nothing happens (same thing with bittorrent-gui). 

I should also mention that I'm new to Linux.

 According to Synaptic, bittorrent is a CLI app, so it probably wouldn't create a menu entry.

 You should look in the directory **/usr/share/doc/bittorrent** for the documentation, or type **man bittorrent** in a terminal for help.

---

### Post by chmacka on 2009-05-30
> **MJWitter said:**
> If you are used to uTorrent, you might like Deluge, I've been told it is a bit similar, also it is more fully featured than Transmission.
I've installed it and it is pretty similar to uTorrent. Thanks!

---

