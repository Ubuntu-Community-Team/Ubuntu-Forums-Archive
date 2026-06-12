---
title: "Why not make a &quot;Learn Python&quot; game??"
date: 2008-06-18
forum: Gaming &amp; Leisure
---

### Post by myromance123 on 2008-06-18
Ok, this is just an idea, but knowing that there are quite a number of youngsters out there like myself wanting to learn how to program the Python way I thought " why not make a game that would teach python in an easy way?"
 for e.g : an rpg with Python functions and what those functions do, used to battle creatures. You gain knowledge of the functions and you get used to typing them :D (it doesnt have to be fancy, 2D will do XD )

   Now since I dont know how to program in any language yet, Im posting the idea here. If I knew how to program, I would indeed spend countless hours on making such an awesome game :)

      I dont believe there is such a game yet, BUT if there is something like it, please do point me in its direction so I can get a head start :]

        I believe if there was a gaming industry on "how to program" games for linux based pcs, then Linux might( just MIGHT) get a whole lot more publicity as well :)   [is this the coming of a new gaming trend!?!]

       What do you think and know? Please do share~

:guitar:

---

### Post by ucal on 2008-06-18
There are a couple games I can recommend actually.  They don't teach you python per se, but they do teach you the basics of programming, if you can be bothered to learn their languages.  Use the add/remove and search for:

droidbattles 

and

GvRng

The first is more of a game, the second more of a tutorial game, with the stated goal of being a precursor to learning python.

---

### Post by myromance123 on 2008-06-19
You ROCK dood !!  If I knew how to give you the beans I would !!

       Thnx so very much

---

### Post by cogadh on 2008-06-19
Just click on the little star medal in botom corner of his post. It won't give him beans, but it will give him thanks.

---

### Post by SlackerTD on 2008-06-19
For python & game programming combined, you should head on over to the [pygame.org]("http://pygame.org") site, specifically, over at the [tutorials]("http://pygame.org/wiki/tutorials") section.

---

### Post by ucal on 2008-06-19
> **myromance123 said:**
> You ROCK dood !!  If I knew how to give you the beans I would !!

       Thnx so very much

Great!  Now go forth and design the greatest droidbattler!  :guitar:

---

### Post by Abras on 2008-06-20
> **SlackerTD said:**
> For python & game programming combined, you should head on over to the [pygame.org]("http://pygame.org") site, specifically, over at the [tutorials]("http://pygame.org/wiki/tutorials") section.
As someone who has been trying to learn pygame for quite some time I can say that the tutorials on the official site aren't that great. Thanks for the heads up on those games, though. I'll have to check them out. Pygame needs better newbie support, but for that it needs an enthusiastic community, which it does not have.

---

### Post by myromance123 on 2008-06-20
Cool, so many awesome replies. Thnx for the pygame tutorial page and the heads up on how much of a challenge python game making is.  I have started learning the python basics and hopefully will start using pygame soon :D

---

### Post by RIchard James13 on 2008-06-20
I've toyed with this idea of making a programming based RPG recently. My problem is not that I can't program but rather I have trouble trying to work out how to do the game mechanics. The ideas I have had so far are:

a) Make each section of the game a puzzle that can be solved by programming. The puzzles get harder as you go along. You are given a tutorial system to get you started. One example puzzle I thought of was having an impassable river. There is a bridge whose planks cannot be walked across because there are too many gaps. The bridge is created with a loop and the code is broken. Correct the code and the bridge will be passable.

b) Break programming up more atomically. Have it so that each time you attack a monster you need to write a program. And also write a program for defence. Different regions and monsters require more advanced programming techniques.

The problem with A is that you need a programming system so that the player can alter the world, and each puzzle needs to be made individually. 

The problem I have with B is that I'm not quite sure how that would work. What does code for attack look like?

Also note that neither of these will teach you computer game programming. They just teach you programming. 

I also have toyed with the idea of using a system like B for learning maths. I am a bit worried that there is too much hard work to make the game enjoyable.

---

### Post by myromance123 on 2008-06-20
Awesome idea man !! For B, when you say you dont know what writing codes for attacks look like, do you mean the code the player types or the game maker types? 

  If its the code by the player, then just make each attack have a specific code that fulfills the game makers attack codes and then have it initialize when pressing enter. Heck if its possible that is.
 
    I hope you dont give up, because you're idea sounds great !!
