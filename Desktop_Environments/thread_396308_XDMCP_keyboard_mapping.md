---
title: "XDMCP keyboard mapping"
date: 2007-03-29
forum: Desktop Environments
---

### Post by rubberglove on 2007-03-29
Hi:

To complicate my life, I use XDMCP to work on my desktop from my powerbook. I do this because I like the screen, keyboard, and trackpad (yes, I like the trackpad) on my powerbook much better than my desktop, and like the flexibility of pressing a few keys to switch between the XDMCP session and OS X. 

However, after upgrading my desktop to feisty the other night, my keyboard mapping has gone completely crazy when I log in from my powerbook - almost no keys are in their correct locations. 

Something similar happened once before, where the right cursor key became incorrectly mapped, and I had to get in the habit of remapping it every time I log in via XDMCP, but this is a bit more of a headache. 

As I understand it, the keymapping is defined on the OS X computer, which is running the x server... so what could be causing this? Is it related to the fact that OS X is running an ancient implementation of X11 (xfree86 4.4.0)?

any ideas what might be causing this, and/or any solutions? 

thanks.

---

### Post by sixhat on 2007-03-30
I'm having the same kind of problem.

I'm using a MacBook to access my feisty box because my monitor died recently and i usually do:

Launch **X11**

Then in **xterm**

```
ssh -Y server.address
```

and after successfully login

```
sudo Xnest :1 -geometry 1280x750 -query localhost
```

this launches the gdm where I can login as I usually would (at this point the keyboard mapping still works fine)

After login into my desktop the mapping becomes completely scrambled and I can't seam to type anything as the mapping is so disrupted.

Anyone has found a solution?

---

### Post by rubberglove on 2007-04-02
I haven't quite figured it out yet, but on a whim, I tried installing xfce and e17. 

The keymapping is still scrambled when I log into xfce, but scrambled differently (and not quite as bad) as with gnome. 
With enlightenment (e17), it appears to be fine. 
Strange. I may try trashing gnome preferences and starting over to see if that fixes things.

---

### Post by rubberglove on 2007-04-02
Well, after seeing this: [http://docs.info.apple.com/article.html?artnum=18966&coll=ap]("http://docs.info.apple.com/article.html?artnum=18966&coll=ap")
I managed to get things working. 

There simply has to be a better way than this, but: oh well. 

if when you SSH in to your feisty box with x forwarding on, and your keymapping is still fine (it should be), then run the following command:

```
xmodmap -pke > $HOME/mykeymap
```

That will make a map of your current key settings and save it in ~/mykeymap
you'll then have to run: 
```
xmodmap ~/mykeymap
```

after you're logged in with XDMCP to switch your keyboard settings. 

this gave me an error for one of the keysyms ('U0003'), but I deleted that line in the file, and it worked after that. 

to simplify my life, I put that command into a script on my desktop, so I can just click it when I need it, but I'm sure there's an easy way to automate the process. 

Oh, and incidentally, did you know that you can just run: 
```
X -query server.name
```

to login via XDMCP? I think only difference would be that you are not tunneling the XDMCP session over SSH, but I like the fact that you can then run it fullscreen.

Hope this helps.

---

### Post by elventear on 2007-05-03
I have the same issue on a MBPro and things got kind of resolved with your solution. The keyboard maps normally but none of the SHIFT modified keys work. Any ideas? Or have you resolved this problem completely?

---

### Post by rapchee on 2007-06-14
> ```
xmodmap -pke > $HOME/mykeymap
```

That will make a map of your current key settings and save it in ~/mykeymap
you'll then have to run: 
```
xmodmap ~/mykeymap
```


xmodmap gives me an '**unable to open display ''** ' message. 
i've tried specifying -display 0 and 1, but it did not help either
any suggestions appreciatied

---

### Post by edalquist on 2007-06-17
You need to run the ssh -Y command from within the X11 xterm window, it won't work from terminal.


I am also having problems with my shift keys working after creating the keymap file and loading it after starting the xdmcp session.

Using xev I can verify that the mappings work (pressing shift results in the correct event) and event shift + other characters work in xev (a shows as A like it should) but the shift key doesn't work correctly in any other application via xdmcp. It almost looks like when I hold shift and hit another key the window looses focus for a second.

Anyone that has xdmcp working from OSX to Gnome I'd love to hear how you do it.

PS: I tried kubuntu and it seems to work just fine (no need for doing keymapping, etc) in KDE.

---

### Post by t.k.egan on 2007-06-26
So I was having the same trouble and after digging around in error messages found some errors about "Unable to initialize XKEYBOARD" so I added the -kb flag to Xnest and it worked!  So try:

>  Xnest :1 -query localhost -geometry 1024x768 -kb

---

### Post by rapchee on 2007-08-31
i've accidentally found that if i switch keyboard layout in osx, after logging in with gnome, the keys work properly

----

Edit:
Actually they worked once XI
it'd be fun to know what happened ...

---

