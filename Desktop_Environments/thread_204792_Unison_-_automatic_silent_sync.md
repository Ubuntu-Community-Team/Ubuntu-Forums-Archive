---
title: "Unison - automatic silent sync?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by stengah on 2006-06-27
Really hope somebody can help turn this thread into a straighforward step-by-step HOWTO guide to auto-sync with [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/"). If provided the answers I'll make a user friendly howto and post it here with credits.

What I'd really like is to setup Unison to run several sync tasks automatically at a specified interval. I specifically want to be able to synch 2 user home folders between:

Laptop <-> Desktop <-> External USB harddrive. 

My problem is that I have no clue of how to get the final step. I have so far managed:

1. Setting up [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/")+Unison-gtk  (GUI). Both are in the repositories.
2. Setting up 'accounts' in unison for the specific folders I wish to sync unsing Unison-GTK interface (home folder to home folder)
3. Setting up SSH server at the 'Desktop' computer for file transfer bt. computers
4. Enabling direct access bt. computers by removing SSH keys (login) for both users

I've tried following this [guide]("http://http://72.14.235.104/search?q=cache:Bn-ETQbzEbUJ:www.minds.nuim.ie/~page/serendipity/index.php%3F/categories/4-Coding+unison+automatic+script&hl=da&gl=dk&ct=clnk&cd=3&client=firefox")  
but it doesn't seem to execute. Copied the script to /etc/cron.hourly as suggested (may be overkill, but for the purpose of getting it running I assued it was fine to do so) 

I'm totally lost as of what to do from here. I'm crash coursing linux/ubuntu, but I don't have the insight to solve this problem, and cannot find any recipies
 for this neither here or by googling.

I've heard/read about cron jobs, deamons or whatever it's called, but I'm afraid things simply are getting too complex for me ](*,) 

Can anybody please help me make the final steps this howto??? :(

---

### Post by stengah on 2006-06-27
bump

Anybody - any ideas? :-)

---

### Post by stengah on 2006-06-28
*bump*

stubborn ol' me.. c'mon good people of ubuntu. Bet someone's got an answer to this...

---

### Post by stengah on 2006-07-01
Okay, last bump from me. I really hoped somebody would be on par with a solution, but I guess I have to prepare myself to throw the towel in the ring on this one...  :( 

Does anybody by any chance have first hand experience with any friendly alternatives as to how to achive the things describes above, apart from using Unison?

Thanks for [COLOR="Orange"]any[/COLOR] help!

---

### Post by nyxynyx on 2006-12-30
Bump. Wants to know too

---

### Post by lol on 2006-12-30
You need to be more specific: what is it that is not working? Unison or cron?

Can you run Unison manually (from the command line)? Can you run it using your script without cron?

---

### Post by rustikus on 2006-12-30
I have not tried this because i like to see the changes but you can try the following switch.

 -batch              batch mode: ask no questions at all

By the way, i would prefer to add the ssh-keys to ~/.ssh/authorized_keys instead of removing them.

---

