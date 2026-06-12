---
title: "Add a custom message to the login screen"
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by Mujaheiden on 2007-05-07
hi

I want to add a custom message to the ubuntu login screen explaining guest users how to login to the guest account.

is there any way of adding a line of text to this screen?

thx

---

### Post by ayoli on 2007-05-07
go to menu Administration > System > Prefrences > GDM pref (i cant renember name in english)
pick 'local' tab and, at bottom, check personalized message and enter your message here.

---

### Post by LuisGMarine on 2007-05-07
Its actually System > Administration > Loging Window

Other than that, the directions after that are acurate.

Good Luck

---

### Post by ayoli on 2007-05-07
thanks translation :)

---

### Post by Mujaheiden on 2007-05-07
ah really, i've overlooked that completely, thanks!

---

### Post by Mujaheiden on 2007-05-21
mmmm ,actually, the text isn't displayed, but ill try the other themes.

---

### Post by forth on 2007-05-27
I got this working but the window gets too wide, does anyone know if there are any short codes you can use to force a line break, like <BR> or something? <- that BR doesnt work by the way I tried it already.

---

### Post by forth on 2007-05-27
> **forth said:**
> I got this working but the window gets too wide, does anyone know if there are any short codes you can use to force a line break, like <BR> or something? <- that BR doesnt work by the way I tried it already.

Sorry resolved my own problem, use **[SIZE="6"]\n[/SIZE]** to create a line break.
next job is to see if I can centralize the text because it doesnt look quite right, but I may be too picky I dont know....

Cheers

---

### Post by ayoli on 2007-05-27
you may want to explore your theme file under:
```
/usr/share/gsm/themes/*<your_theme_name>*
```

---

### Post by forth on 2007-05-27
> **ayoli said:**
> you may want to explore your theme file under:
```
/usr/share/gsm/themes/*<your_theme_name>*
```

Sorry I dont see a gsm folder in /usr/share. Thanks anyway.

---

### Post by forth on 2007-05-27
> **forth said:**
> Sorry resolved my own problem, use **[SIZE="6"]\n[/SIZE]** to create a line break.
next job is to see if I can centralize the text because it doesnt look quite right, but I may be too picky I dont know....

Cheers


Havent yet figured out out to centralise the text but I have got it to line up ok now, heres an example:

if you want the following out put in the message area:
```

Welcome to ABC Computers
Station 5

WARNING
Authorised Users Only!
```

the code will look like:

```

Welcome to ABC Computers\nStation 5\n\nWARNING\nAuthorised Users Only!
```

Hope this helps.

---

### Post by ayoli on 2007-05-28
> **forth said:**
> Sorry I dont see a gsm folder in /usr/share. Thanks anyway.

it was **gdm** not gsm
/usr/share/**gdm**/themes/
choose the folder corresponding to your theme and edit the .xml file
sorry for missplelling :)

---

### Post by forth on 2007-05-29
Thanks, I will have another look when I get home later,I'm guessing that XML is similar to HTML can I just wrap the existing text in  <center> and </center> tags to centralise the welcome text at the login screen?

---

### Post by Mujaheiden on 2007-11-14
How unfortunate that when i upgraded  to Gutsy Gibbon, the login text was reset to default, as well as the custom logo and background color :(

---

