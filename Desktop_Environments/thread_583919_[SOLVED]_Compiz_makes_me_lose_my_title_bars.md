---
title: "[SOLVED] Compiz makes me lose my title bars"
date: 2007-10-20
forum: Desktop Environments
---

### Post by jeffpriz on 2007-10-20
Just did a fresh install of Gutsy, and it's looking nice so far, EXCEPT for not really getting the compiz stuff to function :(

I turn on the Visual effects, and it makes me install the Nvidia drivers.. ok, a quick reboot and things work there... but, with the Nvidia drivers my max resolution/refresh are 1024x768 @ 50hz (headaches incoming).  So I use Administration ---> Screens and Graphics to choose my monitor (a 17" dell crt) so that i can get some better choices... except then the windows loose their title bars (which means no moving  the windows, no control buttons, no window resizing)..

Is there a fix?  Or am i stuck with the choice of the pretty stuff on @ a poor resolution, or a good resolution with the pretty stuff off?

---

### Post by MorayJ on 2007-10-21
Not going to be much help, I'm afraid. There may be a bug relating to this as I searched for compiz "window decoration", I think and got a few answers on an earlier installation.

But I did want to mention as an aid, because it was the most frustrating point, is that you can move windows by holding down the LMB with ALT.

---

### Post by benerivo on 2007-10-21
This might not work, but try installing ''Compiz configuration settings manager' from Synaptic. Open it from the main menu and make sure 'windows decoration' is ticked.

---

### Post by HMartinho on 2007-10-21
Hi there;

What exactly do you mean with "loose" title bars?
Maybe they are just way too much transparent, I don't know how to set the title bar transparency but mine are also too much transparent and i can't find where to change it.
f I find it out I'll let you know.

Cheers.

---

### Post by SalsaDoom on 2007-10-21
Hey, I had this problem in 7.04. Not sure if its "fixed" in 7.10 or not (I've been running the beta for weeks until the completed product, I don't remember if I entered it manually or not). 

But anyway, I had to add the following lines under the "Device" section.

    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"

Then it worked fine for me. 

Good luck :)
--SD

---

### Post by jeffpriz on 2007-10-21
thanks for the replies.

Salsa, where did you add those options?

I'll go d/l the configuration mgr now.

jeffpriz

---

### Post by jeffpriz on 2007-10-21
The compiz configuration manager is really cool.. lots of things to play with..   I did verify that the "window decoration" selection is checked.. so that's not it.

I played around a little bit to see if I disabled any of the effects if it would help me out, but no luck yet... :(

---

### Post by ReloadedFusion on 2007-10-21
Hi I have this working by using the emerald window manager.

To do this you need to install emerald

sudo apt-get install emerald

Then in the Compiz Settings utility click on the window decoration icon and add the following in the command line field: 

emerald --replace

This enabled the borders for me but then i had to ensure the following plugins were also enabled so i could move windows around:

Move Window

and 

Place Windows

You can change the border apperance by going to the emerald theme manager under System->Preferences..

Hope this helps

---

### Post by jeffpriz on 2007-10-22
thanks for the tip on Emerald.. but it hasn't helped.. still the same problem. 

Just for grins I went through and disabled my restricted Nvidia drivers (and therefore the Compiz stuff as well), and then went through the process again.. hoping (insanely) that it would work out differently.. but same thing.    
When I enable the Compiz again (and it re-enables my Nvidia drivers) I'm back with resolution choices maxing at 1024x768.  I again choose my monitor type, which again gives me more choices, the Compiz breaks.

I guess, is there a way to get myself my desired 1280x1024 @ 75hz another way than through that process?

---

### Post by oneadvent on 2007-10-22
Make sure you have a very basic non-transparent emerald theme. (or use one of the ones in the repos.) I have had some that don't work so well. 

If it works with the basic non-transparent one, then try another and get to the real cool ones.

---

### Post by Eggbanjo on 2007-10-22
I only managed to get emerald working by using

sudo emerald --replace

but i dont seem to have any themes and i have to leave terminal running.

Any ideas??

---

### Post by oneadvent on 2007-10-22
it is easier to get the default through the package manager, but you can also get some really good ones from gnome-look.org.

The command line to start synaptic package manager is:
```
$sudo synaptic
```

That should start you up, then search for emerald and grab the themes.

oh, and as for not being able to use the terminal, try Alt-F2 and type emerald. Or another terminal.

EDIT: it is much easier to deal with Emerald and Compiz if you download the compiz icon

---

### Post by Eggbanjo on 2007-10-22
when i was using beryl on feisty you would load up emerald and download the themes thru it. However when loading emerald in gusty its just the one theme and none can be found in synaptic.

---

### Post by oneadvent on 2007-10-22
Sorry for the very long delay, I am a working man after all.

Do this and I think it will help you out a ton.

Download the fusion-icon start it with alt-F2, and get to emerald that way. (It is at the top of the menu when you click on it.)

That Emerald is the same as the one I had with Beryl. (as far as I can tell.) 

Grab a theme from gnome-look and install it the same way you did before, and give it a test drive. 

Let us know what happens.

---

### Post by jeffpriz on 2007-10-22
In the other Compiz titlebar thread that is going, they said to do this:
sudo nvidia-xconfig --add-argb-glx-visuals -d 24

and that seems to have helped me some... I now have title bars... they are just completely transparent.. but that is progress!

---

### Post by adamorjames on 2007-10-22
Anyways you don't NEED titlebars lol. Using alt key + clicking and dragging the window moves the window.. not sure if it was mentioned already. Oh well... :)

---

### Post by jeffpriz on 2007-10-22
no title bars.. now that's just being silly ;)

anyways, I uninstalled Emerald and now my title bars are back not transparent any longer!.. so i think I've got to where I want it!  WOO HOO

---

### Post by oneadvent on 2007-10-22
hum...I have an ATI card, so I do not know anything about nvidia sorry

---

### Post by adamorjames on 2007-10-22
> **jeffpriz said:**
> no title bars.. now that's just being silly ;)

anyways, I uninstalled Emerald and now my title bars are back not transparent any longer!.. so i think I've got to where I want it!  WOO HOO

:lol: ok mark this thread as "[SOLVED]".

---

