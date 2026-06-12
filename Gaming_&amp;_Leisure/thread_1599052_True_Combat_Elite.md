---
title: "True Combat: Elite"
date: 2010-10-17
forum: Gaming &amp; Leisure
---

### Post by H3R3T1K on 2010-10-17
I stumbled upon this fps recently. Is there anyone playing it around here? Can somebody tell me what I got to do to make it run on Ubuntu?

Cheers

---

### Post by Carpentr on 2010-10-17
The game seems decent. If I remember correctly, the web-site's Linux client url does not work properly. Try using this url instead:
[http://www.truecombatelite.com/forums/viewtopic.php?t=1824]("http://www.truecombatelite.com/forums/viewtopic.php?t=1824")

---

### Post by H3R3T1K on 2010-10-18
I downloaded the ET linux installation file. When I double click it, it gives me the following error:

"gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

How do I install the game? I'm running Maverick 32bit desktop.

---

### Post by Carpentr on 2010-10-19
Have you marked the file to be executable? Have you tried running the script in the terminal?

---

### Post by arkbuntu on 2010-10-19
I installed the game fine but i get no sound im running 10.10 64 bit 
if u google it there is many link how to install 

 I ran et and looked to be many people in there playing. When i signed into true combat 
there was alot of servers but only 2 servers had people in them, and not very many at that.
But maybe i dont have most recent patch, 0.49b is the one I'm running. I could not tell you how
game play is because the server I joined everyone was spectating.

---

### Post by Perfect Storm on 2010-10-20
```
I installed the game fine but i get no sound im running 10.10 64 bit 
```

Try run it with the **padsp** command.

---

### Post by H3R3T1K on 2010-10-21
It could be run once I marked it executable. But it now gives me an error that it can't write the folder "usr/local/games". If I right click the folder and view the "permissions"tab, I can't have it accessed. It's all grey.

---

### Post by Perfect Storm on 2010-10-21
Install it via the terminal. Use **sudo** infront.

eg.

```
sudo sh true.combat.elite_0.49-english.run
```

Afterwards exit the installer window - do not launch the game through the installation window, as it have superuser privileges (sudo). You properly will mess up the permission system of the game if you do.


Or you could just install it undeer you users home folder (then you don't need to do the above).

---

### Post by H3R3T1K on 2010-10-21
I typed
"sudo sh et-linux-2.60.x86.run".
It said it couldn't open the file.

How do I install it in my home folder? There's no install wizard when I run the file.

---

### Post by Perfect Storm on 2010-10-21
Try;

chmod +x it.

or instead;

sudo ./filename

---

### Post by H3R3T1K on 2010-10-22
What was the first thing you proposed? What would the code look like?

"sudo ./filename" didn't work.

It's a little strange because I had no problems playing Urban Terror after downloading it. It didn't INSTALL though. I just unpacked the folder in which I found an executable file that I ran.

---

### Post by H3R3T1K on 2011-07-04
I hope it's not considered "necromancy" posting in my own thread. When I run the installer for ET, this error occurs:

```
Initial test release. ver 2.30c
This release is not compatible with the win32 builds
Please enter the installation path [/usr/local/games/enemy-territory] 
No write permission to /usr/local/games
```

So I changed the folder:

```
Please enter the installation path [/usr/local/games/enemy-territory/] /home/arno/enemy-territory/
Please enter the path in which to create the symbolic links [/usr/local/bin] /home/arno/symbolic links/
No write permission to /home/arno/symbolic links/
Please enter the installation path [/home/arno/enemy-territory/] 

```

It still won't work. What are symbolic links anyways?

Your help is appreciated.

---

### Post by auxilium on 2013-01-24
Hi,

I do believe that you had made the file executable.
When you execute the file make sure you are at the working directory otherwise you must specify the path

e.g

```
 sudo ./path_to_executable_file/exec_file 
```

or while in the working directory of the executable file

```
 sudo ./exec_file 
```

---

