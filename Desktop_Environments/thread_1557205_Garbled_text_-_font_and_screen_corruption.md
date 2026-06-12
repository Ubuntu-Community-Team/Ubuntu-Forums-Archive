---
title: "Garbled text - font and screen corruption?"
date: 2010-08-20
forum: Desktop Environments
---

### Post by citro_cell on 2010-08-20
Originally I thought it was a font problem, but my latest screenshot (attached) shows more involvement than just garbled looking text.  This problem has been occurring as often as twice a day and as infrequently as once a month since I installed 10.04 shortly after the final release.  Here is a link to the bug I logged at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/589504](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/589504)

I am happy to provide any information that you might want, but I might need a little bit of coaching as to how to find what you are looking for.  Thank you in advance for any help you can provide!!!

---

### Post by citro_cell on 2010-08-28
...bump..anyone?

It just happened again - all of the text on the screen (including things like "Applications Places System", and the clock) garbled while browsing the Internet.  I had not opened any other programs since my computer had been on (only about 60 minutes).  Is there a system log that might be helpful in diagnosing this?

Thanks in advance for any thoughts on this issue!!

---

### Post by bigchiefgeiko on 2010-09-01
Hi there, I have had the same problem. 

I seem to only get it sometimes and only it seems to be when I am using firefox. 

I have not noticed it on certain sites. 

Do you get this from login or does it login fine and then happen? 

For me it logs in fine and then for some reason it seems to go crazy.

---

### Post by citro_cell on 2010-09-03
Thanks for the reply!!  It has never happened directly from login, and I am pretty sure I am using firefox when it occurs - but it definitely affects all of the system font.

The font went crazy again a few minutes ago.  And this time I tried to hang in there instead of rebooting immediately.  I tried first to change resolution and other system monitor settings, nothing changed.  However, after 5-10 minutes the font seemed to clear up a little. Then, I changed the font from "subpixel smoothing" to "best contrast" and presto it fixed all the font immediately!!

I wonder, is Firefox causing that particular font to corrupt?

---

### Post by Tonya_in_FL on 2010-10-24
> **citro_cell said:**
> Thanks for the reply!!  It has never happened directly from login, and I am pretty sure I am using firefox when it occurs - but it definitely affects all of the system font.

The font went crazy again a few minutes ago.  And this time I tried to hang in there instead of rebooting immediately.  I tried first to change resolution and other system monitor settings, nothing changed.  However, after 5-10 minutes the font seemed to clear up a little. Then, I changed the font from "subpixel smoothing" to "best contrast" and presto it fixed all the font immediately!!

I wonder, is Firefox causing that particular font to corrupt?
Hi Citro!

I just switched to Lucid not too long ago. I use a Dell Mini 10 Netbook. And I've also experienced this. I was using Firefox, Gedit, and Gimp at the same time when all my fonts became garbled. Like you, I tried to wait it out, but ended up having to restart. Now, no problem. What version of FF do you use? What kind of comp do you have? Maybe we can figure this one out by trial and error.

---

### Post by lemonbar on 2011-05-02
I'm having this problem too - I noticed it after clicking my local NBC affiliate and more recently a local FOX story. I just figured my computer gained sentience and rejected those sites on principle!  

This has been happening for awhile - maybe a year, but it's actually gotten worse lately. The fonts remain garbled until I restart (once I figure out which gibberish is "restart").  I noticed that after NBC the fonts are still almost decipherable, but FOX makes them go completely bonkers crazy. It's not a big deal - most of the time I have no use for those sites, but since they are covering school district stuff I'd like to try to figure this out.  

I'm using Firefox, btw.

---

### Post by Bynw on 2011-08-10
I'm experiencing this same issue on 11.04 using the classic gnome desktop. Unlock or login to the desktop and all the fonts are garbled as gibberish. Rebooting does fix it but need a quicker way of getting this resolved and a more permanent fix.

---

### Post by snowguy on 2011-09-08
I have the same problem. And I think I have a work around. 

First the work around. I went into appearances and went to the fonts tab and changed anything that said "ubuntu" or "ubuntu bold" to arial. That cleared up the problem immediately. Or almost cleared it up, I can also see the problem when I open the dash and mouse over the icons there--but it is just a small problem there. Of course the other work around everyone has noted is just rebooting. Also, I'll have to wait to find out if this is a permanent solution or just a temporary fix.

Here are some additional symptoms.

It typically happens to me when I have multiple users logged into the machine. I switch back to an active user and all of a sudden the screen is corrupted. I can log in as a different user again and then everything is working again. It so happens in my case that to date I have repeatedly seen this on the same login (the one I normally use and which has admin rights). I've never seen this on any of the other logins on the computer which are for my kids.

---

### Post by Gardener77 on 2011-09-09
I have the same problem.

Garbled text accompanied by desktop and login images being "Messed-up." Usually the image distortion preceded the text.

What I have figured out is that it only happens when multiple users are logged in at the same time. And it happens right at login.

If I log out, then log in to the other user so as to log them out, I can them log back in to the first and it will be cleared up. 

No correlation to certain websites has been noticed at all.

The problem started with the 10.10 upgrade

---

### Post by Seraphim9 on 2011-10-05
I have the same issue with my fonts as well on Natty and this is what I have been able to track down. Possibly a bug in the **xserver-xorg-video-intel**. 

[http://askubuntu.com/questions/59420/some-characters-hidden-by-half](http://askubuntu.com/questions/59420/some-characters-hidden-by-half)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/745608](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/745608)

*CAUTION*: As suggested in post #40 I tried creating an xorg.conf file and pasting:

Section "Device"
    Identifier "Intel"
    Driver "intel"
    Option "DebugWait" "true"
EndSection

[COLOR=Black]This caused my machine to CRASH![/COLOR] So I am hesitant to try the suggestion in post #59. I am curious if I even NEED this intel package. (It came in an update.)

---

