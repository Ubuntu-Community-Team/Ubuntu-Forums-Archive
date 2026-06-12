---
title: "3d engine for exercising game"
date: 2010-03-11
forum: Gaming &amp; Leisure
---

### Post by granadajose on 2010-03-11
Hi all,

I am currently designing an application for storing and displaying exercising routines. For instance, the user can learn how to stretch correctly before a workout or even follow an aerobic class. For this purpose, I would need a 3d engine able to display an animated character over background. As I want to include the ability to custom the character (male, female, clothing, etc.) and the background (garden, top of a skyscraper, etc.) I can not pre-render the videos in an application such as Blender. I can program in C, C++ (and I am willing to learn new programming languages if necessary). Do you know of any 3d engine for Ubuntu fit for this idea?

Many thanks for your help!

Jose

---

### Post by Ferrat on 2010-03-11
You might want to check out Ogre3D [http://www.ogre3d.org/](http://www.ogre3d.org/)

---

### Post by granadajose on 2010-03-11
Many thanks for your suggestion! I will give it a look. However, I am afraid that it is not easy to start using it in Ubuntu. Also, do you know if it is fit for build the "cutscenes" that I need for the application I have in mind?

Many thanks for your help!

Jose

---

### Post by Ferrat on 2010-03-11
It's a fully developed 3d engine, should be able to do what you want with some tweaking but I don't think you will find one that does exactly what you want out of the box, it's just a 3d engine, you will have to do the rest yourself.

If you want a full game-engine you might wanna go Python/C++ and look at Panda3D developed by disney and used in their own games. [http://www.panda3d.org/](http://www.panda3d.org/)

---

### Post by CharmyBee on 2010-03-11
Panda3D's very slow. It will take the CPU and step on it a lot for simple diffuse model rendering. If you've tried Toontown Online like I have on a 3GHz system, you know 10fps on a Radeon HD card is very wrong when you're just playing on the trolley, and don't get me started on Pirates Online... the animation is jerky even when the framerate is great.

I'd recommend Cube2 instead for that. It has MD5 support, and for that you can move bones variably I think. I also find it strange that engines built for standard FPS games are much more streamlined and simpler to use than general engines and layers like Crystal Space and Ogre3D.

---

### Post by drwr on 2010-03-11
Pardon me for butting in, but--huh?  Really?  10fps playing Toontown?  If that's true, there must be something terribly wrong, since even people with the world's crummiest hardware get consistently better than 25-30 fps in Toontown.  Certainly a decent system such as you describe should be pegged at 60 fps most of the time.  Of course, like any MMO with dynamically-generated avatars coming and going, there can be occasional chugs as you run around and encounter new people, but this isn't the fault of the game engine.

Also, I don't know what you're talking about with the animation of Pirates being choppy.  Are you referring to other avatars' movement?  Or something else?

CPU utilization is yet another issue with is completely unrelated to performance.  Depending on your settings, Panda can be configured to use all available CPU, or only as much as it needs.  There's usually not any reason not to take it all, since unused CPU is wasted CPU.

Not that it matters much to the OP's original question.  There are many reasons to choose one graphics engine over another, and the OP didn't indicate whether raw performance was more important than anything else.  Still, Panda3D can hold its own head-to-head against any other graphics engine in terms of raw vertex crunching--pretty much every engine does the same thing there, just sends vertices to the GPU as fast as possible, so any comparisons of performance of graphics engines are usually misguided.  The real questions come down to how easy is it to use.

David

---

### Post by granadajose on 2010-03-12
Many thanks for all your suggestions! 

Panda3D seems to be a very good fit for the game I plan to develop (thanks for showing me this engine, Ferrat!). It is easy to install and it has a lot of polished tutorials, samples and documentation. In fact, my idea would not be much affected by performance, since it only a few characters (2-3) and small scenarios. It is much of a "casual game". I think that this niche (casual games) is a big opportunity for Linux. While super-productions (such as God of war III, and its 44 $ million budget) may be currently out-of-reach for Linux, the casual games are easy to develop and they can appeal a wider range of users.

Ogre3D and CrystalSpaces seem to be great options, but they seem to be too difficult to install and run the demos for a beginner. This is the first game I develop in quite a long time and I would appreciate a learning curve not too steep.

I have also been looking into the Cube2 engine, but it seems a bit too oriented to FPS games and there isn't much documentation available.

---

