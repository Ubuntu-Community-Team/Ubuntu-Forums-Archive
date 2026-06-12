---
title: "New Ubuntuer wants to play Doom3 + expansion!"
date: 2008-03-12
forum: Gaming &amp; Leisure
---

### Post by peterkeyani on 2008-03-12
Hello,

I am very new to Ubuntu and not that good with Windows XP either. Saying that, thanks to old posts on the forum  I did manage to dual-install Gusty 7.1 and XP SE on my dual-core amd64 PC and get VLC player to install and play DVDs etc!

I understand from these forums that one of my favourite games Doom 3 - and its expansion pack - can be easily installed and played on Gusty 7.1. However, I fall at the first step. I visited ID's site and found the download item which consists of 3 hyper links. But when  I clicked on them, I just brought up a page of code? 

Sorry for the stupid question but what am I supposed to do with it? Copy and paste it somewhere?

Thanks to all!

Pete

---

### Post by peterkeyani on 2008-03-12
The link is [ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)

I was directed to it by [https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3)

Pete

---

### Post by peterkeyani on 2008-03-12
> **peterkeyani said:**
> The link is [ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)

I was directed to it by [https://help.ubuntu.com/community/Doom3](https://help.ubuntu.com/community/Doom3)

Pete


I downloaded to the desktop but when I copied and pasted I got:

 ./Desktop/doom3-linux-1.3.1.1304.x86.run
:confused:
bash: ./Desktop/doom3-linux-1.3.1.1304.x86.run: Permission denied

---

### Post by josh92176 on 2008-03-12
try "sudo ./Desktop/doom3-linux-1.3.1.1304.x86.run" (without the quotes)

-josh

---

### Post by Heo on 2008-03-12
```
cd ~/Desktop/ && chmod +x doom3-linux-1.3.1.1304.x86.run
./doom3-linux-1.3.1.1304.x86.run
```

---

### Post by eragon100 on 2008-03-12
Taht has nothing to do with sudo since it's in YOUR home folder and YOU are the file owner. You simply have to make it executable.

1. Right-click on it

2. select Properties

3. go to permissions tab

4. tick the box that says: allow executing file as program

5. click ok

Now you can run it either from terminal or bu double-clicking on it and selecting run in terminal :)

---

### Post by peterkeyani on 2008-03-12
> **eragon100 said:**
> Taht has nothing to do with sudo since it's in YOUR home folder and YOU are the file owner. You simply have to make it executable.

1. Right-click on it

2. select Properties

3. go to permissions tab

4. tick the box that says: allow executing file as program

5. click ok

Now you can run it either from terminal or bu double-clicking on it and selecting run in terminal :)

Thanks
That sort of worked
Got a "Installation Path" blue box which said " Please enter the installation path usr/local/games/doom3"
The options were "ok" or "cancel": OK  was not accepted!

any ideas?:confused:
Pete

---

### Post by ELD on 2008-03-12
> **peterkeyani said:**
> Thanks
That sort of worked
Got a "Installation Path" blue box which said " Please enter the installation path usr/local/games/doom3"
The options were "ok" or "cancel": OK  was not accepted!

any ideas?:confused:
Pete

Because you are trying to install to a folder that needs "sudo" capabilities, install it into your home folder

"/home/your username/doom3"

---

### Post by Heo on 2008-03-12
> **eragon100 said:**
> Taht has nothing to do with sudo since it's in YOUR home folder and YOU are the file owner. You simply have to make it executable.

1. Right-click on it

2. select Properties

3. go to permissions tab

4. tick the box that says: allow executing file as program

5. click ok

Now you can run it either from terminal or bu double-clicking on it and selecting run in terminal :)
Same thing as my post :P

---

### Post by eragon100 on 2008-03-13
Yes, but I couldn't see the post. We posted at exactlye the smae time!
Just look at the times, they both say "19 hours ago" :lolflag:

---

### Post by peterkeyani on 2008-03-14
> **ELD said:**
> Because you are trying to install to a folder that needs "sudo" capabilities, install it into your home folder

"/home/your username/doom3"

Thanks. Installed it into my home folder. Exc it, double clicked it.
Got a License Agreement Box
Then I got this Installation Path Box

Please enter installation path

(blinking cursor) /usr/local/games/doom3

Thanks for any help!

---

### Post by peterkeyani on 2008-03-14
> **peterkeyani said:**
> Thanks. Installed it into my home folder. Exc it, double clicked it.
Got a License Agreement Box
Then I got this Installation Path Box

Please enter installation path

(blinking cursor) /usr/local/games/doom3

Thanks for any help!


Its in my epiphany folder in the Home Folder

---

### Post by Sabar on 2009-02-17
Hello, I am trying to also install Doom 3 on my ubuntu. I have been following what all this post has. 

1. I downloaded file doom3-linux-1.3.1.1304.x86.run   This is now on my desktop

2. I went to permissions and clicked in the execute as program tab.

3. Double clicked on program and ran in terminal.

4. changed installation path to /home/"my user name"/games/doom3  hit ok

5. Next I get /usr/local/bin if I leave it that. I get no write permission to /usr/local/bin.

5b. If I change it to /home/"username"/bin I get same response I have tried various versions of this including /home/local/bin  and home/"username"/local/bin and for everything I try I get no write permission 

OK now I am stuck, does anybody have any ideas what I have to do?

Sabar

---

### Post by Perfect Storm on 2009-02-17
If you want to install it locally (your home directory), do not use sudo infront.

---

