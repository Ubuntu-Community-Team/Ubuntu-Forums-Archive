---
title: "Game Developers and Game Artists, I need your input"
date: 2007-09-18
forum: Gaming &amp; Leisure
---

### Post by curvedinfinity on 2007-09-18
[IMG]http://www.mirthkit.com/MirthKitBig.png[/IMG]

MirthKit is a no-cost closed-source commercial application strongly influenced by open source ideals. It is essentially a cross between Adobe Flash and XBOX Live Arcade. Its programming interface has everything a 2D game developer needs, and a lot of thought has been put into making it as simple as possible. Games made with MirthKit run on Windows, Linux, and Mac OSX. Plans have been made to bring it to other platforms, such as PSP, DS, and XBOX Live Arcade.

The distribution of MirthKit that most people will download comes with an application made on top of MirthKit called "MirthKit Arcade." MirthKit Arcade is a lot like XBOX Live Arcade; a user can demo games and even buy them with a credit card. Developers who make games with MirthKit have the option of selling them on MirthKit Arcade. Developers can also opt to release their games for free on MirthKit Arcade.

(Please keep in mind that the standard edition of MirthKit with MirthKit Arcade has not been released yet)

Games made for profit will have a small royalty included in their MSRP (about 15% -- meaning devs get about 85% of MSRP). So to reiterate that, it costs nothing to develop and publish with MirthKit, whether the game is for profit or not. Curved Infinity Games sustains itself as indirectly and morally as possible.

A license requirement for games made with MirthKit is that their source be freely available to those who have bought the game (or in the case the game is free, to everyone). Furthermore, users are encouraged to modify games and have the modifications be redistributed through MirthKit Arcade.

[IMG]http://www.mirthkit.com/arcade/FinityFlight/screenshot.png[/IMG]

So, thats a long description, but there is so much more information available on the website...

