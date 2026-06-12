---
title: "Jkeys - simple joystick to keyboard mapping"
date: 2008-08-28
forum: Gaming &amp; Leisure
---

### Post by KillerKiwi on 2008-08-28
Ok here's a little app I setup so I could use my mythbox with a gamepad and some games

A lot of linux games dont have joystick support so this little app will map you joystick buttons/axis to key presses

you run a game by going
```
jkeys example-config.joy armagetronad
```

where example-config.joy is a simple xml file with the key mappings like so
```
<config>
    <joystick id="0">
        <axis number="0" low="Left" high="Right" />
        <axis number="1" low="Down" high="Up" />
        <button number="0" key="Space" />
        <button number="1" key="Return" />
        <button number="2" key="a" />
        <button number="3" key="b" />
        <button number="4" key="c" />
        <button number="5" key="d" />
        <button number="6" key="z" />
        <button number="7" key="x" />
        <button number="9" key="Escape" />
        <button number="10" key="p" />
    </joystick>
</config>
```

It should allow for multi axis any number of buttons and mutliple joysticks etc, although its only been tested with my gamepad ;)

I pushed this into a google project if any one is interested in helping out, or just trying it [http://code.google.com/p/jkeys/](http://code.google.com/p/jkeys/) 

```

sudo apt-get install python-xlib python-pygame svn
mkdir ~/jkeys
cd ~/jkeys
svn checkout http://jkeys.googlecode.com/svn/trunk/ jkeys-read-only  
```

---

### Post by Ape3000 on 2008-09-07
Thanks to you I could play _[JamLegend]("http://www.jamlegend.com/")_ with my dance pad :D

I downloaded the Jkeys from SVN and installed **python-xlib** and **python-pygame**. Then I made a copy of the **example-config.joy** and edited it to look like this:
```
<config>
    <joystick id="0">
        <button number="2" key="Return" />
        <button number="0" key="1" />
        <button number="4" key="2" />
        <button number="1" key="3" />
        <button number="5" key="4" />
        <button number="3" key="5" />
    </joystick>
</config>
```

Then can just ran **./jkeys jam-config.joy firefox** and navigate to the JamLegend site and start a game. It's very playable with a dance pad, but a lot more difficult than with a keyboard.

---

### Post by KillerKiwi on 2008-09-07
Awesome i'm glad it worked for you.. I should add a readme about the deps I guess...

I'm playing with adding mouse support now... it done by adding some key codes
Mouse_Up, Mouse_Down.... Mouse_Click1 (left mouse button), Mouse_Click3 (right mouse button) etc

Using a dance pad as a mouse would be interesting ... lol

---

### Post by diehardlinux on 2008-11-26
I like this program however I am experiencing one slight problem: This program requires a application name to open So i give it a path name ; /home/user/Desktop/et and it runs the program. Say if i have a bash script running a program that requires additional commands prior to running, I experience a script failure. 
bash script example:

#!/bin/bash
#this command will kill all artsd applications prior to running et, this is command needed for sound to work correctly.
killall -9 artsd
#note this is the directory which i have the game file at
cd /usr/share/games/enemy-territory
#et being the application name
./et

Although this is a small speed bump, the program looks lightweight and promising. thanks for this program contribution.

---

### Post by jonobo on 2008-12-31
> **KillerKiwi said:**
> 
I'm playing with adding mouse support now... it done by adding some key codes
Mouse_Up, Mouse_Down.... Mouse_Click1 (left mouse button), Mouse_Click3 (right mouse button) etc

Using a dance pad as a mouse would be interesting ... lol

Hi ;)

I try to use my DancePad as a mouse too - did your playing around come to a usable result and/or can you explain me how to do it?

I tried with js2mouse from [http://cedric.vincent.perso.free.fr/Projets/](http://cedric.vincent.perso.free.fr/Projets/) but with a dancepad that works only for the buttons, because the x/y-navigation is done through the Joystick-Axis-Movement which the Dancepad is missing if i see that right.

So is there a way to use my USB-DancePad as a mouse, and if yes how do i get it running ;?

;j

Update:
Okay - it worked - i adapted the config-file and saved it as dancepad-as-mouse.joy - it looks like this:
```

<config>
    <joystick id="0">
        <button number="0" key="Mouse_Left" />
        <button number="1" key="Mouse_Down" />
        <button number="2" key="Mouse_Up" />
        <button number="3" key="Mouse_Right" />
        <button number="8" key="mouse_click1" />
        <button number="9" key="mouse_click3" />
    </joystick>
</config>

```
Then i did a testrun like this:
```

jkeys dancepad-as-mouse.joy audacity

```
And it worked ;)

