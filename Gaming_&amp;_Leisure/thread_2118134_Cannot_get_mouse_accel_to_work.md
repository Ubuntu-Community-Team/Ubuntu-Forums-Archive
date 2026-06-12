---
title: "Cannot get mouse accel to work"
date: 2013-02-20
forum: Gaming &amp; Leisure
---

### Post by Inoki on 2013-02-20
***** Thread can now be closed, a bug report has been filed. *****

Hi all,

am on Ubuntu Studio 12.10 x64 bit with Steam and used to play CS with mouse acceleration. Problem is, I cannot get it to work despite the many options I've tried configuring it in mouse settings. It seems as if it was always off.

If you hop on Windows and compare to Linux, the accel is different. I need to get that same accel to work on Ubuntu.

To clarify a bit more:

When I play with the settings and adjust them accordingly, the accel can be felt on the desktop, but not under Steam. There it works the same way as before. As if it was turned off. I tried, during a game, to adjust to my liking, on the desktop the mouse goes like crazy, in the game as if accel was turned off.

Any ideas?

---

### Post by stinkeye on 2013-02-20
Open up both your mouse settings and dconf-editor @ **org.gnome.settings-daemon.peripherals.mouse** 
and try some different settings.

---

### Post by Inoki on 2013-02-24
These are the settings in xfconf:

[IMG]http://i47.tinypic.com/3325gmt.png[/IMG]

Can someone tell me what are the highest accepted values for accel?

---

### Post by Inoki on 2013-02-24
Or could someone give me a good tip on a DE that has the best management of peripherals? I.e. I'd need to get my mouse accel properly working. I need it to be real speedy, since I've always used mouse accel in games.

On the desktop the acceleration works, the mouse is blazing fast, but under Steam no, as if it was turned off.

Update:

Running Ubuntu Main now and it's the same. Accel works on desktop, not under Steam.

---

### Post by ripps818 on 2013-02-26
The mouse acceleration in XFCE4 just ruins some games, and it seems that it's impossible to disable it entirely via configuration. So, I just run a command at login that basically disables all mouse acceleration. Even outside of games, I think it works better without acceleration too.

```
xset m 1/1 4
```

---

### Post by Inoki on 2013-02-26
> **ripps818 said:**
> The mouse acceleration in XFCE4 just ruins some games, and it seems that it's impossible to disable it entirely via configuration. So, I just run a command at login that basically disables all mouse acceleration. Even outside of games, I think it works better without acceleration too.

```
xset m 1/1 4
```

You didn't get me. I need to get it to work, not disable.

Some people actually rely on acceleration. I'm one of them. I need it like salt in a soup.

---

### Post by ripps818 on 2013-02-26
> **Anathaen said:**
> You didn't get me. I need to get it to work, not disable.

Some people actually rely on acceleration. I'm one of them. I need it like salt in a soup.

That same command can be used to increase acceleration too.

```
xset mouse [[accel_mult[/accel_div] [threshould]]
```

Play around with the values until you get something that feels comfortable.

I'm pretty sure that most acceleration configuration tools just modify these values anyway.

EDIT:
Okay, I think I misread your post.
You're having problems with the in-game mouse acceleration, not the desktops.
I've sorta experienced this in TF2, and turning off desktop accel and boosting mouse sensitiviy improved things, but I think the mouse accel code in Valve's games isn't that good yet.

---

### Post by Inoki on 2013-02-26
> **ripps818 said:**
> That same command can be used to increase acceleration too.

```
xset mouse [[accel_mult[/accel_div] [threshould]]
```

Play around with the values until you get something that feels comfortable.

I'm pretty sure that most acceleration configuration tools just modify these values anyway.

EDIT:
Okay, I think I misread your post.
You're having problems with the in-game mouse acceleration, not the desktops.
I've sorta experienced this in TF2, and turning off desktop accel and boosting mouse sensitiviy improved things, but I think the mouse accel code in Valve's games isn't that good yet.

Precisely. Accel works on desktop, not in game. I need it. But as you say, this problem is most likely related to Steam.

---

### Post by Bölvaður on 2013-02-26
What configs did you change in-game and what values did you set for them?

Many guides emphasize on the importance of disabling mouse acceleration in all of the Counter Strike games. What you want is 1:1 movement in game and in your hands, which makes perfect sense if you have read any book about engineering psychology. It should improve your aim to remove acceleration no matter how practiced you are with it, I did, my aim is still the same after some adjustments.

Btw which mouse and mousepad do you have?

---

### Post by Inoki on 2013-02-26
How can it possibly be so difficult to understand, that some people actually **do use acceleration**. I've been using it since forever and here is why:

