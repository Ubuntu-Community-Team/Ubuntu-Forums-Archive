---
title: "enlightenment reset?"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by brim4brim on 2007-05-12
I just installed enlightenment and changed to the milky theme from default.  Now, the default shelf doesn't work and when I do go back to the themes menu, I can't select other themes from the menu!

Is there a command that will just reset all the settings in enlightenment to default?

---

### Post by visible on 2007-05-18
that same thing happened to me last night.  I was looking for a sessions or desktop file for it to remove cuz I purged it thru terminal with the intent of reinstalling it but could not remember where it would be like the beryl one and want not.

---

### Post by visible on 2007-05-18
I don't know if I reset it so to speak but I did manage to re install it.

I had gone into /usr/xsessions  as root and deleted the enlightenment session file.

now I don't know if this was nessecary becuase in terminal i ran the following...
```

sudo aptitude remove e17 enlightenment
```

then I ran
```

sudo aptitude install e17 enlightenment
```

restarted X (ctrl=alt+backspace)

and the enlightenment session was under sessions and when I started under that everything was kosher again.

now I have to figure out how to use this stuff.  seems really cool though.

---

### Post by cymen on 2007-05-23
Just in case anybody else comes across this and wants a less drastic solution, here's how to restore the default theme from the terminal:

```
enlightenment_remote -theme-set theme default.edj
```

Restart Enlightenment and there you go. Be careful with the themes at the moment: they're slowly being updated to work with the latest code.

---

### Post by Co.Sinecure on 2007-05-24
I did the same thing a week or so ago...I got around it by renaming the theme file to milky_dead :D
That reset e to the default theme.
The themes reside somewhere like /usr/share/enlightenment/themes IIRC

I couldn't find where the config would have been for e17, although I tried deleting .enlightenment/profile.cfg, with no luck


Edit:-
So I just discovered that the reason the themes are broken is because of a recent addition of desktop icon support to e17. They are working on fixing the broken themes

---

