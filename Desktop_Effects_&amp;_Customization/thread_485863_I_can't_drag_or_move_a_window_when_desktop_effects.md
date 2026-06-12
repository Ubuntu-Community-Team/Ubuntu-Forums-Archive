---
title: "I can't drag or move a window when desktop effects is enabled  (pics)"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by ileo on 2007-06-27
I can't move or close the boxes since the red x is missing. I have to go down and right click to close any window. The wobble is there but I think something is wrong . Is there any changes I could make ?


[IMG]http://www.geocities.com/missthighs2xl/screenshot.png[/IMG]

[IMG]http://www.geocities.com/missthighs2xl/screenshot2.png[/IMG]

---

### Post by hyperair on 2007-06-27
Try this: Press Alt+F2 and type "gtk-window-decorator" without quotes.

---

### Post by ileo on 2007-06-27
I'll give it a shot when I get home, I literally had to reinstall Ubuntu like 7 times before I gave up. I got home at 5 and went to sleep at around 10:30 . I spent 5:30 hours to make a driver work and failed miserably LOL
I really want to make this work though .

---

### Post by rishabh on 2007-06-27
Actually, what you should do is this.
I assume you use Compiz Fusion, in which case you'd start by launching "compiz --replace".
However, you can install the "Emerald Theme Manager" by typing this in a terminal:

```
sudo apt-get install emerald emerald-themes
```

Then, when you want to start Compiz, use 
```

compiz --replace -c emerald &
```

It will now load the window decorations from Emerald. If you want to change the theme, go to System->Preferences->Emerald Theme Manager.

Hope it helps...

---

### Post by hyperair on 2007-06-27
@rishabh: Of course, that's if ileo was using Compiz Fusion. From what it looks like, ileo was using the regular compiz. It is after all, the desktop effects window. And from what ileo says, he's already installed Ubuntu 7 times, so that should be a fresh install of Ubuntu, with just Compiz.

---

### Post by rishabh on 2007-06-27
@hyperair:
I failed to notice :p

@ileo:
You could paste the output of

```
cat /etc/X11/xorg.conf
```

here.

It might have some info.

---

### Post by ileo on 2007-06-27
It might be 24hrs before I do but I will post it for sure. Thank you

---

### Post by hyperair on 2007-06-27
Uh I'd suggest you save that as a text file and attach it instead. I've had bad experiences scrolling up and down a thread with huge configuration files like that pasted within the body of the post >.<

Use this (in the run dialog(alt+f2) or terminal):
```

cat /etc/X11/xorg.conf > ~/Desktop/xorg.conf.txt

```

Then attach the xorg.conf.txt that should appear on your desktop to your post.

---

### Post by keesjelol on 2007-06-27
> **rishabh said:**
> Actually, what you should do is this.
I assume you use Compiz Fusion, in which case you'd start by launching "compiz --replace".
However, you can install the "Emerald Theme Manager" by typing this in a terminal:

```
sudo apt-get install emerald emerald-themes
```

Then, when you want to start Compiz, use 
```

compiz --replace -c emerald &
```

It will now load the window decorations from Emerald. If you want to change the theme, go to System->Preferences->Emerald Theme Manager.

Hope it helps...

i'm having this problem in compiz fusion and what your suggesting doesn't seem to work

---

### Post by hyperair on 2007-06-27
@keesjelol: By "doesn't work" could you provide details about what happens? Like the terminal output, for instance.

---

### Post by ileo on 2007-06-28
okay what I did when I got home is I added this 

Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"


to the device section

this enabled the borders but now it crashes for whatever reason but I honestly thing its my video card. Its a old car (2001) FX 5200AGP I think I need something better. I wish I could see the temps on the card.

---

### Post by dfreer on 2007-06-28
If it is nvidia you can try the nvidia-settings command to view temps

---

### Post by hyperair on 2007-06-28
Old?! You haven't seen old until you've seen the two graphic cards I have at home! nVidia Geforce 2 MX and nVidia Geforce 4 MX

Anyway, what crashes? Compiz or Emerald?

---

