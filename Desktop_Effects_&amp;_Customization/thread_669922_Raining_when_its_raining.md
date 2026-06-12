---
title: "Raining when its raining"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by OneWingedAngel0164 on 2008-01-16
I reecently got ubuntu and fell in love with the rain effect then thought how awesome would it be to have it come on when it is raining. So far I have come up with this much for a shell script that works:

dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_ra in org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'`

and this is what I have attempted to add to make it come on if its raining:

weather --id=KTLH | grep -q rain
if [[ "${?}" -eq "0"]] then
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_ra in org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'`
fi

I don't know how to do if statements in shell yet. If I can get the shell script working, then I can put it into crontab and have it check every 15 mins or so.

Anyone know how to fix my if and if this crazy idea will work?

Thanks,
Mike

---

### Post by glennric on 2008-01-16
I can help you with your if statement, but how did you figure out that command to activate rain?  Do you have to have the dbus plugin for compiz enabled for that to work?  It doesn't seem to work for me.

As to the script try:
```

weather --id=KTLH | grep -q rain
if [[ "${?}" -eq "0"]]; then
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'`
fi

```
Note the semicolon after the conditional.

Edit:  I got this to work.  Here is one for snow.
```

weather --id=KMCI | grep -q snow
if [[ "$?" -eq "0" ]]; then
	dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
fi

```

---

### Post by OneWingedAngel0164 on 2008-01-17
Thank you so much! I almost have it working to where when its raining outside my desktop rains!

---

### Post by allforcarrie on 2008-01-17
that is a great concept! you should have a range of weather!

---

### Post by OneWingedAngel0164 on 2008-01-19
ok so here is the shell script that I have working, but I don't have a way to run a process for it other than crontab which is not working for me :( any ideas?

#!/bin/sh
# id=KTLH is for Tallahassee you have to change this for your location!

weather --id=KTLH | grep -q overcast
if [ "$?" -eq "0" ]; then
	dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'`
fi

---

### Post by xfearxnxloathing on 2008-01-19
this sounds awseome, i hope you guys figure it all out!

---

### Post by DaymItzJack on 2008-01-19
Once you get this working, if you do, can you post a how-to?

---

### Post by MNICY on 2008-01-19
> **DaymItzJack said:**
> Once you get this working, if you do, can you post a how-to?

yes! that would be great.

---

### Post by marckie on 2008-01-20
> **MNICY said:**
> yes! that would be great.

Im looking forward for this one...
I hope this can be included in the Compiz Manager with a range of Weather...
Like:

Desktop Glows or desktop is on fire -- if it is so hot
Snows or rains if it is 
and even thunder and whirlwind if the weather is so damn bad...

Great idea!

---

### Post by glennric on 2008-01-29
After a little research into the workings of dbus, I figured out how to do this.  Here is a quick howto.  You will have to look up the four letter id (in blue below) for your local weather.  You can look in the file /etc/weatherrc, or try to find one on [http://weather.noaa.gov/](http://weather.noaa.gov/).

First we have to have a way for a script run from cron to get the users dbus session bus address.  This is stored in an environment variable.  The only way I could figure out how to do this was to first create a script that saves this information to a file on startup.  So edit the file ~/bin/dbus-address (which should not exist yet) and put the line
```
echo $DBUS_SESSION_BUS_ADDRESS > ~/.dbus/user-dbus-address
```
in it.  Then make this file executable and make it run at startup by adding it  in System->Preferences->Sessions.

The following script depends on the weather program so make sure it is installed by typing 
```
sudo apt-get install weather-util
```
in a terminal.

Next edit the file ~/bin/weather-check and cut and paste the following into it.
```
#!/bin/bash
# Set some session specific variables
export DISPLAY=:0
export DBUS_SESSION_BUS_ADDRESS=`cat ~/.dbus/user-dbus-address`

# Get the local weather
WEATHER=`weather --id=[COLOR="Blue"]KMCI[/COLOR] | grep 'Weather'`

# Check if it is snowing
echo $WEATHER | grep -q snow
if [[ "$?" -eq "0" ]]; then
	if [[ ! -f ~/.snowing ]]; then
		dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`;
		touch ~/.snowing
	fi
elif [[ -f ~/.snowing ]]; then
	dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`;
	rm -f ~/.snowing;
fi

# Check if it is raining
echo $WEATHER | grep -q rain
if [[ "$?" -eq "0" ]]; then
	if [[ ! -f ~/.raining ]]; then
		dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`;
		touch ~/.raining
	fi
elif [[ -f ~/.raining ]]; then
	dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`;
	rm -f ~/.raining
fi

```

Don't forget to make the weather-check script executable.

Finally type "crontab -e" in a terminal and add the line
```
*/15 * * * * ~/bin/weather-check
```
to the last line of the file.

Also make sure the "DBus," "Snow," and "Water Effect" plugins are enabled in compiz.  Note that the snow plugin is part of the compiz-fusion-plugins-unsupported package, which is not in the repositories.  I believe there is a howto in the forums on how to install it.  So you will have to search the forums for it.

This should make it snow if it is snowing, and rain if it is raining.

Edit:  If anyone knows of a better way of obtaining the users dbus session bus address from a script run in cron let me know.

---

### Post by Mary.Riley on 2008-01-29
That's a ridiculously cool idea! Now, if we could only get a lightning plugin for Compiz... Or maybe some fog?

---

### Post by OneWingedAngel0164 on 2008-01-31
Thanks with that dbus part it works now! Now I have something to show off even though I didn't create it entirely :P I suppose the next step is making an installer that does all that for you.

---

### Post by DaymItzJack on 2008-01-31
I can't get this to work, how can I make sure crontab is working correctly and that it's getting the data correctly?

---

### Post by glennric on 2008-02-01
> **DaymItzJack said:**
> I can't get this to work, how can I make sure crontab is working correctly and that it's getting the data correctly?

Are you trying to use your users crontab or the root crontab?  Make sure it is your users crontab, i.e., don't use sudo.  My method can be modified to run from the root crontab, but it probably is not a good idea.
As to checking that crontab is working you can try putting 
```
>> ~/test 2>&1
```
at the end of various lines in the script to see if there are errors when the script executes that line.
Or just insert
```
echo "test" >> ~/test
```
at the beginning of the script to see if it is even running.
Then after the cron job should have run check to see if you have a file test in your home directory and see what is in it.

Another thing I should have said in the howto is that the snow plugin is not part of a default install of compiz.  It is part of the compiz-fusion-plugins-unsupported package, which is not in the repositories.  I think there is a howto somewhere on how to install those.  Search the forums.

---

### Post by DaymItzJack on 2008-02-01
I didn't make weather-check executable, (you didn't tell me too ;p) but now all I got to do is wait for it to rain.