*Acceleration allows me to quickly turn even with low mouse sensitivity, that being said, I am able to aim smooth where I can see, while having the ability to turn tremendously quick _thanks to mouse accel_ even on low mouse sens, which without mouse accel is not possible. In a game, with low mouse sens, before you manage to do a 90° turn, you're dead.*

**I'd appreciate, if people quit forcing their *"don't use mouse accel"* on me** and at the same time skip psychology parts. Just because many "pro" jerks don't use mouse accel it doesn't mean, that everybody like sheep have to do the same.

I don't go with the ratio of 1:1. I prefer it something like (on Windows): 1:8, i.e. 1 = game sens, 8 = Windows sens (acceleration). Acceleration is very natural in reality also. When you hold a gun and aim, you aim very smooth to be precise, while, when scouting new areas, you do swift movements, as if accelerated, to have your environment under control. If it was 1:1, you'd turn the same way as you aim, which would make you an easy kill.

I've been playing e.g. Counter-Strike 5 years competitively back in the days and in fact it was mouse accel what made me one of the most feared gamers in my country. Utilizing accel I was able to perform with dead-sharp reflexes. I never forced my setup on others, so everyone should respect mine, hence kindly asking to stick to the topic. I really had enough of the parts "mouse accel is bad for you...... without it it's way better......" I simply DO NOT CARE. I want to play the way I like and I'm used to.

I've tried even without it, but for me it sucks big time. When I increase mouse speed I can't aim smooth anymore. Not everyone has the same motoric in their hand and increasing mouse sens without accel renders it unstable for me. The setup I use is the result of reasearch for many years, during which I developed my own, unique technique of playing, just as other gamers look for what suits them best and that is the only way to victory in any field, be yourself, do what you like, how you like it.

The mouse I use is a Microsoft Intellipoint Wheelmouse 1.1A, but that is irrelevant, since I can perform the same with about any mouse and I'm used to this one, won't change for another one.

People use different settings and they should be free to do so. No one should be forced other's opinion on them.

[COLOR=#ff8c00]*In reality you also aim smooth where you can see, but need to be able to turn quick, which makes perfect sense. (*[/COLOR][COLOR=#ff0000]*Yet even better than having the same sens for everything like in a game. You don't turn that way in reality*[/COLOR][COLOR=#ff8c00]*. *[/COLOR][COLOR=#008000]*_The velocity of each movement changes_*[/COLOR][COLOR=#ff8c00]*_, that is why, if you want to have it put this way, using acceleration is far more reasonable than not using it._)*[/COLOR]

---

### Post by cristo-father on 2013-02-26
Have you tried other steam/non-steam games to see if it is indeed a steam or engine issue(u can try quake live, urban terror, warsow etc) ?

Anyway i agree, some people like accel, some don't(i don't :P), its a matter of preference.

---

### Post by Inoki on 2013-02-26
> **cristo-father said:**
> Have you tried other steam/non-steam games to see if it is indeed a steam or engine issue(u can try quake live, urban terror, warsow etc) ?

Anyway i agree, some people like accel, some don't(i don't :P), its a matter of preference.

Nope, but I will and will post the results here.

---

### Post by stinkeye on 2013-02-26
> **Anathaen said:**
> People, what is so difficult to understand about the fact, that some people actually **do use acceleration**. I've been using it since forever and here is why:

*Acceleration allows me to quickly turn even with low mouse sensitivity, that being said, I am able to aim smooth where I can see, while having the ability to turn tremendously quick _thanks to mouse accel_ even on low mouse sens, which without mouse accel is not possible. In a game, with low mouse sens, before you manage to do a 90° turn, you're dead.*

**Don't force your *"don't use mouse accel"* on me!** And don't go with any psychology things on me either. Just because many "pro" jerks don't use mouse accel it doesn't mean, that everybody like sheep have to do the same!

No, I don't go with the ratio of trying to achieve mouse movements 1:1. I prefer it something like (on Windows): 1:8, i.e. 1 = game sens, 8 = Windows sens (acceleration). Acceleration is very natural in reality also. When you hold a gun and aim, you aim very smooth to be precise, while, when scouting new areas, you do swift movements, as if accelerated, to have your environment under control. If it was 1:1, you'd turn the same way as you aim, which would make you an easy kill.

I've been playing e.g. Counter-Strike 5 years competitively back in the days and guess what, mouse accel made me one of the most feared gamers in my country, because with it was able to perform with dead-sharp reflexes and all the others didn't use accel. I never forced my setup on them, so everyone should respect mine, hence kindly asking to stick to the topic, ok?

