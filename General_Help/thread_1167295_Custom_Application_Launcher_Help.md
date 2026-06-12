---
title: "Custom Application Launcher Help?"
date: 2009-05-22
forum: General Help
---

### Post by ToyotaGuy23 on 2009-05-22
Hello, 

I installed a very useful application called PDF-SAM (split and merge).  
This program allows you to take a 400 page pdf file and split it into individual pages.  You can also merge those pages back together into one pdf document if you want.  You can remove 50 pages and make your own custom pdf, it's cool.  

Anyway, to launch this program, I open terminal, and...

```
cd /usr/local/share
```

THEN

```
java -jar pdfsam-1.1.2.jar
```

How can I make this easier to launch?  
So far I have 

right clicked panel > add to panel > custom application launcher

The problem I have in creating a launcher is not the specific COMMAND but WHERE to run it FROM.  What should I do next?

---

### Post by amentajo on 2009-05-22
Try this:

```
java -jar /usr/local/share/pdfsam-1.1.2.jar
```

---

### Post by baseface on 2009-05-22
make a shell script.
```
#!/path/to/shell
java -jar /usr/local/share/pdfsam-1.1.2.jar
```

---

### Post by ToyotaGuy23 on 2009-05-22
amentajo, that worked great!
baseface, your solution launched the program also.

How can I add this into my menu or panel, or some easier way of launching this program?

---

### Post by baseface on 2009-05-22
> **ToyotaGuy23 said:**
> amentajo, that worked great!
baseface, your solution launched the program also.
 
How can I add this into my menu or panel, or some easier way of launching this program?
 
right click on the main menu and select "edit menu"... i think. then you should be able to add whatever app you want in there by selecting "add item"... if my memory serves me correctly.

---

### Post by ToyotaGuy23 on 2009-05-22
I'm afraid that doesn't work for me.

---

### Post by Ecologger on 2009-06-03
Well if your script is in the home directory, you can add custom launcher and in the command box type bash <script name here>.

---

### Post by pawnrocket on 2009-06-03
right click on panel
choose add to panel
custom launcher
insert name
insert the command the other guy gave you
pick an icon you like
save

Or 
hit alt+f2

enter in the command once 
choose run in terminal
then you just go back there when you want to use it and select it from the drop down.

or you leave a terminal open (I always have one open)
make the script executable

chmod -x nameofscript

then just type
nameofscript 
in the terminal

---

