---
title: "Xeiso"
date: 2008-08-15
forum: Gaming &amp; Leisure
---

### Post by jpeddicord on 2008-08-15
If you read Planet Ubuntu regularly, you may have already heard of this. If not, you're in for a treat. I've already written about this twice, so I suggest you go here for a general overview:

[http://jacob.peddicord.net/blog/2008/07/03/introducing-xeiso/](http://jacob.peddicord.net/blog/2008/07/03/introducing-xeiso/)
[http://jacob.peddicord.net/blog/2008/08/15/zero-point-one-ish/](http://jacob.peddicord.net/blog/2008/08/15/zero-point-one-ish/)

For those that can't be bothered with reading, Xeiso is a platform designed to turn almost any PC into a gaming system. At its current stage, it is only a UI, but later this year and early next I will be developing a Live CD and installable system from it.

In case you missed the video in those links, [here it is on YouTube]("http://www.youtube.com/watch?v=8enl-PcmI7E"). I know that a lot of the interface seems confusing at first, but that's why I'm here: to get suggestions.

So, give it a try, break it, hack it, branch it. If you have a suggestion, please make sure you have the [latest revision]("http://xeiso.com/dev/bzr/") before posting. If you are interested in development, please don't PM me, but mail me directly at jacob at xeiso dot com. You can also find me in #xeiso on freenode.

[**.deb packages are now available.**]("https://launchpad.net/~xeiso/+archive")

Screenshots attached, but watch the video if you can instead.

---

### Post by cristo-father on 2008-08-16
1.Make a .deb for 32bit and 64bit
2. Boot from usb and external hard drive.
3. Display games, through genre and then sub-genre, alphabetically, online ratings, popularity,mostplayed...etc
4. Allow games to be played through wine.
5. Make it more enjoyable to play, from a resource point of view(even if i am required to login again).[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)
6. Allow compatibility with repos, since playbuntu is coming out.
7.When a game is displayed it should give choice to view,text or images or videos and levels of each for example review,long description,short description, etc,videos and images can be voted.
8.Download while gaming.

---

### Post by jpeddicord on 2008-08-16
> 1.Make a .deb for 32bit and 64bit
Working on (right this minute actually..)
> 2. Boot from usb and external hard drive.
That's more up to the user to configure, but it's possible.
> 3. Display games, through genre and then sub-genre, alphabetically, online ratings, popularity,mostplayed...etc
Been thinking about how to go about that, but something should show up soon.
> 4. Allow games to be played through wine.
No. That would defeat the purpose of creating an open gaming platform. There is nothing that would prevent a packager from including Wine, but it will not be supported.
> 5. Make it more enjoyable to play, from a resource point of view(even if i am required to login again).[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)
Not quite sure what you mean here.
> 6. Allow compatibility with repos, since playbuntu is coming out.
The LiveCD will not really use any repositories other than the "memory-card" based downloads from the Xeiso server. Local installs are not limited to what repos are available.
> 7.When a game is displayed it should give choice to view,text or images or videos and levels of each for example review,long description,short description, etc,videos and images can be voted.
I assume you mean for the download manager; this is being worked on. Individual game banners are up to the packager or developer to create.
> 8.Download while gaming.
This shouldn't be too hard, but it might get tricky getting some interprocess communication going. But it's possible.

---

### Post by cristo-father on 2008-08-16
> **jacobmp92 said:**
> 
Not quite sure what you mean here.


I mean it would be nice to give an option of opening the application under a mode where the games can run as fast as possible.
Even if it is necessary to create a new xserver or install openbox or something else of that kind.
9. Friends list.
-See what games every friend is playing 
-what servers they are on.
-rank the friends(lol).
-join best ranked friend that is playing x, join best ranked friend playing any game, join most friends playing any game server, join the best ranked friends playing on any game server ( what this does is give a friend a ranking=rankingfriendslist-totalfriends+1
and then it sums it up for the game server they are playing.)
10. Rival list.(analogous to friends list)
11. In-game chatting(voice and keyboard).
12. Browse servers of a game without running a game.

---

### Post by cristo-father on 2008-08-19
If you have time, i would really appreciate that you would respond to my previous post(in this topic).
Thank you.

---

### Post by jpeddicord on 2008-08-19
A PPA repository is now available:
[https://launchpad.net/~xeiso/+archive](https://launchpad.net/~xeiso/+archive)

Follow the instructions there to activate it.

> **cristo-father said:**
> If you have time, i would really appreciate that you would respond to my previous post(in this topic).
Thank you.
Sorry, I had seen your post but forgot to respond to it earlier.

> I mean it would be nice to give an option of opening the application under a mode where the games can run as fast as possible.
Even if it is necessary to create a new xserver or install openbox or something else of that kind.The CD mode will have this. The desktop packages (on a standard Ubuntu) won't have and special optimizations.
> 9. Friends list.
-See what games every friend is playing 
-what servers they are on.
-rank the friends(lol).
-join best ranked friend that is playing x, join best ranked friend playing any game, join most friends playing any game server, join the best ranked friends playing on any game server ( what this does is give a friend a ranking=rankingfriendslist-totalfriends+1
and then it sums it up for the game server they are playing.)
10. Rival list.(analogous to friends list)
This is definitely possible, but is currently not in the XPK spec. This would also be troublesome for server load. It is on the to-do list though, but is of lower priority than the other features.

> 11. In-game chatting(voice and keyboard).This would be dependent on whatever game you were playing. Most games lock the keyboard and mouse, so it is nearly impossible to catch keys if a game is running. However, it *might* be possible to implement in the freeze menu (pause a running game with a patch), but that will not be available in the packaged version. Unless I find a workaround with DBUS to grab the key or something.

> 12. Browse servers of a game without running a game.This shouldn't be the job of Xeiso directly, but it's possible to add a hook to the package spec to tell the package/game to grab a list of servers to display.

---

### Post by cristo-father on 2008-08-20
How do i start it through the terminal?

---

### Post by jpeddicord on 2008-08-20
> **cristo-father said:**
> How do i start it through the terminal?

No need to, it's available from Apps > Games > Xeiso (in the PPA). If you have it fully installed though, you can run it with `xeiso-ui`. For a source checkout, use `./xeiso-ui` or `python xeiso-ui` for debug mode.

---

