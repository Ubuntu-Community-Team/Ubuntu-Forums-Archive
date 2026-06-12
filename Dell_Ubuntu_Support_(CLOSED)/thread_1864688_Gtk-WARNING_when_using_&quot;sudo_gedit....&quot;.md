---
title: "Gtk-WARNING when using &quot;sudo gedit....&quot;"
date: 2011-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nvcnvn on 2011-10-19
My Dell is Studio 1558
I just have a clean install of Ubuntu 11.10

when I try to use Gedit to edit or add new file with "sudo" prefix.
Eg: ```
sudo gedit /path/file.txt
```

I get this:
```
(gedit:3855): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8DQC3V': No such file or directory

(gedit:3855): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3855): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Z3XH3V': No such file or directory

(gedit:3855): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```


Not sure why these missing but some one can I download it some where?

I have do some search but not found any help yet!

Thanks for your help!

---

### Post by haqking on 2011-10-19
> **nvcnvn said:**
> My Dell is Studio 1558
I just have a clean install of Ubuntu 11.10

when I try to use Gedit to edit or add new file with "sudo" prefix.
Eg: ```
sudo gedit /path/file.txt
```

I get this:
```
(gedit:3855): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8DQC3V': No such file or directory

(gedit:3855): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3855): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Z3XH3V': No such file or directory

(gedit:3855): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```


Not sure why these missing but some one can I download it some where?

I have do some search but not found any help yet!

Thanks for your help!

dont use sudo for graphical apps.

gksudo is preferred

---

### Post by nvcnvn on 2011-10-19
> **haqking said:**
> dont use sudo for graphical apps.

gksudo is preferred

Thanks for your help, but i still get the issue!
```
(gedit:8305): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3VXH3V': No such file or directory

(gedit:8305): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```


When try to edit a file with gksudo prefix, Gedit open one more Untitled Document and I see the reload Icon next by the "Untitle Document 1".

---

### Post by haqking on 2011-10-19
> **nvcnvn said:**
> Thanks for your help, but i still get the issue!
```
(gedit:8305): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3VXH3V': No such file or directory

(gedit:8305): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```


When try to edit a file with gksudo prefix, Gedit open one more Untitled Document and I see the reload Icon next by the "Untitle Document 1".

why are trying to save to /root ?

---

### Post by crazy bird on 2011-10-19
> **haqking said:**
> dont use sudo for graphical apps.
 
gksudo is preferred
 
Not true, sudo will do just fine! That's how i do it also: *sudo gedit /path/filename*.
 
The problem the topic starter is facing was similar to what i had. It has something to do with Gtk. 
 
Can you check this:
```
 ls /root/.local/share/*.xbel
```
Is that file there? Can ls find the full path?
It looks line that there is no directory /root/.local/share/.

---

### Post by haqking on 2011-10-19
> **crazy bird said:**
> **Not true, sudo will do just fine**! That's how i do it also: *sudo gedit /path/filename*.
 
The problem the topic starter is facing was similar to what i had. It has something to do with Gtk. 
 
Can you check this:
```
 ls /root/.local/share/*.xbel
```
Is that file there? Can ls find the full path?
It looks line that there is no directory /root/.local/share/.

if it makes no difference there would be no gksudo.

im not saying you cant use sudo, alot of people do and it often works the same, however to be safe it is prefered to use gksudo

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by crazy bird on 2011-10-19
> **haqking said:**
> if it makes no difference there would be no gksudo.
 

 
gksudo is a frontend to sudo. Their primary purpose is to run graphical commands that need root without the need to run an X terminal emulator and using su directly. That means you don't need to load up a terminal (or ubuntu doesn't) to use a graphical program as root without being logged in as a root user. So you could type "gksudo gedit <filename>" in a run box (Alt+F2 or have an icon that runs this command), and no terminal would load up.
 
Please, let stay ontopic an try finding a solution to fix the topic starter's problem.

