---
title: "Logitech G7 Compatibility"
date: 2006-01-05
forum: General Help
---

### Post by pianoboy3333 on 2006-01-05
I am buying the Logitech G7 for gaming and such as a birthday present, yet I also plan on installing Ubuntu and I was wondering about the G7's compatablility with Ubuntu. Will I be able to get it to work well?

---

### Post by pianoboy3333 on 2006-01-05
Will I be able to get the side and sensitivity buttons working? Can someone point me to a help page?

---

### Post by RichJacot on 2006-08-06
Hello,  Did you ever get an answer on this?  I just bought one tonight.

---

### Post by D3ATH ROW3 on 2007-08-29
Sensitivity buttons work for me without any configuration. They should always work as I believe they actually adjust the sensitivity on board, not through the driver.

I know you can configure the other button to work, as I have seen others post about it. I have not configured mine yet simply because I am still a novice user and have been trying to get more important issues resolved first.

---

### Post by forsberg on 2007-09-15
the sensitivity buttons and the back button work for me without doing anything

tilt buttons do not do anything ( but i dunno what tilt buttons r used for anyways)

---

### Post by Lex_x64 on 2007-09-19
I beleive I stumbled upon a different thread in the fourms you may wish to [check out]("http://ubuntuforums.org/showthread.php?t=3828&highlight=logitech+buttons"). I'm about to reload so I'll be able to edit and let you know if I got it working yet.

EDIT: It took some time messing around to get everything working (and a ton of reading) but I now have the thumb button as back! To save you some time, here is what exctally I did for the G7 in 7.04.

Open your terminal:
```

sudo gedit /etc/X11/xorg.conf 
```
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" 		"/dev/input/mice"
    Option         "Protocol" 		"ExplorerPS/2"
    Option	   "Buttons"		"7"
    Option         "ZAxisMapping" 	"6 7"
    Option	   "Resolution"		"2000"
EndSection
```

Then:
```
sudo apt get install imwheel

sudo gedit /etc/X11/imwheelrc
```

Put the text:
```

".*"
None,Up,Alt_L|Left
None,Down,Alt_L|Right
```
in and save the file.

Run:  ```
 sudo gedit /etc/X11/Xsession.d/57xmodmap
```

enter the code:
```

#/bin/bash
xmodmap -e "1 2 3 6 7 4 5" 
```

After saving the file run: 
```
sudo chmod 777 /etc/X11/Xsession.d/57xmodmap
```

Here's where I had to combine input from yet another thread to get a working G7 back thumb button...

```
sudo gedit /etc/X11/imwheel/startup.conf
```

Make sure it looks like this:
```

# Configuration file for setting imwheel startup parameters.

# Set this to "1" to make imwheel start along with your X session.
IMWHEEL_START=1

# Specify the command line parameters to pass to imwheel.
# Simply uncomment the bottom line, and if necessary replace
# the default options with your own. A button spec of "0 0 8 9"
# will grab the thumb buttons of most mice. "0 0 0 0 8 9" should
# work for mice with a scroll wheel with two axes. Keep in mind
# that each button number must be separated by a space.
IMWHEEL_PARAMS='-b "0 0 8 9"'
```

Uncommenting the last line seemed to be the integral part here.

Ensure that you saved everything properly, log out and back in. Hopefully your scroll wheel will still scroll and that thumb button should perform the back command when in Firefox.

Hopefully this is clear enough to follow.

---

### Post by sgood on 2007-09-23
I did what you suggested Lex_x64, now my scroll wheel doesn't work.  it was working fine before.

Any suggestions?

I'm on Feisty x86.

---

### Post by measekite on 2007-09-23
I am working on that right now.  If I find (in about a week) a solution I will post what worked for me.  I know it requires editing a config file. This, from what I read, is an 8 button mouse.  I do not understand why but that is what I red. It seems that the scroll wheel counts for 5 buttons ie up, down, left, right, and spin.  I may be wrong on this so do ot quote me.

---

### Post by battleshipterry on 2007-09-24
I tried this to, and my wheel was working before I did this  and after one log off  it worked but on rebooting pc the wheel quit will not scroll the side bar but will cycle forwards and backwards thought web pages I would like it keyed to side bar not the forwards and backwards.I will work on this and post results but I am a bit rusty at this I would accept suggestions I think my problem is similar to sgoods maybe sgood could browse a few web pages and scroll mouse wheel to see if it is same as mine a post result of course Thanks

---

### Post by battleshipterry on 2007-09-24
Ok I comment out the new config and added the original setting and the wheel scrolls again but no back or wheel buttons the g7 im using has also wheel tilt that is not working.here is my xorg settings.

#Section "InputDevice"
    #Identifier     "Configured Mouse"
    #Driver         "mouse"
    #Option         "CorePointer"
    #Option         "Device" 		"/dev/input/mice"
    #Option         "Protocol" 		"ExplorerPS/2"
    #Option	   "Buttons"		"7"
    #Option         "ZAxisMapping" 	"6 7"
    #Option	   "Resolution"		"2000"
#EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by measekite on 2007-09-28
> **D3ATH ROW3 said:**
> Sensitivity buttons work for me without any configuration. They should always work as I believe they actually adjust the sensitivity on board, not through the driver.

[COLOR=Black] I know you can configure the other button to work, as I have seen others post about it. I have not configured mine yet simply because I am still a novice user and have been trying to get more important issues resolved first.

I have tried over and over and over.  I can at least boot up now but the side button still does not work.  I have tried everything posted and have just about given up.  If you get it to work I would appreciate a post.
[/COLOR]

---

### Post by Lex_x64 on 2007-11-27
Well it took me some time to re-find this post after making the appropriate "fixes".

Using the previous directions I posted ammend the xorg.conf with:

```

    Option         "Buttons" "7"
    Option	   "ButtonMapping 1 2 3 6 7"
    Option         "ZAxisMapping" "4 5" 
```

I realized later that it shouldn't have been "6 7", that was from another Logitech mouse possibly the MX300. Hope this may help if anyone is still looking.

---

