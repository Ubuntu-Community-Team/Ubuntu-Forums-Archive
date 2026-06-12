---
title: "[SOLVED] Burning Data to CD"
date: 2008-12-17
forum: General Help
---

### Post by kelpie_canada on 2008-12-17
I recently upgraded to 8.10 and it seems to be working fine. When I put in a blank CD it comes up you have put in a blank CD what do you want to do. So I went to CD/DVD creator followed the instructions as I always have clicked on burn. It went through all the steps as before and said that it had completed and ejected the CD. When I reinserted the same CD it came up as you have put in a blank CD... So I went to Brasero Disc Burning and followed the directions there. It went through all the steps and said that the burning was completed and ejected the CD. When I put the same CD back in once again it came up as you have put in a blank CD.

What am I doing wrong or  what have I missed in doing this?  Before I upgraded I had no problem burning data to a CD. The system recognises the disc that I have already burned and comes up with the data that is on the disc. Why can't I burn a CD now. All my files are in documents should they be somewhere else?

Thank you for any help on with this perplexing problem.

Katie

---

### Post by gettinoriginal on 2008-12-17
I hate to sound simplistic, but are you just highlighting the files, or are you actually adding them to the right hand field before burning in Brasero ??  :p

---

### Post by kelpie_canada on 2008-12-17
> **gettinoriginal said:**
> I hate to sound simplistic, but are you just highlighting the files, or are you actually adding them to the right hand field before burning in Brasero ??  :p

I am following the instructions exactly. I highlight the files and add, they show up an the right hand side. After I finish adding files I select burn. It goes through the process and says that it is successful. But when I reinsert the CD it comes up as a blank. They are the same CD's that I have been using all along and the system does recognize the ones that I did before.

Katie

---

### Post by gettinoriginal on 2008-12-17
Wow, that's strange.  If it is recognizing other CD's, then your hardware is fine.  I would go into synaptic and do a "complete removal" of Brasero and then reinstall.  But that is only a suggestion, as I am no guru at this LOL.

---

### Post by kelpie_canada on 2008-12-17
I did as you suggested. I removed Brasero and then re-installed it. I put another CD in and went through the same procedure. It went through the process, at the end it stated that the CD was successfully burnt and ejected it. When I put the CD back in it once again came up blank CD.

My laptop was purchased in May of this year and converted to Ubuntu immediately. This is my first computer so I am not very computer litterate. I do try to learn as much as possible but in this instance I am at a complete loss.

Katie

---

### Post by kelpie_canada on 2008-12-17
Just as added information. Although the CD comes up as blank on my system, my boyfriend has a Windows XP system and the CD comes up with all the information in tact and he can read it on his system.

I don't know if this will help anyone to solve this mystery but Thank you for trying.

Katie

---

### Post by kanikilu on 2008-12-17
Are you able to try that CD in another computer running Ubuntu?

This probably won't yield anything, but out of curiosity, if you go to the terminal and browse to the CD/DVD drive (*cd /media/cdrom*), can you see the data there?

I've had some issues with Brasero as well, so have resorted to using K3B even though I don't use Kubuntu. It has worked fine for me and has some more options (which I like).

I know that doesn't really solve your problem, but if you don't get any other help here I'd suggest at least giving K3B or another application a try.

---

### Post by kelpie_canada on 2008-12-17
There is no one in my area that has a Ubuntu. I am now living in the middle of nowhere in Ohio. 

Keep in mind that I have no idea of what I would be looking for or at if I go to the terminal does the disc need to be in or not?

I thought of trying to remove Brasero and just using the CD/DVD Creator that I used every other time which is still listed on my system.

If that doesn't work how would I find K3B and install it?

Katie

---

### Post by kanikilu on 2008-12-17
Yes, the disc would need to be in. If you open a terminal and type ```
ls /media/cdrom
``` and press enter, it should list the contents of that CD.

As for installing K3B, you can search for it in Synaptic or just do ```
sudo apt-get install k3b
``` at the terminal.

The downside to K3B if you use Gnome (default Ubuntu desktop environment), is that you'll have to download and install all the KDE libraries (which is all done automatically with Synaptic/apt-get/aptitude), just for that one application. However, there are some nice KDE-based apps that I personally use (Amarok, Kate, KDevelop, etc.), so for me it was worth it.

---

### Post by kelpie_canada on 2008-12-17
I did as you suggested. I opened the terminal and typed in what you have and nothing happened. It just gave me the same line to enter something new on. So I guess that means as far as my system is concerned there isn't any data on that CD, is that correct?

I haven't reached the point where I use very many of the applications that are currently in my system at the moment. All I really need is to be able to download craft patterns and save them to disc so that when a customer whats to see what I can make I just put in the disc and scroll to what they want to see.

Katie

---

### Post by kanikilu on 2008-12-17
> **kelpie_canada said:**
> So I guess that means as far as my system is concerned there isn't any data on that CD, is that correct?

It would seem so :(

Well, if you can spare the disk space, I would give K3B a try. If not, well, hopefully someone more advanced will come along to give you better advice...

---

### Post by kelpie_canada on 2008-12-17
I went back to synaptic manager and removed Brasero completely from my system. Then I put in a new blank CD and went to CD/DVD creator and burned my files to the disc. After it finished and ejected the disc I reinserted it and just like Majic all the data showed up on the new disc. 
So I will not be reinstalling Brasero at any time because the original program works better then the new one.

Thank you for taking the time to try and help with this problem. I appreciate your efforts.

Katie

---

