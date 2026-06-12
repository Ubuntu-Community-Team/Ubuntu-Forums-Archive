---
title: "lfm file manager colors"
date: 2009-06-01
forum: General Help
---

### Post by luigi_mb on 2009-06-01
Ubuntu v9.04 (no desktop effects, no Compiz, etc.).

I have installed  lfm v0.91.2-1.1 (file manager) using Synaptic. When started it created ~/.lfmrc . This file includes color settings. It seems however that lfm does not use the specified colors. Has anybody experienced this problem? Any solution?

In case it helps, here is .lfmrc:

```

########## lfm - Last File Manager Configuration File ##########

[Programs]
web: seamonkey
shell: bash
ps: evince
video: mplayer
editor: nled
graphics: gthumb
pdf: evince
audio: mplayer
pager: pyview

[File Types]
ps: ps
web: html, htm
video: mpeg, mpg, avi, asf
graphics: png, jpeg, jpg, gif, tiff, tif, xpm, svg
pdf: pdf
audio: ogg, flac, mp3, wav, au, midi

[Bookmarks]
0: /
1: /
2: /
3: /
4: /
5: /
6: /
7: /
8: /
9: /

[Colors]
files: white black
selected_file: yellow black
help: green black
title: yellow blue
tabs: white blue
file_info: red black
source_files: cyan black
messages: magenta cyan
current_selected_file: yellow cyan
buttons: yellow red
graphics_files: magenta black
archive_files: yellow black
current_file: blue cyan
document_files: blue black
current_selected_file_otherpane: yellow white
data_files: magenta black
media_files: blue black
temp_files: white black
error_messages1: white red
error_messages2: black red
current_file_otherpane: black white

[Options]
# sort:	None = 0, byName = 1, byName_rev = 2, bySize = 3,
# 	bySize_rev = 4, byDate = 5, byDate_rev = 6
sort: 1
show_output_after_exec: 1
sort_mix_dirs: 0
manage_otherpane: 0
num_panes: 2
sort_mix_cases: 1
save_conf_at_exit: 1
color_files: 1
detach_terminal_at_exec: 1
rebuild_vfs: 0
show_dotfiles: 1

[Confirmations]
quit: 0
ask_rebuild_vfs: 1
overwrite: 1
delete: 1

[Files]
document_files: .txt, .text, .rtf, .odt, .odc, .odp, .abw, .gnumeric, .sxw, .sxc, .sxp, .sdw, .sdc, .sdp, .ps, .pdf, .dvi, .bib, .tex, .xml, .xsd, .xslt, .sgml, .dtd, .html, .shtml, .htm, .css, .mail, .msg, .letter, .ics, .vcs, .vcard, .lsm, .po, .man, .1, .info, .doc, .xls, .ppt, .pps
media_files: .mp2, .mp3, .mpg, .ogg, .flac, .mpeg, .wav, .avi, .asf, .mov, .mol, .mpl, .xm, .med, .mid, .midi, .umx, .wma, .acc, .wmv, .swf
archive_files: .gz, .bz2, .tar, .tgz, .Z, .zip, .rar, .7z, .arj, .cab, .lzh, .lha, .zoo, .arc, .ark, .rpm, .deb
source_files: .c, .h, .cc, .hh, .cpp, .hpp, .py, .pl, .pm, .inc, .rb., .asm, .pas, .f, .f90, .pov, .m, .pas, .cgi, .php, .phps, .tcl, .tk, .js, .java, .jav, .jasm, .diff, .patch, .sh, .bash, .awk, .m4, .el, .st, .mak, .sl, .ada, .caml, .ml, .mli, .mly, .mll, .mlp, .prg
data_files: .dta, .nc, .dbf, .mdn, .db, .mdb, .dat, .fox, .dbx, .mdx, .sql, .mssql, .msql, .ssql, .pgsql, .cdx, .dbi, .sqlite
temp_files: .tmp, .$$$, ~, .bak
graphics_files: .jpg, .jpeg, .gif, .png, .tif, .tiff, .pcx, .bmp, .xpm, .xbm, .eps, .pic, .rle, .ico, .wmf, .omf, .ai, .cdr, .xcf, .dwb, .dwg, .dxf, .svg, .dia

```

Thank you.

