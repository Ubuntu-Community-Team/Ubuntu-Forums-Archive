---
title: "Keyboard shortcuts to mouse buttons ? (not CCSM)"
date: 2011-02-24
forum: Desktop Environments
---

### Post by Guillaumeb on 2011-02-24
Hello, 

i'm looking for a way to map some of my mouse buttosn to activate certain keyboard shortcuts.

I went thru the Compiz setting Manager but they only allow predetermined actions to be mapped.

What I want, for example is to map a mouse button to trigger SHIFT+A to quiclky mark items as read in Google Reader or another one to quickly select unread emails in Gmail.

Is there some software that can achieve this ?

thank you very much

---

### Post by Guillaumeb on 2011-02-24
hum...anyone ?

---

### Post by Krytarik on 2011-02-24
You can use "xdotool" (it's in the official repos) to issue the key combo and the Compiz settings to bind the respective command to the desired mouse button. Though I can image that it interferes with some other mouse button bindings, if you assign just a single button press.

---

### Post by Guillaumeb on 2011-02-25
Thanks for coming back to me. It's too bad there is no GUI though. It's not like i'm a Terminal expert... :)

---

### Post by Krytarik on 2011-02-25
> **Guillaumeb said:**
> Thanks for coming back to me. It's too bad there is no GUI though. It's not like i'm a Terminal expert... :)
Hey, that's Linux, you can customize and tweak almost everything, but you have sometimes to use the command line.;-)

Let me know when you need help, I'd be glad to do so! And believe me, it's not really that difficult to set up.

---

### Post by nikefalcon on 2011-02-25
install xdotool.
open: System > preferences > Keyboard shortcuts
Scroll right down and under custom shortcuts, Add your own shortcut as follows.
In the window that pops up, type in the name of the action, example.
Name: left click
command: xdotool click 1

example two:
Name: right click
comand: xdotool click 2

I have assumed that your mouse is configured for right handed use; if not then exchange '1' and '2' in the commands.

Hope this helped.

---

### Post by Copper Bezel on 2011-02-25
That's actually the reverse of what he's asking for. He has a five-button mouse and isn't using the fourth and fifth buttons, so he wants to set them to execute existing keyboard shortcuts. He'll have to go into CCSM's Commands plugin for this, use xdotool's more complicated syntax for sending keystrokes to create commands there, then bind them to the mouse buttons, as Krytarik was saying.

By the way, Guillaumeb, be warned - they won't be called "button 4" and "button 5" in CCSM, because those are the names of the up and down actions of a vertical scroller, followed by 6 and 7 as the horizontal axis. I *think *your buttons would be 8 and 9.

---

### Post by Krytarik on 2011-02-25
Use "xev" (in the terminal) to lookup the actual button numbers.

---

### Post by Krytarik on 2011-02-25
I forgot to mention: You don't have to use the command line *at all* to achieve what you want. ;-)

1.) install "xdotool" through Synaptic

2.) go to "System -> Preferences -> CompizConfig Settings Manager -> Commands"

- at the first tab, "Commands", enter the respective xdotool command:
```
xdotool key shift+a
```- at the tab "Button Bindings" assign the desired mouse button to the newly created command

