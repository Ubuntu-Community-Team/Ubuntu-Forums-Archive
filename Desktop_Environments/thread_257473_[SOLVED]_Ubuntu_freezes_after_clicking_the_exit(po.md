---
title: "[SOLVED] Ubuntu freezes after clicking the exit(power down) button"
date: 2006-09-14
forum: Desktop Environments
---

### Post by YanalAlHasan on 2006-09-14
Hello all,thanks for reading this thread.
I have ubuntu dapper 6.06 and my problem is that every time i press the exit(power down) button ubuntu freezes:( and after 2-3 minutes i see the logout screen(hibernate,shutdown ...).after i try clicking it again (after i close the logout screen(hibernate,shutdown ...)) it comes up with no delay.but after that when i reboot and log in again i click it and it freezes for 2-3 minutes again.The problem is that i cant wait for 2-3 minutes before i can shutdown the computer! ](*,) .If anyone knows how to solve the problem any help would be very preciated!:KS .thanks again for reading.

---

### Post by neoeden on 2006-09-14
I'm not sure what's going on w\ the freezing. Try opening a console and typing

sudo poweroff

Come back and let us know if that hangs as well.

---

### Post by msingletary on 2006-09-14
> **YanalAlHasan said:**
> Hello all,thanks for reading this thread.
I have ubuntu dapper 6.06 and my problem is that every time i press the exit(power down) button ubuntu freezes:( and after 2-3 minutes i see the logout screen(hibernate,shutdown ...).after i try clicking it again (after i close the logout screen(hibernate,shutdown ...)) it comes up with no delay.but after that when i reboot and log in again i click it and it freezes for 2-3 minutes again.The problem is that i cant wait for 2-3 minutes before i can shutdown the computer! ](*,) .If anyone knows how to solve the problem any help would be very preciated!:KS .thanks again for reading.

I actually had some of the same types of troubles on my first Ubuntu installation. It turns out that trying to use any functions under the log out button would either result in a lack of action or freezing of the OS.

After playing around with things for a while I found that the screensavers weren't working, either. They just wouldn't come up and would spit out errors in the command line if I ran the test through there. I locked my terminal, left my desk and came back minutes later to be presented with a blank screen after trying to log back in.

Unfortunately I don't have any terribly valuable information for you to "fix" the problem, though the same issues didn't present themselves once I reformatted and popped Ubuntu on there all over again.

I'm hoping that someone else will be able to provide something more beneficial, though!

---

### Post by aswells on 2006-09-15
Ugh, now I seem to be having similar problems. You must be contageous.

---

### Post by YanalAlHasan on 2006-09-15
> **neoeden said:**
> I'm not sure what's going on w\ the freezing. Try opening a console and typing

sudo poweroff

Come back and let us know if that hangs as well.

Thank u all for replying,I tried sudo poweroff and it didnt hang at all! it turned off my computer at once.

---

### Post by YanalAlHasan on 2006-09-16
Any help Plz?

---

### Post by YanalAlHasan on 2006-09-19
no one knew about the problem:( so i reinstalled ubuntu and after i installed  packages and updated my ubuntu it went straight on that freezing problem again so i think that installing new packages has to do with the problem!.
thanks.

---

### Post by Roberto Rosselli on 2006-09-19
Same problem here, it would at least help to reach the "exit" dialog with some other means ...

---

### Post by Roberto Rosselli on 2006-09-23
It now seems the freeze is gone, perhaps thanks to the latest kernel update. Is it "cured" for you as well YanalAlHasan?

Ciao!

---

### Post by YanalAlHasan on 2006-09-24
No I guess not :(  I am still facing that problem.

---

### Post by CCBalla10 on 2006-11-09
Hey guys, i am also now having this problem...and mine didn't start until i installed AIGLX/Beryl on my Dapper system.  Maybe Beryl has something to do with it.....
regards
Austin

---

### Post by pizpot on 2008-02-22
I think I know how I made it happen. I went to Prefs->Sessions and disabled things. One of them was power manager. I've put it back and will reboot and see.

Edit: Bingo!

(CCBalla: Beryl/Compiz are built in to 7.10 just click Prefs->Appearance->Visual Effects. Then enable the cube in the custom button. Also, I've had no trouble upgrading with Update Manager on several boxes--go for it)

---

### Post by paranoid_humanoid on 2008-04-05
> **pizpot said:**
> I think I know how I made it happen. I went to Prefs->Sessions and disabled things. One of them was power manager. I've put it back and will reboot and see.

Edit: Bingo!



that was brilliant. i love this forum.. :)
thanks alot.. :D

ps. please mark this problem SOLVED

---

### Post by ExBuM on 2008-04-06
> **paranoid_humanoid said:**
> that was brilliant. i love this forum.. :)
thanks alot.. :D

ps. please mark this problem SOLVED

I've been dealing with this problem for months, and I finally decided to ask ubuntuforums what was wrong. I come and first topic I see solved my problem... (Even though it was posted two years ago)

Thanks pizpot

---

