---
title: "i have no desktop ,all in the screen is ubuntu9.10 song-desktop tty2 ..."
date: 2009-12-19
forum: Desktop Environments
---

### Post by frantzsong on 2009-12-19
ubuntu9.10 song-desktop tty2 
song-desktop login:
 
 
before it i uninstall all the kde sofeware in Synaptic Package Manager  by root, in the uninstalling ,the screen turn blank . ctrl+alt+f7 can't take me back to gnome 
 
tell me how to do..
 
i didnot want reinstall the system..
 
...

---

### Post by RedSingularity on 2009-12-19
Can you get to a text based login?

---

### Post by frantzsong on 2009-12-19
> **RedSingularity said:**
> Can you get to a text based login?
 i can 
but i don't now how to back my desktop

---

### Post by frantzsong on 2009-12-19
> **frantzsong said:**
> i can 
but i don't now how to back my desktop
 mabe my desktop has been uninstalled 
in the Synaptic Package Manager  
i search all the installed software by the keyword KDE 
than ctrl+A unintalled all them..

---

### Post by RedSingularity on 2009-12-19
In a text window type......

sudo apt-get install kubuntu-desktop (if you are using KDE)

see what it says when you do that command.

And reboot.

---

### Post by frantzsong on 2009-12-19
> **RedSingularity said:**
> In a text window type......
 
sudo apt-get install kubuntu-desktop (if you are using KDE)
 
see what it says when you do that command.
 
And reboot.
 i have try  that
 
but cant install the desktop 
 
i cant conntet the internet    i must ust the [SIZE=2][COLOR=#008000]proxy [/COLOR][/SIZE]
[SIZE=2][COLOR=#008000][/COLOR][/SIZE] 
[SIZE=2][COLOR=#008000]and i dont know how to set it[/COLOR][/SIZE]

---

### Post by RedSingularity on 2009-12-19
[http://www.linuxtent.com/?p=105](http://www.linuxtent.com/?p=105)

That seems to be what your looking for.

---

### Post by frantzsong on 2009-12-19
> **RedSingularity said:**
> [http://www.linuxtent.com/?p=105](http://www.linuxtent.com/?p=105)
 
That seems to be what your looking for.
 sudo gedit command not found..

---

### Post by RedSingularity on 2009-12-19
Wow.....it seems that the whole system was deleted!  Do you have the CD?

---

### Post by frantzsong on 2009-12-19
> **RedSingularity said:**
> Wow.....it seems that the whole system was deleted! Do you have the CD?
not the 9.10
 
i have a 7.10 CD
 
i was install ubuntu 9.10 by a  flashdisk.

---

### Post by RedSingularity on 2009-12-19
Ubuntu or Kubuntu?

---

### Post by frantzsong on 2009-12-19
> **RedSingularity said:**
> Ubuntu or Kubuntu?
 ubuntu

---

### Post by RedSingularity on 2009-12-20
Try editing the file like this

sudo vim /etc/bash.bashrc

---

### Post by frantzsong on 2009-12-20
sudo vim not found
 
 use vi can see the text   
 
but i dont know how to edit it

---

### Post by RedSingularity on 2009-12-20
Here are some instructions on editing in VI.  [http://www.cs.rit.edu/~cslab/vi.html](http://www.cs.rit.edu/~cslab/vi.html)

---

### Post by frantzsong on 2009-12-20
> **RedSingularity said:**
> Here are some instructions on editing in VI.  [http://www.cs.rit.edu/~cslab/vi.html](http://www.cs.rit.edu/~cslab/vi.html)
uh.. plaese tell how to do it
 
i still dont know how to  edit it
 
..

---

### Post by frantzsong on 2009-12-20
> **frantzsong said:**
> uh.. plaese tell how to do it
 
i still dont know how to  edit it
 
..
[B]>  
**Inserting**

       r        replace character under cursor with next 
character typed

       R        keep replacing character until *[esc]* is hit

       i        insert before cursor

       a        append after cursor

       A        append at end of line

       O        open line above cursor and enter append mode

[/B]
 
is here ?
 
i cant understand it very well

---

### Post by frantzsong on 2009-12-20
**Line Editor Mode**
	Any commands form the line editor **ex** can be issued 
	upon entering line mode.

	To enter: type ':'

	To exit: press*[return]* or *[esc]*

---

### Post by RedSingularity on 2009-12-20
What is your proxy name and port?

---

### Post by frantzsong on 2009-12-20
> **RedSingularity said:**
> What is your proxy name and port?
222.195.14.15
port 808

---

### Post by RedSingularity on 2009-12-20
Ok do 

sudo vi /etc/bash.bashrc 

Press Shift + L to go to the bottom of the page.
Press enter to go down a line.
Press Shift A and then begin typing what you want.

---

### Post by RedSingularity on 2009-12-20
You can try putting the ubuntu CD in, rebooting and then do 

sudo apt-get install ubuntu-desktop

---

### Post by frantzsong on 2009-12-20
> **RedSingularity said:**
> You can try putting the ubuntu CD in, rebooting and then do 
 
sudo apt-get install ubuntu-desktop
thanks you very much
 
[COLOR=black]Unfortunately,i didnot install it in the end and now i had installed a XP system[/COLOR]
 
i will install ubuntu later maybe under wubi.exe install..
 
also thank you..
 
frantz

---

### Post by frantzsong on 2009-12-20
also my CDdriver is broken..
yesterday i tryed cd install .. but my CDdriver is broken .it only can read new CDROMs
 
and my ubuntuCD is burn myself  , it cant read it
 
also my Redflag linux DVD, it cant read it to..
 
so   i borrow i xp cd, and installed it

---