I plead to pro-programmers to please help out :D
 
       :guitar:

---

### Post by decoherence on 2008-06-20
> What does code for attack look like?

that's the question. maybe something along the lines of

```

inventory.mightySword(equip(leftHand))
while orc not dead:
   leftHand.mightySword(swing)
```

Exp will determine things like the rate at which the loop runs and how much damage 'swing' does.

The programmatic aspect of it makes it easy to get tactical.

```

if stenchOfDeath in targetMonster:
   inventory.holyWater(equip(rightHand))
   rightHand.holyWater(sprinkle)

```

which you might use against an undead monster!

These are basic and probably inconsistent examples, and I would imagine the player would be encouraged to define their own functions in order to save typing and build more complex behavior.

I think an RPG would be an excellent way to teach programming, specifically of the object oriented sort.

---

### Post by myromance123 on 2008-06-20
Thnx so much :)

    Every bit helps, I hope this helps with your part B ~
Keep going !! If this truly becomes a project I will be sooo happy :D

    and if it does, hopefully by the time of takeoff I will be able to lend a hand with the codes :]

---

### Post by ucal on 2008-06-20
You could make the B version of your game a traditional RPG in the sense that you equip weapons manually, and decide what attacks to use, but a programming rpg in that you program the spells.  As you level up, you get access to more output functions to make spells with (electricity, water, fire, that sort of thing).  You'd have to make it so there were many interactions possible to give it depth.  I don't know if its viable though.

EDIT:  You could also apply your idea to companions, in that you can add the ability for the player to program his companions.

---

### Post by myromance123 on 2008-06-20
" EDIT: You could also apply your idea to companions, in that you can add the ability for the player to program his companions. "

  Awesome idea dood :D  That would make the game a WHOLE lot more challenging,fun, and option-filled (sounds like quite a lot of work too~)
   Dang, I have just started learning to make loops with Python XD
       Lets see if I can help out by this month (hoping 100% !)

 Thnx for such a useful and cool idea :D

---

### Post by L337_K3y5 on 2008-06-21
> **RIchard James13 said:**
> 
b) Break programming up more atomically. Have it so that each time you attack a monster you need to write a program. And also write a program for defence. Different regions and monsters require more advanced programming techniques.


Lol, if you was good enough at python, you could dominate the game just by making your character godly or unrealistic defense capabilities.:lol:=D>
-Sorry, just a newb poking fun at the possibilities of what you could do without limitations set in place, make sure there are limits!:wink:

---

### Post by SlackerTD on 2008-06-21
> **Abras said:**
> As someone who has been trying to learn pygame for quite some time I can say that the tutorials on the official site aren't that great. Thanks for the heads up on those games, though. I'll have to check them out. Pygame needs better newbie support, but for that it needs an enthusiastic community, which it does not have.I didn't find them that bad when I was looking at them several years back. It did get me into thinking that I could code a game myself when reading through the tutorial... I ended up diving back into C instead & made a game with it. :)

---

### Post by RIchard James13 on 2008-06-21
Elimination of cheating could be done by restricting the number of times each line is executed. 

```
while True == True:
    attack(monster)
```

Another possibility is that the players code could be limited by the number of total lines run. This could be tied to experience points and then the player could use more powerful code as they progressed.

The other concern I have is how to get past basic stuff. It is pretty simple to write code that calls an attack routine. It is not so simple to write code that sorts a list of names in alphabetical order. Maybe a blend of option A and B might work. Different monsters need different types of attack. The easy ones can be finished off with attack/defend. The harder ones will require things like nested if statements and data structure manipulation.

I should also mention that my timeline for this project is to have it complete by mid 2009 to Christmas 2009. Coding does take time and I have to learn the ropes to be able to start programming such a complex game. I'm almost finished my first pygame game "tic-tac-toe" <- one has to start somewhere. In a few days I will move on to the next one.

---

### Post by myromance123 on 2008-06-22
Wow !! In 2009, thats fast for game coding considering what I have read on making games :D

    Hey, how are you going to handle game graphics ? Even if its 2D thats still work. Are you good to go for that? (If you plan to go all the way, which I hope you do :)  )  

   Its amazing if you can already make  a tic-tac-toe game X)
I have only been able to make codes for classes, and small stuff like that haha ;]

  Cheers to making games with codes ~

---

