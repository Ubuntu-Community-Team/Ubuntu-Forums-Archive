---
title: "beryl wont run at start up ......no matter what i do"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by techno-mole on 2007-05-23
hello.
well ive come back to ubuntu and im using 7.04, had an issue with a hard drive and had to wait for a new one, alot easier to set up this time.
so the problem is that i cant get beryl to run on start up, ive followed various guides and no joy, it just wont have it.
i know that you can tell it to run at start by going to - system--> preferences--> sessions and then click add and type in beryl-manager (one guide foe fiesty that all you need, but you get an error if you dont put a command in) so in the command section on guide said to put beryl --replacer, this didnt work either and all it really achieved was to knock my sound card out (fixed that though)
so how the hell do you get beryl to run at start up under fiesty ?
any help will be appreciated.

---

### Post by crimesaucer on 2007-05-23
For Beryl AiGLX, I use the startberyl.sh script that my /usr/share/xsessions recognizes from the entry in my Autostarted Applications.

If you use Beryl AiGLX I can tell you exactly how to do it, it you use a different version then I can't help beside saying go check out the Beryl installation wiki page archive, or the Legacy support in the Compiz forums.

---

### Post by Znupi on 2007-05-23
If Beryl Xgl, go to sessions, click Add and:

Name: Beryl
Command: beryl-manager

That's all. At least this way it works for me.

---

### Post by jackiecanev2 on 2007-05-23
xgl or aiglx?
and is beryl working properly or no?

i know that i had a hell of a time getting beryl to load, but i had to copy an xgl session script and load an xgl session before i could get everything with beryl-manager loaded in sessions.

---

### Post by sonicprogress on 2007-05-23
what graphics card do you have?

ATI? Nvidia? Model?

Are you using XGL or AiGLX?

log files??? xorg.conf?

the more info you post, the better your chances...

---

### Post by techno-mole on 2007-05-24
cheers for the help, and sorry for not replying sooner, i couldnt find the thread i started, note to self  - check private messages more often.
anyway got beryl running, all i did was to go to --> system --> preferences --> sessions and then i clicked new, and in the name of the application i put beryl, and as a command i put beryl-manager and hey presto it worked, so cheers for the help.

---

