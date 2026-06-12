---
title: "Ubuntu Firfox"
date: 2009-03-24
forum: General Help
---

### Post by gotenks123 on 2009-03-24
Hi, Just a quick 1, im using ubunti 8.10 and firefox randomly closes when im surfing the web...

any ideas?

---

### Post by Sin@Sin-Sacrifice on 2009-03-29
Hmm... I hate this answer but try reinstalling.

---

### Post by sgosnell on 2009-03-29
What version?  3.07 has a bug which causes this.  3.08 is out, and should be installed.

---

### Post by 5l4y3r on 2009-03-30
I'm having this problem too and I already installed the 3.0.8 version.
The worse is that Firefox freezes the entire system and I have no choice but to restart the computer. This use to happen in pages that uses flash.
I'll try a clean reinstall now with Ubuntuzilla and see if that helps.

---

### Post by nanotube on 2009-03-30
if the latest 3.0.8 firefox from the repos doesn't fix the issue, try installing the official mozilla build. the ubuntuzilla project would be helpful in the latter process.

---

### Post by philinux on 2009-03-30
Run firefox from the terminal first. That way you see the errors that are reported.

It could be graphics card/driver related. 

Until you run it from a terminal you're guessing in the dark.

---

### Post by 5l4y3r on 2009-03-30
I already tried running Firefox from the Terminal (just have to type 'Firefox' on it, right?) but the system freezes entirely, including the Terminal, so I wasn't able to determine the problem.
I just finished the Ubuntuzilla installation, now I'll see if that helps.
In the end of the installation I noticed that I had an error related to 'gpg' then it tried to connect to various sites but couldn't. Does anyone know what was that? Apparently the Firefox installation went allright.

---

### Post by nanotube on 2009-03-30
> **5l4y3r said:**
> I already tried running Firefox from the Terminal (just have to type 'Firefox' on it, right?) but the system freezes entirely, including the Terminal, so I wasn't able to determine the problem.
I just finished the Ubuntuzilla installation, now I'll see if that helps.
In the end of the installation I noticed that I had an error related to 'gpg' then it tried to connect to various sites but couldn't. Does anyone know what was that? Apparently the Firefox installation went allright.

Hi
first, it has to be "firefox", not "Firefox".

as to ubuntuzilla: please copy/paste the entire installation log (or at least the part with the error) and i'll take a look. most likely one of the gpg keyservers was down, so it moved on to the next one to get the mozilla release signing key.... 

if firefox still freezes on you, you could (a) start with a fresh profile, or (b) turn off compiz and switch to metacity. and see if either of those do any good.

---

### Post by 5l4y3r on 2009-03-30
Do I need this signing process to be complete in order to have Firefox running correctly? It seems to be installed correctly even without completing this process.

---

### Post by nanotube on 2009-03-30
> **5l4y3r said:**
> Do I need this signing process to be complete in order to have Firefox running correctly? It seems to be installed correctly even without completing this process.

hi
without seeing your install log, i cannot tell what exactly happened, so i'm not going to guess. :) if everything works, and you are running the mozilla build (you can see in help->about, if it mentions ubuntu, it's the ubuntu build), then it went through ok.

---

### Post by csmgj on 2009-08-02
Hi there. I seem to be having the same problem with Mozilla randomly shutting down. Seems lots of people are. Wasn't sure if I should post a new thread, or reply to this one. But I saw in this thread that 'philinux' mentioned it could be graphics card / driver related. Was wondering how I could check into that, as I'm pretty new into Linux. in my case, graphics seems like a likely problem. I've tried various web browsers and have had the same problems. I've also had problems with F-Spot photo manager closing. And most graphic video games (open arena,  War Zone 2100, etc) will crash unless I run metacity --replace. This is driving me NUTS. 

More info for browser closings, if it does it once, it will be more likely to do it again. Left my computer on last night and this morning I couldn't even check my GMail until I rebooted. I don't know how to check logs. If you could tell me where to find the nessesary logs, I'd be more than happy to post them for you. Thanks. 

Seems if we could get to the bottom of this issue, it will help a lot of people.

---

### Post by 5l4y3r on 2009-08-02
All my problems with Firefox hanging the entire system went away after I've installed the 3.5 version. 
Also, the version I'm using was downloaded directly from Mozilla website instead of synaptic.

---

