---
title: "window sizing in Unity - settable?"
date: 2012-01-09
forum: Desktop Environments
---

### Post by freebird54 on 2012-01-09
Whenever I start an application from the Unity environment, the window opens at whatever size and configuration it pleases.  In every other setup I have ever used on Linux (from TAMU in '93 through various 'buntus to  11.04 (Classic)) an application will retain its window size from the values it had when last closed.

Can someone point me at a configuration file that is likely being read, or a setting in Unity or the shell that is overriding it?  The last remaining serious irritant in a workable Unity setup!

Maybe I was off the 'net for too long, but I fear I've forgotten more than I know - and that half of what I think I remember is no longer correct!

Thanks in advance...


BTW:  I asked a week ago, with no response - am just suspecting no-one knew what I was asking for!

FB

---

### Post by Krytarik on 2012-01-09
It might be related to the "Automaximize" feature of Unity?:

[http://lh6.googleusercontent.com/-3XcNlxPOCww/TpghdJRonyI/AAAAAAAAAiU/EQ189FC5olM/s1600/CCSM2.png](http://lh6.googleusercontent.com/-3XcNlxPOCww/TpghdJRonyI/AAAAAAAAAiU/EQ189FC5olM/s1600/CCSM2.png)

If yes, just set its value to 100%.

Hope it helps.

---

### Post by freebird54 on 2012-01-09
Thanks for the thought. I was crawling all through Compiz trying to figure out if anything there sounded like a possibility, and no luck so far.

I guess I'm out of practice at describing these things so that others CAN actually tell what's going on!  I have several small programs, including indispensable ones like mahjongg (!) which open much smaller than is ideal for me (I'm across the room from a 40" LCD). Previously they always opened at the size that I used them (larger) although usually not where I wanted them.

Stranger still is that others *DO* behave (TBird, FF, AbiWord etc) so it makes deciding on the common factors difficult.  Any other search directions come to mind?  Anyone know the mechanism it uses on other shells to 'remember'?

Thanks...

---

### Post by stinkeye on 2012-01-09
Use the ccsm **Window Rules** plugin to set the windows of apps that don't 
remember last state to maximized or fullscreen.
or

Use the "size rules" tab if you want a certain size and then use 
the **Place Windows** plugin to set a screen position.

---

### Post by freebird54 on 2012-01-10
Ahh!  Partial success!  Thank you - I hadn't even noticed that plugin before...

Now  -  if only I can correctly identify other specific windows to it, as I suspect some hide their secrets well... :)

Thanks for the help - now I only await 12.04 and whatever flexibility they decide to give back to us (because Unity does actually work well as a switcher/finder/workflow promoter - they just over-simplified a bit much).

I'll mark my threads as solved, though - and thanks again.

---

### Post by stinkeye on 2012-01-10
> **freebird54 said:**
> 
Now  -  if only I can correctly identify other specific windows to it, as I suspect some hide their secrets well... :)


Use the grab window button and then just click on the window.

---

### Post by freebird54 on 2012-01-10
Yup - discovered that when trying to get a couple of recalcitrant windows to acknowledge control!  Thanks again - more control than I expected to get, actually. :)

---

### Post by ftabor on 2012-01-13
> **stinkeye said:**
> Use the ccsm **Window Rules** plugin to set the windows of apps that don't 
remember last state to maximized or fullscreen.
or

Use the "size rules" tab if you want a certain size and then use 
the **Place Windows** plugin to set a screen position.

I cannot find this plugin, how/where do I start it?

---

### Post by stinkeye on 2012-01-13
> **ftabor said:**
> I cannot find this plugin, how/where do I start it?

ccsm > window management > window rules

---

### Post by ftabor on 2012-01-15
Great, thank you. I finally figured out I didn't have the plugin installed.

---

### Post by ftabor on 2012-01-17
> **stinkeye said:**
> Use the grab window button and then just click on the window.

I used this for Chrome, only I used the Non Maximizable option so that it remembers the last size.

---

