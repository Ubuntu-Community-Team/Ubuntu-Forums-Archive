---
title: "Error Mounting X-Plane DVDs"
date: 2011-12-20
forum: Gaming &amp; Leisure
---

### Post by ThiagoK on 2011-12-20
I cannot run my X-plane 9, as my notebook simply no longer recognizes the DVD 1 no matter how many times I put it to spin - it's as the optic reader can't find the initial line in the DVD. And the message I get is:

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

As a matter of fact, none of the 6 DVDs from that simulator are recognized, though I used them last week to install the game in my notebook!

From my notebook:

$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
0 dev='/dev/scd0' rwrw-- : 'TSSTcorp' 'CDDVDW SN-208BB'
-------------------------------------------------------------------------

$ aptitude search dvd
p bombono-dvd - programa de criação de DVDs com interface
p bombono-dvd-data - Arquivos de dados para bombono-dvd
i dvd+rw-tools - ferramentas DVD+-RW/R
p dvd+rw-tools-dbg - DVD+-RW/R tools (debug)
p dvd-slideshow - Ferramentas para criar apresentações de sl
p dvd95 - DVD9 to DVD5 converter
i A dvdauthor - Cria o sistema de ficheiros de DVD-Video
i dvdbackup - tool to rip DVD's from the command line
p dvdbackup-dbg - debug files for dvdbackup
p dvdisaster - data loss/scratch/aging protection for CD/
p dvdisaster-doc - data loss/scratch/aging protection for CD/
p dvdrip - perl front end for transcode and ffmpeg
p dvdrip-doc - Documentação para o dvd::rip
p dvdrip-queue - queue up dvd::rip projects
p dvdrip-utils - perl front end for transcode and ffmpeg (t
p dvdrtools - Programa para gravação de DVDs
p dvdstyler - Sistema multiplataforma de autoria de DVD
p dvdstyler-data - Arquivos de dados para o DVDStyler
p dvdtape - Create DVD master filesystems on DLT media
p dvdwizard - criação totalmente automática da estrutura
p ladvd - minimal LLDP/CDP sender
p libdvd-dev - extract video and audio tracks - devel fil
p libdvd0 - extract video and audio tracks - runtime f
v libdvdcss -
p libdvdcss-dev - Simple foundation for reading DVDs - devel
i libdvdcss2 - Simple foundation for reading DVDs - runti
p libdvdnav-dbg - DVD navigation library (debug)
p libdvdnav-dev - DVD navigation library (development)
i libdvdnav4 - biblioteca de navegação de DVD
p libdvdread-dbg - library for reading DVDs (debug)
p libdvdread-dev - library for reading DVDs (development)
i libdvdread4 - library for reading DVDs
p lsdvd - read the content info of a DVD
pB mint-meta-gnome-dvd - Set of packages included in the DVD editio
v mythdvd -
p radvd - Router Advertisement Daemon
p submux-dvd - subtitle multiplexer, muxes subtitles into
p vdr-plugin-dvd - DVD playback plugin for VDR
p video-dvdrip-doc - Documentation for dvd::rip - dummy package

---

