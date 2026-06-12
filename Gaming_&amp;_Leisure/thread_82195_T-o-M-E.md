---
title: "T-o-M-E"
date: 2005-10-26
forum: Gaming &amp; Leisure
---

### Post by dolny on 2005-10-26
After atp-getting it from breezy extras/multvierse, and trying to run it, I get the following errror:

```
symbol lookup error: /usr/lib/libXaw.so.6: undefined symbol: xawPrintShellWidgetClass
```

Can somebody help?

[http://www.t-o-m-e.net](http://www.t-o-m-e.net)

---

### Post by dolny on 2005-10-26
Anyway, I managed to compile it. Here's a small HOWTO by me:

[http://forum.t-o-m-e.net/viewtopic.php?p=49803#49803](http://forum.t-o-m-e.net/viewtopic.php?p=49803#49803)

Anybody plays roguelikes here? ;)

---

### Post by shinygerbil on 2005-10-27
I like Zangband, but I only played the TK version, which, to my knowledge (and bitter disappointment), is only available on Windows... I'd love to get into the game but just find ASCII graphics so confusing - it reduces the pick-up-and-play element the TK version had. (there was no "what does this random symbol mean? Is it a rock? an orc? a dragon??? Is it moving towards me??? Oh wait, it's just a tree. Silly me..)

---

### Post by k8to on 2005-11-08
That's not quite true.  ZangTK, AngTK, etc works perfectly well on Linux, I actually have a Half Elf mage winner from AngTK.

The problem is that *AngTK is unmaintained, and difficult to dig up, and uses a special build tool, so you have to find the source, read some instructions, and build it yourself with about 8 or so steps.  Also it's unmaintained so you have to play fairly old versions of angband.

On windows you can just use a binary so it's a bit easier.

---

### Post by J-Rod on 2006-04-24
Can anyone tell me how to get tiled mode working for ToME? Or for that matter, why the terminal windows don't seem to work? All my other terms, such as mirror and recall stay blank. Is that normal for this release from the repository?

---

### Post by shinygerbil on 2006-04-25
I've no idea, i don't have it installed. But it's only a click away, so I might :P

In other news previously discussed in this thread, ZangTK works perfectly under Wine :D

---

### Post by J-Rod on 2006-04-25
Right, but I am a fan of ToME's skill system, and I have played a ton of Zangband on my PC already. I'm just wondering if it's a build issue, or if there's some stupid operator error on my part.

---

### Post by J-Rod on 2006-04-25
okay, well tiled mode was simple. I just looked up the "man tome". I don't see flags for changing font size though. That just leaves why the other terminal windows don't seem to work.

---

### Post by shinygerbil on 2006-04-26
[QUOTE=J-Rod]Right, but I am a fan of ToME's skill system, and I have played a ton of Zangband on my PC already. I'm just wondering if it's a build issue, or if there's some stupid operator error on my part.[/QUOTE]

I know, I know, give me some time!

It seems to be the same on mine. i'm gonna go away and build the latest version myself, and see what happens.

---

### Post by shinygerbil on 2006-04-26
Hah! Cracked it! (No help from the in-game help)

Here goes...

Firstly when you run tome, try something like this:

```
tome -g -- -n4
```

The -g means graphics mode. The -- -n4 (those two extra dashes are important) means use 4 windows in total.

Now you can move/resize these windows as you want. I find 8 terminals too annoying.

Now, once you are in the game, type = to bring up the options menu, then capital W to go to the Window Flags section.

Here you see a list of all the terminals you can display, and all the different types of information you can display in them. Move around with the numpad, and press y to enable each option. Now go back to the game and watch as it all unfolds :P

Hope that's helped you somewhat.

Steve

---

### Post by J-Rod on 2006-04-26
Very nice. I had run the tome -h option late last night, and found the -g and -n flags. What I didn't figure out, however was the window flags stuff. You've been a great help. :) Have you by chance been able to change font sizes?

---

### Post by shinygerbil on 2006-04-27
Nope, but I'll have a play around :D

Edit: I haven't tried it yet but it's likely you could just change the filenames of the font files. They are stored in /var/games/tome/xtra/font - I'm gonna see what one is the default and replace it. It's ugly, but it might just work :)

---

### Post by J-Rod on 2006-04-27
Right on, well let me know what you came up with. My final set of issues to overcome are these: 1) Changing font size to 16x16 if possible 2) finding a way to have the program "remember" the location of various terminals, so that when I close and restart the program, I don't have to move terminals manually every time. 3) Find out why I can't save when using additional modules like FuryMod
The thing I do miss about ZangbandTK was the ability to easily add in new graphics, I enjoyed making new tiles on a whim.

Other than that, it's ToME goodness!

---

### Post by shinygerbil on 2006-04-28
I can solve number 2 :) First, set up all your windows how you want. Now, if you right click on the window's titlebar and go to Advanced -> Special Window Settings, a screen will come up with all these useful goodies - in particular, you'll want to set the Position and Size to Remember the current settings. :) The first couple of times I did this, KWin crashed, and I had to run kwin again from a terminal, but it worked like a charm :)

As for number 3, I assume this is a permissions problem. It depends on how you installed the module; I'm guessing you had to sudo copy things into the right directories. Even so, saves are usually stored under the .tome directory in your home folder, so I don't really know.

Number 1 is proving difficult. The latest thing I am trying is environment variables, but I'm not having much luck. I'll let you know :)

Steve

---

### Post by J-Rod on 2006-04-30
Ah, heh. I should have mentioned I am running Gnome. :) So maybe I need to either figure out Devils Pie or some other type of manager that will let me pin windows and remember positions. I did indeed sudo copy the mod into the proper directory, and I believe I have given full permissions for all accounts to r/w that folder. I noticed Tome installs all over the place though, and the mod doesn't get that option, I wonder if that has something to do with it. I read somewhere else that people were saving by entering the full path, but I don't see how I can enter a path name, it would have to be done in one of the mod files I assume. No idea which one it is, I looked through several. I could live without 16x16, I'm not against ASCII or anything, just like to have some tiled graphics, as I can draw new ones to suit my fancy.

---

### Post by shinygerbil on 2006-04-30
No, it's silly of me, I forget that the majority of people on these forums use Gnome. As yet, I've had no luck with anything else :/

Steve

---

### Post by brass on 2006-07-11
has anybody figured out how to save a file from a mod? I got rw permissions everywhere but it still won't save.

---

