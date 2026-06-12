---
title: "HLDS will not install"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by pimpedz on 2007-08-07
Hi, I'm new to linux and Ubuntu and am having trouble getting hlds to install on my PS3. I got it from here :  [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin) using wget.  When I type ./hldsupdatetool.bin I get this error: bash: ./hldsupdatetool.bin: cannot execute binary file
When I type sudo ./hldsupdatetool i get sudo: ./hldsupdatetool: command not found

---

### Post by hikaricore on 2007-08-07
Hello ^_^

Try:

```

chmod +x hldsupdatetool.bin

```

Then run it as normal.

This flags the file as executable.  The file system works this way for the sake of system security.

---

### Post by pimpedz on 2007-08-07
It still gives me the same error.


Nevermind it gives me this error now : ./hldsupdatetool.bin: 1: Syntax error: "(" unexpected

---

### Post by hikaricore on 2007-08-07
> [hikaricore@devistate:/media/devistate (12.4 Mb)]$ chmod +x hldsupdatetool.bin
[hikaricore@devistate:/media/devistate (12.6 Mb)]$ sudo ./hldsupdatetool.bin
Password:
STEAMTM SUBSCRIBER AGREEMENT

This Agreement is written only in the English language, which language will be controlling in all respects.  All communications to be made or given pursuant to this Agreement will be in the English language, except as may be required under applicable law.

1.  REGISTRATION AND ACTIVATION.

Steam is an online service (.Steam.) offered by Valve Corporation (.Valve.).

You become a subscriber of Steam (.Subscriber.) by installing the Steam client software and completing the Steam registration.  Additionally, as a Subscriber you may obtain access to certain services, software and content (.Subscriptions.) available to Subscribers. This Steam Subscriber Agreement (.Agreement.) is a legal document that explains your rights and obligations as a Subscriber. Please read it carefully.

Runs fine for me.  Make sure you do it exactly like so:

```

chmod +x hldsupdatetool.bin
sudo ./hldsupdatetool.bin 
```

You have to type the file name exactly.  Linux does not automatically assume executable the extention like DOS based CLI does.

---

### Post by pimpedz on 2007-08-07
Nope, I can't figure out what I'm doing wrong.

---

### Post by hikaricore on 2007-08-07
I just noticed that you said you're running on a PS3.
Certian binary installers may not work properly on a PS3 for various reasons.

I'm not 100% sure what platform the PS3 architecture is considered, but if it's not a 32bit system then 32bit binaries may fail.

[http://help.ubuntu.com/community/PlayStation_3](http://help.ubuntu.com/community/PlayStation_3)

Based on the info at the community WIKI the PS3's architecture is similar to a powerpc.

---

### Post by pimpedz on 2007-08-07
Then what should I do?

---

### Post by hikaricore on 2007-08-07
Search around to see if they have a build for your architecture?
If they don't you may be out of luck.

I wasn't even aware that the proper video drivers had been released for the PS3 yet.

Even if you got it running unless you had access to the hardware properly you'd still be SOL.

---

### Post by pimpedz on 2007-08-07
There's no way to emulate something else to get it to run?

---

### Post by hikaricore on 2007-08-07
> **pimpedz said:**
> There's no way to emulate something else to get it to run?

No I'm sorry I don't believe so.

----

However I found a Ubuntuish site about the PS3: [http://psubuntu.com/](http://psubuntu.com/)

I'm not sure if it will help at all but they have a forum that could probably answer your questions better than I can.

---

### Post by pimpedz on 2007-08-07
Thanks for all your help.

---

### Post by kbutcher5 on 2012-01-08
This article should help you, I know this is old, but I hate unanswered questions, gl hf:
[http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10](http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10)

---

