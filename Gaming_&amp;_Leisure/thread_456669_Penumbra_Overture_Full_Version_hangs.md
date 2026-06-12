---
title: "Penumbra Overture: Full Version hangs"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by cisforcojo on 2007-05-27
Anyone had any troubles with penumbra hanging? It's hung twice during the intro movie and another time AFTER the intro movie before you're in the ship. The screen just goes black and I have to restart X.

I've emailed the support but has anyone else had this problem???

The demo worked perfectly under Edgy Eft but now with Feisty and full version, it's not working.

---

### Post by Ruthenium on 2007-05-28
Well the game plays fine for me,  at least until the cave, I haven' played longer than that. You might want to check 

.frictionalgames/Penumbra Overture/Episode1/hpl.log

to see if anything helpful is written.

Maybe try to lower the settings ?

---

### Post by cisforcojo on 2007-05-28
Already did it! Lowered the settings that is. There are a lot of errors in hpl.log actually but nothing I can make use of. I wrote their support with it, which I really didn't wanna do because with $20 there's very little money to spend on customer service and still make a profit and I really want them to be successful. 

I thought it might be a driver issues but I checked glxinfo and the server and client vendor info is the same: SGI.
3d rendering is enabled (my video card is on their supported list)

Here is my hpl.log... don't know how to fix the errors!!!

```
-------- THE HPL ENGINE LOG ------------

Creating Engine Modules
--------------------------------------------------------
 Creating graphics module
 Creating system module
 Creating resource module
 Creating input module
 Creating sound module
 Creating physics module
 Creating ai module
 Creating scene module
--------------------------------------------------------

Initializing Resources Module
--------------------------------------------------------
 Creating resource managers
 Misc Creation
--------------------------------------------------------

Initializing Graphics Module
--------------------------------------------------------
 Init low level graphics
 Setting video mode: 800 x 600 - 32 bpp
 Init Glee...OK
 Setting up OpenGL
  Max texture image units: 8
  Max texture coord units: 8
  Two sided stencil: 0
  Vertex Buffer Object: 1
  Anisotropic filtering: 1
  Max Anisotropic degree: 16
  Multisampling: 1
  Vertex Program: 1
  Fragment Program: 1
  NV Register Combiners: 0
  NV Register Combiners Stages: 140443824
  ATI Fragment Shader: 0
 Creating graphic systems
  Creating Renderer2D
  Renderer2D created
  Creating Renderer3D
   Load Renderer3D gpu programs:
    Extrude
    Diffuse
    Fog
   Creating fog textures: Solid Additive Alpha 
   init sky box
  Renderer3D created
 Creating screen buffers size 800.000000 : 600.000000
 Creating programs
 CG ERROR : The program could not load.
ERROR: Couldn't create program 'PostEffect_Blur_Rect_fp.cg'
 CG ERROR : The program could not load.
ERROR: Couldn't create program 'PostEffect_Blur_2D_fp.cg'
 CG ERROR : The program could not load.
ERROR: Couldn't create program 'PostEffect_Bloom_fp.cg'
ERROR: Couldn't load 'PostEffect_Bloom_fp.cg'!
 CG ERROR : The compile returned an error.
 -----------------------------------
core/programs/PostEffect_Motion_fp.cg(32) : error C5013: profile does not support "for" statements and "for" could not be unrolled.
 -----------------------------------
Error loading: 'core/programs/PostEffect_Motion_fp.cg'!
ERROR: Couldn't create program 'PostEffect_Motion_fp.cg'
Dynamic loops in motion blur fp not supported, loading static instead.
  RendererPostEffects created
 Adding engine materials
--------------------------------------------------------

Initializing Sound Module
--------------------------------------------------------
 Initializing OpenAL.
  Trying to open audio device... Success!
  Device name: 
  OpenAL Version Supported: 1.0
  Number of channels: 32
--------------------------------------------------------

Initializing Game Module
--------------------------------------------------------
 Adding engine updates
 Initializing script functions
--------------------------------------------------------

User Initialization
--------------------------------------------------------
Trying to load vertex program!
Success!
--------------------------------------------------------

Game Running
--------------------------------------------------------
Loading collada for 'maps/level00_01_boat_cabin.dae' took: 302 ms
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
WARNING: Bone 'joint1' is not attached to skin!
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry for joint child '' is missing! Might be connected to bone.
WARNING: Geometry  joint parten '' is missing! Might be connected to bone.
ERROR: Child body 'joint1' for joint 'sjoint2' in mesh 'boat_dynamicparaffin.dae' does not exist!
ERROR: Cannot find sub entity 'parrafinlight_joint1' in mesh 'boat_dynamicparaffin.dae'
Start Num Of: 118
Start Num Of: 1
WARNING: Couldn't find start position 'link01'
Loading map 'level00_01_boat_cabin.dae' took: 5491 ms
```

