---
title: "bash script problem"
date: 2009-05-03
forum: General Help
---

### Post by max_power on 2009-05-03
I wrote a script to convert my mpg videos into flv. 

Everything works except it will only convert the first video in the list and then quit. Can someone give this a quick look and point out what might be the problem.

Thanks


```
#!/bin/bash

flvExt=".flv"
jpgExt=".jpg"

#list all the mpg files in the folder and pipe them to a file
cd /home/chris/Desktop/videos
ls -F  *.mpg  > mpg_list.txt

#read the mpg list file and perform an action on each line
cat mpg_list.txt |
while read a; do
newflv=$a$flvExt 
echo $newflv
ffmpeg -i $a -vcodec flv -f flv -r 29.97 -s 320x180 -aspect 16:9 -b 300kb -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -ac 1 -ar 22050 -ab 56kb "$newflv"
rm $a
done

#list all the flv files in the folder and pipe them to a file
ls -F  *.flv  > flv_list.txt

#read the flv list file and perform an action on each line
cat flv_list.txt |
while read b; do
cp $b /var/www/videos/$b
rm $b
done

#list all the png files in the folder and pipe them to a file
ls -F  *.png  > png_list.txt

#read the flv list file and perform an action on each line
cat png_list.txt |
while read c; do
newjpg=$c$jpgExt
ffmpeg -i $c $newjpg
cp $newjpg /var/www/videos/$newjpg
rm $c
rm $newjpg
done

rm mpg_list.txt
rm png_list.txt
rm flv_list.txt


```

---

### Post by ghostdog74 on 2009-05-03
put set -x at the top of your script just below the shebang, run the script again and see if it shows you anything...

---

### Post by kayvortex on 2009-05-03
Yeah, adding set -x is useful, or alternatively, run your script like:
```
bash -x *script*
```
This will show you exactly what the shell is doing as it runs through the script.

At a cursory glance, doing
> ls -F  *.mpg  > mpg_list.txt
looks "dangerous" since if you've enabled colours, redirecting ls to a file will also store the colour escape codes. Don't delete the files and take a look what's in them. As a replacement, just do something like:
```
for i in *.mpg ; do
*ffmpeg ... $i ...*
done
```

---

### Post by max_power on 2009-05-03
> **kayvortex said:**
> 
```
for i in *.mpg ; do
*ffmpeg ... $i ...*
done
```

awesome thanks. i didn't know one could search a folder like that like. I was using "find -name *.mpg" but i couldn't figure out how to just get the file name and not the path.

The conversion takes a bit but i will post the results as soon as its finished.

---

### Post by max_power on 2009-05-03
Here's my new updated script:

```
#!/bin/bash
set -x

flvExt=".flv"
jpgExt=".jpg"

#convert the mpgs to flvs then delete the mpg
for i in *.mpg; do
newflv=$i$flvExt 
ffmpeg -i $i -vcodec flv -f flv -r 29.97 -s 320x180 -aspect 16:9 -b 300kb -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -ac 1 -ar 22050 -ab 56kb "$newflv"
rm $i
#move the flv to a new folder
cp $newflv /var/www/videos/$newflv
rm $newflv
done

#convert the png thumbnails to jpg
for i in *.png; do
newjpg=$i$jpgExt
ffmpeg -i $c $newjpg
cp $newjpg /var/www/videos/$newjpg
rm $i
rm $newjpg
done

```

I'm waiting for the conversion to finish. I'll post results.

Thanks for the help

---

### Post by max_power on 2009-05-03
Works perfectly. Thanks everyone

---

### Post by kayvortex on 2009-05-04
Don't mention it.
(Don't forget to remove "set -x" now that your script works OK!)

---

