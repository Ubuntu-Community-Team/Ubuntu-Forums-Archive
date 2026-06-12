---
title: "Universal navigation hot keys with sxhkd"
date: 2024-08-24
forum: Desktop Environments
---

### Post by Tom_ZeCat on 2024-08-24
Hi, everyone.  I wish do be able to use the following commands in my word processor or text editor on my computer: 

> Ctrl+A = move one word left
Ctrl+S = move one character left
Ctrl+F = move one word right
Ctrl+D = move one character right
Ctrl+E = move one line up
Ctrl+X = move one line down
Ctrl+QS = move to beginning of line
Ctrl+QD = move to end of line
Ctrl+Alt+[ = move to beginning of line
Ctrl+Alt+] = move to end of line

I've been able to do all of these in LibreOffice Writer, except for Ctrl+QS and Ctrl+QD, via the application's macros and keystroke combination system.  In fact, the reason for the two hot keys, Ctrl+Alt+[ and Ctrl+Alt+], are that they're replacements for those two that I wasn't able to get to work in LO Writer.  

Therefore, in LibreOffice, I'm doing pretty well.  However, I also use two other word processors, one named “Fade In” for writing stage plays and screenplays and another named “SoftMaker TextMaker” for writing in German.  I also use some basic text editors such as Kate, Gedit, and Geany.  I would love to get the same commands working for all of these apps, but they don't have the same macro and hot key systems that LibreOffice has.  

My online research showed me that I should be able to make this work with two tools: 

sxhkd
xdotool

I've had some success getting these tools to launch applications, but I'm not having any luck getting them to do those navigation commands inside a word processor or text editor.  For example, I've gotten the hot key, Meta+Shift+O to open the Opera browser.  I was also able to get Meta+Z to open the Brave browser and Meta+Shift+Z to open the Falkon one.  Kubuntu has a built-in system where you can assign hot keys to launch apps, so these settings weren't desperately needed, but I did them just to see if I could get sxhkd to work.  

In short, I've gotten these application launch hot keys to work, but my navigation hot keys elude me.  For example, if I've turned on sxhkd and xdotool, and I hit Ctrl+A, noting happens the first couple times.  If I keep hitting it, it then just types the letter A.  Same thing with Ctrl+S.  Nothing happens the first two or three times, then it just types S.  

In LibreOffice's macros, I was able to get around the fact that LO writer already has a command assigned to Ctrl+A.  Its innate command selects all text.  In LO Writer, that's no big deal.  Ctrl+A now moves the cursor one word left, but if I need to select all text, I can just use Writer's other hot key for it, Alt+EA.  

I also have it set up so that I can easily turn off these hot key programs and turn them back on if I need to.  The following commands I have put into Kubuntu's app launcher: 

# Run xdotool and sxhkd
xdotool & sxhkd -c $HOME/.config/sxhkd/sxhkdrc && echo "SXHKD is now running."

# Kill both
killall sxhkd && killall xdotool && echo "SXHKD is now terminated"

# Edit my sxhkdrc file
geany $HOME/.config/sxhkd/sxhkdrc

I'll post my sxhkdrc config file at the end of this post, so that maybe someone will be able to tell what I'm doing wrong.  Another option I've found, but haven't delved into deeply is to use xbindkeys instead of sxhkd, but word online is that sxhkd is the nicer of the two tools.  Or maybe I should be doing this with some kind of programming language like Python or C++?  I would need to study up if that's the case.  I don't know those languages.  

If anyone has any pointers on what might make this work, I would greatly appreciate any advice.  Thanks.  

Here's my sxhkdrc config file: 

```
###[Launch apps] #####
# launch opera with Shift+Meta+o  [works]
super + shift + o
    opera
# Meta+Z opens Brave, Shift+Meta+Z opens Falkon [works for both Brave(Meta+Z) and Falkon (Shift+Meta+Z)]
super + {_,shift + } z
    {brave-browser-stable,falkon}
# Meta+BO starts Opera Browser [works]
super + b + o
    opera

###[Navigation Commands]###
# Ctrl+A = move one word left
ctrl + a
    xdotool key "ctrl+Left"

    # Ctrl+S = move one character left
ctrl + s
    xdotool key "Left"

# Ctrl+F = move one word right
ctrl + f
    xdotool key "ctrl+Right"

# Ctrl+D = move one character right
ctrl + d
    xdotool key "Right"

# Ctrl+E = move one line up
ctrl + e
    xdotool key "Up"

# Ctrl+X = move one line down
ctrl + x
    xdotool key "Down"

# Ctrl+QS = move to beginning of line
ctrl + q + s
    xdotool key "Home"

# Ctrl+QD = move to end of line
ctrl + q + d
    xdotool key "End"

# Ctrl+Alt+[ = move to beginning of line
ctrl + alt + bracketleft
    xdotool key "Home"

# Ctrl+Alt+] = move to end of line
ctrl + alt + bracketright
    xdotool key "End"
```

---

