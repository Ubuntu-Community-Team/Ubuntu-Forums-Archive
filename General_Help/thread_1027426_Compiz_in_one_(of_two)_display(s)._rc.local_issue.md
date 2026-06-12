---
title: "Compiz in one (of two) display(s). rc.local issue"
date: 2009-01-01
forum: General Help
---

### Post by Hoyland84 on 2009-01-01
Hi!

I have two screens sharing one computer. I run two separate X screens and are happy with that. However, I want to run compiz on only one of the screens. I have managed to do this by typing this into root terminal:

```
DISPLAY=:0.1 compiz --only-current-screen &
DISPLAY=:0.0 compiz --only-current-screen &
# in that order
```

Now I want this command to run automatically when I boot. I simply pasted the line into /etc/rc.local, thinking that that would do the trick, but it didn't. I'm clueless about rc.local and boot up scripts. What am I getting wrong here?

---

### Post by stderr on 2009-01-01
I really don't know what the proper way to do this would be. Typically I shove something in under System -> Preferences -> Session. 

In your case, maybe I'd be tempted to integrate it into the gnome-wm script under /usr/bin, assuming you're running GNOME. It executes the WM right at the bottom with "exec $WINDOW_MANAGER $OPT1 $OPT2 $OPT3 $OPT4". A bit of a hack maybe, but I would think it would work?

---

### Post by Hoyland84 on 2009-01-02
Yeah, maybe that would work. I'll give it a try some day soon and reply whatever results I get. The worst thing that can happen is that window manager won't start and I have to edit the file back to how it was before.

Thanks!

Other suggestions and points are still welcome.

---

### Post by Hoyland84 on 2009-01-04
I tried editing the gnome-wm script a bit, but quickly came to the conclusion that I was out of bounds with my limited skills here. But I do think that you could be on to something, stderr. Some changes in this script could do the trick. So I am asking you or anyone else for ideas on how to edit this script to meet my requirements.

As you wrote, just putting something under sessions could also do the trick and you're probably right. These commands must however be run as root and I don't know if a script under sessions can be run as root. If this is no problem then, yeah, sure a script like that would be great. But again, that would take more skills than what I'm in possession of.

So, I'm kind of bumping this. Right now I have the options of either getting rc.local to work, putting a simple script in under sessions or reconfiguring the gnome-wm script. Or...maybe something completely different. Any help would be much appreciated.

---

### Post by stderr on 2009-01-04
Well, I have no clue if this will work, but give it a go. 

To edit gnome-wm, you'll need to be root, so if you want a graphical text editor use

```
gksudo gedit /usr/bin/gnome-wm
```

if you're happy with a command line editor, then use something like

```
sudo vim /usr/bin/gnome-wm
```

At the bottom where it says:

```
# Store the selected WM with gconf
gconftool-2 -t string -s /desktop/gnome/applications/window_manager/current "$WINDOW_MANAGER"

exec $WINDOW_MANAGER $OPT1 $OPT2 $OPT3 $OPT4

echo "ERROR: No window manager could run!"

```

I would try changing to:

```
# Store the selected WM with gconf
gconftool-2 -t string -s /desktop/gnome/applications/window_manager/current "$WINDOW_MANAGER"

# Original line
#exec $WINDOW_MANAGER $OPT1 $OPT2 $OPT3 $OPT4

# Start Compiz separately on each screen
DISPLAY=0:1 $WINDOW_MANAGER $OPT1 $OPT2 $OPT3 $OPT4 --only-current-screen&
DISPLAY=0:0 $WINDOW_MANAGER $OPT1 $OPT2 $OPT3 $OPT4 --only-current-screen
echo "ERROR: No window manager could run!"

```

I don't really know what the effect of 'exec' is... I don't think it spawns anything new that simply running the command wouldn't do. You may need that though... and I'm not sure if I've got the backgrounding right there with &. You may need to play around a bit... as you say, if it buggers up, just switch back to a TTY with Ctrl + Alf + F(1,2,3,...), make a change, and give it another go with

```
startx
```

---

