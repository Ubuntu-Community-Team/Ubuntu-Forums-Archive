---
title: "Public servers doubt"
date: 2009-02-10
forum: Gaming &amp; Leisure
---

### Post by Xhip on 2009-02-10
Hello!

I have a doubt about the typical list of public servers that appear on the multiplayer games...

This is a general doubt, that applies to all kind of multiplayer games, but I will use a specific game to launch the doubt: OpenArena

Like we all know, on the multiplayer screen, these kind of games show us a list of servers we can join to on the Internet. My first question is: are these only dedicated servers? For a game to appear on this list, it requires the server to be dedicated?

I have this doubt because typically I only set up a server to run on my LAN, only for the people on my LAN to join it, and I always ask myself if this server that is only created to run on the LAN, if it will appear on the multiplayer server list...

On OpenArena, I don't see any option to declare the server to be public or not, I only have an option to specify if the server is dedicated or not. And I must choose No, LAN or Internet in that option. I always choose No, and all works ok on my LAN, but I don't know if the server will appear on the public list or not, obviously I don't want it to appear there. I don't see it there before joining the LAN game (by specifying the IP), but I don't know if the server will appear during gameplay....

Can someone give me some lights about this theme?

Thanks and regards!

---

### Post by Polygon on 2009-02-10
your server usually wont show up on the internet unless its dedicated from my experience with multiplayer games.

---

### Post by Xhip on 2009-02-10
Thank you for the answer :)

So, it is a general thing? By other words, only dedicated Internet servers appear on the server list, is that valid for all the multiplayer games? You used "usually", that's why I'm asking :)...

---

### Post by Irritant on 2009-02-11
I'm not sure I get the question.  You have doubt about servers?  What kind of doubt?  

I *think* the answer your looking for is this:

LAN means it is not public.
Internet means it is public.

Not all multiplayer games work this way, and some give different options that specifically say if it is public or not.  Non-dedicated public servers are generally referred to as "listen" servers.  An example of these would be UT2k4, Doom III, or Quake 4, where you start up a game to play, and unless you specify it to be lan only, people can and will start joining in your game.

---

### Post by Xhip on 2009-02-11
Obviously I know that LAN is not public! The question is that there isn't an option to specifically say that the server is going only to be local, so I never know if it will appear in the public list... Only stuff that I choose is selecting the type of server as 'No dedicated' in the game creation options...

As I said, the only option I have is choosing if the server is dedicated or not. I have 3 options: "No", "LAN" and "Internet". I select "No". So, only thing I know is that the server will not be dedicated, but I still don't know if it will appear in the public list of servers (even during gameplay), because there is not an option to choose if it will be public or not, or if it will be local only or not; only option I have is the dedicated stuff I mentioned, but by choosing "No" that doesn't mean the game will be local only.

So, a doubt appears: I don't know if the game will be public or not.... So, I asked the main question in the 1st post: for a game to appear on the public list, it requires the server to be dedicated? By other words, that public list are only the dedicated servers? If the answer is yes, then I know that my game will not appear, because I always choose "not dedicated", like I said above. But I don't know if the list are only dedicated servers, that's why I'm asking about it :) A question that can indirectly solve my doubt about my server appearing or not on the public list...

By the way:
> **Polygon said:**
> your server usually wont show up on the internet unless its dedicated

> **Irritant said:**
> Non-dedicated public servers are generally referred to as "listen" servers

So, obviously, 2 different views, who is right?

---

### Post by Xhip on 2009-02-11
Bump..

---

### Post by Ozor Mox on 2009-02-12
This depends on the implementation in the particular game you are playing. There is no set rule. In my experience though, most games will **not** make a server public unless you specify it either with a checkbox in the setup screen, or a command line option telling it to report to a metaserver. In fact, if I remember correctly, the only game I've ever played which makes a locally hosted server public by default is AssaultCube. I soon found this out though when randoms started joining my game!

Also, I don't think a server being called 'dedicated' necessarily equates to it being public. For example, the Nexuiz server executable is named something like 'nexuiz-linux-686-dedicated', but it will run privately unless told to report to the metaserver.

---

### Post by Xhip on 2009-02-12
Yup, I see your point. The question is that the game lacks options to make it visible or not. Is there a general way to see if a general multiplayer game will appear in the public list?

I know that, for others to join an hosted game, you have to open a given port on the host. Even if my game appears on the public list, I know that others will not join, because I only open that port to my local IPs, on my LAN. But even with that, obviously I don't want it to be public... I don't know if, by not opening that port, if the game will appear or not......

This is a very strange situation, I thought that every multiplayer game would had an option to make it visible or not on the Internet, but I see it's not the case. So, it's a more or less random possibility (the game being public), right? Or is there a way to confirm that, for a general game?

---

### Post by donkyhotay on 2009-02-12
> **Xhip said:**
> This is a very strange situation, I thought that every multiplayer game would had an option to make it visible or not on the Internet, but I see it's not the case. So, it's a more or less random possibility (the game being public), right? Or is there a way to confirm that, for a general game?

It's dependent on how the developer coded the game. If they don't code a distinction between public and private games or a way to choose during game creation then it doesn't exist. At that point you have the option of either modifying the code yourself, asking someome else to do it for you, or making certain you IP ports are closed. I've played some games that don't make the difference between LAN/internet but these are games that usually don't announce themselves so you have to give the IP address to your friends that are going to connect anyways. Then you just tweak your firewall to confirm no one else connects but this is unlikely unless they know your IP and that the game is running.

---

