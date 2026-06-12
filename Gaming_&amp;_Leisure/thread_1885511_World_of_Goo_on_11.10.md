---
title: "World of Goo on 11.10"
date: 2011-11-23
forum: Gaming &amp; Leisure
---

### Post by cannon_dt on 2011-11-23
Hello all !
I did a force architecture on the .deb install that I got on my recent x86_63 install of Ubuntu 11.10.

The installation went fine but when I try to launch it I get nothing - no errors whatsoever? Is there anyway to get it working?

Thanks,
Ananth

---

### Post by thatguruguy on 2011-11-23
I'm trying to understand the following:

> **cannon_dt said:**
> I did a force architecture on the .deb install that I got on my recent x86_63 install of Ubuntu 11.10.

Where did you get your version of World of Goo?  It runs just fine on my 64-bit 11.10, and I don't remember doing a "force install" of any kind.

---

### Post by cannon_dt on 2011-11-23
I got the .deb initially when I had my ubuntu 9 and I used the same. I got it from the official download site (not a torrent or something, if that is what you are referring to).

I installed it on my earlier machine which was not x86_64, it was i686. Now I got a new desktop which is x86_64. When I double clicked the deb, the message I got was "Wrong architecture". So I did a sudo dpkg -i --force architecture to install the deb file.

Did I do wrong?

Ananth

---

### Post by R33D3M33R on 2011-11-23
You might be succesful if you install ia32-libs. But try to get the 64-bit one first.

---

### Post by BigSilly on 2011-11-23
They don't supply a 64 bit download. I had to force it too, but I have a 32-64 bit conversion script I got off here ages ago which created a 64 bit .deb for me. I think the above is correct, and despite Ubuntu's best efforts to avoid using them, you will still need ia32-libs. Get that, then run the app from a terminal and see what the output is. I imagine that will fix it personally.

---

### Post by cannon_dt on 2011-11-23
Guys,
Mea culpa. I made a huge blunder.

After doing the force bit, I did not start software center. When I just restarted, it said that Ubuntu needs to repair some broken dependencies and I let it proceed. And then world of goo launched, so I guess it got the ia32-libs and installed it.

But now I am in another bit of bother. Upon quitting the game the resolution does not get back to the normal. It is the huge (I guess 800 x 600) whereas it was 2000 x 1800 (something to that tune). How do I restore back my earlier settings? I got compiz running, could that be the problem?

Ananth

---

### Post by Perfect Storm on 2011-11-23
log out/login should set it back. 

In World of Goo there's an .ini file you can edit to change World of Goo to use the prefer resolution.

---

### Post by BigSilly on 2011-11-23
There's always [GooTool]("http://goofans.com/gootool") as well, which they have lovingly provided for us Linux fans as well as Windows. I have it running peachy on 11.10. :)  It, among other things, allows you to set the proper screen resolution for widescreen monitors. Hope it helps.

---

### Post by thatguruguy on 2011-11-23
> **cannon_dt said:**
> I got the .deb initially when I had my ubuntu 9 and I used the same. I got it from the official download site (not a torrent or something, if that is what you are referring to).


Not really.  I bought it as part of the Humble Bundle, and it was shipped as an _all.deb (meaning it should work, theoretically, on either 32-bit or 64-bit). I also have Desura, and installed it from there to see if it worked on 64-bit. It does, but Desura ships their own ia32-libs.  And, it shows up in the Ubuntu Software Center, and it doesn't note if it is for 32-bit or 64-bit.  

Since there are a number of ways to get it, I was curious which way you got it, because that could impact on how best to trouble-shoot the problem.

---

### Post by cannon_dt on 2011-11-24
@Artificial Intelligence
Logout / Login solved the resolution issue but I could not find any ini file

@BigSilly
Goo Tool worked like a charm. However it does not have a widescreen resolution that matches the one I get in my desktop, I dont know if this will create the same problem when I quit the game

@thatguruguy
I understand your point.

Thanks to all for your help, there is nothing compared to the ubuntu community when it comes to extending help. You guys are the best !

Thanks,
Ananth

---

### Post by Perfect Storm on 2011-11-24
Sorry, it's config.txt

properly /opt/WorldOfGoo/properties/config.txt

---

### Post by cannon_dt on 2011-11-24
Got it, thanks a ton !! :)

Ananth

---

