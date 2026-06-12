---
title: "AWN Crashing"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by d_fiant_1 on 2008-01-09
Hi guys, I install AWN a few days ago, I am also using compiz on Ubuntu Gutsy

Every couple of hours AWN just crashes and the curve task bar just disappears.

I can restart it in terminal by typing avant-window-navigator and it stays up temporarily until I close the terminal window.

I also get this message in the terminal window after typing avant-window-navitagor, over and over again:

** (avant-window-navigator:28924): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed


The only way I can get the task bar to come back and stay back (until it crashes again) is to restart (not log out) my PC.

Any ideas?

Thanks

---

### Post by shifty2 on 2008-01-10
I have been having this issue for the last day or so, getting the same error message when it is started in terminal. I had changed it to awn-curves over the weekend, then it had an upgrade a few days ago so maybe this has something to do with it? I tried running it through terminal to see what the issue was when it crashes, but when it crashes so does the terminal. wierd. 

I can get it to come back just by pressing cntrl + f2 and typing avant-window-navigator. If you are running it in terminal type "exit" and the terminal should exit but leave the program running.

---

### Post by d_fiant_1 on 2008-01-10
> **shifty2 said:**
> I have been having this issue for the last day or so, getting the same error message when it is started in terminal. I had changed it to awn-curves over the weekend, then it had an upgrade a few days ago so maybe this has something to do with it? I tried running it through terminal to see what the issue was when it crashes, but when it crashes so does the terminal. wierd. 

I can get it to come back just by pressing cntrl + f2 and typing avant-window-navigator. If you are running it in terminal type "exit" and the terminal should exit but leave the program running.

Thanks, i'll try those next time it crashes rather than restarting.

---

### Post by d_fiant_1 on 2008-01-10
> **shifty2 said:**
> I have been having this issue for the last day or so, getting the same error message when it is started in terminal. I had changed it to awn-curves over the weekend, then it had an upgrade a few days ago so maybe this has something to do with it? I tried running it through terminal to see what the issue was when it crashes, but when it crashes so does the terminal. wierd. 

I can get it to come back just by pressing cntrl + f2 and typing avant-window-navigator. If you are running it in terminal type "exit" and the terminal should exit but leave the program running.

Ok, couldn't type 'exit' in terminal because the error message was being cretaed over and over again and didn't go back to the command prompt.

But ctrl+F2 worked a treat.

Has anyone else has this happen and know a permenent solution?

---

### Post by rune0077 on 2008-01-11
AWN is still in beta, so don't expect it to be completely bugfree. It will crash on occasion, for various reasons, and there's not much to be done about it as far as I know, except to wait for the final version to be ready. Good news is, the developers are very actively working on it, so be sure to update it often.

---

### Post by lvleph on 2008-01-11
AWN crashes 5+ times a day for me. It seems to happen when I am switching tasks alot.

---

### Post by d_fiant_1 on 2008-01-11
> **rune0077 said:**
> AWN is still in beta, so don't expect it to be completely bugfree. It will crash on occasion, for various reasons, and there's not much to be done about it as far as I know, except to wait for the final version to be ready. Good news is, the developers are very actively working on it, so be sure to update it often.

Thanks for that info, didn't realise it was still in beta.

> **lvleph said:**
> AWN crashes 5+ times a day for me. It seems to happen when I am switching tasks alot.


Seems to happen more when I am closing an application from the bar.

---

### Post by Tech_Power888 on 2008-01-13
No problems with AWN here, once it's open it stays open for me, except when i restart the computer. I have set it up so that it opens when my computer starts up, by going to preferences - sessions and adding it in. use "avant-window-navigator" as the command. If you haven't done this then give it a try, it might just throw in that extra dimension and solve a few problems.

Ryan.

---

### Post by d_fiant_1 on 2008-01-13
> **Tech_Power888 said:**
> No problems with AWN here, once it's open it stays open for me, except when i restart the computer. I have set it up so that it opens when my computer starts up, by going to preferences - sessions and adding it in. use "avant-window-navigator" as the command. If you haven't done this then give it a try, it might just throw in that extra dimension and solve a few problems.

Ryan.

Getting it started isn't the problem, I have had it set up to start from reboot from the beginning, thats why I have had to reboot to get it started again. Getting it to stop crashing when I am closing or changing applications from the AWN task bar is the problem.

It has been a couple of days since it has crashed on me (touching wood :-P )

---