---

### Post by cisforcojo on 2007-05-28
Hmm.. got it kinda working. Had to use the fglrx drivers.
Now, it hangs when I enter the mine.

EDIT: Solved! Had to disable Post Motion effects and now it's working perfectly.

---

### Post by Breepee on 2007-05-28
> **cisforcojo said:**
> Hmm.. got it kinda working. Had to use the fglrx drivers.
Now, it hangs when I enter the mine.

EDIT: Solved! Had to disable Post Motion effects and now it's working perfectly.

What graphicscard are you using?

---

### Post by cisforcojo on 2007-05-28
ATi Mobility Radeon X600.

It's on the list of supported cards.

---

### Post by Ripfox on 2007-05-30
Hangs here and freezes on intro movie after typing sequence. Intel i915 strikes again. Lowered all settings to no avail...

---

### Post by mozetti on 2007-05-30
For those having problems -- did you turn off the GL desktop?

I had a similar problem where the demo would hang during the intro movie, during the second set of typing on the cut-scene of the envelope on the doorstep. Even made a post on their forums. Then I remembered to turn off the GL Desktop/Compiz and it seemed to work.

---

### Post by Ripfox on 2007-05-30
I never run games with Beryl running...I have enough problems. :p

Well I found a few more things to lower, and this time I made it through the whole first movie, then it said "loading" and went black on me. Bah..why can't a guy with intel graphics get cut a break? :(

---

### Post by cisforcojo on 2007-05-30
Did you get the demo to run?

---

### Post by Ripfox on 2007-05-30
I am talking  about the demo. I definately won't buy it if it doesn't work.... EDIT: on MY box

---

### Post by cisforcojo on 2007-05-31
Yeah of course not. I think... you MIGHT be about of luck. If your card isn't supported you definitely might have some problems

---

### Post by Feba on 2007-05-31
I'm having similar problems with a 6200LE, so it's not an ATI problem I don't think.

---

### Post by mykrob on 2007-05-31
same here with an FX5700 Ultra 128MB. I opened the hatch near the beginning that you have to break the ice off to open, then got a black screen.. Had to restart the x-server as well..

---

### Post by Cannaregio on 2007-06-02
> **mykrob said:**
> same here with an FX5700 Ultra 128MB. I opened the hatch near the beginning that you have to break the ice off to open, then got a black screen.. Had to restart the x-server as well..

Just wait a moment. The "black screen" wird twilightish after a while :-)
No need to get scared or restart the x-server: just give it alittle time. It's a tag slow.

What I would like to find now is the complete game, somewhere on the web. 
The demo is interesting (albeit the commands are quite awkward) and I would like to try it out a little more and make sure that there are no bugs, before eventually buying it. 
Guess it will appear on rapidhsare or megaupload in a couple of weeks, so I'll just wait.

---

### Post by Footissimo on 2007-06-02
> **Cannaregio said:**
> What I would like to find now is the complete game, somewhere on the web. 
The demo is interesting (albeit the commands are quite awkward) and I would like to try it out a little more and make sure that there are no bugs, before eventually buying it. 
Guess it will appear on rapidhsare or megaupload in a couple of weeks, so I'll just wait.

Why not buy it and support the development of decent games on Linux - it's hardly an expensive game.

