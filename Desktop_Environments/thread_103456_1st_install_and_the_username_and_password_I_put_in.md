---
title: "1st install and the username and password I put in won't work?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Fibre on 2005-12-14
Hello everyone,

Well I've finally managed to install ubuntu 5.10 after a few hick ups. Then when I have the option to enter username and password the ones I entered into the O/S while installing, it didn't work?

All in lower case, there is no mistake with the wording, I made 100% sure of it.

My question - is there a way around this hurdle or does this mean I have to re-install the system all over again.

I really appreciate any and all help regarding this matter.

And I look forward to the ongoing help and maybe one day helping someone else with this new system that I have had nothing to with before.

I know hardware and 98/xp but any linux system is new to me, so much appreciated.:D

---

### Post by kaamos on 2005-12-14
Boot into recovery mode by selecting it in grubs menu (the one that comes after your bios has loaded) and then use the command
```
passwd **username**
```
Of course replacing username with the username that you created. This will ask you for a new password for this user.

BTW, you didn't use the username "root", did you..?  (Bad idea)

---

### Post by Fibre on 2005-12-14
Thanks for the reply **Kammos** I'll check it out now and see how I go - I'll be back.

---

### Post by Fibre on 2005-12-14
Well Kaamos it looks like I might be stuck my username is my name with a space between and it doesn't accept the username? It's got me stumped I know I put it in correctly so unless there is a way around this problem I'm assuming I'm going to have to re-install aaaahhhhh LOL.

Please let me know if there are any other tricks in your bag or else its time for another episode of re-install LOL.

---

### Post by kaamos on 2005-12-14
Whoops. I'm not sure, but I think usernames with spaces are a very bad idea. A thing you could try is to create a new user completely. Try google for this or searching the forums, I have not done this so cannot help you with it. Sorry. :(

---

### Post by Fibre on 2005-12-14
much appreciated for your help Kaamos you've been nothing but helpful mate.
Ok I go searching and check back here tommorrow morning before lunch Australian time.

Thanks mate :)

---

### Post by Rinzwind on 2005-12-14
Wild guess:

edit **/etc/passwd** and delete that space from the username (should be in the 1st column near the end).
make a new your home dir equal to the name w/o the space and copy(!) all files including hidden to the new homedir.

**passwd {newusername}** and change the pwd.

Dunno if it works like this in Ubuntu  but it does work on the Unix(!) system I work with. And do backup any changes you make ;)

---

### Post by Fibre on 2005-12-14
Nice try but no luck, I get permission denied lol.

Be nice to know for future refrence but I think I'll just start again with out the space in the name.

You live and learn - live and learn. :)

I think I'm going to have a late night re-installing lol doesn't matter.
I'll atleast become good at installing the O/S.

So not to worry, if i spend anymore time on it, I could have installed it 2 more times. So yeah I'll just finish up on this thread and get into it. 

Thank you both once again for your time and knowledge much appreciated.

---

### Post by Rinzwind on 2005-12-14
No problem.

Hmm permission denied on what? Oh wait you can't login on a tty terminal can you!?

LOL. How's that for a lockdown? If it's not a problem do a re-install.

---

### Post by Fibre on 2005-12-14
Yee ha LOL

When it works it works, I'm stoked the whole thing just goes once your going.

Now to learn all I can LOL. I've updated everything and I'm right to go. Perhaps I can get some info on security and maybe how to check that all my devices are working correctly before I go any further.

should I post else where or just continue here LOL I'm excited. Doesn't take much does it LOL.

I'm surprised it worked out how to use my isp connection what a blow out.

And it downloads just as quick if not a faction better than windows.

Can't wait to try the gaming aspect out on this thing. 

Lovin this forum as well, great group of ppl. thanks for the quick responses.

I had some problems with the cd, it kept saying the cd player had the problem but I got past that. Glitch in the installation cd it's got some minor scratches so maybe that was the prob with the install. I read up before I started and was told through reading to place your name that way but obviously it's a big no no.

OK LOL I'll stop no LOL

---

