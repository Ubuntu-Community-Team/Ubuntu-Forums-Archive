---
title: "Automatically Disabling Compiz Script"
date: 2009-05-12
forum: Gaming &amp; Leisure
---

### Post by Amof on 2009-05-12
You know one of the things I hate most about playing games on my Linux machine is the simple task of disabling compiz before I play a game. I know, it's just a  simply click of a button... But I really suck at remembering to do it and then you start a game and it screws up everything and you end up having to restart the x-server.

No more!

I made this simple script in about 3 minutes to check and see if Compiz is running. If it's process is detected then it will replace it with Metacity and then start the full screen application. After the given application is done it will restore compiz.

This is a really simple script that I'm sure most advance Linux users have but in the spirit of ubuntu I am posting this one to see if there is a need for newer users. If there is, then I'm gladly put more then 3 minutes into this thing and add more functionality.

**What it does:**

Disables Compiz  before starting a fullscreen application
Restores Metacity after the application is done.

**What I plan to add:**

Checking for the target before disabling Compiz. (Can be annoying to have compiz die just to be reactivated because of a syntax error)
KDE support.
NVClock fan support. (Is there a program like this for ATI?)
more

**How do you install it:**

Just simply put the attached file in your /usr/bin OR /usr/games.
Make sure you extract it in your home directory and then run this command.

```
sudo mv game /usr/bin
```

Oh and make sure it's executable. 

**How do I use it:**

It's fairly simple, just type game before your game command. Like nexuiz for example:
```
game nexuiz
``` 
It's that easy.

**[COLOR="Red"]WARNING: [/COLOR]**
Again this is only to be used on GNOME until I add KDE detection in. Although, it would be fairly simple to just change the one like to start kwin.

---

### Post by binbash on 2009-05-12
I tried it with a couple of games i have.It is a very simple script but it works great.

---

### Post by Amof on 2009-05-12
Haha ya, when I said it took 3 minutes, I wasn't kidding. If more people like it too I'll gladly make it more complicated. =)

---

### Post by Amof on 2009-05-14
Could someone do me a large favor? Could someone using KDE post me the MAN pages for Kwin? I haven't used it in awhile and I need it to allow me to start Kwin.

Thanks! ):P

---

### Post by KhaaL on 2009-05-17
kwin dosen't have any man pages.

Great script!

---

### Post by Amof on 2009-05-18
I knew I disliked KDE for a reason! Long live MAN pages.

---

### Post by enosis on 2009-05-18
Thanks Amof, will try it when I get back home :)

---

### Post by strycore on 2009-05-18
Last time i benchmarked some stuff with compiz enabled / disabled i got these results 
[IMG]http://tweekers.free.fr/blog/images/bench/ut2004bench.jpg[/IMG]

Apart from benchmarking, I never turn off Compiz (I used to in Edgy or Feisty but not anymore) for gaming as the performance gain is not worth the effort. And I do run some pretty heavy games (Left4Dead on Cedega for example)

Does compiz really have an impact on gaming performance for you guys ?
Would be interesting to see more benchmarks using ATI or Intel cards for example.

---

### Post by KhaaL on 2009-05-18
strycore, i experienced compiz affecting my gaming if its running on the same x-server. If I start my game in a second x-server, then the performance is the same as if i'd have run it in the first one with metacity. Of course RAM usage will be slightly higher :)

Unfortunatly I havent kept my test results

---

### Post by binbash on 2009-05-18
Does compiz really have an impact on gaming performance for you guys ?


Dude if you have an ati card, it is quite impossible to play an opengl game without turning compiz off : )

---

### Post by 0bso on 2009-05-18
> **strycore said:**
> 
Does compiz really have an impact on gaming performance for you guys ?

It's not so much that it impacts performance; It's that it seems to amplify bugs x10. For example the main menu on Urban Terror is only usable about half the time if compiz is running. I disable it out of habit now just to save myself headache.

