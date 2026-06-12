---
title: "How to &quot;add lines&quot;?"
date: 2009-06-18
forum: General Help
---

### Post by eudemonis on 2009-06-18
Hi I've been trying to fix audio pulse problem with Skype... I found some instructions but I'm not sure how to follow this... in particular I don't know hot to "add lines".. here is part of the instructions..

"I've seen a lot of guides to get Skype to work, but I only did it by following a post on the Ubuntu Forums.

Firstly, add these lines:

default-fragments = 8
default-fragment-size-msec = 5

at the end of "/etc/pulse/daemon.conf"

Then, edit "~/.asoundrc" and add the following lines if they do not exist:

pcm.pulse { type pulse }
ctl.pulse { type pulse }

SO HOW DO I "ADD LINES"???

---

### Post by MyR on 2009-06-18
sudo gedit /etc/pulse/daemon.conf

then paste those lines into the text file & save.

sudo gedit ~/.asoundrc

peace

---

### Post by eudemonis on 2009-06-18
thanks MyR...

---

### Post by MyR on 2009-06-18
Glad I could help :] I like the easy questions

---

### Post by eudemonis on 2009-06-18
yea now I'm gediting everything hehehehe that was one of the basic things I just learned for life hehe

---

### Post by eudemonis on 2009-06-18
not much luck with skype though :-) this audio pulse problem is a curse

---

### Post by t4thfavor on 2009-06-18
I hate skype, I opted for Ekiga.net, I know lots of people use Skype, I just never understood the whole pay thing. 

Now I run my own asterisk server with CordiaIP trunks and all paying for usage is forgotten.

---

### Post by eudemonis on 2009-06-19
thanks for this info t4thflavor I'll try it out...

---

### Post by eudemonis on 2009-06-19
I just tried getting Ekiga account but it asks me to get a paid account... could u explain this own asterik server business or refer me to a site... or do I need to buy an account (if so then so much for "free your speech hehehe)

> **t4thfavor said:**
> I hate skype, I opted for Ekiga.net, I know lots of people use Skype, I just never understood the whole pay thing. 

Now I run my own asterisk server with CordiaIP trunks and all paying for usage is forgotten.

---