[http://www.mirthkit.com]("http://www.mirthkit.com")
[http://dev.mirthkit.com]("http://dev.mirthkit.com")

Make sure to visit the [overview]("http://dev.mirthkit.com/index.php?title=MirthKit_Overview") and the [feature list]("http://dev.mirthkit.com/index.php?title=MirthKit%27s_Features").

The website is currently in very active development. For the moment, I'm the only person developing, documenting, and webmastering MirthKit -- and I have a full time job on top of that, so keep that in mind.

My number one goal with MirthKit is to allow game developers to make stable small businesses. I love games, and I am trying to make a way for people to make a living out of their creativity.

I know the topic of morality of software commerce is important to the Ubuntu community... its important to me. My belief is that software IP has no value, but instead the amount and skill of the work that it took to make the software is what has value. So in that sense, MirthKit places little emphasis on protecting games, and instead places a lot of emphasis on creating games.

**What I'm looking for is developers to start making games with MirthKit and give input so MirthKit can be made better as it moves into later stages of development. -- Its currently a beta quality release; it works very well, and needs to be thoroughly tested and revised.**

Already, one development team of four is signed on to make a platformer called Shadow Dash. Additionally, several individuals have expressed interest, and I am personally developing a full-featured shooter called Finity Flight (an early version of which is actually featured as the demo in the DE release).

So, if you are interested, please say something here. If you feel that you aren't capable of making a game by yourself, but you would like to help make one, I can help you find a group to work with.

I can't wait to hear back,

Chase Adams
Curved Infinity Games

---

### Post by Steveway on 2007-09-18
Sounds interesting but:
Screenshots? Examples? Is it closed or open-source?

---

### Post by curvedinfinity on 2007-09-18
My how eye-candy is so necessary, hehe... I have edited the post to answer your questions.

Also, please note that the main website has a download for an example game on the front page. Some simple example apps are in the API reference on the same website -- just click on each function for an example.

[http://www.mirthkit.com]("http://www.mirthkit.com")

---

### Post by Dylnuge on 2007-09-18
I like the idea (I won't be personally using it). My only complaint is the license-no, I am not asking for it to be open-source or non commerical or anything, but I think that maybe a flat fee and a required credit would be better then a royalty charge, since these will be small games, and 15% won't be much at the prices one could reasonably expect to sell the game with.

---

### Post by curvedinfinity on 2007-09-19
Oh, I think you misunderstand ... developers get 85% of MSRP, CIG gets 15%. So, for a $12 game, developers make $10. -- That means a solo developer could live well off of 200 sales per month (depending heavily on cost of living), which isn't a huge goal by any means.

That 15% goes into credit card processing (which has the largest cut), developing MirthKit, marketing help, and donations toward open source projects.

---

### Post by ZylGadis on 2007-09-19
Just to make sure I understand correctly, mirthkit:

- is closed source / proprietary
- requires that products made with it are open source

Is that correct?

---

### Post by Tomosaur on 2007-09-19
May I just ask what the rationale is behind keeping Mirthkit closed source? If the only way you're ensuring payment is by good will (people bothering to take notice of your licence and pay you royalties), then I don't see the benefit of keeping Mirthkit closed - particularly when having it open-sourced could have benefits.

I'm not criticising your decision to keep it closed, I just can't see how keeping it closed has any benefit :S

---

### Post by curvedinfinity on 2007-09-20
I'm happy to answer your questions!

Yes, it is closed source, and yes, games made with it are required to be "open source". -- I put quotes on open source, because that normally implies that they would be completely free, which they are not. This is a very odd arrangement, but it has many purposes...

There are two good reasons for games being required to have source available (this is a better description than open source):
[LIST]
[*]Developers may learn from released games
[*]Players are free to make very extensive mods to existing games, provided the mods are distributed only to other owners of the original game
[/LIST]

I feel those freedoms will create an exciting atmosphere in the MirthKit developer community. If a developer creates a new technique, the rest of the community will be able to learn from his example. Additionally, because competition for technical advancement will be high, it would be beneficial for developers to focus on gameplay, which is more subjectively defined than say a graphics technique -- and therefor harder to duplicate.

So, why, if I am saying I am such a big open source fan and all, is MirthKit a closed source application?

First, morally speaking, MirthKit is provided at no cost. Sure, for commercial games I'll take a little cut, but it is a very small precentage (about a third of that 15% goes straight to the credit card company), and above all, you have the option of making the game for free, in which case, money is never involved.

Secondly, many developers outside of the open source community simply wouldn't use MirthKit if it was trivial to pirate games. I personally don't care so much about pirating, but a lot of developers do. The only way games can be open source, yet not be easy to pirate, is if there are measures in the source of the MirthKit binary, which there are. That said, the measures are very simple...

[LIST]
[*]The distribution of MirthKit most people get is HTTP-locked to trusted domains -- people can't open code on their local machine, or on any website that isn't a partner of some kind (like mirthkit.com or an open source project or a developer)
[*]The developer version of MirthKit can read code on the local machine and on any website, but each copy of the dev version is numbered, and it is possible to lock-out a copy that has been mass-distributed.
[/LIST]

So all that said, if you are a developer and you have access to the source of one of the games, it will be easy for you to play it without purchasing it. However, for most users, the process involved will be too complex and unpractical to warrant caring.

So, I hope this answers your questions, but if it doesn't, please keep asking away. :)

---

### Post by Marsan on 2007-09-20
Hey curvedinfinity. I would just say how much i loved your previous games in the  Finity Flight series. I dont know alot about programing and developing of games, but i will be looking forward to another game-release from you.

---

### Post by Perfect Storm on 2007-09-20
> **Marsan said:**
> Hey curvedinfinity. I would just say how much i loved your previous games in the  Finity Flight series. I dont know alot about programing and developing of games, but i will be looking forward to another game-release from you.

I'll second that!!!

Good work! :KS

---

### Post by curvedinfinity on 2007-09-20
Its good to see you both again! :) If you kept track of ff2.curvedinfinity.com, this is the next "thing" promised in my final post. My first game for MirthKit will be very very similar to those games you liked. However, I hope to make it much higher quality, with more gameplay, and an arcade format and pace.

---

### Post by curvedinfinity on 2007-09-20
Hey AI, I don't suppose you could help me get a little bit more exposure? :)

---

### Post by Dylnuge on 2007-09-20
Yeah, I misunderstood with the 15%, sorry.

Like the idea, but I agree that you could make some more from going open source-most people don't donate to closed source, and most indie game developers don't sell a ton of $12 games.

And open source does not, nor has it ever, been synonymous with free. All it means is that you release the source code with the software. GPL-compatible open source is similar, it means the source code must be publicly available and the users must be able to distribute the software. So the way you want developers to release their games is still open-source, it just is not necessarily compatible with GPL.

---

### Post by Perfect Storm on 2007-09-20
> **curvedinfinity said:**
> Hey AI, I don't suppose you could help me get a little bit more exposure? :)

Not at all. Just PM me when you want some news on the frontpage.

---

### Post by ZylGadis on 2007-09-20
The closed/open decision you have made is extremely controversial, and in my opinion you are not likely to attract any developers with IQ>average for the following reasons:

There are basically two types of value systems as far as Software Freedom is concerned. Your model alienates both types (for different reasons), and any person with the mental capacity to see that will not look at your kit twice.

- First, there is the camp of Free Software developers. You alienate them immediately because your kit is closed source and, what is more, it locks them in your business model / web site / platform / whatever, because it calls home, and on top of that they must distribute their product through your platform only. Essentially, Mirthkit fails every single one of the Debian tests for Software Freedom.

- Second, there is the camp of proprietary / commercial developers. Those people believe in money, hiding information, etc. They will accept both the 15% cut and the vendor lock-in as something natural, but you alienate them immediately because you force them to open their product. To add insult to injury, you do not even open your part. If they call the GPL a virus, imagine what they will call Mirthkit.

Note that all of the above has been purely objective reasoning - I have not added any implications of my personal value system. This is the personal part: I believe I understand your reasoning, and I will tell you that you need to attract clever people, if you want to succeed, and clever people by definition will see through your vaporware reasons for closing/opening immediately. It is difficult for me to imagine how a competent developer such as yourself could come up with such a ridiculous licensing scheme - this is contrary to every single one of the different paths for success that exist in the field. Pick one or the other (or come up with a third), but don't go against all of them simultaneously - that is just stupid.

---

### Post by Mblackwell on 2007-09-20
You could always relicense under LGPL and close the portions of the source that relate to authentication.

---

### Post by curvedinfinity on 2007-09-21
> **ZylGadis said:**
> ... Pick one or the other (or come up with a third), but don't go against all of them simultaneously - that is just stupid.

I agree that MirthKit is very controversial, and I agree that I will have to fight hard to get smart people to use it. I think you have very valuable insight, and perhaps you could suggest some alternatives to what I have currently?

Until something better is found, MirthKit has to remain closed-source so those who want security have security.

As an aside, it isn't necessary for me to convince everyone right now. MirthKit only needs a hand full of users for the moment to test and give feedback. I think in time and only in time, people's concerns (like your own) can be quelled by successful projects and happy developers. -- I think people will grow to trust me once they see my track record, and they see the effort I put forth for those that want it. -- I've made open source games in the past, and explored other commercial models that are compatible with open-source philosophies. This particular model I think is much more open-source friendly than you make it out to be.

In terms of the irony that games made with MirthKit are open source and MirthKit itself is not, does the same relationship not exist with open-source games written for Windows? The fundamental difference is that MirthKit makes it possible for even commercial developers to give source-access to their users.

I think that MirthKit, with its very middle-of-the-road placement can even eventually break the camp lines -- you can't argue that it isn't at least *decent* in terms of both philosophies. -- In the end, users still have as much freedom as with a pure open source game, while developers can easily subsist and learn. -- In the end, the most important results of both ideals are met, and differences are only found behind the scenes.

Because they are applicable, here are some guarantees listed on the developer wiki overview:
[LIST]
[*] You will never have to pay anything to develop and publish with MirthKit
[*] Windows, Ubuntu, and Mac are supported and always will be supported
[*] In the future, more platforms will be supported, starting with hand-held consoles
[*] Curved Infinity Game's proceeds will in portion go toward funding open source projects 
[/LIST]

EDIT: I just realized I need to add the following guarantee: "You will always own your game, though you will have to agree to some terms to publish it"

And once again, I'd like to make a call for developers to come and help. I've always come to the OSS community first because I'd like their blessing the most. -- So, please come try MirthKit and tell me what you think. :)

Thanks,
Chase

---

### Post by curvedinfinity on 2007-09-21
> **Mblackwell said:**
> You could always relicense under LGPL and close the portions of the source that relate to authentication.

Hehe ... Its funny you say this. I wrote the underlying library for MirthKit sometime ago. Its called CIG-A, and it is provided under the LGPL. You can find the C++ source [here]("http://storage.curvedinfinity.com/games/ciga/libcig-a-1-2.tar.gz"). It isn't actually a whole lot of code and is mainly just some major simplifications to SDL and OpenGL -- it is especially great for beginners of graphics programming. I made [Finity Flight 2]("http://ff2.curvedinfinity.com") using this library, which is also released under the GPL.

---

