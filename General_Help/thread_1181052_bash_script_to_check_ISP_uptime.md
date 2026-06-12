---
title: "bash script to check ISP uptime"
date: 2009-06-07
forum: General Help
---

### Post by jakupl on 2009-06-07
Hello, would it be possible, and reliable to make a bash script for checking the reliability of the ISP?

I live in a dormitary, and I really hate my ISP, but I read that they have committed themself for a 99,5% uptime, I think they are braking this promise, as the connection is pretty unstable, so I want to take it to the test and make a bash script to test it, but I need help to do so.

Would it be sufficient and possible to get a boolean result from "ping www.google.com", insert it in a log file together with a time stamp, and make it run every minute or so, and somehow calculate the percentage of the boolean values?

---

### Post by The Cog on 2009-06-07
It's certainly possible. Use the command **crontab -e** and add a line like this to the file:
```
* * * * * ping -c 5 www.google.com ; echo $? $(date) >> ~/pings.log
```
This will do a ping once a minute. It will write a line with a 1 (success) or 0 (failed) followed by the time.

Whether is is sufficient - what for? I doubt it's enough to hold up in court. How would you prove it's not an outage at Google? Good enough for getting a good "feel" for the actual availability figure.

---

### Post by jakupl on 2009-06-07
> **The Cog said:**
> It's certainly possible. Use the command **crontab -e** and add a line like this to the file:
```
* * * * * ping -c 5 www.google.com ; echo $? $(date) >> ~/pings.log
```
This will do a ping once a minute. It will write a line with a 1 (success) or 0 (failed) followed by the time.

Whether is is sufficient - what for? I doubt it's enough to hold up in court. How would you prove it's not an outage at Google? Good enough for getting a good "feel" for the actual availability figure.

thankyou very much, I tested it and when the internet works, It outputs "0" and when i turn off the router, it outputs "2", so what does that mean?

Hehe, I don't think I will take it to court, but it is pretty nice to have some hard statistics when my dorm has meetings and such... I reeealy want to change isp. They have blocked all peer-to-peer activity, they have censored many websites eg. thepiratebay and many others, and it is unstable and expensive. They don't even respond to emails, even though our special agreement clearly states that they are required to do individual support.

---

### Post by The Cog on 2009-06-08
> **jakupl said:**
> thankyou very much, I tested it and when the internet works, It outputs "0" and when i turn off the router, it outputs "2", so what does that mean?

Hehe, I don't think I will take it to court, but it is pretty nice to have some hard statistics when my dorm has meetings and such... I reeealy want to change isp. They have blocked all peer-to-peer activity, they have censored many websites eg. thepiratebay and many others, and it is unstable and expensive. They don't even respond to emails, even though our special agreement clearly states that they are required to do individual support.
It means I told you wrong. It is actually printing the error number or status number the ping returns. 0 means the ping succeeded. By trial and error, 1 means it couldn't get a response from the destination. I get a 2 if it couldn't look up the hostname to an IP address. You can try it by hand to discover when you get different error codes:
[b]ping -c 3 [www.google.com](www.google.com)
echo $?
ping -c 3 1.1.1.1
echo $?
ping -c 3 foo.bar
echo $?[/b]

---

### Post by jakupl on 2009-06-08
ok great. thank you very much.):P

---

