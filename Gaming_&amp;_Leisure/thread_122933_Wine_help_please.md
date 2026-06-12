---
title: "Wine help please"
date: 2006-01-28
forum: Gaming &amp; Leisure
---

### Post by schnabea on 2006-01-28
Last time I successfully ran winecfg I accidently clicked the ALSA option on the audio tab and now every time I run Wine or winecfg I get the following error message:

ALSA lib seq_hw.c:455: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  14

Any ideas on how to fix this?

---

### Post by Who on 2006-01-28
Hi,
I don't know _exactly_ what to do but I can point you. the _much_ less sensible solutions are at the top :P

Depending on how precious your configuration is you could:
(most destructive:) obliterate ~/.wine using delete
delete just the system.reg (or simlar name, use the wine manuals to be sure - I'm not on Ubunut right now) 
(least distructive) edit the system.reg with a registry editor. Unfortunately if you can't open any wine apps this is gonna be unlikely.

In windows the registry is binary, not text - but I seem to remember wine dies it differently. you could try opening the system.reg (same applies as above to the name, it is just in ~/.wine) in a text editor like gedit.

I can have a look when I get back to my Ubuntu box on Monday if you want (post again or private message if you do want)

Good Luck

Who

---

### Post by schnabea on 2006-01-28
I can edit the system.reg file with gedit, but I have no idea which key or whatever to change in there.

---

### Post by Who on 2006-01-29
Righty: here is my plan:

When I get back to my breezy PC I copy my system.reg, then change the alsa option and then run a diff on them both (diff compares two files and says where they have been changed) - I could then paste the differences here and you could try and fix it....ok?

I won't be able to do that 'till Monday or Tuesday night though - sorry

---

### Post by schnabea on 2006-01-30
sure that works. Thanks for the help :)

---

### Post by pkroks on 2006-04-02
I have a similar problem. Please post your system.reg file.

---

