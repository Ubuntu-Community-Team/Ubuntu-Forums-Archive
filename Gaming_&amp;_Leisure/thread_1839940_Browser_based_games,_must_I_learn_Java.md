---
title: "Browser based games, must I learn Java?"
date: 2011-09-06
forum: Gaming &amp; Leisure
---

### Post by Neoncamouflage on 2011-09-06
I've recently had an interest in browser based games, like all the flash games you see on various sites I'm sure everyone visits when they're bored. Now I've been playing around with game design in Python, but in researching it I've discovered there's really no decent way to use Python alone in creating these games.

Everywhere I read says use Java, but to be honest I spent some time with Java and I hate it. Is there any other good language, possibly like Python, that can be used to create these games? Or am I just SOL without Java?

EDIT: Was also not at all sure whether to place this in this section or the programming one, so I apologize if I picked wrong.

---

### Post by Beacon11 on 2011-09-06
Hahaha, I'm glad I'm not the only one who doesn't get a particularly fuzzy feeling from Java. It just sorta feels dirty. That said, I'd point you towards HTML5/Javascript development.

---

### Post by Neoncamouflage on 2011-09-06
I had always kind of lumped Javascript in with Java, assumed it was just a simpler version of it, after a little research it seems they're two vastly different languages. I may check it out, thanks.

---

### Post by Beacon11 on 2011-09-06
> **Neoncamouflage said:**
> I had always kind of lumped Javascript in with Java, assumed it was just a simpler version of it, after a little research it seems they're two vastly different languages. I may check it out, thanks.

Oh heavens no, they are quite different. That's funny though, I used to lump them together when I was a kid.

Let me know if you've got any questions! I'd direct you to [http://www.chromeexperiments.com/](http://www.chromeexperiments.com/) -- it has some pretty cool Javascript examples.

---

### Post by donkyhotay on 2011-09-07
> **Neoncamouflage said:**
> I had always kind of lumped Javascript in with Java, assumed it was just a simpler version of it, after a little research it seems they're two vastly different languages. I may check it out, thanks.

It's the name, just hearing javascript you (well I at least) think of a watered-down script version of regular java.

---

### Post by DangerOnTheRanger on 2011-09-07
There are *much* better options, IMHO, if you don't care about having your game work on some mobile devices. Namely, [Panda3D]("http://panda3d.org/") - a complete FOSS Python game engine (that's used by Disney and CMU) has a web plugin available for it. Considering just how much more powerful Panda is over flat HTML5 + Javascript (not to mention it lets you use hardware-accelerated 3D graphics in the browser), I think it's the better choice.

---

### Post by Beacon11 on 2011-09-07
> **DangerOnTheRanger said:**
> Considering just how much more powerful Panda is over flat HTML5 + Javascript (not to mention it lets you use hardware-accelerated 3D graphics in the browser), I think it's the better choice.

I don't disagree (I had never heard of Panda3D before now), but you can get hardware acceleration from Javascript too using WebGL: [http://www.chromeexperiments.com/webgl](http://www.chromeexperiments.com/webgl)

---

### Post by DangerOnTheRanger on 2011-09-07
> **Beacon11 said:**
> I don't disagree (I had never heard of Panda3D before now), but you can get hardware acceleration from Javascript too using WebGL: [http://www.chromeexperiments.com/webgl](http://www.chromeexperiments.com/webgl)

Panda's hardware acceleration works even on browsers that don't support WebGL, most notably Firefox <= 3.6 and Internet Explorer.

---

### Post by R33D3M33R on 2011-09-07
I would recommend JavaScript/HTML5. JavaScript is very easy to learn, especially if you are familiar with languages like PHP/Python/etc..

---

### Post by Beacon11 on 2011-09-07
> **DangerOnTheRanger said:**
> Panda's hardware acceleration works even on browsers that don't support WebGL, most notably Firefox <= 3.6 and Internet Explorer.

But Firefox is going to be on version 15 in a couple months!

Panda does look rather interesting though.

---

### Post by Sofox on 2011-09-07
Panda3D looks good and I've followed it for a while, but users need to install a plugin to play it on their browsers which they may not always be inclined to do. Still a good engine and you can of course create standalone games for it. Uses Python too.

For web games development, you've got Java for creating Java applets that run in browsers or on their own (like Minecraft), Flash (more people have this installed than Java), or HTML/CSS/Javascript which doens't need plugins (and so can run on mobile clients) but requires a bit of work to make it run on all platforms.

