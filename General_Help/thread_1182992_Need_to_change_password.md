---
title: "Need to change password"
date: 2009-06-09
forum: General Help
---

### Post by lilyphoenix on 2009-06-09
I got my mini 9 from dell today, but when I was setting it up, I mistyped my password (it's not what I thought I typed). I looked at a couple guides people posted, but I can't seem to get to the screen to get to recovery mode. The dell version doesn't seem to have the usual start up screens.

---

### Post by jonobr on 2009-06-09
From doing a google I found [This]("http://nomi.ibnmasud.com/blog/reset-your-lost-ubuntu-password/")
I havent tried it myself, and maybe you tried this already,
but worth a try

---

### Post by michy99 on 2009-06-09
When you get to the login screen, I think you can click on options. Does it allow you to go to recovery mode from there? I would check to see if it works, but I am in the middle of downloading a large, slow file.

---

### Post by bradyfehr on 2009-06-09
I have the exact same problem.  I've tried hitting the esc key, the 0 key, and the 2 key.  The best I can do is get to the bios screen but it requires a password to get into that!  So far anything I do just goes right to the password request.  Very frustrating ....

---

### Post by Iowan on 2009-06-09
[This]("http://www.psychocats.net/ubuntu/resetpassword") one help?

---

### Post by bradyfehr on 2009-06-09
didn't help me.  I can't get to any type of screen where I can type anything.  Everything I do goes staright to the passowrd request, this leads me to believe that it's the Bios password that needs to be reset since I never see Ubuntu try to load ....  ESC key, 0 key, 2 key all do not work.

---

### Post by BlazeFire247 on 2009-06-09
Try [this]("http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/") one I found.

You have to boot from the Live CD, and choose "Try Ubuntu without any change to your computer".

---

### Post by bradyfehr on 2009-06-09
can't boot from a Live CD, I have no CD player .....

---

### Post by lilyphoenix on 2009-06-09
Someone helped me on another thread: 
[http://ubuntuforums.org/showthread.php?t=1179703](http://ubuntuforums.org/showthread.php?t=1179703)
quote:
Hmm... from reading this: [https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

It would seem the grub menu on the dell ubuntu is set to time out at 0 so you might have a hard time accessing it. But it recommends this:

     Quote:
                                                 Booting into Recovery mode

If you have an original Dell Mini 9 with Ubuntu pre-installed, you may have a hard time entering the GRUB menu as the default delay is zero. This is particularly problematic if you're trying to reset your password using the passwd command.

You can enter the recovery mode following these steps:

   1. Boot the mini 9 while pressing ESC every second
   2. When you see the "MBR 2FA:" prompt or similar, the boot process is stopped.
   3. Press ENTER and ESC very fast one after the other.
4. You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode.

---

### Post by bradyfehr on 2009-06-10
Thanks Lily but I'm having no luck at all. No matter what I do I get the "enter password:" prompt. I've hit ESC a million times and I don't get any type of open prompt at all, just the "enter password:" prompt. Same with the "2" key, the "0" key, and the combo of "ESC" and "ENTER". I think it might be the Bios password because I can't even get to the point where Ubuntu tries to load. The "2" key gets me to the Bios Setup screen but it is without content and has the same password prompt. I don't have a CD drive so I can't boot from that (not sure that would even work since I can't change the boot sequence).
 
After 3 tries the computer locks up with a "system disabled [02204]" message.
 
Very, very frustrating. I called Dell and they they don't support Ubuntu and just give me a phone number for Ubuntu supoort. I call that number (866-622-1947) and they have an automatic message that sends me to this forum. I told them that I need to reset the Bios password but they just come back with the same "we don't support Ubuntu" comment.
 
At this point it looks like my only choice is to disassemble the laptop, take out the cell battery, and hope that works. Dell won't take the damn thing back so I'm likely to end up with a expensive paper weight.
 
I'm done with Dell or any other online purchase of a computer. If I buy locally at least I can dump the piece of crap in their lap .....

---

### Post by lilyphoenix on 2009-06-10
You have to press esc while turning on the computer, before anything comes up. You should get  mfb b2: or something like that. You pretty much have to start hitting esc before you turn the laptop on.

---

### Post by bradyfehr on 2009-06-10
Lily - thanks but I have done that a 1000 time - no luck.  can't get the damn thing to do anything but bring up that stupid "enter password" prompt.  I even took the damn thing apart but can't find the CMOS battery.  I also tried getting it to boot off a flash drive but that doesn't work either (boot sequence is probably wrong and since I need a password to get into the Bios setup I can't chnage it).  Know anyone who wants a Mini 9 cheap?  LOL

---

### Post by Iowan on 2009-06-10
> **bradyfehr said:**
>   Know anyone who wants a Mini 9 cheap?  LOLI'll pay for shipping... how much is handling? ):P

But first... perhaps I should point out [this]("http://en.community.dell.com/forums/p/19245362/19384692.aspx") one.

---

