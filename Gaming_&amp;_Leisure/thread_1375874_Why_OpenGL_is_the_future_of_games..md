---
title: "Why OpenGL is the future of games."
date: 2010-01-08
forum: Gaming &amp; Leisure
---

### Post by cajual on 2010-01-08
Read this: [http://blog.wolfire.com/2010/01/Why-you-should-use-OpenGL-and-not-DirectX](http://blog.wolfire.com/2010/01/Why-you-should-use-OpenGL-and-not-DirectX)

This is my favorite part:
> 
It's common knowledge that OpenGL has faster draw calls than DirectX (see NVIDIA presentations like [this one]("http://developer.nvidia.com/object/opengl-nvidia-extensions-gdc-2006.html") if you don't want to take my word for it), and it has first access to new GPU features via [vendor extensions]("http://www.opengl.org/wiki/OpenGL_Extensions"). OpenGL gives you direct access to all new graphics features on all platforms, while DirectX only [provides occasional snapshots of them]("http://en.wikipedia.org/wiki/Comparison_of_OpenGL_and_Direct3D#Extensions") on their newest versions of Windows. The tesselation technology that [Microsoft is heavily promoting for DirectX 11]("http://www.microsoft.com/games/en-US/aboutGFW/pages/directx.aspx") has been [an OpenGL extension for three years]("http://developer.amd.com/gpu_assets/AMD_vertex_shader_tessellator.pdf"). It has even been possible for years before that, using [fast instancing and vertex-texture-fetch]("http://http.developer.nvidia.com/GPUGems3/gpugems3_ch05.html"). I don't know what new technologies will be exposed in the next couple years, I know they will be available first in OpenGL.
  Microsoft has worked hard on DirectX 10 and 11, and they're now about as fast as OpenGL, and support almost as many features. However, there's one big problem: they don't work on Windows XP! [Half of PC gamers still use XP]("http://store.steampowered.com/hwsurvey/"), so using DirectX 10 or 11 is not really a viable option. If you really care about having the best possible graphics, and delivering them to as many gamers as possible, there's no choice but OpenGL.[B]
[/B]

****

---

### Post by edd07 on 2010-01-08
And yet, developers continue to use DirectX....
Buisiness is buisiness, I guess.

---

### Post by cajual on 2010-01-08
> **edd07 said:**
> And yet, developers continue to use DirectX....
Buisiness is buisiness, I guess.

That's the premise of the article.

---

### Post by kforum on 2010-01-08
Thats because most schools teach directx, which in turn is a msoft legacy.
And also because most devs arent worth their pay, honestly. They are too lazy to dwell on competence.

---

### Post by edd07 on 2010-01-08
> **cajual said:**
> That's the premise of the article.
Haha, well, I didn't read it, just the bit you quoted.

---

### Post by Melcar on 2010-01-08
I already saw this pop up on several of the hardware enthusiast boards I frequent.  Needless to say that the article is getting flamed right and left,  No surprise given the general membership of those places.
In my opinion the only "hope" for OpenGL in the gaming scene is with the smaller indie studios.  That is were OpenGL has a better chance of adoption and were it can become a major player in the gaming graphics arena.  The mainstream market is too bloated and big to use anything but DX and keep betting on the sure thing; they have proven us time and time again that they are more interested in chasing profits rather that making good games.  Hope they crumble and die in a fire.  The whole gaming "industry" needs to be cleansed.

---

### Post by del_diablo on 2010-01-08
Well, who can disagree with wise words that should have hit the world a few years ago?

---

### Post by CharmyBee on 2010-01-08
> **del_diablo said:**
> Well, who can disagree with wise words that should have hit the world a few years ago?
You mean Carmack's words?

One of the main drives behind DirectX is in the marketing. OpenGL doesn't have a high version number to stimulate profits with, and it doesn't have a 'Defective By Design' bribe behind it (DX10 requiring Vista/7, despite new equivalent capabilities available in OpenGL extensions for all platforms), and OpenGL doesn't have a big PR department to hype what it can do.

