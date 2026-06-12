---
title: "Ubuntu 8.10 BTNX replacement tutorial"
date: 2008-11-02
forum: Desktop Environments
---

### Post by cecilx22 on 2008-11-02
With the release of Ubuntu 8.10, BTNX has been broken.  As such, I figured I'd write up a small, hopefully as clear as possible tutorial on how to 'replace' it with a few other simple utilities.

There have been a few others posts on this, and I've found them helpful after some head scratching.  I figured I'd try to make a simple, unified post.

So here is how I got my Logitech MX Revolution working again.

**1) Install 2 utilities: xmacroplay and xbindkeys**

```
sudo apt-get install xbindkeys xmacro
```

xbindkeys runs commands when certain keyboard key presses or mouse button presses are detected.  xmacro is a program for playing, shocker, macros.  It can be used to generate, amongst other things, keypresses in an X window

**2) Go through the (painful) button discovery process.  To do this:**

**a)** edit the configuration file for xbindkeys

gedit ~/.xbindkeysrc

delete the full contents of this file and add the following lines:

```

"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0"
b:1
```

This will echo a very simple macro to the macro player which will direct the results of said macro to the default X display.  In this case, it will generate a press of the 'enter' key.

**b)** launch a text editor window.  We will use this to see the results of the macro running

**c)** run the following command in the terminal window:

```
xbindkeys -n -v
```

Note: This will likely prevent the normal functioning of whatever button you are looking for.

**d)** select the text editor and start pressing mouse buttons until you get an 'enter' that will be button b:1 for your mouse.  Once you find the button, reselect the terminal and Ctrl+C the process to stop it.

Repeat the whole process for different b:#'s (i.e. b:2).  Make sure to note what button codes correspond to which buttons.  Also, try multi button presses if no single button generates an event.  For instance on my Revo, pressing the left and right buttons together is b:3

You should be able to find the button codes for most buttons using this process.  On my mouse, the only button I couldn't find was the search button (which is handled differently by the OS for some odd reason).

For my mouse, the list looked like this:

```
# Mappings for keys for MX Revo
# b:1	-	left mouse button
# b:2	-	left and right mouse button together
# b:3 	-	right mouse button
# b:4	-	mouse wheel up
# b:5	-	mouse wheel down
# b:6	-	mouse wheel left
# b:7	-	mouse wheel right
# b:8	-	back button
# b:9	-	forward button
# b:10	-	-none-
# b:11	-	-none-
# b:12	-	-none-
# b:13	-	media wheel up
# b:14	-	-none-
# b:15	-	media wheel down
# b:16	-	-none-
# b:17	-	media wheel press
```

this list is only for your refrence when you start binding button presses to macros.  You don't need to have it anywhere in any file (but it dosen't hurt to note them as comments in the ~/.xbindkeysrc file.

**3) Figure out the Xmacro names for the keys you want to simulate**

xmacro uses special codes to represent key presses and button clicks.  The simplest way to figure out what codes to use for what you want to do is by using the xmacrorec2 utility.

To do this, start xmacrorec2 in a terminal and redirect the output to a reference file.

```
xmacrorec2 > dump.txt
```

After starting xmacrorec2, press the scroll lock key to start recording actions.  Then press any key or button you'd like to know the code of.  When done, press scroll lock again to stop recording.  Then look in the dump.txt file:

```
cat dump.txt
```

You should see things like this:

```
MotionNotify 378 241
KeyStrPress XF86AudioMute
KeyStrRelease XF86AudioMute
KeyStrPress XF86AudioMute
KeyStrPress XF86AudioLowerVolume
KeyStrRelease XF86AudioMute
KeyStrRelease XF86AudioLowerVolume
KeyStrPress XF86AudioLowerVolume
KeyStrRelease XF86AudioLowerVolume
KeyStrPress XF86AudioLowerVolume
KeyStrPress XF86AudioRaiseVolume
KeyStrRelease XF86AudioLowerVolume
KeyStrRelease XF86AudioRaiseVolume

```

**4) Create your configuration file**

Using the button codes from step 2 and the xmacro codes from step three, form your configuration file.  Use the following format:

```
# Example for a key press
"echo 'KeyStrPress <xmacro code> KeyStrRelease <xmacro code>' | xmacroplay :0"
<mouse button code>

```

where <xmacro code> is replaced (including carrots) with the keyboard code from step three and where <mouse button code> is replaced with a button code from step two.

Simulating mouse button presses is a bit different, but follows the same idea.

The above example will simulate a key press followed by an immediate key release.  To configure multi-key presses, simply list all the keys, first as presses, then as releases, in a list seperated by spaces.

My final simple configuration file ended up looking like this:

```
# Mapping enter key to mousewheel right
"echo 'KeyStrPress Return KeyStrRelease Return' | xmacroplay :0"
b:7

# Mappings for media wheel
"echo 'KeyStrPress XF86AudioNext KeyStrRelease XF86AudioNext' | xmacroplay :0"
b:13
"echo 'KeyStrPress XF86AudioPrev KeyStrRelease XF86AudioPrev' | xmacroplay :0"
b:15
"echo 'KeyStrPress XF86AudioPlay KeyStrRelease XF86AudioPlay' | xmacroplay :0"
b:17
```


**5) Test your configuration**

Once all of the above is setup, test your configuration by running:

```
xbindkeys -n -v
```