### Post by RIchard James13 on 2008-06-22
If I stick to 2D graphics it decreases development time. At the moment I dedicate about 30mins a day to game development. If I can continue at a similar rate that means ~180 hours of development time between now and the middle of next year. 1 year is a feasible development time for a small 2D RPG written by one person.

---

### Post by myromance123 on 2008-06-23
I would like to be of assistance to you, how much of python must I know? How did you learn python for gaming? 

   To do it all alone, and complete it in one year, you're one awesome dude ~  Maybe I could help you out in the 2D part? What is used to do the graphical part of a game? is pygame it ?  (I know lol, im offering to help yet I know not how to :D  ):lolflag:

---

### Post by RIchard James13 on 2008-06-24
Please don't jump my gun. Even though this is a program I want to make I am still quite behind in my skill level to complete it. In order to increase my skill level I need to do smaller games first, hence the "tic-tac-toe" game. 

What I have been doing for this game is looking around for a good gameplay mechanic. Which basically means how can I make a programming game fun AND also teach you programming. When you posted this thread I thought hey that person wants to play the game I was thinking of writing, but at the time I had not considered using Python as the in-game language but now it seems obvious. 

So I'm all ears for any ideas on how this should work but I'm not ready to write any code yet because I don't know yet how it should work. 

I have written some games but not completed them properly before. I have a space invaders game written in C++/SDL and another shoot em-up written in C using Ncurses, various other titles that I have lost over the years. The last time I tried a RPG was in 2003 and it err sucked. Mainly due to gameplay issues (map too small, game unbalanced etc). So this time I'm looking at how to get that game mechanic done properly, even if that means coding toy RPG games just to see how things could work. 

Also I'm increasing the amount of time I spend making games. Previously due to illness I have not done enough work to complete projects. Now I have lost some of the skill I once had and that is one reason why I try to dedicate 30mins a day to coding. The other reason is I'm a big procrastinator. I need to change my habit. I'm doing that by forcing myself to code for 30mins a day for a month. hopefully when the month is up I will be able to sit at the computer and churn through the code. At the moment I have some trouble doing that.

Could you help? Yes. At the moment I want to understand how the game should work. In the future when I start coding I may need people to design levels and/or maps, also graphics, sound effects and music. Otherwise just tell me to keep coding.

---

### Post by noerrorsfound on 2008-06-24
Someone has actually already been working on this: [http://iamar3d.com/](http://iamar3d.com/)

He started it in Irrlicht but moved it to OGRE.

---

### Post by myromance123 on 2008-06-24
Uuuu, I didnt know someone was working on a program like this :)

  Im sorry RIchard, I didnt mean to rush you or set rules or anything ~
Whatever the game code language you want to use please feel free to do so. (Im good for anything :D just interested in python thats all~)

 When I thought about this game, my idea was more on the lines of an rpg with battles that you fill in the required beginner programming language code to perform an attack(the code written is not the code used to make the attack happen, it just fills the blanks with the proper data) and then game code performs the attack when its text field requirements are met~

  The game code already knows the code there, it just needs the player to input it for the attack to happen.
  
   I was thinking for the characters leveling, each level you gain earns you a book(or scroll) with programming code(higher codes) for higher attacks. 

  The actual code written by the player does not have to be game making codes, but the beginning codes of that language, like if functions and while loops (there could be a hint bar with what the codes task is, to make the game slightly more educationally challenging).

  After which, you could make new versions of the game(just change the text input for players) to specialize in programmings different fields(uses) or different programming languages itself if you want~

---

### Post by RIchard James13 on 2008-06-26
I have a new idea on how this could be done. Instead of the code being some sort of abstract thing it is the programming for a machine. That machine being a spaceship, which has multiple processors. So each processor needs to be programmed. At the beginning of the game there is already code in the ship but it is not efficient. The code controls things like attack, defence, fuel efficiency (via navigation), trading or cargo handling. As you improve the code you can complete more complex missions. These gain you cash which you can use to upgrade each of the ships systems from the shield to the shield processor. If you upgrade the processor you can increase the amount of code it can execute and how fast it executes.

I'm not certain how this would work. I'll probably need to make a prototype game to play with the mechanics some. One thing I can't quite work out is execution speed. Because you can't judge code by the number of characters or the number of lines, for example the following 2 pieces of code do the same thing.
[PHP]if attacker_weapon == "plasma" and shield_plasma == "ready":[/PHP]
[PHP]if attacker_weapon == "plasma":
    if shield_plasma == "ready":[/PHP]
