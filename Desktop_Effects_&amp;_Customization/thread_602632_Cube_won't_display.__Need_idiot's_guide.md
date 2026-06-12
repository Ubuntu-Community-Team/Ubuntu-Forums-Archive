---
title: "Cube won't display.  Need idiot's guide"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by Nebutron on 2007-11-04
I am ruinning Gutsy Gibbon with athlon 64 3200+ and Nvidia Gforce 6200 LE.  Very very new to Ubuntu/Linux.  Please talk to me like I am an idiot!  Compiz seems to have installed with no problem.  Using restricted Nvidia drivers.  No error messages.  Wobbly windows work fine.  Desktop cube is checked, but don't see any change.  Thanks for any help you can offer.  Been surfing the forum for almost two weeks now and have not found anything that worked.

---

### Post by jimerickso on 2007-11-04
go to compizconfig settings manager
go to general options
go to desktop size
set horizontal virtual size to 4
set vertical virtual size to 1
set number of desktops to 4

also make sure rotate cube is enabled

---

### Post by Nebutron on 2007-11-04
> **jimerickso said:**
> go to compizconfig settings manager
go to general options
go to desktop size
set horizontal virtual size to 4
set vertical virtual size to 1
set number of desktops to 4

also make sure rotate cube is enabled

Thanks jimerickso,

Applied the values as you described.  Something I had not yet discovered.  Still no cube though.  Don't really have a clue why.  Tried rebooting, but no difference.  Again, I really appreciate the help.:)

---

### Post by Nebutron on 2007-11-04
Do I need to do something with the display settings outputs.  Output is currently set at 640x480+0+0

---

### Post by benerivo on 2007-11-04
Are you using Kubuntu? I know the cube it is more difficult to set up than in Ubuntu. It took me a week to figure out how to get the cube, and even now it still doesn't work properly with the dekstop screens in the panel.

I have my kde preferences set to only 1 desktop (in the kde control centre), and in compiz-fusion i have...

horizontal virtual size to 4
vertical virtual size to 1
number of desktops to 1

This got my cube working.

It's not the 'Output currently set at 640x480+0+0'. As mine says that and it works.

---

### Post by Nebutron on 2007-11-04
> **benerivo said:**
> Are you using Kubuntu? I know the cube it is more difficult to set up than in Ubuntu. It took me a week to figure out how to get the cube, and even now it still doesn't work properly with the dekstop screens in the panel.

I have my kde preferences set to only 1 desktop (in the kde control centre), and in compiz-fusion i have...

horizontal virtual size to 4
vertical virtual size to 1
number of desktops to 1

This got my cube working.

It's not the 'Output currently set at 640x480+0+0'. As mine says that and it works.

Thanks so much for your reply.  I am not using Kubuntu.  Kept the gnome settings.  I may try changing my number of desktops to 1 as you have and see if it changes anything.

---

### Post by Forlong on 2007-11-04
Go [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) if you have any further questions on how to get the cube.

---

### Post by Nebutron on 2007-11-04
> **Forlong said:**
> Go [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) if you have any further questions on how to get the cube.

Thank you Forlong.  I followed your article step by step.  Sorry to say still no cube showing up.  With all the suggestions I have tried and all my own efforts, am becoming pretty familiar with the compiz options.  Sad that I still can't get the cube to work.  If you or anyone else has suggestions, I would still be greatful.

Thanks you:confused:

---

### Post by Forlong on 2007-11-05
Could you please try to elaborate on what is not working for you?

---

### Post by Nebutron on 2007-11-05
> **Forlong said:**
> Could you please try to elaborate on what is not working for you?

Thanks again for your response.  sorry for my delayed reply.  I have successfully installed compiz advanced desktop.  I have the wobbly windows which works fine.  I am able to check the boxes for desktop cube, rotate cube, cube caps, and cube gears.  However, no cube appears.  All I see is my regular flat desktop.  Have tried uninstalling and reinstalling a couple of times.  I get no error messages.  Just no cube at all.

---

### Post by Nebutron on 2007-11-05
Commen sie aus Deutschland?  If so, your english is really excellent.  I lived in Deutschland for 3.5 years...an american soldier at the time.  Just curious.

---

### Post by keforex on 2007-11-05
I have the same issue, when I press Ctrl-Alt-Down I can only see all 4 desktops on a panel, flat. No cube. 

I don't have the "Desktop Plane"  enabled.

I have:

- Desktop Cube
- Rotate Cube
- Cube Reflection
- Cube Caps