in a terminal window.  Leave the terminal up and let the code run and try out your mappings.  When you are satisfied everything is working correctly, close the terminal window, and add a strait call to xbindkeys with no flags to your session.  For gnome, this involves opening the System->Prefrences->Sessions, click on Add, then put any name (i.e: xbindkeys) and put xbindkeys in the command box (without the -n (not daemon) and -v (verbose) options), just xbindkeys. The next time you restart you system xbindkeys will run automatically.

Please let me know if anything here is unclear.  Also, feel free to post your button mappings for others to use!

---

### Post by Macdelaney on 2008-11-02
Thanks for this, it's been very helpful since I forgot most of this after I discovered Btnx :P
Wouldn't it be easier to do the button discovery using xev? It directly tells you what button you're pressing.
I don't know if you're using it, but you could use revoco to change the click wheel behaviour to that of a normal click wheel (you can also set at which speed it switches to free spin and so)
There're just 2 things I can't get to work properly.One of them is that I dont know how to map the search button to something else, and the other thing I never got working without Btnx and i'm not sure how to explain it properly.
I use the compiz plugin Scale, which is similar to OS X's Expose, the problem is the key needs to remain pressed until I choose a window but if there's no "key up" event it will just loop back to Scale after I select a window, I have no idea how this was done in Btnx, so any ideas would be welcomed.

---

### Post by cecilx22 on 2008-11-03
Thanks for the info.  I didn't manage to discover xev.  If you'd like to put up a how-to I'll incorporate it gladly.

Also, the search button is actually mapped to the search key XF86Search.  Hope that helps with that.  I'm not sure what c:# that works out to, or if it's a combination.

As far as the 'Scale' plugin, I use it too.  If I map the functionality to a key press, it works fine, but to a mouse button I have the same issue you describe.  I'd call it a bug in 'Scale' rather than you doing something wrong.  Maybe put in a bug report?

---

### Post by Macdelaney on 2008-11-03
Regarding xev, it's pretty simple, you just open up a terminal and run "xev", after that a small window appears, when you click inside the window with, let's say, the left button a bunch of text comes up in the terminal, somewhere in this text it says "Button 1" (for the left button, of course), I can't test it right now to give you an example but it's not at all hard to see, and it's a lot less painful and simple than the method you used, since xev basically asks the X server to send it events whenever anything happens to the window. Also, you can read eny event such as the window being moved, resized, typed in, etc.

