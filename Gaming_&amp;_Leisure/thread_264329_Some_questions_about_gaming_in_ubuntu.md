---
title: "Some questions about gaming in ubuntu"
date: 2006-09-24
forum: Gaming &amp; Leisure
---

### Post by rekahsoft on 2006-09-24
I have been using just ubuntu for about half a year now and have been using linux for about two years. I sometimes enjoy to game and just baught Halflife 2 episode 1...i apsolutly hate windows and wanted to put windows xp on my portable drive so i could keep my laptop windows free. So i first installed windows xp to my laptops disk then atempted to copy it to my externel drive...i found that it just doesn't work...:'(...I have a radeon 200M and have yet to get the ati propriatary drivers working (i have been trying for a couple monthes now) so i can't run any games with Wine. So basicly i am stuck with letting microsoft win because i will have to leave windows on my laptop...so what i want is to have windows off my laptop...the prefered would be to be able to play games in ubuntu (btw where is gaming at in linux? is Wine up to Direct X 9 libraries yet? Is it faster (i am assuming it is slower because it is OpenGL)) but if need be i wouldn't mind if i could get windows onto a portable drive and game off the portable drive at my leisure. Thanks for the input and help.

---

### Post by Donshyoku on 2006-09-24
These are questions that I have been wrestling wtih for some time, and as such, I think I have a bit to add to your confusion.

First off, running games natively (that is, those games with Linux versions) are usually quite a bit faster and more stable than Windows.  Linux uses about 50-60% less RAM than Windows, freeign that up for your game to access. Furhter, OpenGL is really a superior format in terms of speed even though DirectX/Direct3D has some functions that OpenGL does not.  To see if OpenGL is effecient and gorgeous look at Quake and Doom over the years.  

But the problem arises, like in your case, when you want to play a game in Linux that does not have that native suppport.  There are really two options and I have been flirting around with both of them for a few weeks.  Firstly, there is Transgaming's Cedega application ([www.transgaming.com)](www.transgaming.com)).  It is, more or less, a graphical interface for Wine, but includes some optimizations and bug fixes specifically for gaming and particular games.  They have a voting system for members in which they can vote on the new features and bug fixes they want most focused on for the next patch.  I find that this works the best for me, but as with all the other "emulation" programs, it only supports DirectX8.1 with pixel shaders up to v1.4.  A lot of games nowadays are using 2.0 and there is starting to become another shift now to 3.0.  It isn't estimated for Wine/Cedega to support 2.0 until mid-2007.  Cedega is a paying membership program.  You pay $5US/month and have to pay for three months ($15US) when you first start your membership.  This money supports the company and allows you access to patches and new versions as they arrive.

The other option, and the free (as in beer and freedom) one, is Wine.  Cedega itself is based off of Wine, but as mentioned, contains some additional codea and a graphical interface in which to operate.  Wine is easy to install (it is in the repositories), so it is easy and free to give it a shot when you get some time.  I have been trying to learn this program the last few days, and have run into some problems.  I can get things installed (navigate to the exe directory and run **wine setup.exe**.  The game will install using the game's inteface, just as Cedega... but I haven't been able to launch a single application I have installed.  It cannot navigate to the directory of the exe, so I aligned exe's with Wine.  This worked in a way in that Wine tries to open it, but again, I am getting silly errors that prevent me from reaching the game's menu.  

I am currently typing this on WindowsXP as I want to play Far Cry. It works great with Cedega, but the lack of pixel shaders 2.0 really uglify and beatufil game.  I am hoping to see a big transition when Cedega/Wine incorporates 2.0 shaders as that will mark a huge leap in graphics (3.0 was rather a small hop above 2.0).  

Moral of the story:  Try Wine and see if it works for you.  If not, and you are willing to spend %$15US, download Cedega and see if you are satisfied with its performance and quality.  If it comes down to it, slap Windows back on a portion of your hard drive and pray for the devs to start looking at Linux and perhaps porting a few more apps to it natively, the real ultimate goal.

---

### Post by rekahsoft on 2006-09-24
Yea...i think i will have to put windows on a partition so i can play games...it is sad because i hate windows but am forced to use it:'( Wine needs some work and i just can not for the life of me get the ati propriatary drivers working...(i have a Radeon 200M and have tried every tutorial out there).

---

### Post by rekahsoft on 2006-09-24
well...i just removed windows...and i now vow i will not use windows for any reason...microsoft will not win with thier propriatary software!!! Now...linux gaming HAS to be IMPROVED!!! right now it is not up to par. For home users to switch to ubuntu they will need good game support. Contribute to Wine!! I am going to because i see the need in the project.

---

### Post by nalmeth on 2006-09-24
Did you get the ATI drivers working?

---

### Post by rekahsoft on 2006-09-24
No...it is basicly hopeless...i have tried and tried and fglrxinfo keeps saying i am using the Mesa drivers...help would be apricated.

---