Both pieces of code do the same thing but differ in their execution scheme depending on how they are interpreted. I could model the game so that python is compiled into some pseudo-machine code for each processor or I can count the lines executed or I can count the number of characters read in by the interpreter, or I can count each individual python instruction. Anyway enough of my rambling I'm sure I'll work something out.

---

### Post by myromance123 on 2008-06-26
That is definitely an awesome concept ~ Having 4 processors with capability to be upgraded with the users code and further upgraded with new parts. 

Dont forget though, this game also has to be compatible with beginner programmers(capable programmers may not be that interested), so the code for upgrading has to be quite simple at first and since the code will be used to upgrade the ship from already very basic functions, that may be hard to achieve.
( Instead there could be an optional tutorial, where the player gets to just type in the code for the basic functions following a simple how-to)

 But this is all still a challenge to complete and I salute you for it~ :)
You could start off with a simple text version of the game(like b4 arcades were in existence XD ) and this could just teach even more basic programming like pseudo code (to make things start off easier and show playable results). That might be a good way to start ( I dont know, Im just sprouting words lol)

 I couldnt understand very well your last paragraph, sorry Im still in my newbie stages :]  
(What I understood was that you're not sure what format the code should be in for optimal execution and user-friendliness, but hey what do I know :P)

A question to all able programmers who read this:
  Did you learn programming through your own means or was it in college/university ? (Just want to get a heads up on how capable programmers are born)   :guitar:  Too much talk lol sry ~

---

### Post by RIchard James13 on 2008-06-28
Had another idea about the problem with people not knowing where to start. If the game includes a set of challenges for the player to complete that introduce basic programming concepts then that should work. Also the processors cannot run all at the same time as that is an advanced concept. 

As for your question about how do people learn programming. I know of at least two ways. I learnt by myself with Commodore VIC-20, I had very few games and had to resort to making my own. This caught on and I became hooked at programming. The other way is to go to a formal institution like a school or University and learn through their courses. It all depends on the person and the type of learning they take in.

Of course everyone has different abilities don't ask me to draw anything but basic graphics.

---

### Post by myromance123 on 2008-06-28
Wow, you were there when they sold those ~ Heh, the oldest computer I know is a Win95 :P 

   So self-taught is also possible, although I am having troubles trying to truly understand the languanges concept and manner of function. I like the idea of the challenges teaching the basics~ 

  For a game like this, do you make your own engine or borrow ideas from other engines? Or is it not even necessary for a 2D game?  I also read that it takes great mathematical abilities for 3D rendering and to be a graphics programmer or even an AI programmer. Is it hard to achieve ?

  Do you apply math in your programming? ( I mean high lvl math ~)
Anyhow thanks for continuously replying, Im learning a lot :D

  Rock on dude ~ :lolflag:

---

### Post by grossaffe on 2008-06-29
so what's the deal with python, anyways?  It took over as the entry-level computer programming class at my university.  is it supposed to be easier than java?

---

### Post by RIchard James13 on 2008-06-29
Python is slightly more easier to learn than Java. Consider the following code that compares two strings

In Python (Ignore the php tags they just colour the code)
[PHP]
    string1 = "you"
    string2 = "me"
    if string1 == string2:
        print "you is me"[/PHP]

In Java
[PHP]String string1 = "you";
String string2 = "me";
if ( string1.equals(string2) )
{
    System.out.println("you is me")
}[/PHP]

Most people learning Java assume that the == will give you a string comparison but it does not it compares the object's references. Java however is a powerful language. Many businesses rely on it. Python is just a bit easier to learn.

Of course once you get to a certain level of programming skill you can program in what ever language you desire, or your job requires. Which reminds me I need to port some Python to 6502 Assembly language.

Don't be afraid to learn Java thinking that Python will usurp it. That is absurd, you are learning programming not Java. Even though the game I would like to write is using Python it is going to be teaching programming. Stuff like variables, loops, conditionals, flow control, functions, passing variables, scope, object orientation. 

*Note: For the purists the game will teach procedural and object oriented programming. Maybe a little functional programming will be added.*

---

### Post by myromance123 on 2008-06-30
That is quite true~ Python is a whole lot easier, I have had an easier time learning programming ideas and functions with it compared to C and Ruby (Just what I experienced). Its a good place to start.

  Just one thing I dont get still, python is said to be all object-oriented but what does object-oriented mean? Will the game you make be affected by this?  Why aren't all programming languages object-oriented?

     If you were to make the game 3D would it be impossible since you are on your own right now? 

  Man Im off with the questions ~ Feel free to answer or not answer :P
         All I need is a textbook with programming concepts,
                      and Im good to go XD

:guitar:        Oh yeah, since the player upgrades the processors to his liking, Im guessing there has to be inter between missions for this to happen eh. Would it be easy to supply documentation for this game?

---

### Post by myromance123 on 2008-06-30
Ok I have been asking to many questions, and from what I have read this is what newbies do and it can be very annoying, so Im sorry Richard please pay no attention to my previous programming questions, I shall study and find out for myself :)

  Please do keep me posted on your ideas for the game, hopefully sometime soon I could contribute something solid to help ~ 

 Cheers :guitar:

