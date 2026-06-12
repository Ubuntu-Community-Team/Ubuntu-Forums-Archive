---
title: "Swap/Remap Apostrophe and Semi-Colon Keys on Mini 9"
date: 2008-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yakker.yak on 2008-12-02
I thought the location of the apostrophe/double quote would grow on me, but after giving it a try for two weeks I've decided to pop out the key and swap it with the semi-colon/colon key. BTW, this was very easy to do, provided you have a strong fingernail: just lift up the key slowly but with firm pressure starting in the lower, right-hand side of the key. Once that corner snaps off, you should be able to easily snap off the lower, left-hand side corner and then finally the upper part of the key. They snap back on pretty easily.

In any case, once that's done, you'll need to do the following:

Create a new folder in your home directory and call it Bin.

Open-up a text editor (Applications->Accessories->Text Editor) and copy-and-paste the following:

```
#!/bin/sh

xmodmap -e "keycode 47 = apostrophe quotedbl"
xmodmap -e "keycode 48 = semicolon colon"

```

Save the file in your new Bin folder as swap_quote_semicolon.sh

Open-up the file browser, right-click on the new file, and select Properties. On the 'Permissions' tab, make sure that the 'Allow executing file as program' option is checked. Close the Properties window.

Go to System->Preferences->Sessions. Click the 'Add' button to add a new session with the following details:

_Name:_ Swap Apostrophe and Semi Colon
_Command:_ /home/<user>/Bin/swap_quote_semicolon.sh
_Comment:_ Added by me

In the above, replace  <user> with your username.

That's it, once you logout and log back in, your swapped keys should now work properly. That is, each time you login, the above will be executed and the keys will be swapped.

---

### Post by yakker.yak on 2008-12-02
Now if you're like me and you occasionally dock your Mini to an external monitor and USB keyboard/mouse, you'll want the keys to work with your external keyboard (which does not have the keys swapped). In addition to the above, you'll also need to do the following:

Open-up a text editor (Applications->Accessories->Text Editor) and copy-and-paste the following:

```

#!/bin/sh

xmodmap -e "keycode 48 = apostrophe quotedbl"
xmodmap -e "keycode 47 = semicolon colon"

```

Save the file in your Bin folder as restore_default_keyboard.sh

Open-up the file browser, right-click on the new file, and select Properties. On the 'Permissions' tab, make sure that the 'Allow executing file as program' option is checked. Close the Properties window.

Right-click on the top panel, and select 'Add to panel...'

Select 'Custom Application Launcher' at the top. Fill in the details:

_Name:_ Restore Keyboard
_Command:_ /home/<user>/Bin/restore_default_keyboard.sh
_Comment:_ Added by me

In the above, replace <user> with your username.

Before closing, click on the default "spring/launch" icon and replace the path of the icon with:

```

/usr/share/icons/Human/scalable/devices/gnome-dev-keyboard.svg

```

That's a keyboard icon. Close the create new launcher window. You should now be able to right-click on the new launcher in the top panel and select 'Move' from the menu to move it around on the panel and also to lock-it into place.

Now, each time you plug-in your external USB keyboard, you can click on the new keyboard launcher in the panel to restore your keyboard and turn off the key swap used for the regular Mini 9 keyboard.

---

### Post by areitu on 2009-02-06
This article's a lifesaver! I was starting to get frustrated with the apostrophe key on my Mini9 and this is the simplest fix yet. 

What resource can I refer to (for the keycode and key name) if I want to remap some of the other keys? I'm looking to switch ctrl and fn on the lower left side of the keyboard.

---

### Post by yakker.yak on 2009-02-08
Try the man command in a terminal and check out the options for xmodmap:

```
man xmodmap
```

Particularly helpful:

```
xmodmap -pk
xmodmap -pke

```

There also xev, which will show you which key is being pressed.

---

