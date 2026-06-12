---
title: "Sony VAIO FZ brightness WORKS!"
date: 2008-12-07
forum: General Help
---

### Post by hihihi on 2008-12-07
Hello!
Good News!
I can report, that brightness is working now on my Sony VAIO FZ31M. (nvidia 8400M GT)
thanks to the guide of "frank17" here (it is in italian):
[http://www.frank17.it/linux/fz18m.htm](http://www.frank17.it/linux/fz18m.htm) from [http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)

it is a real solution:
the nvclock from cvs, provided in that site, is able to control the brightness of my laptop!
I waited for that now very long...

let's put that in English:

**(MINI-HOW-TO)**:

First of all, be careful, I do not know if this can demage your hardware,
it works very well for me, but you should know what you are doing... at your own risk..
you should also have everything one needs to compile, like autoconf tools etcetc..

i highly recommend checkinstall instead of make install,
checkinstall keeps your system clean and you can easely find and uninstall your self-compiled packages under synaptic.
```
$ sudo apt-get install checkinstall
```

1) 
if you never downloaded anything with cvs, and you never heard of it, than you need to open the terminal ant type this:

```
  $ sudo apt-get install cvs
```

2)
create a folder somewhere in your home-dir called "nvclock"
in my case I hava a folder in my home-dir called "apps" and inside that one I will create a folder called "nvclock"

```
  $ mkdir ~/apps/nvclock
```


3)
now enter your new folder

```
  $ cd ~/apps/nvclock
```

paste this into the terminal:

```
  $ cvs -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock login
```

it will ask for a password, but you just press 'ENTER'

to download the nvclock from cvs paste this into your terminal:

```
  $ cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock
```


4)
after the cvs snapshot is done you can
compile and install nvclock:

```
  $ cd ~/apps/nvclock/nvclock 
  $ ./configure
  $ make
  $ sudo checkinstall
```

you need to go through the checkinstall-wizard inside the terminal and correct the name and version, otherwise it will abort.
it is very easy as the wizard is well done.
i named it "nvclock" and set version to "0.8.4"

everything went flawlessly yesterday and you will end up with a nice build and installed .deb package which you can uninstall at anytime via synaptic.


5)
now we can try it out:
*(note: nvclock will be installed as default in /usr/local/bin)*

```

    $ /usr/local/bin/nvclock -S -10

    $ /usr/local/bin/nvclock -S -10
```

Look how the brightness is changing: Smartdimmer should be working now and you should be reading this message: "Changing Smartdimmer level from 100% to 90% New Smartdimmer level: 90%"


6)
To get this function to work with the FnKeys FN+F5/F6 we will have to change the scripts /etc/acpi/events/sony-brightness-down e sony-brightness up:

```
    $ sudo gedit /etc/acpi/events/sony-brightness-down

    event=sony/hotkey SNC 00000001 00000010
    action=/usr/local/bin/nvclock -S -10
```
```

    $ sudo gedit /etc/acpi/events/sony-brightness-up

    event=sony/hotkey SNC 00000001 00000011
    action=/usr/local/bin/nvclock -S +10
```

Save the changes and type this into the terminal to make them executable again:
```

    $ sudo chmod +x sony-brightness-down

    $ sudo chmod +x sony-brightness-up
```

Finally restart your acpi-demon:

```
    $ sudo etc/init.d/acpid restart
```

The FnKeys should work now, but we will have to reboot the machine
and test again, if everything went well, your FnKeys FnF5/F6 should control the real brightness of your LCD.


**Dim backlight on Battery**

Create the file /etc/udev/rules.d/80-smartdimmer.rules  (thx to IntuitiveNipple)
```

# NVidia backlight control using nvclock





ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Battery", ATTR{status}=="Discharging", RUN+="/usr/local/bin/nvclock -S 50"

ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Battery", ATTR{status}=="Charging", RUN+="/usr/local/bin/nvclock -S 100"
```

Reload the UDEV rules and then try switching the charger off/on:
```

 sudo udevadm control &#8211;reload_rules
```



Happy brightnessing!
):P

---

### Post by steve101101 on 2008-12-11
do you know how to do with on a cr120 sony vaio without a nvidia card in it??

---

### Post by remarks on 2008-12-16
Thanks for this info....

It mostly works for my VGN-SZ55TN

I also required a few packages before I could ./configure

```
 sudo apt-get install libxext-dev libx11-dev
```

I can use the ```
/usr/local/bin/nvclock -S -10
``` and ```
/usr/local/bin/nvclock -S +10
``` to adjust the brightness by -10% and +10% increments but I cannot seem to get the function keys to work.

My brightness keys are F5 and F6.
[B]
How can I check to see what numbers I need for my FN keys to work because the default entries in this tutorial don't seem to work for my FN keys??[/B] event=sony/hotkey SNC 00000001 00000011

