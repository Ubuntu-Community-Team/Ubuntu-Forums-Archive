---
title: "WMV/ASF problem with mplayer"
date: 2005-12-07
forum: General Help
---

### Post by bananaman on 2005-12-07
Ok, so this is the problem:
When I double click a wmv file to be oppened in mplayer, this is what i get:

-------------------------------------
The filename "test.wmv" indicates that this file is of type "Microsoft
WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.
 
" Do not open the file unless you created the file yourself, or received
the file from a trusted source. To open the file, rename the file to the
correct extension for "Microsoft ASF video", then open the file
normally. Alternatively, use the Open With menu to choose a specific application
for the file." 
-------------------------------------

Ths is easily fixed by changing the extension from wmv to asf...but its a hassle to do that for every single video... It also works if I right-click and select Open with...
but i dont want to do that every time, i just want to double click and watch...

So if you know a way to get around this Id be very thankful, its very annoying and there must be a way for Nautilus to not care what the content says and just play the damn file... 

Thanks in advance...

---

### Post by infoburner on 2005-12-27
you can write a quick shell script that will rename all the files for you. open a terminal and change to the directory that contains the filesyou need to rename and type :
<CODE>
for i in `ls *.asf`
do
mv $i $i.wmv
done
</CODE>

---

### Post by kaamos on 2005-12-27
This apparently worked: [http://ubuntuforums.org/showthread.php?t=108136](http://ubuntuforums.org/showthread.php?t=108136)

---