### Post by kshep on 2009-02-21
Thanks a ton for this, yakker. I've had my eye on the Mini 10 pics thinking I might bite the bullet and "upgrade" to get a more usable keyboard, but it's worth living with the keys swapped for a bit to see how it feels.

One other thing I miss is a full, normal-size right shift key. So much so that I've just remapped the up arrow so that it's also a "shift" key (in case I miss the real key :-)). I never use Pg Up, so I just dropped that and remapped Fn-Up to Up. As a VI user I'm tempted to just remap the Fn-I, Fn-J, Fn-K, and Fn-L keys to handle cursor movement, but then a bunch of other stuff has to move too... so... maybe later.

My remapping looks like this:

```
#!/bin/sh

xmodmap -e "keycode 47 = apostrophe quotedbl"
xmodmap -e "keycode 48 = semicolon colon"
xmodmap -e "keycode 47 = Shift_R"
xmodmap -e "keycode 47 = Up"
xmodmap -e "add shift = Shift_R"
```

---

### Post by yonexFactory on 2009-03-04
What should it look like if I just want to swap the Up/Pg Up key with the right shift key?

---

### Post by yonexFactory on 2009-03-05
Alright, I figured something out with a little help from the Google. Here is what I added to the start-up script... 
```
# set up keyboard to exchange the Shift and Up keys
xmodmap -e "keycode 62 = Up" # Shift => Up
xmodmap -e "keycode 109 = Prior" # Shift-shift => PgUp
xmodmap -e "keycode 98 = Shift_R" # Up => Shift
xmodmap -e "keycode 99 = Control_R" # PgUp => Shift-shift
xmodmap -e "add shift = Shift_R" # Make the new Shift key actually do shifting
xset r 62 # Make the new Up key autorepeat
xset r 109 # Make the new PgUp autorepeat
xset -r 98 # Prevent the new Shift key from autorepeating
```
Unfortunately, according to xev there is no keycode for Fn-Shift (which I think is their 109 above) on the mini, so I don't have Pg Up anymore... but that's a small sacrifice.

---

### Post by lnb73 on 2009-03-07
Was grateful to see your instructions for remapping.
When I tried to save to my bin file, I got an error message saying "cannot save to /bin/remapkey" and "You do not have the permissions necessary to save the file."
So I'm stuck.
Any ideas?

---

### Post by anjilslaire on 2009-03-07
edit the file via sudo

---

### Post by yonexFactory on 2009-03-07
> **lnb73 said:**
> Was grateful to see your instructions for remapping.
When I tried to save to my bin file, I got an error message saying "cannot save to /bin/remapkey" and "You do not have the permissions necessary to save the file."
So I'm stuck.
Any ideas?

> **anjilslaire said:**
> edit the file via sudo

Actually, you don't need to put the file in the root /bin directory. Just make a Bin folder in your home directory. So something like /home/yourusername/Bin

---

### Post by terrapin99 on 2009-04-12
I really appreciate your help with this.  Between remapping the apostrophe and turning off some of the touchpad functions, you have immensely improved my ability to easily use the keyboard on my mini.  I believe you have even lowered my blood pressure!

---

### Post by terrapin99 on 2009-05-30
This swap worked great for several weeks, but it failed to execute following an Ubuntu update.  I can still execute it manually, but I miss the ease of having it execute when I opened Mozilla.  I double checked the permissions and it is still marked as executable.  Any idea what could be going wrong?

---

### Post by jaqrah on 2009-06-06
Yakker.yak =D>=D>

Great job!

---

### Post by thegreenblob on 2009-06-08
Thanks. Just what I was looking for.

I can now type on my mini without making typos all the time! :p :popcorn:

---

### Post by ryanjs on 2009-11-05
Hi,

Thanks for the great info, however, this only half worked for me.

I followed the instructions and the lower key (originally labeled with the apostrophe) remapped successfully and is now a semicolon/colon. The upper key next to enter is still a semicolon/colon.

Any thoughts? I ran xev in terminal and confirmed that the keycodes were correct.

Thanks,

Ryan

---

