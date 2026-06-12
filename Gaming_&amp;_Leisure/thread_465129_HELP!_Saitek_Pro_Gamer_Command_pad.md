---
title: "HELP! Saitek Pro Gamer Command pad"
date: 2007-06-05
forum: Gaming &amp; Leisure
---

### Post by ./Coffee on 2007-06-05
Hello,

I bought a Saitek Pro Gamer Command pad because everybody said that it was Linux compatible; However I loaded the software that other posts and blogs had said and configured them yet to no avail. It still doesn't work it registers as one big button (there are 22 buttons). 

Please help me.:(

Just let me know what you need.

Thank you.

---

### Post by Pragmatist on 2007-06-05
Unplug the device, open a terminal, and type this:
```
tail -f /var/log/messages
```

Note the last line on the terminal and remember it.  Now, plug the device in and watch for new lines on the terminal.  Post those new lines here.  When your all finished, you can press CTRL-C in the terminal to stop the above command.

---

### Post by ./Coffee on 2007-06-05
Ok I did just as you said and here are the results.

with it unplugged:
Jun  5 11:09:59 codepoets-station gconfd (root-26137): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  5 11:09:59 codepoets-station gconfd (root-26137): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  5 11:09:59 codepoets-station gconfd (root-26137): GConf server is not in use, shutting down.
Jun  5 11:09:59 codepoets-station gconfd (root-26137): Exiting
Jun  5 11:37:36 codepoets-station kernel: [43113.471550] usb 1-1: USB disconnect, address 3
Jun  5 11:38:01 codepoets-station kernel: [43137.647260] usb 1-1: new low speed USB device using ohci_hcd and address 5
Jun  5 11:38:01 codepoets-station kernel: [43137.858135] usb 1-1: configuration #1 chosen from 1 choice
Jun  5 11:38:01 codepoets-station kernel: [43137.871104] input: Saitek Pro Gamer Command Unit as /class/input/input8
Jun  5 11:38:01 codepoets-station kernel: [43137.871161] input: USB HID v1.00 Joystick [Saitek Pro Gamer Command Unit] on usb-0000:00:03.0-1
Jun  5 11:38:37 codepoets-station kernel: [43173.643563] usb 1-1: USB disconnect, address 5

Then when I plugged it in again it added these:

Jun  5 11:38:56 codepoets-station kernel: [43193.279259] usb 1-1: new low speed USB device using ohci_hcd and address 6
Jun  5 11:38:57 codepoets-station kernel: [43193.489857] usb 1-1: configuration #1 chosen from 1 choice
Jun  5 11:38:57 codepoets-station kernel: [43193.502818] input: Saitek Pro Gamer Command Unit as /class/input/input9
Jun  5 11:38:57 codepoets-station kernel: [43193.502878] input: USB HID v1.00 Joystick [Saitek Pro Gamer Command Unit] on usb-0000:00:03.0-1

---

### Post by ./Coffee on 2007-06-21
Any help would be much appreciated even to get a little functionality out of the unit would be great .
:-k

---

### Post by Pragmatist on 2007-06-21
What is the output of these:
```
ls -l /dev/input
```

```
ls -l /dev/input/by-id
```

```
ls -l /dev/input/by-path
```

---

### Post by ./Coffee on 2007-06-22
Here are the outputs that you wanted.

the out put for ls -l /dev/input:

drwxr-xr-x 2 root root        120 2007-06-19 23:15 by-id
drwxr-xr-x 2 root root        140 2007-06-19 23:15 by-path
crw-rw---- 1 root input   13,  64 2007-06-19 23:15 event0
crw-rw---- 1 root input   13,  65 2007-06-19 23:15 event1
crw-rw---- 1 root input   13,  66 2007-06-19 23:15 event2
crw-rw---- 1 root input   13,  67 2007-06-19 23:15 event3
crw-rw---- 1 root input   13,  68 2007-06-19 23:15 event4
crw-rw---- 1 root input   13,  69 2007-06-19 23:16 event5
crw-rw---- 1 root input   13,  70 2007-06-19 23:16 event6
crw-rw---- 1 root input   13,  71 2007-06-19 23:16 event7
crw-rw-r-- 1 root plugdev 13,   0 2007-06-19 23:15 js0
crw-rw---- 1 root root    13,  63 2007-06-19 23:15 mice
crw-rw---- 1 root root    13,  32 2007-06-19 23:15 mouse0
crw-rw---- 1 root root    13,  33 2007-06-19 23:15 mouse1
crw-rw---- 1 root root    13, 128 2007-06-19 23:15 ts0
crw-rw---- 1 root root    13, 129 2007-06-19 23:15 ts1

The output for ls -l /dev/input/by-id:

lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-06a3_Saitek_Pro_Gamer_Command_Unit-event-joystick -> ../event2
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-Device_USB_Device-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-Device_USB_Device-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-Device_USB_Device-mouse -> ../mouse1

The output for ls -l /dev/input/by-path:

lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-06a3_Saitek_Pro_Gamer_Command_Unit-event-joystick -> ../event2
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-Device_USB_Device-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-Device_USB_Device-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 usb-Device_USB_Device-mouse -> ../mouse1
codepoet@codepoets-station:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 pci-0000:00:03.0-usb-0:2:1.0-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 pci-0000:00:03.0-usb-0:2:1.1-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 pci-0000:00:03.0-usb-0:2:1.1-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 pci-0000:00:03.2-usb-0:1:1.0-event-joystick -> ../event2
lrwxrwxrwx 1 root root 9 2007-06-19 23:15 platform-pcspkr-event-spkr -> ../event1

And there you have it I know what most of it means but not how it helps(That is the reason I am asking for help)

---

### Post by Pragmatist on 2007-06-22
Try this:
```
cat /dev/input/js0
```

Now, while that is running, press different buttons and watch the terminal.  Which buttons cause something to happen and which do not?

---

### Post by ./Coffee on 2007-06-23
Well they all caused something to print out but a lot of them  just printed question marks which I am assuming that is what you meant. Here is the output for whatever reason you may need it.

output: (hitting all the buttons in order upper to lower left to right)

&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;&#65533;/&#65533;   &#65533;&#65533;/&#65533;
&#65533;&#65533;/&#65533;
    &#65533;&#65533;/&#65533;
&#65533;&#65533;/&#65533;ð·/   &#65533;&#65533;/&#65533;&#65533;&#65533;/&#65533;`&#65533;/`&#65533;/`&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;/&#65533;/&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/(&#65533;/(&#65533;/(&#65533;/X&#65533;/X&#65533;/X&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/
                                                               &#65533;&#65533;/H&#65533;/H&#65533;/
                                                                            H&#65533;/h&#65533;/h&#65533;/h&#65533;/h&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;/&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/$&#65533;/$&#65533;/&#65533;&#65533;/&#65533;&#65533;/
                                            &#65533;&#65533;/&#65533;/&#65533;/
                                                         &#65533;/$&#65533;/$&#65533;/$&#65533;/$&#65533;/&#65533;&#65533;/&#65533;&#65533;/d&#65533;/d&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/&#65533;&#65533;/\&#65533;/\&#65533;/&#65533;/&#65533;/&#65533;/&#65533;/t&#65533;/t&#65533;/<&#65533;/&#65533;/,0,0,0&#65533;0&#65533;0&#65533;0
                        0
                           0
                                0|0|0    |0&#65533;0&#65533;0
&#65533;0\0\0
\0000&#65533;0&#65533;0&#65533;04     04     04    0  ô  0   ô  0   ô 0  \
     0   \
           0  \
                 0&#65533;
                     0&#65533;
                        0&#65533;
                           0$0$0,07-,0,040&#65533;4040<0&#65533;<0<0&#65533;0&#65533;l&#65533;0&#65533;0&#65533;0? &#65533;0&#65533;0&#65533;0&#65533;0&#65533;&#65533;0&#65533;0000t0t0|0a&#65533;|0|0&#65533;0&#1407;&#65533;0&#65533;0&#65533;0&#65533;&#65533;&#65533;0&#65533;0&#65533;0&#65533;&#65533;0&#65533;00&#65533;&#65533;000ê 0   0  $0    $0 ä0   ä0  ì0 ] ì0   ì0  ô0 ÿ ô0   ô0  T0   T0  \0 ó \0   \0  &#9229;0    &#9229;0   &#9229;0  ä0   ä0  ô0 ù       ô0   ô0  ü0 à/ü0   ü0  0 &#9149;R0   0  
                                            0 &#9618;&#9532;
                                                   0   
                                                         0  0  0   0  0 £0   0  $0 ÐF$0   $0  ,0 ö,0   ,0  40   40   40  
&#9228;&#9146;&#9229;&#9226;&#9147;&#9146;&#9226;&#9500;@&#9228;&#9146;&#9229;&#9226;&#9147;&#9146;&#9226;&#9500;&#9149;-&#9149;&#9500;&#9618;&#9500;&#9227;&#9146;&#9532;:·$ 

this is as clear as mud so um... ya thats about it.

Thanks for the help.

---

### Post by Pragmatist on 2007-06-24
You didn't understand my suggestion.  The output is not supposed to be readable.  The point is to press buttons and see if *anything* shows up in the terminal.  So you have to watch the terminal while pressing a button and see if any new characters appear on the screen.  Then repeat this process with a different button.

If all 22 buttons output characters on the screen, it means that all buttons are recognized by Linux.  This was the purpose of all of my suggestions.  First you determine if the device works at the lowest levels.  If it does, then you look elsewhere for the problem (such as specific configurations of a game, or other application that uses the controller).

I own two different controllers, and this is the method I used to get them  to work.

Bottom line: Linux recognizes your controller (repeat the suggestion in my previous post if you want to know how many buttons are recognized)

---

### Post by viodream on 2008-03-18
I have this keyboard but i dont know to work with the games.

In terminal i see the characters that you say.

Any idea how to do it working whit any game? Thanks!

PD: Sorry for mi bad english.

---

### Post by cunning001 on 2008-04-17
ok, so I'm in the same boat.

From following this thread I've found that the pro gamer ... (i just can't type that it sounds ridiculous they shouldn't have used a google translation of the korean i suspect) anyway all of the buttons work for this and the thumb stick but the problem is as follows...
when using this in a win system you need a little app running to use it , what this program does is take all of the input from it and translate it into keystrokes which are set based on a profile you set up for the particular app/game .

So, what we would need is something similiar running and ideally config files that could be set (most likely manually ?) I'm guessing I'll have to look for some app like I'm describing (seems like there should be something) if I find something I'll post it.

---

### Post by imlost on 2008-10-14
> **cunning001 said:**
> ok, so I'm in the same boat.

From following this thread I've found that the pro gamer ... (i just can't type that it sounds ridiculous they shouldn't have used a google translation of the korean i suspect) anyway all of the buttons work for this and the thumb stick but the problem is as follows...
when using this in a win system you need a little app running to use it , what this program does is take all of the input from it and translate it into keystrokes which are set based on a profile you set up for the particular app/game .

So, what we would need is something similiar running and ideally config files that could be set (most likely manually ?) I'm guessing I'll have to look for some app like I'm describing (seems like there should be something) if I find something I'll post it.


Try this: [https://launchpad.net/pystromo](https://launchpad.net/pystromo)

It might work with it.

---

### Post by Kuroyume on 2008-10-14
> **cunning001 said:**
> ok, so I'm in the same boat.

From following this thread I've found that the pro gamer ... (i just can't type that it sounds ridiculous they shouldn't have used a google translation of the korean i suspect) anyway all of the buttons work for this and the thumb stick but the problem is as follows...
when using this in a win system you need a little app running to use it , what this program does is take all of the input from it and translate it into keystrokes which are set based on a profile you set up for the particular app/game .

So, what we would need is something similiar running and ideally config files that could be set (most likely manually ?) I'm guessing I'll have to look for some app like I'm describing (seems like there should be something) if I find something I'll post it.

i used joy2key (it's on the ubuntu repos) but i don't have my config file anymore :(

I remember it being fairly easy to configure though. I'll see if i can find a tutorial for you.


EDIT: [http://psubuntu.com/forum/viewtopic.php?t=1768](http://psubuntu.com/forum/viewtopic.php?t=1768)

That's a config tutorial. It seems to be for playstation joysticks, but the basics are pretty much the same.

---

### Post by imlost on 2008-10-15
> **cunning001 said:**
> ok, so I'm in the same boat.

From following this thread I've found that the pro gamer ... (i just can't type that it sounds ridiculous they shouldn't have used a google translation of the korean i suspect) anyway all of the buttons work for this and the thumb stick but the problem is as follows...
when using this in a win system you need a little app running to use it , what this program does is take all of the input from it and translate it into keystrokes which are set based on a profile you set up for the particular app/game .

So, what we would need is something similiar running and ideally config files that could be set (most likely manually ?) I'm guessing I'll have to look for some app like I'm describing (seems like there should be something) if I find something I'll post it.

Here is what you guys need.

[https://launchpad.net/pystromo](https://launchpad.net/pystromo)

download version 0.6.0 unpack it and follow the readme file included in the tar.

Go to /home/username/.config

In there create a folder called "pystromo" without the quotes.
Extract the files from the tar you downloaded to this location.

Open a terminal window and do the following commands.

```
sudo gedit /etc/modules
```

In there add "uinput" (without the quotes) to the file and save and close it.

Open another terminal window and do the following command.

```
modprobe uinput
```

Now close that terminal window and open another terminal window and do the following.

```
lsusb
```

This should output a list of USB devices connected to the computer. Now I use a Belkin Nostromo N52 and the line for my controller looks like this:

```
Bus 002 Device 004: ID [COLOR="Red"]050d[/COLOR]:[COLOR="Blue"]0815[/COLOR] Belkin Components
```

But yours should say something with Saitek at the end.

What we are looking for is the vendor number and Product number. Notice the part I have in red and blue in the above line. The red part is the vendor number and the blue part is the product number.

Write this part from your Saitek line down. We will be adding it to one of Pystromo's config files.

Now from a terminal window do the following command.

```
gedit /home/username/.config/pystromo/config/saitek.map
```

In this file put the following info.
> 
# Saitek Pro Gamer Command pad
[Device:pro]
vendor=0x(Put in the red numbers I had you right down)
product=0x(Put in the blue numbers I had you right down)

[Map:pro]

Now save and close that file.

Open another terminal window and do the following command.

```
gedit /home/username/.config/pystromo/config/monitor.conf

```

Now take out all the lines and copy and paste the following information.

```
# This is the configuration file for Pystromo's monitoring script.
# Each line herein specifies a mapping file to use when certain
# processes are detected as running.
# With the exception of "*", whitespace in the key IS NOT ignored.
# "=" is an invalid character in keys.

# The * defines mapping files to use all the time
*=config/saitek.map
```

Now save and close this file.

Now open a regular blank text file.

Press the buttons on your Saitek one by one and mark down what character appears for which button you pressed. We are going to use this information to configure it.

Once you have written down all of the information and you know what every button does on the Saitek do the following command from a terminal window.

```
gedit /home/username/.config/pystromo/config/saitek.map
```

Now here we want to put the information all after the last line in the current file, the [Map:pro] part.

Basically what we are doing now is telling Pystromo first what the button on the Saitek we are wanting to configure is bound to by default.

The easiest way to do this is write the following.

```
KEY_
```

You will then press the button on the Saitek that you want to configure. This will out put a character to your document or it will do something else, such as shift or capslock or tab.

Lets say it output the character A, but the character will be small so it will look like this:

```
KEY_a
```

Delete the small "a" and replace it with a big "A"

```
KEY_A
```

We will now tell it what we want to bind that key to.

```
KEY_A:KEY_1
```

This will bind the key "1" to the Saitek key we are programming.

Do this for each key that you want to program. For a list of keys the Pystromo can understand and bind to your Saitek open up the constrants.py file with a text editor. That file is located here:

/home/username/.config/pystromo/lib/constrants.py

Now for specific programming such as delays or having the key repeat itself every so many miliseconds take a look at the test.map file located at: /home/username/.config/pystromo/config/test.map

It gives a list of commands you can use to configure it.

Once you have every key you want configured on the Saitek open a terminal window and type the following commands.

```
cd /home/username/.config/pystromo
sudo ./pystromo-remap.py -m config/saitek.map
```

Now minimize this terminal window (DO NOT close it)

Open a text editor and test your Saitek by pressing it's keys. If all went well it should now be outputting whatever key you programmed to each key on the Saitek!

As far as running Pystromo as sudo, I don't know how to make a .rules file for the Saitek so that you can run it as a normal user. Perhaps someone else knows and can enlighten the rest of us.

Good luck and happy gaming!!

---

### Post by Dataforce on 2009-04-11
I know this is an old thread, so sorry for bringing it back up, but its one of the first results on google for this, so.

I've created a git repo at [http://git.soren.co.uk/?p=shane/pystromo.git](http://git.soren.co.uk/?p=shane/pystromo.git) that contains a version of pystromo that has has been modified specifically to work with this pad (Or rather, the updated version "Saitek Cyborg Command Unit" which I assume is still quite similar)

[LIST]
[*] Allow specifying buttons to be treated as LEDs (BTN_Z, BTN_TR and BTN_TL are used for changing mode and are sent as BTN events not the LED Change events that the app expected)
[*] Allow storing last-known LED to a savefile (If the mode changes between sessions, it is annouced, otherwise it is not.)
[*] Add missing items in constants to allow buttons 13, 14 and 15 to work.
[*] Add empty config file for gamepad containing all the buttons available.
[/LIST]

Any questions/problems, pm me or something :)

---

