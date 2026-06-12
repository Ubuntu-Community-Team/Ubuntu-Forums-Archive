---
title: "Glest on LAN"
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by gagadude on 2008-03-02
I got glest up and running (yay me) but I want to play on LAN with my little brother.
I got into "create game" and i open up a network slot and it says "network not connected" or something to the likes of that. Whats happening and how do I fix it?

---

### Post by Belliinator on 2008-03-02
Sorry mate, but unfotunately on these forums you gotta be more specific, if you want to solve your problem. Im no expert, and I don't play glest, but I'll try to help you. (sorry if you think im telling you off, you just have to remember that we could be half way round the world.;))

Firstly how are your computers connected? Like thru a router or something? Crossover cable?

How is your network configured? DHCP, fixed IP, IPv 4ll?
(I assume your both on linux.)

Have you been able to connect to each other at any other time, any other game?

Have you googled it? Im doing that right now

Have you checked: [http://www.glest.org/glest_board/viewforum.php?f=12&sid=2d86f7078e54df1cdd71522b503661fe](http://www.glest.org/glest_board/viewforum.php?f=12&sid=2d86f7078e54df1cdd71522b503661fe)
The glest forums for someone with the same problem? There is a whole multiplayer section there.

Good luck. From my experience there is little more dissapointing the not being able to play a good RTS with your brother.

---

### Post by gagadude on 2008-03-02
Im connected thru a router

I've checked google & the glest forums

I'm not sure how my network is configured

My brother and I can connect to each other on "Nexuiz"

---

### Post by Belliinator on 2008-03-03
> **gagadude said:**
> Im connected thru a router...

I'm not sure how my network is configured


Your probably running DHCP then. 

To check go to 
system -> administration -> Network. You should see "wired connection" in the big white box. Click "wired connection" then the properties button that lights up.

Whats next to configuration? But you probably wont need to change anything. If worse comes to worse run it on a static ip and then see what happens.If your router connects to the internet, we  may need to use DNS addresses but im not so sure about that.

> 
My brother and I can connect to each other on "Nexuiz"Oh no, that means its probably not a simple issue. Well at least one game works!

When you downloaded Glest did you download all the packages? There might be a mulitplayer package that you need to download seperately. Did you get it via synaptic? If so whats the package called (coz I can't find it :-?.)  I know other games for linux need more addon packges for multiplayer.

Sorry man, I really want to help, but im not sure what to do. If your not sick of it yet keep posting and Ill try to help you, too many times the same thing has happened to me when I tried to play Empire Earth (windows) with my brothers. Theres gotta be some reason.

---

### Post by Sammi on 2008-03-03
If you can connect in other games, then your network is fine. The problem is most likely with Glest. 

But I don't know much about Glest either...

---

### Post by gagadude on 2008-03-04
There's no package I need to download for multipayer (from what Google can tell me). I checked the configuration of my network and it has a small box checked off in the corner that says "enable roaming mode" when this box in checked all the fields (Configuration, IP address, subnet mask, gateway address) are grayed out(although, does that still matter?). 

I appreciate your enthusiasm!

---

### Post by Robin T Cox on 2008-03-04
Try the Glest multiplayer forum:

[http://www.glest.org/glest_board/viewforum.php?f=12&sid=2d153e0381e3cee9dd1c92d27a1a189e]("http://www.glest.org/glest_board/viewforum.php?f=12&sid=2d153e0381e3cee9dd1c92d27a1a189e")
or
[http://tinyurl.com/ysrv9n]("http://tinyurl.com/ysrv9n")

---

### Post by Belliinator on 2008-03-05
No, don't do roaming mode if it doesn't help, I think it just resets everything.

Can you tell me what the original package was named in synaptic? I might download it and play around with the multiplayer settings and see if I can get it to work. This is probably the most I can offer at the moment, but Ill keep my eyes open. You thanked me for one of my posts before, no I want make sure that it was worthwhile.

Did you try running through a static Ip on both computers? (I really don't know if this will change much)

Did you have the network enabled? To check just go to that icon with two monitors at the top of your screen, right click and a drop down menu will appear with 'enable networkling', If theres a tick next to it your on.

Yeah I know that sounds stupid, but for some reason you could have accidentally turned it off!( Im just checking that its not something totally obvious thats causing the trouble, because it happens to me a lot.)

Keep trying.

---

### Post by sjdenton on 2008-03-12
So...You on computer 'A' start a server in Glest by selecting Network under Player 1 - Control. At this point it should report 'Not Connected'.
Then on computer 'B' start glest and select 'Join Game' and enter the IP address of Computer 'A' and click connect. If your network is ok both Computer 'A' and 'B' will report that they are connected to each other! On Computer 'A' select 'Play Now'...and off you go.

When I went through this process with Glest 3.1.0 it did not work first time. The join game button did nothing. I had to create a blank file called servers.ini within your /home/'username'/.glest directory on computer 'B', before the Join Game button worked.:-\":

---

