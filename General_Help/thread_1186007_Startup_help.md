---
title: "Startup help"
date: 2009-06-12
forum: General Help
---

### Post by Crunchy the Headcrab on 2009-06-12
Hey all.  Using Ubuntu 9.04 on an Asus laptop.  The laptop has a lightup touchpad that is really annoying.  There is a command to get it to turn off.

sudo sh -c "echo 0 > /sys/class/leds/asus\:\:touchpad/brightness" 
I was wondering if there was a way to make it so that this command is run at startup so that I don't have to use it every time I want to turn the light off (the light turns on every time the pc is restarted).

I would also like it if users who aren't administrators could log in from a fresh boot without the lights on.  Not sure if this is possible, but it doesn't seem unreasonable.

Please excuse my newbishness.

---

### Post by briguy47 on 2009-06-14
> **Crunchy the Headcrab said:**
> Hey all.  Using Ubuntu 9.04 on an Asus laptop.  The laptop has a lightup touchpad that is really annoying.  There is a command to get it to turn off.

sudo sh -c "echo 0 > /sys/class/leds/asus\:\:touchpad/brightness" 
I was wondering if there was a way to make it so that this command is run at startup so that I don't have to use it every time I want to turn the light off (the light turns on every time the pc is restarted).

I would also like it if users who aren't administrators could log in from a fresh boot without the lights on.  Not sure if this is possible, but it doesn't seem unreasonable.

Please excuse my newbishness.


Howdy.  Here is the solution.   This will cause your command to run at bootup everytime.  It will also run regardless of who is logging in, so it should take care of your users who aren't admins.  :D

1.  Open your favorite terminal.


2.  Type the following command to create the necessary script in your init.d directory:

```
sudo echo 'sh -c "echo 0 > /sys/class/leds/asus\:\:touchpad/brightness"' > /etc/init.d/leds 
```3.  Update rc.d with:

```
sudo update-rc.d /etc/init.d/leds defaults
```4. Reboot and you should be good to go.

Let me know if you have any questions!  :D

---

### Post by Crunchy the Headcrab on 2009-06-14
Hey thanks for the info.  I learned that writing the info to /etc/local.rc fixes the issue. 

Is there any benefit to writing to writing to init.d?  I checked and there is no leds file, so does that command create one or would I have to touch one first?

I hope you don't mind me continuing to ask these questions, but I'm interested in learning as much as possible.  Thanks again for your reply. ;)

---

### Post by briguy47 on 2009-06-14
No worries about the questions.  It is MUCH better to ask and understand, than to ask how to fix a mistake. lol

So far as I can tell, there shouldn't be much difference to either approach.  The only significance is that your way will ensure that the script is run at the END of the boot process (which is probably best), where as using my way can give you control over where in the boot process the script runs. Your way is also probably a lot more User-Friendly and therefore most likely safer in some way. lol

Oh, and yah, my command would have created the leds file.  I just picked that name because that is how I used the command before, to manipulate leds.

---

