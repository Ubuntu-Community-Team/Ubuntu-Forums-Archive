---
title: "java classic RPG under development"
date: 2007-06-29
forum: Gaming &amp; Leisure
---

### Post by timong on 2007-06-29
I am currently developing a brand new open-source classic role playing game framework and engine written in Java under LGPL license. It aims at legacy of games like Wizardry 7, EOB, classic Might and Magic. It's openGL, runs under Java Runtime Environment. So Linux is completely supported. :-) Soon the project will be in need of low polygon beasts, plants and humanoid beings too, and later Java coders will be welcome too. 

Visit the developer blog to have a taste of the development, and many screenshots:

[http://jcrpg.blogspot.com]("http://jcrpg.blogspot.com")

The source is in the SVN repository of sourceforge.net and the first (very basic :-) ) snapshot can be found too at the project's SF site:

[http://javacrpg.sf.net]("http://javacrpg.sf.net")

You will need a Sun JRE 1.5 or later to run it, and opengl HW acceleration too!

cheers,
T.

P.S.: Contributions can be easily done at [http://forum.freegamedev.net/index.php?t=index&cat=9](http://forum.freegamedev.net/index.php?t=index&cat=9)

Latest release: [http://ubuntuforums.org/showpost.php?p=9429174&postcount=121](http://ubuntuforums.org/showpost.php?p=9429174&postcount=121)

[img]http://bp0.blogger.com/_f57_nB05Gno/SD6jgMfk6PI/AAAAAAAAArA/jd7EnvXEB0o/s200/sheet.jpg[/img]
[img]http://2.bp.blogspot.com/_f57_nB05Gno/SJ9IlWwTApI/AAAAAAAAAu4/63P70njr5hk/s200/SimpleGameScreenShot.png[/img]
[img]http://bp0.blogger.com/_f57_nB05Gno/SJJEV8nJ6qI/AAAAAAAAAuQ/Tl1ZPPZtzLY/s200/house-comp2.jpg[/img]

---

### Post by Anonymvs on 2007-06-29
Hmmm, looks interesting.  I'll check it out, thanks.  Good luck with development!

---

### Post by lunetter on 2007-06-29
looks nice. I hope you will pull it to the end!

---

### Post by timong on 2007-06-29
:D Thanks for the kind words! 
Hope to see your comments and ideas now and later!

[IMG]http://bp3.blogger.com/_f57_nB05Gno/RoWEVwTVxbI/AAAAAAAAAGc/XE9rnHHqfps/s1600-h/floraE2.jpg[/IMG]

---

### Post by timong on 2007-06-30
Check out the latest snapshot (2007-06-30) on [http://sourceforge.net/project/showfiles.php?group_id=197331 ]("http://sourceforge.net/project/showfiles.php?group_id=197331").

"Fixes in 3D engine, walk restrictions implemented, Flora generated on all geographic place type (Mountains,Plains, Forests), new 3d models (mostly trees)"

---

### Post by charlieg on 2007-07-01
I've been covering JCRPG on [Free Gamer]("http://freegamer.blogspot.com/") for a few weeks now.  It's a very interesting project. :)

---

### Post by timong on 2007-07-17
[http://sourceforge.net/project/showfiles.php?group_id=197331](http://sourceforge.net/project/showfiles.php?group_id=197331) New snapshot release available. Checkout:

New plant model collection, day-night cycle with orbiters Sun and Moon, many changes in 3D core and render part, use of mipmapping for the textures.

---

### Post by Beren Camlost on 2007-07-17
Looks nice, and installation on my Win XP system went flawless. While FPS is mostly around 90, I do run into some "lag", especially when turning left or right. Taking into account that it is still in development I don't mind that much :)

I didn't come across any UI but I take it that isn't implemented yet?

All in all it's a very interesting project (Was/is a huge fan of the EOB series, especially EOB2). I do hope you pull it off and get it where you want to. Kudos :D

---

### Post by timong on 2007-07-17
No UI implemented yet! Still with some lags in the code it has been optimized a bit since that release too so the next release maybe a bit faster in respect of turning around in the game too...we will see ! :-D

Thanks for testing!! :-)

---

### Post by srsairbags on 2007-07-17
is it true that d3d is better than onenGL ? ? ?

---

### Post by charlieg on 2007-07-17
I have an idea for the UI btw - let me know when you are closer to starting on it. ;)

---

### Post by Dimitriid on 2007-07-17
Looks nice. By the way I havent seen much in the way of native single player rpgs for Linux, any of you can recommend some? ( All styles from old school turn based to diablo clickfests are welcome )

---

### Post by timong on 2007-07-17
> **srsairbags said:**
> is it true that d3d is better than onenGL ? ? ?

For what? AFAIK opengl is more professional, more for business use, d3d is said to be better for games. Anyway d3d is not for Java or multiplatform, and not really for native linux, so that's why jcrpg is opengl project! And as such, you may judge, is it worth to play even if it is not in d3d. :D

---

### Post by timong on 2007-07-17
> **Dimitriid said:**
> Looks nice. By the way I havent seen much in the way of native single player rpgs for Linux, any of you can recommend some? ( All styles from old school turn based to diablo clickfests are welcome )

Very oldschool is Devil Whiskey. It's commercial but native! Scourge is another cool in development h'n'slash rogue-like RPG. 

Yeah, and thanks for your kind words! :)

---

### Post by timong on 2007-07-17
> **charlieg said:**
> I have an idea for the UI btw - let me know when you are closer to starting on it. ;)

I will be eager to hear about your ideas! :-D I am already thinking a bit about it. One idea is that there will be much more text output in a box than it is usual in modern games! (Especially because JCRPG basically is not aimed to be an action rpg, rather an RPG with more time to think and read too, just like Wiz7 was. I liked it much! :D)

---

### Post by shynko on 2007-07-17
this sounds great I planned on learning how to use blender so if I get comfortable with it I'll contribute
some which sorry the noob in me is showing  :oops:  how do I contribute.

---

### Post by timong on 2007-07-18
> **shynko said:**
> this sounds great I planned on learning how to use blender so if I get comfortable with it I'll contribute
some which sorry the noob in me is showing  :oops:  how do I contribute.

Hey, Shynko, if want to contribute something, just come over [http://jcrpg.blogspot.com](http://jcrpg.blogspot.com) , you can post there comments easily, and we can talk about this which I will read immediately. Contribution is as easy as sending me some blender files, if you have something ready. :-) And yeah, I am a beginner in blender too, so don't be afraid to show what you are capable of! And don't forget as soon as you contribute you will get into the Hall Of Fame of JCRPG too! :-D

---

### Post by Nkari on 2007-07-18
So this is going to be a sort of toolkit for people to build RPGs with? Sort of like the level editor that came with neverwinter nights or are you building a full game, looks like a cool project regardless.

The JMonkey engine demo on you tube clip looks very good too, the fantasy game in it made me think World of Warcraft.

Guess it is time to learn how to use blender.

---

### Post by timong on 2007-07-18
Yeah, jcrpg will be a framework/engine like toolkit for building classic style RPGs, and at the same time we are providing a demo like prototype game with the toolkit itself. Later when the projects gets more features, we plan to release a demo game, and finally one first real, long story, big world game too...so far these are plans.

It's important to see, that this classic style RPG may contain a lot of different subframework projects, meaning that it may be containing a framework part for sci-fi games, a part for fantasy games, one combat engine for ad and d, one combat engine for Wiz7 like combat... these are examples, but in the future I wish many aspects of RPG can come true in the jcrpg framework, and so many new games can build out of it too.

---

### Post by shynko on 2007-07-18
> **timong said:**
> Hey, Shynko, if want to contribute something, just come over [http://jcrpg.blogspot.com](http://jcrpg.blogspot.com) , you can post there comments easily, and we can talk about this which I will read immediately. Contribution is as easy as sending me some blender files, if you have something ready. :-) And yeah, I am a beginner in blender too, so don't be afraid to show what you are capable of! And don't forget as soon as you contribute you will get into the Hall Of Fame of JCRPG too! :-D


thanks :) unfortunately I  don't have anything ready for you as of now but was wondering what do you need the most right now I was thinking of just trying some plants and stuff out and seeing if i could get something that didn't look horrible  :lolflag:
P.S(my display name is harek :D )

---

### Post by Nkari on 2007-07-18
Awesome, it could well be to computers based RPGs what Hero System or GURPS is to pen and paper based RPGs.

---

### Post by timong on 2007-07-19
> **shynko said:**
> thanks :) unfortunately I  don't have anything ready for you as of now but was wondering what do you need the most right now I was thinking of just trying some plants and stuff out and seeing if i could get something that didn't look horrible  :lolflag:
P.S(my display name is harek :D )

