---
title: "firefox crashing - losing faith in ubuntu!"
date: 2009-03-28
forum: General Help
---

### Post by jensenguy on 2009-03-28
Ive just installed ubuntu on my computer for the first time. (Windows user previously) I like the concept of ubuntu, and I really want to like using it, but one bug is driving me up a wall. 

My Firefox browser keeps crashing, mostly when trying to load flash heavy site. But it will also crash at other times. (a couple times just trying to go through this forum) I have tried every fix i can find online. Ive done the pulseaudio fix, removed libflashsupport, ran a couple commands from terminal that downloaded several hundred megs of plugins and updates i guess. Running firefox through terminal results in a segmentation fault after crash.

Everything is up to date on this system. Ubuntu 8.10, Firefox 3.0.7, Adobe Flash 10. What i dont understand, is Ive found countless threads about this exact problem, and there doesnt seem to be a real fix. I do like that fact that linux is tweakable, but I shouldnt have to be going through all this to make an included application on a final release work as it should.

Im about to wipe this drive out and go back to windows. If anyone can help me with this problem, please do!

---

### Post by cc8balla on 2009-03-28
Try updating Firefox to 3.0.8.

And firefox crashing is NOT the operating system's fault (usually). Windows users have been complaining about 3.0.7 crashing alot as well. 

Also, don't have such a closed mind, or a short fuse when using Linux. It'll take a bit to get used to, but once you do, you'll never go back.

---

### Post by Yownanymous on 2009-03-28
Was about to say so myself - over on Windows, FF 3.0.7 has been a real PITA with crashing, all fixed with the update though.:)

---

### Post by brayden13 on 2009-03-28
yes as cc8balla said it is most likely happening with the browser itself. So by crashing it just completely locks up? well i've never ever had a problem like this with firefox when using ubuntu. are you sure you didn't download some really odd plugins or apps before hand?

---

### Post by Bucky Ball on 2009-03-28
No, you shouldn't have to do all that and something you have done may have made the problem worse. You're losing faith in Ubuntu because firefox is crashing? Maybe if Ubuntu was crashing ... 

Is everything you installed installed correctly? Have you tried uninstalling and reinstalling Firefox? (System->Administration->Synaptics Package Manager). Have you got the correct Ubuntu for your machine, 32 or 64bit (may sound like a silly question but you never know)? Have you checked any log files or run 'dmesg' in a terminal *immediately* after Firefox crashes? (Applications->Accessories->Terminal and type, or paste from here 'dmesg' without the quotes). Have you opened a terminal and run Firefox from there to see if that makes any difference? (goto a terminal and type 'firefox' without the quotes)

Last but not least, did you check your Ubuntu install cd for defects before installing Ubuntu? It is an option on the list when you boot that disk. Best and most reliable way is to get the torrent file and download that way. I would try installing again, or perhaps even try 8.04 or the Alternate version of whatever you are using (rather than desktop) and last resort try re-installing Ubuntu and see if that makes a difference. May sound over the top but just covering all bases. It is definitely a browser problem though, not OS as everything else appears to be working. 

You have one post and this is your first reply. You would give up on Windows if a program kept crashing? Eek! No-one would use Windows. Don't give up too easy, Linux is something you may grow to love ... or not. Once you have this problem fixed, there is a good chance your machine will be stabler than it ever has been ... :)

* here, here cc8balla

---

### Post by Yownanymous on 2009-03-28
> **Bucky Ball said:**
> No, you shouldn't have to do all that and something you have done may have made the problem worse. You're losing faith in Ubuntu because firefox is crashing? Maybe if Ubuntu was crashing ... 

Is everything you installed installed correctly? Have you tried uninstalling and reinstalling Firefox? (System->Administration->Synaptics Package Manager). Have you got the correct Ubuntu for your machine, 32 or 64bit (may sound like a silly question but you never know)? Have you checked any log files or run 'dmesg' in a terminal *immediately* after Firefox crashes? (Applications->Accessories->Terminal and type, or paste from here 'dmesg' without the quotes). Have you opened a terminal and run Firefox from there to see if that makes any difference? (goto a terminal and type 'firefox' without the quotes)

Last but not least, did you check your Ubuntu install cd for defects before installing Ubuntu? It is an option on the list when you boot that disk. Best and most reliable way is to get the torrent file and download that way. I would try installing again, or perhaps even try 8.04 or the Alternate version of whatever you are using (rather than desktop) and last resort try re-installing Ubuntu and see if that makes a difference.

You have one post and this is your first reply. Don't give up too easy, Linux is something you may grow to love ... or not. :)

* here, here cc8balla

No need for this complicated set of instructions - it's just the browser itself has been made a bit iffy and unstable with 3.0.7. Just install the 3.0.8 update and everything should work.

---