---

### Post by anthropo on 2008-12-16
> **remarks said:**
> Thanks for this info....

It mostly works for my VGN-SZ55TN

I also required a few packages before I could ./configure

```
 sudo apt-get install libxext-dev libx11-dev
```

I can use the ```
/usr/local/bin/nvclock -S -10
``` and ```
/usr/local/bin/nvclock -S +10
``` to adjust the brightness by -10% and +10% increments but I cannot seem to get the function keys to work.

My brightness keys are F5 and F6.
[B]
How can I check to see what numbers I need for my FN keys to work because the default entries in this tutorial don't seem to work for my FN keys??[/B] event=sony/hotkey SNC 00000001 00000011



acpi_listen

):P

---

### Post by hihihi on 2008-12-18
> **remarks said:**
> ...
My brightness keys are F5 and F6.
[B]
How can I check to see what numbers I need for my FN keys to work because the default entries in this tutorial don't seem to work for my FN keys??[/B] event=sony/hotkey SNC 00000001 00000011

hello there, as anthropo said, you need to work now with acpi_listen in order to find out the key code, it is very easy:

1)
open termninal,
$ sudo gedit /etc/acpi/events/sony-brightness-down


2)
open another terminal and type:
$ acpi_listen


3)
press your fn-f5 (brightness-down) and read the value
compare that with the one in the script and if needed replace that.

4)
repeat the same with /etc/acpi/events/sony-brightness-up

5)
restart acpid
$ sudo /etc/init.d/acpid restart

6)
test it
if it does not work, try to reboot before getting the crisis//
this should work.

good luck

---

### Post by psyeye on 2008-12-29
two things: 
1) thanks a ton! :)
2) added vaio sz tag since I have such a model with nvidia gfx

regards,
psyeye

---

### Post by psyeye on 2008-12-30
One question though: I always need to restart acpid before my fn-keys start to work.

Anyone any idea why? Seems a bit strange to me...

regards,
psyeye

---

### Post by Flashman2003 on 2009-01-19
Whoaw thanks man, I've been waiting for this to work for years now :P

I can finally use Ubuntu on my vaio FZ21S

---

### Post by jacklsw2008 on 2009-01-23
i got a problem here. when i used acpi_listen and typed fn+f5, nothing appears. maybe keyboard layout settings problem?

---

### Post by matts12290 on 2009-03-01
i have to do: sudo /etc/init.d/acpid restart every time for it to work. any work around for having to manually type it in every time i restart?

---

### Post by matts12290 on 2009-03-02
I was able to fix the problem of having to enter it every time I restarted by editing my rc.local file in /etc to do the command when the computer starts.

Thanks for all of the help here!  Works like a charm!!

---

### Post by skkeeper on 2009-03-07
I got a Sony VAIO FZ21E with a NVIDIA 8400GT, and i installed nvclock and smartdimmer with sucess and now i can change the brightness with the console with no problems at all.

My problem begins in the ACPI, i followed the tiny how here and nether the FN keys or the charger ACPI event work.

I restarted the laptop and the acpid service itself... no luck...

CAn my acpi daemon have something wrong? (by the way, cant i disable the GNOME screens that pop out when i push the FN combinations, if theire doing nothing with the nvclock?)

Thanks in advance

EDIT: the FN keys work now with a fresh install, but the AC trick stil doesnt work for me

---

### Post by prcjac on 2009-03-16
I recently upgraded to 8.10 because I needed some features of the new kernel.
With 8.04 nvclock worked perfectly with the function keys and the display dimmed when on battery.
I also need to restart acpi daemon to get the function keys to work but couldn't get the rc.local script to work.
I wondered what the triggers are to bring up the brightness up and down window and whether it was possible to piggy back that?

---

