---
title: "Workspaces cube dissapears"
date: 2007-05-06
forum: Desktop Effects &amp; Customization
---

### Post by readitsideways on 2007-05-06
Hi

I'm very new to Ubuntu and love it so far. One problem I'm having, though, is that while I have enabled desktop effects and the workspaces cube, the cube doesn't work. The window effects are fine, but no cube.

Also, I set it to have 4 workspaces, but they keep disappearing down to just one. THis all worked using the live CD and initially after installing yesterday but not now. Any ideas? Should I install Beryl?

Another thing: while the window effects work great, they don't work with playing movies - the movie screen goes blank. Movies work fine without effects.

I'm running an HP laptop nx6110 with 512M RAM 1.8GHZ and (I think) a 128 MG graphics card

Thanks

Duncan

---

### Post by schnupi on 2007-05-06
Thats a fairly common problem, i had it myself as well. Here is the solution

1) type gconf-editor into the terminal
2) go into apps -> compiz -> general -> screen0 -> options
3) find hsize and change it the value to 4

That should do the trick.. hope this worked

good luck

---

### Post by readitsideways on 2007-05-06
Hi

Thanks for the help, but it didn't work. 

I set hsize to 4 and rebooted and I had 4 workspaces but no cube. 
I then disabled and re-enabled desktop effects and my workspaces disappeared again and I was left with one.

Any ideas?

Duncan

---

### Post by staib on 2007-05-06
I got the same issue here, Duncan.

Worked fine yesterday (even took a video to show the Ubuntu doubters back at the office :) ) but today just doesn't want to play fair...

On my login I now have 3 workplaces showing (bottom right) and on the other (my wife's) there is now only one - no cube's on either - but wobbles aplenty.

I too tried:

1) type gconf-editor into the terminal
2) go into apps -> compiz -> general -> screen0 -> options
3) find hsize and change it the value to 4

I am assuming you don't need to do a 'sudo gconf-editor' ?

Graphically I am using the Envy nvidia drivers that I d/l for 6.10 but that seem to be working fine on 7.04

Nick

---

### Post by axle_foley00 on 2007-05-06
> **schnupi said:**
> Thats a fairly common problem, i had it myself as well. Here is the solution

1) type gconf-editor into the terminal
2) go into apps -> compiz -> general -> screen0 -> options
3) find hsize and change it the value to 4

That should do the trick.. hope this worked

good luck

Thanks very much. That seemed to work for me.

---

### Post by schnupi on 2007-05-06
> **readitsideways said:**
> Hi

Thanks for the help, but it didn't work. 

I set hsize to 4 and rebooted and I had 4 workspaces but no cube. 
I then disabled and re-enabled desktop effects and my workspaces disappeared again and I was left with one.

Any ideas?

Duncan

Hmm i how does your workspace thingy look? is it just one big thing like mine in the picture below or is it seperated?
 
Eventhough i've hsize hsize set to 4 if i right click the panel and go to preference its set to 1. like the number of workspaces is 1 and the number of rows

Just in case u dont know how to use the cube 
CTRL+Alt+left mouse
and if u want to switch to the next workspace ctrl+alt+right/left arrow

---

### Post by readitsideways on 2007-05-07
Hi

My Screenshot attached below. The cube was working on the live CD, and initially when I installed Ubuntu (for about 10 min) but not since then. 

After my 4 workspaces dissapear into one, as in the attachment, I can set them back to four, buT no cube.
This is a bit irritating as I love the cube!

Duncan

---

### Post by staib on 2007-05-07
Well, well, well...

I switched off 'Desktop Effects' - took a deep breath and installed Beryl - I already had the Nvidia drivers installed from Envy...

Everything went fine - rotating cube worked immediately, placing ticks in the appropriate Beryl Manager boxes soon had raindrops falling - no problems with the edges of windows - using the Emerald Theme Manager I chose a cool transparent web 2.0 look - and windows now even 'roll up' neatly.

VLC media player is not happy with Beryl (but Mplayer still works OK).  And so far no crashes or other signs of instability.

Cool stuff for sure,

Nick

---

### Post by Radamanthys on 2007-05-07
> **schnupi said:**
> 
Just in case u dont know how to use the cube 
CTRL+Alt+left mouse


Thanks, this is the tip I've been missing :)

---

### Post by schnupi on 2007-05-07
> **readitsideways said:**
> Hi

My Screenshot attached below. The cube was working on the live CD, and initially when I installed Ubuntu (for about 10 min) but not since then. 

