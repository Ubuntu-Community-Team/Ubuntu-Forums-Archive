---
title: "[Volunteer Request] Dwarf Blast (Bomberman-style 2D game)"
date: 2011-04-18
forum: Gaming &amp; Leisure
---

### Post by wolterh on 2011-04-18
**CONCEPT**
The game is a 2D bomberman-style game, with dwarf characters and a little of gore involved.

**LICENSE**
The game is open-source, and it is licensed under the CC-BY-SA v3.0 license.

**TECHNOLOGY**
Language: Python
Libraries: Pygame

**PROGRESS**
The game has a lot of its core already developed, it is mostly missing only the AI of computer players, menus, and game logic.
Here you can see a video of how the game looks so far:
[http://db.tt/0xrfwBs](http://db.tt/0xrfwBs)
**Note:** in the video, the explosions were not captured, but they do exist. The meatchunks that fly off of the dwarf are supposed to rotate and bounce off of objects. The "FIRE" texts are solely for debugging purposes as I was having some trouble with them.

If you have any questions, please feel free to ask.

---

### Post by wolterh on 2011-04-21
Bump! Help wanted, python programmers and 2D artists are the main interest

EDIT:
For those who cannot view the video, here is a screenshot of the game:
[IMG]http://i.imgur.com/OyDey.png[/IMG]
*The dwarf player was next to an exploding bomb, causing meatchunks from his body to fly off violently, in a normal non-testing occasion, this would cause the dwarf player to die*

So far, what is implemented is the following:
 * Easy 2D frame animation system
 * Intelligent layer-based rendering system (for floor, decals, objects, and overlay objects like text)
 * Collision detection
 * Explosion sensing
 * Meatchunks that fly from the dwarf's body do so in a direction parallel to the distance between the dwarf and the explosion center
 * Input handling

The next tasks in the TODO are:
 * Map loading
 * AI Players (and their path-finding)
 * Basic HUD
 * Get sprites done (for maps, player walk-vertical animations, etc)

This project is ideal for those who just want to gain experience in game development and programming in general. Though the math and physics in the game are all taken care of, there are plenty more challenges to overcome.

---