The DirectX vs OpenGL fight did matter... in the '90s when every card had a crappy OpenGL ICD.

---

### Post by mister_playboy on 2010-01-09
This was posted to Slashdot... just the kind of thing to get fanboys on both sides riled up. :popcorn:

---

### Post by myromance123 on 2010-01-09
I talked to some of my buddies who use DirectX and they all think OpenGL is crap. They don't even know what it can do, they just "think" its crap...

 They don't even take time to explore. I don't see the gaming industry changing to OpenGL on a largescale unless MS mess up with the next DirectX in a big way lol....

Its a sad shame.

---

### Post by Sockerdrickan on 2010-01-09
I hope the next generation of devs are leaning for OpenGL. I use it exclusively for my work, I havn't even looked at D3D because of how closed it is.

---

### Post by Sindwiller on 2010-01-09
> I talked to some of my buddies who use DirectX and they all think OpenGL is crap. They don't even know what it can do, they just "think" its crap...

Despite the fact that Direct3D copied the state-driven API of OpenGL in later versions? :D :D :D

Besides, most "new" people program in C# with XNA, anyway, which is enough proof of how advanced their knowledge actually is. :P

---

### Post by jrothwell97 on 2010-01-09
Give people an easy-to-learn, coherent API for OpenGL game programming and people will use it.

A good programmer maketh not a good game designer, and vice versa. (Hence, XNA is not necessarily a bad thing.)

---

### Post by Sindwiller on 2010-01-09
> Give people an easy-to-learn, coherent API for OpenGL game programming and people will use it.

OpenGL might not be easy-to-learn, but it is pretty coherent for it's API level. For other stuff, there's things like OGRE and Irrlicht (both of which support both API's though).

---

### Post by MaximB on 2010-01-10
The one thing I've noticed about some game developers and indies is that they develop with both OpenGL and DirectX (AoD, Regnum Online, WoW etc...) , the question is why ? why do they develop on DirectX (specially for the Windows users) if they have OpenGL ?

---

### Post by mrobert on 2010-01-10
Hello,

As a developer, I have used both APIs (and still do) over the past 10 years. For me, they both seem the same in terms of complexity. I decided which to use, based on project requirements.

I picked up OpenGL again (OpenGL ES actually) to develop games for the iPhone. 
I have made the graphics engine for [Hacker Evolution: Untold]("http://www.exosyphen.com/page_hacker-evolution-untold.html") using Direct3D 9.
We are almost done with porting Hacker Evolution: Untold to linux (just played it under Ubuntu last night), and the developer doing the port, ported the graphics engine over to OpenGL.

Sometime in the next months, I will start working on a new PC game engine and I will do it in OpenGL this time. It's awfully easy to port it to Linux,Mac and iPhone, using OpenGL.

[Rail Adventures 3D]("http://www.exosyphen.com/page_iphone-rail-adventures.html") was developed under Windows using OpenGL. I ported it to the iPhone in 10 minutes with a few lines of code changes. The graphics engine under it, allows me to work under Windows and just compile for the iPhone by changing a single line of code. After the graphics engine was finalized, 100% of the game was developed under Windows and just compiled on a Mac for release on the iPhone.

On the other hand, DirectX now opens up the possibility to develop for the XBox. I might end up porting the engines back to Direct3D if I decided to target the XBox.

Bottomline is:
OpenGL is available on a lot of platforms and a lot of developers use it. Despite the lack of PR and advertising around it :)

---

### Post by MaximB on 2010-01-10
If it took you 10 minutes to port Rail Adventures 3D to the iPhone, why not invest another 10 minutes to port it to Linux ?

---

### Post by munky99999 on 2010-01-10
OpenGL + Id tech 4(to be made open source sometime in 2010)

This i think will be the best part of open source games. Currently they suffer from really bad graphics... but with this new engine they will be able to build games which are much nicer looking.

Sadly it will probably take 1-2 years at least before we see some good stuff coming out.

Something to hope for though :)

---

