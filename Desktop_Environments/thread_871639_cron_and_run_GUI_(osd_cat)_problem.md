---
title: "cron and run GUI (osd_cat) problem"
date: 2008-07-27
forum: Desktop Environments
---

### Post by cccccccc on 2008-07-27
Hellou,
I have this problem. I wanna use osd program osd_cat to display some message at certain time. I wrote simple bash script, so when I run the script from command, I can see my osd message. Problem is, that this does not work with cron. I did some google, and folks were telling, that I should write to cron:
export DISPLAY=:0 && myscript.
I did that, but this does not work neither. When I run command: echo $DISPLAY I get :0.0, so instead export DISPLAY=:0 I set export DISPLAY=:0.0 in cron, but no go after all:(
I redirect output from osd_cat program in cron and it gives me this:
"No protocol specified
Error initializing osd: Cannot open display"
Can anyone help me with this? Thanks.

I use Ubuntu 8.04, Gnome 2.22.2

---

### Post by dirtydev on 2011-02-16
Did you ever find an answer to your issue?

---