### Post by prcjac on 2009-03-19
I've managed to find a solution to the function keys not working unless you restarted acpi on my FZ11.
I used information on a Suse Forum [http://forums.opensuse.org/hardware/laptop/403273-sony-vaio-fz21m-everything-now-working.html](http://forums.opensuse.org/hardware/laptop/403273-sony-vaio-fz21m-everything-now-working.html) by philipraets's so all credit is to him.

Insert this into /etc/acpi/events/sony-brightness-up
```
# /etc/acpi/events/sony-brightness-up
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/sonybright.sh up
```

Insert this into /etc/acpi/events/sony-brightness-down
```
# /etc/acpi/events/sony-brightness-down
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/sonybright.sh down
```

Insert this into /etc/acpi/sonybright.sh
```
#!/bin/bash
if [ "x$1" = "xdown" ]; then
# xbacklight -steps 10 -dec 10 2>/tmp/sonybright.log
        nvclock -S -15
elif [ "x$1" = "xup" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
        nvclock -S +15
elif [ "x$1" = "xdim" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
        nvclock -S 15
elif [ "x$1" = "xbright" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
        nvclock -S 100
else
   echo >&2 Unknown argument $1
fi
```

Then run
```
sudo chmod +x sony-brightness-up
sudo chmod +x sony-brightness-down
sudo chmod +x sonybright.sh
```

Restart ACPI by
```
sudo /etc/init.d/acpid restart

```
Now the function keys should be ok

Still can't get the backlight to dim on power loss...

Oh well,
Hope that helps

---

### Post by bruxo_da_silva on 2009-04-24
> **prcjac said:**
> I've managed to find a solution to the function keys not working unless you restarted acpi on my FZ11.
I used information on a Suse Forum [http://forums.opensuse.org/hardware/laptop/403273-sony-vaio-fz21m-everything-now-working.html](http://forums.opensuse.org/hardware/laptop/403273-sony-vaio-fz21m-everything-now-working.html) by philipraets's so all credit is to him.

Insert this into /etc/acpi/events/sony-brightness-up
```
# /etc/acpi/events/sony-brightness-up
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/sonybright.sh up
```

Insert this into /etc/acpi/events/sony-brightness-down
```
# /etc/acpi/events/sony-brightness-down
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/sonybright.sh down
```

Insert this into /etc/acpi/sonybright.sh
```
#!/bin/bash
if [ "x$1" = "xdown" ]; then
# xbacklight -steps 10 -dec 10 2>/tmp/sonybright.log
        nvclock -S -15
elif [ "x$1" = "xup" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
        nvclock -S +15
elif [ "x$1" = "xdim" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
        nvclock -S 15
elif [ "x$1" = "xbright" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
        nvclock -S 100
else
   echo >&2 Unknown argument $1
fi
```

Then run
```
sudo chmod +x sony-brightness-up
sudo chmod +x sony-brightness-down
sudo chmod +x sonybright.sh
```

Restart ACPI by
```
sudo /etc/init.d/acpid restart

```
Now the function keys should be ok

Still can't get the backlight to dim on power loss...

Oh well,
Hope that helps

I follow this tutorial, and managed to work with the Fn keys to control the brightness, on my vgn-c2z in Jaunty.

To get the backlight to dim on power loss, I simply create two new files:

/etc/acpi/events/sony-brightness-dim
```
# /etc/acpi/events/sony-brightness-down
event=ac_adapter ADP1 00000081 00000000
action=/etc/acpi/sonybright.sh dim
```

/etc/acpi/events/sony-brightness-ac
```
# /etc/acpi/events/sony-brightness-down
event=ac_adapter ADP1 00000081 00000001
action=/etc/acpi/sonybright.sh bright
```

And everything just works :)

Now I just need to see how to change the notification about the brightness... It doesn't go to the maximum value...

---

### Post by herculea8n1982 on 2009-04-25
Oh man I'd just like to say to the two previous posters that your solutions worked a treat with Ubuntu 9.04 on my Sony Vaio VGN-NR32S (even the dimming on loss of AC power.) So I had to:


[LIST]
[*]Install proprietary NVIDIA driver
[*]Install nvclock
[*]Create the scripts from your posts
[*]Enjoy
[/LIST]
Thanks again.:guitar:

---

### Post by cldmello on 2009-04-25
> **matts12290 said:**
> I was able to fix the problem of having to enter it every time I restarted by editing my rc.local file in /etc to do the command when the computer starts.

Thanks for all of the help here!  Works like a charm!!

Thanks for the rc.local tip!

Just one question ..... do I need to put in sudo when executing the restart script in rc.local?

To re-phrase, should I use 

sudo /etc/init.d/acpid restart

OR 

/etc/init.d/acpid restart 

Thanks!

---

### Post by lordjeremias on 2009-04-26
Sudo restart
you're messing in protected areas and with systems daemons ;)

---

### Post by dugii on 2009-05-01
Works just fine on my FZ470E :) Now everything realy works :) I've been waiting for this since i bought my sony vaio, at last vaio and ubuntu loves each other :)
Thanks!

---

### Post by carljmoss on 2009-05-11
I've got a SZ330P and with a small mod the same fixes work under Jaunty.

Do exactly the same thing as here but, in sony-brightness-down and sony-brightness-up, replace SNC by SPIC. It works like a charm!

It may not be relevant, but the other files in /etc/acpi/events on my system don't have the execute attribute set. So I didn't bother with

sudo +x sony-brightness-*

and it still seems to work OK.

---

### Post by mosquetero on 2009-05-11
Hi everyone!

Today I changed from Ubuntu 8.04 to Ubuntu 9.04 but I didn't upgrade, I deleted Ubuntu 8.04 and I installed 9.04 in its place (I had my reasons). This "trick" used to work in the 8.04 version but in the new one it does not work.
Everything goes fine but when I write /usr/local/bin/nvclock -S -10 it says: Xlib: extension "NV-CONTROL" missing on display ":0.0".