### Post by Arthur_D on 2010-01-10
As far as graphics go, it's mostly a matter of lack of good artists. As someone else said, a programmer can make a game 10 times before getting any artist on board. And artists aren't necessarily good at making the stuff the project needs; for example he might be a great 3D modeller but lack in texturing skills (or good textures) and vice versa.

---

### Post by myromance123 on 2010-01-10
I have to agree with Arthur_D there.

 Probably the reason open source doesn't go as far as closed source in gaming is because there is no *money* to push the artists (if any) and the programmers to get things to meet and match at the ends. When art doesn't match the game, it can seriously ruin it. 

 Mmm art isn't easy either, and I think artists like money. Lots of money....

---

### Post by Sindwiller on 2010-01-10
> **Arthur_D said:**
> As far as graphics go, it's mostly a matter of lack of good artists. As someone else said, a programmer can make a game 10 times before getting any artist on board. And artists aren't necessarily good at making the stuff the project needs; for example he might be a great 3D modeller but lack in texturing skills (or good textures) and vice versa.

Parallel to that, good programmers and good artists don't make a good game. Game design is just as important.

---

### Post by Melcar on 2010-01-10
Well, a game in Linux doesn't have to be open source.  It has already been shown that people are more than willing to buy good, quality software for Linux.  There is no reason a company cannot make money from a Linux game.  The problem I think lies with the current state of PC gaming.  IGN just put out an article that explained it really well.  In short, none of the big studios and publishers will ever do it.  Linux is seen as sort of a Wild West, and only the smaller indie firms are flexible enough to be able to invest in such a venture.

---

### Post by mrobert on 2010-01-10
> **MaximB said:**
> If it took you 10 minutes to port Rail Adventures 3D to the iPhone, why not invest another 10 minutes to port it to Linux ?

Going to do that!
I just need to remake some of the graphics to look great on desktop displays.

The textures and models are designed for a 480x320 display.
I tested it at 1280x800 and it doesn't look so great (yet).

---

### Post by MaximB on 2010-01-10
> **mrobert said:**
> Going to do that!
I just need to remake some of the graphics to look great on desktop displays.

The textures and models are designed for a 480x320 display.
I tested it at 1280x800 and it doesn't look so great (yet).

Great news.
Thanks.

---

### Post by johnboy1313 on 2010-01-10
I read this article and reposted it on my blog as well, I found it to be really interesting, but at the same time, as much as I hate to admit it I don't think direct x is really gonna go away any time soon

---

### Post by mrobert on 2010-01-10
I believe there is room for both API's on the long run.
It's not like there is a "war" out which one API should win.

---

### Post by Bad Sector on 2010-01-11
A good reason for someone choosing DirectX over OpenGL is a little file called *dxsdk.chm* (or whatever is called these days anyway) that comes with the DirectX SDK. This file contains everything you need to know to use DirectX. It includes tutorials, guides, reference, etc - even a brief introduction to 3D graphics.

For OpenGL the closest thing is a site called Google. Which, frankly, is as nicely categorized and laid out as the aforementioned dxsdk.chm file. Actually, it lacks categories, a TOC, index, etc. It has nice search facilities though, although the results do not always contain what you're looking for. Also it looks like it has been written by thousands of people in a vacuum. Beyond that, the guide seem to cover only the 1993 version. And the reference is a major version old. Not to mention the latest version removes almost the whole API. There are some official books, but they're also outdated and refer to the removed API.

So, basically, what i want to say is that Direct3D is simply easier to learn and start using. Yea yea yea, i know! glBegin()/glEnd() and stuff are easier than the COM-based API of a bunch of objects that Direct3D requires. But the problem is, its harder to find the right information about OpenGL than Direct3D.

Now you might wonder what this has to do with good games in Linux. Good programmers won't have a problem figuring out how to obtain information about OpenGL afterall, right? Right. I agree with that.

The problem begins when you start realizing that good programmers aren't born good: they start as beginners. And as a beginner in 3D, you'll choose to learn what seems easier to learn (and what seems to be everywhere too, but thats another point). Currently, getting started with Direct3D is easier because all you need to do is download Visual Studio Express and the Direct3D SDK and you're set. Everything is included in your computer, ready to be read, right from the mouth (and hands) of those who designed and implemented them. OpenGL doesn't have this jumpstart easiness (not even in Linux which is a bit easier since in most distributions you can install a GL development environment via the package system).