I need mouse accel to work in-game as well, not only the desktop. I like it that way, I use it. I have been for years and I'm not gonna dodge my settings just because someone forces their opinion of "it's better to play without mouse accel" on me.

I've tried playing without it and for me it sucks big time. When I increase mouse speed I can't aim smooth anymore. Not everyone has the same motoric in their hand and increasing mouse sens without accel renders it unstable for me.

The setup I use is the result of reasearch for many years, during which I developed my own, unique technique of playing, just as other gamers look for what suits them best and trust me I've tried playing without mouse accel as well. It simply doesn't work for me.

The mouse I use is a Microsoft Intellipoint Wheelmouse 1.1A, but that is irrelevant, since I can perform the same with about any mouse and I'm used to this one, won't change for another one.

People use different settings and they should be free to do so. No one should be forced other's opinion on them.

In reality you also aim smooth where you can see, but need to be able to turn quick, which makes perfect sense.

Sheest, pretty aggressive response for someone trying to help.
Lighten up.
Good luck with that.

---

### Post by Inoki on 2013-02-26
> **stinkeye said:**
> Sheest, pretty aggressive response for someone trying to help.
Lighten up.
Good luck with that.

That wasn't meant to be aggressive. The problem is, whereever I turned to with this problem the only response I got was "don't use accel" and at some point I got the same feeling with the post that was supposed to "help". It was just a firm explanation of the problematic, going into details. Was not meant to attack anybody.

I edited my post for it to seem "less offensive", because it was not meant to be, but I have to admit I was outraged by this part:

*"Many guides emphasize on the importance of disabling mouse acceleration in all of the Counter Strike games. What you want is 1:1 movement in game and in your hands, which makes perfect sense if you have read any book about engineering psychology. It should improve your aim to remove acceleration no matter how practiced you are with it, I did, my aim is still the same after some adjustments."*

- I don't care about guides that emphasize this or that. _It's plain forcing someone to get used to what others use._ **WHY SHOULD I?!** Should I buy Persil instead of Ariel just because some advert in TV says it's better, while I have my own experiences with another appliance?

If people copy one another like trained monkeys and go by the saying: "Hey, since it works for him, it will work for me too!" is plain BS, but ok, I accept their decision and I don't care if they do this sort of monkey business, but not me.

Everyone has the freedom and the right to use what they want / feel most comfortable with. I am not forcing anybody to use accel, so no one should force me not to use it. Period.

Instead of lecturing me what is better for me, which only I know best, let's focus on the topic and get this fixed, shall we?

---

### Post by ripps818 on 2013-02-28
I understand your angry and frustrated, but I think you're misinterpreting people's intentions. They aren't telling you to not use accel because they don't want to help you, it's that they can't help you. As far as I know, there isn't a real solution to in-game mouse acceleration yet. Mouse acceleration is built into the display server, and it's not very sophisticated. And Valve's attempt to do a custom software one either isn't working or it just plain sucks.

There is no real solution or workaround yet. The best option is to just not use acceleration and wait until someone comes up with a better option. I know it might not be the answer you want, but these people aren't paid to give you solutions, we all are friends and volunteers in a community and we're just trying to help each other.

I recommend filing some bug reports and contacting the actual software developers about if there's a solution or if they can make a bug fix.

