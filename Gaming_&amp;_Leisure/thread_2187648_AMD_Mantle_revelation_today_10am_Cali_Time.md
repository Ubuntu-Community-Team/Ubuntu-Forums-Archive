---
title: "AMD Mantle revelation today 10am Cali Time"
date: 2013-11-13
forum: Gaming &amp; Leisure
---

### Post by DanglingPointer on 2013-11-13
Today we get a glimpse of Mantle at the AMD Gamming Summit.  Looking forward to what gets said, demoed, and what it means for Linux!  How soon will FGLRX cater for it?

Essentially today for many carefully-waiting gpu-card buyers, it will determine whether to go and get an AMD GCN card or get an Nvidia Kepler card to last them several years.  
I for one am one of them hoping to make the best possible decision based on what factual information is out there.  I've been ready to buy a card for the last 3 months but decided to wait for today's news and demos and perhaps what custom cards for the R9-290(X)'s will come from the OEM's.

My gut tells me that Linux gaming will benefit in the end as all this competition from the red and green camps and the ubiquitous SteamOS on the horizon within months drawing more and more attention to our cherished, free and open platform.

That said, if the news is <deleted> today; I'm getting an EVGA GTX 780 Ti Superclocked with ACX cooling! ](*,)

---

### Post by Arthur_D on 2013-11-13
I'm not sure if the Mantle API will be good news at all - API's need to be vendor neutral and I'm not sure if this will be. Also consider how much retraining and reworking switching API's might be; they better have a **really **good reason for not cleaning up and optimizing OpenGL instead.

---

### Post by DanglingPointer on 2013-11-13
I too believe that OpenGL should have been the way to go and that they should've done something sophisticated and funky with OpenGL ES for all GCN chips regardless of version.

However they are a business for profit and they have monopolised the next-gen console market who use their APU and GPU.  Thus ALL games coming to the consoles will be developed for the GCN architecture and will be optimised for it.  
Since most games in history were developed for the consoles first and not all of them getting ported to PC due to extra development costs (PC having completely different architecture to PS3, Wii and XBOX360); they saw the opportunity to make it easier for game developers to simplify game development for all platforms since they are all on x86 and using their chips.  Thus comes in Mantle which makes it even easier to optimise and develop for GCN specifically or to port existing GCN-console games to PC.

The existing PR and marketing spin on Mantle looks impressive citing between 2-9 times more draw calls per second than existing OpenGL and D3D.  Citing significantly more FPS or more graphics fidelity features turned on at a desired FPS rate.

However the scientific process dictates observed results through testing and experimentation and the public has not seen this yet.  Hopefully today we will see some.  Independent reviews however will not come around until the BF4 December patch which will enable Mantle optimisations for GCN customers which will supposedly give them a massive boost.

---

### Post by DanglingPointer on 2013-11-13
Nvidia can use Mantle!

This is hot off the press...[INDENT]
"[COLOR=#494949][FONT=Helvetica]AMD insists that Mantle was not intended to be limited to a particular architecture. At its base level, Mantle is comprised of relatively generic functions that could be supported by other architectures. Support for functions specific to its Radeon GPUs is included as an extension. This implies that Mantle could potentially become a standard with multiple extensions to cater for architectural differences. However, this is all in theory and it remains to be seen if the technology is feasible in the long run.[/FONT][/COLOR]"[/INDENT]