So a lot of people start with Direct3D. And when they become "good programmer" later, what they know is Direct3D. So when they decide what to use for their new/next game is simply what they know: Direct3D.

You might hear a lot of excuses from people who use Direct3D (OpenGL is crap, it has bad drivers, etc) but while there is some truth in these statements (some vendors indeed produce crappy ICD drivers for Windows and ATI performance on Linux is laughable) , but the real reason people choose Direct3D is because that's what they know better and they don't see a good reason to switch - especially for commercial games (who cares about the combined sub-1% of the linux+macosx game market? Of course most people do not realize that the 99% windows game market is oversaturated and the linux+macosx game market is hungry for good games,  nor they believe indies who get more sales from linux+macosx than windows).

Anyway.

All my games (the 3D ones at least) are written in OpenGL, all my 3D code is written in OpenGL and this will remain true as far as i can use OpenGL. If one day Windows decides to drop OpenGL support, i'll just write a GL-like wrapper for my code that uses Direct3D (thats my "cross-API wrapper" solution).

The reason i chose OpenGL was the same reason others chose Direct3D: when i started i had more people around me knowing OpenGL that i could bother asking questions. The crossplatform stuff was something i figured out later.

In fact i tried to learn Direct3D back then, but my english weren't as good as today and couldn't understand what the docs were saying.

Today i'm using OpenGL not only because its simple, crossplatform, open standard, etc, but also (and mostly) because thats what i know and i don't see a reason to switch.

---

### Post by Bucky Ball on 2010-01-11
ARM processors maybe another reason OpenGL is the future of graphics. Embedded into the processor I believe, no need for a separate graphics chip.

Give it five years and they might be beefy enough to match what's around in desktops, but they'll probably flood the netbook market sooner and offer full HD 1080 x whatever it is already.

---

### Post by MaximB on 2010-01-11
@Bad Sector :
What games have you made ? are they commercial, FOSS, freeware ?
Do you work for a gaming company ?

---

### Post by Bad Sector on 2010-01-11
@MaximB:
I've worked in a greek (i'm from Greece) game developer, but the company closed before the game was finished due to financial reasons. Unfortunately there aren't many devs in Greece (i consider moving to UK at some point).

I've made some small games myself. One of them is actually included in Ubuntu: Nikwi Deluxe :-). Other games include Nico Tuvla (a predecessor of Nikwi), Square Shooter and some Flash games (one of them is  a 3D FPS style game). Unfortunately my VPS is down atm - i'll put it up tomorrow and post links if you're interested.

For OpenGL stuff, i've always stumbled on making the 3D art so i never released anything :-P. I decided to learn 3D art using Blender recently though, so eventually i hope i'll release something.

The "*all my games (the 3D ones at least) are written in OpenGL*" line is a bit misleading though; sorry for that, i noticed it now. I haven't *released* a 3D game in OpenGL (unless walking around in 3D worlds counts as a game :-P). I have *written* code for such games though. I hope i'll have one released before the end of 2010. Hopefully. Finger crossed. Etc. :-P

---

### Post by Sindwiller on 2010-01-11
Nowadays, nobody actually bothers to read .chm's anymore.

> But the problem is, its harder to find the right information about OpenGL than Direct3D.

I [beg]("http://nehe.gamedev.net/") [to]("http://www.opengl.org/documentation/") [differ]("http://www.opengl.org/sdk/docs/tutorials/"), dear sir. :) Nehe is actually the best source for basic GL/GLUT stuff. :)

> I hope i'll have one released before the end of 2010. Hopefully. Finger crossed. Etc.

Good luck =)

---

### Post by munky99999 on 2010-01-11
> **Arthur_D said:**
> As far as graphics go, it's mostly a matter of lack of good artists. As someone else said, a programmer can make a game 10 times before getting any artist on board. And artists aren't necessarily good at making the stuff the project needs; for example he might be a great 3D modeller but lack in texturing skills (or good textures) and vice versa.

