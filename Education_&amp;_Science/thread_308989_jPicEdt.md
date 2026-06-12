---
title: "jPicEdt"
date: 2006-11-29
forum: Education &amp; Science
---

### Post by adamkane on 2006-11-29
Anyone know how to install jPicEdt on Ubuntu?
[http://jpicedt.sourceforge.net/](http://jpicedt.sourceforge.net/)

The instructions say to install the Swing JFC (Java Foundation Class):
[http://java.sun.com/products/jfc/](http://java.sun.com/products/jfc/)

The link brings you to Sun's website, and informs you that Swing is part of the Java SDK.

I have the JDK installed.

I installed jPicEdt this way:
```

sudo java -jar jpicedt-install_1_3_2.jar

```I tried installing jPicEdt into:
/usr/local/share/jpicedt/1.3.2/
/usr/bin

and also into:
/home/<username>/jpicedt/1.3.2/
/usr/bin

but neither installation worked. jPicEdt hangs when opening.

---

### Post by parktownprawn on 2006-11-30
hmmm - jpicedt 1.3.2 just hangs for me as well


I downloaded the last version 1.2 and it works fine

just type

```
java -jar jpicedt-1_2.jar
```

to run it

---

### Post by adamkane on 2006-12-02
jPicEdt 1.3.1 also seems to work.

Woohoo!

---

### Post by adamkane on 2006-12-02
jpicedt-install-1.4.jar work also, but you need to use sudo.

```

sudo java -jar jpicedt-install-1.4.jar

```Accept the installation defaults.

```

gksudo jpicedt

```

---

### Post by parktownprawn on 2006-12-02
hmmmm 

running an application with sudo is a generally a bad idea

I would advise installing the program in your home directory.

just run 

```
java -jar jpicedt-install-1.4.jar
```

*without* sudo 

and choose somewhere in your home directory to install the program.

---

### Post by adamkane on 2006-12-02
I agree. I actually installed it my home directory, but I wanted to keep the instructions simple. For some reason you need sudo to get it working.

I think the author must have received a lot of complaints like "this software doesn't work, and implemented the sudo-for-everything solution."

jpicedt 1.4-pre has vastly more options than jpicedt 1.3.1 You should install it, and report which steps worked for you.

---

### Post by parktownprawn on 2006-12-03
I had no problems installing 1.4 and it runs fine with out sudo

To install

Just to be safe first remove  ```
~/.jpictedt
``` and any preexisting versions of jpictedt 

type 

```
java -jar jpicedt-install-1_4_pre_5.jar
```

(without sudo)

go through the installation procedure and select somewhere in 
your home directory to install the program

eg. Install program in 

```
/home/username/applications/jpicedt/1.4/
```

Install short cut in 

```
/home/username/bin
```

Now type

```
gedit ~/.bashrc
```
and add the follwing line 
```
export PATH=$PATH:~/bin
```

To configure jpicedt goto preferences and click on the commands tab. Click the load button next to Load predefined config.
Select unix/tetex/configTeTeX.properties

-------------

seems to work fine for me

---

### Post by adamkane on 2006-12-03
Woohoo!

---

### Post by parktownprawn on 2006-12-03
You may also want to check out

Latexdraw : [http://latexdraw.sourceforge.net/](http://latexdraw.sourceforge.net/)

---

### Post by adamkane on 2006-12-03
Nice!

JPGfDraw
[http://theoval.cmp.uea.ac.uk/~nlct/jpgfdraw/](http://theoval.cmp.uea.ac.uk/~nlct/jpgfdraw/)

Lyx + Maxima + PSTricks + LabPlot = 
Near complete GUI LaTeX function editing, solving, plotting and drawing suite.

---

### Post by daspliff12345 on 2011-08-20
> **parktownprawn said:**
> I had no problems installing 1.4 and it runs fine with out sudo

To install

Just to be safe first remove  ```
~/.jpictedt
``` and any preexisting versions of jpictedt 

type 

```
java -jar jpicedt-install-1_4_pre_5.jar
```

(without sudo)

go through the installation procedure and select somewhere in 
your home directory to install the program

eg. Install program in 

```
/home/username/applications/jpicedt/1.4/
```

Install short cut in 

```
/home/username/bin
```

Now type

```
gedit ~/.bashrc
```
and add the follwing line 
```
export PATH=$PATH:~/bin
```

To configure jpicedt goto preferences and click on the commands tab. Click the load button next to Load predefined config.
Select unix/tetex/configTeTeX.properties

-------------

seems to work fine for me

Thanks for this detailed instruction to install Jpicedt. Can you explain what the last two lines of code does?
 I followed your instructions and got it installed.....howver i place the shortcut in /home/username/ and then I ran the program from there....I am now making a shortcut to the desktop. Is it ok to move the shortcut file?..I am assuming it is a symlink and will keep pointing to the executable...
I did not complete the last couple lines...beginning with gedit....please explain workings of this code.

Thanks

---