About the Search button, there's a way to change it to middle click, and I dont see why you couldn't change that to anything else, posted here -> [http://ubuntuforums.org/showpost.php?p=1617137&postcount=1](http://ubuntuforums.org/showpost.php?p=1617137&postcount=1)
It's quite old, but I think it should work, I'll have to try it when I get home.

And as far as the Scale plugin it worked fine in 8.04 with Btnx so i dont see why it wouldn't work now, but, of course, the how remains unanswered. I sure miss Btnx!

---

### Post by iamnotthemessiah on 2008-11-03
oh thanks for this,i was just about to test and see if [http://ubuntuforums.org/showpost.php?p=1617137&postcount=1](http://ubuntuforums.org/showpost.php?p=1617137&postcount=1) would work in intrepid.
this guide will be a blessing when i get around to it. search button as middle click is essential for me

---

### Post by AJLobo on 2008-11-03
Thank you SO MUCH for this tutorial. Thanks for saving those with the MX Revo from doing the trial and error work ;-)

By the way, the code for the search button is "c:0xE1" as shown by mgc8 in [_this post_]("http://ubuntuforums.org/showpost.php?p=6017927&postcount=1134").


Edit: Sweet! I just discovered the CompizConfig settings manager can detect the media wheel. I use it to flip the 3d cube around. If you try to change the mouse button setting for flipping left/right, you only get mouse buttons up to Button9. However, if you click the edit button next to that button, you can type in Button15/13.

I also mapped my search button to Button2 as done in the referenced post. Now I'm back to btnx functionality. The only thing is the annoying delay in xmacroplay.

---

### Post by iamnotthemessiah on 2008-11-03
great discovery on the cube rotation :D

---

### Post by Macdelaney on 2008-11-03
Great discovery in deed with the cube rotation, i'm using it for the Scale plugin.
I still can't make the Search button thing work! The Search window keeps popping up! 
My .xbindkeysrc in its pertinent part reads

# Mapping for Search button
"echo 'ButtonPress 2 ButtonRelease 2' | xmacroplay :0"
c:0xE1

after that I run xbindkeys -n -v, and oddly it tells me that there may be another program running which captures one of the keys captured by xbindkeys, which is incredibly strange since i have nothing running.
Any help would be much appreciated

---

### Post by iamnotthemessiah on 2008-11-04
to get rid of the search window popping up:
system > prefs > keyboard shortcuts
scroll down to the entry called 'search'
click it and disable by pressing backspace

---

### Post by seven-up on 2008-11-04
> I've not messed with multi-key press macros. If anyone wants to clue me in on this, I'll be happy to add it. 
well actually it's very simple, i wanted to do that for the 'show-desktop' option in compiz.
I manage to link my button10 on my logitech cordless click with this event :
> "echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStrPress d KeyStrRelease Alt_L KeyStrRelease Control_L KeyStrRelease d' | xmacroplay :0"
b:10
It seems that you just have to list every event one after the other ...

anyway thank you very much for your tuto !!

---

### Post by chris_j on 2008-11-04
I would just like to switch page's in my browser but it won't work?
My scroll button can click left/right. I want to use that to go to the next/previous page in my browser.  With the tut. above i made this macro...

```
"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0"
b:1

"echo 'KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left' | xmacroplay :0"
b:6
"echo 'KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right' | xmacroplay :0"
b:5
```

But it does'nt work as it should.  I can only go to the next page when i click the button for the previous page??  
I found out that scroll click right = b:5 and scroll click left = b:6

But my keyboard even works odd?  When te macro runs, and i press te left arrow on my keyboard i go to the previous page (normal you press ALT+ left arrow).
The same happens when i use the right button. Does the macro change's my keyboard to???

---

### Post by iamnotthemessiah on 2008-11-04
anybody elses search/middle button only function as middle button in firefox? and not when for example trying to drag/drop a file?

---

### Post by cecilx22 on 2008-11-04
> **chris_j said:**
> I would just like to switch page's in my browser but it won't work?
My scroll button can click left/right. I want to use that to go to the next/previous page in my browser.  With the tut. above i made this macro...

```
"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0"
b:1

"echo 'KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left' | xmacroplay :0"
b:6
"echo 'KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right' | xmacroplay :0"
b:5
```

But it does'nt work as it should.  I can only go to the next page when i click the button for the previous page??  
I found out that scroll click right = b:5 and scroll click left = b:6

But my keyboard even works odd?  When te macro runs, and i press te left arrow on my keyboard i go to the previous page (normal you press ALT+ left arrow).
The same happens when i use the right button. Does the macro change's my keyboard to???



Try adding release statements for the Alt key as well as the left arrow keys.

---

### Post by wilbbe01 on 2008-11-04
I have things working with this tutorial, but two of my buttons are controlled prior to settings this up (just do things I don't want them to).  Is there a way to turn off their default action so they only perform what I have told them to?

---

### Post by cecilx22 on 2008-11-04
I _think_ that this should capture the mouse events before they get to anything else.  If not, let me know what IS capturing them, maybe I can figure it out, but I'll warn you I don't have a lot of time.  :o)

---

### Post by wilbbe01 on 2008-11-04
The problem lies with the tilt wheel.  I use it to switch workspace left and right "ctrl + alt + left, and ctrl + alt + right" respectively.  I noticed today that the horizontal scrolling is also still being captured, as a page was scrolling when I pushed the wheel to the right.  Thanks.

---

### Post by cecilx22 on 2008-11-04
Actually, horizontal scrolling can be enabled/disabled in the System->Prefrences->Mouse menu, I think.  At least, for my laptop touch pad, it's there.  Don't know for 'normal' mice.

---

### Post by wilbbe01 on 2008-11-05
> Actually, horizontal scrolling can be enabled/disabled in the System->Prefrences->Mouse menu, I think. At least, for my laptop touch pad, it's there. Don't know for 'normal' mice.

I looked there and I'm not seeing it, any other ideas?  Thanks.

---

### Post by cecilx22 on 2008-11-05
you might try using xev to track down what is going on.  Not sure if it'll help, but it's worth a shot.  If that dosen't do it, I don't know what to tell you.  Maybe in your Compiz Config?

---

### Post by chris_j on 2008-11-05
I did enter the release key's.
Only when i click right something happens. I've changed the b:5 en 6 and
again only the right click works. When i start the macro i see the registration of the right click and the enter click.  When i click left nothing happens.  And in the browser also nothing happens :-(





```
"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0"
b:1

"echo 'KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L' | xmacroplay :0"
b:5
"echo 'KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right KeyStrRelease Alt_L' | xmacroplay :0"
b:6

```

---

### Post by cecilx22 on 2008-11-05
Only other thing I can think of trying making sure that you are using the correct button code for the mouse-wheel-left button.  Everything looks correct otherwise.  You PROBABLY don't want the left mouse button (b:1) mapped to 'enter' in a full config, as it will keep you from grabbing focus on a window by clicking on it though...  maybe try removing that and trying again?

---

### Post by chris_j on 2008-11-05
> **cecilx22 said:**
> Only other thing I can think of trying making sure that you are using the correct button code for the mouse-wheel-left button.  Everything looks correct otherwise.  You PROBABLY don't want the left mouse button (b:1) mapped to 'enter' in a full config, as it will keep you from grabbing focus on a window by clicking on it though...  maybe try removing that and trying again?

Yesss :guitar:

Stupid stupid me ](*,) i did the test again to figure out the b: numbers and
i made a mistake earlier.  Now right click is b:6 left click is b:**7**
and it works perfectly \\:D/
Thanx all ;-)

EDIT: one thing... how do i make this work ?

```
and add a strait call to xbindkeys with no flags to your session. For gnome, this involves opening the System->Prefrences->Sessions utility.
```

---