It's funny you say that actually. I'm like a savant at 3d modeling(I have perfect spatial IQ). I have made a very highly detailed model before. Then when it came time for texturing. I was clueless. I found some help and they basically refused to believe I could make the model; demanded that I be sued for copyright infringement and plagiarism. Also wanted to hire the person who did the model. Then when I proved that it was me; right infront of his eyes. He was very apologetic but I wasnt taking that crap.

What's even wierder. I'm decent as photoshop/gimp in photoediting. I'm absolutely horrible at trying to start something from scratch.

> Probably the reason open source doesn't go as far as closed source in gaming is because there is no *money* to push the artists (if any) and the programmers to get things to meet and match at the ends. When art doesn't match the game, it can seriously ruin it.
Ya. The single most damning thing for open source games atm is that they dont look good. Like I play all the latest games. I've beaten dragon age origins. I dont think games need to have anything close to that kind of graphics for them to be fun.

Doom3 - Bf2142 are just perfect for games now. Hell I've been playing loads of bf2142 recently.

The great thing is. The ID tech 4 game engine is being open sourced this year :)
> 
Nowadays, nobody actually bothers to read .chm's anymore.
I disagree sir. Tons of malware is actually hiding information in .chm files. Lots of reading of .chms happens.

Wait that's not a good thing :(

---

### Post by mrobert on 2010-01-11
One thing I don't like in these kind of discussions.
When non-programmers come and make statements that Direct3D will become extinct and OpenGL is the future.
What do you base those assumptions on? Personal propaganda?
This is close to the thin line next to a dogma.

At today's state, I see both OpenGL and Direct3D as being very mature API's.

@Bad Sector gave us a very reasonable explanation as why he has chosen one, over the other.

I remember Carmack stating at some point, that what would be really cool is a low-level assembly like API which we could use to work directly with the videocard.

---

### Post by Bad Sector on 2010-01-12
> **Sindwiller said:**
> I [beg]("http://nehe.gamedev.net/") [to]("http://www.opengl.org/documentation/") [differ]("http://www.opengl.org/sdk/docs/tutorials/"), dear sir. :) Nehe is actually the best source for basic GL/GLUT stuff. :)

But here is the problem actually: i mentioned i know about GL and used it and yet you thought that i wouldn't know these sites - if that was the case, how could a beginner know about them? :-)

The [current OpenGL SDK page](http://www.opengl.org/sdk/) is a step in the right direction though, but i think that currently is very weak and depends too much on external sites.

@mrobert:
I think CUDA has this :-). And maybe OpenCL since i think its modeled after CUDA, but it might include only the high level language, not the assembly one.

---

### Post by MaxIBoy on 2010-01-13
> **munky99999 said:**
> OpenGL + Id tech 4(to be made open source sometime in 2010)The shadow code will be stripped out of the engine due to patent concerns, leaving it looking very dated. Fortunately, better algorithms already exist and can be re-added to the engine without violating the patents.

---

### Post by mrobert on 2010-01-13
I wrote the graphics engine for our latest (indie) game on top of Direct3D in a pretty abstract maner.

That made the port to Mac (using OpenGL) and now Linux (also using Linux), pretty straightforward.

Targeting both API's (D3D and OGL) is not that hard.

---

### Post by ALIENDUDE5300 on 2010-01-13
I absolutely loved this article. I actually found it before I saw your post, but it's such a great insight into the world of game development, and seeing how microsoft is abusing their money to get more and more people locked into their platform.

---

### Post by MaximB on 2010-01-14
> **mrobert said:**
> I wrote the graphics engine for our latest (indie) game on top of Direct3D in a pretty abstract maner.

That made the port to Mac (using OpenGL) and now Linux (also using Linux), pretty straightforward.

Targeting both API's (D3D and OGL) is not that hard.

I've asked it before, but got no answer...

Why would anyone use DirectX AND OpenGL for the same project ?
If he knows his game will be multi platform and he uses OpenGL for it , why use DirectX only for the Windows users who can use OpenGL like the rest ?

