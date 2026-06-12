---
title: "[SOLVED] Compiz-Fusion Screenshot command"
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by santiagoward2000 on 2007-09-26
Hi everyone!
I have a question which may sound stupid, but I just couldn't figure it out. There's a screenshot key bindings option under general options in Compiz-Fusion, and it is set to work with the print button. When I press it, my CPU usage goes up, so I guess it is taking the picture. However, I can't find it anywhere. I'm using Xubuntu Feisty, do I need any pakage or something for this to work?

---

### Post by sisco311 on 2007-09-26
> do I need any pakage or something for this to work?```
sudo aptitude install gnome-utils
```then edit the /usr/share/compiz/take-screenshot.sh script:
```
sudo mousepad /usr/share/compiz/take-screenshot.sh
```uncomment the following lines:
> TAKE_SCREENSHOT="gnome-screenshot"
TAKE_SCREENSHOT_window_option="--window"


---

### Post by santiagoward2000 on 2007-09-26
Hi sisco311,
Thanks! It worked just fine!

---

### Post by michael37 on 2007-10-09
Doesn't work for me...

~$ ls -l /usr/share/compiz/take-screenshot.sh 
-rwxr-xr-x 1 root root 76 2007-10-09 15:33 /usr/share/compiz/take-screenshot.sh
~$ cat /usr/share/compiz/take-screenshot.sh 
TAKE_SCREENSHOT="gnome-screenshot"
TAKE_SCREENSHOT_window_option="--window"

Both Alt-PrintScreen and PrintScreen make the cursor blink but do not produce anything.

When I created the file, it didn't have executable permissions, so I was getting an error "can't execute /usr/share/compiz/take-screenshot.sh".

I am running compiz 0.6 with Gutsy beta.

---

### Post by michael37 on 2007-10-09
I tried running gnome-screenshot --window from a terminal, and it works -- takes the screenshot of the terminal itself.  Now, to get it working on other windows....

---

### Post by santiagoward2000 on 2007-10-16
> **michael37 said:**
> Doesn't work for me...

~$ ls -l /usr/share/compiz/take-screenshot.sh 
-rwxr-xr-x 1 root root 76 2007-10-09 15:33 /usr/share/compiz/take-screenshot.sh
~$ cat /usr/share/compiz/take-screenshot.sh 
TAKE_SCREENSHOT="gnome-screenshot"
TAKE_SCREENSHOT_window_option="--window"

Both Alt-PrintScreen and PrintScreen make the cursor blink but do not produce anything.

When I created the file, it didn't have executable permissions, so I was getting an error "can't execute /usr/share/compiz/take-screenshot.sh".

I am running compiz 0.6 with Gutsy beta.

I think the ones you need to uncomment are those under Example:
> # EXAMPLE
TAKE_SCREENSHOT="gnome-screenshot"
TAKE_SCREENSHOT_window_option="--window"

---

### Post by michael37 on 2007-10-16
> **santiagoward2000 said:**
> I think the ones you need to uncomment are those under Example:

Not real sure what you mean.  Don't I have the lines uncommented already?

---

### Post by santiagoward2000 on 2007-10-16
> **michael37 said:**
> Not real sure what you mean.  Don't I have the lines uncommented already?

I don't know... In my case, I had:
```
# EXAMPLE
#TAKE_SCREENSHOT="gnome-screenshot"
#TAKE_SCREENSHOT_window_option="--window"
```

And I changed it to:
```
# EXAMPLE
TAKE_SCREENSHOT="gnome-screenshot"
TAKE_SCREENSHOT_window_option="--window"
```

That did it!

---

### Post by michael37 on 2007-10-17
> **santiagoward2000 said:**
> ...
And I changed it to:
```
# EXAMPLE
TAKE_SCREENSHOT="gnome-screenshot"
TAKE_SCREENSHOT_window_option="--window"
```

That did it!

I see.  As I mentioned in comment 4, I already have these lines uncommented.

---

### Post by santiagoward2000 on 2007-10-17
Hmmm, I'm sorry I can't help you. I hope someone else can!

---

### Post by franganghi on 2007-10-20
Go into gconf-editor, then nav on to '/apps/metacity/keybinding_cammands/cammand_screen shot' and assign the values:

command_screenshot:
gnome-screenshot
command_window_screenshot:
gnome-screenshot --window -e shadow

# "-e shadow" to get a shadow around the captured image.:lolflag:

---

### Post by michael37 on 2007-10-22
> **franganghi said:**
> Go into gconf-editor, then nav on to '/apps/metacity/keybinding_cammands/cammand_screen shot' and assign the values:

command_screenshot:
gnome-screenshot
command_window_screenshot:
gnome-screenshot --window -e shadow

# "-e shadow" to get a shadow around the captured image.:lolflag:

I use compiz, not metacity.  Still the same command or a different one?

---

### Post by Steven_B on 2007-10-23
> then edit the /usr/share/compiz/take-screenshot.sh script:
I don't have that file.  From michael37's replies, I'm guessing he didn't either.
However, I am able to take screenshots of the cube and other effects by using a delay:
```
gnome-screenshot -d 5
```

---

### Post by IHateSnow on 2007-10-23
> **Steven_B said:**
> 
However, I am able to take screenshots of the cube and other effects by using a delay:
```
gnome-screenshot -d 5
```

I'm taking them the same exact way and its working fine.

Of course this can give you a bunch more info:

```
man gnome-screenshot
```

---

### Post by vaishnavi on 2007-11-04
Strange as it may sound, in /usr/share/compiz folder I find screenshot file as an xml application and not as .sh. Renaming dint help either.I am unable to take screenshot of cube effect using gnome screenshot option.
Any idea how to fix this issue?

---

