---
title: "CPU Monitoring Software"
date: 2006-07-20
forum: Desktop Environments
---

### Post by jpprice912 on 2006-07-20
Is there a good program or something that I can monitor my cpu temp on my laptop?  I'm having shutdown issues and I think its an overheating problem.

---

### Post by krismatth3 on 2006-07-20
Check out the packages lm-sensors and gdesklets.

---

### Post by John.Michael.Kane on 2006-07-20
You can also use GNOME Sensors Applet ```
**[COLOR="Red"]sudo aptitude install sensors-applet[/COLOR]**
```

---

### Post by maiki_desu on 2006-07-28
@SD-Plissken : Thanks, that's exactly what I wanted.  Since my fan is about to die, this will be quite useful.

---

### Post by max_dingemans on 2006-07-28
I've been looking for something like sensors-applet for awhile. Thanks alot Plissken.

---

### Post by The Pinny Parlour on 2006-08-14
Hi 

How does one get these programs to work?  Newbie.  ;)

---

### Post by mostwanted on 2006-08-14
> **The Pinny Parlour said:**
> Hi 

How does one get these programs to work?  Newbie.  ;)

To install an applet, right-click on the panel and click "add..."

---

### Post by tribaal on 2006-08-14
To add my 2c to the conversation, I personally use *emifreq-applet* since it also allows you to scale your processor's frequency as you see fit (a nice way to save up on batteries or to control your laptop's temperature).

It's just an apt-get away once you added universe repos.

Enjoy :)

- trib'

---

### Post by The Pinny Parlour on 2006-08-14
Thank you.    No sensors found  doh!

---

### Post by tribaal on 2006-08-14
[QUOTE=The Pinny Parlour]Thank you. No sensors found doh![/QUOTE]

You mean with emitfreq-applet? If that's the case, could you paste the output of ```
acpi -t
```
in here?

This sounds like acpi support isn't turned on or something...

- trib'

---

### Post by [h2o] on 2006-08-14
> **tribaal said:**
> To add my 2c to the conversation, I personally use *emifreq-applet* since it also allows you to scale your processor's frequency as you see fit (a nice way to save up on batteries or to control your laptop's temperature).
Is that neccessary on a newer computer? The frequency applet that is preinstalled shows that my computer (Turion64) very seldom use 100% frequency,but stays at 50% except for when programs start etc...

---

### Post by tribaal on 2006-08-14
> **'[h2o] said:**
> Is that neccessary on a newer computer? The frequency applet that is preinstalled shows that my computer (Turion64) very seldom use 100% frequency,but stays at 50% except for when programs start etc...

Oh well no it's never a necessity... I just like having my temperature and the scaling capabilities bundled in a single applet :)

It's just a choice: I was pointing out that there are alternatives to the most commonly used applet :)

Cheers :-P 

- trib'

---