### Post by ileo on 2007-06-28
I don't have Compiz or Emerald on my PC. Just Desktop effects.

---

### Post by hyperair on 2007-06-28
Uhm.. this can get confusing. So, does the entire desktop effects thing crash? Or just the window borders? As in, if you Alt+Click can you move the window around after the window borders disappear?

---

### Post by ileo on 2007-06-28
the borders have appeared but when I attempt to close the window by clicking the red X it crashes , it just freezes and I have to restart. I was thinking it was my video card but now I'm thinking the install went wrong again .

Thanks for your concern

---

### Post by rishabh on 2007-06-28
@ keesjelol:
Try adding this to your xorg.conf:
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by Skneepa on 2007-06-28
Hi ,same problem here with a GF7600GS 256MB graphics card with the Nvidia-glx-new drivers. My Ubuntu install is fresh, never installed anything Beryl or Compiz related. Composite support is enabled, in my case if I had it disabled I couldn't even get to the desktop effects menu.  When I turn on desktop effects window menus dissappear and while moving the cursor over drop down menus graphics and text on them appear somewhat distorted, something like a strange blurr (although I'm not sure if this is related).

---

### Post by rishabh on 2007-06-28
@Skneepa:
Do you have these lines under Section "Device" in your xorg.conf?

```
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True
```"

---

### Post by Skneepa on 2007-06-28
No i actually don't...

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

I'll try adding them and post back later. One more question though. If I try Beryl or Compiz instead later will it be neccesary to remove those parameters I'm going to add now?

---

### Post by Skneepa on 2007-06-28
> **rishabh said:**
> @Skneepa:
Do you have these lines under Section "Device" in your xorg.conf?

```
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True
```"



Ok, I added these lines and restarted! Everything seems ok and no freezes occured until now. I'll post more impressions later.;)

---

### Post by ileo on 2007-06-28
I have add one more line just like you did, I only added one . :hammer: on me.

---

### Post by keesjelol on 2007-06-28
> **Skneepa said:**
> Ok, I added these lines and restarted! Everything seems ok and no freezes occured until now. I'll post more impressions later.;)

i've given up on the whole compiz fusion thing. So i tried using the desktop settings, which at first were not even there. fixed that. Now when i enable the desktop setting my window borders disapear, it seems just like everyone else.  heres exerpts from my xorg.conf

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
EndSection

```

```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

my card is a 319MB NVIDIA GeForce 8400M GS

---

### Post by offchance on 2007-06-29
the same thing happens to me. desktop effects makes my borders, title bar, and second workspace disappear. I tried to edit my /etc/x11/xorg.conf file but it was blank! 
nvidia driver 100.14.11. NVIDIA(R) GeForce(R) Go 6150

---

### Post by dfreer on 2007-06-29
> **offchance said:**
> the same thing happens to me. desktop effects makes my borders, title bar, and second workspace disappear. I tried to edit my /etc/x11/xorg.conf file but it was blank! 
nvidia driver 100.14.11. NVIDIA(R) GeForce(R) Go 6150

You would most likely not be able to log in if it was blank. Did you try to edit it as root, such as with this code?:
```
sudo gedit /etc/X11/xorg.conf
```
If it is really missing, try looking around that folder for a backup file... although like I said, i doubt you'd be able to log in if it was blank.

---

### Post by offchance on 2007-06-29
silly me, I typed x11 and not X11.

---

### Post by rishabh on 2007-06-29
> **ileo said:**
> I have add one more line just like you did, I only added one . :hammer: on me.

What exactly has happened?

---

### Post by izizzle on 2007-07-02
**FOR ILEO**
I can help you on this one. The problem is that you added 2 line that incorporate arbg visuals, you only need one. Do this: 
1. delete ALL the lines everyone has told you to add.
2. Open xorg conf file by typing: > gksudo gedit /etc/X11/xorg.conf
3. Find the section "Screen". Add a line right before the EndSection line that reads like this: > Option "AddARGBGLXVisuals" "true"
4. Now save the file, and restart X with ctrl-alt-backspace.

tell me if it works, izizzle

P.S: How did you install the drivers for your graphics card?

---

