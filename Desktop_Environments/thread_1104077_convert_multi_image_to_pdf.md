---
title: "convert multi image to pdf?"
date: 2009-03-23
forum: Desktop Environments
---

### Post by fukid on 2009-03-23
us there any software that can convert multi image into a pdf file?:confused::confused:

---

### Post by rozbarwinek on 2009-03-23
Please give more info, you want to print few pictures in one pdf file?
Open your image and go to File/Print, change PS to PDF and print :)

---

### Post by kaibob on 2009-03-23
> **fukid said:**
> us there any software that can convert multi image into a pdf file?:confused::confused:

It depends on the image type, but Imagemagick convert (a command-line tool) will do this:

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by hellocatfood on 2009-08-25
Is there a program with a GUI that can convert multiple-page pdfs to images?

---

### Post by shailesh138 on 2010-09-29
Hi.........this tutorial is only for Ubuntu user..........

            1) Collect all images in one folder. As per your sequence .

            2) Then right Click on folder
                                          >>Compress as cbz

            3) that's all enjoy...............the folder is converted as compress Image file & rather than pdf in ubuntu you can open it Ubuntus document viewer

---

### Post by mkrate on 2011-09-11
shailes123: THANK YOU!!! Now all I have to do is convert to pdf or ePub (easy enough), and I can read Alan Ford on my Kobo :)

---

### Post by Primefalcon on 2011-12-20
I was just looking up the same and since there was a fairly recent post here as well, I'll just answer a way to make a pdf like this

install imagemagick via ```
sudo apt-get install imagemagick
```

then just put all the images you want into a pdf foler (i'd recommend using jpeg) for this.... into one folder sequentially numbered in the order you wish to be... 

```
convert -compress jpeg * outputFile.pdf
```

voila, you have an actual PDF file

---