I believe Valve uses their github steam-for-linux account to track issues and bugs in the Steam software and it's games:
[https://github.com/ValveSoftware/steam-for-linux/issues]("https://github.com/ValveSoftware/steam-for-linux/issues")

P.S. Have you tried running CS using the Windows version in Wine? From what I hear, TF2 runs nearly as well in Wine as it does natively, and the mouse acceleration might work better in wine too.

---

### Post by cristo-father on 2013-02-28
I heard from someone that uses linux and plays quake, that it indeed works well. So it seems its a CS thing. Anyway i think wine supports accel, so i guess u can try running cs with wine.

---

### Post by Inoki on 2013-02-28
> **Bölvaður said:**
> Many guides emphasize on the importance of disabling mouse acceleration in all of the Counter Strike games. What you want is 1:1 movement in game and in your hands, which makes perfect sense if you have read any book about engineering psychology. It should improve your aim to remove acceleration no matter how practiced you are with it, I did, my aim is still the same after some adjustments.

> **ripps818 said:**
> I understand your angry and frustrated, but I think you're misinterpreting people's intentions. They aren't telling you to not use accel because they don't want to help you, it's that they can't help you. As far as I know, there isn't a real solution to in-game mouse acceleration yet. Mouse acceleration is built into the display server, and it's not very sophisticated. And Valve's attempt to do a custom software one either isn't working or it just plain sucks.

There is no real solution or workaround yet. The best option is to just not use acceleration and wait until someone comes up with a better option. I know it might not be the answer you want, but these people aren't paid to give you solutions, we all are friends and volunteers in a community and we're just trying to help each other.

I recommend filing some bug reports and contacting the actual software developers about if there's a solution or if they can make a bug fix.

I believe Valve uses their github steam-for-linux account to track issues and bugs in the Steam software and it's games:
[https://github.com/ValveSoftware/steam-for-linux/issues](https://github.com/ValveSoftware/steam-for-linux/issues)

P.S. Have you tried running CS using the Windows version in Wine? From what I hear, TF2 runs nearly as well in Wine as it does natively, and the mouse acceleration might work better in wine too.

If you check the above post it's clear the good man, although it seems he's trying to help, he's in fact just infuriating me, because that's the same approach I've met everywhere. People just tell you "don't use accel", but that is not what I came here asking for. I turned to this forum for a solution, but it seems this is a VALVe-related issue and their platform, they need to fix this.

I was hoping, that there would be some sort of workaround for this, maybe some talented hackers could help me out.

I've tried running Steam via Wine, but that, to say it bluntly, sucked. I'll just stick to the native client and hope for a fix from VALVe's side. I've already filed a bug report and they know about it. **[The issue can be tracked here]("https://github.com/ValveSoftware/halflife/issues/630")**.

Thanks for all the efforts, but this is beyond Ubuntu.

---

### Post by kaldor on 2013-03-02
> **Don't force your *"don't use mouse accel"* on me!** And don't  go with any psychology things on me either. Just because many "pro"  jerks don't use mouse accel it doesn't mean, that everybody like sheep  have to do the same!

As someone who has spent a lot of time playing competitive FPS games such as Quake and Counter-Strike, I have to jump on this :)

There's a reason why pros disable mouse acceleration- it's inaccurate. I'm assuming you're only using it because you are used to it and find it too hard to get used to otherwise. I was the same way for a few years, then I decided to play without mouse accel. After a few days of adjusting I could never go back to using accel. To me, there's just no comparison. The mouse **goes where it is supposed to** and I don't need to reposition my crosshair because it decided to speed up on me, even if that speed is very slight. Granted, if you just play public/casual servers then do whatever you want. 

It's not a matter of people just doing what "pros" do just because they're "pro". They aren't good players because they use those settings, they use those settings because they're good players and know what to do.

Nutshell: If you're serious about FPS games, don't use mouse accel. Acceleration forced you to overshoot your target and readjust.

---

### Post by Inoki on 2013-03-02
> **kaldor said:**
> As someone who has spent a lot of time playing competitive FPS games such as Quake and Counter-Strike, I have to jump on this :)

There's a reason why pros disable mouse acceleration- it's inaccurate. I'm assuming you're only using it because you are used to it and find it too hard to get used to otherwise. I was the same way for a few years, then I decided to play without mouse accel. After a few days of adjusting I could never go back to using accel. To me, there's just no comparison. The mouse **goes where it is supposed to** and I don't need to reposition my crosshair because it decided to speed up on me, even if that speed is very slight. Granted, if you just play public/casual servers then do whatever you want. 

It's not a matter of people just doing what "pros" do just because they're "pro". They aren't good players because they use those settings, they use those settings because they're good players and know what to do.

Nutshell: If you're serious about FPS games, don't use mouse accel. Acceleration forced you to overshoot your target and readjust.
Again, just because you were unable to perform well with it, doesn't mean others cannot handle it.

- inaccurate? Oh I could show you how damn accurate I am with it. Mouse accel actually allows me to operate on different sensitivities. While some prefer to have one sensitivity for everything, which even in reality is illogical, because you don't perform all movements at the same velocity, others utilize the option to operate with different velocities, e.g. the advantage is I can aim smooth where I can see, since when I don't do a swift curve, the mouse accepts the in-game sens, so if that is set to low values, I aim smooth, when I do a quick swing, then accel activates, allowing me to turn even on low sensitivities as if I had just changed my sens only for the sake of turning around.
- mouse doesn't go where it's supposed to? Then you're doing it wrong. You simply cannot handle accel, just **admit your own inability**!

Whenever there's a failure at something, only human factor can be blamed. The system on its own doesn't do anything, you control it, and if you cannot control accel, it's your fault. If you dump it and don't see its potential, ok, your choice, but _spare me of your lectures_. I've heard the same sh*t all over and over and yet people were unable to comprehend how come I was always able to perform that well with accel and I would never turn away from it. So live with it.

