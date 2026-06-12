---
title: "Evolution 2.24.2 change 'Preview Pane' Background color"
date: 2009-01-25
forum: General Help
---

### Post by tbuss on 2009-01-25
Hello,

I am using Ubuntu 8.10 with Evolution 2.24.2. 

I have looked everywhere to find a way to change the way Evolution displays **Received** HTMl email in the 'Preview Pane', mostly how to change the font color of the email or change the background color of the 'Preview Pane' for HTMl messages. (Please do not mistake this for changing the font/background color for composing HTML messages.)

The theme I am using is called Industrial-DarkAndBlue, a dark gray theme with a bright blue font color. Plain text 'Received Mail' is displayed with a black font on a gray background in the 'Preview Pane'. HTML 'Recieved Mail' is displayed with a bright blue font on a white background in the 'Preview Pane'; very difficult to read. I don't know why the text is not rendered in black or why the 'Preview Pane' background color is not gray. 

The theme I am using doesn't allow changing the colors through System->Preferences->Appearance. I found the config file for my theme and made some changes there.

~/.themes/Industrial-DarkAndBlue/gtk-2.0/gtkrc

**Changes made:**
```

### changed bg[INSENSITIVE] = "#efebe7" to "#5b5b5b"

  bg[NORMAL] = "#5b5b5b"
  bg[INSENSITIVE] = "#5b5b5b"
  bg[ACTIVE] = "#bab5ab"
  bg[PRELIGHT] = "#9db3cc" #"#ffbc00"
  bg[SELECTED] = "#9db3cc" #"#ffbc00"

  fg[NORMAL] = "#9db3cc" #"#ffbc00"#"#000000"
  fg[SELECTED] = "#ffffff"
  fg[ACTIVE] = "#000000"
  fg[PRELIGHT] = "#000000"

#### changed base[NORMAL] ="#efebe7" to "#5b5b5b"

  base[NORMAL] = "#5b5b5b"
  base[ACTIVE] = "#777777"
  base[SELECTED] = "#9db3cc" #"#ffbc00"

```
This changed the behavior of the 'Preview Pane' for 'Plain Text' email, the background changed from gray to dark gray (you can run the values through a color picker to see actual color) but the 'Preview Pane' for HTML messages did not change (white background, bright blue fonts). 

I also looked in the following places to make changes: 
/usr/share/gconf/schemasevolution-mail.schemas
~/.gconf/apps/evolution/mail/display/%gconf.xml

I was looking for this, looked like it might do what I need:
/schemas/apps/display/evolution/mail/display/fonts/use_custom
Default value: FALSE, Description: Use custom fonts for displaying mail

Don't know if this allows changing just the font or the color as well.

This seems simple enough I would think. I just need to find where I can change the value of the background color or the font color of the 'Preview Pane' for HTML messages. (For Received Mail, not Composing mail)

---