---

### Post by Bad Sector on 2010-01-14
@MaximB:
In Windows OpenGL drivers are still inferior when compared to DirectX drivers in term of stability, features or even existence. While nVidia and ATI do a good job, they're far from the market leaders (Intel is) and there are other GPU manufacturers beyond nVidia, ATI and Intel. These GPUs are usually used in low cost systems. If you want your game to cover as many players as possible, you need to use DirectX in Windows because OpenGL might not exist or be crippled.

Note however that this probably makes sense only if your game's target audience contains people who have absolute no knowledge about choosing PC parts and your game is 2D or very simple 3D. Usually these are the casual games who are 2D and want hardware acceleration to support bigger resolutions and alpha blending for some extra "blitz" effects.

@MaxIBoy:
Do you have a source for this? From what i've read all these years, the patent that Creative holds is not enforceable both because it is mathematically very simple to derive and there is prior work for it before Creative submitted it. And beyond that, the patent - if is enforceable - applies only in US.

Unfortunately there isn't a better method for stencil shadows, at least not one which is not based on the zfail shadows (which is what Creative claims to hold a patent for). Of course you can use some other shadow type - most likely shadow buffers - but the game simply won't look the same.

---

### Post by MaxIBoy on 2010-01-14
Well, the patent may or may not be enforceable (never been tried in court so I can't provide any specific examples,) but as id software has backed down from lawsuit threats, this gives it an "air of legitimacy." And with apologies to everyone else in the world, US law is the most important here. It is the worst common denominator of what is allowed.

First of all, there is an algorithm which does Carmack's Reverse "backwards." I'm not sure how this is done, but I know DarkPlaces does this; Alien Arena's most recent releases do this as well ([link1](http://corent.proboards.com/index.cgi?action=display&board=aatech&thread=4203&page=1), [link2](http://alienenforcer.com/e107_plugins/macgurublog_menu/comment.php?rid=3),) but as far as I know they are [switching to shadowmaps](http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4571&page=1) (which are looking a lot cooler already.)

---

### Post by mrobert on 2010-01-14
@MaxIBoy ... where can I find some additional info on Carmack's Reverse "backwards" ?

---

### Post by yester64 on 2010-01-14
> **mrobert said:**
> One thing I don't like in these kind of discussions.
When non-programmers come and make statements that Direct3D will become extinct and OpenGL is the future.
What do you base those assumptions on? Personal propaganda?
This is close to the thin line next to a dogma.

At today's state, I see both OpenGL and Direct3D as being very mature API's.

@Bad Sector gave us a very reasonable explanation as why he has chosen one, over the other.

I remember Carmack stating at some point, that what would be really cool is a low-level assembly like API which we could use to work directly with the videocard.

I am not a programmer at all, but i do remember the time most games were using OpenGL (Decent, Unreal) and then bang DirectX took over.
At that time Vodoo cards were the hottest thing on earth but thats gone a long time ago.
Can't tell really whats better or not, but i don't recall any problems with OpenGL at that time, but some issues with DirectX (no sound huh).
In the end, what works works and a normal consumer with no knowledge about whats going on behind the dots does not worry about all these issues.
One thing is for certain, that DirectX is Windows only and OpenGL can be used anywhere else.

---

### Post by mrobert on 2010-01-14
Unreal used OGL, D3D and a software renderer :)

---

### Post by CharmyBee on 2010-01-14
It also used 3dfx Glide, S3 Metal, and PowerVR SGL. It only had Glide and SGL support in its initial release, the OGL, S3 and D3D support were all afterthoughts.

---

### Post by Bad Sector on 2010-01-15
> **MaxIBoy said:**
> but as id software has backed down from lawsuit threats, this gives it an "air of legitimacy."

Well, Carmack said that they initially wanted to dispute the patent but that would only delay an already delayed game, so they just went with Creative. Creative on their part didn't asked for more than licensing their EAX tech. I think Creative knew that their patent claims wouldn't hold in court and they wanted to make id license the tech exactly because "if id backed down, then its legal". Basically a case of good old FUD.

