---
title: "Anyone know why my unbuntu resets the DNS numbers every 5/10 mins??"
date: 2006-09-03
forum: Desktop Environments
---

### Post by sketchone on 2006-09-03
iv entered DNS supplied by my ISP that i enter into the networking consol, everything is fine for about 10 mins then it resets so i have to put them in again

anyone got any ideas?

---

### Post by Lunchmeat on 2006-09-03
I have ethe exact same problem!! I think it might be a bug since i have been searching  (looking on irc, boards and web) for two days for a solution.

---

### Post by mssever on 2006-09-03
Are you trying to use custom DNS numbers? When that happened to me, it was due to the DHCP lease being renewed. In my case, I fixed it by telling my router not to send DNS numbers.

---

### Post by dare2dreamer on 2006-09-12
I'm having the same issue here.

How do you tell your router to not send dns? My cheapo airlink101, which has worked for years, is having the same issue.

---

### Post by mssever on 2006-09-12
That depends on your router. Mine is a Linksys WRT54G v.5. There's a section on the basic setup page labeled "Static DNS." I just put my DNS there and made sure that it wouldn't use my ISP's DNS. I have no idea how your router works, though.

If you can't configure your router properly, here's a bubblegum workaround: Edit /etc/resolv.conf to contain the proper DNS info and save it in another file. Then, when you have problems, merely copy your custom resolv.conf to /etc/resolv.conf. You could even set this up as a cron job.

---

### Post by skymt on 2006-09-12
This has come up before. See [this post](http://www.ubuntuforums.org/showpost.php?p=1485201&postcount=10) for a solution.

---

