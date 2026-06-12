---
title: "From svg to png"
date: 2006-02-03
forum: Desktop Environments
---

### Post by christooss on 2006-02-03
Is there application/script that can change bunch of pictures in svg format to png.

I appriciate all the anwsers. Bye

---

### Post by firecat53 on 2006-02-03
Inkscape can save svg as png pix.  Not sure about bulk tools, though. You can check out Imagemagick. Not sure of their svg support, but I think so.

Scott

---

### Post by christooss on 2006-02-03
I can do this in Gimp. But I don't have one picture to convert

---

### Post by christooss on 2006-02-04
[http://linux.about.com/od/commands/l/blcmdl1_convert.htm](http://linux.about.com/od/commands/l/blcmdl1_convert.htm)

I found application called convert. But its not in repositories. Wierd cause as link say app is default one

---

### Post by GeneralZod on 2006-02-04
[QUOTE=christooss][http://linux.about.com/od/commands/l/blcmdl1_convert.htm](http://linux.about.com/od/commands/l/blcmdl1_convert.htm)

I found application called convert. But its not in repositories. Wierd cause as link say app is default one[/QUOTE]

You really should have it.  It's part of the imagemagick package.

---

### Post by christooss on 2006-02-06
Yes with install inmagemagick everything is on the right place :)

Thanks

---

### Post by delfick on 2007-07-16
i have the same question...

so if i have 60 svg images in a directory called ~/svg

and i want to convert them all to pngs of 50px in height (and keep proportion)

how would i do that ??

thnx for help :D

---

### Post by mbsullivan on 2007-07-17
> i have the same question...

so if i have 60 svg images in a directory called ~/svg

and i want to convert them all to pngs of 50px in height (and keep proportion)

how would i do that ??

thnx for help 

Assuming that ImageMagick tools / convert work (they seem to, judging from the previous responses), you could follow the following steps to convert all into .png files:

(1) Install imagemagick suite

```
sudo aptitude install imagemagick
```

(2) Resize and convert all .svg files (from containing folder)

```
mogrify -resize x50 -format png *.svg
```

(3) Move resulting files to correct folder

```
mkdir ~/svg
mv *.png ~/svg
```

Hope this helps!  

Mike

---

### Post by delfick on 2007-07-17
thankyou :D

unfortunately the png versions don't looks so good :(

attached is a screenshot (yes they are the plugin icons from the compiz ccsm)

---

### Post by mbsullivan on 2007-07-18
Hmm... SVG is a complex format, and Imagemagick doesn't seem to have full support for them, as of yet.  It should work with most SVGs, but you must be out of luck in that arena.

Will Gimp convert the images?  Try one.  If it does, let m know and we'll work on putting together a Gimp batch script to do the conversion.

Mike

---

### Post by delfick on 2007-07-18
gimp2.2 doesn't work, probably because mine doesn't have svg enabled...

so i installed gimp2.3 with svg support and it works perfectly...

>  If it does, let m know and we'll work on putting together a Gimp batch script to do the conversion.

awsome :D

thankyou :D

---

### Post by delfick on 2007-07-20
actually, don't worry about it, i found this 

> for i in *.svg; do inkscape -f "$i" -e "$i.png" -w 50; done

works perfectly :D

thnx for your help anyway :D

---

### Post by mattfarmerdotnet on 2007-08-29
> **delfick said:**
> actually, don't worry about it, i found this 

```
for i in *.svg; do inkscape -f "$i" -e "$i.png" -w 50; done
```

works perfectly :D

thnx for your help anyway :D

Hey thanks for this post.  Inkscape is a little bigger than what I was looking for, but this works for now.  A small tweak to your example:

```
for i in *.svg; do inkscape -f "$i" -e "${i%%.svg*}.png" -w 50; done
```

This will strip off the .svg tag and put on the .png.

---

### Post by delfick on 2007-08-29
cool, thnx :D

that's much better :D

---

### Post by stani on 2007-08-29
In case you want to batch many non-svg images, have a look at phatch:
[http://ubuntuforums.org/showthread.php?p=2796331](http://ubuntuforums.org/showthread.php?p=2796331)

---

### Post by delfick on 2007-08-29
cool, thnx :D

---

