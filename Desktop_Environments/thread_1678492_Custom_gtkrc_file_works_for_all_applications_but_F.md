---
title: "Custom gtkrc file works for all applications but Firefox"
date: 2011-01-30
forum: Desktop Environments
---

### Post by oarion7 on 2011-01-30
Hi everyone

I use a dark theme in gnome, which of course doesn't display correctly on many websites that force a white background onto text input dialogues (I have to type white or light gray on white) - Because of this, I never use a dark theme for more than a few days before I switch back to light, which really sucks - My workaround for this was going to be changing my Firefox launcher so that a custom GTKRC is used.

It *works* for all applications except for Firefox.

e.g. if I type into a Terminal:

```
env GTK2_RC_FILES="/usr/share/themes/Redmond/gtk-2.0/gtkrc" speedcrunch
```

or

```
bash -c 'GTK2_RC_FILES=/usr/share/themes/Redmond/gtk-2.0/gtkrc speedcrunch'
```

It loads speedcrunch in Redmond theme, no problem. This works with Pidgin as well. But if I run


```
env GTK2_RC_FILES="/usr/share/themes/Redmond/gtk-2.0/gtkrc" firefox
```

or

```
bash -c 'GTK2_RC_FILES=/usr/share/themes/Redmond/gtk-2.0/gtkrc firefox'
```

I get Firefox in my normal GTK theme, no Redmond. Even if I run **gksudo firefox**, it still loads in my own regular GTK theme.

On my system, the Firefox bin file is not a binary but a symbolic link to a shell script inside "/usr/lib/firefox-3.6.13" which in turn loads Firefox. I don't know if this is the norm or not. Could this be related to my problem?

---

### Post by kerry_s on 2011-01-30
firefox is **not** gtk.

---

### Post by Krytarik on 2011-01-31
What colors do you actually want to have in the text input boxes? Black on white background or the other way around?

You may try to set them with a custom "userContent.css" in the "chrome" directory of your Firefox profile. This one is from the Elegant Gnome theme:
```
input {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

textarea {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

select {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

input[type="radio"],
input[type="checkbox"] {
border: 2px inset white ! important;
background-color: white ! important;
color: ThreeDFace ! important;
-moz-appearance: none !important;
}

*|*::-moz-radio {
background-color: white;
-moz-appearance: none !important;
}

button,
input[type="reset"],
input[type="button"],
input[type="submit"] {
border: 2px outset white;
background-color: #eeeeee;
color: black;
-moz-appearance: none !important;
}

body {
background-color: white;
color: black;
display: block;
margin: 8px;
-moz-appearance: none !important;
}
```

---

### Post by Frogs Hair on 2011-01-31
Another option is to try a Firefox theme (Not Personas) that uses its own colors . I like dark themes also and have used this is as a solution.
 
I don't like black or dark search boxes and a theme was one way around this.

---

### Post by oarion7 on 2011-02-01
> **Krytarik said:**
> What colors do you actually want to have in the text input boxes? Black on white background or the other way around?

You may try to set them with a custom "userContent.css" in the "chrome" directory of your Firefox profile. This one is from the Elegant Gnome theme [...]

This is very helpful, thanks. Thanks for your help, all.

---

