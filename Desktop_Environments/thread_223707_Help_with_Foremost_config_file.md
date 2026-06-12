---
title: "Help with Foremost config file"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Joseph Elliott on 2006-07-26
Ok long story short.  I screwed with my partitions now I need to fix them.  AZZ has helped me alot but i dont want to continue to bug him all the time.  I'm not sure which parts of the config file I should edit.

here is a section of the file.  I realize that i need to remove the # from the ones i want  but can someone show me exactly which lines i need to remove # from and do the values in the lines have to be changed or can they stay as they are.  I have no idea what the values mean or what i should change them to.


# GRAPHICS FILES
#---------------------------------------------------------------------	
#
#
# AOL ART files
#	art	y	150000	\x4a\x47\x04\x0e	\xcf\xc7\xcb
#  	art	y 	150000	\x4a\x47\x03\x0e	\xd0\xcb\x00\x00
#
# GIF and JPG files (very common)
#	(NOTE THESE FORMATS HAVE BUILTIN EXTRACTION FUNCTION)
#	gif	y	155000000	\x47\x49\x46\x38\x37\x61	\x00\x3b
#  	gif	y 	155000000	\x47\x49\x46\x38\x39\x61	\x00\x00\x3b
#  	jpg	y	20000000	\xff\xd8\xff\xe0\x00\x10	\xff\xd9
#  	jpg	y	20000000	\xff\xd8\xff\xe1 \xff\xd9 
#  	jpg	y	20000000	\xff\xd8	\xff\xd9
#
# PNG   (used in web pages)
#	(NOTE THIS FORMAT HAS A BUILTIN EXTRACTION FUNCTION)
#  	png	y	200000	\x50\x4e\x47?	\xff\xfc\xfd\xfe
#
#
# BMP 	
#	(NOTE THIS FORMAT HAS A BUILTIN EXTRACTION FUNCTION)
#	bmp	y	100000	BM??\x00\x00\x00
#
# TIF
#  	tif	y	200000000	\x49\x49\x2a\x00


thanks ahead
Joseph

---

### Post by klick on 2006-08-12
Im messing around with foremost myself, and this is what ive figured out if it helps you.  The config file is where you choose which type of files you want to recover.  say you want all jpg's gifs, and AVI's  you would uncomment the following to make them look like this....
# GIF and JPG files (very common)
        gif     y       155000000       \x47\x49\x46\x38\x37\x61        \x00\x3b
        gif     y       155000000       \x47\x49\x46\x38\x39\x61        \x00\x00\x3b
        jpg     y       200000000       \xff\xd8\xff\xe0\x00\x10        \xff\xd9

# AVI (Windows animation and DiVX/MPEG-4 movies)
        avi     y       4000000 RIFF????AVI

then you run a command like this from root

foremost -v /dev/sda

or whereever the disc/image is you want to scan

it will output all the files it has to the dir you run that command form, or you can use -o to specify a new directory, hope this helps

---

