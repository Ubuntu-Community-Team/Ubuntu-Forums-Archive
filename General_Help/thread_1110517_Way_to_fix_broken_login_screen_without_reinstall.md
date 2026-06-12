---
title: "Way to fix broken login screen without reinstall?"
date: 2009-03-29
forum: General Help
---

### Post by calvinball81 on 2009-03-29
I'm running 8.10.  I downloaded a new login screen (just tryin to make it look prettier, you know), applied it, and restarted.  Apparently the information for that login screen is corrupt or something, because I just get a black screen with the little "Ubuntu is running" circle.  I never even get to the part where I enter my username.  Ergo, I can't get into Ubuntu at all.  I'm really hoping to be able to rectify this without reinstalling EVERYTHING.  Here are my ideas/questions:

1) Is there a way to bypass the login screen so I could get in and change things back?  Doesn't seem likely (security and all that), but thought I'd ask.
2) I have the install CD (that's what I'm working with now).  Is there some way that, while running Ubuntu from that, I could go into the file system on my hard disk and change the login screen from there?  I know a lot can be accomplished on Ubuntu without a GUI, so it seems remotely possible.

Any other ideas, feel free to share.  I'm not a total noob, but to be on the safe side better talk to me like I'm three.  Thanks in advance, folks.

---

### Post by zvacet on 2009-03-29
You can boot in recovery mode and find that corrupted file and delete it.You should have your old login screen again.

---

### Post by RedSingularity on 2009-03-30
Which theme did you pick??

---

### Post by calvinball81 on 2009-03-30
Recovery mode was the first thing I tried.  Problem is, I still have to go through the login screen if I boot from the Recovery Menu.  Like I said, I can run Ubuntu from CD and get into my file system.  Only I have no clue where the login screen files would be kept or what to look for.  Besides, if I did find it, could I even get the system's permission to delete them from here?

By the way, the screen is from the Mac OSX clone stuff that can be downloaded here: 

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)  

Idiot that I am, I never DREAMED that using stuff designed for Hardy might give me any problems on Ibex.  Grr.

---

### Post by ispy on 2009-03-30
when you get to the login screen try hitting Ctrl + Alt + F1 and logging in there.

It should give you a shell from where you can navigate to the corrupted file and delete it.

---

### Post by ispy on 2009-03-30
upon further investigation it appears that the /etc/gdm/gdm.conf file is the key.

In it there is a line that controls the theme. For example, an excerpt from mine would be:

```
# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Mac4Lin_GDM_v1.0_RC
#GraphicalThemes=bijou/:blueswirl/:circles/:debblue-list/:debblue/:ayo/:debian-dawn/:debian-greeter/:debian/:glassfoot/:hantzley/:happygnome/:industrial/:crystal/:linsta
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
```

So if you want to change that to the default just edit the GraphicalTheme line to read 

```
GraphicalTheme=circles
```

That should work.

---

### Post by calvinball81 on 2009-03-30
Edited gdm.conf as instructed.  Alas, no go.  I was surprised, however, to see that my theme was set to "Human" rather than anything Mac related.  Hmm.

Ctrl + Alt + F1 does let me log in, giving me the terminal window only.  From there, however, I'm not sure how to proceed.  Any advice would be greatly appreciated.

---

### Post by stereomuffin on 2009-03-30
what happens when you type: startx at the terminal? the terminal output probably will give you some clues as to where to look.

---

### Post by zvacet on 2009-03-30
@ **calvinball81**

If you followed install instructions then you have folder named **Mac_files**.Try to delete it and you should be back on default Ubuntu.

---

