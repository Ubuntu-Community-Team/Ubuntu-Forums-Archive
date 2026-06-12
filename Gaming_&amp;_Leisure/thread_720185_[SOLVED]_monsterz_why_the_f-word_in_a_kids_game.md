---
title: "[SOLVED] monsterz why the f-word in a kids game?"
date: 2008-03-10
forum: Gaming &amp; Leisure
---

### Post by regor210 on 2008-03-10
I downloaded monsterz from the repository but when I am finished playing a round, it scrolls .... is licensed under the do what the (f-word) you want licensed.... at the bottom of the games screen.

I think this is inappropriate in a kids game. 

Any ideas on how to fix it?

---

### Post by itix on 2008-03-10
*snip*

It's educational :p

---

### Post by GameGod on 2008-03-10
regor210: I would both contact the original developer, file a bug [against the package in Launchpad]("https://launchpad.net/ubuntu/+source/monsterz") and tell a MOTU or someone. This should definitely get fixed in the Ubuntu repository, I agree with you.

---

### Post by buried on 2008-03-10
Can't Fix, File a report, Kids game having that is actually quite funny.

---

### Post by rolando2424 on 2008-03-10
You probably talking about the license [WTFPL]("http://sam.zoy.org/wtfpl/").

I think in that case it's really up to the guys that created the game if they want to change their license or not (or use the acronym WTFPL, or put the license in a separate text file).

---

### Post by Sockerdrickan on 2008-03-10
HAHAHAAHHAHAHAHAHA XD

>             DO WHAT THE **** YOU WANT TO PUBLIC LICENSE
                    Version 2, December 2004

 Copyright (C) 2004 Sam Hocevar
  14 rue de Plaisance, 75014 Paris, France
 Everyone is permitted to copy and distribute verbatim or modified
 copies of this license document, and changing it is allowed as long
 as the name is changed.

            DO WHAT THE **** YOU WANT TO PUBLIC LICENSE
   TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

  0. You just DO WHAT THE **** YOU WANT TO. 

---

### Post by doorknob60 on 2008-03-10
Hmm if you wanted to you could download the source code and take it out and recompile :P

---

### Post by forrestcupp on 2008-03-10
I agree that it's pretty dumb to do something like that.

---

### Post by nutz on 2008-03-10
Why cut your kids off from the real world like that? Is it so you don't have to teach them what the word means? Do you really think it will make any difference? They will just feel silly when the other kids at school have a larger vocabulary than them.

I laugh every time I see stuff like this. It is like the parents are too afraid to introduce their kids to the real world. So they make up lies like the tooth fairy and the Easter bunny, haha!

Sure, lies are better...

My parents were honest with me right from the start and I respect them for that more than they will ever know. When other kids were talking gibberish about what Santa brought them for x-mas I knew the truth and laughed at their ignorance.

---

### Post by lha on 2008-03-11
> **regor210 said:**
> I downloaded monsterz from the repository but when I am finished playing a round, it scrolls .... is licensed under the do what the (f-word) you want licensed.... at the bottom of the games screen.

I think this is inappropriate in a kids game. 

Any ideas on how to fix it?