### Post by 4Play on 2008-11-05
thanks for the great tutorial!
I configured my VX Revolution to do most of the things I had in btnx (why did it have to become obsolete in 8.10 :( )
but there is a very noticeable and irritating delay, for example, when I want to to rotate the cube (crt+alt+left/right) it takes a measurable amount of time to start rotating, and sometimes I have to press twice to get it to register.
This is very annoying...is this just an issue with me or does someone else have this problem (and hopefully a solution)

edit: chris_j, you have to go to System->Preferences->Sessions, click on Add, then put any name (i.e: xbindkeys) and put xbindkeys in the command box (without the -n (not daemon) and -v (verbose) options), just xbindkeys. The next time you restart you system xbindkeys will run automatically.

---

### Post by cecilx22 on 2008-11-05
I don't have any noticeable delay at all.  Can you post your final config file?  Maybe there's something in there.

> 
edit: chris_j, you have to go to System->Preferences->Sessions, click on Add, then put any name (i.e: xbindkeys) and put xbindkeys in the command box (without the -n (not daemon) and -v (verbose) options), just xbindkeys. The next time you restart you system xbindkeys will run automatically.

Stealing this bit for the tutorial.  Thanks!

---

### Post by chris_j on 2008-11-06
> **4Play said:**
> 
edit: chris_j, you have to go to System->Preferences->Sessions, click on Add, then put any name (i.e: xbindkeys) and put xbindkeys in the command box (without the -n (not daemon) and -v (verbose) options), just xbindkeys. The next time you restart you system xbindkeys will run automatically.

Thnx :guitar:  It works perfect now!!

---

### Post by 4Play on 2008-11-06
here is the contents of my xbindkeyscr (making it simple for tests)...pretty straightforward, but using the mouse to change desktops is nowhere neare as fluid and responsive as using the keyboard (or with btnx)

```
# Mousewheel right -> turn cube right
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:7

# Mousewheel left -> turn cube left
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:6

```

For example, if I hold the mousewheel to the right (or left) the cube takes about 0.5 second to turn. Now, holding down ctr+alt+right turns it really fast. I know that some 'time' is lost due to the repeated 'press' then 'release' that occurs with the macro, perhaps compiz captures the press/release, even at a very high frequency,thus somehow limiting the cube rotation speed

perhaps if I could bind the kepress events to the 'pressing' of the mouse button, and the key release to the 'release' of the mouse button I would get more acceptable results...however I do not know how to trigger events on button press/release, just press.

Thanks for any tips :)

---

### Post by cecilx22 on 2008-11-07
> **4Play said:**
> here is the contents of my xbindkeyscr (making it simple for tests)...pretty straightforward, but using the mouse to change desktops is nowhere neare as fluid and responsive as using the keyboard (or with btnx)

```
# Mousewheel right -> turn cube right
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:7

# Mousewheel left -> turn cube left
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:6

```

For example, if I hold the mousewheel to the right (or left) the cube takes about 0.5 second to turn. Now, holding down ctr+alt+right turns it really fast. I know that some 'time' is lost due to the repeated 'press' then 'release' that occurs with the macro, perhaps compiz captures the press/release, even at a very high frequency,thus somehow limiting the cube rotation speed

perhaps if I could bind the kepress events to the 'pressing' of the mouse button, and the key release to the 'release' of the mouse button I would get more acceptable results...however I do not know how to trigger events on button press/release, just press.

Thanks for any tips :)
I should point out that most compiz plugins support mapping to mouse buttons directly.  You might try binding these in compiz to button6 and button7 (might be different than the b:# codes, I'm not sure).  Using this directly rather than mapping this to keys, and keys to action, might work better.

---

### Post by Pi314 on 2008-11-07
I'm looking for a possibility to use buttons (of my MX Revolution) as 'Control' or 'Shift'-Button.
Is it possible with xbindkeys to differ between a button-up and button-down event? That means that 'Control' is held down, as long as I hold down the mousebutton.

If I use e.g. "b:8" in the configuration, there will be only a single 'click'.

Greetings from Germany ;)

---

### Post by cecilx22 on 2008-11-07
I don't know of any way to do this, but that certainly dosen't mean it can't be done.  Let us know if you figure it out!

---

### Post by Pi314 on 2008-11-07
It seems that it should work in principle...

from xbindkeys' man-page:
```

       List of modifiers:
           Release, Control, Shift, Mod1 (Alt), Mod2 (NumLock),
           Mod3 (CapsLock), Mod4, Mod5 (Scroll).

       The release modifier is not a standard X modifier, but you can  use  it
       if you want to catch release events instead of press events.

[...]

EXAMPLES
[...]
       # Control+Shift+a  release event starts rxvt
       "rxvt"
         release+control+shift + a

       # Control + mouse button 2 release event starts rxvt
       "rxvt"
         Control + b:2 + Release


```

