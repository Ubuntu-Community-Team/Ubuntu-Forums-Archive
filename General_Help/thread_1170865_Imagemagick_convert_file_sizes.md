---
title: "Imagemagick convert file sizes"
date: 2009-05-26
forum: General Help
---

### Post by kaibob on 2009-05-26
I've been getting some weird file sizes with Imagemagick since upgrading to Jaunty. To illustrate, I used the import utility to create a screenshot of the Ubuntu forums front page with:

```
import -frame import.png
```

The file size was 267 KB.

I then did the same thing except used pdf format:

```
import -frame import.pdf
```

The size was 147 KB.

Finally, I converted the PNG screenshot taken above to pdf format with:

```
convert import.png import.pdf
```

The file size was 2.2 MB.

I use convert a lot and have never seen this increase in size. I tried the -resize option to get file sizes down, but the resulting PDF was of poor quality.

Anyone experiencing this issue or better yet have a solution.

---

### Post by kaibob on 2009-05-27
I decided to go back to Hardy, after which I reran the commands in my first post. The file sizes under Jaunty and Hardy are:

```
import -frame import.png
```

Jaunty: 267 KB

Hardy: 255 KB

```
import -frame import.pdf
```

Jaunty: 147 KB

Hardy: 141 KB

```
convert import.png import.pdf
```

Jaunty: 2.2 MB

Hardy: 140 KB

Jaunty doesn't really add anything that I need, so I'll stick with Hardy for now.

---

### Post by kaibob on 2009-08-02
I decided to give Jaunty another try and came across a fix for the situation described above. It does not appear to be an issue for anyone else, but I thought I would post what I found just in case.

The fix is to use the -compress option. Compression types that I tried are Zip, BZip, and LZW. With Zip and BZip compression, file size was about a tenth of that without this option. For example, 

```
convert input.png -compress Zip export.pdf
```

I was curious and tried the compress option with PNG files, but it made no difference.

---

### Post by kk_furtiva on 2009-12-07
I'm having this problem too. Using -compress and/or -quality the PNG image size actually increases!

It seems that moving from 6.3.7 to 6.5.6 fixes the problem
([http://stackoverflow.com/questions/1492056/imagemagick-png-resize-increases-file-size](http://stackoverflow.com/questions/1492056/imagemagick-png-resize-increases-file-size))

---