It might already be fixed by the developers: The changelog on [http://sam.zoy.org/monsterz/]("http://sam.zoy.org/monsterz/") informs that version 0.7.1 'removed scary language from the title screen'. The repos have version 0.7.0, so you probably have an outdated version of the game.

---

### Post by eljoeb on 2008-03-11
> **nutz said:**
> Why cut your kids off from the real world like that? Is it so you don't have to teach them what the word means? Do you really think it will make any difference? They will just feel silly when the other kids at school have a larger vocabulary than them.

I laugh every time I see stuff like this. It is like the parents are too afraid to introduce their kids to the real world. So they make up lies like the tooth fairy and the Easter bunny, haha!

Sure, lies are better...

My parents were honest with me right from the start and I respect them for that more than they will ever know. When other kids were talking gibberish about what Santa brought them for x-mas I knew the truth and laughed at their ignorance.

Not sure where you're coming from, but around here swearing isn't common with anyone but 15 year olds who watch too many movies.  It's probably the easiest way to undermine your credibility and professionalism.  It's obvious that there should be some education involved ("don't say that it makes you sound stupid"), but using it like the program did is just not necessary.

---

### Post by erginemr on 2008-03-11
> **regor210 said:**
> I downloaded monsterz from the repository but when I am finished playing a round, it scrolls .... is licensed under the do what the (f-word) you want licensed.... at the bottom of the games screen.

I think this is inappropriate in a kids game. 

Any ideas on how to fix it?

For you, I have extracted the Debian packages **monsterz** and **monsterz-data**, removed the offending word from a few files in the source code and rebuilt them under the name **monsterz-custom** and **monsterz-data-custom**. Due to the size of the files, I had to upload them elsewhere, you can download them both from:

[http://www.zshare.net/download/87767598d4cc82/](http://www.zshare.net/download/87767598d4cc82/)

If you like try these, first you need to remove the two original packages from Synaptic and install these custom packages by double-clicking on them. I have checked them and they seemed to work as expected in my system.

---

### Post by lespaul_rentals on 2008-03-11
> **eljoeb said:**
> Not sure where you're coming from, but around here swearing isn't common with anyone but 15 year olds who watch too many movies.  It's probably the easiest way to undermine your credibility and professionalism.  It's obvious that there should be some education involved ("don't say that it makes you sound stupid"), but using it like the program did is just not necessary.

The reason swearing is common with adolescents is because of the forbidden fruit effect.  If you are raised in surroundings where swearing is off-limits, you will be more tempted to do so in the rebellious stages of your life because it's the naughty thing to do.

---

### Post by regor210 on 2008-03-18
The Linux Game Tome has reported Monsterz 0.7.1 has "removed scary language from the title screen"

[http://www.happypenguin.org/news](http://www.happypenguin.org/news)

Thank you makers of  Monsterz 0.7.1  .

---

### Post by fredbird67 on 2008-03-23
I saw this too in the 0.7.0-2 version that's in the repos and found it inappropriate, so I downloaded and installed the 0.7.1 version instead.  However, they've changed it to a "WTFPL" license, and to me, that's not good enough, either, because I don't allow my kids to talk like that at all, even just referencing that word by its initial, because there's no good reason for it, and to swear like that is a definite sign of a limited vocabulary.

Therefore, since this is a kids' game, WHY DOES THE DEVELOPER INSIST ON KEEPING A REFERENCE TO THAT WORD IN THERE?!!  If he has kids, does he let them swear all they want?  If so, he needs to wake up and smell the coffee and realize that he's by far the exception and not the rule.

Until he cleans up his language, I'm sorry to do it, but I'm completely removing this game from my Ubuntu system.  To me, even just the F is unacceptable, because I don't wanna have to explain that acronym to my kids.

Fred in St. Louis

---

### Post by KIAaze on 2008-03-23
I was about to say that this license is equivalent to public domain.
Good thing I read their FAQ first:
>  Isn&#8217;t this license basically public domain?

There is no such thing as &#8220;putting a work in the public domain&#8221;, you America-centered, Commonwealth-biased individual. Public domain varies with the jurisdictions, and it is in some places debatable whether someone who has not been dead for the last seventy years is entitled to put his own work in the public domain. 

What's the public domain in soviet Russia?
American public domain: This program is property of the US-American public domain and may only be used by US citizens.
:lolflag:

---

### Post by steveneddy on 2008-03-23
I work with and around professional persons daily and we don't curse or use foul language around each other and we also feel it is inappropriate for our children to use such language.

Use of curse words or any types of foul language just downplays your education, if any, and reasserts the fact that proper language, respect for others and general positive social skills aren't available when dealing with those who choose to use such language and, in my opinion, should be avoided.

The OP chooses not to have his children be exposed to this type of language and those who posted that it was stupid for him to care otherwise should have more respect. You want free speech, as long as it is crude and offensive, but refuse to give free speech to someone who chooses not to be crude and offensive.

Free speech means you can say anything you wish, but doesn't mean that you should. I believe this is where education and respect for others kicks in, or should.

---

### Post by kidux on 2008-03-23
> **nutz said:**
> Why cut your kids off from the real world like that? Is it so you don't have to teach them what the word means? Do you really think it will make any difference? They will just feel silly when the other kids at school have a larger vocabulary than them.

I laugh every time I see stuff like this. It is like the parents are too afraid to introduce their kids to the real world. So they make up lies like the tooth fairy and the Easter bunny, haha!

Sure, lies are better...

My parents were honest with me right from the start and I respect them for that more than they will ever know. When other kids were talking gibberish about what Santa brought them for x-mas I knew the truth and laughed at their ignorance.
We tell our children about Santa, the Easter Bunny and the Tooth Fairy because we want them to grow up with a bit of wonder and mysticism about the world. Any good parent gets this, and also realizes that as they get older they need to learn more of the truth in the world. It does not mean we are sheltering them from the harshness of reality. If anything, it adds a bit of a safety net for when that harshness becomes apparent. My son is 6, and both his mother and I, as well as his grandfather, are in the military and been on deployments overseas for 1-2 years at a time. Having that little bit of mysticism has been a blessing. I grew up like you knowing they didn't exist, and I wish my child to have some of that wonderment while he still can.

> **lespaul_rentals said:**
> The reason swearing is common with adolescents is because of the forbidden fruit effect.  If you are raised in surroundings where swearing is off-limits, you will be more tempted to do so in the rebellious stages of your life because it's the naughty thing to do.
This is only true if the parents have done a poor job at raising their children and haven't been involved in their lives growing up. If you take the time to teach your kids instead of being a dictator and telling them, as they get older they are more apt to listen to you and heed your advice.

> **steveneddy said:**
> I work with and around professional persons daily and we don't curse or use foul language around each other and we also feel it is inappropriate for our children to use such language.

Use of curse words or any types of foul language just downplays your education, if any, and reasserts the fact that proper language, respect for others and general positive social skills aren't available when dealing with those who choose to use such language and, in my opinion, should be avoided.

The OP chooses not to have his children be exposed to this type of language and those who posted that it was stupid for him to care otherwise should have more respect. You want free speech, as long as it is crude and offensive, but refuse to give free speech to someone who chooses not to be crude and offensive.

Free speech means you can say anything you wish, but doesn't mean that you should. I believe this is where education and respect for others kicks in, or should.
Couldn't have said it any better.

---

### Post by noerrorsfound on 2008-03-23
I think it's ridiculous how people get upset just by seeing a word. "Bloody" is considered a swear word in a few countries, yet here in the USA people would say it's not a swear word at all. "Swears" and "curse words" change over time, with new words becoming inappropriate and others being acceptable. So what's the point? If I say "banana" is now a swear word, would you get upset at people saying banana?
[quote=Definition of bitch]1.	a female dog.
2.	a female of canines generally.[/quote]
These were the original definitions. Then, people started saying it was a swear word, and it's suddenly unacceptable.

---

### Post by KIAaze on 2008-03-23
I just checked version 0.7.1 and it doesn't seem to show the F-word ingame.
Current scroll text:
```
COPYRIGHT = 'MONSTERZ - COPYRIGHT 2005 - 2007 SAM HOCEVAR - MONSTERZ IS ' \
            'FREE SOFTWARE, YOU CAN REDISTRIBUTE IT AND/OR MODIFY IT ' \
            'UNDER THE TERMS OF THE WTFPL LICENSE, VERSION 2 - '

```

However, the license is still the same and the F-word can be seen when reading the license or running "./monsterz.py -v":
```
grep -in **** *
COPYING:1:            DO WHAT THE **** YOU WANT TO PUBLIC LICENSE
COPYING:10:            DO WHAT THE **** YOU WANT TO PUBLIC LICENSE
COPYING:13:  0. You just DO WHAT THE **** YOU WANT TO.
monsterz.c:12: *   modify it under the terms of the Do What The **** You Want To
monsterz.py:10:   modify it under the terms of the Do What The **** You Want To
monsterz.py:1920:    print 'the terms of the Do What The **** You Want To Public License, Version 2, as'

```
(all "****" corresponding to the F-word obviously)

Easy solution (which you are legally allowed to apply by the license):
```
grep -il <F-word> * | xargs sed -i s/<F-word>/****/gi
```
Replace <F-word> with the F-word (without the <>).

Only problematic file:
> grep -ri **** *
Binary file graphics/bigtiles.png matches


PS: The porn section on the WTFPL site is the most child-friendly I have ever seen. :lolflag:

---

### Post by steveneddy on 2008-03-23
> **noerrorsfound said:**
> I think it's ridiculous how people get upset just by seeing a word. "Bloody" is considered a swear word in a few countries, yet here in the USA people would say it's not a swear word at all. "Swears" and "curse words" change over time, with new words becoming inappropriate and others being acceptable. So what's the point? If I say "banana" is now a swear word, would you get upset at people saying banana?

These were the original definitions. Then, people started saying it was a swear word, and it's suddenly unacceptable.

It's called **context**.

Which means looking at the rest of the conversation around the word you are using.

If we were talking about a mother dog, it would be appropriate to use this word.

If I were talking about your Mom or girlfriend, you would be offended, and it is never appropriate.

Context.

In private conversation with your friends who also use this language, it is appropriate. In public, where we should respect others, do not use such language.

---

### Post by cisforcojo on 2008-03-25
:shock: Someone please close this.

---

