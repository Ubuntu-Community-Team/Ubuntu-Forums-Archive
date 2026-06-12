---
title: "Vostro 2420 function keys not working after ubuntustudio 13.10 install"
date: 2014-01-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by handysmurf on 2014-01-30
laptop had ubuntu 11.10 preinstalled, and failed to advise of LTS update before EOL.

did a fresh install of ubuntu studio 13.10 (xfce), now some (i guess model specific?) function keys won't work.

before doing upgrade, was poking around in \boot,or \etc (or somewhere... don't remember exactly) looking for cause of then current problem, and stumbled on a file that determined what actions to take based on keypress/combination.  at the time, that all seemed to be working, and seemed unimportant, and while interesting, I passed it over without another thought.  I can't help but wonder if a file like that is what I'm now missing?

any help would be greatly appreciated.,

---

### Post by Toz on 2014-01-30
> **handysmurf said:**
> did a fresh install of ubuntunow some (i guess model specific?) function keys won't work.

Which function keys are not working? Which ones are?

---

### Post by handysmurf on 2014-02-01
Hello Toz my friend... one that is not working is (Fn+ F3) it enables/disables the touchpad.  very handy for typing... if enabled, and i accidentally touch it, it moves my cursor to an unwanted area of my sentence/paragraph, causing extra editing.  I don't know any other easy way to temporaraly disable touchpad.

others seem to work mebbie?  some I've not had occasion to use. FF, rewind, play/stop.

---

### Post by Toz on 2014-02-01
> I don't know any other easy way to temporaraly disable touchpad.I believe Ubuntustudio runs Xfce, so try going to Settings Manager -> Mouse and Touchpad. On the "Devices" tab, you should be able to select your touchpad as the Device. Once selected, go to the "Touchpad" tab and enable "Disable touchpad while typing".

> one that is not working is (Fn+ F3) it enables/disables the touchpad. very handy for typing... if enabled, and i accidentally touch it, it moves my cursor to an unwanted area of my sentence/paragraph, causing extra editing. 
If you want to get the Fn+F3 (enable/disable) touchpad key to work:
1. First create a bin directory in your home directory (if one doesn't exist):
```
 mkdir ~/bin
```

2. Create the file toggletouchpad.sh:
```
mousepad ~/bin/toggletouchpad.sh
```

3. Copy/paste the following content:
```
#!/bin/bash
if [ $(synclient -l | grep TouchpadOff | awk '{print $3}') == 1 ] ; then
  synclient touchpadoff=0;
else
 synclient touchpadoff=1;
fi
```

4. Save the file.

5. Make it executable:
```
chmod +x ~/bin/toggletouchpad.sh
```

6. Test it. Run the command:
```
~/bin/toggletouchpad.sh
```
...and it should disable the touchpad. Run it again to enable the touchpad.

7. Go to Settings Manager -> Keyboard -> Application shortcuts and create an Fn+F3 shortcut to point to /home/USER/bin/toggletouchpad.sh (replace USER with your actual username) and test the Fn+F3 combination.

---

### Post by handysmurf on 2014-02-01
when i enter "mousepad ~/bin/toggletouchpad.sh"

response is:
"The program 'mousepad' is currently not installed. You can install it by typing:
sudo apt-get install mousepad"

do i follow through?

---

### Post by Toz on 2014-02-01
> **handysmurf said:**
> when i enter "mousepad ~/bin/toggletouchpad.sh"

response is:
"The program 'mousepad' is currently not installed. You can install it by typing:
sudo apt-get install mousepad"

do i follow through?

Sorry, I thought mousepad was the editor. Try replacing "mousepad" with the name of your editor (is it leafpad? or gedit? or something else?).

---

### Post by handysmurf on 2014-02-01
when i enter "mousepad ~/bin/toggletouchpad.sh"

response is:
"The program 'mousepad' is currently not installed. You can install it by typing:
sudo apt-get install mousepad"

do i follow through?

---

### Post by Toz on 2014-02-01
What text editor do you have installed? Is it leafpad? Or gedit? If so, use that one instead.

Or if you want, follow through and install mousepad, its not a big program.

---

### Post by handysmurf on 2014-02-01
it's gedit,  and once again you have made life much easier for me...

Toz, once more, thank you so much for your time, and advice, laptop works more like I'm used to now, you're a great help!

---