### Post by Kareeser on 2009-03-28
I wouldn't be too quick to jump on the "Windows crashes, so it's part of the program" bandwagon. Firefox shouldn't crash at all...

jensen: Are you using 64-bit ubuntu?

---

### Post by Bucky Ball on 2009-03-28
They aren't instructions. They are questions (note the question marks). And yes, I make it perfectly clear it is a browser problem.

---

### Post by cc8balla on 2009-03-28
> **Kareeser said:**
> I wouldn't be too quick to jump on the "Windows crashes, so it's part of the program" bandwagon. Firefox shouldn't crash at all...

jensen: Are you using 64-bit ubuntu?

It SHOULDN'T but it has. The 3.0.7 update was a huge annoyance to alot of people. 

This is clearly a browser problem.

Like I said before OP, the new update is in the repos, so go to a terminal and type:

```
sudo apt-get update
```

Or if you want a more graphical way of doing it, go to System > Update Manager (can't remember the exact menu location in GNOME) and check for updates that way. Make sure your repos are checked though, under Software Sources > Third party software. 

If your crashes still occur after updating, then go ahead and post back here with the problem, and we'll go from there.

---

### Post by jensenguy on 2009-03-28
Thanks for all the quick replies. I am using 32-bit ubuntu. And I did check the cd for defects before installation. 

Im glad to hear of the update to firefox, I will try that first and see where it puts me. I do realize this is more than likely a firefox problem as opposed to ubuntu, it was kinda making me think, 'this is the kind of support software gives to linux??'

I guess the main reason this frustrated me so much was that I had heard linux was so stable and bulletproof, and I had problems as soon as I installed it. Windows at least usually is good on a fresh install, It doesnt get to locking up until you use it for a while!

---

### Post by 3rdalbum on 2009-03-28
I'd suggest a temporary move of browser; you could "stay in the family" and try Flock. It's a social networking web browser but underneath it's a tweaked Firefox. As such, all your Firefox plugins will work with it.

You should check your Firefox addons too, actually; try disabling the more exotic ones and see if that helps.

---

### Post by cc8balla on 2009-03-28
> **jensenguy said:**
> 
Im glad to hear of the update to firefox, I will try that first and see where it puts me. I do realize this is more than likely a firefox problem as opposed to ubuntu, it was kinda making me think, 'this is the kind of support software gives to linux??'


As I said in my first post, this was an issue shared between Linux AND windows. The 3.0.7 update was just...bad. 3.0.8 has seemed to fix all issues. 
> **jensenguy said:**
> 
I guess the main reason this frustrated me so much was that I had heard linux was so stable and bulletproof, and I had problems as soon as I installed it. Windows at least usually is good on a fresh install, It doesnt get to locking up until you use it for a while!
Fresh installs are always like that. I usually think of it like this, once I get everything I want, and get rid of everything I don't want, it usually runs flawlessly. This time around, this box has an uptime of 21 days, 9 hours, and 54 minutes. Without one crash, and it has been fully updated many times. That's not something windows can do, as it needs to restart after every update, and after every program you install!

Give linux a chance. That's all we ask here, is to give it a fair chance. If you have problems its normal, but that is what the forum is for. You will learn soooo much about your computer, trust me.

---

### Post by Bucky Ball on 2009-03-28
> **jensenguy said:**
> 
I had heard linux was so stable

It is. This is a browser issue. :) Hang in there, and you're welcome.

---

### Post by jensenguy on 2009-03-28
Well so far so good with 3.08! Ive loaded and watched several different videos on a couple different sites without problem. Now that i think about it, I had 3.0.4 originally, which crashed sometimes, but when i upgraded to 3.0.7, it started crashing all the time. I should have noticed that. 

One question i do have is why did 3.0.8 not show up on the update list? I followed one of the tips above to change my third party software settings, and suddenly the firefox updates were there. Does this mean 3.0.7 is still the officially approved version for ubuntu? 

thanks to everyone for their help! Ill stick with Ubuntu for now!

---

### Post by Bucky Ball on 2009-03-28
Excellent news, you're welcome and welcome to the forums and Ubuntu.

---

### Post by cc8balla on 2009-03-28
No, it probably wasn't at the time that the update manager checks for new software. You can force it to, by manually checking. I believe Firefox was only updated last night, and was in the repos as soon as it was. 

Good to hear you are sticking it out!

---

### Post by bendib on 2009-04-19
A few questions... 
1. does everything else work?
2. did you install flash with the crappy plugin thingy?
3. Does it crash when you load a flash thingy?
4. Have you tried reinstalling firefox?.
5. Do you use you cd drive as a cupholder? Sploosh!
6. Do you tape your plumber's fridge magnet to your laptop?
7. Do you enjoy pain?
8. Do you eat babies?

5 through 8 are stupid jokes, no offence intended, just joking with the Micro$oft user.

---

