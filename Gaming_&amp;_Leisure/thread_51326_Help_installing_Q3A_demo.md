---
title: "Help installing Q3A demo"
date: 2005-07-23
forum: Gaming &amp; Leisure
---

### Post by arcanistherogue on 2005-07-23
Hey.  I should probably own a copy of Q3A by now, me being a big fan of FPS games, but I don't.  I downloaded the demo from FilePlanet, and it was in .gz.sh format.  

I tried getting this to work, I used chmod +x filename.sh and then used sh filename.sh, but it produced an error.  From what I have gathered from google, this error is pretty common.  

It only flashes for about 2 seconds, but using KSnapshot I managed to get a picture of it.  

Here it is: [http://img347.imageshack.us/img347/601/errormessage9nv.png](http://img347.imageshack.us/img347/601/errormessage9nv.png)

How do I install this file?  I read on a forum that if you open the file with a text editor and delete the shell script, then save it as filename.gz instead of .gz.sh it will work, but I can't edit the file.

---

### Post by arcanistherogue on 2005-07-26
Bump

---

### Post by aggiechemist on 2005-07-26
I would also love to see a reply to this. I have the same problem, with no solution.

You can get a better version of the terminal error problem. Open up terminal (right click on the desktop) and run the .sh file. It wil print the error file, but the terminal window won't close.

But that doesn't fix the problem.

---

### Post by No6 on 2005-07-26
[QUOTE=aggiechemist]I would also love to see a reply to this. I have the same problem, with no solution.

You can get a better version of the terminal error problem. Open up terminal (right click on the desktop) and run the .sh file. It wil print the error file, but the terminal window won't close.

But that doesn't fix the problem.[/QUOTE]
 I'm downloading the files as we speak, will see what I can find out...

---

### Post by aggiechemist on 2005-07-26
Also, if you are just looking around to play with an FPS on Ubuntu try unreal tournament 4. Downloads for the demo can be found at atari.com. It has worked far more easily for me than Q3A. I did have to change my open GL software to mule instead of what ubuntu has natively.

Just a thought, finding it certainly did make me feel better that I could get *something* working.

---

### Post by arcanistherogue on 2005-07-26
My friend (who has been using linux for about 2 years) couldn't figure this out ._.

and I own a legit copy of UT2004.  :D.  Its on windows, but I might put it on linux.

---

### Post by aggiechemist on 2005-07-26
Have you tried it as root? I have occasianally ahd shell script stuff that only worked when I was logged in as root. I haven't tried it with this, and I don't have a linux box in front of me, but it might be worth a shot.

---

### Post by arcanistherogue on 2005-07-26
I just tried that and got another error, something with dcopserver.  I checked and it was already runnning, although it said there was an error running it or something.  Odd.

---

### Post by aggiechemist on 2005-07-26
I think dcopserver is a KDE thing. Again, I don't have a linux box handy, but I am curious what would happen if it was tried in Gnome or maybe even window maker (as root). If you don't get a chance I will try those when I get home. At the very least I don't think it will be a dcopserver error.

---

### Post by No6 on 2005-07-27
Right, OK I've got it installed!!! :-)

The script assumes too much about commands and locations so you're best to not use it.

Here's what to do. 

1) Open up a terminal.

2) Open up the file in nano:

**      nano ./linuxq3ademo [TAB]  (just use tab to autocomplete...)**

3) Using CTRL-K remove all the lines upto and including [b]END OF STUB

[/b]4) Save this file (CTRL-X) as q3ademo.gz

5) Create a dir called q3demo and move the q3ademo.gz in there.

[b]mkdir q3demo
mv q3ademo.gz q3demo/q3ademo.gz
[/b] 
6) cd into that directory.

**cd q3demo**

7) Run the following command as root, if you have enabled root then just su, if not use sudo -s -H

either
[b]su
[/b]
or
**sudo -s -H** (note capitalization)

     [b]gzip -cd ./q3ademo.gz | tar xvof -

[/b]Ignore the error message

8 ) run the setup.sh file in this directory
    
**     sh ./setup.sh**

9) follow the GUI!!!

10) Once installed don't run as root but exit the installer and exit the superuser terminal and run q3ademo as your user.

HTH :-)

---

### Post by aggiechemist on 2005-07-27
[QUOTE=aggiechemist]I think dcopserver is a KDE thing. Again, I don't have a linux box handy, but I am curious what would happen if it was tried in Gnome or maybe even window maker (as root). If you don't get a chance I will try those when I get home. At the very least I don't think it will be a dcopserver error.[/QUOTE]


For the record, I did try these and it was no help at all. I can't wait to go home and try the new stuff from No6. I submit to his/her linux superiority, and have high hopes.

---

### Post by No6 on 2005-07-27
[QUOTE=aggiechemist]For the record, I did try these and it was no help at all. I can't wait to go home and try the new stuff from No6. I submit to his/her linux superiority, and have high hopes.[/QUOTE]
 I'm a him :-), and I hope it works for you.

Just post back any questions, unfortunately I'm on GMT +1 so may not be able to reply quickly...

---

