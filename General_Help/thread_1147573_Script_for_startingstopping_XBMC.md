---
title: "Script for starting/stopping XBMC"
date: 2009-05-03
forum: General Help
---

### Post by Blobba on 2009-05-03
Hi, i have made a script, well i have combined 2 diffrent scripts that i found on other forums, thats supposed to:

check if XBMC is running 
if not start it
if running kill it

heres how it looks:

```
# Test to see if XBMC is running first
if pidof -s /usr/share/xbmc/xbmc.bin
then
echo "Closing xbmc!"
# Try a clean kill
ps aux|grep -i tv|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill
echo `date` "Killed XBMC! (soft)" >> /tmp/killXBMC.log
echo "XBMC stoped (soft)"
# takes a second or two to die with the soft kill
sleep 2
if pidof -s /usr/share/xbmc/xbmc.bin
then
ps aux|grep -i tv|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill -9
echo `date` "Killed XBMC! (hard)" >> /tmp/killXBMC.log
echo "XBMC stoped (hard)"
else 
echo "XBMC Stoped (soft)"
exit
fi
else
echo "Startup XBMC"
xbmc
exit
fi
echo "Done!"
```


i have this script set up so with a button on my remote so that i can start stop XBMC even if it hangs.

my problem is that the script starts XBMC but dont stop it and if i press the button on my remote many times it starts it again when i manually stop it...
but if i start XBMC from the program menu and press the button when in XBMC it shuts it down..

im pretty sure it has to do with my maybe not so good script :)

---

### Post by Blobba on 2009-05-07
Uppdated version:

```
# Test to see if XBMC is running first

if pidof -s /usr/share/xbmc/xbmc.bin ; then
	# Try a clean kill
	echo "Closing xbmc!"
	ps aux|grep -i tv|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill
	echo "XBMC stoped (soft)"
	# takes a second or two to die with the soft kill
	sleep 2
	if pidof -s /usr/share/xbmc/xbmc.bin ; then
		ps aux|grep -i tv|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill -9
		echo "XBMC stoped (hard)"
	else 
		echo "XBMC Stoped (soft)"
	fi
else
	echo "Startup XBMC"
	xbmc
fi

echo "Done!"
```

im starting to suspect that it has something to do with xbmc or the ir deamons running in the backround..

---

### Post by cewan on 2009-06-07
Thanks for the script!
I had to modify it a little for it to work for me. Here is my version:
```

# Test to see if XBMC is running first

if pidof -s /usr/share/xbmc/xbmc.bin ; then
   # Try a clean kill
   echo "Closing xbmc!"
   ps aux|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill
   echo "XBMC stopped (soft)"
   # takes a second or two to die with the soft kill
   sleep 2
   if pidof -s /usr/share/xbmc/xbmc.bin ; then
      ps aux|grep -v grep|grep -i xbmc.bin|awk '{print $2}'|xargs kill -9
      echo "XBMC stopped (hard)"
   else 
      echo "XBMC stopped (soft)"
   fi  
else
   echo "Startup XBMC"
   DISPLAY=:0 xbmc &
fi

echo "Done!"

```

I changed the following:
* added ```
DISPLAY=:0
``` for when starting xbmc
* removed ```
grep -i tv
```, don't know why you needed that?

Thanks again!

---

### Post by generator85 on 2010-02-18
I love this script. But how can I map it to a button on my remote?

---

### Post by EnZiMa on 2010-09-16
UP!!!

i have the same question of generator85

---

### Post by generator85 on 2010-09-16
Coincidentally I was searching for the solution again yesterday. This is how you do it:

Create a file called .lircrc in your home folder with the following contents:

```
begin
remote = mceusb
button = DVD
prog = irexec
repeat = 0
config = '/path/to/startstop.py'
end

```

Change "mceusb" to your remote, and "DVD" to the button you want to map (find it out by entering "irw" in the terminal, and pressing the button)

Now when you enter "irexec" in the terminal, pressing the button on your remote should start the script.

To autostart irexec at login you should go to System->Preferences->Startup Applications. There you add the command "irexec" to the list.

---

### Post by EnZiMa on 2010-09-17
> **generator85 said:**
> Coincidentally I was searching for the solution again yesterday. This is how you do it:

Create a file called .lircrc in your home folder with the following contents:

```
begin
remote = mceusb
button = DVD
prog = irexec
repeat = 0
config = '/path/to/startstop.py'
end

```

Change "mceusb" to your remote, and "DVD" to the button you want to map (find it out by entering "irw" in the terminal, and pressing the button)

Now when you enter "irexec" in the terminal, pressing the button on your remote should start the script.

To autostart irexec at login you should go to System->Preferences->Startup Applications. There you add the command "irexec" to the list.

Thhnaaaakksssss! ;) it work, it's fantastic :D

---