---

### Post by Ripfox on 2007-06-02
Really man...there  are not many games for Linux, so if it actually works on your box, BUY IT :eek:

---

### Post by justin whitaker on 2007-06-02
Did you patch?

[http://frictionalgames.com/forum/showthread.php?tid=1132](http://frictionalgames.com/forum/showthread.php?tid=1132)

---

### Post by Cannaregio on 2007-06-02
Let's see.. where did I say that I wouldn't buy it?
I said:

> **Cannaregio said:**
> What I would like to find now is the complete game, somewhere on the web. 
The demo is interesting (albeit the commands are quite awkward) and I would like to try it out a little more and make sure that there are no bugs, before eventually buying it. 
Guess it will appear on rapidshare or megaupload in a couple of weeks, so I'll just wait.

What I said, and repeat, is  also that it is not very clever to buy BUGGY software, and that it is always worth to try NOT ONLY the demo crippled versions they release BUT ALSO the complete cracked versions you can easily find on the web  BEFORE buying your games, since the game producing clowns often release games full of bugs and patch them, maybe, eventually, afterwards.

I'll add, moreover, that even if I bought some (few) software, usually for windows, before switching to GNU/Linux, I always found the cracked versions of the same software I bought to be BETTER than the original software I bought, coz they run without haslles/compelled CD in the drive/ protection and whatsnot.

So, once again: free software (as GNU/Linux software should be) is the best. And cracked software is waaaay better than legit software, for users, because it eliminates all the clowns' anti-copy tricks that annoy legit users (like me) and don't worry in the least thieves and crackers (that have of course cracked, and hence better, versions as the legit one we buy).

Should we buy software? No: in general we should use free software. 
Should we buy linux commercial games? Maybe, if we really like them and we find it is worth it. Can we judge if it is worth it from a crippled demo? No.

Hope I was more clear this time. I don't like to "buy" software, but I might do it if I like it. And I prefer to check before, not to complain afterwards.

My 0.00002 cents.

---

### Post by cisforcojo on 2007-06-02
I understand your point but I doubt you'll find many here who share the same view. I also don't think it will be well-received. 

As previously said, it's only $20. The support team is excellent and work very hard to solve any technical problems you might have.

---

### Post by Ripfox on 2007-06-02
> **Cannaregio said:**
> tricks that annoy legit users (like me)

lol...your talking about stealing it, what exactly is "legit" about that?

---

### Post by Feba on 2007-06-02
He's talking about trying more than a tiny bit before he sinks his money into it and gets burned.

---

### Post by Ripfox on 2007-06-02
Yes...he sounds like he's going to buy it. I take it back. :roll:

---

### Post by Footissimo on 2007-06-02
> **Cannaregio said:**
> Let's see.. where did I say that I wouldn't buy it?
I said:



What I said, and repeat, is  also that it is not very clever to buy BUGGY software, and that it is always worth to try NOT ONLY the demo crippled versions they release BUT ALSO the complete cracked versions you can easily find on the web  BEFORE buying your games, since the game producing clowns often release games full of bugs and patch them, maybe, eventually, afterwards.

I'll add, moreover, that even if I bought some (few) software, usually for windows, before switching to GNU/Linux, I always found the cracked versions of the same software I bought to be BETTER than the original software I bought, coz they run without haslles/compelled CD in the drive/ protection and whatsnot.

So, once again: free software (as GNU/Linux software should be) is the best. And cracked software is waaaay better than legit software, for users, because it eliminates all the clowns' anti-copy tricks that annoy legit users (like me) and don't worry in the least thieves and crackers (that have of course cracked, and hence better, versions as the legit one we buy).

Should we buy software? No: in general we should use free software. 
Should we buy linux commercial games? Maybe, if we really like them and we find it is worth it. Can we judge if it is worth it from a crippled demo? No.

Hope I was more clear this time. I don't like to "buy" software, but I might do it if I like it. And I prefer to check before, not to complain afterwards.

My 0.00002 cents.

Pathetic.

Others are being way to nice to you.  You are encouraging the piracy of a game that is made by a tiny developer, one that has been helpful enough to make a linux port, make a demo available AND to only charge a tenner for a full (and [decent](http://uk.gamespot.com/pc/action/penumbra/index.html?q=penumbra&tag=result;title;0)) game.  Now, I don't really give a **** if you pirate Windows games - the market is big and development massive on that platform..but on linux we only have a handful of people who are willing to develop games for linux or make ports.  With people like you, this will only get worse and any people that do try to make an effort with porting games will end up like [this](http://www.lokigames.com/).

Oh and go and [look up](http://www.google.com) the meaning of free libre/speech software before trying to use it to justify your behaviour, whilst most of here would promote the use of **FLOSS** software, only the daftest would suggest that the piracy of commercial linux software is justifiable.

Hopefully you'll be going back to Windows soon.

---

### Post by Feba on 2007-06-02
Again, if you read what he wrote, he clearly states that he intends to buy the game AS LONG AS IT WORKS, which can't be told by how short the demo version is. 


>  Should we buy linux commercial games? Maybe, if we really like them and we find it is worth it. Can we judge if it is worth it from a crippled demo? No.

---

### Post by cisforcojo on 2007-06-03
Perhaps a redesign of the demo is in order. I don't believe MOST would pay for software after having it for free. They'd use their money towards something new. That being said, if you truly feel that you can't get a feel for a game from a 'crippled' demo. Possibly their demo isn't designed well. Personally, I really liked the DEMO and it made me want to play the full version as it should. To each his own. However noble your intentions, I feel that most wouldn't do the same (get cracked software and then buy if it is worthy) so please, if you buy it, don't distribute.

---

### Post by Ripfox on 2007-06-03
I can't believe someone here actually BELIEVES this dude is gonna buy it after he gets it for free...wow. I personally think he didn't quite know where he was, and was looking for a link to a torrent or something...

---

### Post by Feba on 2007-06-03
He didn't ask for a torrent, so he likely doesn't care about us helping him, he's just making his intentions clear.

---

### Post by Cannaregio on 2007-06-03
> **ripfox said:**
> I can't believe someone here actually BELIEVES this dude is gonna buy it after he gets it for free...wow. I personally think he didn't quite know where he was, and was looking for a link to a torrent or something...

I think you must be -basically- unable to read. That's not a problem for nobody, unless you answer unpolitely to somebody you didn't even care to read, as you seem indeed inclined to do. In fact my original posting was an answer to the subject of this thread "<i>Penumbra Overture: Full Version hangs</i>": helping mykrob
> **mykrob said:**
> same here with an FX5700 Ultra 128MB. I opened the hatch near the beginning that you have to break the ice off to open, then got a black screen.. Had to restart the x-server as well..
telling him to wait a moment: his problem is just due to the slowness of the software in object. 
But we are now into your delirium delusions of "*Gosh, pirating software is really really naughty*". 
So one more answer of mine is - I deem - still necessary.

Noone but silly morons need torrents (or would ask for your help) to find pirated sofware. Should thou want to fetch pirated sofware, learn that it is much quicker, and effectiver, to find it on the fly through simple google queries. Alternatively,  if you really want to wget pirated copies the easiest way, look onto one of those zillion rapidshare and megaupload alike repositories THAT ARE MADE for spreading pirated stuff and porn (and get money from morons that believe that paying for a premium account there is worth it). 
Torrents? Nope: torrents are ** too slow** for an educated webcitizien's tastes.

Again you did not read, and don't understand. Of course I buy the sofware I use (note that what you actually believe or not believe is fully irrelevant: this is what I do, point). 
Fortunately there is rarely some sofware I would use that doesn't have a (often better) free alternative version :-)
So, again: I prefer free software, but I might accept - and eventually buy - even commercial software... **if I really like it**. 
How do I know if I like it or not? From a demo? No. I have been burned much too much in the past. Never again. Demos are always made _for the sales pitch_, and only for that. Don't trust demos, they bark a lot and then bite your fingers.

So: how do we know if we can have some use for some software? 
**We try it thoroughly out, duh**. And the web offers us the possibility to do it. Any software, for any operating system, complete, cracked and regged BEFORE you can even find it in any shop: a paradise of testing and checking possibilities. It's up to your morality to buy that software after having tested it. Many might not care, I do. But the fact that you can test it _is a great facility that the web offers_, and I don't see why we shouldn't use it.

Moreover, again, I repeat that there is an _added advantage in using cracked versions of the very sofware you'll buy later_: cracked copies are BETTER than the legit ones, they run with less hassles, they don't compel you to stick a CD in the drive and so on. So I have good outstanding software I bought ([combat mission ]("http://www.battlefront.com/products/cmak/cmak_bundle.html")is a "gaming" example already made) that is still here in its plastic sealed box, I guess I could even return it... but I won't. The game is so good that they deserved the money :-)

Anyway: again: noway I'm gonna buy software just for the apparent frills or for the look of the box. Without having tested it? Nossir: in most cases you quickly realize that it's just utter crap full of bugs.

I treat commercial sofware EXACTLY as I treat free software: I check it thoroughly in its full version and then I decide if I buy and keep it or not.

Uff... you know what? The real annoying thing is that you have to spend time to clear things that should be obvious to anyone  just because some hyper-"politically correct" dude  ("*What? You can easily find pirated copies of any software whatsoever? Everywhere? Anytime you like? At once? Oh gosh. Don't say such blasphemies out loud: this is really really bad!!*") has been brain-conditioned into jerking off every time he suspects somebody might be insulting the holy patents of the commercial slavemasters.

---

### Post by Ripfox on 2007-06-03
That was the longest self-justification for ripping off a small company that decided to do your ungrateful a** a favor by developing a game for Linux I have ever heard. (and you talk about others being delusional...if your going to rip the game off, at least admit it to yourself) Once again, thanks for ruining our scene, people like you make this ( [http://www.lokigames.com/](http://www.lokigames.com/) ) kind of end result possible...

Please go back to your world of pirated proprietary software and leave us alone?

Pretty pleeease?

---

### Post by cisforcojo on 2007-06-04
> Should** thou** want to fetch pirated sofware, learn that it is much quicker, and effectiver, to find it on the fly through simple google queries.

Haha alright, Shakespeare.

You have a very un-Ubuntu attitude. I bite my thumb at you, sir.

In any case, this thread should definitely be closed.

---

### Post by fktt on 2007-06-04
hmm.. indeed the demo hangs for me too at the intro there, im running on fx5200 :(

and as for the fella:
> **Cannaregio said:**
>  Nope: torrents are ** too slow** for an educated webcitizien's tastes.
"educated" webcitizen would know to choose a torrent with enough seeds and/or open(redirect) his/her ports ^^''

---

### Post by Ripfox on 2007-06-05
I second the "close this thread" sentiment.

---

### Post by aidanr on 2007-06-05
before it is closed, just one more thing to try for anyone that's having trouble with the game hanging, some people have reported that setting UseThreading to false in ~/.frictionalgames/Penumbra\ Overture/Episode\ 1/settings.cfg has helped

---

### Post by Ripfox on 2007-06-05
Ah hah! I wil try that. As long as this thread gets back on topic...it will be useful :)

---

### Post by Feba on 2007-06-05
It worked, but it was horrible performance once I was in game. Oh well.

---

### Post by Ripfox on 2007-06-06
No good here...got me through the movie at the beginning then just sat on a blank screen for 10 min.

---

### Post by cisforcojo on 2007-06-06
ripfox: 

You sure you've got the correct drivers installed?
Thats what it did for me when I wasn't using fglrx.

---

### Post by Ripfox on 2007-06-06
I have intel graphics and I am using the latest intel driver thats stable. I am just screwed again by this laptop's graphics...I'll be more careful next time in choosing. But, VO works, OA works and Nexuiz works, along with Padman, so I am pretty set I guess :)

No Regnum, no Penumbra, SLOW Planeshift...

---

