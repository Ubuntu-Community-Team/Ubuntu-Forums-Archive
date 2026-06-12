---
title: "Open Office"
date: 2006-02-08
forum: Desktop Environments
---

### Post by Icebear on 2006-02-08
Hi

Why when I  use open office writer in ubuntu what fits on one page and when the same document is loaded into open office writer in window it has more lines per page? In Windows there is about another 3 lines of text per page. The paper  is for both A4 and same margine.

---

### Post by Denis on 2006-02-08
I assume this is because of the font that is used. Most likely you are using another font in Ubuntu, one that Windows doesn't have. 

Most word processor file formats (like ODT e.g.) do not include the font itself. So if your operation system doesn't have the font, it uses another one. 
This can result in the font being a bit smaller or larger. Different fonts have different sizes even though you specified the same font size. 

If you want it to be exactly the same, you would have to copy the font that is used in your document to the other operating system.

---

### Post by darehanl on 2006-02-08
This can be a bit unrelated, but I'll just write this.

You can go to **Options > OpenOffice.org > Fonts** and use the table there. For example, if you change **Microsoft Sans Serif** to something like **Roman**, a document with Microsoft Sans Serif letters will look like it uses Roman.

---

### Post by BlackJack on 2006-02-08
I have had the same problem with fonts and formatting between Word and OpenOffice. Only problem is that I can not figure out how to import the fonts into OpenOffice.

Can anybody tell me how I can get these fonts out of Word and into OpenOffice?

Right now I an looking at CrossOver Office so that I can continue to run Word, but I would prefer not to run word at all if I don't have to.

Thanks............

---

### Post by ubuntu27 on 2006-02-09
[QUOTE=BlackJack]I have had the same problem with fonts and formatting between Word and OpenOffice. Only problem is that I can not figure out how to import the fonts into OpenOffice.

Can anybody tell me how I can get these fonts out of Word and into OpenOffice?

Right now I an looking at CrossOver Office so that I can continue to run Word, but I would prefer not to run word at all if I don't have to.

Thanks............[/QUOTE]

Well, you can copy your Windows' fonts that are in
C:\Windows\Fonts\

to the Ubuntu's Font folder which I don't know where it is :P
I think it is on /Fonts

The TrueType fonts are the one which will work if I remember correctly...

Sorry I am not much of a help. 
Hope somone here could point you out with the solution.

---

### Post by nanotube on 2006-02-09
simplest way to install fonts is to copy them over to the .fonts directory in your home directory. (ie, /home/<username>/.fonts). the dir does not exist by default, so have to create it.
for more info, see [https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto)

---

### Post by BlackJack on 2006-02-09
Well I copied my Windows\Fonts directory and renamed it to .fonts. I then went into OpenOffice Write and all the fonts were there and my pagination was correct.

Worked like a charm!

Thanks............

---

### Post by ronmarley1 on 2006-02-09
I've found great help with OOo here: [http://www.oooforum.org/](http://www.oooforum.org/)

---

### Post by nanotube on 2006-02-10
blackjack: glad to know it worked for you. have fun. :)

---

### Post by ubuntu27 on 2006-02-12
BTY, Talking about OpenOffice. I think you guys will be interested in OO.o Tutorials and Guides ;)

[http://www.tutorialsforopenoffice.org/](http://www.tutorialsforopenoffice.org/)

[http://openoffice.blogs.com/](http://openoffice.blogs.com/)

[http://www.edafe.org/openoffice/index.html](http://www.edafe.org/openoffice/index.html)

---

