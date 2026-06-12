---
title: "Counter Strike 2D"
date: 2009-08-12
forum: Gaming &amp; Leisure
---

### Post by kaelonlloyd on 2009-08-12
I want to play CS 2d(0.1.1.5) but i can't get the linux install to work.

I Extract the file , but when i run it i get a message saying that theres not program to run it with.

I can't use wine to run the windows version because it lags big time

---

### Post by dmcdaniel on 2009-08-12
> **kaelonlloyd said:**
> I want to play CS 2d(0.1.1.5) but i can't get the linux install to work.

I Extract the file , but when i run it i get a message saying that theres not program to run it with.

I can't use wine to run the windows version because it lags big time

Sounds like you didn't download both files. Make sure you download both of the following:

[http://www.unrealsoftware.de/get.php?get=cs2d_0115_linux.zip](http://www.unrealsoftware.de/get.php?get=cs2d_0115_linux.zip) - This is the Linux File

AND

[http://rapidshare.com/files/246343853/cs2d_0115_win.zip](http://rapidshare.com/files/246343853/cs2d_0115_win.zip) - This is the Windows File that the Linux file gets all its information from 

Hope this helps!

---

### Post by kaelonlloyd on 2009-08-12
I've done that and put all the windows files into the linux file, but i still get an error when i try to run the 'CounterStrike2D' file.
The Terminal says 'Command not found'

An the desktop error is 
'No application suitable for automatic installation is available for handling this type of file'

---

### Post by Narcolepsy06 on 2009-08-12
Did you add the command to the terminal using "chmod 0755 <scriptfilename>" like homebrew scripts?

---

### Post by kaelonlloyd on 2009-08-12
I got it to work.

After alot of searching i found out that i had to set the permissions to run the file as an application. then i had to run it in terminal with either '-24bit' or '-win' following the app name.

---

### Post by Bölvaður on 2009-08-12
> **kaelonlloyd said:**
> I got it to work.

After alot of searching i found out that i had to set the permissions to run the file as an application. then i had to run it in terminal with either '-24bit' or '-win' following the app name.

owww I was too late then.

The only problem was that you hadn't allowed this file to be executed, thereis no need to run it from terminal or add -24it or -win, just double click.

---

### Post by mjaws on 2009-11-12
sorry to dig up a old thread but you do need to add -24bit in the terminal or the game will give you a graphics error "Graphics Mode Error:
640x480 at 32 bit does not work!"
just encase anyone else is wondering

---

