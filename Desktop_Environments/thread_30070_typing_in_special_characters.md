---
title: "typing in special characters"
date: 2005-04-27
forum: Desktop Environments
---

### Post by theonewhoismany on 2005-04-27
on my windows boxes i use "special characters" like "ð" and "ß" by presseing key combinations like "ALT+0240" however under Ubantu i can't seem to figure out how to enter these characters.

i've found the characters under the character map but for the life of me can't figure out how to type them in. please help me.

thanks

---

### Post by Alexander Kirillov on 2005-04-27
[QUOTE=theonewhoismany]on my windows boxes i use "special characters" like "ð" and "ß" by presseing key combinations like "ALT+0240" however under Ubantu i can't seem to figure out how to enter these characters.

i've found the characters under the character map but for the life of me can't figure out how to type them in. please help me.

thanks[/QUOTE]
 If you just need one or two, use character map:
find a symbol in character map, double-click on it. It will appear in "text to copy" field. Press "Copy". Now you can paste this anywhere by using CTRL+V. 

If you use it frequently, you can use "compose" keys. Go to Preferences-Keyboard, 
 select "layout options" tab and click on "compose". Enable one of the options (e.g., Right Alt is compose). Now, to enter, say ß, press Right Alt+s, then s. To enter é, press  Right Alt+', then e.

---

### Post by MadL on 2006-08-17
> **Alexander Kirillov said:**
> 
If you use it frequently, you can use "compose" keys. Go to Preferences-Keyboard, 
 select "layout options" tab and click on "compose". Enable one of the options (e.g., Right Alt is compose). Now, to enter, say ß, press Right Alt+s, then s. To enter é, press  Right Alt+', then e.

Thanks! This problem had me ](*,) for a while. Makes typing German much easier. :)

Is there a layout somewhere of all the different characters the Compose key creates?

---

### Post by TuxCrafter on 2006-09-11
I am going to pop up this topic.

I use xubuntu and i have the problem that i am not able to use:
SHIFT+; then e for ë it will give me :e

this is my xorg section i believe is is good and it also doesn't for these mapping characters.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
```

found this info i am checking it out now

Linux / NetBSD: Using the dead-keys. In an xterm window first press the (´) or (`) key. The character should not appear on the screen. Now press a letter, such as "e". The e is given an accent, é or è. If not, then check in the XF86Config file if a "nodeadkeys" XkbdVariant has been loaded there and replace it. You may also have set the environment variable SAL_NO_DEADKEYS, which deactivates the dead-keys. 

I don't have a keyboard setting dialogue or something like that. How do get my special characters working? 

Please use only terminal and text editor as tools for explanations

---

### Post by TuxCrafter on 2006-09-11
I have changed my xorg to:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option 		"XkbVariant" 	"deadkeys"
EndSection
```

it get loaded

```

error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbVariant" "deadkeys"
(**) Generic Keyboard: XkbVariant: "deadkeys"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
```

I also checkt the printenv file but there is nothing related to the deadkeys.

Can somebody help me?

---

### Post by Riel on 2007-07-01
Same problem here!

Linux / NetBSD: Using the dead-keys. In an xterm window first press the (´) or (`) key. The character should not appear on the screen. Now press a letter, such as "e". The e is given an accent, é or è. If not, then check in the XF86Config file if a "nodeadkeys" XkbdVariant has been loaded there and replace it. You may also have set the environment variable SAL_NO_DEADKEYS, which deactivates the dead-keys. 


Can't find anything related.

---

### Post by Riel on 2007-07-01
You can use the Compose-key.


I set the Ralt, so pressing R-alt, and the tilde (shift `) and then n  makes ñ.

Just works

ë ö é ì ;)

Now doing it automaticcally would be nice.

---

### Post by kstella on 2007-07-04
How do you make them lowercase? I keep getting a capitalized Ñ.

---

### Post by andycyca on 2007-07-05
I've just seen a quick method without Composite, already enabled in (X)Ubuntu. 

1. In the Character Map select the character you wish to use
2. On the lower part of the window, you can see the code for the character, something like **U + 2669 QUARTER NOTE**
3. Now you may be wondering *What is U?* U is the shorthand for Shift+Ctrl+u. When you input these an underlined u will appear. the, you simply type the code (2669 in this example) and press space
4. Voilà! There's your special Character.

Info [here]("https://help.ubuntu.com/community/ComposeKey"). More about the Character Map [here]("https://help.ubuntu.com/community/CharacterMap")

---

### Post by GerryB on 2007-07-08
> **theonewhoismany said:**
> on my windows boxes i use "special characters" like "ð" and "ß" by presseing key combinations like "ALT+0240" however under Ubantu i can't seem to figure out how to enter these characters.

i've found the characters under the character map but for the life of me can't figure out how to type them in. please help me.

thanks

This will give you where to start. 
[http://ubuntuforums.org/showthread.php?t=480849](http://ubuntuforums.org/showthread.php?t=480849)

---

### Post by fjgaude on 2007-07-08
I use the Add to Panel feature, the Character Palette, which puts most of the upper ASCII characters on a tab. Click on a character then middle (wheel) mouse click in your document where you which the character placed. Works nicely and is elegant in terminal and gedit. Don't use other text programs except Xara and Scribus.

frank

---

