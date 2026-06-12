---
title: "Tux Picross"
date: 2010-03-19
forum: Gaming &amp; Leisure
---

### Post by schuay on 2010-03-19
picmi contains

* a picross clone (see [http://en.wikipedia.org/wiki/Picross](http://en.wikipedia.org/wiki/Picross)  )
* a minesweeper clone (see [http://en.wikipedia.org/wiki/Minesweeper_(computer_game]("http://en.wikipedia.org/wiki/Minesweeper_%28computer_game")) )

[[IMG]http://img688.imageshack.us/img688/6931/tuxpicross.th.jpg[/IMG]]("http://img688.imageshack.us/i/tuxpicross.jpg/") [[IMG]http://img340.imageshack.us/img340/6931/tuxpicross.th.jpg[/IMG]]("http://img340.imageshack.us/i/tuxpicross.jpg/")[[IMG]http://img519.imageshack.us/img519/421/picmi.th.png[/IMG]]("http://img519.imageshack.us/i/picmi.png/")


For more information, please take a look at the github site or the archlinux forum thread (see below)

Github: [http://github.com/schuay/picmi](http://github.com/schuay/picmi)
Archlinux forum thread: [http://bbs.archlinux.org/viewtopic.php?id=92600](http://bbs.archlinux.org/viewtopic.php?id=92600)

**New Packages:**

Now available from [B]ppa:jakob-gruber/picmi
[/B]
Step by step installation:

Open a terminal and enter:     
             sudo add-apt-repository ppa:jakob-gruber/picmi
sudo apt-get update
sudo apt-get install picmi

For more information, see [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

Enjoy!


**Updates:**

2011-09-07: Updated ppa with picmi-1.3.1-2 for 11.04 natty

---

### Post by _h_ on 2010-03-19
Is it clean?

---

### Post by schuay on 2010-03-19
> **_h_ said:**
> Is it clean?

Err.. What do you mean? :)

PS: yeah it's [squeaky clean](http://allcarsreview.com/wp-content/uploads/15611.jpg)

---

### Post by n0dix on 2010-03-19
Did you post days ago a post in the Arch forum related to this game?
Btw, i don't know anything about the game but looks great.

---

### Post by schuay on 2010-03-20
> **n0dix said:**
> Did you post days ago a post in the Arch forum related to this game?
Btw, i don't know anything about the game but looks great.

Thanks, give it a try (it's addictive).

Working on a minesweeper implementation within this framework at the moment, we should have 2 games in 1 soon :)

---

### Post by schuay on 2010-03-27
Added a .deb package for an easier installation.
Link is in first post.

:popcorn:

---

### Post by Yvan300 on 2010-03-27
Looks intimidating!

---

### Post by schuay on 2010-04-04
1.1.1 is now available (see first post for link).

New stuff in 1.1.0:
 * Minesweeper
 * Rewrote / restructured large  parts of the code
 * Settings moved to separate form
 * Various  minor changes / fixes

New stuff in 1.1.1:
 * Fixed missing  icon
 * Automatically expose an initial area in minesweeper

---

### Post by schuay on 2010-04-11
1.1.4 is now available.

picmi-1.1.2    
    * fixes and tweaks
     * preliminary work on statistics (highscores and more)

picmi-1.1.3     
    * display aggregated stats on game end
    * changed  default picross background
    * changed mine icon

picmi-1.1.4
     * more tweaks game over screen
    * moved all sdl objects to  smart pointers
    * other minor fixes / changs

---

### Post by schuay on 2010-04-25
1.1.7 is out.

picmi-1.1.5
    
Display top 5 games in current category
Fix  floating point format error (thanks hatten)
Don't show lost games  statistics for picross

picmi-1.1.6
    
Games can now be  paused by pressing the p key
Keyboard controls added to minesweeper  (similar to picross controls, see README or 'picmi -h')

picmi-1.1.7

added help form
display all times in 1m13s format
difficulty presets added
clear stats option added
remove minesweeper winning option (all bombs marked -> win) since it can be used to cheat
better placement of minesweeper info area
better placement of game over screen

---

### Post by Bölvaður on 2010-04-26
**picmi** is exactly what I was looking for.
is there a 64 bit deb package or do I need to get it from the git repo?

---

### Post by schuay on 2010-04-26
> **Bölvaður said:**
> **picmi** is exactly what I was looking for.
is there a 64 bit deb package or do I need to get it from the git repo?

Hi, 64bit package added to first post :)

---

### Post by Rustybolts on 2010-04-26
64bit deb feed back..
I am getting this error
[COLOR=Red]Error: Dependency is not satisfiable: libqt4-xml (>= 4:4.5.3)[/COLOR]

---

### Post by schuay on 2010-04-27
> **Rustybolts said:**
> 64bit deb feed back..
I am getting this error
[COLOR=Red]Error: Dependency is not satisfiable: libqt4-xml (>= 4:4.5.3)[/COLOR]

Hm, I built the 64bit deb with 10.04, sorry bout that.
I will rebuild it with 9.10 sometime today.

---

### Post by schuay on 2010-04-27
Rebuilt for karmic, see first post. Please let me know if it works for you.

Offtopic - libqt4-xml in karmic is version *4.5.3really4.5.2*. Wtf is that :)

---

### Post by Rustybolts on 2010-04-27
When i clicked on link it asked if i wanted to save or open with Gdebi package installer. 
As usual i picked option of gdebi only to get this error
[COLOR=Red]tmp/picmi_1.1.7-1_amd64_karmic-3.deb could not be opened, because the associated helper application does not exist. Change the association in your preference[/COLOR]
However it did work for me when i saved the file and then opened using Gdebi package manager. :confused:  Oh well...

T.y for deb

---

### Post by schuay on 2010-05-23
1.1.9 is now available. Both debs are now built for Ubuntu 10.04, they probably won't work with earlier releases.

picmi-1.1.9
  
* fade in at game over can be aborted early by pressing any key 
* 'r' can be pressed at game over screen (or during fade in) to 
  restart game with identical settings 
* fixed bug which made high score table not respect difficulty 
* sane limits for difficulty/board size in settings form 
* further minor changes

picmi-1.1.8  

* installation now handled by makefile 
* remove rotation hacks (use special 90deg rotozoom func instead)

---

### Post by schuay on 2010-06-26
1.2.0 is now available from **ppa:jakob-gruber/picmi** (see first post for more instructions)

Changelog:

```

picmi-1.2.0
 * minesweeper perfect puzzle algorithm implemented: 
   puzzles can now (optionally) be guaranteed solvable. 
   the generator is still slow and will hopefully be improved 
   in the next few releases. 
   requires boost::thread. 
 * mine density limit raised to 35% 
 * new minesweeper difficulty preset "very hard" 
 * more tweaks on game over screen 
 * added more control options: arrow keys, numpad keys, 
   wasd keys, or hjklbnyu keys
```

---

### Post by DancemasterGlenn on 2010-07-18
If I could meet you, I'd shake your hand. I've been waiting for a real linux picross for so long I thought it must be IMPOSSIBLE, and here you are with a delightfully competent version! I'm looking forward to watching picmi continue to grow. That said, I had two questions/comments and one issue I'd like to throw your way.

- I was wondering why a specific font was chosen for the interface (I'm figuring to make sure everything is readable?). In a future release, could picmi simply use the system font? It would really beautify the already very lovely interface. The numbers in the picross game look less smooth than the minesweeper game, perhaps for this reason. By contrast, the stock sudoku that comes with ubuntu has incredibly clear numbers (though I'm not certain they use a system font)

- it would screw with the custom background (and probably some other things, unfortunately), but is there any plan to allow games to be graphically scalable in the future? I'd love to be able to resize a smaller picross puzzle to take up a bit more room on the screen (and making the numbers and boxes proportionally larger in the process). This would be a useful feature for anyone with poor eyesight... I personally would just like having the option, if it becomes possible to implement.

In terms of issues, this is the only problem I'm having: if I choose the "clear picross statistics" option, trying to exit a picross OR minesweeper game (or beating a picross game) will cause a segfault (didn't try beating a minesweeper game, I'm not very good at minesweeper). Deleting my configuration folder fixes this issue. The issue does not happen when I use the "clear minesweeper statistics" button.

Anyhoo... I'm really pumped about this! Thank you so much for your hard work, and I'll be recommending the game to my friends. Thanks!

EDIT: actually, as long as I'm still here... (this is just constructive stuff, I do testing for a lot of programs, so don't feel any of it is imperative. Just thinking "out loud")

- when a game is selected, can the game selection window be hidden? And then made to reappear when a game is exited? This would be a nice visual touch, and give people one less window to worry about at a time
- I feel as though the timer should not begin until the first click is made (this is how ubuntu's mahjong works). In addition, I'm not sure what the difference is between total and real... oh. Gotcha, you're doing the time penalty for incorrect guesses thing. I do like that method, but there should be some visual indicator that something went wrong...perhaps boxes clicked in error should have a red X, instead of a black one? I know in the nintendo games, you get a visual of the time being added, but the red X might be a simple way to get the idea across.
- I really like the background you're using as the default, but the blacks and shades of gray you're using around it seems overly contrast-y. Maybe these bits should use system colors, or possibly even make the number area semi-transparent (really get your money's worth for the custom backgrounds)? It's hard to say for sure without seeing it in action, though.
- I'd almost like to suggest an option for turning off the cross that follows your pointer, as I find it a bit distracting when playing with the mouse... but then I realized that it would make it impossible to play the game with the keyboard, and I'm sure people would be confused if they switched the option by accident. Not a big deal. A suggestion (not necessary, but to throw it out there) would be to use small arrows on the top and left for positioning, as in the original gameboy game (see this video: [http://www.youtube.com/watch?v=7F0CNOWN2gA](http://www.youtube.com/watch?v=7F0CNOWN2gA))
- how attached to the "completed" indicator are you? The greying-out of numbers on the grid seem like a very good indicator already to me. I think the only really necessary thing being displayed in the top corner at the moment is the time, particularly the total (real being less necessary, especially if the red X or other penalty warning is implemented). Perhaps the space could be used for something arty/cute/what have you? Your little mascot guy could sit up in the corner, just as an example (like in the original gameboy game, again), which might be cute. He could even wince or something when you hit an incorrect square. I dunno.

Anyway, that's probably more than enough feedback. I hope you don't mind, I just like to critique things I find enjoyable. I find this very enjoyable, and I appreciate you making it. I'll be on a trip for like two weeks, but I hope you'll find some of this useful while I'm gone. Thanks again.

---

### Post by schuay on 2010-07-19
Hi,

thanks for your post! I'm glad you enjoy the game, its user reactions that keep me motivated to work on this :)

> **DancemasterGlenn said:**
> 
In terms of issues, this is the only problem I'm having: if I choose the "clear picross statistics" option, trying to exit a picross OR minesweeper game (or beating a picross game) will cause a segfault (didn't try beating a minesweeper game, I'm not very good at minesweeper). Deleting my configuration folder fixes this issue. The issue does not happen when I use the "clear minesweeper statistics" button.


I uploaded 1.2.1 to the ppa a few hours ago, that should hopefully fix the segfault (let me know if it doesn't). 

> ...why a specific font was chosen for the interface...No specific reason, I've used sdl_ttf before and I was most familiar with it. Somebody else has already suggested using sdl_pango, so I might do that.

> ...allow games to be graphically scalable...That does make alot of sense, I'll try to take a look at it. I'm thinking more along the lines of "scaling the entire screen surface" instead of the awesome scaling that lots of gnome / kde games do though, so I'm not sure how ugly it would be.

> ...when a game is selected, can the game selection window be hidden?...> ...timer should not begin until the first click is made...> ...some visual indicator that something went wrong...I agree with all of these.

> ...background you're using as the default, but the blacks and shades of  gray you're using around it seems overly contrast-y...I've been hoping to get new / better gfx made by friends, but none seem to have pulled through. I know there's alot of potential for improvement in that area :) I might play around with making the nonboard area semi translucent, but I'm not sure how that will affect the visibility of light gray numbers.

> ...turning off the cross that follows your pointer...What I've seen other games do is hide the position indicator while using the mouse, and switching it on as soon as a keyboard control is pressed. This makes sense for minesweeper, but in picross it often helps me find the right row/column when I'm somewhere in the middle of the board. Maybe outline the numbers area in some way?

> ...I think the only really necessary thing being displayed in the top  corner at the moment is the time...While I do agree with you, I don't have any other graphics to use in that area. 


I won't make any promises on getting all of this stuff implemented since I know how easy it is to get distracted / bored / busy with something else. That said, I think all of your suggestions sound good, lets see how far I can get :)

Again, thanks for playing and taking the time to post feedback!

---

### Post by DancemasterGlenn on 2010-07-19
Excellent, the segfault is fixed. It was chance that I stumbled across it at all, but I'm glad it wasn't a headache to fix.

I'm glad my post was found agreeable, you never know how people will react to comments (especially in such a big block). You should certainly take your time in implementing any of the ideas, the game is running perfectly serviceably as-is. At some point when I come back from my trip perhaps I can mock up some of the ideas. Until then, thanks a bunch for picmi.

---

### Post by schuay on 2010-07-20
I've ported picmi to use pango. See screenshots below for comparison, left is sdl_ttf (old), right is sdl_pango (new).

[[IMG]http://img842.imageshack.us/img842/2060/picmittf1.th.png[/IMG]]("http://img842.imageshack.us/i/picmittf1.png/")[[IMG]http://img833.imageshack.us/img833/7627/picmipango1.th.png[/IMG]]("http://img833.imageshack.us/i/picmipango1.png/")

[[IMG]http://img839.imageshack.us/img839/2922/picmittf2.th.png[/IMG]]("http://img839.imageshack.us/i/picmittf2.png/") [[IMG]http://img841.imageshack.us/img841/2597/picmipango2.th.png[/IMG]]("http://img841.imageshack.us/i/picmipango2.png/")

I'm not sure which I like better.

Pango:

+ formatting through markup
+ i18n support

- old / unmaintained (?), last release is from 2004 and has unfixed bugs
- needs to be patched before picmi is able to build. debian has the patch, but this is probably the deal breaker for me
- no text justification (left/center/right) support
- can introduce font issues if user font / font size does not work well with picmi

TTF:

+ always looks the same
+ easy justification
+ still maintained

Edit: I switched the master branch to TTF's antialiased rendering. It should be a bit slower but looks much nicer. This is my favorite alternative at the moment.

Oh, and I tried making the window resizable using software scaling on the main surface just before flipping it to the screen. 
It worked ok, but it was way too slow. Which leaves me with either 

a) scaling all surfaces (and fonts) on every resize and drawing depending on the current window size, 
b) going with openGl, or 
c) switching to a different drawing mechanism like Qt's QGraphicsView. 

Of all these options I like c) the most because I could dump SDL and integrate the game area into the main window. Plus, all games using QGraphicsView look pretty awesome (take a look at KSudoku and how well it scales.. it looks perfect at full screen and at a window size of 200x200). I'm not sure how easy the conversion would be though, and QGraphicsView will definitely have its own limitations and annoyances.

---

### Post by DancemasterGlenn on 2010-07-20
Glad to hear there was another font alternative. Any screenshots?

As for resizing, I think option b or c would be preferable. Qt has become increasingly popular, so it might behoove you to take advantage of it. I do see opengl used for many games, though (even smaller 2d ones). I guess just take a look into both and see which you'd rather try maintaining? Qt sounds very promising, though.

---

### Post by schuay on 2010-07-28
> **DancemasterGlenn said:**
> Glad to hear there was another font alternative. Any screenshots?

As for resizing, I think option b or c would be preferable. Qt has become increasingly popular, so it might behoove you to take advantage of it. I do see opengl used for many games, though (even smaller 2d ones). I guess just take a look into both and see which you'd rather try maintaining? Qt sounds very promising, though.

I ended up going with SFML instead of SDL. 

1.3.0 is queued for building right now, it should be up on the ppa by tomorrow.

---

### Post by SpetsnazC4 on 2010-10-15
Great Job!

---

### Post by benW1985 on 2011-09-06
Hi
I just discovered this Thread here, I was originally searching for a Picross game on Ubuntu, and so I found this... Now, what I wanted to know, is it possible that the ppa repository is down or something? Because, when I type

sudo apt-get update

I have some 404-Error concerning your stuff:
[PHP]Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
                      
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jakob-gruber/picmi/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jakob-gruber/picmi/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
[/PHP]Well, i hope that it's something someone can fix soon... And either way, it looks really cool, so thanks I guess :D

---

### Post by schuay on 2011-09-07
@benW1985: I haven't updated the Ubuntu packages in a long time. It might be difficult with the latest versions because they use an early version of SFML 2 and I'm not sure if it's easily available in Ubuntu.

I'll try to get around to it later today sometime and let you know how it turns out.

---

### Post by schuay on 2011-09-07
I updated the ppa to the latest version still using SFML 1.6. Packages are now available for 11.04.

---

### Post by benW1985 on 2011-09-07
Thanks a bunch :) Installed it and played it for a few mins. Works fine. That was really fast, too. Going to play it now :D

---

