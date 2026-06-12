---
title: "Idea's on coding choices for making a game."
date: 2011-05-20
forum: Gaming &amp; Leisure
---

### Post by Omegus on 2011-05-20
Hello everyone,

**History**:
  Since I got home from over seas (Afghanistan) , I switched to Linux and have never looked back. I have worked on a few projects such as a multi-touch table for my living room running Maverick Meerkat. Then I was really getting into download and playing tons of games . So anyways my twin brother and I are wanting to make a Hi-res 2d RPG like the Classic Final Fantasy games.

**Question**: 
I want to know which type of coding would be best for my situation? I was looking at Python and C++ and both seem great but are there other options out there? Is Ruby effective on Linux? 


**Sum Up**:
I will be doing all the coding so this will keep me busy. (Or at least until Dilogus: Winds of War comes out.)
But We are dead set to mostly make the game for our selves and for Linux users.

---

### Post by HolgerB on 2011-05-20
Since I never developed any game for Linux it is somewhat hard to judge the tools but in the end it often boils down to this:
There is a huge amount of tools there to do the job (Python, C++, Basic, etc)
All of them have advantages as well as disadvantages (depending on your requirements)

C++ might work well but Python could do the job also.

The mayor work should be the content though.

In your position I would check out the work of other similar project (this is the advantage of Open Source) and evaluate if this drives your boat.

---

### Post by ExileAmongYou on 2011-05-20
How much coding experience do you have? If you're just starting to learn, I would recommend Python and Pygame. I had almost zero coding experience at the start of this year, and it only took me about 3 weeks to figure out how to code a psychology experiment with Pygame (not quite as exciting as a game, but still).

---

### Post by Petrolea on 2011-05-20
Ruby can be used to create games but I don't really recommend it (I can say from my own experiences).

Lots of 2D games are made with SDL. It is not too hard to learn, the documentation is great and making 2D games is really easy. 

This is by far the best tutorial I've ever seen on making Linux games: the3fold.free.fr/doc/games.pdf

Make sure to look up OpenGL if you want more advanced graphics.

---

### Post by Arthur_D on 2011-05-20
You should check out FLARE. It's an engine for isometric 2D RPG's - the man behind wants to make a complete game with it, and he's already made quite a few assets that might be reusable.

Introduction of [FLARE]("http://forum.freegamedev.net/viewtopic.php?f=22&t=1230") over at FreeGameDev.

---

### Post by Omegus on 2011-05-22
Thanks for aot of the feedback. To answer somme of the questions I have had some exp with C++ and SDL but nothing major. I have been getting back into coding since I joined the wonderful world of Linux (Ubuntu).
 
I just started reading the PDF book now and it seems like this is ging to be a good read. The look i'm going for is hi-res 2d gaming.

---

### Post by Petrolea on 2011-05-23
> **Omegus said:**
> Thanks for aot of the feedback. To answer somme of the questions I have had some exp with C++ and SDL but nothing major. I have been getting back into coding since I joined the wonderful world of Linux (Ubuntu).
 
I just started reading the PDF book now and it seems like this is ging to be a good read. The look i'm going for is hi-res 2d gaming.

For advanced graphics check out Open GL. It is used in many games and is cross-platform. It might be a bit hard to understand but it's worth the time you spend while learning it. 

Oh, and let us know when your game is finished ;)

---

### Post by sakuramboo on 2011-05-23
There is some misinformation in here.

OpenGL is a graphics rendering library, but very bare bones. Requiring you to code a lot of basic functions. It does NOT handle audio (that is what OpenAL is for).

SDL encompasses graphics, audio and input. SDL DOES handle 3D graphics. The goal of SDL is to create a simple abstraction layer to get 2D and 3D graphics to the screen, create simple APIs for audio and input controls and to fully utilize OpenGL and OpenAL to allow for easy cross platform development.

You never really want to code directly using OpenGL API's. Doing so will create rather ugly code and not very portable. OpenGL is not smart enough to know the difference between X11 and Windows (what ever the name for Windows display daemon is) or the difference between nVidia or ATI graphics chipsets. SDL, on the other hand, handles all of that behind the scenes.

To the OP:
You have two options when making a game. Built your own engine or use a pre-existing engine. Both have the strengths and weaknesses. Check out some different engines and see if any fit the bill for what you are looking to do. If not, then build your own.

Also, depending on your level of programming knowledge will determine where you should start off. For anyone just starting out, you have to start small. Write a Tetris close. If you feel really adventurous, write a Super Mario Brothers 1 clone. From there, you should have enough understanding on how to build your own engines.

Also, a great listen for anyone looking to get into game development is the interview with Ryan Gordon from FLOSS Weekly.