Source: [http://gearnuke.com/in-depth-look-at-amd-mantle/](http://gearnuke.com/in-depth-look-at-amd-mantle/)

Questions:

[LIST=1]
[*]When does Linux support it?
[*]What will be the first Linux native AAA game title to use it?
[*]Will game developers provide Nvidia Mantle optimisations for Kepler cards as well? (My Conjecture: Not probable, depends on the size of the game project. GTA V-sized games will probably do it but lesser known titles from smaller developers with smaller budgets won't; there would be too much extra development costs as GCN extension optimisations would have already been mapped out for the GCN chips on the consoles thus just porting them to PC is a lot cheaper.  Optimising for Nvidia would blow smaller or tighter budgets.)
[*]Will BF4 release a Mantle patch for Nvida?
[*]Will Nvidia play cooperatively/collaboratively with AMD?
[*]Will Intel play cooperatively/collaboratively with AMD?
[*]Will Mantle be given to a new agnostic group to govern the standard similar to Khronos for OpenGL?
[/LIST]

One thing I can say though, if that quote above and the presentation proves to be accurate and not a mistake, then..........  +200 "Good Guy" Points to AMD!  (They are good and not evil greedy, but good greedy! :D)

Here is another link: [http://www.dsogaming.com/news/amds-mantle-does-not-require-gpus-with-gcn-architecture/](http://www.dsogaming.com/news/amds-mantle-does-not-require-gpus-with-gcn-architecture/)

ADDITIONAL HIGHLIGHT:
Something that just caught my eye...[INDENT]
"[COLOR=#494949][FONT=Helvetica]The application also acquires the ability to take control of multi-GPU configuration and decide where to run each issued command. What AMD is essentially offering is direct access to data transfer between multiple GPUs, with flexible workload scaling and partitioning. It will also support asymmetric multi-GPU systems, such as an APU working in conjunction with a dedicated GPU. This leads to the idea of novel usage scenarios where the GPU may handle the rendering load and offload all post-processing to the APU.[/FONT][/COLOR]"[/INDENT]

If I'm interpreting this correctly, an APU coupled with a powerful dGPU ends up unified without crossfiring for graphics and direct-compute (OpenCL for physics as an example) computational tasks with both sharing memory realms without fixed delineations (you know in the BIOS you allocate fixed memory amounts for the integrated graphics like Intel's HD4000, with Mantle and an APU it would not be needed!)!  WoW!  You can get the gpu part of the APU to help the vastly more powerful dGPU all while the quad x86 core in the APU is processing high-level stuff; AND all using the same pool of memory!

I may not be entirely correct about this though...  If I'm wrong someone please correct me.

Question is, how does this affect Intel?

ADDITIONAL SLIDES:
There are slides on this post from xtremesystems; one of which mentions Linux.  I suppose it would also be important to note that DICE is using the PS4 as the base development platform.  PS4's OS is a *nix based off BSD which is very similar to Linux.  Thus perhaps a conjecture could be made that it would be easier to port to Linux than to Windows.
[http://www.xtremesystems.org/forums/showthread.php?287815-AMD-Mantle-update...&p=5216523](http://www.xtremesystems.org/forums/showthread.php?287815-AMD-Mantle-update...&p=5216523)

ADDITIONAL FULL VIDEO PRESENTATION:

[LIST]
[*]Johan Andersson is the Technical Director and Architect for the Frostbite Engine at DICE.
[/LIST]

[LIST]
[*]He mentions 15 games under development will utilise Mantle.
[/LIST]

[LIST]
[*]~29mins into the video he discusses Linux and Mac and I quote:
[/LIST]
[INDENT=2]"Significantly easier to do efficient renderer with Mantle than with OpenGL"
"Mantle + SteamOs = Powerful combination!"[/INDENT]

Video: [http://www.youtube.com/watch?v=N_6CAneoW-0](http://www.youtube.com/watch?v=N_6CAneoW-0)

---

### Post by Arthur_D on 2013-11-15
> **DanglingPointer said:**
> Nvidia can use Mantle!

This is hot off the press...[INDENT]
"[COLOR=#494949][FONT=Helvetica]AMD insists that Mantle was not intended to be limited to a particular architecture. At its base level, Mantle is comprised of relatively generic functions that could be supported by other architectures. Support for functions specific to its Radeon GPUs is included as an extension. This implies that Mantle could potentially become a standard with multiple extensions to cater for architectural differences. However, this is all in theory and it remains to be seen if the technology is feasible in the long run.[/FONT][/COLOR]"
[/INDENT]
 Well this sounds all good and well in theory, but I'm still wary. Standards may be intentionally crafted to favour one or another even if others could potentially implement the same features (but with great hassle) - see Microsofts [OOXML]("https://en.wikipedia.org/wiki/Office_Open_XML") as an example. So I guess we'll just have to wait and see, also regarding adoption and real-world performance (if Mantle needs a lot of optimizations that most games except the major studios can't afford to implement, it won't be particularly useful except to make future AAA titles a little bit more photorealistic).

---

### Post by sheridanm962 on 2013-11-15
Johan Andersson said that with the Frostbite 3 Engine when he was working with Mantle on the engine that it was able to be then ported to other games natively and fluidly, there's more than one game running on the engine itself and for that to be across the board is pretty neat, the learning curve shouldn't be too steep unless someone were to go by what they did back in the day with DirectX vs OpenGL, they would say "I'm not experienced enough for OpenGL, I just don't think I would implement it, I already know how to implement DirectX" Which in itself is a pretty bad statement to make considering the payoff was immensely better on the OpenGL side.

---

### Post by DanglingPointer on 2013-11-15
I guess I'm sold on the idea of Mantle.  But that's the problem! Right there in my statement! "idea".  It is still nothing but an idea!
Until we can see demonstrable evidence and proof, it would literally be a leap of faith for a customer currently on the market (like myself) to buy a GCN card instead of the currently better performing Kepler cards which have better quality propriety Linux drivers which should work all the way up to a GTX 780 Ti.

However that said, the writing is on the wall especially with EA and DICE sold on Mantle and spending millions of dollars refactoring their code for 15 AAA games which will undoubtedly generate billions of dollars of revenue!  That in itself will wake up the whole industry!

I wish I was a fly on a wall around the steering committee meetings undoubtedly happening at Nvidia on how they plan to respond to Mantle and the massive threat of market share decreasing due to this technology and AMD cornering the console market thus a majority % of all AAA game development inherently optimised for GCN when it comes time to PC porting.

---

### Post by R33D3M33R on 2014-06-18
PCWorld: [AMD wants to improve gaming in Linux and Steam boxes with its Mantle tools]("http://www.pcworld.com/article/2364760/amd-wants-to-improve-gaming-in-linux-and-steam-boxes-with-its-mantle-tools.html")

---

### Post by mastablasta on 2014-06-20
Huh? > Advanced Micro Devices wants to bring console-quality gaming to Linux users by porting its Mantle gaming tools to the OS

ok so console games are developed on PC, so PC experience will always be better than console. i am not sure why i would want console limitations on pC games.

but anyway i hope AMD get's their drivers together be it mantle or opengl or whatever. as long as it works propperly. It works in Windows so there is no reaosn it shouldn't in Linux. it's all about how much time you put in it.

---

### Post by -Marco on 2014-06-23
There will take time, Mantle is still not very mature. 
nVIDIA drivers side is light years ahead, instead Intel beats all. :)

---