I'm still confused about something:

you check the " Sky conditions", but "rain" and "snow" is under the "weather"

---

### Post by PinkFloyd102489 on 2008-02-01
It rained here today and it's supposed to rain tomorrow. I'll test this out. :-P

---

### Post by glennric on 2008-02-01
> **DaymItzJack said:**
> I didn't make weather-check executable, (you didn't tell me too ;p) but now all I got to do is wait for it to rain.

I'm still confused about something:

you check the " Sky conditions", but "rain" and "snow" is under the "weather"

I will add the part about making the files executable.  Also, I am not sure what the format for various weather types looks like.  You may have to adjust that line.  My output looks like this:
```
Current conditions at Kansas City International Airport (KMCI)
Last updated Feb 01, 2008 - 04:53 PM EST / 2008.02.01 2153 UTC
   Wind: from the SSE (160 degrees) at 16 MPH (14 KT)
   Sky conditions: partly cloudy
   Temperature: 37.0 F (2.8 C)
   Relative Humidity: 61%

```
It hasn't snowed or rained while I was working on this so I will adjust that when I figure it out.  If someone could show me their output when it is raining or snowing that might help.

---

### Post by Liv on 2008-02-01
> **glennric said:**
> I can help you with your if statement, but how did you figure out that command to activate rain?  Do you have to have the dbus plugin for compiz enabled for that to work?  It doesn't seem to work for me.
I have the same problem.  I can get the fire to work no problem but not the rain :(

---

### Post by DaymItzJack on 2008-02-01
I got it to completely work on my system:

```
#!/bin/bash
# Set some session specific variables
export DISPLAY=:0
export DBUS_SESSION_BUS_ADDRESS=`cat ~/.dbus/user-dbus-address`

# Get the local weather
WEATHER=`weather --id=KIAH | grep 'Weather'`

# Check if it is raining
echo $WEATHER | grep -q rain

WEATHER = $(tr [:upper:] [:lower:] <<< "$WEATHER")

if [[ $WEATHER == *rain* || $WEATHER == *mist* ]]
then
   if [[ ! -f ~/.raining ]]
   then
      dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | awk '/id:/ {print $4}'`;
      touch ~/.raining
   fi
else
   if [[ -f ~/.raining ]]
   then
   dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | awk '/id:/ {print $4}'`;
      rm -f ~/.raining
   fi
fi
```
I didn't do snow.. because it doesn't snow it Texas!

---

### Post by glennric on 2008-02-01
> **Liv said:**
> I have the same problem.  I can get the fire to work no problem but not the rain :(

What do you mean fire and not rain?  What fire?  The script I gave has snow and rain.  The rain is really the water effect.

---

### Post by glennric on 2008-02-01
> **DaymItzJack said:**
> I didn't make weather-check executable, (you didn't tell me too ;p) but now all I got to do is wait for it to rain.

I'm still confused about something:

you check the " Sky conditions", but "rain" and "snow" is under the "weather"

After checking the weather around the nation (it is snowing in Buffalo), I changed the script.  Thanks for pointing this out.

Edit: I didn't see your last post.  I haven't seen any weather conditions that have upper case letters, but it doesn't hurt to make sure.  As to the mist thing activating rain, if you use snow as well you may get both.  For instance, here is Buffalo's current weather:
```

Current conditions at Greater Buffalo International Airport (KBUF)
Last updated Feb 01, 2008 - 08:01 PM EST / 2008.02.02 0101 UTC
   Wind: from the SW (230 degrees) at 7 MPH (6 KT)
   Sky conditions: overcast
   Weather: light snow; mist
   Precipitation last hour: A trace
   Temperature: 33 F (1 C)
   Relative Humidity: 93%

```

---

### Post by DaymItzJack on 2008-02-01
I'm not sure, I was testing some where in New York and it said "Rain" and "Mist" so I'd figure it's better to do it than to have it mess up.

---

### Post by Liv on 2008-02-02
> **glennric said:**
> What do you mean fire and not rain?  What fire?  The script I gave has snow and rain.  The rain is really the water effect.

:) Well first off, I didn't upload the code because I get my friend to do it because he's much better at it than I am. But even before this amazing "rain when it's raining" achievement; the rain effect will not work, even if I change the toggle keys. I can get the fire on screen effect to work, the cube, and the negative windows effect to work but no raindrops :(.
If anyone knows how I can do this?  Maybe I have to reload.  I can use the terminal but I'm just learning, so step by step instructions would be much appreciated.
Liv

---

### Post by DaymItzJack on 2008-02-02
First, try to see if your water plugin works correctly in the first place by doing "Shift+F9" (if you didn't change it)

If that works, try typing this in the terminal:

```
dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/toggle_rain org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | awk '/id:/ {print $4}'`;
```

If that works, try my script on page #2 and test that out!

---

### Post by Liv on 2008-02-02
> **DaymItzJack said:**
> First, try to see if your water plugin works correctly in the first place by doing "Shift+F9" (if you didn't change it)
I don't think the plugin is working because none of that helped... :confused:

---

### Post by DaymItzJack on 2008-02-02
> **Liv said:**
> I don't think the plugin is working because none of that helped... :confused:

Type "ccsm" in terminal, go to water effect (make sure it's checked). If it's checked, go to the plugin settings and make sure rain delay is set somewhere low (around 250-350). After that check the "Actions" tab and find the hotkey for "Toggle rain", make the hotkey Shift+F9 (the default) if yours isn't set. After all that, check to see if it's working again by doing the hotkey set (Shift+F9), and if that works, try pasting that line in my last post into terminal and tell me if that works.

---

### Post by vektra on 2008-03-14
I am having a problem with both scrips, with the scrip on the first page everything seems to run smoothly but it does not fire off the effect at the end but I get no errors. on the 2nd script posted by DaymItzJack I think I will have better luck but when I run it I get 

./weather-check: line 12: WEATHER: command not found

and I do not know enough about scripting to fix it myself. Thanks for your help and your work on this awesome effect.

btw I copy and pasted the scrips

---

### Post by DaymItzJack on 2008-03-14
Paste ```
sudo apt-get install weather-util
``` into your terminal.

---

### Post by DaymItzJack on 2008-03-15
-ignore-

---

### Post by Crusty Juggler on 2008-03-20
Anyone know if this is possible for non US cities?

---

### Post by easybake on 2008-06-06
What am I doing wrong. I want my background to change rather than start the rain command. I copied the script on page 2. The coloring of letters stop after <<<"$WEATHER" Any help on what I can change?

> #!/bin/bash
# Set some session specific variables
export DISPLAY=:0
export DBUS_SESSION_BUS_ADDRESS=`cat ~/.dbus/user-dbus-address`

# Get the local weather
WEATHER=`weather --id=KMDW | grep 'Weather'`

# Check if it is raining
echo $WEATHER | grep -q rain

WEATHER = $(tr [:upper:] [:lower:] <<< "$WEATHER")

if [[ $WEATHER == *rain* || $WEATHER == *mist* ]]
then
   if [[ ! -f ~/.raining ]]
   then
      gconftool -t string -s /desktop/gnome/background/picture_filename /home/easybake/Pictures/Background/Rain.jpg
   fi
else
   if [[ -f ~/.raining ]]
   then
      gconftool -t string -s /desktop/gnome/background/picture_filename /home/easybake/Pictures/Background/Cloudy.jpg
   fi
fi

---

### Post by dblank7 on 2008-07-21
I just installed Ubuntu today without much prior experience in scripting or Linux, i was wondering if you could explain more in depth what to do? I get lost around the first step, how do i edit/create things in the bin folder if it is read only? making a file an executable is just checking the box in preferences? also it worked fine when i did "sudo apt-get install weather-util" but then there is no ~/bin/weather-check and still?

---

