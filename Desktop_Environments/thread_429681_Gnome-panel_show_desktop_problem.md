---
title: "Gnome-panel show desktop problem"
date: 2007-05-01
forum: Desktop Environments
---

### Post by Crosbie on 2007-05-01
Having an odd problem with my gnome desktop... 

On login - but not always - I find that there's a tiny compressed window showing under where my mouse pointer is, with the accompanying titlebar (at the bottom) reading 'gnome-panel'.  All I can do with it is shut down the window, upon which my 'show desktop' button - which I added to the panel bottom left - disappears. 

???

Hope someone has a clue what's going on here... I've tried removing and replacing it, but same issue.

---

### Post by Crosbie on 2007-05-02
Just to add some more specifics (and bump):  The widget is Show Desktop Button 2.18.1 - and it loaded normally today, so definitely an intermittent problem.

---

### Post by haricharan on 2007-05-02
you can try locking your desktop icon to the panel..that way it wont move to another panel instance....

---

### Post by Crosbie on 2007-05-02
Thanks for the suggestion - I'll try that and report back if it behaves oddly again. :)

---

### Post by Crosbie on 2007-05-06
Hmm, got the same behaviour again today.

Attached is a screenshot of the lower left corner of my screen.  this shows the 'gnome-pnael' bar which seems to refer to the odd lozenge-shaped microwindow showing upper-right here (actually it's bang centre of the screen).

Any thoughts anyone?

---

### Post by 4tro on 2007-05-07
the problem isn't only related to that button.

I see those small window thingies now and then.
they can be anything on the gnome-panel, even the clock.
killing those windows with xkill will either stop the applet from showing on gnome-panel or it will restart one of the applets.

i have had this behaviour with: the clock, the window-list, power-manager applet, and also with the desktop (not being a gnome-panel problem probably)

This behaviour occured first when i updated to feisty testing, now running clean feisty release but the problem is still there.

Hope this helps in finding the problem.

---

### Post by metalheart on 2007-05-07
Please check what settings you have for gnome-panel in the Computer -> Preferences -> Sessions -> Current Session. I have Order = 50, Style = Restart.

---

### Post by 4tro on 2007-05-08
> **metalheart said:**
> Please check what settings you have for gnome-panel in the Computer -> Preferences -> Sessions -> Current Session. I have Order = 50, Style = Restart.

i have Order=40 Style = Restart

---

### Post by Crosbie on 2007-05-08
> **4tro said:**
> i have Order=40 Style = Restart

As do I.  You think it should be 50?

---

### Post by Crosbie on 2007-05-10
> **Crosbie said:**
> As do I.  You think it should be 50?

Well, I've gone ahead and made this change.  Will report back on any change in behaviour.  (If I don't get back, assume all is well!)

---

### Post by orb9220 on 2007-05-10
Also sometimes removing the offending applet then relog on so you boot without it there then re add it to panel.

---

### Post by Crosbie on 2007-05-15
So, my problem is back - with some slight diffs!

Attached image: Beryl has tried valiantly to attach some window icons to this mini-window.

WTF?

---

### Post by 4tro on 2007-05-16
I don't think that's beryl, it seems like a systray being populated

---

### Post by Crosbie on 2007-05-20
> **4tro said:**
> I don't think that's beryl, it seems like a systray being populated

I'm pretty sure it is... the icons to the left are identical to those from the Emerald theme 'MacVrun Flipped', which I'm using.  Not so sure about the little window icon.

---

### Post by shanike on 2007-05-20
> **Crosbie said:**
> Hmm, got the same behaviour again today.

Attached is a screenshot of the lower left corner of my screen.  this shows the 'gnome-pnael' bar which seems to refer to the odd lozenge-shaped microwindow showing upper-right here (actually it's bang centre of the screen).

Any thoughts anyone?

i get the same thing. funny thing is that this panel appears in more-or-less constant cycle - like every 4th or 5th boot....

[IMG]http://img133.imageshack.us/img133/4568/gnomepanelry2.png[/IMG]

---

### Post by 4tro on 2007-05-21
we should try to find out if it is the same thing showing up every time,
every time we see one we should watch what window it is by using xwininfo

---

### Post by aeiah on 2007-05-22
i have the same problem, as does my girlfriend.

this is a cap of the bottom left quarter of my screen, so the strange small window is actually in the middle. i always get one called 'untitled window'.

[img]http://img502.imageshack.us/img502/5669/screenshotvw9.png[/img]

this strange small window thing appears for me on both edgy and feisty, and if you do xwininfo on it, it just registers the desktop, not the window you click on. if i reload beryl the problem goes away so im thinking its to do with the way we're all loading beryl. i just load it up in the start up programs tab of sessions with 'beryl-manager', but it might be loading it too quickly sometimes

---

### Post by Crosbie on 2007-05-26
Ah, interesting to see others having this problem.  

Shanike: yes, it appears to be a fairly regular cycle for me too.  Haven't kept a record though.
4tro: What info do you expect to get from xwininfo?  I'll try to remember to do this & post it next time anyway.

Mine seems to be evolving/gestating/mutating... this is the latest manifestation.  It's growing!

---

### Post by 4tro on 2007-05-26
xwininfo on the contents of the window won't work, on the border it does work though, just getting a hex value though, no name.

---

### Post by Crosbie on 2007-06-08
In my latest manifestation - yes, it's back again - xwininfo does give results.  Dunno whether they're meaningful to anyone, but here goes:

```
xwininfo: Window id: 0x1200022 "Desktop"

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1280
  Height: 1024
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1280x1024+0+0

```

---

### Post by linedpaper on 2007-06-08
i'm having the same problem as well...

---

