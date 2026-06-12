---
title: "I can't get TA Spring working no matter what I do"
date: 2007-10-16
forum: Gaming &amp; Leisure
---

### Post by jarocooke on 2007-10-16
Does anyway have a fool proof way of installing TA Spring on Gutsy 64bit?

I have tried all the usual suspects (debspring, the various howto's, compiling instructions, etc...).

[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di)

Using the " How to recompile Spring for a different Debian'isch Distribution" instructions found on the above link I have built my own deb installed it and I can get the menu to run (after changing the font in springrc file).  However when I try to actually play a game it crashes with the following message.

```

jaro@jaro-laptop:~$ spring
I: workdir is '/home/jaro/.springdir/jaro-laptop_0.0'
I: type spring-setup to configure spring
Warning: Incorrect/Missing content:
  file gamedata/explosion_alias.tdf not found
jaro@jaro-laptop:~$ 

```

Does anyone have any ideas, I am out.  If you have a way of installing that worked for you could you let me know what you did, because this is driving me mad.  I haven't ever been able to Spring working and I really want to give it a go as it looks pretty cool.

Thanks.

---

### Post by jarocooke on 2007-10-16
OMG, I have found a "gamedata" folder, which contained the missing explosions_alias.tdf file, and copied the whole thing into the ~/.springdir/jarolaptop_0.0/ folder and now when I run spring, the error message reads:

```
jaro@jaro-laptop:~$ spring
I: workdir is '/home/jaro/.springdir/jaro-laptop_0.0'
I: type spring-setup to configure spring
Warning: Incorrect/Missing content:
  Parse error in gamedata/explosion_alias.tdf at line 45 column 2 near
}
jaro@jaro-laptop:~$ 

```

I'm starting to think that this game wasn't designed to actually be played, but rather the entertainment comes from trying to make the thing work!

---

