---
title: "Print-to-File selects &quot;File System&quot; as default save location-- how to fix?"
date: 2011-01-30
forum: Desktop Environments
---

### Post by nrundy on 2011-01-30
Not sure how this happened, but my Print-to-file always automatically displays "File System" as the default save location.

Does anybody know how to change this back to save by default to ~/username

---

### Post by Krytarik on 2011-01-31
Hi nrundy!

For which application?

---

### Post by nrundy on 2011-01-31
which application?  all of them (at least everyone I've tried)

---

### Post by Krytarik on 2011-01-31
I asked, because at least Firefox and Thunderbird use its own configs for that. I didn't find so far where the global settings are stored. I try to soon look futher into that.

---

### Post by nrundy on 2011-01-31
hmm. Yeah, it occurs in Firefox, Thunderbird, and OpenOffice. When I first installed Ubuntu though it was defaulting to /Home/User

so something got messed up at some point.

---

### Post by Krytarik on 2011-01-31
Like I said, you have to fix it for Fx and Tb independendly anyway. Do the following steps for those:
- close them
- go into their respective profile dirs, "~/.mozilla/firefox/*.default" and "~/.thunderbird/*.default"
- open the file "prefs.js"
- remove all entries which start with "user_pref("print."
- save them

If you want to change the default print to file format to PDF instead of PS, and set a default filename, add this option:
```
user_pref("print.print_to_filename", "/home/USERNAME/FILENAME.pdf");
```

---

### Post by nrundy on 2011-01-31
You don't know what "system setting" is making it default to .PS?

Wouldn't it be a "System setting" (as opposed to each application's setting) that got messed up to make it default to File System instead of Home?

---

### Post by Krytarik on 2011-01-31
> **nrundy said:**
> You don't know what "system setting" is making it default to .PS?

Wouldn't it be a "System setting" (as opposed to each application's setting) that got messed up to make it default to File System instead of Home?
If the app doesn't use its own setting, the default format is PDF, and default filename and location is "~/output.pdf". But Fx, Tb and OOo (just yet checked it) don't comply to that settings.

In OOo it's that way: If you check "Print to file" in the "Print..." dialog and press "OK", the "Save" dialog comes up, its default file format is "PostScript", and its default location is the home directory of the current user (as usually is in all "Open" and "Save" dialogs).

---

### Post by nrundy on 2011-02-02
alright. I used about:config to get firefox to default to ~/home and pdf. 

Now I just have to figure out OOo and Thunderbird. No luck on these two so far :)

---

### Post by Krytarik on 2011-02-02
> **nrundy said:**
> alright. I used about:config to get firefox to default to ~/home and pdf. 

Now I just have to figure out OOo and Thunderbird. No luck on these two so far :)
I will definetely take a deeper look into that in the next 2 days or so. Please try in the meantime again to settle Thunderbird, just follow my instructions, it should work, it did for me.

Greetings.

---

### Post by nrundy on 2011-02-05
Alright, I got Tb. Thanks for all your help Krytarik :)

I'll look at OOo next when I get time. Hopefully I'll get that too.

---