---

### Post by javyn999 on 2009-05-19
What about installing xubuntu-desktop and just booting into that to play games?  Is compiz enabled by default in Xubuntu?

---

### Post by mal1958 on 2009-05-19
I am having problems with some games using Xubuntu 9.04, and would like to know the answer to that question too.  I have an Invidia 9200 or 9400 and it is overclocked by a company called BFG.  It Xubuntu has Compiz and it interferes with my games or anything, I want to know, and know how to shut it off.  That is what I love about Linux over Winblows (insert your screwed up flavor of that OS here).  I have control, just like in the old dos days.

Mike

---

### Post by KhaaL on 2009-05-20
> **javyn999 said:**
> What about installing xubuntu-desktop and just booting into that to play games?  Is compiz enabled by default in Xubuntu?

What would you gain from booting into xubuntu? it's still linux, just with a different preselection of packages that isn't as taxing on ram. Unless you have EXTREMLY little ram, you should be fine running in your current desktop with compiz disabled, or in another X-server.

---

### Post by javyn999 on 2009-05-20
So how does one disable Compiz?

Warsow runs fine for me, but Alien Arena and Open Arena crash to desktop whenever I try to join a server.  I'm assuming it's Compiz causing this.

---

### Post by 0bso on 2009-05-20
> **javyn999 said:**
> So how does one disable Compiz?

I use compiz-switch. You can add it to one of the task bars and clicking it will toggle compiz on or off. 

Or on games I play a lot I'll throw together a simple startup script like this:

```

#!/bin/bash
compiz-switch
gamename
compiz-switch

```

That way it switches to metacity, runs the game, then switches back to compiz when it's done. Or you can use the program in the OP of this thread which accomplishes the same thing.

---

### Post by javyn999 on 2009-05-20
Brilliant!  Thanks!

---

### Post by mal1958 on 2009-05-20
I run Xubuntu 9.04 and need to know if Compiz is on by default in my version.  How can I tell?  And will it help the game performance in Pharoah, Caesar 3, and MOO 3 if I switch it off?  Will switching it off (if it is present and on) help me play either Civ 3 or Alpha Centauri Planet pack?

   I am a NOOB so I apologize in advance if it seems that these questions are a bit dumb.

Mike

---

### Post by BoyOfDestiny on 2009-05-20
> **Amof said:**
> *snip*
```
sudo mv game /usr/bin
```

Oh and make sure it's executable. 
*/snip*

Or you can make a folder called 
bin
in your home folder

It's an easy way to add your scripts globally without needing root privilege.

---

### Post by javyn999 on 2009-05-22
Thanks a bunch man.  I tried the script but it seemed to hose the sound in every game I tried it on.  But compiz-switch works great. Doubled my fps in Nexuiz from 30 to 60!

> **0bso said:**
> I use compiz-switch. You can add it to one of the task bars and clicking it will toggle compiz on or off. 

Or on games I play a lot I'll throw together a simple startup script like this:

```

#!/bin/bash
compiz-switch
gamename
compiz-switch

```

That way it switches to metacity, runs the game, then switches back to compiz when it's done. Or you can use the program in the OP of this thread which accomplishes the same thing.

---

### Post by 5nak3 on 2009-05-31
Can i ask is this script only working if you run the game via terminal e.g. "game openarena"? 

I usually run mine through launchers so if so, the script won't be of use for me. Thanks in advance.

---

### Post by z0mbie on 2009-06-01
You know the best method I found is to assign keybindings to disable/enable Compiz. It's faster than Fusion icon and doesn't require scripting at all.

---

### Post by 5nak3 on 2009-06-02
care to explain how you managed to do that? I'd be quite interested in that actually. Thanks

---

### Post by gabdullah on 2009-06-16
I enable and disable Compiz regularly with Compiz Switch. Although the performance difference is somewhat negligible, it does have an impact occasionally.

---