---

### Post by RIchard James13 on 2008-06-30
I am not bothered by many questions. Even if they are noob like questions. I spent 6 years working as a computer technician and part of my job was explaining complicated topics to computer illiterate people. The only reason I may not reply straight away is that I have trouble composing my thoughts into writing.

As for the high level maths. Most programmers don't need to use it. Sometimes it is necessary though. In 3D graphics you once had to know a lot of maths but modern libraries can take care of many aspects so you don't need to understand if translation and rotation of objects goes before translation and rotation of the worldscene any more. 

As for making the game 3D it is not that hard. What would be hard then is that the programming in the game would need to deal with 3D which means the person playing it would need to understand 3D concepts like space battles. Another thing I will probably chuck out with the 3D world is Newtonian physics. There have been many games done that use that in space and it makes combat awkward. With Newtonian physics objects are moving at different accelerations and directions and you need to calculate where they will be in weapons range in order to fire. If on the other hand I stick to a turn based strategy style of combat like in many console RPG's then things are a lot easier. 

I can divide space up into a 2D grid and if two ships are in combat range they can have a turn based battle. This simplifies the programming of the ships combat computer.

As for the status of the game, hopefully I will make a prototype today or on Thursday. I finished my Tic-Tac-Toe game using pygame and have converted it to run on a VIC-20 using 6502 assembler.

*EDIT*

I should add that the reason for not doing Newtonian physics can be summed up in the following example. Imagine two people go to fight each other with sticks. They walk towards each other and then stop and whack each other with the sticks. The reason they can stop is that on Earth there is friction from both the air and the ground. Now imagine those same two people in space they move towards each other but they cannot stop so they fly past each other. They only have a small time frame in which to whack each other with their sticks. In order to turn around and have another fight they need to decelerate using some form of rocket motor, then they need to accelerate in the opposite direction toward the other person, where they will fly past again. 

Having said that it is possible for two objects in space to stop and meet each other within attacking distance and stay that way but the amount of calculation of how to do so is very complex especially if the objects are already moving at high speeds. You can see this when astronauts take a space walk or when the space shuttle docks with a space station. However these slow speeds take time to reach after you have been moving at high speed (high enough to get between planets). Also the speeds needed to get between planets is quite high and they are not in a straight line between each other because they all orbit at different speeds. If tomorrow you chose to fly to Mars you might end up hitting the sun. Some months it takes less time to get from Earth to Mars some time it takes more.

Dealing with the time issue is difficult. Some games have chosen to use unrealistic travel measures to avoid this. One of the later Elite sequels enabled the player to accelerate time during trips. I prefer the use of unrealistic travel and fake friction in space, just because it makes everything easier. I want to make a game about programming not one about calculating launch windows and orbital trajectories.

---

### Post by estyles on 2008-07-01
Sounds interesting.  I particularly like the idea of making a droidbattles-style of game using python.  Which leads me to two divergent thoughts:

1) Whatever happened to droidbattles?  I just discovered this game in the couple of months, and I really like it.  I haven't had the time to devote to it that I'd like and I haven't really designed a droid that can defeat the default "Circles" droid with regularity (I had a cool idea, but it just tries to do too much processing on each step and gets bogged down - needs either way less complexity or more processors), but I like it.  The thing is, there were some community sites for it, but both appear to be long dead, and as far as I can tell, no one plays it anymore.  Would be interested in starting up a new group of players if others are interested.