So I tried defining two events with xbindkeys, one for the butten-press and one for the release...
Unfortunately it seems to work with all "normal" keys, but not with 'Shift', or 'Control' :(

I tried it with both 'xte' (which I used also for other buttons) and 'xmacroplay' with the same result:
It works with keys like a,b,c,3,4,5 etc. but it doesn't with Control or Shift. They are "pressed" but not released.


Here are the passages from terminal, when pressing buttons 8 and 9. ('xbindkeys -v')

b:8 is linked with 'a' and b:9 is linked to Shift_L
```
Button press !
e.xbutton.button=8
e.xbutton.state=0
"xte 'keydown a'"
    m:0x0 + b:8   (mouse)
got screen 0 for window 13b
Start program with fork+exec call
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaButton release !
e.xbutton.button=8
e.xbutton.state=0
"xte 'keyup a'"
    Release + m:0x0 + b:8   (mouse)
got screen 0 for window 13b
Start program with fork+exec call

Button press !
e.xbutton.button=9
e.xbutton.state=0
"xte 'keydown Shift_L'"
    m:0x0 + b:9   (mouse)
got screen 0 for window 13b
Start program with fork+exec call
Button release !
e.xbutton.button=9
e.xbutton.state=1
```

The release of button 9 is noticed, but somehow the command is not executed.

...
Hmm, wait I've an idea...;)


Yes, this is the problem!
It seems that xbindkeys doesn't run commands, while Shift- or Control-key is pressed. :(


Now there's only on question left:
Is this a bug, or a feature?:lolflag:

---

### Post by rubo77 on 2008-11-08
i put it all together and created a bash script to install and configure your logitech revolution MX. just copy and paste it to your console:
```
sudo apt-get install xbindkeys xmacro
mv ~/.xbindkeysrc ~/.xbindkeysrc.old
echo "# Mappings for keys for MX Revo
# b:1	-	left mouse button
# b:2	-	left and right mouse button together
# b:3 	-	right mouse button
# b:4	-	mouse wheel up
# b:5	-	mouse wheel down
# b:6	-	mouse wheel left
# b:7	-	mouse wheel right
# b:8	-	back button
# b:9	-	forward button
# b:10	-	-none-
# b:11	-	-none-
# b:12	-	-none-
# b:13	-	media wheel up
# b:14	-	-none-
# b:15	-	media wheel down
# b:16	-	-none-
# b:17	-	media wheel press">>~/.xbindkeysrc
#do this to check your own mouse: (see http://ubuntuforums.org/showthread.php?t=968530)
#echo '"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0"'>>~/.xbindkeysrc
#echo 'b:1'>>~/.xbindkeysrc
#kate &
#xbindkeys -n -v

echo "
# Mapping enter key to mousewheel right
# i disabled that cause i want to use it as browser forward (see below)
#\"echo 'KeyStrPress Return KeyStrRelease Return' | xmacroplay :0\"
#b:7">>~/.xbindkeysrc

echo "
# Mappings for media wheel
\"echo 'KeyStrPress XF86AudioNext KeyStrRelease XF86AudioNext' | xmacroplay :0\"
b:13
\"echo 'KeyStrPress XF86AudioPrev KeyStrRelease XF86AudioPrev' | xmacroplay :0\"
b:15
\"echo 'KeyStrPress XF86AudioPlay KeyStrRelease XF86AudioPlay\' | xmacroplay :0\"
b:17">>~/.xbindkeysrc

echo "
# Mapping for Search button as 'left and right mouse button together'
\"echo 'ButtonPress 2 ButtonRelease 2' | xmacroplay :0\"
c:0xE1">>~/.xbindkeysrc

echo "
# Mapping for mouse wheel left and mouse wheel right: go to the next/previous page in firefox browser
\"echo 'KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L' | xmacroplay :0\"
b:6
\"echo 'KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right KeyStrRelease Alt_L' | xmacroplay :0\"
b:7">>~/.xbindkeysrc

echo "# Mapping for back button to Ctrl+F9 (which is compiz->show all windows)
\"echo 'KeyStrPress Control_L KeyStrPress F9 KeyStrRelease F9 KeyStrRelease Control_L' | xmacroplay :0\"
b:9
# Mapping for 'forward' buttons to ALT+Tab
\"echo 'KeyStrPress Alt_L KeyStrPress Tab KeyStrRelease Tab KeyStrRelease Alt_L' | xmacroplay :0\"
b:8">>~/.xbindkeysrc

killall xbindkeys
xbindkeys

```

i personally also like to have the enter on my mouse somewhere, so i will replace the media-wheel-press button with "Enter":
```

# Mapping enter key to b:17-media wheel press
"echo 'KeyStrPress Return KeyStrRelease Return' | xmacroplay :0"
b:17

```

---

### Post by Capa Pinbacker on 2008-11-11
Side note: one thing I like to do is to turn the scroll button of my Logitech mouse into a double click.  btnx worked great at the time.

This post was a great help "Linux: Make Your Scroll Wheel Double Click":
[http://robwilkerson.org/2008/08/20/linux-make-your-scroll-wheel-double-click/](http://robwilkerson.org/2008/08/20/linux-make-your-scroll-wheel-double-click/)

However, I had to use the following in the .xbindkeysrc file to make it work under Ubuntu 8.10:
"/usr/bin/xte 'mouseclick 1' 'mouseclick 1' &"
 b:2 + Release

---

### Post by rubo77 on 2008-11-13
> **cecilx22 said:**
> 
**2) Go through the (painful) button discovery process.  To do this:**

**a)** edit the configuration file for xbindkeys

gedit ~/.xbindkeysrc

delete the full contents of this file and add the following lines:

```

"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0"
b:1
```

This will echo a very simple macro to the macro player which will direct the results of said macro to the default X display.  In this case, it will generate a press of the 'enter' key.

**b)** launch a text editor window.  We will use this to see the results of the macro running

**c)** run the following command in the terminal window:

```
xbindkeys -n -v
```

Note: This will likely prevent the normal functioning of whatever button you are looking for.

**d)** select the text editor and start pressing mouse buttons until you get an 'enter' that will be button b:1 for your mouse.  Once you find the button, reselect the terminal and Ctrl+C the process to stop it.

Repeat the whole process for different b:#'s (i.e. b:2).  Make sure to note what button codes correspond to which buttons.  Also, try multi button presses if no single button generates an event. 