Manpage of "xdotool":  [http://manpages.ubuntu.com/manpages/maverick/en/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/xdotool.1.html)

---

### Post by Copper Bezel on 2011-02-25
Oh, hey, that's a hell of a lot simpler than the corresponding command for xautomation. I'll remember this one.

---

### Post by stinkeye on 2011-02-25
Easystroke (mouse gestures) will allow you to assign a keyboard shortcut to a mouse button.
Go to easystroke > preferences and click on the add button under Additional Buttons.
Set to instant gestures and click the button you want to modify in the window
or choose the button in the dropdown. Click OK.

Go to the actions tab and hit the add actions button.
Choose a name and and select type.. **key** and add keystroke.

Select the **Record Stroke** button and press the mouse button you want to modify.

You will need to set easystroke to autostart in the preferences tab.

---

### Post by thecapsaicinkid on 2011-04-03
So is there a way to map keyboard shortcuts to mouse clicks *without* Compiz.

I want to map Alt+Esc to my middle mouse button.

Easystroke doesn't work, record gesture just refuses to work.

---

### Post by Krytarik on 2011-04-03
You can use "xdotool" for that, it's in the official repos.

Add a command like this to "Preferences -> Keyboard Shortcuts":
```
xdotool click 2
```Then set the desired key combination for it.

You may need to lookup/check the actual button number for your middle click button, usually it should be "2" (stated in xdotool's manpage). Therefore run
```
xev
```and press the middle click button while having the pointer in the square.

Greetings.

---

### Post by thecapsaicinkid on 2011-04-03
> **Krytarik said:**
> You can use "xdotool" for that, it's in the official repos.

Add a command like this to "Preferences -> Keyboard Shortcuts":
```
xdotool click 2
```Then set the desired key combination for it.

You may need to lookup/check the actual button number for your middle click button, usually it should be "2" (stated in xdotool's manpage). Therefore run
```
xev
```and press the middle click button while having the pointer in the square.

Greetings.
Doesn't this do the opposite, i.e a keyboard shortcut generates a mouse click?

---

### Post by Krytarik on 2011-04-03
> **thecapsaicinkid said:**
> Doesn't this do the opposite, i.e a keyboard shortcut generates a mouse click?
LOL:D Sure! Your post wasn't so clear to me in that aspect, and I didn't read the OP again, sorry. Apparently, I'm the second guy who has reversed the original intention. I was already wondering why someone would like to do it this way around. :)

So, as for your actual question, no, I don't know any other apps than already mentioned with whom one is able to achieve this. And so far I didn't try Easystroke as well.

---

### Post by stinkeye on 2011-04-04
> **thecapsaicinkid said:**
> So is there a way to map keyboard shortcuts to mouse clicks *without* Compiz.

I want to map Alt+Esc to my middle mouse button.

Easystroke doesn't work, record gesture just refuses to work.
Are you adding the button first?
> Go to easystroke > preferences and click on the add button under Additional Buttons.
Set to instant gestures and click the button you want to modify in the window
or choose the button in the dropdown. Click OK.

---

### Post by idodialog on 2011-04-21
Absolutely brilliant
Despite searching and searching I did not locate Easystroke. Had I located it I would have struggled to work out how to use it!
In two minutes my extra 2 side buttons on my trusty Logitech now Copy and Paste. I am a happy man.
Accurate and clear instructions. 
Thanx

---

### Post by yoramdavid on 2012-07-03
> **stinkeye said:**
> Easystroke (mouse gestures) will allow you to assign a keyboard shortcut to a mouse button.
Go to easystroke > preferences and click on the add button under Additional Buttons.
Set to instant gestures and click the button you want to modify in the window
or choose the button in the dropdown. Click OK.

Go to the actions tab and hit the add actions button.
Choose a name and and select type.. **key** and add keystroke.

Select the **Record Stroke** button and press the mouse button you want to modify.

You will need to set easystroke to autostart in the preferences tab.


Never mind what I had written after this line, I got it working now:
I had not added a button under preferences.
Thank you.

Hello, I know this is an old thread but...
I cannot install btnx so I followed the instructions here.
I want to be able to use my 5-mouse buttons on Dolphin.
I add an action, name it "Back", select "Key" as Type and "Alt+left" as details. I then press record, a message pops up saying "The next stroke will be associated with action "Back" You can draw it anywhere on the screen (except for the two buttons below)". I click on the back button of the mouse and nothing happens.
I tried a gesture just in case still nothing.
Am I doing something wrong?

Thank you.

Yoram

PS- I am using Ubuntu gnome-classic 12.04 64 bits and installed easystroke from synaptic.

---

### Post by wildmanne39 on 2012-07-04
Hi, this is an old thread so it has been closed.
Thanks

---