Mostly the project will be in need of low-poly animals/humanoids in the near future...they are a big job to create in blender too... but to make it more easy static (not animated) models will suffice too, so if you have the mood to start experimenting with it, please start with animals/humanoids, or simple everyday objects like furniture and such. But it's up to you to decide.

Plants will be covered mostly with ngplant.sf.net 's application, a very useful tool for such purpose.

---

### Post by timong on 2007-07-19
> **Nkari said:**
> Awesome, it could well be to computers based RPGs what Hero System or GURPS is to pen and paper based RPGs.

We will see! :-) I am wanting to create a framework where such things can come true easily, so changeable combat system will be a goal in some point of the development, and also the way to provide ways for subframeworks to fit into the whole.

---

### Post by shynko on 2007-07-19
> **timong said:**
> Mostly the project will be in need of low-poly animals/humanoids in the near future...they are a big job to create in blender too... but to make it more easy static (not animated) models will suffice too, so if you have the mood to start experimenting with it, please start with animals/humanoids, or simple everyday objects like furniture and such. But it's up to you to decide.

Plants will be covered mostly with ngplant.sf.net 's application, a very useful tool for such purpose.

thanks I can hopefully have my first model for the game by the end of the week I'm thinking of a giant wasp like creature  :)

---

### Post by timong on 2007-07-19
> **shynko said:**
> thanks I can hopefully have my first model for the game by the end of the week I'm thinking of a giant wasp like creature  :)

I hope you will succeed in it! I can't say how much I appreciate your enthusiasm, hope to see your results! 

I do not have currently the time for much modeling in blender, I am still coding the engine in my spare time as fast and reliable as possible! :-) So good luck with your work!



I am subscribed now to this thread in email, so post any news here, I will read it regularly.

---

### Post by shynko on 2007-07-19
> **timong said:**
> I hope you will succeed in it! I can't say how much I appreciate your enthusiasm, hope to see your results! 

I do not have currently the time for much modeling in blender, I am still coding the engine in my spare time as fast and reliable as possible! :-) So good luck with your work!



I am subscribed now to this thread in email, so post any news here, I will read it regularly.

ok thats a good idea. since this thread is dead to the public lol. 

yeah It's probably better for you to focus on having coding done than to have a milloin models with no place to put them.

also i tried to make that wasp thing last night and it looked like it was  1-bit lol

so I was wondering how do you want me to send you blend files  :confused:

---

### Post by timong on 2007-07-19
> **shynko said:**
> ok thats a good idea. since this thread is dead to the public lol. 

yeah It's probably better for you to focus on having coding done than to have a milloin models with no place to put them.

also i tried to make that wasp thing last night and it looked like it was  1-bit lol

so I was wondering how do you want me to send you blend files  :confused:

I will send you a private message on the forum right now with my email address. You can send things there! :)

---

### Post by shynko on 2007-07-19
ok

---

