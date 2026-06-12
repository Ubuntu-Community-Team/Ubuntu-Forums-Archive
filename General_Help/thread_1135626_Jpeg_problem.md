---
title: "Jpeg problem"
date: 2009-04-24
forum: General Help
---

### Post by tom2oz on 2009-04-24
2 questions really......

1. I have created a label and have saved it as .odt - as this was the only option available to me upon saving.  I have also created an PDF format of the image.

However i need to convert the document to jpeg if this is possible?  How would i go about doing so.


2. Finally can anyone recommend any good drawing/design programs for ubuntu that will enable me to save as .jepg?  A similar set up to MS publisher back in the day, dare i say it LOL!

---

### Post by DeMus on 2009-04-24
> **tom2oz said:**
> 2 questions really......

1. I have created a label and have saved it as .odt - as this was the only option available to me upon saving.  I have also created an PDF format of the image.

However i need to convert the document to jpeg if this is possible?  How would i go about doing so.


2. Finally can anyone recommend any good drawing/design programs for ubuntu that will enable me to save as .jepg?  A similar set up to MS publisher back in the day, dare i say it LOL!

Did you create a file in OpenOffice Writer and saved it as .odt? Can't you select the drawing/picture in your file, right-click on it and select save as...? I'm not entirely sure but I think it might work.

For picture editing I would select The Gimp, the Linux counterpart of Photoshop.

For MS Publisher you can choose:
Artstream
PageStream
Passepartout
Scribus
VivaDesigner

I got this info from a web page called:
[http://linuxappfinder.com/alternatives?page=1]("http://linuxappfinder.com/alternatives?page=1")

Here you can find many replacements.

---

### Post by tom2oz on 2009-04-24
Tried what you suggested and it did not work unfortunately.  Thanks i will take a look @ some of them....

---

### Post by _Purple_ on 2009-04-24
You can convert pdf files into jpg files using imagemagick.

To install imagemagick:
```
sudo apt-get install imagemagick
```

To convert pdf file into jpg file, go to to directory where you have the pdf file:
```
convert your_pdf_filename.pdf jpg_filename.jpg
```

---

### Post by tom2oz on 2009-04-24
> **_Purple_ said:**
> You can convert pdf files into jpg files using imagemagick.

To install imagemagick:
```
sudo apt-get install imagemagick
```

To convert pdf file into jpg file, go to to directory where you have the pdf file:
```
convert your_pdf_filename.pdf jpg_filename.jpg
```

Cheers for that....I have done the top install, no new app's added to the tool bar but the terminal said the install was a success. 

However I don't quite understand what is meant by the second part of your post.  Could you please elaborate, I am new to the unbutu OS.

Thanks...

---

### Post by Screwdriver0815 on 2009-04-24
> **tom2oz said:**
> Cheers for that....I have done the top install, no new app's added to the tool bar but the terminal said the install was a success. 

However I don't quite understand what is meant by the second part of your post.  Could you please elaborate, I am new to the unbutu OS.

Thanks...

the second part of the post tells you the command to convert the pdf file to the desired jpg file.

Imagemagick is a commandline program, so you can run it only via the terminal. But it works great as long as you know the command. Because it is a commandline program you don't get any new entry in the applications menu

So if you want to convert the pdf file into the jpg:

1. you have to change into the folder where the pdf file is saved:

open the terminal and type into it:

```
cd name_of_the_directory
```

you have to change "name_of_the_directory" into the actual name of it, where you have saved the pdf file. Maybe its like /home/user/directory, where "user" means your username. 

2. type in the command, _purple_ has given to you:

```
convert pdffile.pdf jpgfile.jpg
```

you have to exchange "pdffile" and "jpgfile" with the actual names of the files. For the jpg-file, which you want to create you can type in any name you want, but don't use space blanks in it as the commandline will interprete it somehow silly.

after you hit return, the jpg file will be created in the directory where you have the pdf file.

good luck!

---

### Post by tom2oz on 2009-05-06
Thanks I will give that a try soon....

---