i wrote a loop script, that does the work of opening and editing the .xbindkeyssrc file all the time:
```
echo
mv ~/.xbindkeysrc ~/.xbindkeysrc_bak
echo "
\"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0; killall xbindkeys \"
b:1">~/.xbindkeysrc
echo
echo press all buttons until you get output then you have the 1. Button \(look for 'e.xbutton.button' \)
echo if you cannot generate output, then your mouse doesent have the left mouse button as 1. Button, then press ^C to abrt this script \(and
echo edit it to your needs\)
echo
xbindkeys -n -v

echo

for i in  2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17; do


echo
echo
mv ~/.xbindkeysrc ~/.xbindkeysrc_bak
echo "
\"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0; killall xbindkeys \"
b:$i
\"echo 'KeyStrPress Enter KeyStrRelease Enter' | xmacroplay :0; killall xbindkeys; echo 'Button $i skipped' \"
b:1">~/.xbindkeysrc
echo
echo press all buttons until you get output then you have the $i. Button \(look for 'e.xbutton.button' \)
echo if you cannot generate output, then your mouse doesent have a $i. Button, then press the first Button again
echo
xbindkeys -n -v
echo

done
mv ~/.xbindkeysrc_bak ~/.xbindkeysrc


```

---

### Post by theApokalypsis on 2008-11-17
> **cecilx22 said:**
> I should point out that most compiz plugins support mapping to mouse buttons directly.  You might try binding these in compiz to button6 and button7 (might be different than the b:# codes, I'm not sure).  Using this directly rather than mapping this to keys, and keys to action, might work better.

Ah! so indeed running the new kernel that comes with 8.10 it seems the MX revo buttons are all registered from the get go and seems to be in the same order. Compiz manager (ccsm) only has buttons 1 - 9 by default to pick from, but use the edit button to change to for example Button13 (media wheel up) and voila it works with no delay. I can't believe I didnt even notice! :mad: 

:guitar:

---

### Post by danx on 2008-11-26
Has anyone had any success binding shift/ctrl to the mouse yet?  Tried this but it doesn't work.

```
"echo 'KeyStrPress Control_L' | xmacroplay :0"
  m:0x0 + b:8

"echo 'KeyStrRelease Control_L' | xmacroplay :0"
  m:0x0 + b:8 + release
```

When xbindkeys is killed everything behaves as if the control key were permanently held down but the output from xbindkeys/xmacroplay says Control_L is not a recognised tag (xmacrorec :0 suggests otherwise).  This is the output from xbindkeys -n -v:

```
2 keys in /home/danx/.xbindkeysrc                                      

min_keycode=8     max_keycode=255 (ie: know keycodes)
"echo 'KeyStrPress Control_L' | xmacroplay :0"       
    m:0x0 + b:8   (mouse)                            
"echo 'KeyStrRelease Control_L' | xmacroplay :0"     
    Release + m:0x0 + b:8   (mouse)                  
starting loop...                                     
Button press !                                       
e.xbutton.button=8                                   
e.xbutton.state=0                                    
"echo 'KeyStrPress Control_L' | xmacroplay :0"       
    m:0x0 + b:8   (mouse)                            
got screen 0 for window 8b                           
Start program with fork+exec call                    
Catch CHLD signal -> pid 8829 terminated             
XTest for server ":0.0" is version 2.2.              

KeyStrPress: Control_L
Unknown tag: Control_L
xmacroplay: pointer and keyboard released. 
Button release !                           
e.xbutton.button=8                         
e.xbutton.state=4
```

Any ideas?  Alternatives?  I can't hold down shift + key or use a mouse with the left hand due to injury and really miss having control and shift on the side buttons.


Cheers,
Danx

---

### Post by Digitm on 2008-11-30
This might seem like a stupid question but does anyone know if there is any difference using:

KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L

vs.

KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Alt_L KeyStrRelease Left 

I only ask because is use ctr + w to close tabs in firefox and it only work like half the time. I'm wondering if it has anything to do with the order of the last two. I Would test this instead of asking but I'm not home at the moment.

---

### Post by Krace on 2008-12-03
Well I installed the xbindkeys and got every thing set up. All i really want to do is make b:17(media wheel push) open links in a new tab in FF. What line do i need to add to .xbindkeysrc make this possible?

---

### Post by Krace on 2008-12-03
Anyone? I tried using this but it don't seem to work. I know that if you hit right and left mouse buttons it will open the link in a new tab. or if you hit Ctrl + left mouse will also open it . I just don't know how to wright it in the code to get it to work :( 

 This is what is in my .xbindkeysrc, am I missing something? 
```

# Mapping enter key to mousewheel right
"echo 'KeyStrPress Return KeyStrRelease Return' | xmacroplay :0"
b:7

# Mappings for media wheel
"echo 'KeyStrPress XF86AudioNext KeyStrRelease XF86AudioNext' | xmacroplay :0"
b:13
"echo 'KeyStrPress XF86AudioPrev KeyStrRelease XF86AudioPrev' | xmacroplay :0"
b:15
"echo 'ButtonPress 2 ButtonRelease 2' | xmacroplay :0"
b:17

```
FYI this is for my MX Rev.

---

### Post by Krace on 2008-12-05
Follow Up:
 Well I got it to work the way I wanted it to work I used xmodmap to change the buttons around, moving button 2 to 17 and 17 to 2 and run that code in sessions. To make the thumb button push to work like a 3rd mouse button. 

```
xmodmap -e "pointer = 1 17 3 4 5 6 7 8 9 10 11 12 13 14 15 16 2"
```
Yay! Now I can browse Fire Fox the way I wanted!

---

### Post by chris_j on 2008-12-23
First... Does xbindkeys work on hardy 64x?
second... first i've tried btnx but that did'nt work.  After
that i took this tut. because it works perfectly on my intrepid.
Now on hardy everything works normal with the search for the b:'s until i reach to the b:6 and b:7. These are the keys i need. It's the function on the scroll weel for clicking left and right.  I get an error in the terminal screen??  From b:1 to b:5 there is no error?

[IMG]http://i3.photobucket.com/albums/y69/lycans/Schermafdruk-8-1.png[/IMG]

---

### Post by chris_j on 2008-12-25
bump

---

### Post by oni5115 on 2009-01-03
Are you absolutely sure it is 6 and 7?  On my MX1000 there is no 6 and 7 - at least not that I can determine.

Try using xev in a command line.  It will bring up a little window.  Move the mouse into the window, press your buttons and watch the stream of info it puts into the terminal.

It should say Button X whenever you press/release a button.  It also tells you keyboard info as well.  Such as keycode # and command like Control_L, so it's very easy to use for making these macros and things.

Has anyone had any luck simply making one button act as another? (Particularly speaking of mouse buttons as Ctrl/Alt buttons.)  I like using them while playing video games.  Without that it'll be much harder.

On a side note, with Intrepid I was able to remove the old xmodmap file I had and have absolutely nothing special in my xorg.conf and BOOM.  Everything worked as per a normal MX1000, except for the app switcher button.  On the other hand, BTNX is broken, and I don't know how to do the shift/alt thing without it.  :(

---

### Post by tpe11etier on 2009-01-07
> **oni5115 said:**
> Are you absolutely sure it is 6 and 7?  On my MX1000 there is no 6 and 7 - at least not that I can determine.

Try using xev in a command line.  It will bring up a little window.  Move the mouse into the window, press your buttons and watch the stream of info it puts into the terminal.

It should say Button X whenever you press/release a button.  It also tells you keyboard info as well.  Such as keycode # and command like Control_L, so it's very easy to use for making these macros and things.

Has anyone had any luck simply making one button act as another? (Particularly speaking of mouse buttons as Ctrl/Alt buttons.)  I like using them while playing video games.  Without that it'll be much harder.

On a side note, with Intrepid I was able to remove the old xmodmap file I had and have absolutely nothing special in my xorg.conf and BOOM.  Everything worked as per a normal MX1000, except for the app switcher button.  On the other hand, BTNX is broken, and I don't know how to do the shift/alt thing without it.  :(


Hi,

Not sure if this helps, but everytime my G5 stops working WoW becomes WAY harder to play.  I managed to get everything working by having the following in my config file.

```

#Left Middle Button
"echo 'KeyStrPress Alt_L KeyStrPress F8 KeyStrRelease F8 KeyStrRelease Alt_L' | xmacroplay :0"
b:6
#Right Middle Button
"echo 'KeyStrPress Alt_L KeyStrPress F9 KeyStrRelease F9 KeyStrRelease Alt_L' | xmacroplay :0"
b:7
#Back
"echo 'KeyStrPress Alt_L KeyStrPress F10 KeyStrRelease F10 KeyStrRelease Alt_L' | xmacroplay :0"
b:8
#Forward
"echo 'KeyStrPress Alt_L KeyStrPress F11 KeyStrRelease F11 KeyStrRelease Alt_L' | xmacroplay :0"
b:9


```

---

### Post by Joe Momma on 2009-01-09
I think I remapped the keys, but nothing happens when I press them.

My .xbindkeysrs looks like this:

```
# 1 left click
# 2 wheel press
# 3 right click
# 4 wheel up
# 5 wheel down
# 6
# 7
# 8 back
# 9 forward
# 10 search button
# 11 wheel left
# 12 wheel right
# 13 thumb wheel forward
# 14
# 15 thumb wheel backward
# 16
# 17 thumb wheel press

# Map thumb wheel to desktop swap
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:13
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:15

# Mapping for Search button as middle click
"echo 'ButtonPress 2 ButtonRelease 2' | xmacroplay :0"
b:10

```

If I do an 'xbindkeys -v', I get

```
KeyStrPress: Control_L
KeyStrPress: Alt_L
KeyStrPress: Left
KeyStrRelease: Left
KeyStrRelease: Alt_L
KeyStrRelease: Control_L
Unknown tag: Control_L
xmacroplay: pointer and keyboard released.
Button release !
e.xbutton.button=15
e.xbutton.state=16
```

but if I just do an xbindkeys, nothing happens when I hit the button, can someone offer some advice?

---

### Post by Nitrius on 2009-01-10
Worked flawlessly for me, thanks :D

Can't guarantee it, but if you got a Logitech G9, and are looking for a way to get your thumb back and forward buttons to work in nautilus, this may work:
In terminal type:
```

gedit ~/.xbindkeysrc

```

And in the xbindkeysrc file add this:
```
# Thumb buttons back and forward
"echo 'KeyStrPress Alt_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L' | xmacroplay :0"
b:8
"echo 'KeyStrPress Alt_L KeyStrPress Right KeyStrRelease Right KeyStrRelease Alt_L' | xmacroplay :0"
b:9
```

And of course remember to start xbindkeys with you session, according to how it's described in the first post.

---

### Post by silentknyght on 2009-01-20
I do appreciate the effort done here to get this mouse to work in linux, but really, isn't there an easier way?


I'm willing to purchase a linux-friendly mouse as a solution if it's possible.  Are there any out-of-the-box Ubuntu 8.10 -compatible mice with 6-8 usable buttons?

---

### Post by Songwind on 2009-03-04
Thanks for this tutorial.  It really made my life easier today.

---

### Post by Malacki on 2009-03-25
So I'm a bit of a noob here, and I've been trying to get this config stuff to work for my Logitech G7.  I want the mouse wheel left to be F11 and the mouse wheel right to be F12.  I can't seem to get modifying any of the things suggested here to work.  Any help?

---

### Post by cecilx22 on 2009-03-25
Can you please post the content of the config files you've created?  Thanks!

---

### Post by Malacki on 2009-03-26
I will when I get home from work this evening.  Unless I just decide to whipe the PC and start a new install.  I think I somehow broke WINE last night.

---

### Post by t.rei on 2009-04-03
Ok, now since I am totally lost in Jaunty without any clue where my event are hiding:

this is my mouse according to 'lspci':
Bus 006 Device 005: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse

/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse
exists.

The mouse does work. 'revoco' reports battery status and click status and can appoint the toggle to ANY mouse button.

But in X no event show up for anything but b1, b2 and wheel.

I tried so many xorg.conf settings I really shouldn't post here. 

If you have this mouse working on jaunty, *please* post.

---

### Post by MrKlister on 2009-04-08
> **danx said:**
> Has anyone had any success binding shift/ctrl to the mouse yet?  Tried this but it doesn't work.

```
"echo 'KeyStrPress Control_L' | xmacroplay :0"
  m:0x0 + b:8

"echo 'KeyStrRelease Control_L' | xmacroplay :0"
  m:0x0 + b:8 + release
```

...
...
...

Any ideas?  Alternatives?  I can't hold down shift + key or use a mouse with the left hand due to injury and really miss having control and shift on the side buttons.


Cheers,
Danx


Been having the same problem and searching for a solution for it for a while. Now I finally understand! It's pretty simple actually.

When you are waiting for the mouse button release event you are waiting for a mouse release event without Control being pushed at the same time.
Since you just recently pushed the Control key down with xbindkey when pressing the button down the event you are waiting for will never show up and the Control key will stay as pushed down.

So the problem is that the modifier m:0x0 should be m:0x1 (or just with the string "Shift" a prettier way to present it)

Try this instead:
```
"echo 'KeyStrPress Control_L' | xmacroplay :0"
  b:8

"echo 'KeyStrRelease Control_L' | xmacroplay :0"
  Shift + b:8 + Release
```

---

### Post by nanogordo on 2009-05-17
I have been having a small issue getting xbindkeys to capture the mouse actions: when I start xbindkeys (using xbindkeys -n), I receive the following message:

[FONT="Fixedsys"]
Please verify that there is not another program running
which captures one of the keys captured by xbindkeys.
It seems that there is a conflict, and xbindkeys can't
grab all the keys defined in its configuration file.[/FONT]


Any ideas for what is stepping in between xbindkeys and my mouse? Thanks in advance for any insights!

---

### Post by SnappyU on 2009-12-07
Am trying to configure my mousewheel up/down scrolling to send out more scrolls than the default.

Tried sending up and down keys, but it is different from mouse scrolls.  Mouse scrolls do not move the cursors, whereas up/down keys does.

Any ideas how to emulate multiple mouse scrolls with xmacroplay?  Many thanks!

---

### Post by cecilx22 on 2009-12-07
> **nanogordo said:**
> I have been having a small issue getting xbindkeys to capture the mouse actions: when I start xbindkeys (using xbindkeys -n), I receive the following message:

[FONT="Fixedsys"]
Please verify that there is not another program running
which captures one of the keys captured by xbindkeys.
It seems that there is a conflict, and xbindkeys can't
grab all the keys defined in its configuration file.[/FONT]


Any ideas for what is stepping in between xbindkeys and my mouse? Thanks in advance for any insights!


don't know how this reply slipped though my email.  Sorry!! I have no idea what that might be.  There are so many variables involved here...

I might suggest booting off the liveCD, following the above steps, and seeing if it works.  At least then you'll know it's something you've installed after the inital install.

---

### Post by cecilx22 on 2009-12-07
> **SnappyU said:**
> Am trying to configure my mousewheel up/down scrolling to send out more scrolls than the default.

Tried sending up and down keys, but it is different from mouse scrolls.  Mouse scrolls do not move the cursors, whereas up/down keys does.

Any ideas how to emulate multiple mouse scrolls with xmacroplay?  Many thanks!

That's a really good question.  I'm not 100% sure this will work but...

I just used xev and twirled my wheel (man, that sounds like a euphemism) and got the following output (along with LOTS MORE)

```
ButtonPress event, serial 36, synthetic NO, window 0x5c00001,
    root 0xcd, subw 0x0, time 86353503, (87,152), root:(92,177),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5c00001,
    root 0xcd, subw 0x0, time 86353503, (87,152), root:(92,177),
    state 0x1000, button 5, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5c00001,
    root 0xcd, subw 0x0, time 86354847, (87,152), root:(92,177),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5c00001,
    root 0xcd, subw 0x0, time 86354847, (87,152), root:(92,177),
    state 0x800, button 4, same_screen YES

```

So it looks like, on my system, buttons 4 and 5 are the mouse wheel up and down.  A single 'click' of the wheel is a press event followed by a release event.  So to make xbindkeys create multiple 'clicks' for each click, just make a nice long macro!

Hope this works for you!

---