If you choose Javascript (which I think you already have), I recommend this site for learning how to program with it: [http://www.codecademy.com/](http://www.codecademy.com/)

I'd recommend using HTML/CSS/Javascript to start out wi

---

### Post by TheShadowFog on 2011-09-07
> **Sofox said:**
> I'd recommend using HTML/CSS/Javascript to start out wi

This.

---

### Post by juancarlospaco on 2011-09-07
HTML/CSS/Javascript, you dont need more...

---

### Post by DangerOnTheRanger on 2011-09-07
> **juancarlospaco said:**
> HTML/CSS/Javascript, you dont need more...

Show me something in HTML5 + WebGL that comes close to comparing to any Panda3D game, especially Pirates of the Caribbean Online. Oh, and your example needs to run in Internet Explorer. :p

---

### Post by donkyhotay on 2011-09-07
> **DangerOnTheRanger said:**
> Show me something in HTML5 + WebGL that comes close to comparing to any Panda3D game, especially Pirates of the Caribbean Online. Oh, and your example needs to run in Internet Explorer. :p

Depends entirely though on his skill and what kind of game he wants to create. You use different tools for different jobs. Panda3D is pretty impressive (I've been thinking about using it in a game I've been working on) but that doesn't mean it's perfect for every type of game out there. If he's wanting to create yet another bejeweled or tetris clone or something small I wouldn't recommend using panda3D. Of course if it's something big that needs 3D graphics then it would be a good choice.

---

### Post by IWantFroyo on 2011-09-07
JavaScript and HTML5, as previous comments say.

You could also use Flash ;)

---

### Post by juancarlospaco on 2011-09-08
> **DangerOnTheRanger said:**
> Show me something in HTML5 + WebGL that comes close to comparing to any Panda3D game, especially Pirates of the Caribbean Online. Oh, and your example needs to run in Internet Explorer. :p

Dude, im Python fan, so dont Troll me with Panda, please...

---

### Post by Redstricted on 2011-09-09
Java Applets and JavaScript are definitely superior in any type of browser development for its essential capability in taking the least resources from a computer. There is no must when it comes to learning a programming language due to its challenging complicity by which one must partake motivation, obligation, and inspiration. Learning is a Java great idea, it is worldwide popular, and I highly encourage you to do so.

---

### Post by Beacon11 on 2011-09-09
> **Redstricted said:**
> Java Applets and JavaScript are definitely superior in any type of browser development for its essential capability in taking the least resources from a computer.

You do realize that JavaScript is (usually) client-side? If it wasn't there would be no point in programming any sort of graphics interaction.

---

### Post by Zephilinox on 2011-09-09
I assume your talking about flash games, like the ones at kongregate.com, those are made using action script 2/3 in a flash compiler, you may want to check out stencylworks, I'm not sure but I think it may work in linux as it was made in java, it's very easy to use.

---

### Post by juancarlospaco on 2011-09-10
Say **NO** to:  ActiveX, SilverLight, Flash, Java Applets.
HTML5 all the way, its better, 
if you want overkill power, search info about HTML5 Native Client and WebGL.

---

### Post by lykeion on 2011-09-11
OP asked if he must learn Java to create browser-based games.
I'd say no, but it wouldn't hurt him. It also would'n hurt him to learn JavaScript (HTML5) and ActionScript (Flash). Each platform have its pros and cons. To be a good game developer you need a healthy curiosity in programming as a whole and don't lock yourself in one programming language due to personal dislike of other languages.

Without knowing anything about what kind of game OP have in mind, it's very hard to say what language is best suited for job.

---

### Post by Neoncamouflage on 2011-09-11
Actually I was talking exactly about the ones at kongregate.com. So it sounds like, learn Javascript, HTML5, and ActionScript. And Java doesn't hurt.

Thanks for the help guys, will probably take a good look at all of them.

Also, 100th post. :D

---

### Post by Kodeine on 2011-09-14
Yoyogames is releasing a new version of game maker later this year that allows you to build your game to html5. Probably would work under wine?

---

### Post by TheCompBoy on 2011-09-14
Everyone doesn't like java.. Myself i love it :)

If u want to create this small games easy you can check a language called "Flash" And you need to check out the ActionScript for flash.. Thats the script u need to make the games :)

