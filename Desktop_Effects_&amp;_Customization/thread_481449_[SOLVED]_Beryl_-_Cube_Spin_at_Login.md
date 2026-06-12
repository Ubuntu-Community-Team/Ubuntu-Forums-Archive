---
title: "[SOLVED] Beryl - Cube Spin at Login?"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by mtn on 2007-06-22
Just wondering, using Beryl can the cube desktop be made to automatically spin during, or just after, login?

---

### Post by Ultra Magnus on 2007-06-22
Spinning at login!! Well there was a thread a couple of days ago with somone wanting to be able to automatically switch workspaces - apparently there is a script to be able to do it, you can find the thread here: [http://ubuntuforums.org/showthread.php?t=479657](http://ubuntuforums.org/showthread.php?t=479657)
I don;t know whether it will work with beryl but you can give it a go - I suppose you could alter it to just spin a few times and then stop or something. Anyway hope that helps!

---

### Post by mtn on 2007-12-06
Thanks Ultra Magnus (I have finally com back to this). The script works if Compiz-Fusion if OFF, but not when on - unfortunately it is the spinning cube I want, not just to change desktops. Thanks anyway tho, well worth a try - good script to save for later!

---

### Post by jsully1 on 2007-12-06
This may help get you started - it uses a macro along with compiz keybindings (control alt right is the default rotate combination)

1. First I installed xmacro (sudo apt-get install xmacro)

2. create a file called rotate.macro (sudo nano rotate.macro)

Here is the contents:
```
Delay 5
KeyStrRelease Right
KeyStrPress Control_L
KeyStrPress Alt_L
KeyStrPress Right
KeyStrRelease Control_L
KeyStrRelease Alt_L
KeyStrRelease Right
KeyStrPress Control_L
KeyStrPress Alt_L
KeyStrPress Right
KeyStrRelease Control_L
KeyStrRelease Alt_L
KeyStrRelease Right

```

Save and close.  What this does is wait 5 seconds, then press control+alt+right, then release the keys, then it does it - four times total.

Test the script by going to the command line and doing this: 
```
cat rotate.macro | xmacroplay -d 100 :0
```
This tells it to run on display 0 with a delay of 100ms.

If you want to learn other commands just type xmacrorec2 and start hitting keys, it gives you the output right there.

Then create a file called rotate.sh - contents:
```
cat rotate.macro | xmacroplay -d 100 :0
```
Add this script to your startup session under System > Preferences > Session

You may have to play with the initial delay - everything has to be loaded before the script executes, otherwise Compiz won't be running and listening for the hotkeys.

---

### Post by mtn on 2007-12-06
EDIT: Ok, I missed a step - just going to try that now - sorry.

IT WORKED! AMAZING, THAT IS SO COOL - THANKS FOR THIS.
(I had missed the bit about creating the .sh, I did that and added saved both file in my home folder and added ./rotate.sh to the start up programs.)

Amazing, that works from the command line :) . How do you know stuff like this!!! I had a quick look at the xmacro site - interesting stuff.

I upped the delay to 10 in the script and added ```
cat rotate.macro | xmacroplay -d 100 :0
``` System>Preferences>Sessions>Start up Programs but no joy. I also tried  ```
cat /home/myhome/rotate.macro | xmacroplay -d 100 :0
```, /home/myhome/rotate.macro is where the script is. After each change I tried logging out and in again.

Ages ago I added a script to some fill that runs at log in - I can't remember for the life of me whatthe  file it was now.I normally make a note of these kind of things for future ref. I wanted to default Firefox for a guest user account, at every log in to pre-configured settings. The script deleted .mozilla and replaced it with a pre-configured .mozilla folder stored in root's home, when the guest user logged in. 

Anyway, sorry to ramble on. Any ideas about getting this to spin just after log in?

Thanks so much so far :)

---

### Post by jsully1 on 2007-12-07
Ok, your first step should be to make a script file that you can execute that will rotate the cube successfully - have you gotten that far, where you can call the script and it will rotate?

---