2) I've had an idea for a game which I think would work well with the python-game theme.  I don't know python, although I started teaching it to myself once until I decided that I wasn't going to take the job that required python even if it was offered (wife wasn't up for relocation), but the game idea would definitely work well with a simple programming language like python.  

The idea is this: "The Wars of the Future Are Fought in the Past".  You are a general (or an engineer, or whatever) in the future, and a military objective has been found in the past.  You must construct drones to send into the past to fight over those objectives.  Each battle is fought over a set number of turns, with a minimum and maximum number of iterations (if either side wins the objectives between the min and max iterations, the game ends in that side's favor).  Each iteration, you can send a certain number of CP's worth of drones to the past, they enter the battle at your insertion point, at a turn that you denote.

Frex, the first iteration, you send a drones to your insertion point at turn 0, as does your opponent.  Your opponent's drone pulls off some sort of tricky move at turn 4, and destroys your drone.  Eventually, you reach the end of this iteration (say, turn 10, or 50 , or whatever).  At that point, you can decide to send a second drone back to your insertion point at turn 4 (or earlier), to try and make the second iteration go differently and save your first drone from destruction.  That is, the same set of turns is run several times, with different initial conditions, presumably with different results each iteration.

Your drones would have certain components (motivators, trackers, weapons, graspers, 'porters, converters), and some programming to make them work.  The objectives would be things like strategic points, scrap metal, converted enemy drones, etc...

The original idea was to do all the "programming" of your drone via radio-buttons and options in a menu, thus limiting how much you could really optimize your drones.  But if you actually did some programming with python, it would really increase the customization.

Of course, I also like the idea of an RPG, but it would make a lot more sense to be a futuristic RPG, rather than fantasy, if you're using programming...

---

### Post by RIchard James13 on 2008-07-02
> **estyles said:**
> "The Wars of the Future Are Fought in the Past"

That does sound interesting

> **estyles said:**
> Your drones would have certain components (motivators, trackers, weapons, graspers, 'porters, converters), and some programming to make them work.  The objectives would be things like strategic points, scrap metal, converted enemy drones, etc...

Those ideas have great potential. I could even use them in a non-combat setting. Say you launch a droid from your spaceship to a planet or asteroid. Then you have some task to fulfil there mining, rescuing people, flipping switches etc. The player has to write a program that navigates their droid in the environment and the droid itself manipulates the world, flipping switches and using teleporters, moving objects etc. Droids can be upgraded in the game so different missions need certain upgrades. The player has to be given a rough map and a list of objectives before the mission otherwise their droid would fail. This could be added into the game I am making, giving the player more options in how to increase their skills makes the game more fun.

I have started on my first prototype for trying some of these ideas out.

---

### Post by myromance123 on 2008-07-03
> "The Wars of the Future Are Fought in the Past"

 That sounds like an awesome idea ~   The non-combat setting taking place first as a way to "level up" your drone/ship/robot (with new python programming for each tasks fulfillment, each being new/complex programs) would be so awesome !

  One thing I have found with available programming games is that instructions on how to play/program in the game are not beginner friendly (from what I've experienced) so it might do this game great good if you could insert a how-to-play after you've made it for beginner and advanced programmers~

  If this game is going to have a story and its in 2D, does that mean the story will have to be in text only? (no short 2d cutscenes or anything?
  Would it be a hassle ?

I was also thinking that for the code input by the player, it doesnt have to be actual code to run the action, it can just be a [COLOR="SeaGreen"]fill[/COLOR]-[COLOR="SeaGreen"]in[/COLOR]-[COLOR="SeaGreen"]the[/COLOR]-[COLOR="SeaGreen"]blanks[/COLOR] type of user input game so that the code to make the actual action (shoot,land etc) happen is just  a [COLOR="Blue"]TRUE[/COLOR] or [COLOR="Red"]FALSE[/COLOR] situation for the data input, where the data input would be validated from a list of functions/loops etc to determine whether it matches with the required input (where IF input_function = TRUE, THEN display shootanimation, Else Display shot-missed or something on the lines of that)
 
 I think that would make it easier for you, no? Yes it most probably will hold the player back from using his own coding ideas but it could be just used in the first part for starters and it would also make this game programming language specific. I was just thinking it would be an easier start, correct me if Im wrong ~

  Thanks for putting up with my questions XD 
Awesome ideas dudes~ :lolflag:

---

