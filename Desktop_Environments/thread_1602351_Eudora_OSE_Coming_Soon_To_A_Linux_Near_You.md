---
title: "Eudora OSE Coming Soon To A Linux Near You?"
date: 2010-10-21
forum: Desktop Environments
---

### Post by onaridge on 2010-10-21
Anyone know if Eudora, now that it is open source, will be coming to Ubuntu? I've used it for ten years now and need all those mailboxes I accumulated over the years. Now that it's gone open source I was wondering if anyone knows of any plans to add it to Linux? That is the only thing stopping me from converting my laptop over from Windows. Right now I use the laptop for my mail and my Linux PC for everything else.

I know of no web clients that allow you to import mailboxes.

---

### Post by SantaFe on 2010-10-21
> **onaridge said:**
> Anyone know if Eudora, now that it is open source, will be coming to Ubuntu? I've used it for ten years now and need all those mailboxes I accumulated over the years. Now that it's gone open source I was wondering if anyone knows of any plans to add it to Linux? That is the only thing stopping me from converting my laptop over from Windows. Right now I use the laptop for my mail and my Linux PC for everything else.

I know of no web clients that allow you to import mailboxes.
Yep.  Here's the home page for it & it shows a Ubuntu Linux version.

[https://wiki.mozilla.org/Eudora_OSE](https://wiki.mozilla.org/Eudora_OSE)

Looks sort of Thunderbird'ish to me. :)

---

### Post by onaridge on 2010-10-21
Ha! Ya know when I was on that page last week Ubuntu wasn't even a glimmer in my eye and I never noticed it. Ok so because I am still newbiesh, how do I install it? IOW where to extract the tar to and what to do next?

---

### Post by onaridge on 2010-10-21
also I am not sure how to find out if there is a linux distributed package in which case it would be easy to install

---

### Post by SantaFe on 2010-10-21
I just downloaded it into a folder I made in Nautilus, then right clicked on the eudora download & picked Extract here.  Then I moved the extracted folder called eudora into my home directory.  Right clicked on my desktop & Picked Create Launcher.  Then entered Eudora in the name field, & in command, clicked on the  browse button & clicked on the eudora folder, then when it showed the contents of the eudora folder, I clicked on Eudora, Not the eudora.bin , just the one that says eudora.  Picked an Icon I liked, clicked OK, and it showed up on my desktop.   Should work the same for you I would guess.

Now watch someone come by with an easier & better reply! :P

---

### Post by howefield on 2010-10-21
Not a better reply, just what is in the README.txt

> Linux
-----

1.  After downloading the file, open up a terminal window.

2.  In the terminal window type in the following:

    sudo tar -C /opt -xvf <place where you downloaded the file>

3.  Then create a link for easy execution by typing:

    sudo ln -s /opt/eudora/eudora /usr/local/bin/eudora

4.  After installation is complete, we recommend that you read the
    README.txt file (this file) in /opt/eudora.

5.  You will then be able to run Eudora from any command prompt
    by just typing in "eudora" (no quotes).

Pretty straightforward and simple. Now to enjoy a blast from the past...

---

### Post by SantaFe on 2010-10-21
> **onaridge said:**
> also I am not sure how to find out if there is a linux distributed package in which case it would be easy to install
Nope, doesn't look like their is ....YET.  There may be soon if there's any demand for it, but all they have is the download file called EudoraOSE-1.0.en-US.linux-i686.tar.bz2.

---

### Post by SantaFe on 2010-10-21
> **howefield said:**
> Not a better reply, just what is in the README.txt Well I was Half right. ;)  You nailed the simple part.

---

### Post by onaridge on 2010-10-21
sudo tar -C /opt -xvf <place where you downloaded the file>

Hey Santa Fe, thanks. I think I will try the command line since I should get comfortable with that asap. 

Howefield: I am not sure how to write out the path correctly for the above between the <>. I had /home/loren/downloads. Got no file found because I know I am writing this incorrectly. I presume you meant the <  and > to be there also in the command?

The Tar is in my home folder, Loren, downloads and is called EudoraOSE-1.0.en-US.linux-i686.tar.bz2.tar

---

### Post by howefield on 2010-10-21
Open a fresh terminal and type

```
cd Downloads
```

Then try the command

```
sudo tar -C /opt -xvf EudoraOSE-1.0.en-US.linux-i686.tar.bz2.tar
```

Incidentally, the tab feature can be quite useful when typing a long filename, when you start typing the filename... in this case with E then press the tab key. It will auto complete the file name for you (as long as there is no other file in that folder starting with E, if there is you might need to type a few more characters, can be useful for avoiding typos.

---

### Post by onaridge on 2010-10-21
says cannot open no such file or directory

---

### Post by onaridge on 2010-10-21
Hey SantaFe,

I ended up doing it your way and the installation itself went well. But then I tried to import stuff. I have my current Eudora folder that I was using in Windows, saved to my external drive. When I went from Eudora 8.0 to OSE on Windows I was easily able to import all those mailboxes and  settings. Now the "import all settings" never worked, so I imported each setting individually and that worked well. With the same version of Eudora in Linux, the import does not work at all. It also wants me to import mail from Communicator 4X? I can't even receive mail, it says "unable to locate mail spool file" when I try to get mail. Any idea what's happening here?

In Windows before OSE I would copy the whole Eudora folder into the program file after I installed a fresh copy of Eudora. I would have all my settings and mailboxes intact. Is there anything similar I can do in this case with Linux? But the spool issue will still be a problem and I don't know enough about that part of a mail program.

---

### Post by SantaFe on 2010-10-21
To be honest, I never even used the import option, as when I started it, it saw my Thunderbird E-Mail profile & used that, right down to the TBird extensions/themes.  It doesn't seem very Eudora-ish to me, just a different version of Thunderbird.:confused:

---

### Post by onaridge on 2010-10-21
Rats, I was hoping you could tell me how to solve my dilemma. :-)

I agree, it's pretty much Thunderbird. But I learned to get used to it in Windows and it was the only one compatible with previous Eudora versions.

I registered at the Eudora forum and asked the question there. We will see what happened. The only thing I use my windows PC anymore is for mail!!

---

### Post by SantaFe on 2010-10-22
Sorry I couldn't have been more helpfull. :(

---

### Post by onaridge on 2010-10-22
Not to worry, I bit the bullet and am using Evolution which is way more than I need since I don't need a PIM but it's the only one that doesn't give me a mail spool error and I will just start fresh mailboxes and save the others on a Windows computer. Hey I learned how to install a program and make a launcher thanks to you! :-)

---

