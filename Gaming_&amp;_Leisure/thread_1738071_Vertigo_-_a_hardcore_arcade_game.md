---
title: "Vertigo - a hardcore arcade game"
date: 2011-04-24
forum: Gaming &amp; Leisure
---

### Post by amireh on 2011-04-24
Hi guys! I'm not sure if my project is worthy of posting here, but it's the first game I ever release and I'm very excited about it :P

Vertigo is an arcade game that is completely free, open-source and cross-platform. I built it using Ogre3D and BulletPhysics.

For Linux, I tested on the following distros: Ubuntu 10.04, 10.10 and Debian Lenny.

[SIZE=4]**The gameplay in a nutshell**[/SIZE]
You are a probe which is set with 2 shields to protect from fire and ice drones, but only 1 shield is active at a time. You will engage zones, each of which might have a different game mode and different objectives, and you'll be briefed once you're in. You have to flip shields in time to protect yourself, and you can possibly move left and right to avoid some obstacles. It's a pure reflex game, a brain teaser :D

[SIZE=4]**Gameplay trailer**[/SIZE]
The trailer shows all 4 game modes and 3 of the camera modes: [http://youtu.be/6x6BfZNGabc?hd=1](http://youtu.be/6x6BfZNGabc?hd=1)

[SIZE=4]**Screenies**[/SIZE]
You can see different states of the game in a couple of the zones below.
[[IMG]http://vertigo-game.com/images/screenies/latest/640/dante_afterlife.jpg[/IMG]]("http://vertigo-game.com/images/screenies/latest/original/dante_afterlife.jpg")
[URL="http://vertigo-game.com/images/screenies/latest/original/Screenshot_1303045386.png"]
[IMG]http://vertigo-game.com/images/screenies/latest/640/Screenshot_1303045386.png[/IMG][/URL]
[URL="http://vertigo-game.com/images/screenies/latest/original/Screenshot_1303045482.png"]
[IMG]http://vertigo-game.com/images/screenies/latest/640/Screenshot_1303045482.png[/IMG][/URL]
[URL="http://vertigo-game.com/images/screenies/latest/original/hysteria.jpg"]
[IMG]http://vertigo-game.com/images/screenies/latest/640/hysteria.jpg[/IMG][/URL]

[SIZE=4]**Links**[/SIZE]
Try it out! You can find everything at [www.vertigo-game.com]("http://www.vertigo-game.com").

I hope you find it fun, and I'd love to hear any kind of feedback!

---

### Post by amireh on 2011-04-25
Hi,

Vertigo source is now available on GitHub @ [https://github.com/amireh/Vertigo](https://github.com/amireh/Vertigo)

Feel free to join in with any code review, comments, or flames.! You can find me on IRC @ irc.freenode.org#vertigo - I'm known as kandie

Cheers,
amireh

---

### Post by oldos2er on 2011-04-25
Thanks! I haven't tried it yet, but it looks like fun.

---

### Post by ubuntu27 on 2011-04-25
Thank you amireh! I will keep an aye on this game. :D

---

### Post by amireh on 2011-04-27
Hi guys,

I'd like to announce that a blog for Vertigo's updates and news has been launched. You can find it at: [http://blog.vertigo-game.com](http://blog.vertigo-game.com) stay tuned for updates! It provides RSS feeds as well.

Cheers,
amireh

---

### Post by Giraffemonster on 2011-04-27
Good to hear about the blog.:)

How many people are working on this project? Is it just you?

---

### Post by thenickrulz on 2011-04-27
This looks awesome!

---

### Post by amireh on 2011-04-28
> **Giraffemonster said:**
> Good to hear about the blog.:)

How many people are working on this project? Is it just you?

Yes it's just me, a friend helped me with the music though. ^^ None of the assets are my work though, besides of the game's logo. It's powered by free/open-source resources all the way.

It's meant to be a small game that you'd play in a break. I have some enhancements in mind but right now I'm focused on making the game packagable for Debian / Arch repositories.

> This looks awesome!

Thank you! :D

---

### Post by Syotos on 2011-04-28
I think this will be the first game I will put my hands on right when Ubuntu is done installing !

---

### Post by rizzeh on 2011-04-30
> **amireh said:**
> .... I'm focused on making the game packagable for Debian / Arch repositories....


thanks you, can't wait for *.deb :)

---

### Post by Capsad on 2011-04-30
Can't wait for the arch package :) Just saw the game on freegamer.blogspot and immediately searchead for it in the AUR, but unfortunately I have to wait a little bit longer ;)
Greetings,
 capsad

---

### Post by amireh on 2011-04-30
Hi guys,

I'm sad to announce that the game won't make the official repositories anytime soon. Turns out it needs almost a 50% rewrite for it to be compatible and right now I don't have the time. However, I have 2 ideas that *should* work for Arch users:

[LIST=1]
[*]I can supply you with a statically linked version of the game, then there's a good chance it runs without modifying anything, but in case that still doesn't work..
[*]I'll guide you through building it from source: the only "proprietary" library being used is the ParticleUniverse one and I already supply that in the main .tar.gz package, so you can use it in linking.
[/LIST]
Building from source shouldn't be much trouble but it certainly isn't my recommendation, I really tried to provide alternative, smoother deployment methods but since I'm a noob and didn't know what it takes to get the package into the official repositories, there's little I can do now.

Please let me know which method you prefer. I will create the static package right now and update this post once it's uploaded.

Cheers,
amireh

---

