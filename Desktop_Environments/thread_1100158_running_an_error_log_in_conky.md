---
title: "running an error log in conky"
date: 2009-03-18
forum: Desktop Environments
---

### Post by turvyc on 2009-03-18
Hi all,

After lurking around for a while, I'm finally ready to emerge. These forums have been a HUGE help so far . . . very impressive

So I've been searching for a while for a way for conky to run an error log on my desktop. The closest I found was somebody's background image, with no config file in sight. Check it out to see what Im' talking about.

Any ideas?

---

### Post by m_duck on 2009-03-19
Hey,

You will want a line in your ~/.conkyrc that looks something like the following:```
${execi 60 cat /var/log/messages | tail -n5 | fold -s -w50}
```This will display the last 5 lines of /var/log/messages, and update it every 60 seconds. The fold part is to wrap lines so you can see the whole message, it is currently allowing 50 columns before wrapping, but will check for spaces and wrap there if it would otherwise cut off in the middle of a word. The above screenshot would not have the "-s" switch in.

---

### Post by turvyc on 2009-03-20
Thanks! That worked great!!!

I'm new to Ubuntu (obviously :) ), and I was wondering if there are other useful logs other than /var/log/messages . . .

Any specific ones that you all out there like to use? Specifically I'd like something that outputs the error messages of any running applications . . . for example if Songbird or something bites the dust, I'd like to see the error output right on my desktop. Is there one log for this, or is it application-specific?

Thanks!

---

### Post by m_duck on 2009-03-20
There are others, mostly all in /var/log. [This site](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/) seems to list the majority with a description of what they do, so you can substitute one of them in the line in your conky.

As for the application specific thing I'm not sure, though that is far from meaning it's not possible. From the site above, it looks like /var/log/apport should have messages pertaining to program crashes but that does not exist on my install.

If you wanted to try to diagnose a problem with songbird or a program specifically, run it from the terminal, then when it crashes it will give an output which you can then use for troubleshooting.

---

