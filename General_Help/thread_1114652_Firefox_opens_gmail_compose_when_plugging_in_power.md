---
title: "Firefox opens gmail compose when plugging in power cord"
date: 2009-04-03
forum: General Help
---

### Post by Auslegung on 2009-04-03
I know, weirdest thing ever, huh?  I have an eeePC 1000h running Ubuntu 8.10 Adam's kernel.  I was wanting gmail to be my default mailto: link thing and I ran across this code:

```
perl -MURI::Escape -e '$to= shift;if ($to =~ /^([^\?]+)\?(.*)$/){$to=$1;$args="&".$2;$args=~s/\&subject=/&su=/};$to =~
s/^mailto://i;exec("firefox","https://mail.google.com/mail/?view=cm&fs=1&tf=1&cmid=22&to=".URI::Escape::uri_escape($to).$args);' %s
```

I added that this past weekend, and I started noticing the problem sometime around early this week.  I'm not entirely sure if this is related.  The first few times it happened I kinda assumed I had hit a button or something, so I'm not sure the first time it happened.  I don't know what the  code means, so basically, is that the problem?  I'm at work w/out my power cord so I can't erase the code and plug it in, or I would.  I've made a couple other tweaks this week but nothing in particular I can remember, so idk what else it could be.  Thanks in advance.

Update: I deleted the code, plugged in my power code and Firefox did nothing.  I put the code back in, plugged in my power code, and it opened gmail compose.  I have no idea what the code means so if someone could read that and tell me what part to delete so this no longer happens, I'd appreciate it.

---

