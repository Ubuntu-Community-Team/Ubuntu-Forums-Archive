---
title: "How do I install a tar.gz file?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by randell6564 on 2006-06-05
Im running 'Breezy' and want to add a new 'gdm screen' to system>administration>login setup screen.

The problem is that I dont know how to install a tar.gz file!


Any help?

---

### Post by Perfex on 2006-06-05
Just hit the add button in administration,login window, then browse to the tar.gz

Other wise go here [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by randell6564 on 2006-06-05
[QUOTE=Perfex]Just hit the add button in administration,login window, then browse to the tar.gz

Other wise go here [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)[/QUOTE]

Cant install 'tar.gz' using the "install new theme" button.

It does not see 'tar.gz' files, so it does not show up on the desktop when browsing for it.

I'll check out the link, Thanks!

---

### Post by randell6564 on 2006-06-05
Wel...

The tutorial doesnt work!

Every thing that It says to enter at the terminal gets: "command not found"!

I got as far as creating a folder in '/' and moving the 'tar.gz' file into it. Then 'extracting' to that folder!

I then opened a terminal, 'cd' to that folder and entered the commands given.

NOTHING!

---

### Post by localzuk on 2006-06-05
First can I ask you to calm down...

Second, the file you have is a 'gzipped tar archive' which in English is a compressed archive similar to a zip file. To extract the file entirely, run 'tar zxf blah.tar.gz' from the directory which contains the file (and blah.tar.gz is the file).

This will then extract it. If you do not want to totally extract it, but instead leave it as a .tar file, run 'gunzip blah.tar.gz' instead.

Try both of these and see which one the splash screen app wants.

---

### Post by randell6564 on 2006-06-05
[QUOTE=localzuk]First can I ask you to calm down...

Second, the file you have is a 'gzipped tar archive' which in English is a compressed archive similar to a zip file. To extract the file entirely, run 'tar zxf blah.tar.gz' from the directory which contains the file (and blah.tar.gz is the file).

This will then extract it. If you do not want to totally extract it, but instead leave it as a .tar file, run 'gunzip blah.tar.gz' instead.

Try both of these and see which one the splash screen app wants.[/QUOTE]

Sorry...

I didnt mean to seem upset.

I'll do as you instructed and get back to you.  Thanks!

---

### Post by randell6564 on 2006-06-05
[QUOTE=randell6564]Sorry...

I didnt mean to seem upset.

I'll do as you instructed and get back to you.  Thanks![/QUOTE]

Ok...

Heres what I get when typing, **sudo tar zxf blah.tar.gz**:

[B]scott@Home:/tux$ sudo tar zxf blah.tar.gz
Password:
tar: blah.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
 
[/B]

Dunno man!

I did this in the directory that I created named, 'tux'.  The files IN that directory have been extracted already.

---

### Post by localzuk on 2006-06-05
Blah.tar.gz needed to be changed to the name of the actual tar.gz file.

Ah, so you have already extracted the files.

What does the command 'ls' return from within that directory? Also, what type of file does the Splash Screen application want?

---

### Post by randell6564 on 2006-06-05
[QUOTE=localzuk]Blah.tar.gz needed to be changed to the name of the actual tar.gz file.

Ah, so you have already extracted the files.

What does the command 'ls' return from within that directory? Also, what type of file does the Splash Screen application want?[/QUOTE]

LMAO!!  Sorry!  "blah" should have been a pretty good indication of what you were trying to get across!

As for 'ls':

[B]Tux G2                        Tux_G2_GDM_orange.tar.gz  Tux_G2_Pack.tar.gz
Tux G2 - Ecrans de démarrage  Tux_G2_GDM_vert.tar.gz    Tux_G2_vert
Tux G2 - Fonds d'écran        Tux_G2_orange

[/B]

It DOES look like they are not all extracted!

As for,  **"what type of file does the Splash Screen application want"?**

Im not quite sure how to go about getting that info for you!

---

### Post by localzuk on 2006-06-05
When you try to use the 'add splash screen' function in the app, what type of files does it show?

---

### Post by randell6564 on 2006-06-05
[QUOTE=localzuk]When you try to use the 'add splash screen' function in the app, what type of files does it show?[/QUOTE]

GOT IT!

for some strange reason, once I extracted the files into the 'tux' folder that I created earlier, I could then go to my 'login set up' and browse to that folder and SEE the files!

I then just double-clicked on the one that I wanted and BAM, I've got it!

Thanks my friend!  For being so patient!

Now I'm off to try and install the fonts that came with the package!

---

### Post by Perfex on 2006-06-05
for fonts ```
sudo cp /home/user/Desktop/*.ttf /usr/share/fonts
```

and refresh your font cache like this:
```
sudo fc-cache -f
```


the above code is if the font was on your desktop, just type sudo cp then drag the .ttf to the terminal and it should write its location in then the rest of the code as shown

---

### Post by Perfex on 2006-06-05
.

---

### Post by randell6564 on 2006-06-05
[QUOTE=Perfex].[/QUOTE]

Thanks Again!

---

