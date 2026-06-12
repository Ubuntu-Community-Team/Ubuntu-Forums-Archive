---
title: "Games ARE NOT INSTALLING CORRECTLY!"
date: 2012-06-17
forum: Gaming &amp; Leisure
---

### Post by meathdeath on 2012-06-17
I am not sure what the problem is with games that i install because i follow tutorials from online and they say they are in my games folder but when i go to launch them they dont launch successfully. For example Shank is glitchy, alot of blacked out areas on the menus and Super Meat Boy closes as soon as its launched. Amnesia stops at the loading screen with the sun emblem. Any idea what is wrong?

---

### Post by Perfect Storm on 2012-06-17
Try launch the games via the the terminal.

Also post you PC specs, which video driver you're using and version of Ubuntu.

---

### Post by meathdeath on 2012-06-17
how do i launch games in terminal?

Specs:
4GB DDR2 ram
Intel HD graphics (mobile)
Pentium 6100 CPU @ 2.0ghz
Ubuntu 12.04 LTS

i should be able to play these games without problems no?

---

### Post by meathdeath on 2012-06-17
Thanks for the reply i understand now. Sadly that did not fix the problem.

---

### Post by Perfect Storm on 2012-06-17
It's not meant for fixing but for finding the problem. Post the output.

> Intel HD graphics (mobile)

Properly the problem. 3D games works poorly with Intel cards on Linux.

---

### Post by meathdeath on 2012-06-17
> **Artificial Intelligence said:**
> It's not meant for fixing but for finding the problem. Post the output.



Properly the problem. 3D games works poorly with Intel cards on Linux.

super meat boy and shank are more along the lines of an arcade game not a 3D game.

---

### Post by bud986 on 2012-06-17
Basically you need a dedicated gfx card to run amnesia.

---

### Post by thatguruguy on 2012-06-17
> **meathdeath said:**
> super meat boy and shank are more along the lines of an arcade game not a 3D game.

True, but that doesn't mean you should read the [minimum system requirements]("http://support.humblebundle.com/customer/portal/articles/261150-humble-indie-bundle-4-system-reqs").

Here's the one for Shank:
> _Linux_:      Processor: Intel Pentium 4 running at 1.7 GHz or Greater; Athlon 64  running at 1.7GHz or greater with support for SSE2 instructions
    Memory: 1 GB of ram, 1.5 GB (Vista and Windows 7)
    Video Card: ATI Radeon X1800 GTO 256MB and the Nvidia GeForce 6800 Ultra 256MB cards
    Misc: May require Vsync to run smoothlyHere's the one for Super Meat Boy:
> 
     _Linux_:
      Processor: 1.2GHz processor
    Memory: 256 MB RAM
    Graphics: Graphics Card that supports Pixel Shader 2.0 and Vertex  Shader 2.0 (Vertex Shader Support can be supported with software  emulation)
    DirectX®: DirectX® 9.0c
    Note: May not work with Intel Integrated Graphics
Also, from the Amnesia: The Dark Descent section of the Humble Indie V Bundle minimum system requirements:
> _Note_: Integrated graphics and very low budget graphics cards might not work.
In other words, you should ALWAYS check the minimum system requirements. If you don't meet the minimum system requirements, you can't be surprised that the games don't work the way you want them to.

---

### Post by meathdeath on 2012-06-17
> **thatguruguy said:**
> True, but that doesn't mean you should read the [minimum system requirements]("http://support.humblebundle.com/customer/portal/articles/261150-humble-indie-bundle-4-system-reqs").

Here's the one for Shank:
Here's the one for Super Meat Boy:

Also, from the Amnesia: The Dark Descent section of the Humble Indie V Bundle minimum system requirements:

In other words, you should ALWAYS check the minimum system requirements. If you don't meet the minimum system requirements, you can't be surprised that the games don't work the way you want them to.

Thanks for all of that information. Based on what you just said my system should still be able to run Shanks and Super Meat Boy. This is confusing.

---

### Post by thatguruguy on 2012-06-17
> **meathdeath said:**
> Thanks for all of that information. Based on what you just said my system should still be able to run Shanks and Super Meat Boy. This is confusing.

I'll assume you weren't able to read what I posted, so I'll write slower this time, or something.

Shank:
> Video Card: ATI Radeon X1800 GTO 256MB and the Nvidia GeForce 6800 Ultra 256MB cards
You'll notice that it doesn't list an integrated Intel graphics card as a possibility. 

The Super Meat Boy requirements are even more direct, in that they specifically state:
> Note: May not work with Intel Integrated Graphics
I fail to see what is confusing about any of this, really.

---

### Post by Mr Lanun on 2012-06-17
**Integrated** graphic cards can't run most, if not all, recent games, even using Windows. You'd need a **dedicated** graphics card for any serious gaming.

---

### Post by meathdeath on 2012-06-18
> **thatguruguy said:**
> I'll assume you weren't able to read what I posted, so I'll write slower this time, or something.

Shank:

You'll notice that it doesn't list an integrated Intel graphics card as a possibility. 

The Super Meat Boy requirements are even more direct, in that they specifically state:

I fail to see what is confusing about any of this, really.

wow i just cant read today i dont know what my problem is :lolflag: sorry

---

### Post by Perfect Storm on 2012-06-18
No worries :popcorn:

If you have a desktop with a dedicated video card you can run the games there.
Then perhaps have some lightweight games on your laptop.

---

### Post by oldrocker99 on 2012-06-19
> **Artificial Intelligence said:**
> No worries :popcorn:

If you have a desktop with a dedicated video card you can run the games there.
Then perhaps have some lightweight games on your laptop.

Some lightweight games that run on laptops include most turn-based games (Wesnoth, AAA, the roguelikes). I can attest that 7kaa (Seven Kingdoms Ancient Adversaries, a RTS game) runs on about anyhting, and it was a great game when I played it in the distant past, and it's still a great game. If you're dismayed that the game doesn't include a manual, the manual is available for cheap from GOG.com, along with the M$ version of the game. They have LOTS of games that run great under wine or DOSBox.

It's not free, but the best damn turn-based game I have EVER played, Dominions 3, also runs on just about any machine.

---

### Post by Ranko Kohime on 2012-06-29
I'm running Amnesia on Intel HD 3000 graphics:

Install driconf:

```
sudo apt-get install driconf
```

Then open driconf, click Image Quality tab, and enable S3TC.

Amnesia, despite it's suggested hardware, is NOT that demanding.  And Intel HD graphics are severely underrated.

---

