---
title: "Window size of Terminal"
date: 2009-06-01
forum: General Help
---

### Post by dogcity77 on 2009-06-01
Being a relatively complete newbie..

I've got Terminal set to load with a touch of the F12 button, but it keeps starting up with a maximised window, which is proving irritating.

Have the feeling there's a really simple answer, but how do I get it to load using the smaller window? (The size after hitting Alt+F5)

Thanks in advance!

---

### Post by pastalavista on 2009-06-01
I use a great terminal program called 'tilda' which is very customizable and can be set to open with any (not already used) hotkey. You'll just need to add it to your start-up program list or start it manually with the command 'tilda' after which one key launches/hides it. The default is F1 but you can change it easily in preferences.
```
sudo apt-get install tilda
```

---

### Post by arubislander on 2009-06-01
I use guake
```
sudo apt-get install guake
```

That also becomes visible with F12. If you hit F11 it will become full screen and remain so until you hit F11 again. Maybe your terminal program does that too?

---

### Post by baseface on 2009-06-01
have you read the man page?
im 99.9999999% sure there will be a geometry option you can set.
man pages are typically a good resource.

---

### Post by benj1 on 2009-06-01
> **arubislander said:**
> I use guake
```
sudo apt-get install guake
```

That also becomes visible with F12. If you hit F11 it will become full screen and remain so until you hit F11 again. Maybe your terminal program does that too?

+1 for guake compared to tilda imo

---

### Post by cubeist on 2009-06-01
Or just open the terminal with a custom profile... command is

```
gnome-terminal --window-with-profile=name
```
just change name to the name of your profile, then in the terminal settings, set the size of the terminal window...

---

### Post by dogcity77 on 2009-06-01
Thanks guys, will look into the suggestions and solutions

---

### Post by dogcity77 on 2009-06-05
> **baseface said:**
> have you read the man page?
im 99.9999999% sure there will be a geometry option you can set.
man pages are typically a good resource.

Yeah, expect it comes back with no manual available for terminal...

---

