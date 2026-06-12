---
title: "Mathematica"
date: 2008-02-28
forum: Education &amp; Science
---

### Post by ravenon on 2008-02-28
I am using Gutsy for work and Mathematica 6 works fine. I am running the dev release Hardy on a spare partition. Mathematica installs fine and the gui opens as it should (as long as libstdc 5 is installed), however, when typing into a mathematica notebook, nothing appears on the screen--its like the frontend cannot render fonts (unless you highlight what you just type, then it appears in white letters on dark).

Anyone else experience this or have a clue as to what the problem is? 

I posted on the Hardy dev thread without success.

---

### Post by Stochastics on 2008-03-10
Hi,

I just installed Mathematica 5.2 with Ubuntu 7.10 and i have the same problem...don't know what to do with this :(!

Hope somebody can help.

---

### Post by paulita on 2008-03-12
I've installed Mathematica 6.0 on my Ubuntu Feisty and when i start Mathematica everything freezes. It seems X just crashed and all i can do is restart my computer. Anyone with the same problem?

---

### Post by ravenon on 2008-03-15
A possible fix is to start mathematica with the -defaultvisual option. Solved my problem on Hardy.

---

### Post by aschmitz on 2008-03-23
Thank you! That solution seemed to work. Just wish I'd known before I ended up reinstalling Mathematica, reformatting the computer, and waiting for (ultimately fruitless) responses from Wolfram support. Sent them an email with this information, hopefully they'll be able to diagnose/fix the problem faster for people who have it in the future.

Anyway, for anyone who might come here via Google, my problem with Mathematica not working after I upgraded to Hardy, where it was showing no text or corrupted text, which appeared somewhat properly when highlighted, was solved with the solution provided by ravenon, start Mathematica by using the command "mathematica -defaultvisual".

Thanks again!

---

### Post by aliencam on 2008-04-05
is there any way to edit it so it always runs with "Mathematica -defaultvisual" ?? (i'm having this same problem with mathematica 6 on Hardy) 

btw thanks, it works great running with -defaultvisual. even the "help" function works now! (didn't in 7.10) only problem is compiz still makes mathematica spawn those two random blank windows lol.

---

### Post by ravenon on 2008-04-07
There are a couple of ways to get Mathematica to run with the option.

1) A desktop or panel launcher where the command line is mathematica -defaultvisual

2) You can put Mathematica on your application menu somewhere and make sure to use command mathematica -defaultvisual

3) Create a shortcut key, I use Alt+Shift+W. For this open gconf (Alt+F2 and type gconf-editor)
Go to apps->metacity->global key bindings. Pick a command, say run_command_1, double click it to edit and put <Alt><Shift>W
Now go to keybindings commands and edit command_1, put in 
mathematica -defaultvisual

Edit: Regarding the extra kernel windows when running compiz, open mathematica and go to Format->Options Inspector
Choose Global Preferences. Go to Notebook Options, Window Preferences and change the WindowFrame to say "Generic".
The extra windows will still flash when mathematica opens, but then disappear.

---

### Post by hayim on 2008-05-01
Man i had the same problems!!

I was running mathematica just fine on Mandriva 2008.0, but with -defaultvisual enabled (after adding fontpaths to xorg.conf.. jeeesh).

Then i upgrade to Hardy, and the thing opens bogus windows and displays no text!!

The windows go when you turn off compiz, as has been said above, but i totally forgot i had used -defaultvisual, and so i gave up trying to get mathematica to work in Hardy.

Now im writing from Mandriva 2008.1 spring, had the *exact same* text problem as Hardy, just found this thread and now mathematica is back in operation!

So... back to Hardy.. (?)

Thanks ravenon!!

---

### Post by Redoubts on 2008-05-06
Unfortunately -defaultvisual adds some problems, and disables anti-aliasing. I have discovered the following:

[QUOTE=Tom Kalvoda](**[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163)**)

So, I got the font rendering right now. It seems that the version of Qt libraries supplied by Mathematica are incompatible with Hardy. This procedure worked for me:

1) Make sure you have libqt4-core and libqt4-gui installed (use synaptics or aptitude),
2) remove (delete or backup somewhere) these files:
PathToMathematica/SystemFiles/Libraries/Linux/libQtCore.so.4
PathToMathematica/SystemFiles/Libraries/Linux/libQtGui.so.4
where PathToMathematica is typicaly /usr/local/Wolfram/Mathematica/6.0
(Substitute Linux-x86-64 for Linux if needed.)

Notes:
1) I deleted ~/.fonts.conf, so fonts are set up as on a clean install of Hardy.
2) If you remove only one of these files mentioned above, then Mathematica crashes.
3) I have noticed another bug - which brought me to the idea that our problems are not only font-related - when I tried to print a notebook (File -> Print) then there were no printers in the drop down menu (any one else can confirm this?)! This issue is also solved by the procedure suggested above.

Hope it helps.
[/QUOTE]

This has worked for me, running 8.04 x64 and Mathematica 6.0.1 (x64)

---

### Post by mrernia on 2009-01-21
none of this works for me. Intrepid x64 and mathematica5.2. tried Editing Xmathematica and with -defaultvisual but still a huge bunch of trasparencies.

---

### Post by Berto88 on 2009-01-21
try running this in the terminal

```
 env XLIB_SKIP_ARGB_VISUALS=1 mathematica
```

---