To find out the Button-Numbers of your dancepad install the Joystick-Calibrator, run it, bounce around on your DancePad and write down the Numbers:
```

sudo apt-get install jscalibrator
jscalibrator

```

Is there a way to assign "diagonal" movement to a Button?
Like key="Mouse_Up_Left" or something like that?

Congratulations!
Neat little Program.
Seems way easier to use to me than js2mouse.

Happy New Year!

---

### Post by grossaffe on 2009-01-01
jscalibrater is full of fail.  Installing it will cause joystick-related headaches.  I believe jstest and jscal are the good ones.

---

### Post by garybrlow on 2009-06-08
anyone made this work with stepmania?

---

### Post by thejambi on 2010-03-23
Thank you very much for this. I bought a real cheap usb controller and this jkeys did the trick! jscal, etc didn't quite get the job done. Jkeys wins.

---

### Post by skolnick on 2010-04-11
I tried installing this on Fedora 12 x64. I installed python-xlib and pygame (there is no python-pygame in fedora). Then I run it but I get this:

```
[gpulido@hal9000 jkeys-read-only]$ ./jkeys fakenes.joy fakenes
Joystick mappings found : 
 - axis 7 direction low mapped to key Up
 - axis 7 direction high mapped to key Down
 - axis 6 direction low mapped to key Left
 - axis 6 direction high mapped to key Right
 - button 1 mapped to key d
 - button 0 mapped to key s
 - button 10 mapped to key Space
 - button 6 mapped to key Return
Starting application
['fakenes']
Fatal Python error: (pygame parachute) Segmentation Fault
Aborted (core dumped)
[gpulido@hal9000 jkeys-read-only]$
```

The segmentation fault happens about a second after I press anything on the gamepad. Any ideas? could it be because my linux is 64 bits?

Thanks!

---

### Post by skolnick on 2010-04-11
I just found kbstick: [http://www.ditch.org/kbstick/](http://www.ditch.org/kbstick/) . It's a pretty old program (2003) but it does exactly what I need. It doesn't support mouse (AFAIK) and it needs some tweaks to compile (some includes are missing) but it works really well.

Regards.

---

### Post by sk3jt on 2010-05-15
Hi all
I am new to the Linux community but I want to stay. 
I have tried but I do not understand and need a step-by-step instruction how to get my game-pad (Logitech DualAction) to map a few keys from the keyboard. 

I want to control my boxee and/or play SNES emulated games.

How do I do that with Jkeys?

Please help!

I have tried with jojsticken-0.0.5 to no success.

Kind regards,
Matt

---

### Post by Rimus on 2010-05-29
> **sk3jt said:**
> Hi all
I am new to the Linux community but I want to stay. 
I have tried but I do not understand and need a step-by-step instruction how to get my game-pad (Logitech DualAction) to map a few keys from the keyboard. 

I want to control my boxee and/or play SNES emulated games.

How do I do that with Jkeys?

Please help!

I have tried with jojsticken-0.0.5 to no success.

Kind regards,
Matt

I tried to get my Rock Band 1 Xbox 360 guitar controller working with JamLegend, only to find out that JamLegend's Flash is too sloppy on my Ubuntu. I can't even play it with keyboard :( Anyway, here's my guide:

1) Install 'joystick' either via Ubuntu Software Center or
```
sudo apt-get install joystick
```2) plug in the controller, go to terminal and write:
```
jstest --normal /dev/input/js0
```3) push the buttons of the controller to see what input they give
4) write the config.joy file as described in the first post, now replacing the button numbers and keys however you want to map them. My jam-config.joy with the guitar controller was:

```
<config>
    <joystick id="0">
        <button number="0" key="1" />
        <button number="1" key="2" />
        <button number="2" key="4" />
        <button number="3" key="3" />
        <button number="4" key="5" />
        <button number="10" key="Return" />
    </joystick>
</config>
```If you have axis in your controller, write
```
<axis number="x" low="key here" high="key here" />
```I couldn't get the strum bar (axis 7) to work (keys stopped working every time I strummed), so I mapped the Back key (number 10) to do the strumming.

5) Just run in jkeys folder:

```
./jkeys config.joy game-here
```

---

### Post by jony121 on 2011-03-12
Excellent work here. This runs just the way I wanted. The only other thing I found was [http://maketecheasier.com/qjoypad-keyboard-to-gamepad-mapping-for-linux/2010/05/03](http://maketecheasier.com/qjoypad-keyboard-to-gamepad-mapping-for-linux/2010/05/03) Qjoypad. But with that you have to use a systray icon to switch between profiles instead of running a profile at the program execution (like yours).

Some things that might be nice to work on would be overlapping instances of jkeys and a graphical tool for creating profiles.

I was worried I might have to create this myself. If I find the time I will see if I can contribute to your google code project.

Thanks.

---

