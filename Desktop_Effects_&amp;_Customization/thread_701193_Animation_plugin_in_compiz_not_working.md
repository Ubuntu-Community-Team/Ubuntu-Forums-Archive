---
title: "Animation plugin in compiz not working"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by karthik_jce on 2008-02-19
Hi,

    I have installed compizfusion on my feisty. I am able to get all the desktop effects like cube, tab switching, shift switching, snow skydome etc. to work but not animations.

   I tried different options in compiz setting manager--> animations but none of them seems to work. Any idea what could cause this ?

Regards
Karthik

---

### Post by chavanak on 2008-02-19
Have you enabled the animations?? Its a very basic thing but people tend to forget. And also type compiz in terminal and post the output here

---

### Post by karthik_jce on 2008-02-25
I have anabled the plugin, also I checked for compiz-fusion-extra package and it is also installed, but still I am not able to get it to work. 

Any thoughts on this ?

---

### Post by iobelisk on 2008-03-06
bump, i have this same problem. everything is enabled: no animations, everything else is fine

i have it running on my other laptop though!

---

### Post by iobelisk on 2008-03-09
hi, sorry to bump this again. but i've searched quite a bit on this forum, google and also consulted folks at the compiz irc channel but to no avail. i have removed ALL compiz packaged and reinstalled them, but to no avail.

everything else runs fine, in fact the default animations are also working, but the changes i make in ccsm within the animations plugin do not work. all changes to other plugins run fine. i noticed that there were a few folks with this same problem, but i never saw this issue resolved


i'd be grateful if somebody could help me find a way to resolve this.

compiz gives me the following output:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

i have an nvidia 8400 GS M video card. like i mentioned-- everything in compiz except the animations plugin seems to work fine

thanks!

---

### Post by eagledrc on 2008-03-13
i have the same problem
when i entered compiz in the terminal, i got some of the same output that iobelisk got, but then everything flashed and i could only see my desktop background, nothing else.  none of the compiz shortcuts worked, to try to move around, so i had to reboot.  i don't wanna try it again right now....

---

### Post by eagledrc on 2008-03-13
...and i solved it (for my part at least)
system>preferences>advanced desktop effects settings>animations>minimize animation>
click on the top entry in that white box (default is zoom) and click edit.  make the minimize effect "beam up," click ok, and then click back.  minimize a window, and then bring it back up again.  you should have this shiny sweet animation.  you can choose random or any other effect and also mess with the duration.  hope this works for you

---

### Post by RebelwithoutaClue on 2008-03-13
Thanks eagle, that worked for me too,  which was  something of a surprise as when I typed compiz into a terminal, my results were similar to the contributor above only without pixmap textures and despite the mental flashing screen and disappearing apps and taskbar not actually locking up and needing a reboot.

I know it's silly but I was feeling quite put out that I didn't seem to be getting an window animation.

:)

---

### Post by eagledrc on 2008-03-14
yeah i like that stuff too lol

---

### Post by prospero52 on 2008-03-14
I had the same problem with getting animations to work even when they were enabled in the Advanced Desktop Settings Manager.  I got all mine working by choosing 'Advanced Search" in the Manager...Select 'Animations Enabled'...then select 'Effect Settings'.  Then in the lower window, I just had to check "Random Animations for all Events" and 'Voila'...all animations came to life.  Hope this helps.

---

### Post by lilalmond on 2008-03-15
hello

im tryin desperatly to make the animation in compiz fusion to work, but it doesnt
I read what others wrote before and i typed compiz in a terminal .now my puter is kinda screwed up   i cant close or open my current windows.i cant even paste what i copied from the terminal.
My top bar from the window also disappeared
Dunno what to do, guess i have to reboot
Any help would be welcome before i reboot
thx

---

### Post by lilalmond on 2008-03-15
I cant do anything else then using this window (ubuntu forum)  
My winodw from the terminal is minimized but cant open it
tried to alt+F2 to type reboot   but it doesnt work
Im stucked on this window
Please any help

---

### Post by lilalmond on 2008-03-15
Please anyone?

---

### Post by lilalmond on 2008-03-15
i know im in the wrong thread to get help but as i said before im just able to use this %&¤&%! window...
If nobody replies i'll have to restart the puter manually using the start button...
Without solving my problem :(

---

### Post by iobelisk on 2008-03-15
hi, configuring the animations plugin to randomly select any animation for any action works, although not too well. but the idea is to be able to set select animations for each action. for some strange reason this does not work. i have mimicked my settings on the other laptop (on which everything works sweet and fine) but to no effect.

i've searched around quite a bit and there does not seem to be a posted resolution to this on this forum, nor have i been able to find anything via google.

lilalmond, if nothing else works restart x by hitting ctrl alt backspace.

---

### Post by reasonably_clever on 2008-04-12
i have a similar problem. I am using gutsy on intel gma 950 with 2gig system ram.

the animation plugin cannot be enabled. Whenever i enable it, i go back a screen and its disabled again...

maybe its a hardware compatibility issue??

any link to minimum system requirements or anything for compiz/animation?

---

### Post by magicmanfk on 2008-05-25
> **prospero52 said:**
> I had the same problem with getting animations to work even when they were enabled in the Advanced Desktop Settings Manager.  I got all mine working by choosing 'Advanced Search" in the Manager...Select 'Animations Enabled'...then select 'Effect Settings'.  Then in the lower window, I just had to check "Random Animations for all Events" and 'Voila'...all animations came to life.  Hope this helps.

thanks man, that worked like a charm!

---

### Post by i22yb on 2008-06-07
Ok, this took me a while to figure out on my system as well, until I realized what I did!

The problem is that K/Ubuntu has it's own desktop effects default settings which can override what the Compiz Config Settings Manager uses.

I use Kubuntu, and here is what I did to fix the problem (ubuntu/gnome menu options will differ somewhat):

1) Go to "System"..."Desktop Effects", and select "Custom Effects", then click "Apply".

2) Restart X (Control-Alt-Backspace, or reboot your system).

3) Go into "Settings"..."Advanced Desktop Effects Settings" and adjust compiz settings as desired.

Presto, now it should be working!

---

