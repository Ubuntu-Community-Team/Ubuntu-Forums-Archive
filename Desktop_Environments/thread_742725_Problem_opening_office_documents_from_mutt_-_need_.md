---
title: "Problem opening office documents from mutt - need help"
date: 2008-04-02
forum: Desktop Environments
---

### Post by berbs on 2008-04-02
I need some help from people using mutt on hardy or gutsy. Each time I open a Microsoft word document from mutt, the file opens with open office but has lost its formatting. If I save the document and open it with ooo, no problem ?!?

I am looking for feedback from other mutt users. I haven't changed the default mailcap, but it does seem like some conversion happens. the attachment shows the right mime type "application/msword".

In any case, help would be greatly appreciated. I may post this one into other other forums to try to solve this problem which is really irritating.

---

### Post by andrew.46 on 2008-04-03
Hi,

A mailcap file does not come with mutt so you are using something provided by Ubuntu perhaps. Can you post the mailcap file?

                    Andrew

---

### Post by berbs on 2008-04-04
Here is the default /etc/mailcap from Hardy that I am using.

```

###############################################################################
#
#  MIME types and programs that process those types
#
#  Much of this file is generated automatically by the program "update-mime".
#  Please see the "update-mime" man page for more information.
#
#  Users can add their own rules if they wish by creating a ".mailcap"
#  file in their home directory.  Entries included there will take
#  precedence over those listed here.
#
###############################################################################


###############################################################################
#
#  User section follows:  Any entries included in this section will take
#  precedence over those created by "update-mime".  DO NOT CHANGE the
#  "User Section Begins" and "User Section Ends" lines, or anything outside
#  of this section!
#

# ----- User Section Begins ----- #
# -----  User Section Ends  ----- #

###############################################################################

application/vnd.oasis.opendocument.chart; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="OpenDocument Chart"; nametemplate=%s.odc
application/vnd.oasis.opendocument.spreadsheet; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="OpenDocument Spreadsheet"; nametemplate=%s.ods
application/vnd.oasis.opendocument.spreadsheet-template; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="OpenDocument Spreadsheet Template"; nametemplate=%s.ots
application/vnd.oasis.opendocument.graphics; soffice -draw '%s'; edit=soffice -draw '%s'; test=test -n "$DISPLAY"; description="OpenDocument Drawing"; nametemplate=%s.odg
application/vnd.oasis.opendocument.graphics-template; soffice -draw '%s'; edit=soffice -draw '%s'; test=test -n "$DISPLAY"; description="OpenDocument Drawing Template"; nametemplate=%s.otg
application/vnd.oasis.opendocument.presentation; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="OpenDocument Presentation"; nametemplate=%s.odp
application/vnd.oasis.opendocument.presentation-template; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="OpenDocument Presentation Template"; nametemplate=%s.otp
application/vnd.oasis.opendocument.text; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="OpenDocument Text Document"; nametemplate=%s.odt
application/vnd.oasis.opendocument.text-master; soffice -global '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="OpenDocument Master Document"; nametemplate=%s.odm
application/vnd.oasis.opendocument.text-template; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="OpenDocument Text Document Template"; nametemplate=%s.ott
application/vnd.oasis.opendocument.text-web; soffice -web '%s'; edit=soffice -web '%s'; test=test -n "$DISPLAY"; description="OpenDocument HTML Document Template"; nametemplate=%s.oth
text/plain; less '%s'; needsterminal
application/vnd.sun.xml.calc; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="OpenOffice.org Spreadsheet"; nametemplate=%s.sxc
application/vnd.sun.xml.calc.template; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="OpenOffice.org Spreadsheet Template"; nametemplate=%s.stc
application/vnd.sun.xml.draw; soffice -draw '%s'; edit=soffice -draw '%s'; test=test -n "$DISPLAY"; description="OpenOffice.org Drawing"; nametemplate=%s.sxd
application/vnd.sun.xml.draw.template; soffice -draw '%s'; edit=soffice -draw '%s'; test=test -n "$DISPLAY"; description="OpenOffice.org Drawing Template"; nametemplate=%s.std
application/vnd.sun.xml.impress; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="OpenOffice.org Presentation"; nametemplate=%s.sxi
application/vnd.sun.xml.impress.template; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="OpenOffice.org Presentation Template"; nametemplate=%s.sti
application/vnd.sun.xml.writer; soffice -writer '%s'; edit=soffice -writer '%s'; description="OpenOffice.org Text Document"; nametemplate=%s.sxw
application/vnd.sun.xml.writer.global; soffice -global '%s'; edit=soffice -writer '%s'; description="OpenOffice.org Master Document"; nametemplate=%s.sxg
application/vnd.sun.xml.writer.template; soffice -writer '%s'; edit=soffice -writer '%s'; description="OpenOffice.org Text Document Template"; nametemplate=%s.stw
video/mpeg; vlc '%s'; description="MPEG Video"; test=test -n "$DISPLAY"
video/x-mpeg; vlc '%s'; description="MPEG Video"; test=test -n "$DISPLAY"
video/mpeg-system; vlc '%s'; description="MPEG Video"; test=test -n "$DISPLAY"
video/x-mpeg-system; vlc '%s'; description="MPEG Video"; test=test -n "$DISPLAY"
audio/x-wav; vlc '%s'; description="WAV Audio"; nametemplate=%s.wav; test=test -n "$DISPLAY"
video/mpeg4; vlc '%s'; description="MPEG-4 Video"; test=test -n "$DISPLAY"
audio/mpeg; vlc '%s'; description="MPEG Audio"; nametemplate=%s.mpg; test=test -n "$DISPLAY"
audio/mpegurl; vlc '%s'; description="MPEG Audio URL"; nametemplate=%s.m3u; test=test -n "$DISPLAY"
audio/x-mp3; vlc '%s'; nametemplate=%s.mp3; description="MPEG Audio"; test=test -n "$DISPLAY"
audio/mpeg4; vlc '%s'; description="MPEG-4 Audio"; test=test -n "$DISPLAY"
application/mpeg4-iod; vlc '%s'; description="MPEG-4 Video"; test=test -n "$DISPLAY"
application/mpeg4-muxcodetable; vlc '%s'; description="MPEG-4 Video"; test=test -n "$DISPLAY"
application/pdf; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.pdf
application/x-pdf; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.pdf
application/x-bzpdf; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.pdf.gz
application/x-gzpdf; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.pdf.bz2
application/postscript; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.ps
application/x-bzpostscript; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.ps.bz2
application/x-gzpostscript; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.ps.gz
image/x-eps; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.eps
image/x-bzeps; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.eps.bz2
image/x-gzeps; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.eps.gz
application/x-dvi; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.dvi
application/x-gzdvi; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.dvi.gz
application/x-bzdvi; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.dvi.bz2
image/vnd.djvu; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.djvu
image/tiff; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.tiff
application/x-cbr; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.cbr
application/x-cbz; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.cbz
application/vnd.sun.xml.impress; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.sxd
application/vnd.oasis.opendocument.presentation; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.odp
application/x-arj; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/arj
application/x-bzip; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-bzip-compressed-tar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/bzip2
application/x-compress; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-compressed-tar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-gzip; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-java-archive; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-lha; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/lha
application/x-lzma; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/lzma
application/x-lzma-compressed-tar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/lzma
application/x-lzop; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /bin/lzop
application/x-lzop-compressed-tar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /bin/lzop
application/x-rar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/unrar -o -e /usr/bin/rar
application/x-rar-compressed; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/unrar -o -e /usr/bin/rar
application/x-stuffit; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-tar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/zip; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/unzip
application/x-zoo; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY" -a -e /usr/bin/zoo
application/x-ace; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-ar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-cpio; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-deb; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-gtar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-lhz; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-zip; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-zip-compressed; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
multipart/x-zip; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-rpm; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-jar; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-war; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-ear; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-cd-image; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-7z-compressed; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-gzpostscript; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-troff-man; /usr/bin/nroff -mandoc -Tutf8; copiousoutput; print=/usr/bin/nroff -mandoc -Tutf8 | print text/plain:-
application/x-java-jnlp-file; /usr/lib/j2se/1.4/jre/javaws/javaws '%s'
application/x-ogg; rhythmbox '%s'; description="Ogg Vorbis audio"; test=test -n "$DISPLAY"; nametemplate=%s.ogg
application/ogg; rhythmbox '%s'; description="Ogg Media"; test=test -n "$DISPLAY"
audio/x-mp3; rhythmbox '%s'; description="MP3 audio"; test=test -n "$DISPLAY"; nametemplate=%s.mp3
audio/x-scpls; rhythmbox '%s'; description="MP3 ShoutCast playlist"; test=test -n "$DISPLAY"; nametemplate=%s.pls
audio/x-mpeg; rhythmbox '%s'; description="MP3 audio"; test=test -n "$DISPLAY"
audio/mpeg; rhythmbox '%s'; description="MP3 audio"; test=test -n "$DISPLAY"
audio/x-mpegurl; rhythmbox '%s'; description="Playlist"; test=test -n "$DISPLAY"; nametemplate=%s.m3u
application/x-flac; rhythmbox '%s'; description="FLAC audio"; test=test -n "$DISPLAY"; nametemplate=%s.flac
application/x-java-jnlp-file; /usr/lib/jvm/java-6-sun-1.6.0.05/jre/javaws/javaws -viewer '%s'
application/x-tar; /bin/tar tvf -; print=/bin/tar tvf - | print text/plain:-; copiousoutput
application/x-gtar; /bin/tar tvzf -; print=/bin/tar tvzf - | print text/plain:-; copiousoutput
application/x-dvi; /usr/bin/xdvi '%s'; description=TeX DVI; test=test -n "$DISPLAY"; nametemplate=%s.dvi
application/x-bittorrent; transmission '%s'; description="GTK-based BitTorrent client"; test=test -n "$DISPLAY"
text/plain; more '%s'; needsterminal
image/*; evince '%s'; test=test -n "$DISPLAY"; nametemplate=%s.dummy
text/plain; view '%s'; edit=vim '%s'; compose=vim '%s'; needsterminal
text/plain; gview -f '%s'; edit=gvim -f '%s'; compose=gvim -f '%s'; test=test "$DISPLAY" != ""
video/mpeg; vlc -I rc -V caca '%s'; needsterminal; description="MPEG Video"
video/x-mpeg; vlc -I rc -V caca '%s'; needsterminal; description="MPEG Video"
video/mpeg-system; vlc -I rc -V caca '%s'; needsterminal; description="MPEG Video"
video/x-mpeg-system; vlc -I rc -V caca '%s'; needsterminal; description="MPEG Video"
audio/x-wav; vlc -I rc -V caca '%s'; nametemplate=%s.wav; needsterminal; description="WAV Audio"
video/mpeg4; vlc -I rc -V caca '%s'; needsterminal; description="MPEG-4 Video"
audio/mpeg; vlc -I rc -V caca '%s'; nametemplate=%s.mpg; needsterminal; description="MPEG Audio"
audio/mpegurl; vlc -I rc -V caca '%s'; nametemplate=%s.m3u; needsterminal; description="MPEG Audio URL"
audio/x-mp3; vlc -I rc -V caca '%s'; nametemplate=%s.mp3; needsterminal; description="MPEG Audio"
audio/mpeg4; vlc -I rc -V caca '%s'; needsterminal; description="MPEG-4 Audio"
application/mpeg4-iod; vlc -I rc -V caca '%s'; needsterminal; description="MPEG-4 Video"
application/mpeg4-muxcodetable; vlc -I rc -V caca '%s'; needsterminal; description="MPEG-4 Video"
video/x-msvideo; vlc '%s'; description="MS Video (AVI)"; test=test -n "$DISPLAY"
video/quicktime; vlc '%s'; description="Apple Quicktime Video"; test=test -n "$DISPLAY"
application/ogg; vlc '%s'; nametemplate=%s.ogg; description="Ogg stream"; test=test -n "$DISPLAY"
application/x-ogg; vlc '%s'; nametemplate=%s.ogg; description="Ogg stream"; test=test -n "$DISPLAY"
application/x-ms-asf-plugin; vlc '%s'; description="Windows Media Video"; test=test -n "$DISPLAY"
application/x-mplayer2; vlc '%s'; description="Windows Media"; test=test -n "$DISPLAY"
text/html; /usr/bin/w3m -T text/html '%s'; needsterminal; description=HTML Text; nametemplate=%s.html
text/html; /usr/bin/lynx -force_html '%s'; needsterminal; description=HTML Text; nametemplate=%s.html
text/csv; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="CSV Document"; nametemplate=%s.csv
text/spreadsheet; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Spreadsheet Interchange Document"; nametemplate=%s.slk
application/x-quattropro; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Quattro Pro 6 for Windows Spreadsheet"; nametemplate=%s.wb2
application/x-dbf; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="xBase Document"; nametemplate=%s.dbf
application/vnd.ms-excel.sheet.macroEnabled.12; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Office Open XML Spreadsheet with Macros Enabled"; nametemplate=%s.xlsm
application/vnd.ms-excel.template.macroEnabled.12; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Office Open XML Spreadsheet Template with Macros Enabled"; nametemplate=%s.xltm
application/vnd.openxmlformats-officedocument.spreadsheetml.sheet; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Office Open XML Spreadsheet"; nametemplate=%s.xlsx
application/vnd.openxmlformats-officedocument.spreadsheetml.template; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Office Open XML Spreadsheet Template"; nametemplate=%s.xltx
application/vnd.lotus-1-2-3; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Lotus 1-2-3 spreadsheet"; nametemplate=%s.123
application/vnd.ms-excel; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Microsoft Excel Document"; nametemplate=%s.xls
application/msexcel; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="Microsoft Excel Document"; nametemplate=%s.xls
application/x-dbase; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="xBase Document"; nametemplate=%s.dbf
text/x-csv; soffice -calc '%s'; edit=soffice -calc '%s'; test=test -n "$DISPLAY"; description="CSV Document"; nametemplate=%s.csv
application/vnd.ms-powerpoint.presentation.macroEnabled.12; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Office Open XML Presentation with Macros Enabled"; nametemplate=%s.pptm
application/vnd.ms-powerpoint.slideshow.macroEnabled.12; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Office Open XML Presentation Slide Show with Macros Enabled"; nametemplate=%s.ppsm
application/vnd.ms-powerpoint.template.macroEnabled.12; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Office Open XML Presentation Template with Macros Enabled"; nametemplate=%s.potm
application/vnd.openxmlformats-officedocument.presentationml.presentation; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Office Open XML Presentation"; nametemplate=%s.pptx
application/vnd.openxmlformats-officedocument.presentationml.slideshow; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Office Open XML Presentation Slide Show"; nametemplate=%s.ppsx
application/vnd.openxmlformats-officedocument.presentationml.template; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Office Open XML Presentation Template"; nametemplate=%s.potx
application/vnd.ms-powerpoint; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Microsoft PowerPoint Document"; nametemplate=%s.ppt
application/mspowerpoint; soffice -impress '%s'; edit=soffice -impress '%s'; test=test -n "$DISPLAY"; description="Microsoft PowerPoint Document"; nametemplate=%s.ppt
application/rtf; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Rich Text Format"; nametemplate=%s.rtf
application/x-extension-txt; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Plain Text Document"; nametemplate=%s.txt
application/x-t602; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="T602 Document"; nametemplate=%s.602
application/vnd.wordperfect; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="WordPerfect Document"; nametemplate=%s.wp
application/vnd.ms-word.document.macroEnabled.12; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Office Open XML Document with Macros Enabled"; nametemplate=%s.docm
application/vnd.ms-word.template.macroEnabled.12; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Office Open XML Document Template with Macros Enabled"; nametemplate=%s.dotm
application/vnd.openxmlformats-officedocument.wordprocessingml.document; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Office Open XML Document"; nametemplate=%s.docx
application/vnd.openxmlformats-officedocument.wordprocessingml.template; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Office Open XML Document Template"; nametemplate=%s.dotx
application/msword; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Microsoft Word Document"; nametemplate=%s.doc
application/vnd.ms-works; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Microsoft Works Document"; nametemplate=%s.wps
application/wordperfect; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="WordPerfect Document"; nametemplate=%s.wp
text/plain; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Plain Text Document"; nametemplate=%s.txt
text/rtf; soffice -writer '%s'; edit=soffice -writer '%s'; test=test -n "$DISPLAY"; description="Rich Text Format"; nametemplate=%s.rtf
video/x-msvideo; vlc -I rc -V caca '%s'; needsterminal; description="MS Video (AVI)"
video/quicktime; vlc -I rc -V caca '%s'; needsterminal; description="Apple Quicktime Video"
application/ogg; vlc -I rc -V caca '%s'; nametemplate=%s.ogg; needsterminal; description="Ogg stream"
application/x-ogg; vlc -I rc -V caca '%s'; nametemplate=%s.ogg; needsterminal; description="Ogg stream"
application/x-ms-asf-plugin; vlc -I rc -V caca '%s'; needsterminal; description="Windows Media Video"
application/x-mplayer2; vlc -I rc -V caca '%s'; needsterminal; description="Windows Media"
text/html; /usr/bin/w3m -dump -T text/html '%s'; copiousoutput; description=HTML Text; nametemplate=%s.html
text/html; /usr/bin/html2text '%s'; copiousoutput; description=HTML Text
text/html; /usr/bin/lynx -dump -force_html '%s'; copiousoutput; description=HTML Text; nametemplate=%s.html
text/*; less '%s'; needsterminal
text/*; view '%s'; edit=vim '%s'; compose=vim '%s'; needsterminal
text/*; gview -f '%s'; edit=gvim -f '%s'; compose=gvim -f '%s'; test=test "$DISPLAY" != ""
text/html; /usr/bin/sensible-browser '%s'; description=HTML Text; nametemplate=%s.html
text/*; more '%s'; needsterminal
application/x-debian-package; /usr/lib/mime/debian-view '%s'; needsterminal; description=Debian GNU/Linux Package; nametemplate=%s.deb
audio/basic; /usr/lib/mime/playaudio '%s'; description=Basic uLaw Audio; nametemplate=%s.au

```

---

### Post by andrew.46 on 2008-04-04
Hi,

 That is a huge mess of a file! Can I suggest that you make your own mailcap file, source it from mutt and slowly build it up?

```
$ touch ~/.mailcap_mutt
```

And then the following in your ~/.muttrc:

```
set mailcap_path="~/.mailcap_mutt"
```

From here construct your own mailcap file, pillaging sections from the system files as required. Perhaps something simple like:

```
application/msword;  soffice -writer '%s'
```

would be a good start, although I have not tested this.

        Andrew

---