### Post by timong on 2007-07-19
And again! New snapshot pre-alpha release at sf.net: [http://sourceforge.net/project/showfiles.php?group_id=197331](http://sourceforge.net/project/showfiles.php?group_id=197331) ! Optimizations, configuration file added for tuning, new models, and ground flora.

---

### Post by shynko on 2007-07-20
hey I've been pressed for time lately  and wasn't able to do much modeling  lately but I did get a bad dagger together I am gonna try to put some textures on it late tommorow night. if you wanna  see the model or have the time to put the textures on yourself( I'm still learning about textures) then just post telling me you want me to email it to you :)

---

### Post by timong on 2007-07-21
> **shynko said:**
> hey I've been pressed for time lately  and wasn't able to do much modeling  lately but I did get a bad dagger together I am gonna try to put some textures on it late tommorow night. if you wanna  see the model or have the time to put the textures on yourself( I'm still learning about textures) then just post telling me you want me to email it to you :)

Hello! Of coure I'm eager to see it! Send it anytime! :-) If problem with uv texture mapping, search google for the quickie blender tutorial. I learned it from that source.

---

### Post by shynko on 2007-07-21
ok I will email it to you then.

---

### Post by shynko on 2007-07-21
I've emailed it  hope you get it....

---

### Post by timong on 2007-07-24
> **shynko said:**
> I've emailed it  hope you get it....

Yeah, i've got it it was one cool blade to start with! :-) Thanks much!

Here I will link a demo video on youtube for ppl who want to check it out in motion too without downloading the game itself:

[http://www.youtube.com/watch?v=jeO5lFAk1UU](http://www.youtube.com/watch?v=jeO5lFAk1UU)

---

### Post by Cappy on 2007-07-24
That's a pretty impressive java engine. Color me impressed if your character/monster models look as good!

---

### Post by timong on 2007-07-24
> **Cappy said:**
> That's a pretty impressive java engine. Color me impressed if your character/monster models look as good!

Thanks! No characters monsters yet, and maybe they won't be that nice in the first time. :) Until more people like Shynko joins the project, willing to contribute to an opensource game. :) We will try our best! :)

---

### Post by timong on 2007-07-29
[http://sourceforge.net/project/showfiles.php?group_id=197331](http://sourceforge.net/project/showfiles.php?group_id=197331)

New release, with many new features like billboarded grass, shadows for some objects, bloom effect, optimizations, more config options. Check out! :-)

---

### Post by timong on 2007-07-30
If interested in contributing to this opensource role playing game project visit: [http://freegamer.schattenkind.net/index.php?t=msg&th=30&start=0](http://freegamer.schattenkind.net/index.php?t=msg&th=30&start=0)

---

### Post by Beren Camlost on 2007-08-03
Tried with both Kubuntu Feisty and Windows XP, smooth :)

---

### Post by timong on 2007-08-03
> **Beren Camlost said:**
> Tried with both Kubuntu Feisty and Windows XP, smooth :)

Wow,Great! Thanks for replying! 

Which version? The download or from SVN? Currently heavy work on optimizations, and I might say that there are big boosts of FPS especially without bloom and shadow! New release will come soon with optimizations.

---

### Post by Beren Camlost on 2007-08-03
The lastest version's been tried on both platforms, though various earlier version haven been tried on either platform individually. Just downloaded from SourceForge and go! :guitar:

---

### Post by timong on 2007-08-03
Great! :-D Thanks for reporting... hopefully next release will be even smoother and better looking! :)

---

### Post by timong on 2007-08-10
new release of java classic rpg, details:

[http://jcrpg.blogspot.com/2007/08/hooray-for-bz2-release.html](http://jcrpg.blogspot.com/2007/08/hooray-for-bz2-release.html)

download:

[http://sourceforge.net/project/showfiles.php?group_id=197331](http://sourceforge.net/project/showfiles.php?group_id=197331)

---

### Post by timong on 2007-08-12
> **timong said:**
> new release of java classic rpg, details:

[http://jcrpg.blogspot.com/2007/08/hooray-for-bz2-release.html](http://jcrpg.blogspot.com/2007/08/hooray-for-bz2-release.html)

download:

[http://sourceforge.net/project/showfiles.php?group_id=197331](http://sourceforge.net/project/showfiles.php?group_id=197331)

There is an optimization patch released today downloadable at the same link.

Blogpost: [http://jcrpg.blogspot.com/2007/08/patch-it-to-go.html](http://jcrpg.blogspot.com/2007/08/patch-it-to-go.html)

---

### Post by timong on 2007-08-27
youtube demo video: [http://youtube.com/watch?v=KU_QAK2Q3X8](http://youtube.com/watch?v=KU_QAK2Q3X8)

---

### Post by Cappy on 2007-08-27
That's pretty fracking impressive! =)

I have to ask though:
Why are the trees redrawing as you get closer? There was a bug like that in Oblivion (I think it was fixed).
Also, why is the view distance so low?

This project reminds me a lot of an Ultima project I know of (because the graphics look a bit similar):
[http://www.cfkasper.de/ultima/](http://www.cfkasper.de/ultima/)

---

### Post by timong on 2007-08-27
> **Cappy said:**
> That's pretty fracking impressive! =)

I have to ask though:
Why are the trees redrawing as you get closer? There was a bug like that in Oblivion (I think it was fixed).
Also, why is the view distance so low?



Trees are LOD models, and sorrowfully they look a bit different on each Level of detail. :-) This may be helped later, but for a (possibly long) while it will look like that. :-)
view distance is set a bit lower for the fraps capture (set to view distance 24), but the view distance will be not too much bigger anyway, I use view distance 30 on a 6200Go. On my other test machine (8800GTS, dual core) I use a view distance of 40 mostly. Maybe some other day there will be some generated far panorama to trick you to believe a bigger view distance. :-)

Glad you like it! :-)

EDIT: And there's a view distance trick there, internal parts are displayed on a low view distance  when view from outside place, so when you enter the internal parts, the cave, you will have a 4 time bigger view distance inside.

---

### Post by timong on 2007-08-27
That ultima thing looks pretty cool...wow, much prettier than jcrpg. :-) Anyway I hope jcrpg will have some fans as well later. :biggrin:

---

### Post by xen on 2007-08-27
Excellent looking project. Is the world going to be set on a 'flat' piece of terrain, or are we going to see swooping hills and great draw distances :)

---

### Post by timong on 2007-08-27
> **xen said:**
> Excellent looking project. Is the world going to be set on a 'flat' piece of terrain, or are we going to see swooping hills and great draw distances :)

It will be mostly flat, like it is a successor of old style classic rpgs, with the 45 degree steeps of the mountains already present. The great draw distance can be achieved maybe later with some new tricks and more optimization.

---

### Post by timong on 2007-09-03
New release:

[http://jcrpg.blogspot.com/2007/09/cave-batch-and-shader.html](http://jcrpg.blogspot.com/2007/09/cave-batch-and-shader.html)

Files:

[http://sourceforge.net/project/showfiles.php?group_id=197331](http://sourceforge.net/project/showfiles.php?group_id=197331)

---

### Post by Jiiprah on 2007-09-03
Is this a single player RPG or an MMORPG?

---

### Post by timong on 2007-09-03
> **Jiiprah said:**
> Is this a single player RPG or an MMORPG?

Singleplayer, definitely. :-)

---

### Post by Nkari on 2007-09-03
Hence the word classic in the title.

---

### Post by timong on 2007-09-27
FYI: project moved from LGPL to GPLv3 License.

---

### Post by muski on 2007-09-28
i downloaded this thing ... how am i supposed to run it ??
there seems to be no executable ... 
i have Sun JRE 1.5

---

### Post by timong on 2007-09-28
Have you tried the batch file (jcrpg.bat)? Or under Linux: jcrpg.sh. It's not too complicated.

---

### Post by timong on 2007-10-07
New pre-alpha test release available:

Headlines: bumped terrain tiles, river and lake water geographies, optional far view mode were added. JME's water render pass applied on water surface with reflection (optional, switch off for less stress on GPU/CPU). Grass is added to the mountain slopes too and the grass vertex shader is improved.

[http://jcrpg.blogspot.com/2007/10/flowing-to-release.html](http://jcrpg.blogspot.com/2007/10/flowing-to-release.html)

[http://sourceforge.net/project/showfiles.php?group_id=197331](http://sourceforge.net/project/showfiles.php?group_id=197331)

---

### Post by timong on 2007-10-20
new release:

[http://jcrpg.blogspot.com/2007/10/minor-special-release.html](http://jcrpg.blogspot.com/2007/10/minor-special-release.html)

highlights:

grass vertex shader fix for intel integrated video card low temp limit, new animal models (gorilla, fox etc.), advanced lake with depth, waters with better looking coast, fix for small billboarding bug added

---

### Post by timong on 2007-12-02
New pre-alpha test release available:

Headlines:

- UI base elements were added: load icon, compass, time meter, world map, HUD panel.
- Internal Flora is now configurable through FloraGenerators. Example internal flora in the Cave.
- Initial version of the World Generator is added. The World Map UI element shows a world generated by it.
- Updated JME libraries from CVS.

[http://jcrpg.blogspot.com/2007/12/base-ui-release.html](http://jcrpg.blogspot.com/2007/12/base-ui-release.html)

Download:

[https://sourceforge.net/project/showfiles.php?group_id=197331](https://sourceforge.net/project/showfiles.php?group_id=197331)

---

### Post by matthewcraig on 2007-12-02
Ubuntu needs more RPGs, for sure!  Thanks for taking the time to support Linux gaming, and good luck with the upcoming alpha release.

---

### Post by Beren Camlost on 2007-12-02
The pre-alpha release won't run in Windows. Give me a black screen after selecting resolution then quits. Will try with Kubuntu later and my Debian installation once I get it to boot.

---

### Post by timong on 2007-12-03
> **Beren Camlost said:**
> The pre-alpha release won't run in Windows. Give me a black screen after selecting resolution then quits. Will try with Kubuntu later and my Debian installation once I get it to boot.

Are you using Sun JVM or the gjc version? You must use the Sun JVM. Please paste here your console log, there must be some error in it. Thanks!

---

### Post by Beren Camlost on 2007-12-03
> **timong said:**
> Are you using Sun JVM or the gjc version? You must use the Sun JVM. Please paste here your console log, there must be some error in it. Thanks!

Yes, Sun Java for all my Java needs ;)

Terminal output after selecting resolution:

```
03.des.2007 17:30:31 class com.jme.renderer.lwjgl.LWJGLTextureRenderer render(Spatial, Texture)
SEVERE: Exception
java.lang.RuntimeException: FrameBuffer: 2, has caused a GL_FRAMEBUFFER_UNSUPPORTED_EXT exception
        at com.jme.renderer.lwjgl.LWJGLTextureRenderer.checkFBOComplete(Unknown
Source)
        at com.jme.renderer.lwjgl.LWJGLTextureRenderer.render(Unknown Source)
        at com.jme.renderer.lwjgl.LWJGLTextureRenderer.render(Unknown Source)
        at org.jcrpg.threed.jme.effects.WaterRenderPass.renderReflection(WaterRe
nderPass.java:486)
        at org.jcrpg.threed.jme.effects.WaterRenderPass.doRender(WaterRenderPass
.java:342)
        at com.jme.renderer.pass.Pass.renderPass(Unknown Source)
        at com.jme.renderer.pass.BasicPassManager.renderPasses(Unknown Source)
        at org.jcrpg.threed.J3DCore.simpleRender(J3DCore.java:3410)
        at org.jcrpg.threed.J3DCore.render(J3DCore.java:3467)
        at org.jcrpg.threed.J3DCore.updateDisplay(J3DCore.java:3008)
        at org.jcrpg.threed.J3DCore.render(J3DCore.java:1639)
        at org.jcrpg.threed.J3DCore.simpleInitGame(J3DCore.java:3368)
        at com.jme.app.BaseSimpleGame.initGame(Unknown Source)
        at org.jcrpg.threed.J3DCore.initGame(J3DCore.java:1354)
        at com.jme.app.BaseGame.start(Unknown Source)
        at org.jcrpg.threed.J3DCore.initCore(J3DCore.java:1156)
        at org.jcrpg.apps.Jcrpg.start(Jcrpg.java:170)
        at org.jcrpg.apps.Jcrpg.main(Jcrpg.java:57)
03.des.2007 17:30:31 class com.jme.renderer.lwjgl.LWJGLTextureRenderer render(Sp
atial, Texture)
SEVERE: Exception
java.lang.RuntimeException: FrameBuffer: 2, has caused a GL_FRAMEBUFFER_UNSUPPOR
TED_EXT exception
        at com.jme.renderer.lwjgl.LWJGLTextureRenderer.checkFBOComplete(Unknown
Source)
        at com.jme.renderer.lwjgl.LWJGLTextureRenderer.render(Unknown Source)
        at com.jme.renderer.lwjgl.LWJGLTextureRenderer.render(Unknown Source)
        at org.jcrpg.threed.jme.effects.WaterRenderPass.renderRefraction(WaterRe
nderPass.java:520)
        at org.jcrpg.threed.jme.effects.WaterRenderPass.doRender(WaterRenderPass
.java:348)
        at com.jme.renderer.pass.Pass.renderPass(Unknown Source)
        at com.jme.renderer.pass.BasicPassManager.renderPasses(Unknown Source)
        at org.jcrpg.threed.J3DCore.simpleRender(J3DCore.java:3410)
        at org.jcrpg.threed.J3DCore.render(J3DCore.java:3467)
        at org.jcrpg.threed.J3DCore.updateDisplay(J3DCore.java:3008)
        at org.jcrpg.threed.J3DCore.render(J3DCore.java:1639)
        at org.jcrpg.threed.J3DCore.simpleInitGame(J3DCore.java:3368)
        at com.jme.app.BaseSimpleGame.initGame(Unknown Source)
        at org.jcrpg.threed.J3DCore.initGame(J3DCore.java:1354)
        at com.jme.app.BaseGame.start(Unknown Source)
        at org.jcrpg.threed.J3DCore.initCore(J3DCore.java:1156)
        at org.jcrpg.apps.Jcrpg.start(Jcrpg.java:170)
        at org.jcrpg.apps.Jcrpg.main(Jcrpg.java:57)
03.des.2007 17:30:31 class org.jcrpg.threed.J3DCore start()
SEVERE: Exception in game loop
org.lwjgl.opengl.OpenGLException: Invalid framebuffer operation (1286)
        at org.lwjgl.opengl.Util.checkGLError(Util.java:53)
        at org.lwjgl.opengl.Display.swapBuffers(Display.java:591)
        at org.lwjgl.opengl.Display.update(Display.java:609)
        at com.jme.renderer.lwjgl.LWJGLRenderer.displayBackBuffer(Unknown Source
)
        at org.jcrpg.threed.J3DCore.updateDisplay(J3DCore.java:3012)
        at org.jcrpg.threed.J3DCore.render(J3DCore.java:1639)
        at org.jcrpg.threed.J3DCore.simpleInitGame(J3DCore.java:3368)
        at com.jme.app.BaseSimpleGame.initGame(Unknown Source)
        at org.jcrpg.threed.J3DCore.initGame(J3DCore.java:1354)
        at com.jme.app.BaseGame.start(Unknown Source)
        at org.jcrpg.threed.J3DCore.initCore(J3DCore.java:1156)
        at org.jcrpg.apps.Jcrpg.start(Jcrpg.java:170)
        at org.jcrpg.apps.Jcrpg.main(Jcrpg.java:57)
ENGINE TERMINATING
]ENGINE TERMINTATED
```

---

### Post by timong on 2007-12-03
Hmm. What video card are you using? Maybe trying to edit config.properties and switch WATER shader to false will help you! How long is it since you upgraded your video driver?

---

### Post by timong on 2007-12-03
> **matthewcraig said:**
> Ubuntu needs more RPGs, for sure!  Thanks for taking the time to support Linux gaming, and good luck with the upcoming alpha release.

Thanks! :)

---

### Post by Beren Camlost on 2007-12-07
> **timong said:**
> Hmm. What video card are you using? Maybe trying to edit config.properties and switch WATER shader to false will help you! How long is it since you upgraded your video driver?
 
My drivers were, at the date of testing, the latest official Nvidia drivers (163.75). Later the same day I reinstalled some older drivers to be able to play Neverwinter Nights again (latest Nvidia driver for Windows is somewhat buggy), and this time jcrpg would stay up long enough for me to get a glimpse of the UI ;)

More importantly, it ran flawless in Kubuntu Feisty straight out of the box :D Will try with my amd64 installation too.

Edit: Oh, my graphics card is a 7800GT, almost 2 years old ;)

---

### Post by Adrian.C on 2007-12-08
Hi

I would like to test the game, but I've got an exception when I try to launch it, maybe you can help me.

I'm using Dapper, with the Sun Jvm 5.0 :

```
$ java -version
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)Java HotSpot(TM) Client VM (build 1.5.0_13-b05, mixed mode, sharing)
```

This is the trace of the exception when launching the sh script :

```
0 ms
2 ms
SEALEV PLAIN:5
MOUNTAIN SIZE = 1
!!!!!!!!!! VIEW POS: 50
8 déc. 2007 11:44:16 class org.jcrpg.threed.J3DCore start()
GRAVE: Exception in game loop
java.lang.UnsatisfiedLinkError: /home/adrian/javarpg/jcrpg-20071202/lib/liblwjgl.so: Can't load IA 32-bit .so on a IA 32-bit platform
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.lwjgl.Sys$1.run(Sys.java:75)
        at java.security.AccessController.doPrivileged(Native Method)        at org.lwjgl.Sys.doLoadLibrary(Sys.java:68)
        at org.lwjgl.Sys.loadLibrary(Sys.java:84)
        at org.lwjgl.Sys.<clinit>(Sys.java:101)
        at org.lwjgl.opengl.Display.<clinit>(Display.java:111)
        at com.jme.system.lwjgl.LWJGLPropertiesDialog.<init>(Unknown Source)
        at com.jme.app.AbstractGame.getAttributes(Unknown Source)
        at com.jme.app.BaseGame.start(Unknown Source)
        at org.jcrpg.threed.J3DCore.initCore(J3DCore.java:1156)
        at org.jcrpg.apps.Jcrpg.start(Jcrpg.java:170)
        at org.jcrpg.apps.Jcrpg.main(Jcrpg.java:57)
ENGINE TERMINATING
ENGINE TERMINTATED
```

Thanks for you help. ;)

---

### Post by timong on 2007-12-08
"java.lang.UnsatisfiedLinkError: /home/adrian/javarpg/jcrpg-20071202/lib/liblwjgl.so: Can't load IA 32-bit .so on a IA 32-bit platform"

This is the error, sounds quite stupid. What's your system? 32 or 64 bit?

---

### Post by Adrian.C on 2007-12-08
My system is 32 bits. 
Yeah this error sounds stupid to me too... :-k

But it seems to run on another computer with Edgy (I did with VNC, so I didn't test the game yet, but I got the screen-config window).

Strange, I thought I had configured the 2 PCs the same way...

---

### Post by Adrian.C on 2007-12-08
Okay, I tried with the JRE 6, and the exception is different this time :

```
GRAVE: Exception in game loop
java.lang.UnsatisfiedLinkError: /home/adrian/javarpg/jcrpg-20071202/lib/liblwjgl.so: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /home/adrian/javarpg/jcrpg-20071202/lib/liblwjgl.so)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
```

/lib/tls/i686/cmov/libc.so is a symbolic link to  libc-2.3.6.so and apparently the 2.4 version is needed. 
However there is no 2.4 version available for Dapper. :(

Has anyone succeeded in launching it with Dapper ?

---

### Post by timong on 2007-12-21
svn_20071221 is out!

Headlines:
"Base geographies (Mountain, Plain, Forest) were refactored to point height calculated tile generation. Cave and River were rewritten to be compatible with the modififed base geographies. Farview mode was refactored and beautified based on new geographies. New configuration parameter called RENDER_DISTANCE_FARVIEW was added. World generation was extended with rivers and caves. The demo game is now running in the generated world." Download, test and report!

[http://jcrpg.blogspot.com/2007/12/many-things-plus-farview-release.html](http://jcrpg.blogspot.com/2007/12/many-things-plus-farview-release.html) 

[https://sourceforge.net/project/showfiles.php?group_id=197331](https://sourceforge.net/project/showfiles.php?group_id=197331)

[img]http://bp1.blogger.com/_f57_nB05Gno/R2uw78m1uRI/AAAAAAAAAas/4xMaTv1QVDg/s200/rel.JPG[/img]

---

### Post by timong on 2007-12-28
new youtube demo video:
[http://www.youtube.com/watch?v=Mh8rp9moiWY](http://www.youtube.com/watch?v=Mh8rp9moiWY)

---

### Post by timong on 2008-01-24
> **timong said:**
> new youtube demo video:
[http://www.youtube.com/watch?v=Mh8rp9moiWY](http://www.youtube.com/watch?v=Mh8rp9moiWY)


Another one with animated gorillas - a new thing in jcrpg :)
[http://www.youtube.com/watch?v=hSv-SJ-KcKM](http://www.youtube.com/watch?v=hSv-SJ-KcKM)

---

### Post by Vispo on 2008-01-25
Hi,
after seeing the nice animation, i had to check out the SVN version.
just wanted to note that i got an error:
```
    
J3DCore.java:170: illegal start of expression
[javac] <<<<<<< .mine

J3DCore.java:303: illegal start of expression
    [javac] =======

J3DCore.java:308: illegal start of expression
    [javac] >>>>>>> .r685

J3DCore.java:171: 'try' without 'catch' or 'finally'

J3DCore.java:357: illegal start of expression
    [javac]     static

```

Well anyway :-) maybe i'm just too tired to do this, but just wanted to inform you :-)

I also wanted to say greatwork timong and keep it up. You can be proud of it.
MFG
                       Vispo

---

### Post by Vadi on 2008-01-25
> **timong said:**
> Another one with animated gorillas - a new thing in jcrpg :)
[http://www.youtube.com/watch?v=hSv-SJ-KcKM](http://www.youtube.com/watch?v=hSv-SJ-KcKM)

Niice. The back legs look a bit funny though :)

---

### Post by timong on 2008-01-26
> **Vispo said:**
> Hi,
after seeing the nice animation, i had to check out the SVN version.
just wanted to note that i got an error:
```
    
J3DCore.java:170: illegal start of expression
[javac] <<<<<<< .mine

J3DCore.java:303: illegal start of expression
    [javac] =======

J3DCore.java:308: illegal start of expression
    [javac] >>>>>>> .r685

J3DCore.java:171: 'try' without 'catch' or 'finally'

J3DCore.java:357: illegal start of expression
    [javac]     static

```

Well anyway :-) maybe i'm just too tired to do this, but just wanted to inform you :-)

I also wanted to say greatwork timong and keep it up. You can be proud of it.
MFG
                       Vispo

Strange! I've just committed it over to be sure, but I couldn't find a version in the repo that had this problem. Please try again, if you'd like to do so. :) Thanks for your kind words! Cheers! :-)

---

### Post by Vispo on 2008-02-02
Well, got it 
just had to remove the J3DCore.java file and download it again from the SVN.
It seems to work :-) so it will be a pleasure to peek around into your program. Nice little wind animation :-) maybe a too sharp function, for the little hills but :-) really a nice work you have done here. Thank you

---

### Post by timong on 2008-02-02
Cool! :-) Check the latest SVN, there's a preliminary encounter draft version (no combat and such, but might be interesting) :-) [http://jcrpg.blogspot.com/2008/02/draft-version-of-encounter-in-svn.html](http://jcrpg.blogspot.com/2008/02/draft-version-of-encounter-in-svn.html)

---

### Post by timong on 2008-02-03
12th prealpha snapshot release svn_20080203 is out!
```

"- Ecology System and ecology generation with 3 type of animal packs (gorilla, wolf, warthog) was added
- Encounters' system draft version was implemented
- World geography generation was boosted with Cave and River addition
- Animated /rigged model loading (Gorilla)
- Text box log and choice box window added to UI elements
- World map colorization was extended 
- 'UI ruining shadows' bug fixed."

```

Test and report back if in the mood. ;-)

[img]http://bp2.blogger.com/_f57_nB05Gno/R6Y2isWAoOI/AAAAAAAAAew/VnNsvgC0OGk/s200/enc-release.jpg[/img]

[http://jcrpg.blogspot.com/2008/02/animal-outside-release.html](http://jcrpg.blogspot.com/2008/02/animal-outside-release.html)

[https://sourceforge.net/project/showfiles.php?group_id=197331](https://sourceforge.net/project/showfiles.php?group_id=197331)

---

### Post by Vadi on 2008-02-03
Take a vid please! For us on the low-end graphics.. because that anti-aliased screenshot is looking sexy.

---

### Post by timong on 2008-02-04
> **Vadi said:**
> Take a vid please! For us on the low-end graphics.. because that anti-aliased screenshot is looking sexy.

There's video about animation already. The encounter with gorillas is a bit animated, but nothing really complex is involved *yet*. So probably it's enough the check to last video I've posted here about animation. :-) Otherwise the screenshot tells it much how it looks *in-game*. Later when we will have some more movement or even combat and such, I'll create another video for sure. :-)

---

### Post by timong on 2008-02-10
jcrpg needs **free licensed (CC-by-sa and such) fantasy 2D portrait **donations or resources pointed out with url! Topic:

[http://forum.freegamedev.net/index.php?t=msg&th=629&start=0](http://forum.freegamedev.net/index.php?t=msg&th=629&start=0)

---

### Post by Vadi on 2008-02-10
Well, my system76 laptop with an nvidia 8600 came, so I'm in the action. I'll try out the svn tonight

---

### Post by jdemesse on 2008-02-17
I've downloaded the latest version from sourceforge and it works on OS X Leopard with some work. jcrpg.sh doesn't work (java.lang.LinkageError: Unknown platform: Darwin) so I created an Eclipse project. Most of the applications work except whn I try to run them in fullscreen mode. But that is a OS X/LWJGL issue i'm afraid...

Nevertheless, great engine! Looks like you're having fun :)

---

### Post by timong on 2008-02-17
Strange for an error, that Darwin thingy. :-O People reported it's working well on some machines with Mac OS X. Glad you could make it work...full screen thing is weird again. Never bumped into such problem under Linux or Win.

Have you created the eclipse project by checking out the SVN repo? If so, music is playing on your Mac? Linux and Win plays well, so I'm curious if Mac does well or not..

---

### Post by Vispo on 2008-02-18
Ok get a Exception since ~3 days.

Using Kubuntu:
```
     [echo] system: wolf on linux (i386)
     [echo] ant version: Apache Ant version 1.7.0 compiled on August 29 2007
     [echo] jvm version: 1.6.0_03 at /usr/lib/jvm/java-6-sun-1.6.0.03/jre

```

Non critical (does not make it crash:
```

     [java] java.lang.NullPointerException
     [java]     at org.jcrpg.ui.window.LoadMenu.loadSlots(LoadMenu.java:165)
     [java]     at org.jcrpg.ui.window.LoadMenu.<init>(LoadMenu.java:77)
     [java]     at org.jcrpg.threed.J3DCore.simpleInitGame(J3DCore.java:1941)
     [java]     at com.jme.app.BaseSimpleGame.initGame(Unknown Source)
     [java]     at org.jcrpg.threed.J3DCore.initGame(J3DCore.java:869)
     [java]     at com.jme.app.BaseGame.start(Unknown Source)
     [java]     at org.jcrpg.threed.J3DCore.initCore(J3DCore.java:560)
     [java]     at org.jcrpg.apps.Jcrpg.start(Jcrpg.java:58)
     [java]     at org.jcrpg.apps.Jcrpg.main(Jcrpg.java:38)

```

```

     [java] # FILE: /home/wolf/Project/javacrpg/trunk/jcrpg/./save
     [java] java.lang.NullPointerException
     [java]     at org.jcrpg.ui.window.LoadMenu.updateFromDirectory(LoadMenu.java:98)
     [java]     at org.jcrpg.ui.window.LoadMenu.<init>(LoadMenu.java:75)
     [java]     at org.jcrpg.threed.J3DCore.simpleInitGame(J3DCore.java:1941)
     [java]     at com.jme.app.BaseSimpleGame.initGame(Unknown Source)
     [java]     at org.jcrpg.threed.J3DCore.initGame(J3DCore.java:869)
     [java]     at com.jme.app.BaseGame.start(Unknown Source)
     [java]     at org.jcrpg.threed.J3DCore.initCore(J3DCore.java:560)
     [java]     at org.jcrpg.apps.Jcrpg.start(Jcrpg.java:58)
     [java]     at org.jcrpg.apps.Jcrpg.main(Jcrpg.java:38)


```

```

     [java] WARNING: Unable to locate: ./data/sky/day/top.jpg

```

Critical exception is:
```

[java] SEVERE: Exception in game loop
     [java] java.lang.NoSuchFieldError: player
     [java]     at org.jcrpg.threed.moving.J3DMovingEngine.updateScene(J3DMovingEngine.java:186)
     [java]     at org.jcrpg.threed.J3DCore.simpleUpdate(J3DCore.java:2121)
     [java]     at org.jcrpg.threed.J3DCore.update(J3DCore.java:2171)
     [java]     at org.jcrpg.threed.J3DCore.updateDisplay(J3DCore.java:1578)
     [java]     at org.jcrpg.threed.J3DCore.init3DGame(J3DCore.java:1746)
     [java]     at org.jcrpg.ui.window.PartySetup.inputUsed(PartySetup.java:207)
     [java]     at org.jcrpg.ui.window.element.input.TextButton.handleKey(TextButton.java:104)
     [java]     at org.jcrpg.ui.window.InputWindow.handleKey(InputWindow.java:104)
     [java]     at org.jcrpg.ui.window.PartySetup.handleKey(PartySetup.java:179)
     [java]     at org.jcrpg.ui.UIBase.handleEvent(UIBase.java:86)
     [java]     at org.jcrpg.threed.input.menu.CKeyMenu.performAction(CKeyMenu.java:41)
     [java]     at com.jme.input.ActionTrigger.performAction(Unknown Source)
     [java]     at com.jme.input.ActionTrigger$CommandTrigger.performAction(Unknown Source)
     [java]     at com.jme.input.InputHandler.processTriggers(Unknown Source)
     [java]     at com.jme.input.InputHandler.update(Unknown Source)
     [java]     at com.jme.input.InputHandler.updateAttachedHandlers(Unknown Source)
     [java]     at com.jme.input.InputHandler.update(Unknown Source)
     [java]     at com.jme.app.BaseSimpleGame.updateInput(Unknown Source)
     [java]     at org.jcrpg.threed.J3DCore.updateInput(J3DCore.java:1609)
     [java]     at com.jme.app.BaseSimpleGame.update(Unknown Source)
     [java]     at org.jcrpg.threed.J3DCore.update(J3DCore.java:2167)
     [java]     at com.jme.app.BaseGame.start(Unknown Source)
     [java]     at org.jcrpg.threed.J3DCore.initCore(J3DCore.java:560)
     [java]     at org.jcrpg.apps.Jcrpg.start(Jcrpg.java:58)
     [java]     at org.jcrpg.apps.Jcrpg.main(Jcrpg.java:38)
     [java] ENGINE TERMINATING

```

Hopefully this will help you. Anyway thx for your work.
Best regards

                   Vispo

---

### Post by timong on 2008-02-18
I think you should try to clean the compiled classes and recompile it to solve the issue. This is typical error when some of the classes were not compiled while others were. I hope it helps! I don't have this problem with the current SVN.

---

### Post by Nkari on 2008-02-19
Where you still looking for more character portraits? 

Was there any standards decided on in regards to file size, image size, image format or stylistic considerations such as transparent or specific colour backgrounds or something? 

The discussion on that other forum seems to have stopped about 8 months ago in regards to the topic so I thought I would ask here.

---

### Post by timong on 2008-02-20
Thanks for you question! :) Yes, we are still looking for new portraits! 500x500 px is a good size for them and a transparent background is the best solution.

About the other topic, I don't get what's that 8 month you saw, there are rather new posts on the other forum, last in the portraits thread is 8 days old, there are 2 day old posts in another portrait thread too.

---

### Post by Nkari on 2008-02-21
errr, that would be me looking at the wrong part of the post for the dating. 

Just figured out it was actually someones date of joining that other forum I was looking at, not the post date.

---

### Post by timong on 2008-02-22
> **Nkari said:**
> errr, that would be me looking at the wrong part of the post for the dating. 

Just figured out it was actually someones date of joining that other forum I was looking at, not the post date.

Okay. So portraits are very welcome at the moment! :guitar: Hope we'll see you around!

---

### Post by charlieg on 2008-02-22
Example portrait WIP here:
[http://forum.freegamedev.net/index.php?t=msg&th=657](http://forum.freegamedev.net/index.php?t=msg&th=657)

Contribute portraits here:
[http://forum.freegamedev.net/index.php?t=msg&th=651&start=0](http://forum.freegamedev.net/index.php?t=msg&th=651&start=0)

---

### Post by timong on 2008-02-28
The "Winter Killer" release is out

Highlights:
"Main menu added with working Save/Load/New Game options. Sounds and in game music added along with the new Audio System. Character generation screens with many skills and classes along with currently 4 new races were added. Party setup for new games is working now. On screen party portraits view to visualize your party was added. A set of portraits was added for use with the character generation."
Download, test and report back here or at the forum. :-)

[img]http://bp1.blogger.com/_f57_nB05Gno/R8Ha4liENHI/AAAAAAAAAg8/QxcPNJ2RtEM/s200/winterkrel.jpg[/img]


Project still in need of 3D and 2D contributions. All will go under open free media license (CC,GPL) - building other possible current and later free open source games, not only jcrpg. 

devblog:
[http://jcrpg.blogspot.com/](http://jcrpg.blogspot.com/)

Download:
[https://sourceforge.net/project/showfiles.php?group_id=197331](https://sourceforge.net/project/showfiles.php?group_id=197331)

---

### Post by eragon100 on 2008-02-28
Nice!

Keep up the good work, but mouse should be able to click buttons in menu thuogh.

Lots of potential! :popcorn:

---

### Post by timong on 2008-02-28
> **eragon100 said:**
> Nice!

Keep up the good work, but mouse should be able to click buttons in menu thuogh.

Lots of potential! :popcorn:

Thanks for testing and commenting! :) 
See ya!

---

### Post by ShirishAg75 on 2008-03-12
Hi there, 
 Saw the post at [http://freegamer.blogpost.com](http://freegamer.blogpost.com) then went to freegamer.dev forums & then finally here.

Unfortunately, don't have the hardware so could test your stuff but still like the photographs, hopefully you have a video for us guys to look at one of these days. Would recommend it to the guys who have the monster rigs ;)

---

### Post by timong on 2008-03-12
> **ShirishAg75 said:**
> Hi there, 
 Saw the post at [http://freegamer.blogpost.com](http://freegamer.blogpost.com) then went to freegamer.dev forums & then finally here.

Unfortunately, don't have the hardware so could test your stuff but still like the photographs, hopefully you have a video for us guys to look at one of these days. Would recommend it to the guys who have the monster rigs ;)

[http://youtube.com/watch?v=KU_QAK2Q3X8](http://youtube.com/watch?v=KU_QAK2Q3X8)
[http://youtube.com/watch?v=Mh8rp9moiWY](http://youtube.com/watch?v=Mh8rp9moiWY)
[http://youtube.com/watch?v=hSv-SJ-KcKM](http://youtube.com/watch?v=hSv-SJ-KcKM)

These are videos previously published, linked here in this topic before and on the blog too they can be found in the video bar part.

---

### Post by timong on 2008-03-16
The "Contributionary" release is out svn_20080315:
```

"UI graphics were completely redesigned including main menu, 
character creation widgets, on screen display. 
Some new character portraits were added. 
Code optimization for 3D and loading performance were done. 
World and Ecology generation configuration through XML file 
were developed. Some mushrooms and other vegetation appended 
to flora and fox re-added to possibly met fauna.. 
Local map was implemented and added replacing mini world map on the HUD. 
Sky-sphere lighting bug was fixed along with other minor bugs. 
Turning around camera rotation was expanded with view position 
changing to add a better view of the faced things around."
```

[img]http://bp3.blogger.com/_f57_nB05Gno/R9wUs0k22XI/AAAAAAAAAiE/5iQnH4jVR3A/s200/rel1.jpg[/img]

[http://jcrpg.blogspot.com/2008/03/contributionary-release.html](http://jcrpg.blogspot.com/2008/03/contributionary-release.html)

---

### Post by ShirishAg75 on 2008-03-16
> **timong said:**
> [http://youtube.com/watch?v=KU_QAK2Q3X8](http://youtube.com/watch?v=KU_QAK2Q3X8)
[http://youtube.com/watch?v=Mh8rp9moiWY](http://youtube.com/watch?v=Mh8rp9moiWY)
[http://youtube.com/watch?v=hSv-SJ-KcKM](http://youtube.com/watch?v=hSv-SJ-KcKM)

These are videos previously published, linked here in this topic before and on the blog too they can be found in the video bar part.

Don't these videos have any audio in them? I downloaded the files & ran them through mediainfo, they don't seem to have any music or that's still something to be done ?

---

### Post by Vadi on 2008-03-17
I don't believe music is avialable yet at this stage of the game. Which means they're quite open to suggestions!

---

### Post by timong on 2008-03-17
> **ShirishAg75 said:**
> Don't these videos have any audio in them? I downloaded the files & ran them through mediainfo, they don't seem to have any music or that's still something to be done ?

There were no audio at that time. There's now music and sounds in the game since before last release was out.

---

### Post by timong on 2008-03-17
> **Vadi said:**
> I don't believe music is avialable yet at this stage of the game. Which means they're quite open to suggestions!

Actually there is since a month or so! :) I've added some sounds too, walking, animal sounds at encounter is included with latest two releases. Check out if interested.

---

### Post by Vadi on 2008-03-17
I can't get past the second character creation screen... the finishing button there just refuses to work. My profession was left blank though (couldn't select anything), did that have something to do with it?

---

### Post by timong on 2008-03-17
> **Vadi said:**
> I can't get past the second character creation screen... the finishing button there just refuses to work. My profession was left blank though (couldn't select anything), did that have something to do with it?

Just read what's written on the screen below the fields.

Help: you must add the points to your attributes in such a way that you can select a profession. :-) Easiest is to add all attribute points strength, you'll have a warrior. :) Next screen is the same, select skills press enter, tune it, and when no point left, Ready. :)

---

### Post by timong on 2008-04-17
Thursday, 17 April 2008
The "Nightside" Release is out

Check out the downloads, ungzip, play and report back with your experience here or at the forum. As things go further and further we are nearing a state where more and more 3D models and their animation is becoming tremendously needed in the art department! There are already several models (e.g. bear, wolf, fox, spider) that's in need of rigging and animation or there's the already rigged human model pair that just needs animation. So if you want to help out, join the effort! A great opportunity to practice animation and it would mean a lot to the free game development community and jcrpg.

Highlights:
"New animals as bear and spider were added. Humanoid groups were introduced with the humans and their basic economy. Basic populations and houses added for human groups. New sounds for animals and humans along with environmental effects depending on nearby beings and climate. Party Behavior and Pre-encounter input screens were introduced. On screen display extended with the 'Entity-O-Meter' which shows nearby groups' icons. New portraits and models by Archenemy."

[http://jcrpg.blogspot.com/2008/04/nightside-release-is-out-call-for.html](http://jcrpg.blogspot.com/2008/04/nightside-release-is-out-call-for.html)
[img]http://bp3.blogger.com/_f57_nB05Gno/SAcClyfXSnI/AAAAAAAAAo4/mPMyAuWYlvo/s200/relapr4.JPG[/img]

---

### Post by timong on 2008-05-30
New anniversary release is out!

Highlights:
"New UI windows for Encounter Phase, 
Turn Act Phase, Character Sheet (F3 key) 
and Inventory (F4) were added. New Population 
generation algorithms (GrownInfrastructure, 
DefaultInfrastructure) were added along with 
new integration level of named Towns for 
friendly populations to unite in. Economy 
Update Turn implemented for growing or 
declining population changes. Basic level 
Entity relations and Entity states 
(level and points) and Entity fragments 
(roaming entity groups) were added. 
A few Objects for inventory were added. 
Skill system further implemented with 
object dependencies and Skill Act Forms 
(like some spells and some combat forms etc.).
New animals heron and deer were added 
and wolf replaced (glestanimals of 
wciow at glest.org). Smaller bugfixes, 
optimizations (culling works again 
now correctly). This is the First 
Anniversary Release!"

[img]http://bp0.blogger.com/_f57_nB05Gno/SEBTfsfk6RI/AAAAAAAAArQ/GKYogIcYg5E/s200/heron.jpg[/img]

[http://jcrpg.blogspot.com/2008/05/anniversary-boom-release-attacks.html](http://jcrpg.blogspot.com/2008/05/anniversary-boom-release-attacks.html)

Project is in need of mythic monsters 3d models:

[http://forum.freegamedev.net/index.php?t=msg&th=1064&start=0](http://forum.freegamedev.net/index.php?t=msg&th=1064&start=0)

Hope to see you around!

---

### Post by oldrocker99 on 2008-05-31
The 2008-05-30 release is at:

[https://sourceforge.net/project/showfiles.php?group_id=197331&package_id=233637&release_id=603113](https://sourceforge.net/project/showfiles.php?group_id=197331&package_id=233637&release_id=603113)

:guitar:

---

### Post by timong on 2008-06-01
> **oldrocker99 said:**
> The 2008-05-30 release is at:

[https://sourceforge.net/project/showfiles.php?group_id=197331&package_id=233637&release_id=603113](https://sourceforge.net/project/showfiles.php?group_id=197331&package_id=233637&release_id=603113)

:guitar:

Thanks for linking in the download directly! Hope to see some test results, if people are interested in trying it... or even better if someone would like to actively help out this opensource project with some 3D models (even static ones would do for first!)

---

### Post by timong on 2008-08-13
jcrpg svn_20080813 prealpha snapshot release is out!
```

- Turn based playable Combat phase added
- New animated models (boarmen thug and mage by Zphr)
- New house and town models (by Zphr)
- New static monster model (kobold by Surt)
- Total redesign of jungle plants, new plants for continental,
- New Encounter Ground system that separates the encounter scene
- Inventory enhanced (equip,attach,give,drop)
- New Loot Window after combat
- Character leveling
- New ground tile generation system with smoothed ground
- New 2D elements, some refactored UI images
- Optional support for secondary ground textures
- Optional texture splatted ground tile blends
- New spells, skills, items, artifacts, objects
- Bard instrument concept available with one implemented item
- Particle system with lights for spells added
- Support for continuously playing sound sources like waters, forest ambient
- New environment & humanoid sounds added
- New Body Part system that enables critical impacts
- Optimizations: tree trunk batching, cutting of non-visible interior parts, more locking
- Bug fixes
- Far view mode is disabled till fixing it for the new ground system

```

Testers and new contributors needed!

[ http://jcrpg.blogspot.com/2008/08/vigilante-eye-release.html](http://jcrpg.blogspot.com/2008/08/vigilante-eye-release.html)

[http://javacrpg.sourceforge.net/wiki/index.php/Download](http://javacrpg.sourceforge.net/wiki/index.php/Download)

[img]http://3.bp.blogspot.com/_f57_nB05Gno/SKM5EhJDblI/AAAAAAAAAvc/JgnAlu0VY3Q/s200/fight.jpg[/img]

---

### Post by Vadi on 2008-08-13
Can you fix your wiki to allow apt: links? I couldn't get them working.

---

### Post by timong on 2008-08-14
> **Vadi said:**
> Can you fix your wiki to allow apt: links? I couldn't get them working.

Well, I'm really a noob at wiki things, I just fired up the version suggested for sourceforge.net. :) But what does 'apt: links' really mean? That you can install from browser?

---

### Post by Vadi on 2008-08-14
Yeah, you click on it and it'll install the package. Like [this]("apt:firefox")!

---

### Post by timong on 2009-02-02
There's been some progress since my last post here. Some optimizations, new 3D monsters, a simple maze generation along with normal mapping, a simple unlocking UI together with the new storage looting window. If things are going fine plan to release a new test package soon(er or later :D)..

A bit slower of pace in coding partially because of my new interest in music composition which has taken shape in some soundtracks for the jClassicRPG. I will post you here the links to the released soundtrack albums, two pieces, each under free license (CC-BY-SA & CC-BY-SA-NC). Enjoy, if you can! ;)

[http://www.jamendo.com/en/album/39136](http://www.jamendo.com/en/album/39136)
[http://www.jamendo.com/en/album/35929](http://www.jamendo.com/en/album/35929)

---

### Post by timong on 2009-09-01
The development is again on track (since I returned to coding after a few months of relaxation through music composition for another project: scourge rogue-like).

The project is nearing a new release again.Different additions and enhancements are incorporated at a steady pace. Current efforts are concentrated on creating a basic road network connecting towns (using a weighed A* algorithm) , an enhanced world map, optimized 2D text rendering, full mouse support for the UI, also making the use of UI easier and addition of some new content.

The next step on the roadmap following the next release will be the addition of a 'templated' story/dialog system which is planned to be woven into the carpet of the world at the phase of the seed based generation.

Check the blog if you want some screenshots and details.

[http://jcrpg.blogspot.com](http://jcrpg.blogspot.com)

---

### Post by timong on 2009-09-20
Project is steadily progressing towards the new test release. A heap of medium or smaller feature upgrades are incorporated to the SVN. You can expect some new content too. Easier to use input/handling and more help texts (tooltips) are being added. Please help to get the project some spotlight - post about it where you think it's reasonable, other sites,blog, other forums. Thanks! :)

[http://jcrpg.blogspot.com/2009/09/content-integration-on-way-still-more.html](http://jcrpg.blogspot.com/2009/09/content-integration-on-way-still-more.html)

[img]http://1.bp.blogspot.com/_f57_nB05Gno/Sraaho7aRtI/AAAAAAAABPQ/hPsWJ_x1YyY/s200/shrine.png[/img]

---

### Post by timong on 2009-10-18
steadily progressing still: nice new things, many fixes, polishing, contributions. Check latest shots/news:

[http://jcrpg.blogspot.com/2009/10/contributions-shaders-new-normal-maps.html](http://jcrpg.blogspot.com/2009/10/contributions-shaders-new-normal-maps.html)

Also we have a new forum here:
[http://jcrpg.ath.cx/phpbb/index.php](http://jcrpg.ath.cx/phpbb/index.php)

[url=http://4.bp.blogspot.com/_f57_nB05Gno/StuPj8rXRfI/AAAAAAAABP4/og2m6r5Ig7Q/s1600-h/screenshot_2009.10.18.14.51.12.174.png]
[img]http://4.bp.blogspot.com/_f57_nB05Gno/StuPj8rXRfI/AAAAAAAABP4/og2m6r5Ig7Q/s200/screenshot_2009.10.18.14.51.12.174.png[/img][/url]

---

### Post by beastrace91 on 2009-10-18
Looks like a very interesting project! How far along is the game itself? I'm downloading it now from source forge - is the latest version the one [posted](http://sourceforge.net/projects/javacrpg/files/jClassicRPG/svn_20090228/jcrpg-20090228.zip/download) on Feb 28th 09?

At any rate looking forward to giving it a go :)

~Jeff

---

### Post by timong on 2009-10-19
> **beastrace91 said:**
> Looks like a very interesting project! How far along is the game itself? I'm downloading it now from source forge - is the latest version the one [posted](http://sourceforge.net/projects/javacrpg/files/jClassicRPG/svn_20090228/jcrpg-20090228.zip/download) on Feb 28th 09?

Yes, that's the latest release. So far the story is not yet implemented. You can explore a big world with 4 climate zones and different humanoid races/do combat/level/have inventory hmm and many more things. :) The release that will be out now will be much more polished, so I advise you to check out the SVN or wait for the next release. Now it's much more user friendly than the last official test-release is. :) For info how to check the SVN please check the project's wiki: [http://sourceforge.net/apps/mediawiki/javacrpg/index.php?title=Download#Downloading_Developer_version_from_SVN](http://sourceforge.net/apps/mediawiki/javacrpg/index.php?title=Download#Downloading_Developer_version_from_SVN)

---

### Post by beastrace91 on 2009-10-19
All righty, cool I'll give that a go later this week.

~Jeff

---

### Post by timong on 2010-06-08
Major technical upgrade release is out. Changed to Ardor3D openGL engine to resolve some technical issues and step aboard a new, freshly developed 3D engine written in Java with Cpp binding to OpenGL. The release features new voicepacks and some buildings too additionally.

A fixpack is already available which resolves some nVidia related issues:
[http://jcrpg.blogspot.com/2010/05/almost-pristine-release.html](http://jcrpg.blogspot.com/2010/05/almost-pristine-release.html)
[http://jcrpg.blogspot.com/2010/06/fix-pack-download-is-available.html](http://jcrpg.blogspot.com/2010/06/fix-pack-download-is-available.html)

Direct download links:
[https://sourceforge.net/projects/javacrpg/files/jClassicRPG/svn_20100525/jCRPG-engine-fix20100607.zip/download](https://sourceforge.net/projects/javacrpg/files/jClassicRPG/svn_20100525/jCRPG-engine-fix20100607.zip/download) 17mb
[http://sourceforge.net/projects/javacrpg/files/jClassicRPG/svn_20100525/jcrpg-20100525a.zip/download](http://sourceforge.net/projects/javacrpg/files/jClassicRPG/svn_20100525/jcrpg-20100525a.zip/download) 170mb

Instructions:
[http://sourceforge.net/apps/mediawiki/javacrpg/index.php?title=Download](http://sourceforge.net/apps/mediawiki/javacrpg/index.php?title=Download)

Give it a go, and report back how it runs.
Thanks! 

[img]http://1.bp.blogspot.com/_f57_nB05Gno/S_hjTjborYI/AAAAAAAABW4/orPSMdTqfio/s200/shot1274564503090.jpg[/img][img]http://1.bp.blogspot.com/_f57_nB05Gno/S-8gVoMVDyI/AAAAAAAABWk/QGNpCtDYBRY/s200/shot1273957421164.jpg[/img]

---