---

### Post by nvcnvn on 2011-10-19
> **haqking said:**
> why are trying to save to /root ?

I want to make some new file and but it in a restricted folder.

> Is that file there? Can ls find the full path?
It looks line that there is no directory /root/.local/share/.

Yes, there is no such folder!
Can you show me how to fix it?

Thanks for all of you!

---

### Post by jag022054 on 2011-10-19
I think I have the same problem. I did as suggested and tried to check the path. I have no ability to navigate into or LS anything in root.
Could the mode attributes for root be a problem?

Another observation. I didn't have this problem when I upgraded from 11.04 to 11.10. I ended up doing a clean install later. After that I had this problem. I suspect it has something  to do with creating root. The upgrade may have worked because root already existed.

---

### Post by nvcnvn on 2011-10-21
There is still no solutions?

---

### Post by crazy bird on 2011-10-22
-

---

### Post by crazy bird on 2011-10-22
Try this in a terminal:

```
sudo chmod 777 /root/.local/share/
```

---

### Post by barry853 on 2011-11-05
Hi I have the same problem,

Some strange things are going on since I've installed 11.10. When I open gedit using sudo with terminal I got this message in terminal:

for example: sudo gedit ~/test.txt

```

(gedit:2439): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Utworzenie pliku "/root/.local/share/recently-used.xbel.HJHH4V" si&#281; nie powiod&#322;o: Nie ma takiego pliku ani katalogu

(gedit:2439): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Nie ma takiego pliku ani katalogu

```

It is a polish version so:

"Utworzenie pliku "/root/.local/share/recently-used.xbel.HJHH4V" si&#281; nie powiod&#322;o" is something like: "Failed to create file "/root/.local/share/recently-used.xbel.HJHH4V" " and "Nie ma takiego pliku ani katalogu" means "There is no such file or directory"

Gedit opens fine and seems to we working but everytime I save something in gedit this message above is being repeated (with different ending in "recently-used.xbel.HJHH4V" filename). Also after opening and closing I can't open gedit without sudo (I have to use sudo again to open it).

@crazy bird
I used "ls /root/.local/share/*.xbel" and what I get is this:
```
ls: nie ma dost&#281;pu do /root/.local/share/*.xbel: Brak dost&#281;pu
```
Which means:
"nie ma dost&#281;pu do" - no access to
"Brak dost&#281;pu"  - permission denied

when using the ls command with sudo I get info that there is no such file or directory.

as in @jag022054's case in my case it is also fresh ubuntu 11.10 installation

---

### Post by ronnystickshift on 2011-11-06
hi all - this command "ls /root/.local/share/*.xbel" won't work, you need to add sudo to the beginning, since the permissions on that directory are drwx------ (meaning only root can read/write/execute)

i tried "sudo ls /root/.local/share/*.xbel" on my machine and nothing is there.  the only files in /root/.local/share/ on my computer are "applications" and "webkit"

P.S. barry i just saw that you had in the very last line of your post, sorry!  maybe it will be beneficial for others :)

---

### Post by barry853 on 2011-11-06
The answer to that problem will be appreciated as I still can't get rid of it

---

### Post by PROTEUS_5 on 2011-11-20
HI All,

This is the sollution to get away the GTK Warnings.
Type the following in terminal.

sudo mkdir -p /root/.local/share

good l.

---

### Post by [MSRS]Joey on 2011-11-26
> sudo mkdir -p /root/.local/shareWorked for me, thx :)

Ubuntu 11.10 64bit, trying to figure out the crappy 5.1 sound i encountered this "problem" on my way -> solved (even if just this problem is solved ^^).

---

### Post by champost on 2012-02-07
> 
sudo mkdir -p /root/.local/share
Solved for me too on Ubuntu 11.10 64bit...the owner of this post should mark it as solved as soon as he verifies it for himself...

---

### Post by JamesSwift on 2012-03-13
Worked here as well.

---

