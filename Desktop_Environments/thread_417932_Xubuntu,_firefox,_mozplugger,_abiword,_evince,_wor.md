---
title: "Xubuntu, firefox, mozplugger, abiword, evince, word docs, pdfs and mime type errors"
date: 2007-04-22
forum: Desktop Environments
---

### Post by simonn on 2007-04-22
This is a solution in case anybody else is having similar problems using mozplugger to use abiword and evince to display documents and pdfs in firefox. This is tested on Xubuntu Feisty 7.04. It assumes you already have mozplugger installed and know how to use it.

PROBLEM: Opening pdfs in Firefox will result in evince opening with firefox, but displying the error message box:

Unable to open document 
Unhandled MIME type

Opening word/open office/star office documents in firefox results in:

AbiWord cannot open [file]. It appears to be an invalid document

DIAGNOSIS: What I think is happening is that firefox passes the cached file name to mozplugger which passes it to abiword or evince. However, the cache file does not have an extension and there is no way (yet*) to tell evince or abiword what the mime type is so they do not know what to do with it.

SOLUTION: I wrote a wrapper script which creates a symlink in /tmp or $TMPDIR with the (mostly**) correct file extension and passes the symlink to either abiword or evince rather than the cache file.

Unfortunately, there is no way to delete the symlink afterwards because the script seems to just stop after evince or abiword are executed. This is not much of a problem as symlinks only take up bytes of space, but mess is bad, mkay. The wrapper script checks to see if evince or abiword, depending on which is required, is running when it starts and if it is not then it deletes any stale symlinks. I would also consider setting up tmpreaper anyway, not just for this - mess is bad, mkay.

Anyway... the script, save it to /usr/local/bin/mozplugger-mime-wrapper.sh and make it executable using sudo chmod +x /usr/local/bin/mozplugger-mime-wrapper.sh:

```

#!/bin/sh
#
# USAGE: mozplugger-mime-wrapper.sh filename mimetype application
#

# Check for existance of all parameters or exit
[ -z "$1" -o -z "$2"  -o -z "$3" ] && exit 1

# Determine file extension based on mime type
case "$2" in
	application/x-rtf | application/rtf | text/rtf ) EXT="rtf" ;;
	application/x-msword | application/msword ) EXT="doc" ;;
	application/vnd.sun.xml.writer | application/so7_vnd.sun.xml.writer ) EXT="sxw" ;;
	application/vnd.oasis.opendocument.text ) EXT="odt" ;;
	application/x-abiword | text/abiword ) EXT="abw" ;;
	application/pdf | application/x-pdf | text/pdf | text/x-pdf ) EXT="pdf" ;;
	application/x-dvi ) EXT="dvi" ;;
	application/x-postscript | application/postscript ) EXT="ps" ;;
esac

# Exit if this script does not handle mimetype
[ -z "$EXT" ] && exit 2

# Create temporary directory
TDIR="$TMPDIR"
[ -z "$TDIR" ] && TDIR="/tmp"
TARGETDIR="$TDIR/mozplugger-$USER/$3"
[ -d "$TARGETDIR" ] || mkdir -p "$TARGETDIR"
[ -d "$TARGETDIR" ] || exit 3

# Try and delete stale links
[ -z $(ps -U "$USER" | grep "$3$") ] && rm -f "$TARGETDIR"/*

# Create link with correct file extension
TARGET="$TARGETDIR/`basename $1`.$EXT"
ln -s "$1" "$TARGET"

# Start application with link
"$3" "$TARGET"

# This does not work???
rm "$TARGET"

```

Next, in /etc/mozpluggerrc call mozplugger-mime-wrapper.sh instead of abiword or evince when needed. For example, here is a fragment of my /etc/mozpluggerrc for the relevent mime types:

```

...
application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
application/x-postscript:ps:PostScript file
application/postscript:ps:PostScript file
	repeat noisy swallow(evince) fill: mozplugger-mime-wrapper.sh "$file" "$mimetype" evince

application/x-rtf:rtf:Rich Text Format
application/rtf:rtf:Rich Text Format
text/rtf:rtf:Rich Text Format
application/x-msword:doc,dot:Microsoft Word Document
application/msword:doc,dot:Microsoft Word Document
application/vnd.sun.xml.writer:sxw:OpenOffice Writer 6.0 documents
application/so7_vnd.sun.xml.writer:sxw:OpenOffice Writer 7.0 documents
application/vnd.oasis.opendocument.text:odt:OASIS OpenDocument Text
application/x-abiword:abw,zabw,bzabw:AbiWord Document
text/abiword:abw,zabw,bzabw:AbiWord Document
	repeat swallow(AbiWord) fill: mozplugger-mime-wrapper.sh "$file" "$mimetype" abiword
...

```

Remember to close all instances of firefox and delete pluginreg.dat from all your users $HOME/.mozilla/firefox dirs or the changes to mozpluggerrc will not be picked up.

NOTE: Postscript files (.ps) will not load with evince-gtk from Xubuntu. evince-gtk is an older version of evice with which this is a bug. The normal evince package with the gnome dependencies should not have this problem.

*By the looks of it, the CVS version of abiword allows you  to force the mime type of a file when opening a file from the command line.

**There is no way of determining .dot (word templates) files so .doc will be used. .dot files load into abiword within firefox as .doc files fine though.

---

### Post by kerry_s on 2007-04-22
Interesting, i use epdfview for pdf's with mozplugger in firefox and regular open office for docs, ps i use gv. Only my pdf's are open in the browser, the rest are open outside. If you look at the mozplugger site it says he will update to the new apps in time.

my epdf line:

```
	repeat noisy swallow(epdfview) fill: epdfview "$file"
```

My mozpluggerrc:

```
# Configure file for MozPlugger 1.7
# Version: July 17, 2005
#
# Commands which are not installed on your system will not be used.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111, USA.


###################
### m4 macros   ###
###################

changequote([,])

### Helpers

#define(ENABLE_HELPERS)

ifdef([ENABLE_HELPERS],[
  define(HELPER,[nokill noisy: $1])
],[
  define(HELPER,[])
])

### MPlayer

define(MP_CMD,[mplayer -really-quiet -nojoystick -nofs -zoom -osdlevel 0 $1 </dev/null])

define(MP_EMBED,[embed noisy ignore_errors: MP_CMD(-xy $width -wid $window $1)])

define(MP_NOEMBED,[noembed noisy ignore_errors maxaspect swallow(MPlayer): MP_CMD($1)])

define(MP_VIDEO_STREAM,[stream MP_EMBED($1 "$file")
	stream MP_NOEMBED($1 "$file")])

define(MP_AUDIO_STREAM,[controls stream noisy ignore_errors: mplayer -really-quiet -nojoystick "$file" </dev/null])

ifelse(esyscmd([mplayer -afm help 2>&1 | grep vorbis]),[],[
  define(MP_NO_VORBIS)
],[
  define(MP_VORBIS)
])

### Totem

define(TM_CMD,[totem $1</dev/null])

define(TM_EMBED,[embed noisy ignore_errors hidden fill swallow(Totem): TM_CMD(--toggle-controls $1)])

define(TM_NOEMBED,[nokill noembed noisy ignore_errors: TM_CMD($1)])

define(TM_VIDEO_STREAM,[stream TM_EMBED("$file")
	stream TM_NOEMBED("$file")])

define(TM_AUDIO_STREAM,[controls stream noisy ignore_errors: TM_CMD("$file")])

### OpenOffice

define([OO],[swallow(OpenOffice) fill: openoffice -nologo $1 "$file"
	swallow(OpenOffice) fill: ooffice -nologo $1 "$file"
	swallow(OpenOffice) fill: soffice -nologo $1 "$file"])

### Acrobat Reader

define(ACROREAD_OPTS,[-geometry +9000+9000 -tempFileTitle acroread])
define(ACROREAD_FLAGS,[repeat swallow(acroread) fill])
define(ACROREAD,[ACROREAD_FLAGS(): acroread ACROREAD_OPTS() -openInNewWindow "$file"])

### GV

define(GV_OPTS,[--safer --quiet --antialias -geometry +9000+9000])
#define(GV_OPTS,[-geometry +9000+9000])
define(GV_FLAGS,[repeat noisy swallow(gv) fill])
define(GV,[GV_FLAGS(): gv GV_OPTS() "$file"])

###################
### Video       ###
###################

video/mpeg:mpeg,mpg,mpe:MPEG animation
video/x-mpeg:mpeg,mpg,mpe:MPEG animation
video/x-mpeg2:mpv2,mp2ve:MPEG2 animation
	MP_VIDEO_STREAM()
	TM_VIDEO_STREAM()
        HELPER(xine -pq "$file")
	loop: mtvp -l -W$window "$file"
	: mtvp -W$window "$file"
	loop: xanim +Av100 -Zr +W$window +q +f "$file"
	: xanim +Av100 -Zr +W$window +q +Ze +f "$file"

video/mp4:mp4:MPEG4 animation
	MP_VIDEO_STREAM()
	TM_VIDEO_STREAM()
	HELPER(xine -pq "$file")

video/msvideo:avi:AVI animation
video/x-msvideo:avi:AVI animation
video/fli:fli,flc:FLI animation
video/x-fli:fli,flc:FLI animation
	MP_VIDEO_STREAM()
	TM_VIDEO_STREAM()
	HELPER(xine -pq "$file")

application/x-mplayer2:wmv,asf,mov:Windows Media
video/x-ms-asf:asf,asx,wma,wax,wmv,wvx:Windows Media
video/x-ms-wmv:wmv:Windows Media
	MP_VIDEO_STREAM()
	TM_VIDEO_STREAM()

application/x-quicktimeplayer:mov:Quicktime animation
image/x-macpaint:pntg,mov:Quicktime animation
video/quicktime:mov,qt:Quicktime animation
video/x-quicktime:mov,qt:Quicktime animation
	MP_VIDEO_STREAM()
	TM_VIDEO_STREAM()
	HELPER(xine -pq "$file")

video/x-theora:ogg:OGG stream with video
video/theora:ogg:OGG stream with video
video/ogg:ogg:OGG stream with video
video/x-ogg:ogm,ogv:OGG stream with video
ifdef([MP_VORBIS],[	MP_VIDEO_STREAM()
])	TM_VIDEO_STREAM()

video/dl:dl:DL animation
video/x-dl:dl:DL animation
video/sgi-movie:movie,movi,mv:SGI animation
video/x-sgi-movie:movie,movi,mv:SGI animation
video/anim:iff,anim5,anim3,anim7:IFF animation
video/x-anim:iff,anim5,anim3,anim7:IFF animation
	loop: xanim +Av100 -Zr +W$window +q +f "$file"
	: xanim +Av100 -Zr +W$window +q +Ze +f "$file"


##################
### Audio      ###
##################

audio/mid:midi,mid:MIDI audio file
audio/x-mid:midi,mid:MIDI audio file
audio/midi:midi,mid:MIDI audio file
audio/x-midi:midi,mid:MIDI audio file
	controls noisy stream: timidity -Od "$file"
	controls: playmidi "$file"

audio/mod:mod:Soundracker audio Module
audio/x-mod:mod:Soundracker audio Module
	controls loop noisy: mikmod -q --interpolate "$file"
	controls noisy: mikmod -q --interpolate "$file"
	controls loop noisy: xmp -l --nocmd "$file"
	controls noisy: xmp --nocmd "$file"

audio/mp3:mp3:MPEG audio
audio/x-mp3:mp3:MPEG audio
audio/mpeg2:mp2:MPEG audio
audio/x-mpeg2:mp2:MPEG audio
audio/mpeg3:mp3:MPEG audio
audio/x-mpeg3:mp3:MPEG audio
audio/mpeg:mpa,abs,mpega:MPEG audio
audio/x-mpeg:mpa,abs,mpega:MPEG audio
	MP_AUDIO_STREAM()
	TM_AUDIO_STREAM()
	controls: mpg321 -q "$file"
	controls: mpg123 -q "$file"
	controls: splay -t 200 "$file"
	controls: amp -b 200 -q "$file"
	controls: maplay "$file"
	controls: mpeg3play "$file"
	HELPER(xmms -e -p "$file")
	repeat noisy swallow(alsaplayer): alsaplayer -q "$file"

audio/mpeg-url:m3u:MPEG music resource locator
audio/x-mpeg-url:m3u:MPEG music resource locator
audio/mpegurl:m3u:MPEG music resource locator
audio/x-mpegurl:m3u:MPEG music resource locator
audio/mpeg-url:m3u:MPEG music resource locator
audio/x-mpeg-url:m3u:MPEG music resource locator
audio/x-scpls:pls:Shoutcast Playlists
#	controls: mpg321 -q -@ "$file"
	HELPER(xmms -e -p "$file")

audio/x-ogg:ogg:OGG audio
application/x-ogg:ogg:OGG audio
application/ogg:ogg:OGG audio
ifdef([MP_VORBIS],[	MP_AUDIO_STREAM()
])	TM_AUDIO_STREAM()
	controls stream noisy: ogg123 -q -b 128 "$file"
	HELPER(xmms -e -p "$file")

audio/x-sidtune:sid,psid:Commodore 64 Audio
audio/sidtune:sid,psid:Commodore 64 Audio
audio/psid:psid,sid:Commodore 64 Audio
audio/x-psid:psid,sid:Commodore 64 Audio
	controls noisy: sidplay -16 -f44100 -a "$file"

audio/basic:au,snd:Basic audio file
audio/x-basic:au,snd:Basic audio file
	controls: play "$file"
	controls: sox "$file" -t .au - > /dev/audio

audio/wav:wav:Microsoft wave file
audio/x-wav:wav:Microsoft wave file
audio/x-pn-wav:wav:Microsoft wave file
audio/x-pn-windows-acm:wav:Microsoft wave file
        controls: play "$file"
	controls: wavplay -q "$file"
	controls noisy: bplay "$file"
	controls: splay "$file"
	HELPER(xmms -e -p "$file")
 	repeat noisy swallow(alsaplayer): alsaplayer -q "$file"

audio/x-pn-realaudio-plugin:rpm:RealPlayer Plugin Metafile
audio/x-pn-realaudio:ra,rm,ram:Realaudio-plugin resource locator
audio/x-realaudio:ra,rm,ram:RealAudio file
application/vnd.rn-realmedia:rm:RealMedia file
application/smil:smi:RealPlayer
audio/vnd.rn-realaudio:ra,ram:RealAudio file
audio/vnd.rn-realvideo:rv:RealVideo file
	nokill stream: hxplay "$file"
        nokill stream: realplay "$file"

audio/x-ms-wax:wax,wma:Windows Media
	MP_AUDIO_STREAM()
	TM_AUDIO_STREAM()

#######################
### Documents       ###
#######################

image/sun-raster:rs:SUN raster image
image/x-sun-raster:rs:SUN raster image
image/x-rgb:rgb:RGB Image
image/x-portable-pixmap:ppm:PPM Image
image/x-portable-graymap:pgm:PGM Image
image/x-portable-bitmap:pbm:PBM Image
image/x-portable-anymap:pnm:PBM Image
image/tiff:tiff,tif:TIFF image
image/x-tiff:tiff,tif:TIFF image
	repeat noisy swallow(gqview) fill: gqview -t "$file"
	swallow(:) maxaspect: xv -ima -igeom +9000+9000 -geometry +9000+9000 "$file"
	repeat swallow(display): display "$file"
	repeat swallow(Sdtimage) fill: sdtimage "$file"
	swallow(*qiv:) fill maxaspect: qiv -n "$file"

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	ACROREAD()
	repeat noisy swallow(epdfview) fill: epdfview "$file"
	repeat noisy swallow(evince) fill: evince "$file"
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -z width "$file"
	GV()

application/x-dvi:dvi:DVI file
        repeat swallow(kviewshell) fill: kdvi "$file"
	repeat swallow(xdvi) fill: xdvi -safer -hush -geometry +9000+9000 "$file"

application/x-postscript:ps:PostScript file
application/postscript:ps:PostScript file
	repeat noisy swallow(evince) fill: evince "$file"
	GV()
	repeat swallow(Pageview) fill: pageview "$file"

application/x-rtf:rtf:Rich Text Format
application/rtf:rtf:Rich Text Format
text/rtf:rtf:Rich Text Format
	repeat noisy swallow(Ted) fill: Ted "$file"
#	repeat noisy swallow(AbiWord) fill: abiword --nosplash --geometry +9000+9000 "$file"
#	repeat noisy swallow(kwrite): kwrite "$file"
	repeat noisy swallow(kword): kword "$file"
	OO()

application/x-msword:doc,dot:Microsoft Word Document
application/msword:doc,dot:Microsoft Word Document
#       repeat noisy swallow(AbiWord) fill: abiword --nosplash --geometry +9000+9000 "$file"
	repeat noisy swallow(kword): kword "$file"
	OO()

application/vnd.ms-excel:xls,xlb:Microsoft Excel Document
	repeat swallow(PluggerGnumeric) fill: gnumeric --name PluggerGnumeric "$file"
	OO()

# OpenOffice MimeTypes (http://framework.openoffice.org/documentation/mimetypes/mimetypes.html)
application/vnd.sun.xml.writer:sxw:OpenOffice Writer 6.0 documents
application/so7_vnd.sun.xml.writer:sxw:OpenOffice Writer 7.0 documents
application/vnd.sun.xml.writer.template:stw:OpenOffice Writer 6.0 templates
application/vnd.sun.xml.writer.global:sxg:OpenOffice Writer 6.0 global documents
application/vnd.stardivision.writer:sdw:StarWriter 5.x documents
application/vnd.stardivision.writer-global:sgl:StarWriter 5.x global documents
application/x-starwriter:sdw:StarWriter 4.x documents
	OO()

application/vnd.sun.xml.calc:sxc:OpenOffice Calc 6.0 spreadsheets
application/so7_vnd.sun.xml.calc:sxc:OpenOffice Calc 7.0 spreadsheets
application/vnd.sun.xml.calc.template:stc:OpenOffice Calc 6.0 templates
application/vnd.stardivision.calc:sdc:StarCalc 5.x spreadsheets
application/x-starcalc:sdc:StarCalc 4.x spreadsheets
	OO()

application/vnd.sun.xml.draw:sxd:OpenOffice Draw 6.0 documents
application/so7_vnd.sun.xml.draw:sxc:StarOffice Draw 7.0 documents
application/vnd.sun.xml.draw.template:std:OpenOffice Draw 6.0 templates
application/vnd.stardivision.draw:sda:StarDraw 5.x documents
application/x-stardraw:sda:StarDraw 4.x documents
	OO()

application/vnd.sun.xml.impress:sxi:OpenOffice Impress 6.0 presentations
application/so7_vnd.sun.xml.impress:sxi:StarOffice 7.0 Impress presentations
application/vnd.sun.xml.impress.template:sti:OpenOffice Impress 6.0 templates
application/vnd.stardivision.impress:sdd:StarImpress 5.x presentations
application/vnd.stardivision.impress-packed:sdp:StarImpress Packed 5.x files
application/x-starimpress:sdd:StarImpress 4.x presentations
application/vnd.ms-powerpoint:ppt:PowerPoint Slideshow
application/mspowerpoint:ppt,ppz,pps,pot:PowerPoint Slideshow
	OO()

application/vnd.sun.xml.math:sxm:OpenOffice Math 6.0 documents
application/so7_vnd.sun.xml.math:sxm:StarOffice 7.0 Math documents
application/vnd.stardivision.math:smf:StarMath 5.x documents
application/x-starmath:smf:StarMath 4.x documents
	OO()

```

---

### Post by guysmiley25 on 2007-05-04
Before I came across your page, my solution was to uninstall "evince-gtk" and then install evince.
```

sudo aptitude purge evince-gtk
sudo aptitude install evince

```

So I assumed that it was a problem with the evince-gtk package?

I still do not understand the abiword problem as it did work with Dapper. Why would it work then, and not now?

---

