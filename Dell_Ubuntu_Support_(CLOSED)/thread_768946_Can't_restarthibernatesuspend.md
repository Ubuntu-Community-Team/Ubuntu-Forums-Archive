---
title: "Can't restart/hibernate/suspend"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EliBaskin on 2008-04-26
I've used Ubuntu 7.10 and yesterday decided to upgrade to 8.04. One of the problems I had with 7.10 was the inability to enter suspend mode and the hibernate mode often failed.

After the upgrade I hoped that the issue will be resolved. I tried to reboot using the reboot button on the top right side of the screen - and the computer hang. I tried to hibernate/suspend - same effect.

I am using Dell Inspiron 6400.

Any ideas how to approach or fix this problem?

---

### Post by LewisR on 2008-04-26
EliBaskin,

Are you hanging on the cylon screen (Ubuntu logo, empty bar?) If so I have the same behavior and I am on a Dell XPS 410.

Would appreciate any thoughts!

Thanks,
Lewis

---

### Post by agentnixon on 2008-04-27
I'm having the same problem. It's driving me nuts. It's hanging on the desktop (doesn't even reach the loading screen).

---

### Post by kstee on 2008-04-27
Similar problems for me. I also just upgraded to 8.04 from 7.10 on a Dell Inspiron 530. Before the upgrade hibernate mostly worked ok (occasioanly restarts would fail) and suspend rarely if ever worked. Now hibernate doesn't seem to work very well at all. :(

However, I did discover that on restart after hibernate that not much looks like it happening but if a press a key my screen goes all white - and then if I pressed enter I'll see the wait icon spin - so on a hunch I typed in my password and hit enter and my desktop came up. :-?

Go figure! I guess better than nothin'... 

Might have something to do with the video h/w drivers.

---

### Post by peddy on 2008-06-18
Can you go to system>administration>login window> 'edit commands' and tell me what the Halt Command path is?

Cheers

---

### Post by stevezygote on 2008-06-18
> **EliBaskin said:**
> I've used Ubuntu 7.10 and yesterday decided to upgrade to 8.04. One of the problems I had with 7.10 was the inability to enter suspend mode and the hibernate mode often failed.

After the upgrade I hoped that the issue will be resolved. I tried to reboot using the reboot button on the top right side of the screen - and the computer hang. I tried to hibernate/suspend - same effect.

I am using Dell Inspiron 6400.

Any ideas how to approach or fix this problem?

There doesn't seem to be any responses to this post. I'm having the same problem. My HP Pavilion 2.2Ghz, 512MB RAM, on 60Gig HDD won't hibernate. I'm using Kubuntu 8.04 fresh install. When I tried to restart the system, I can't use CTRL-ALT-DEL and have to physically hold the I/O button. Then I had to use the recovery console and finally managed to reboot into Kubuntu.

---

### Post by marast78 on 2008-06-19
Hi,

I've fixed this problem. Dell + Ubuntu = problem with BIOS and ATI. I've just off outter video card over BIOS and problem has been resolved (outter card will still work correctly).

---