and... no cube.

---

### Post by Forlong on 2007-11-06
> **Nebutron said:**
> Commen sie aus Deutschland?
Hehe, that's correct. Although it's *kommen*, actually. And you wouldn't have to call someone "sie" on a forum like this. :)
> **Nebutron said:**
> If so, your english is really excellent. 
Thanks, we all have english in school over here but I always had bad grades ^^
> **Nebutron said:**
> I lived in Deutschland for 3.5 years...an american soldier at the time.
Cool. Where were you based at?


Anyway... lets get back to topic ;)

Did you (both) make sure this is set the right way:
> Secondly, we have to increase the number of the virtual desktops to **4** at **General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size**
(the other two options have to be left at **1**)
So in the end, it should look like this:

---

### Post by keforex on 2007-11-06
Yes, mine is set to 4, 1, 1 and I still can't see a cube, just flat panels.

---

### Post by Forlong on 2007-11-06
And you read what I wrote about how to actually use the cube (in the guide)?
Ctrl-Alt-Down will *always* give you a flat filmstrip.

---

### Post by TheOtherLinuxFreak on 2007-11-06
.

---

### Post by keforex on 2007-11-07
> **Forlong said:**
> And you read what I wrote about how to actually use the cube (in the guide)?
Ctrl-Alt-Down will *always* give you a flat filmstrip.

This might make me look like an idiot, but yes, I've read the guide. But where is the line that tells me how to activate the damn cube? I mean, what is the key combination? I thought Ctrl-Alt-Something would do it? :confused:

---

### Post by Forlong on 2007-11-07
> Now we can switch desktops via [Ctrl]+[Alt]+[Left]/[Right] and spin the cube via [Ctrl]+[Alt]+[Left Mousebutton] (or via middle-click on the desktop)..

---

### Post by candtalan on 2007-11-07
> **keforex said:**
> This might make me look like an idiot, but yes, I've read the guide. But where is the line that tells me how to activate the damn cube? I mean, what is the key combination? I thought Ctrl-Alt-Something would do it? :confused:
ctrl-alt- left arrow
ctrl-alt- right arrow

FWIW I have had rather similar problems Ithink, and have found this thread very useful. However, I still could not get the effects enabled!!
I eventually realised that not all the suitable conditions were in fact being met - In the Guide I saw
'Last but not least, there are also certain hardware tests such as checking the amount of memory and the maximum 3D texture size of the card, compared to the resolution in use.'
and then I reduced my screen resolution, and then the effects could be enabled in
System>Preferences>Appearance
whereas they could not be enabled before doing this.

---

### Post by keforex on 2007-11-09
Thanks for the replies. Here's what happens:

1) When I use Ctrl-Alt-LeftMouseButtonClick
                 a. the mouse pointer disappears

2) When I use the same key/mouse combo but with "cube gears" selected
                a. the mouse pointer disappears
                b. I see the gears turning on the screen

Problem: Still no cube.


Hardware info:
              . Intel Core 2 Extreme @ 3.44GHz
              . Asus P5K3 Deluxe
              . 4 GB of RAM
              . nVidia 8800GTX with 768Mb RAM

---

### Post by white_sox_fan_82 on 2007-11-09
Once you press Ctrl + Alt, press the left-click on the mouse and DRAG/MOVE your mouse.  It will rotate the cube.  Ctrl + Alt + Left arrow or right arrow will move the cube as well.

Let us know if that works.

---

### Post by Forlong on 2007-11-09
> **keforex said:**
> 1) When I use Ctrl-Alt-LeftMouseButtonClick
                 a. the mouse pointer disappears

2) When I use the same key/mouse combo but with "cube gears" selected
                a. the mouse pointer disappears
                b. I see the gears turning on the screen
Great. Now try moving your mouse. :)

---

### Post by Nebutron on 2007-11-09
I have tried all the suggestions in this thread with still no success.  I have the wobbly windows, no problem.  I have checked the boxes for desktop cube, rotate cube, and cube caps.  No error messages coming up.  Just no cube.  Is it possible that my Gforce 6200 LE vid card is being blacklisted for the cube?

---

### Post by Gotit on 2007-11-10
Hi, I think I may have an answer for you.  I too was/am looking for how to get “the cube” to appear scaled down and rotate it in space.  After pulling my hair out and reading forums and blogs until my eye bled I finally haphazardly stumbled onto what I think you are looking for.