Any idea about how to solve it??

---

### Post by jungaar on 2009-05-13
does this work with sony vaio fw292 ?? on 64 jaunty

---

### Post by sephirot_5 on 2009-05-24
> **jungaar said:**
> does this work with sony vaio fw292 ?? on 64 jaunty

YES it does ;) (working here)

---

### Post by cyleo on 2009-06-03
I'm trying to install it nvclock on xubuntu. Everything went well untill the ./configure part, where the terminal gives me the following error: 
checking for gtk+-2.0 >= 2.4.0... checking for x11... configure: error: "X11 required for nvcontrol support"
So I checked, but X11 is installed, anyone know what I need to do? Maybe I miss a X11 package? Thanks in advance.

---

### Post by DracheMitch on 2009-11-08
I have a VGN AR630e with 9.10 and adding the scripts worked for me.

---

### Post by klaush on 2009-12-01
Following [http://www.uluga.ubuntuforums.org/showpost.php?p=7133147&postcount=14](http://www.uluga.ubuntuforums.org/showpost.php?p=7133147&postcount=14) and [http://www.uluga.ubuntuforums.org/showpost.php?p=7133147&postcount=15](http://www.uluga.ubuntuforums.org/showpost.php?p=7133147&postcount=15) worked on a Sony Vaio VGN-SZ1XP with kubuntu 9.10, I just had to 

  sudo apt-get install nvclock 

and create the files under /etc/acpi as mentioned,
slightly modifying the ACPI events to fit to the VGN-SZ1XP - using acpi_listen and noting the events for keypresses and power cable removal/re-plug.
Now increasing/decreasing display brightness works, and display is dimmed automatically if power is plugged off and set to bright once power is plugged in again.

The only (minor) issue left is that the display brightness is always reported as being "0%" in all cases, but display brightness changes properly.

Thanks folks for posting these tweaks!

---

### Post by Regenkind on 2010-11-20
Just like klaush said: Thanks for this post! I have an updated Mint 10 Linux and Brightness control via fn now works with my vaio VGN-FW31M ! :D

---

### Post by Rich62 on 2011-02-12
Thanks for all the great work on this tutorial.  The commands /usr/local/bin/nvclock -S -10 and /usr/local/bin/nvclock -S +10 are working for me, but what isn't working is the key combinations.  My laptop is a FZ11L and the brightness keys are Fn+F5 and Fn+F6 but when I run acpi_listen and press them I get 

sony/hotkey SNC 00000001 00000010

sony/hotkey SNC 00000001 0000003b


sony/hotkey SNC 00000001 00000011

sony/hotkey SNC 00000001 0000003b


Can someone show me how to correctly input these into /etc/acpi/events/sony-brightness-down and /etc/acpi/events/sony-brightness-up?

Thanks
Rich

---

### Post by adelani on 2011-12-01
I have Sony Vaio VGN FZ340E and after long search I found the solution in the following link 
[B]
[http://doube.org/karmic-vaio](http://doube.org/karmic-vaio)[/B]

and now its working perfect without any problem I've only changed the (the SPIC to SNC) for both files
  
sony-brightness-up
sony-brightness-down
Shown expression


for sony-brightness-up file
event=sony/hotkey SPIC 00000001 00000011

I used the following expression
event=sony/hotkey **SNC** 00000001 00000011

for sony-brightness-down file
event=sony/hotkey SPIC 00000001 00000010

I used the following expression
event=sony/hotkey **SNC** 00000001 00000010


Backlight

Backlight support for Vaios is now incorporated in nvclock 
Make sure you have nvclock installed for basic backlight control, and until HAL has been updated you have to specify the hotkey event manually.

$ sudo apt-get install nvclock
$ nvclock -S 100
$ nvclock -S 15
$ nvclock -S +10

Enable the "brighter" hotkey:

$ sudo gedit /etc/acpi/events/sony-brightness-up
put this text into it:

event=sony/hotkey SNC 00000001 00000011
action=/usr/bin/nvclock -S +10
And the "dimmer" hotkey:

$ sudo gedit /etc/acpi/events/sony-brightness-down
put this text into it:

event=sony/hotkey SNC 00000001 00000010
action=/usr/bin/nvclock -S -10
Make the scripts executable

$ sudo chmod +x /etc/acpi/events/sony-brightness-*
Restart acpid

$ sudo /etc/init.d/acpid restart
If you have a different model, you might have different keys controlling your backlight. To check the event ID, run

$ acpi_listen

---

### Post by adelani on 2011-12-01
I forgot to say that I am using Ubuntu 11.10

Best wishes for all

---