/luigi

---

### Post by luigi_mb on 2009-06-01
> **luigi_mb said:**
> Ubuntu v9.04 (no desktop effects, no Compiz, etc.).

I have installed  lfm v0.91.2-1.1 (file manager) using Synaptic. When started it created ~/.lfmrc . This file includes color settings. It seems however that lfm does not use the specified colors. Has anybody experienced this problem? Any solution?

In case it helps, here is .lfmrc:

```

########## lfm - Last File Manager Configuration File ##########

[Programs]
web: seamonkey
shell: bash
ps: evince
video: mplayer
editor: nled
graphics: gthumb
pdf: evince
audio: mplayer
pager: pyview

[File Types]
ps: ps
web: html, htm
video: mpeg, mpg, avi, asf
graphics: png, jpeg, jpg, gif, tiff, tif, xpm, svg
pdf: pdf
audio: ogg, flac, mp3, wav, au, midi

[Bookmarks]
0: /
1: /
2: /
3: /
4: /
5: /
6: /
7: /
8: /
9: /

[Colors]
files: white black
selected_file: yellow black
help: green black
title: yellow blue
tabs: white blue
file_info: red black
source_files: cyan black
messages: magenta cyan
current_selected_file: yellow cyan
buttons: yellow red
graphics_files: magenta black
archive_files: yellow black
current_file: blue cyan
document_files: blue black
current_selected_file_otherpane: yellow white
data_files: magenta black
media_files: blue black
temp_files: white black
error_messages1: white red
error_messages2: black red
current_file_otherpane: black white

[Options]
# sort:	None = 0, byName = 1, byName_rev = 2, bySize = 3,
# 	bySize_rev = 4, byDate = 5, byDate_rev = 6
sort: 1
show_output_after_exec: 1
sort_mix_dirs: 0
manage_otherpane: 0
num_panes: 2
sort_mix_cases: 1
save_conf_at_exit: 1
color_files: 1
detach_terminal_at_exec: 1
rebuild_vfs: 0
show_dotfiles: 1

[Confirmations]
quit: 0
ask_rebuild_vfs: 1
overwrite: 1
delete: 1

[Files]
document_files: .txt, .text, .rtf, .odt, .odc, .odp, .abw, .gnumeric, .sxw, .sxc, .sxp, .sdw, .sdc, .sdp, .ps, .pdf, .dvi, .bib, .tex, .xml, .xsd, .xslt, .sgml, .dtd, .html, .shtml, .htm, .css, .mail, .msg, .letter, .ics, .vcs, .vcard, .lsm, .po, .man, .1, .info, .doc, .xls, .ppt, .pps
media_files: .mp2, .mp3, .mpg, .ogg, .flac, .mpeg, .wav, .avi, .asf, .mov, .mol, .mpl, .xm, .med, .mid, .midi, .umx, .wma, .acc, .wmv, .swf
archive_files: .gz, .bz2, .tar, .tgz, .Z, .zip, .rar, .7z, .arj, .cab, .lzh, .lha, .zoo, .arc, .ark, .rpm, .deb
source_files: .c, .h, .cc, .hh, .cpp, .hpp, .py, .pl, .pm, .inc, .rb., .asm, .pas, .f, .f90, .pov, .m, .pas, .cgi, .php, .phps, .tcl, .tk, .js, .java, .jav, .jasm, .diff, .patch, .sh, .bash, .awk, .m4, .el, .st, .mak, .sl, .ada, .caml, .ml, .mli, .mly, .mll, .mlp, .prg
data_files: .dta, .nc, .dbf, .mdn, .db, .mdb, .dat, .fox, .dbx, .mdx, .sql, .mssql, .msql, .ssql, .pgsql, .cdx, .dbi, .sqlite
temp_files: .tmp, .$$$, ~, .bak
graphics_files: .jpg, .jpeg, .gif, .png, .tif, .tiff, .pcx, .bmp, .xpm, .xbm, .eps, .pic, .rle, .ico, .wmf, .omf, .ai, .cdr, .xcf, .dwb, .dwg, .dxf, .svg, .dia

```
...


Solved! I was misled by the item names in the [Colors] section. 
Let me add that in my opinion lfm is the best console file manager for Linux. 

/luigi

---