If you have nothing better to say regarding the topic, then remain silent.

[COLOR=#ff0000]This topic was opened for a workaround, for technical help, not listening to trash people enforce on people. If I cared about someone's opinion on accel, I'd open a separate thread for it.[/COLOR]

As for those, who are convenient with being a copy of a copy: (using settings just because they work out for someone else)

*"Stop trying to be everyone else's perfect." *In the end, it's not you. You just adopt something because someone else uses it. But why doesn't that surprise me in this consumer's world.

I at least am not ashamed of what I developed over all those years. Anything can be done, even accel mastered.

P.S.:

You know what's ironic? Checking your signature I stumbled upon this: [http://ubuntuforums.org/showthread.php?t=865750](http://ubuntuforums.org/showthread.php?t=865750)
It says how preaching is bad, why don't you learn something from your own signature?

> **smartboyathome said:**
> Let me ask you this: when was the last time this worked to convert you to anything? It just doesn't work with humans. If you try to force the decision on most people, they will reject it. Its great that you love it, but maybe it won't work for someone else, or they are happy with what they have.

---

### Post by kaldor on 2013-03-02
Are you really this worked up over a Counter-Strike post? 

> Oh I could show you how damn accurate I am with it. Mouse accel actually  allows me to operate on different sensitivities. While some prefer to  have one sensitivity for everything, which even in reality is illogical,  because you don't perform all movements at the same velocity, others  utilize the option to operate with different velocities, e.g. the  advantage is I can aim smooth where I can see, since when I don't do a  swift curve, the mouse accepts the in-game sens, so if that is set to  low values, I aim smooth, when I do a quick swing, then accel activates,  allowing me to turn even on low sensitivities as if I had just changed  my sens only for the sake of turning around.

That's fine. However having a mouse that speeds up is still inaccurate compared to one that does not, even if you were quite good at controlling it. I'm also not questioning your skill level.

> mouse doesn't go where it's supposed to? Then you're doing it wrong. You simply cannot handle accel, just admit your own inability!

It doesn't go where it's supposed to because it speeds up and (depending on the setup) adds a curve. I handled mouse accel for years without problem and discovered that after adjusting to no accel it was better. I also did not claim to be a high-level player.

> This topic was opened for a workaround, for  technical help, not listening to trash people enforce on people. If I  cared about someone's opinion on accel, I'd open a separate thread for  it.

I don't think anyone here was trash talking, and you did get some answers regarding the mouse accel situation on CS:S in Linux. Hence I posted the mouse accel opinion after it was clear that there's currently no simple solution. 

> As for those, who are convenient with being a copy of a copy: (using settings just because they work out for someone else) .... In the end, it's not  you. You just adopt something because someone else uses it. But why  doesn't that surprise me in this consumer's world.

Get off your high horse. A mouse movement option means you're copying for the sake of convenience? And I set my settings because *I* use them, not because pros do. In almost all games I have play I maintain an extremely default config so that I don't need to rely on obscure settings. Hopefully you are following your own "independence" logic and using [HJKL]("https://en.wikipedia.org/wiki/Hjkl#HJKL_keys") instead of WASD ;)

> It says how preaching is bad, why don't you learn something from your own signature?

I'm not preaching. I stated an opinion (which I believe to be correct) in one post. Hopefully some future CS players who discover this game through Linux (Steam, etc) will find these posts and be able to decide what they think is best.

Relax. It's a PC game.

Edit: try toggling raw input.
Edit 2: I just went in game and unchecked Raw Input. Mouse acceleration works perfectly fine as long as Raw Input is off. If it does not work for you [please file a bug on Steam's GitHub page]("https://github.com/ValveSoftware/steam-for-linux").

---

### Post by Inoki on 2013-03-03
Yer, next time, when you feel like posting an opinion, don't. No one is interested.

This thread was started to receive technical support. If I wanted to hear someone's opinion I would have asked for it.

I kindly ask a mod to close this thread, as it is no longer needed. A bug report has officialy been filed to VALVe and they are aware.

---

### Post by oldrocker99 on 2013-03-03
I will admit it was a little distressing to see an actual flame war on this forum:icon_frown:.

---

### Post by Inoki on 2013-03-03
> **oldrocker99 said:**
> I will admit it was a little distressing to see an actual flame war on this forum:icon_frown:.
That's because people don't stick to the topic. No one asked them for an opinion, I asked for a technical remedy to the issue, yet they go on with their babble no one cares about.

---

