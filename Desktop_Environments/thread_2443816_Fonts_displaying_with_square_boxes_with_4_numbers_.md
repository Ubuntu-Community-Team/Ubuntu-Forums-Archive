---
title: "Fonts displaying with square boxes with 4 numbers in"
date: 2020-05-20
forum: Desktop Environments
---

### Post by bobtedbob on 2020-05-20
Hi

I am using ubuntu 20.04 and I am having issues with some fonts not displaying. In font manager I can see this when the font displays example text with a square box with 4 numbers in the middle. The attached shows what it looks like for the font courier. there are other examples. I have tried rebuilding the font cache, reinstalling the fonts but nothing I have done seems to have fixed it. Does anyone know how to solve this issue?

Thanks

[ATTACH=CONFIG]285939[/ATTACH]

---

### Post by GhX6GZMB on 2020-05-21
Did you check if the font files are actually there? (/usr/share/fonts/truetype) (or opentype)
If yes, what's the ownership?   should be root:root
If OK, what are the permissions?    should be 644 for all font files, 755 for all font directories
Also be aware that each font family should be in it's own subdirectory (eg, all Courier font files in one directory).

Here's what my TrueType directory looks like:

> macro@macro-pc:/usr/share/fonts/truetype$ ls -la
total 308
drwxr-xr-x 76 root root 4096 Mai 12 23:13  .
drwxr-xr-x  8 root root 4096 Apr 23 09:34  ..
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Agency FB'
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Arial
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Bahnschrift
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Bell MT'
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Berlin Sans FB'
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Bodoni MT'
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Book Antiqua'
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Bookman Old Style'
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Caladea
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Calibri
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Californian FB'
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Calisto MT'
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Cambria
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Candara
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Carlito
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Century Gothic'
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Century Schoolbook'
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Comic Sans MS'
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Consolas
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Constantia
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Copperplate Gothic'
drwxr-xr-x  2 root root 4096 Mai  5 00:21  Corbel
drwxr-xr-x  2 root root 4096 Mai  5 00:21 'Courier New'
drwxr-xr-x  2 root root 4096 Mai 12 23:07  crosextra
drwxr-xr-x  2 root root 4096 Mai 12 22:55  dejavu
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'DejaVu Sans'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'DejaVu Sans Mono'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'DejaVu Serif'
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Elephant
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Eras ITC'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Franklin Gothic'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Franklin Gothic Book'
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Garamond
drwxr-xr-x  2 root root 4096 Mai 12 23:07  gentium
drwxr-xr-x  2 root root 4096 Mai 12 23:07  gentium-basic
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Gentium Basic'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Gentium Book Basic'
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Georgia
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Gill Sans'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Gill Sans MT'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Goudy Old Style'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'High Tower Text'
drwxr-xr-x  2 root root 4096 Apr 23 09:34  liberation
drwxr-xr-x  2 root root 4096 Mai 12 23:07  liberation2
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Linux Biolinum G'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Linux Libertine G'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Lucida Bright'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Lucida Fax'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Lucida Sans'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Lucida Sans Typewriter'
drwxr-xr-x  2 root root 4096 Mai 12 23:07  openoffice
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Open Sans'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Palatino Linotype'
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Perpetua
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Perpetua Titling MT'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'PT Serif'
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Rockwell
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Segoe Print'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Segoe Script'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Segoe UI'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Sitka Banner'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Sitka Display'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Sitka Heading'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Sitka Small'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Sitka Subheading'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Sitka Text'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'System Volume Information'
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Tahoma
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Terminal
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Times New Roman'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Trebuchet MS'
drwxr-xr-x  2 root root 4096 Mai  5 00:22 'Tw Cen MT'
drwxr-xr-x  2 root root 4096 Apr 23 09:35  ubuntu
-rw-r--r--  1 root root   36 Apr 23 09:36  .uuid
drwxr-xr-x  2 root root 4096 Mai  5 00:22  Verdana




And as an example, this is what the Arial subdirectory looks like:

> macro@macro-pc:/usr/share/fonts/truetype/Arial$ ls -la
total 4272
drwxr-xr-x  2 root root    4096 Mai  5 00:21 .
drwxr-xr-x 76 root root    4096 Mai 12 23:13 ..
-rw-r--r--  1 root root  980756 Mär 19  2019 arialbd.ttf
-rw-r--r--  1 root root  721144 Mär 19  2019 arialbi.ttf
-rw-r--r--  1 root root  717428 Mär 19  2019 ariali.ttf
-rw-r--r--  1 root root  180084 Jun 16  2017 ARIALNBI.TTF
-rw-r--r--  1 root root  180740 Jun 16  2017 ARIALNB.TTF
-rw-r--r--  1 root root  181124 Jun 16  2017 ARIALNI.TTF
-rw-r--r--  1 root root  175956 Jun 16  2017 ARIALN.TTF
-rw-r--r--  1 root root 1036584 Mär 19  2019 arial.ttf
-rw-r--r--  1 root root  167592 Mär 19  2019 ariblk.ttf
-rw-r--r--  1 root root      36 Mai  5 00:21 .uuid




---