Assuming you have Compiz-fusion installed successfully and you have Systems > Preferences > Advanced Desktop Effects Settings ensure Desktop Cube and Rotate Cube are checked (I bet you've heard that enough!!).  In General Options on the Desktop Size tab make sure you have the “4, 1, 1” settings top to bottom respectively. Double click Rotate Cube to open the form, select the Actions tab, expand the General settings and read the entries for initiate.  I show Key = Disabled; Button = <Control><Alt>Button1.

When I hold down the Control and Alt keys and click Button1 (the left mouse button) the desktop scales back.  How far back it scales depends on where you have Zoom set on the General tab for Rotate Cube.  The higher the Zoom number the further back the desktop will recede, 0.300 is good for me.  If Zoom is set to 0.000 then the desktop will not recede at all and you will not see a cube.  Release the mouse button and the desktop will advance and fill your screen (return to normal).  

Now, scale back the desktop again (Ctrl+Alt+left mouse button) and move the mouse around to get the cube to tilt and spin. Yea!!!!  Let go of the mouse button and the side of the cube that is most prominent will fill your screen.  Ahhh... 

I have not found a way to make the cube hang and spin on it's own, but this should be enough to cheer you up!!!! :)

---

### Post by rainwalker on 2007-11-10
> I have not found a way to make the cube hang and spin on it's own

Unfortunately, there's no way to do that (yet?)

---

### Post by Nebutron on 2007-11-12
> **Gotit said:**
> Hi, I think I may have an answer for you.  I too was/am looking for how to get “the cube” to appear scaled down and rotate it in space.  After pulling my hair out and reading forums and blogs until my eye bled I finally haphazardly stumbled onto what I think you are looking for.

Assuming you have Compiz-fusion installed successfully and you have Systems > Preferences > Advanced Desktop Effects Settings ensure Desktop Cube and Rotate Cube are checked (I bet you've heard that enough!!).  In General Options on the Desktop Size tab make sure you have the “4, 1, 1” settings top to bottom respectively. Double click Rotate Cube to open the form, select the Actions tab, expand the General settings and read the entries for initiate.  I show Key = Disabled; Button = <Control><Alt>Button1.

When I hold down the Control and Alt keys and click Button1 (the left mouse button) the desktop scales back.  How far back it scales depends on where you have Zoom set on the General tab for Rotate Cube.  The higher the Zoom number the further back the desktop will recede, 0.300 is good for me.  If Zoom is set to 0.000 then the desktop will not recede at all and you will not see a cube.  Release the mouse button and the desktop will advance and fill your screen (return to normal).  

Now, scale back the desktop again (Ctrl+Alt+left mouse button) and move the mouse around to get the cube to tilt and spin. Yea!!!!  Let go of the mouse button and the side of the cube that is most prominent will fill your screen.  Ahhh... 

I have not found a way to make the cube hang and spin on it's own, but this should be enough to cheer you up!!!! :)


Ahah!  That did it!  Thank you so much for sharing your discovery.  Te cube was there all along,  Just couldn't figure out how to get it to come out and play!  Do you know if it is possible to suspend the cube so that you can view two sides at once?

---

### Post by candtalan on 2007-11-12
> **Nebutron said:**
> Ahah!  That did it!  Thank you so much for sharing your discovery.  Te cube was there all along,  Just couldn't figure out how to get it to come out and play!  Do you know if it is possible to suspend the cube so that you can view two sides at once?

(When I used sabayon) it was ctrl alt and click and drag the mouse cursor, I have not yet got to that stage with ubuntu compiz..... :-)

---

### Post by Gotit on 2007-11-12
As far as I have found, the best you can do is keep the cube in view as long as you hold the mouse button down.  Note: once you have the cube as outlined above, you can release the Ctrl and Alt keys.  Just keep the mouse button down to maintain the cube.  Once you release the mouse button, the desktop will fill the screen.

---

### Post by Nebutron on 2007-11-12
> **Gotit said:**
> As far as I have found, the best you can do is keep the cube in view as long as you hold the mouse button down.  Note: once you have the cube as outlined above, you can release the Ctrl and Alt keys.  Just keep the mouse button down to maintain the cube.  Once you release the mouse button, the desktop will fill the screen.

Thanks so much again.  It works just as you describe.  This has been so much fun.  My daughter and son are even taking an interest in Ubuntu now.  They had never even seen a linux program before.  I must tell you the help on this forum is great!  Hope to give back some once I get to know things better.  :)

---

