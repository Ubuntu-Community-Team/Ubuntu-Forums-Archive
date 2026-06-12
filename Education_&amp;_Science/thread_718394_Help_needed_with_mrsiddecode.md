---
title: "Help needed with mrsiddecode"
date: 2008-03-08
forum: Education &amp; Science
---

### Post by skywatcher on 2008-03-08
PLEASE IGNORE -- PROBLEM FOUND!

Has anyone had any experience with using LizardTech's mrsid(geo)decode utility?  I downloaded it, unpacked it and changed the permissions etc., but when I try to use it (on Dapper), e.g. as follows

```
mrsidgeodecode -i input.sid -o output.jpg
```

I get

```
bash: mrsidgeodecode: command not found
```

Please can someone point me in the right direction.

Thanks.

---

### Post by caitifty on 2009-01-02
Just a guess for other complete newbies with the same problem:

./mrsidgeodecode -i input.sid -o output.jpg

You also need libstdc++ version 5 or above installed for this converter to work:

sudo apt-get install libstdc++5

ps the best output format to use with sid files is tifg - tiff with geodata embedded.  sid files are almost always raster map data, so keeping the embedded geodata is useful if you're going to use it in any other mapping program (like Grass GIS or QGIS):

./mrsidgeodecode -i input.sid -o output.tifg -of tifg

This produces much bigger files though - if you're just trying to have a quick look at what's in the file, go with .jpg (the first example).

Pete

---

### Post by skywatcher on 2009-01-04
Thanks, caitifty.

I found that the tif format works with QGIS, but then the coordinates are not shown in degrees.  As you say, tifg is the format to use if you want QGIS to display map coordinates in degrees.

By the way, may I point out a small error in the command line that you provided:

./mrsidgeodecode -i input.sid -o output.tifg -of tifg 

should read

./mrsidgeodecode -i input.sid -o output.tif -of tifg

Otherwise, mrsidgeodecode generates an output file with extention tifg, which QGIS does not recognise.  Of course, one could also use

./mrsidgeodecode -i input.sid -o output.tifg

but then it is necessary to rename output.tifg to output.tif, which works correctly with QGIS.

---