[http://twit.tv/floss8](http://twit.tv/floss8)

I always make sure to share that link with anyone looking to get into game development. Ryan goes over many points on game development, cross platform development, open source and SDL. Always a great listen.

---

### Post by Petrolea on 2011-05-23
> **sakuramboo said:**
> There is some misinformation in here.

OpenGL is a graphics rendering library, but very bare bones. Requiring you to code a lot of basic functions. It does NOT handle audio (that is what OpenAL is for).

SDL encompasses graphics, audio and input. SDL DOES handle 3D graphics. The goal of SDL is to create a simple abstraction layer to get 2D and 3D graphics to the screen, create simple APIs for audio and input controls and to fully utilize OpenGL and OpenAL to allow for easy cross platform development.

You never really want to code directly using OpenGL API's. Doing so will create rather ugly code and not very portable. OpenGL is not smart enough to know the difference between X11 and Windows (what ever the name for Windows display daemon is) or the difference between nVidia or ATI graphics chipsets. SDL, on the other hand, handles all of that behind the scenes.

To the OP:
You have two options when making a game. Built your own engine or use a pre-existing engine. Both have the strengths and weaknesses. Check out some different engines and see if any fit the bill for what you are looking to do. If not, then build your own.

Also, depending on your level of programming knowledge will determine where you should start off. For anyone just starting out, you have to start small. Write a Tetris close. If you feel really adventurous, write a Super Mario Brothers 1 clone. From there, you should have enough understanding on how to build your own engines.

Also, a great listen for anyone looking to get into game development is the interview with Ryan Gordon from FLOSS Weekly.

[http://twit.tv/floss8](http://twit.tv/floss8)

I always make sure to share that link with anyone looking to get into game development. Ryan goes over many points on game development, cross platform development, open source and SDL. Always a great listen.

Of course you won't code ONLY in OpenGL (and whichever language you choose with it) but in combination with SDL it can do quite a lot. I programmed in combination of both (using C) and in few minutes there's a character moving around the screen and shooting bullets (2D ofc). 

Once you make a basic engine it gets way easier.

Oh and to answer the primary question, I browsed my Dropbox folder and found a game made in Ruby with Chingu (not much different from the sample on the website of Chingu tho). It can be used to create games quick & easy but I don't think it's powerful enough for your task. Code sample:

```

require 'rubygems'
require 'chingu'
include Gosu
include Chingu

class Game < Chingu::Window
  def initialize
    super(640,480,true)             
    self.input = { :escape => :exit }
    
    @player = Player.create(:x => 200, :y => 200, :image => Image["spaceship.png"])
    @player.input = { :holding_left => :move_left, :holding_right => :move_right, 
                      :holding_up => :move_up, :holding_down => :move_down }
  end
  
  def update
    super
    self.caption = "FPS: #{self.fps} milliseconds_since_last_tick: #{self.milliseconds_since_last_tick}"
  end
end

class Player < Chingu::GameObject  
  def move_left;  @x -= 5; end
  def move_right; @x += 5; end
  def move_up;    @y -= 5; end
  def move_down;  @y += 5; end
end


Game.new.show

```

Just moving a spaceship around in 30 lines (could be much less but I prefer very clean and readable code).

---

### Post by Omegus on 2011-05-23
Well I have decided SDL with some OpenGL and OpenAL is the way to go. I know from my RPG Maker days SDL was very easy and workable. I just finished reading about opengl and al I think it would be the best to combined all 3 types of to get the results. now all I need to do is find a source codes from  FFIV to FFVI. I know alot of people in the RPG community have redone a lot of the same stuff from those games in SDL but i would rather write it myself and add a twist.

    Anyways enough rambling time to start coding thanks for the help I will be back in this thread again to discuss more on future problems that will arise. Thanks guys.



Update 23/May/11 19:42: Just found a great engine FFVI SDK at this site if anyone is interested. [http://ff6sdk.webs.com/about.htm](http://ff6sdk.webs.com/about.htm) check it out.

---

### Post by juancarlospaco on 2011-05-23
[http://www.pilas-engine.com.ar/videos](http://www.pilas-engine.com.ar/videos)

Press Play on the Videos.

If you need an IDE:  [http://ninja-ide.org/](http://ninja-ide.org/)

---

### Post by Omegus on 2011-05-23
That is really interesting Ill get my twin brother to try that out and see what he thinks I'm doing some tests right now . But looks like great piece of kit. thanks.

---

### Post by Petrolea on 2011-05-24
> **juancarlospaco said:**
> [http://www.pilas-engine.com.ar/videos](http://www.pilas-engine.com.ar/videos)

Press Play on the Videos.

If you need an IDE:  [http://ninja-ide.org/](http://ninja-ide.org/)

Any non-spanish videos available? It looks interesting.

---

### Post by HolgerB on 2011-05-26
[QUOTE=sakuramboo]There is some misinformation in here.[/QUOTE]
IMO this applies to your posting too.

[QUOTE=sakuramboo]
OpenGL is a graphics rendering library, but very bare bones. Requiring you to code a lot of basic functions. It does NOT handle audio (that is what OpenAL is for).
[/QUOTE]
OpenGL provides all the functionality you need to code stuff like Q3A, Doom3, Quake4 and so on. 
Determine what you consider "basic functions" ?!?

[QUOTE=sakuramboo]
You never really want to code directly using OpenGL API's. Doing so will create rather ugly code and not very portable. OpenGL is not smart enough to know the difference between X11 and Windows (what ever the name for Windows display daemon is) or the difference between nVidia or ATI graphics chipsets. SDL, on the other hand, handles all of that behind the scenes.
[/QUOTE]
Partially true...
The name of the Display framework of Windows is GDI. I wonder why someone should NOT code using OpenGLs API ? At least unless you use a prebuild engine which abstracts the 3D stuff in own functions. OpenGL is one (if not THE) solution for portable code. Unless you use vendor-specific shader / custom function stuff, your code will be very portable to other platforms. Shurely OpenGL is solely for rendering but beside changing the render context you use, a well written OpenGL game should be easy to port from Windows to Linux (in example). Its the developer who needs to be smart enough to write OpenGL stuff which doesn't rely on special functions of NVida / ATI.

I would be curious how SDL could handle differences in OpenGL implementation for ATI versus NVidia chips ? :confused:

Using SDL only helps for being independent of things like handling mouse code, network stuff and so on. Basically a DirectX equivalent for other platforms. For 3D you still need to use something like OpenGL. Esp. since the 3D drivers on Linux only provide it as supported interface.

---

### Post by HolgerB on 2011-05-26
> **juancarlospaco said:**
> [http://www.pilas-engine.com.ar/videos](http://www.pilas-engine.com.ar/videos)

Press Play on the Videos.

If you need an IDE:  [http://ninja-ide.org/](http://ninja-ide.org/)
Hi there,

are there any plans of writing english documentation. From my limited spanish language I would guess that the pilar engine is a gaming frontend to quickly implement python based games, right ?

I guess there would be a lot of interest also in the English speaking community.

Regards,
Holger

---

### Post by juancarlospaco on 2011-05-26
> **Petrolea said:**
> Any non-spanish videos available? It looks interesting.

Its a GPL proyect from Argentina, so Presentations are on Spanish,
but Developers know English, so you can use the forums/email/whatever anyways,
if you need help drop me a line, i speak spanish too.

---

### Post by juancarlospaco on 2011-05-26
> **HolgerB said:**
> Hi there,

are there any plans of writing english documentation. From my limited spanish language I would guess that the pilar engine is a gaming frontend to quickly implement python based games, right ?

I guess there would be a lot of interest also in the English speaking community.

Regards,
Holger

Yes they have plans of writing it, its a young proyect, but powerful.
*"Pilas"* it means *"Battery's"* (from the *Python, with Batterys included*).
Yes its a Engine for Games, like others, 
it can do more complex things than the videos actually show.

Post on their Forums, they will reply you, on english too. 
If you need help drop me a line.  :)

---

### Post by juancarlospaco on 2011-05-26
The Pilas Engine official forum:  
[http://www.losersjuegos.com.ar/foro/viewforum.php?f=22&sid=2c20a48a94175ac66d9f2a488b27ca23](http://www.losersjuegos.com.ar/foro/viewforum.php?f=22&sid=2c20a48a94175ac66d9f2a488b27ca23)

---

### Post by forrestcupp on 2011-05-26
> **Omegus said:**
> Well I have decided SDL with some OpenGL and OpenAL is the way to go.

Before you get too involved in SDL, I encourage you to check out SFML. It is written in C++, and it's great for 2D games. It's easier to use than SDL, and it's great for 2D audio and networking as well.

Also, it uses the zlib/libpng license, which is compatible with GPL, but much freer, so you can do whatever you want with the code, even commercial/proprietary.

---

### Post by HolgerB on 2011-05-26
> **juancarlospaco said:**
> Yes they have plans of writing it, its a young proyect, but powerful.
*"Pilas"* it means *"Battery's"* (from the *Python, with Batterys included*).
Yes its a Engine for Games, like others, 
it can do more complex things than the videos actually show.

Post on their Forums, they will reply you, on english too. 
If you need help drop me a line.  :)
Yes indeed. I guess using a gaming framework together with the opportunities of Python is a nice idea.

Thanks for your offer but currently I am not in urgent need for such a framework. It is more the idea the english documentation would attract more people. Unfortunately my spanish is non-existant. So I can hardly help in translating anything.

---

### Post by juancarlospaco on 2011-05-26
> **HolgerB said:**
> 
Thanks for your offer but currently I am not in urgent need for such a framework. It is more the idea the english documentation would attract more people. Unfortunately my spanish is non-existant. So I can hardly help in translating anything.

You are welcome    &#664;&#8255;&#664;

---

### Post by Omegus on 2011-05-28
Thanks everyone for the information, I am going to have to cancel production of my rpg since I'll be on my sniper course soon and don't have time.

---

### Post by desktorp on 2011-05-29
Magitek > Carbine

---

