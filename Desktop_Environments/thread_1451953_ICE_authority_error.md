---
title: "ICE authority error"
date: 2010-04-11
forum: Desktop Environments
---

### Post by Odaym on 2010-04-11
I have the problem of ICEauthority file. when i boot i dont get my  desktop, instead i get an error 

"Could not update ICEauthority  file /home/oday/.ICEauthority", 

I press ok and then there's  another error with the 

"configuration server  (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

then  i get the error "Nautilus could not create the following required  folders: /home/oday/Desktop, /home/oday/.nautilus.
Before running  Nautilus, please create these folders, or set permissions such that  Nautilus can create them."

There is already a topic about this issue, but i couldnt post more in it.

I tried the following from the solutions in it

 - run [B]sudo chown mike:mike .ICEauthority
[/B]- run [B]sudo /etc/init.d/gdm restart

[/B]it worked for the session i did that in, but when i rebooted the system it gave the same error again.
help please thanks

---

### Post by Spirobranchus on 2010-07-14
I get the same first error message, except when I click OK it lets me log in as normal. Not a major problem, just very annoying to have to click it at start up each time. Please help.

---

### Post by Braik on 2010-07-14
Hi there,
 
Just a little question, what is your username? "mike" or "oday"?
 
Let me explain you, when you put
```
 
sudo chown mike:mike .ICEauthority

```
You are asking for ownership of ".ICEauthority" file to mike of the group mike, but when I see the file location "/home/oday/.ICEauthority" it seems to be on the folder of a user called oday.

---

### Post by NetworkCowgirl on 2010-12-03
Try dpkg-reconfigure nautilus. Then reboot.

---

### Post by mikkopa on 2011-07-05
Had similar case in which I accidentally changed owner for files under /var/lib/gdm. This should fix the problem:


[LIST]
[*]cd /var/lib
[/LIST]

[LIST]
[*]sudo chown -R gdm:gdm gdm
[/LIST]

---

### Post by jvgeli on 2011-07-08
Yup, permissions will have to be changed for the ICE file. You can also change it manually using sudo nautilus and changing permissions for the average user.

---

### Post by eveg on 2011-07-23
i'm having the same problem, only it's gone a little further on mine. [i'm now getting a warning message when i try to fix it from the command line with gksudo, which says 
Gtk-WARNING**:cannot open display. i seem to be locked out of all graphical applications, but fortunately command line isn't dead --- yet?]
 it's my own fault because i did a variety of things wrong including using a very good book(unleashed) which unfortunately happens to be for one of the ubuntu 11 versions not the current stable 10.04:(. 

have you used sudo where you should've used gksudo? this may've happened on mine. i got the ubuntu bible for 10.04 and it warned very strongly that you could disable graphical applications and be left with only command line if you use sudo where you should use gksudo.

i don't have the answer to this and i'm hoping someone does. by way of a warning, i'll embarass myself by explaining exactly how i got in this mess so no one else will. [the only thing i've done right so far is that all my tinkering has been on an old cpu that doesn't go online and is only to play with, not essential for anything.]
i had a few books and magazines and the help pages for ubuntu are so good that i managed to manually partition my harddrive and install 10.04 without losing and data from the old o.s.--- so i got a bit overconfident. also i didn't have the 10.04 book yet.
and i picked up something called linux in easy steps. 

*it tells you how to enable root without telling you why not to!* 
[NEVER *NEVER*, ENABLE ROOT, unless you are an experienced linux-guru system administrator and you're certain you absolutely have to--- but if you are that much of an expert, you're probably one of the people telling the rest of us not to and being ignored at our peril. to be fair to the 'easy steps' guy, he did say in the margin that you shouldn't enable root, but he didn't explain why not to, and by the time i noticed the margin note i'd already done it. it's a massive security hole. if you wouldn't leave your car sitting in a bad neighborhood with the engine running, the driver's door open and no one in the car, don't enable root--- it's asking for just as much trouble as the car stupidity would be. if you have enabled root, take your computer offline, back up all your data, reinstall your linux o.s. with root disabled, and if you can afford it have a security expert look at your data before you copy it back onto your rebooted machine.]
 
having enabled root without realizing until i read further what a disastrous mistake i'd made, i remembered the root password as important and managed to forget my user password. never do that. don't make it too easy to guess, don't leave it lying around written, but make yourself memorize it. ( and change it often and re-memorize. and of course never use the same password for more than one thing.)

at this point all i'd lost was access to an encrypted home directory with some unimportant personal files on it. but in trying to fix it without looking up how to first, i think i've made things worse. when i'd guessed a few times wrong and couldn't recall my password, i logged out and logged back in from the BIOS to recovery mode, clicked thru until it offered me the root account and logged in as that. aware i could really mess things up as root, but not aware how thouroughly, i tried a book example for changing password. at which point it offered to change my unix password, which was nothing to do with my home directory, but was the computer's 'super-user' or root, also as it was that acct i was using when i enabled root. so i put sudo before the change password script as root. now i have no graphics.

---

