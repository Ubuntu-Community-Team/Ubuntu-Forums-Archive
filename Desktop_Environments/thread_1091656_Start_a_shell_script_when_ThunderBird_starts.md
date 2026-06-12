---
title: "Start a shell script when ThunderBird starts"
date: 2009-03-09
forum: Desktop Environments
---

### Post by revival on 2009-03-09
Hello all,

I need to start a shell script whenever Thunderbird is launched. The reason for this is that I have a shell script that creates a ssh tunnel to my mail server, so in order to send emails I need to start that script first.

I was thinking about pointing the Thunderbird Desktop Launcher to the script and then in the script, launch the ssh tunnel first, and then start the Thunderbird binary in the background (&)

Another issue is that I also need to provide a password for my ssh tunnel (it is a regular shell account with my school), is there any way I can automatically feed that password to the script instead of typing it every time?

Any idea how can I accomplish this task?

Thanks in advance.

---

### Post by revival on 2009-03-16
anyone? I need some enlightenment with this issue :)

---

### Post by M1GEO on 2009-03-25
I am not sure how to answer the Thunderbird part of your question.  I found this post by looking for a way to start scripts with Thunderbird.

As for the SSH password problem, there is an excellent mini howto here, which I have found to be excellent:  [http://linuxproblem.org/art_9.html]("http://linuxproblem.org/art_9.html")

As for the Thunderbird script, I assume you could just call the Thunderbird binary and background it, then continue with the script.  As for this part, I haven't figured it out yet.

Hope this is at least helpful to people looking for similar.

Kind Regards,
George Smart

---

### Post by revival on 2009-11-30
HI,

thanks for the ssh link, I already fix that part!

regarding the Thunderbird script, I manage to make it but I think it can be improved. The problem is that I am opening a secure tunnel to my mail server after launching thunderbird BUT it opens the shell screen (to avoid the opening of the shell screen, I tried to redirect the exit and error streams &2>1>/dev/null of the ssh tunnel but it does not work. The tunnel closes after 3 seconds, its like the server detects that there is no shell screen open in the other end. I also tried to add the nohup at the beginning but it didn't work either)

Here is the script:

#!/bin/bash

/usr/bin/thunderbird &
ssh -L 19025:mail.myserver.com:25 [email]myuser@myotherserver.com[/email]

Any ideas to avoid the opening of the shell script?

Thanks!

---