### Post by Xhip on 2009-02-12
> **donkyhotay said:**
> but these are games that usually don't announce themselves so you have to give the IP address to your friends that are going to connect anyways. 

Yeah, that's the case on my local LAN. Usually I set up my computer as the host, and, on the other computers (on the LAN) that will join, they don't see my game even on the LAN tab of the in-game browser... So they connect directly by typing my IP... This is very strange too, I don't know if it is some kind of delay between game creation and game announcement on the in-game LAN browser... I'm just very confused about this stuff lol, and it's not just about OpenArena, there are other games that suffer from that lack of public options set...

---

### Post by donkyhotay on 2009-02-12
Sometimes thats just the way things are with games. There was an open source gaming project I was working on a few months ago that worked this way. It didn't announce itself so connecting required typing in an address to connect whether LAN or internet. Course this is because I'm lazy and it's easier for me to type in IP addresses then to code network announcements.

---

### Post by Xhip on 2009-02-12
Yup. Another strange thing is the game having a LAN tab in the in-game browser and the LAN game that I create not appearing there. So, I thought that the tab was only to dedicated LAN servers, as I set my own server to not be dedicated... So, I expanded that idea to the Internet tab, or public list: only dedicated Internet servers should appear there. But I see that this is not true at all....

---

### Post by Polygon on 2009-02-12
Ok, you said you had two different views, but both are right

Ill just use the source engine as an example. If you have ever played half life, half life 2, etc, the way the engine works is a client / server model, even in single player games. the client and the server take care of different things, but even in single player games, your computer runs both the server and the client at the same time

On multiplayer games, things are a bit different. Yes its still a client / server model, but instead of running both the client and the server, you just run the client which connects to a server which is far away in some place.

in the first example, those kinds of servers are called 'listen' servers, im guessing its called that because it only listens to commands, it doesn't actually advertise itself on the master server list. Usually listen servers have 1/2 slots (at least in source games) and are not meant for real online games because one: the computer might not be powerful enough and 2: the internet connection might not be fast enough. Most listen servers do advertise themselves on a LAN though, and most games have some sort of feature to show servers on a LAN

However, dedicated servers are JUST servers, usually computers running a dedicated server do not run the client, just the server executable, hence the name 'dedicated'. They are usually on faster computers and on a good internet connection, and these actually send their IP out to the master server list that players download and look through when they want to find a game to play online.

So no, by default listen servers should not show up on the public server list. To do this in source engine games, you have to start up the listen server, set sv_lan to 0 (false) and then run 'heartbeat' a couple of times (to get your listen server to announce itself to the master serverlist and what not).

---

### Post by Xhip on 2009-02-12
Ok, I know all that about dedicated and listen servers, I know what they are and what they do, my doubt was only if they would make a public appearance or not... :)

So, you're saying that dedicated servers "actually send their IP out to the master server list", but Ozor Mox doesn't think that a "server being called 'dedicated' necessarily equates to it being public". So, this results in more confusion for me........ thats my main question/doubt. Dedicated results in public appearance or not? Where do we stay? 

For the listen servers..... ok, so, it can be public or not, but it's not public by default, correct? So, by selecting dedicated option to "No" in my game, I make my server as a listen server, so, no appearance on public correct? And that's why it doesn't also appear on the clients in-game LAN browser correct? Only access by direct IP is possible correct?

---

### Post by Polygon on 2009-02-13
that depends on the game. in source engine games a dedicated server will automatically announce itself to the master server list, you would have to tell us what game your considering.

but you can always make a dedicated server then set it to lan only, most games have a command for that (in source its sv_lan 1)

---

### Post by Irritant on 2009-02-13
> **Xhip said:**
> For the listen servers..... ok, so, it can be public or not, but it's not public by default, correct? 

That depends on the game.  In UT, Quake 4, Doom III, listen servers are indeed public by default.

---

### Post by Xhip on 2009-02-13
> **Polygon said:**
> that depends on the game
> **Irritant said:**
> That depends on the game

Humm... ok, so, anyone knows how things work on these ones: Warzone2100 and OpenArena, anyone knows if they set public appearance on by default on listen servers? On FreeCol I don't have that problem, since it's a rare case of a game that has a "Public Server" option directly on the multiplayer screen...

---

### Post by Xhip on 2009-02-15
Bump..

---

### Post by Polygon on 2009-02-17
the best thing to do is ask on each games respective forum....although even if the server IS public, i doubt anyone will join cause the ping will be terrible and  it will be like a 2 slot server with 1 player =)

and anyway, if its open arena, its a quake-based engine game so i would say maybe public by default since thats what someone said earlier in this thread?

---

### Post by Xhip on 2009-02-17
> **Polygon said:**
> although even if the server IS public, i doubt anyone will join

I know that nobody will join because, like I said, I only open the required port (on my computer) to my LAN partners, and I'm behind a router with ports closed. Problem is that I'm not confortable with my game being all the way public, when the only target is the LAN area... 

It's curious because this last days I tested several other multiplayer games, and almost all of them have the option to make the (listen) server visible on the Internet or not. And that should be available on all games, but it seems that only the ones I'm interested in playing are lacking the option :( 

One option I tested was creating the server (on my computer) and then using one of the other computers on the LAN to see if the game appears on the public list, and it doesn't.... But I'm not sure if the game doesn't appear because of some kind of delay between the time of the creation and the time when it would eventually appear public, or if the other LAN computers can't see the game public because they are on the LAN...

Like I said, to join my game, they always use the method of specifying directly my IP...

---