After my 4 workspaces dissapear into one, as in the attachment, I can set them back to four, buT no cube.
This is a bit irritating as I love the cube!

Duncan

Hmm i really couldnt tell you whats wrong with it cause i am just a newb too :) .. ok well try to download the compiz manager

go to synaptic package manager and search for gnome-compiz-manager. after u installed it u ll be able to find it in system->preference->gl desktop. there go to workspaces and set ur desired settings

---

### Post by readitsideways on 2007-05-08
```
go to synaptic package manager and search for gnome-compiz-manager. after u installed it u ll be able to find it in system->preference->gl desktop. there go to workspaces and set ur desired settings
```


Yaaayyy! Working great, thanks. And there're some great settings there!

Duncan

---

### Post by schnupi on 2007-05-08
> **readitsideways said:**
> ```
go to synaptic package manager and search for gnome-compiz-manager. after u installed it u ll be able to find it in system->preference->gl desktop. there go to workspaces and set ur desired settings
```


Yaaayyy! Working great, thanks. And there're some great settings there!

Duncan

your welcome ;)

---

### Post by Garfield83 on 2007-05-10
> **schnupi said:**
> Hmm i really couldnt tell you whats wrong with it cause i am just a newb too :) .. ok well try to download the compiz manager

go to synaptic package manager and search for gnome-compiz-manager. after u installed it u ll be able to find it in system->preference->gl desktop. there go to workspaces and set ur desired settings

Thank you! I had the desktop cube running last night and this morning it refused to work. Installing the compiz manager has made it work! :)

---

### Post by pondochris on 2007-05-11
awesome thanks!!!:guitar:

---

### Post by tarek on 2007-06-18
Hi, I don't have the workspace problem, but when I play movies I get a black screen. If I turn bery/compiz off they work fine.

Any idea how to fix this? I'm using 7.04.

Thanks,
tarek

---

### Post by morghi76 on 2007-06-19
I also experience the same problem! I used the cube for about two weeks. Today, all of a sudden, they disappeared!
With the compiz manager I fixed it!

T H A N K  Y O U!

---

### Post by kraymore on 2007-08-19
i installed the gnome-compiz-manager package and i still dont get a cube.  

opening up the settings in gconf-editor i will tell you what i have

apps-compiz-general-allscreen0-options

hsize=4
number_of_desktops=1
outputs 1680x1050+0+0
vsize=1

i dont know what else to do to get it to work.  

system-preferences-gl-desktop

workspaces, cube and rotation, selected
number of viewports, 4
cube, skydome
rotation, flip on dnd

--

thats all, dont know how to get it enabled.  i'm running gutsy gibbon

your help would be appreciated

---

### Post by Lithium17 on 2007-08-19
What did you expect, for it to work flawlessly from the word go? That is the whole point in it being at a testing stage.

---

### Post by kraymore on 2007-08-19
it has worked for me in gutsy gibson just fine until i unchecked workspace on a cube in desktop effects, then check it back again.  i think its rather fine to think that if something once worked, it can work again. 

you did not mention what you were running and if you had heard of other people having the same problem you have, assuming you do, or do not, i wont jump there.  i will say "it once worked, its not unreasonable to say it wont again"

---

### Post by PHuN on 2007-08-19
I ran into the issue of no cube rotation, changed h_size to 4 through gconf...
Cube is back, but to the point of being unusable, it will rotate, but all of the 4 sides are the same desktop, making a type of array creating 4 0f each workspace in layers and I have to switch between each desktop through keyboard.  This is actually quite cool to some extent, but I have no reason to use 4 separate workspaces per 4 desktop (16 workspaces) when I primarily only use 3-4 "places", mostly 3. As you see this is quite useless to me, because I use compiz not just for the effects (which are awesome) but also for the enhanced usability (yes, it is tooooo usable right now and I want to make it more functional).

Does anyone know where I went wrong, or better how to revert back to default 4 desktops with one workplace each.

It would be much appreciated.

If you need me to explain it better please post back and I will try harder, with steps I believe that got me to this point.

EDIT: I solved my issue with having layers of desktops, there was an option in compiz setting manager under general, I had both options set to 4, won't do that again.

---

### Post by Taum on 2007-08-20
I had the loss of workspaces, too, and the first line of code helped, but the compiz manager was a lot more user friendly!  Thanks!

---

### Post by xxhaloownerxx on 2007-09-14
i know this thread is just about as good as dead, but how does one switch the pictures  on the top and bottom of the cube? it wont let me pick any of mine :( any ideas? :)? 

Edit: i had to save it as a png file, but now the image is all.... streached out around the edges...

---