>  First of all, there is an algorithm which does Carmack's Reverse "backwards." I'm not sure how this is done, but I know DarkPlaces does this; Alien Arena's most recent releases do this as well ([link1]("http://corent.proboards.com/index.cgi?action=display&board=aatech&thread=4203&page=1"), [link2]("http://alienenforcer.com/e107_plugins/macgurublog_menu/comment.php?rid=3"),) but as far as I know they are [switching to shadowmaps]("http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4571&page=1") (which are looking a lot cooler already.)

That's interesting. As for shadow maps, they might work in a game like Alien Arena which is based mostly on lightmaps, but i'm not sure they would work in a game like Doom 3 which uses shadows everywhere.

---

### Post by Sindwiller on 2010-01-15
> That's interesting. As for shadow maps, they might work in a game like Alien Arena which is based mostly on lightmaps, but i'm not sure they would work in a game like Doom 3 which uses shadows everywhere.

UE3 games heavily use cascaded shadow maps along with Doom3-ish per-pixel lighting sometimes. However, the level designer can define that in the level editor, whether a model or a surface is affected by pre-computed (so, radiosity lightmapping) lighting or real-time lighting and shadows and which lights to take in account for either one or even both. It does really depend on what your approach is, really :)

> First of all, there is an algorithm which does Carmack's Reverse "backwards." I'm not sure how this is done, but I know DarkPlaces does this; Alien Arena's most recent releases do this as well (link1, link2,) but as far as I know they are switching to shadowmaps (which are looking a lot cooler already.) 

Not only DarkPlaces. Most likely OGRE, too. And other libraries/frameworks/engines using that technique. :)

---

### Post by Mistrblank on 2010-01-15
> **kforum said:**
> Thats because most schools teach directx, which in turn is a msoft legacy.
And also because most devs arent worth their pay, honestly. They are too lazy to dwell on competence.

I don't necessarily agree with that.  Most of the bigger schools teach DirectX, and they probably do it because Microsoft will offer grants and other incentives to do so.  

I went to a smaller state college and we learned OpenGL for our graphics classes.  

On a similar vein, I'd say that most game developers continue to use it as well because Microsoft gives them incentives.

---

### Post by ZeroSpawn on 2010-01-15
DirectX will win cause microsoft owns it. Thats why Carmack left the ranks.

---

### Post by mrobert on 2010-01-16
> **ZeroSpawn said:**
> DirectX will win cause microsoft owns it. Thats why Carmack left the ranks.

None will win because there is no contest.
Developer will use one of the 2 API's, based on their needs.

It's been like this for the past 10 years, and it will continue just like that.

---

### Post by MaxIBoy on 2010-01-17
> **mrobert said:**
> @MaxIBoy ... where can I find some additional info on Carmack's Reverse "backwards" ?
As I said, I don't know. I'm not a graphics programmer. I was quoting an Alien Arena dev when I described the technique as "backwards." I know DarkPlaces does this, but that's the most I can tell you, sorry.

---

### Post by mrobert on 2010-01-17
> **MaxIBoy said:**
> As I said, I don't know. I'm not a graphics programmer. I was quoting an Alien Arena dev when I described the technique as "backwards." I know DarkPlaces does this, but that's the most I can tell you, sorry.

Found it eventually :)

---

### Post by Bad Sector on 2010-01-18
> **Sindwiller said:**
> UE3 games heavily use cascaded shadow maps along with Doom3-ish per-pixel lighting sometimes. However, the level designer can define that in the level editor, whether a model or a surface is affected by pre-computed (so, radiosity lightmapping) lighting or real-time lighting and shadows and which lights to take in account for either one or even both. It does really depend on what your approach is, really :)

Yes, shadow mapping works better with precomputed lightmaps and is possibly a better approach (Source engine uses that method too and looks just fine too). However Doom3 doesn't use these - all lighting is dynamic. While it is possible to use shadowmaps in Doom3 (in fact, i think the newer Wolfenstein game uses shadowmaps instead of shadow volumes and its based on the Doom3 engine), what i doubt is that it'll look as good as Doom3 used to look. You need very high resolution shadowmap textures to match the same result as shadow volumes and even then you'll still get some jagginess. Not only that, but Doom3 has a large number of lightsources when compared to engines that use shadowmaps and when you combine this with the large texture needed, i think its probably impractical to use shadowmaps unless you have a very high end card.

