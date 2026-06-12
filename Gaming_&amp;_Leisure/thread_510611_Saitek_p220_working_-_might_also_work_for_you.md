---
title: "Saitek p220 working - might also work for you"
date: 2007-07-26
forum: Gaming &amp; Leisure
---

### Post by nowshining on 2007-07-26
well  beeldings  from another post said something that finally helped me, I read the thread on setting the gampad up, and it was too confusing to say the most, however like I said one post I finally found while trying to find something with the name Saitek p220 and nothing found (yes used the ubuntu forums search feature) well this should help...

download jscalibrator by going to the startmenu accessiores and opening up terminal..

input 

sudo apt-get install libjsw2 libjsw-dev joystick jscalibrator

not input your password (ur login password) which is not shown while typing, nothing will show at all, and this is normal, so again blindly type the password in the keyboard and when done hit Enter now when it asks you a Y/N, input Y and hit enter again if it ever does..

Okay you got that installed...

plug in the saitek p220 gamepad and go to the start menu - accessiores - and find and click on joystick calibration now a dialog box will say that nothing is connected, etc.. hit enter on the keyboard or okay now exit the program, unplug the p220 and re-plug it in, open up the joystick calibration again, and keep doing this before opening up the program or after and at some point when the application is exited and not even open and when the p220 is plugged in - it should work.... and there is NO calibration needed - so you have no need to do anything else..

I hope this helps, I am using Ubuntu Feisty 7.04 and nothing else helped... I know a bit weired on what's happening, :P but that little trick worked for me...and yes if the lights come on or you can turn them on, and u leave the program and nothing happens, try re-opening it press ok or enter, exit the program and unplug the p220 and re-plugging it back in....

If you have any explanation why or how this worked or if you believe it's a bug, let me know... 'cause I just wanted to share something that I just unthinkably did and it worked for me, even works with the Wine emulator....

---

