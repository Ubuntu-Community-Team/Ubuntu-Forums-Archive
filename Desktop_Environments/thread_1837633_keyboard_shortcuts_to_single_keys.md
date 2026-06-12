---
title: "keyboard shortcuts to single keys?"
date: 2011-09-02
forum: Desktop Environments
---

### Post by rylleman on 2011-09-02
I have a [[COLOR="black"][COLOR="black"][COLOR="Red"]A4 x7-G100 keyboard[/COLOR][/COLOR][/COLOR]]("http://www.x7.cn/en/product.asp?id=7") which I've setup with a custom keymappping (as  [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1560537")).
This way I can remap the keyboard to a custom layout which is fine. But what I want to do is assigning shortcuts to keys.

[I]I want to use the board as a controlbox for graphics and video work so assigning shortcuts like ctrl+s to single buttons.

How can this be done? I have searched but haven't found a way yet.
[/I]
Next step after I get shortcuts working is that I'd like to have different keymaps for different applications.

---

### Post by David Andersson on 2011-09-06
I'll divide it into two sub-problems: 1) Catch a key press to make it run a command. 2) Send a key press from a command. Second first.

**2. Send a key press from a command**

One way to generate key events is the *xmacroplay* in package *xmacro*. This command will send Ctrl-S after 2 seconds:

```
sleep 2; echo KeyStrPress Control_L KeyStr s KeyStrRelease Control_L | xmacroplay $DISPLAY
```

The 2 second sleep is needed so the Return-key which invoked the command have been released before new key presses are generated. It also gives you time to move focus from the terminal to the video application, so the Ctrl-S is sent to the application.

When you bind this command to a key, shorten the sleep to something like 0.3 seconds. Focus is supposed to be in the video application when invoked, so sleep just long enough for the invoking key to be released. 

```
sleep 0.3; echo KeyStrPress Control_L KeyStr s KeyStrRelease Control_L | xmacroplay $DISPLAY
```

The command can be used as is, but to simplify management, save it in a script. I'll assume the script is called ~/bin/mysendctrls. A script may look like this

```
#!/bin/bash
# Send a Ctrl-S. You may freely copy, change and distribute this script.
sleep 0.3; echo KeyStrPress Control_L KeyStr s KeyStrRelease Control_L | xmacroplay $DISPLAY
```

**1. Catch a key press to make it run a command (in Gnome)**

In Gnome, go to **System > Preferences > Keyboard Shortcuts**. Press **Add**, enter name **Send Ctrl-S** and enter the command **mysendctrls**.

Scroll down to Send Ctrl-S, **click on Inactive** and **press the keyboard key** that is to invoke this command.

_Alternative_

**1. Catch a key press to make it run a command (in Xfce)**

In Xfce, go to **Settings > Keyboard**, tab **Application Shortcuts**, press **Add**, enter command **mysendctrls**, and **press the keyboard key** that is to invoke this command.

_Alternative_

**1. Catch a key press to make it run a command (with xbindkeys)**

Install package *xbindkeys*. 
To find the name of a keyboard key, run
```
xbindkeys -k
```
and press the keyboard key that is to be bound. Create a file ~/.xbindkeysrc containing (replace NAME_OF_KEY with the name of the key):

```
# You may freely copy, change and distribute this config file.
# Let the NAME_OF_KEY key send Ctrl-S
"mysendctrls"
  NAME_OF_KEY
```

---

### Post by rylleman on 2011-09-07
Thank you!
We're on the right track here I think but there are some issues.

I create scripts in a folder in my home folder, then symlinking these to /bin. All works well here, I can execute scripts from terminal.

Now to binding to keys. here is when it all goes wrong...
I've mapped a layout with strange characters I'll never use for anything else to the x7-keyboard,afghanistaan. So &#4324; is mapped to "F" key.
I'm doing this so I can map single characters to commands and still being able to use main keyboard as normal.

I use Gnome so I set up custom command in "Keyboard Shortcuts", assigning &#4324; to "x7-save".

1. It does work somewhat. I have to double-tap the key to execute "x7-save". With a higher sleep-value, I can hold down the key to execute, which probably is because key is repeated when held.
With lower values, <~0.5, holding doesn't work and I have to double tap. with even lower sleep value, or without sleep I can't even double tap to execute.
2. Assigning &#4324; (F-key on x7-keyboard) to script does work. But it also makes the F-key on my main keyboard stop working... Seems like keyboard shortcuts doesn't actually use the characters assigned but the keys pressed...

---

### Post by rylleman on 2011-09-07
It seems to be pretty much the same with xbindkeys.
It uses keys and not characters.

xbindkeys -k for X7-keyboard &#4324; ("F"-key) gives
    m:0x10 + c:41
    Mod2 + Georgian_phar
for "F"-key on main keyboard:
    m:0x10 + c:41
    Mod2 + f

I've tried using "Mod2 + Georgian_phar" but can't get it to work. control+f is bound to x-term which starts with "control+&#4324;" also...

---

### Post by David Andersson on 2011-09-07
> **rylleman said:**
> 
I create scripts in a folder in my home folder, then symlinking these to /bin. All works well here, I can execute scripts from terminal.

If you save the script in ~/bin (that is $HOME/bin or /home/rylleman/bin) it is made available to you automatically. (It would not be automatically available to other users of the same computer, but I don't think that was the intention anyway, since you symlinked to home.)

---

### Post by rylleman on 2011-09-08
Thanks for the tip, good to know.
However that is not the issue now, scripts work, it's the execution by keyboard shortcuts that does not.
Do you have any suggestions there?

---

### Post by David Andersson on 2011-09-08
If I understand correctly you have two keyboards. I have no experience with that.

I am thinking about a solution where the key mapping depends on what application is active. You could extend the script, using xdpyinfo or xdotool to find the id of the window that currently has focus, xwininfo to find its name, and then a case-statement with different xmacroplay depending on the name. It is a bit clumsy, and you may still have a problem if you need to auto-repeat the key. Therefor I searched for ready solutions how to re-map keys per application, but didn't find anything obvious.

Other routes are to find out how to remap keys strictly on the symbols ("&#4324;" and "f"). Or to design a new layout for the other keyboard where the alphabetical keys will be special functions keys that does not exists on your normal keyboard. That would be some extra work, I guess.

---