---

### Post by Irritant on 2010-01-18
I've been working on shadowmapping in Alien Arena for some time as Max mentioned.  What I've found is, that it's good for some things, and dreadful looking in others.  

The shadowmaps in UT3 are pretty weak.  They are only on players, ammo, weapons, etc, don't have shadows.  Not only this, but they are completely unaffected by dynamic light, and world lighting doesn't appear to have any effect either that I can see.  Quite disappointing after the early videos and promises that engine made.  Unless they've made some changes since UT3 was released?

Xreal has shadowmaps working but as far as I can tell it's really using GLSL to do vertex extrusions much like Carmack's Reverse, then filling them.  It works cleanly though, and looks decent enough.  Darkplaces has also implemented them as well, but something doesn't seem quite right about them to me in regards to shadows cast by world lights(as in they don't seem to exist in places they belong - note that could be an issue with the map makers).  

As for my shadowmap excursions, I've had them working semi-decently, but the usual problems of artifacts, and pixelation are there, as well as light source limitations, etc.  I think that shadowmaps work great for dynamic lights, and we've recently committed that to SVN.  Shadows casted from world lights are still using stencil volumes(using the "reverse Carmack's Reverse" algorithms for now.  I'm currently working on an algorithm that will actually blur the stencil volumes using GLSL, but it's tricky.  I do have an example program that I'm following, so it is possible to be sure.  It requires rendering the scene into a renderbuffer with no textures and applying the stencil mask, capturing the image from the renderbuffer, then blurring it in GLSL before rendering it in a quad over the screen.  The results are pretty nice from what I've seen, but there are some problems.  For starters, I'm not sure how the performance will be, but so far it seems similar to shadowmaps.  The larger problem is that ATI drivers are severely broken in regards to render buffers.

---

### Post by mrobert on 2010-01-19
Everytime I get dragged into discussion like this, I always end up wasting time with a pen and pencil.

I have been doing some research on shadows again. The subject has obsessed me for a few years.

To make things sound crazy, I got an idea while looking at a graphics in an nVidia document on shadows. 
The idea is to break down everything to 2D, and work with 3 cross sections along each axis. Then reconstruct the 3D model with shadows and lights.

---

### Post by Sindwiller on 2010-01-19
> he shadowmaps in UT3 are pretty weak. They are only on players, ammo, weapons, etc, don't have shadows. Not only this, but they are completely unaffected by dynamic light, and world lighting doesn't appear to have any effect either that I can see. Quite disappointing after the early videos and promises that engine made.

That's because in a multiplayer-oriented game like UT, you hardly want to have recurring performance jerks ;) Due to the nature of the responsible element (it being a purely visual phenomenon not needed in a MP game), you can dismiss it at the gain of performance and stability, hence why dynamic shadows and dynamic lights are disabled on most of the level geometry in UT maps. Though you can do otherwise in UT3/UE3, since you're able to define all these things in UnrealED (as already mentioned, ffs).

---

### Post by Irritant on 2010-01-19
> **Sindwiller said:**
> Though you can do otherwise in UT3/UE3, since you're able to define all these things in UnrealED (as already mentioned, ffs).

No need to get testy.  

Are you sure these are truly dynamic, and not static shadows?  I ask because the player shadows are unaffected at all by dynamic light.

---

### Post by ZeroSpawn on 2010-01-24
All I have to say is that I would buy a video card that will do 60fps at all times. Voodoo people know what I'm talking about.

---

### Post by mrobert on 2010-01-24
> **ZeroSpawn said:**
> All I have to say is that I would buy a video card that will do 60fps at all times. Voodoo people know what I'm talking about.

You just reminded me of some private email conversations I had with the designers at 3DFX when they were still making them.
Damn smart and talented guys.

---