Hope i helped.

---

### Post by thatguruguy on 2011-09-14
> **juancarlospaco said:**
> Say **NO** to:  ActiveX, SilverLight, Flash, Java Applets.
HTML5 all the way, its better, 
if you want overkill power, search info about HTML5 Native Client and WebGL.

... except that there are a lot of browsers in use (I'm looking at you, IE 8 and earlier) that don't support HTML5 to the extent required for games.

---

### Post by DangerOnTheRanger on 2011-09-15
> **thatguruguy said:**
> ... except that there are a lot of browsers in use (I'm looking at you, IE 8 and earlier) that don't support HTML5 to the extent required for games.

Exactly what I said earlier. IE still doesn't really support HTML5 yet, and since it still has around 45-50% of the browser market, it would be wise to use a technology that IE does support.

---

### Post by Sofox on 2011-09-15
> **DangerOnTheRanger said:**
> Exactly what I said earlier. IE still doesn't really support HTML5 yet, and since it still has around 45-50% of the browser market, it would be wise to use a technology that IE does support.
HTML5 is a very vague term that refers to a whole set of various technologies.
If you're referring to a specific HTML5 features such as HTML5 Video or HTML5 Canvas, then yes, IE8 and less won't support them. However, other aspects of HTML can still be used to make games, and with hacks and tweaks you can make them support older and less advanced browsers.

Also, building on top of a library that does a lot of this browsers adjusting for you, such as jQuery, can also be helpful.

---

### Post by juancarlospaco on 2011-09-15
Thats the point, i code a Web WITHOUT any FallBack, 
i dont want a web with 20 FallBacks for each item...,
i want the users see how Browsers FAIL...

---

### Post by DangerOnTheRanger on 2011-09-15
> **juancarlospaco said:**
> Thats the point, i code a Web WITHOUT any FallBack, 
i dont want a web with 20 FallBacks for each item...,
i want the users see how Browsers FAIL...

And by throwing IE support in the gutter, you needlessly pass on almost 50% of the web browser market. If you use Panda3D, your game will work on IE, Google Chrome/Chromium, and any Mozilla-compatible browser (Firefox, Konqueror, Midori, etc...). Plus, you get automatic shader generation, a large community, the full power of Python (and C++ at your option), and a load of other features HTML5 (WebGL in particular) just cant compare with.

---

### Post by juancarlospaco on 2011-09-16
> **DangerOnTheRanger said:**
> And by throwing IE support in the gutter, you needlessly pass on almost 50% of the web browser market. If you use Panda3D, your game will work on IE, Google Chrome/Chromium, and any Mozilla-compatible browser (Firefox, Konqueror, Midori, etc...). Plus, you get automatic shader generation, a large community, the full power of Python (and C++ at your option), and a load of other features HTML5 (WebGL in particular) just cant compare with.

[No]("http://code.google.com/chrome/chromeframe/")

---

### Post by zulrang on 2011-09-18
And IE still has the kind of market share because developers cater to them.

Do you think people will still use IE when 50% of the websites out there tell them "To use this site, download a real browser (anything but IE)?"

---

### Post by R33D3M33R on 2011-09-18
Old IE versions that don't support standards will drop to zero soon. Newer IE's actually seem to support standards (they must if they want to remain competitive).

---

### Post by juancarlospaco on 2011-09-19
> **R33D3M33R said:**
> Newer IE's actually seem to support standards

Nope

---

### Post by thatguruguy on 2011-09-20
> **zulrang said:**
> And IE still has the kind of market share because developers cater to them.

Do you think people will still use IE when 50% of the websites out there tell them "To use this site, download a real browser (anything but IE)?"

Yes, because IE comes pre-installed.  They (the IE users)  just won't use those websites.  And if they are commercial websites, the websites need customers more than customers need them, and the website owners will figure out a way to make their sites IE compatible.  Which is what's been happening all along.

> **juancarlospaco said:**
> Nope

Link, please.

---

### Post by R33D3M33R on 2011-09-20
> **juancarlospaco said:**
> Nope

Arguments?

IE9 passes Acid3 and supports HTML5 well. Thats enough standards for me...

---

### Post by powersurge360 on 2011-09-24
Hey! I know this thread has gotten kind of old, but I'm suprised to see how many people are recommending Java applets.

Java applets had a heyday in the mid nineties, but has since fallen out of favor. Most users won't have the plugin necessary installed to play them, and some browsers (like Chrome) will warn against it as a security risk.

Java applets are almost certainly not the solution you want.

Panda3D (although I admittedly know very little about it) also requires a third party plugin that I am unsure you would be able to convince the average user to run off and install. I know that I wouldn't unless the game was *extremely* compelling and I'm certainly no average user.

Panda3D is almost certainly not the solution you want. For web clients, at least. Desktop apps look very good.

Flash, too, depends on a plugin but unlike java applets and Panda3d, it has huge market share in browsers today. I forget the actual statistic, but I'm sure a quick google search will pull up the results. Adobe sure loves tooting that horn of theirs :>. I can't say much about flash, other than that it is more or less *designed* for web applications and games.

Unfortunately, it runs poorly on the mobile devices where it is supported, and at all on most non-android devices. Depending on the target audience you are trying to hit, this may not be what you want.

Flash is a very viable platform for your usecase.

The last option you have for browser game development is to use a combination of new and old. It is a very exciting time to be a web developer! There are many, many programming languages you can use to build an application server (PHP, Python, CLisp, Java, C#, the list is staggering), and any of these can handle server interactions. If you use a server that can handle long-standing connections, you can even incorporate a persistent living world that other players can interact with. This is personally what I would choose, but I am admittedly biased because I am a web developer by trade. If you decide that route, be sure to contact me as I am a python developer :>.

In summary, the simplest games can be created with Javascript/HTML5/CSS and server-side technologies. Yes, even as far back as IE6. Unfortunately, DOM selecting can be very slow, so as the complexity increases, performance will decrease. Canvas, the other alternative, is inefficient, poorly supported, and too young a technology to use (although it will be come viable very quickly). I strongly suggest using these technologies if you can at all get away with it.

Flash is the second best option, and the best if you want a game of moderate complexity available on the web. I can't speak of much of this, but you get hardware acceleration, as well as a ton of web features. Unfortunately, flash games are the subject of much derision in the modern web and can't handle very complex games or ones with very sophisticated graphics. This is, in my opinion, the only other option for web game development.

If you find yourself in Java applets or Panda3D, I would seriously reconsider doing it in a browser at all. Unless you find yourself in need of it being in the browser, a native app would likely serve your needs better. The install base for each of these technologies is just far too small.

---

### Post by thatguruguy on 2011-09-24
Wow, that's a lot of words.

The most common suggestions were to learn html5, javascript (which will be necessary for html5 apps) and Flash.  Which are still the best suggestions.

---

### Post by juancarlospaco on 2011-09-25
If you think Adobe Flash is cool, ask a person who uses Screen Readers...

---

### Post by thatguruguy on 2011-09-25
1. I never said flash is "cool." I said it's widely supported, and available to a much larger audience than html5 is right now.

2. How does one use a screen reader with a video game, exactly? I imagine the screen reader saying something like this: "OK, here comes the monster. Now, you're jumping. Now, you're shooting. Aim to the left. I meant my left!"

---

### Post by juancarlospaco on 2011-09-25
I did not say that for you.
They tend to play more calm games like cards, memory, and stuff...

---

### Post by maever on 2011-09-26
Plugins ? pff
We're building an MMORPG based on nothing more then HTML and javascript : [http://www.sagramore.com](http://www.sagramore.com) . I do believe HTML5 is the way to go when it comes to browser games.

---

### Post by juancarlospaco on 2011-09-26
> **maever said:**
> Plugins ? pff
We're building an MMORPG based on nothing more then HTML and javascript : [http://www.sagramore.com](http://www.sagramore.com) . I do believe HTML5 is the way to go when it comes to browser games.

Now...  THATS the way to go!, looks stunning game.

Too bad OpenID its broken ATM?, i try google login and it fails with Open Failed message

---

### Post by thatguruguy on 2011-09-26
> **maever said:**
> Plugins ? pff
We're building an MMORPG based on nothing more then HTML and javascript : [http://www.sagramore.com](http://www.sagramore.com) . I do believe HTML5 is the way to go when it comes to browser games.

Yes, but does it work with a screen reader?

---

### Post by DangerOnTheRanger on 2011-09-27
> **maever said:**
> Plugins ? pff
We're building an MMORPG based on nothing more then HTML and javascript : [http://www.sagramore.com](http://www.sagramore.com) . I do believe HTML5 is the way to go when it comes to browser games.

I beg to differ - I personally don't think your MMO will scale very well, mainly due to varying performance in the different implementations of JavaScript and HTML5, not to mention the fact that neither technology was built to support such an endeavor in the first place. Plus, this still doesn't even come close to rivaling the quality of Panda3D inside a web browser, due to many factors:
[LIST]
[*]Panda is written entirely in C++, so it's naturally much faster than WebGL + JavaScript
[*]Panda uses hardware-accelerated rendering, meaning it can already render even 2D images much faster than any HTML5 web browser
[*]HTML5 and WebGL implementations can vary in terms of performance; Panda's performance doesn't change across web browsers
[/LIST]
True, HTML5 comes bundled with *most* browsers, but IE8 and under don't support it.

---

### Post by juancarlospaco on 2011-09-27
> **DangerOnTheRanger said:**
> 

Panda is written entirely in C++, 

He can use HTML5 Native Client if want even more speed, which uses entirely C++

> **DangerOnTheRanger said:**
> 
Panda uses hardware-accelerated rendering, meaning it can already render even 2D images much faster than any HTML5 

HTML5 got Hardware Accelerated Graphics, 2D and 3D.

> **DangerOnTheRanger said:**
> 
HTML5 and WebGL implementations can vary in terms of performance; Panda's performance doesn't change across web browsers


It depends more on the Hardware on both cases...


> **DangerOnTheRanger said:**
> HTML5 comes bundled with *most* browsers, but IE8 and under don't support it.

You can recommend a Browser and/or chrome frame.

---

### Post by Sofox on 2011-09-27
DangerOnTheRanger, we get you're an advocate of Panda3D, that's fine, we're all advocates of something.

But when you go and critizise someone else's choice in technology when they've when they've already spent a lot of work implementing it, that's crossing a line. That's showing disrespect to the time and effort that they have put into their work, and most of all it's a disrespect to the knowledge and experience they gained in the process.

You can still keep praising Panda3D all you want and if you genuinely think they chose the wrong technology, that's fine; but dammit show respect for the people you talk to and tone down the arrogance because if you don't, it won't do any favours either for you or the causes you support.

---

### Post by DangerOnTheRanger on 2011-09-28
> **Sofox said:**
> DangerOnTheRanger, we get you're an advocate of Panda3D, that's fine, we're all advocates of something.

But when you go and critizise someone else's choice in technology when they've when they've already spent a lot of work implementing it, that's crossing a line. That's showing disrespect to the time and effort that they have put into their work, and most of all it's a disrespect to the knowledge and experience they gained in the process.

You can still keep praising Panda3D all you want and if you genuinely think they chose the wrong technology, that's fine; but dammit show respect for the people you talk to and tone down the arrogance because if you don't, it won't do any favours either for you or the causes you support.

I did not think I was being arrogant; I apologize if I was. But if I think someone chose an inferior technology, I see no problem with stating my thoughts. If someone told me there were better options than the technology I chose, I would ask them why they think their suggestion is a better technology. Who knows, I might be convinced by their argument, and use the technology they suggested. And if I did, I would be grateful towards them, not bitter, since they took the time to tell me about something that I previously had not known of/considered, and made my project better in the process.

I never said maever's MMO was gutter trash; I merely stated I did not think the MMO would scale very well, and if I am/was wrong, then I will be the first to admit it.

My opinion on HTML5, stated as respectfully as possible, is: It is fine for making 2D games, and low-quality/simple 3D games. But if you want to take a commercial-quality game (with, say, physics and shaders) and put it inside a web browser (like QuakeLive), then Panda looks like the best choice.

---

### Post by ferrarirs on 2011-09-29
I like Tetris which is based on Java. You can learn other languages like php,html..

---

### Post by lykeion on 2011-10-03
I find this thread an interesting read even though OP seems to have got his question answered weeks ago. Thread contributors like DangerOnTheRanger, juancarlospaco, thatguruguy and powersurge360 all have posted valid opinions I think. I may not agree with them but the discussion of selecting the right tool/language to get the job done is an interesting one. As a developer I encounter it quite frequently and of course the choice will depend on what kind of project it is and what the goals are with it. For a personal project I'd say use a language that you like and don't bother with scaleability or 100% browser compatibility.

---

